---
category: general
date: 2026-02-21
description: Hoe grammatica te controleren in C# door een DOCX te laden, de tekst
  naar een lokale LLM te sturen en de gecorrigeerde versie terug te schrijven. Inclusief
  hoe je LLM gebruikt en de tekst van een Word‑document leest.
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: nl
og_description: Hoe je grammatica controleert in C# door een DOCX te laden, de tekst
  naar een lokale LLM te sturen en de gecorrigeerde versie terug te schrijven. Leer
  hoe je LLM gebruikt en tekst uit een Word‑document leest.
og_title: Hoe grammatica te controleren in C# met een lokale LLM
tags:
- C#
- LLM
- Aspose.Words
title: Hoe grammatica te controleren in C# met een lokale LLM
url: /nl/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe grammatica controleren in C# met een lokale LLM

Heb je je ooit afgevraagd **hoe je grammatica kunt controleren** in een Word‑document zonder je C#‑project te verlaten? Je bent niet de enige—ontwikkelaars vragen voortdurend: “Kan ik proeflezen automatiseren met dezelfde code die chatbots aandrijft?” Het korte antwoord is ja. Door een DOCX te laden, de tekst te extraheren en deze aan een lokaal gehost groot taalmodel (LLM) te voeren, kun je directe grammatica‑correcties krijgen en het gepolijste resultaat direct terug in het bestand schrijven.

In deze tutorial lopen we het volledige proces door: een `.docx` lezen met **load docx in c#**, **how to use llm** aanroepen voor grammatica‑correctie, en uiteindelijk het opgeschoonde document opslaan. Aan het einde heb je een kant‑klaar console‑applicatie die precies doet wat je nodig hebt—geen handmatig kopiëren‑plakken, geen externe API's, alleen pure C# en een lokaal LLM‑endpoint.

> **Wat je nodig hebt**
> - .NET 6.0 of later (de code werkt ook op .NET Framework, maar .NET 6 is de ideale keuze)
> - De [Aspose.Words for .NET](https://products.aspose.com/words/net/) bibliotheek (gratis proefversie werkt voor testen)
> - Een draaiende LLM‑server die een eenvoudige `CheckGrammar(string)`‑endpoint blootstelt (bijv. Ollama, LM Studio, of een aangepaste FastAPI‑wrapper)
> - Basiskennis van async/await (optioneel maar aanbevolen)

Als je je afvraagt **waarom dit belangrijk is**, denk dan aan de tijd die je besteedt aan het handmatig corrigeren van typefouten in gegenereerde rapporten. Het automatiseren van die stap versnelt niet alleen pipelines, maar garandeert ook consistentie over tientallen documenten. Laten we beginnen.

---

## Hoe grammatica controleren – Overzicht

Voordat we aan de slag gaan, hier is een snelle routekaart:

1. **Maak een client** die communiceert met het lokale LLM‑endpoint.  
2. **Lees het Word‑document** met Aspose.Words—dit is de klassieke manier om **read word document text** te lezen in C#.  
3. **Stuur de ruwe tekst** naar het LLM en ontvang een gecorrigeerde versie.  
4. **Vervang de originele inhoud** in het document door de gecorrigeerde tekst.  
5. **Sla** het bijgewerkte bestand op (optioneel maar meestal vereist).

Elke stap is verpakt in een eigen methode zodat je later onderdelen kunt hergebruiken of vervangen. De volledige broncode staat aan het einde van het artikel.

## Stap 1: LLM‑client instellen (How to Use LLM)

Om alles netjes te houden, zullen we de HTTP‑aanroep in een kleine wrapper‑klasse encapsuleren. Deze klasse gaat ervan uit dat de LLM‑service een POST‑verzoek accepteert met een JSON‑payload `{ "prompt": "..."}` en `{ "response": "..." }` teruggeeft. Pas de serialisatie aan als je service anders is.

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**Waarom dit belangrijk is:**  
- **Ontkoppeling** – Als je later van Ollama naar LM Studio overschakelt, hoef je alleen de URL of payload‑indeling te wijzigen.  
- **Async‑vriendelijk** – Netwerk‑I/O blokkeert je UI of achtergrondwerker niet.  
- **Foutafhandeling** – `EnsureSuccessStatusCode` gooit een duidelijke uitzondering als het LLM niet beschikbaar is, die we later opvangen.

> **Pro tip:** Als je LLM op een GPU draait, houd de request‑grootte onder ~4 KB om latency‑pieken te vermijden.

## Stap 2: Laad de DOCX en extraheer tekst (Read Word Document Text)

Aspose.Words maakt het lezen van Word‑bestanden een fluitje van een cent. De `Document.GetText()`‑methode retourneert de volledige zichtbare tekst, met behoud van regeleinden. Als je rijkere opmaak nodig hebt (tabellen, voetnoten), moet je door de node‑boom lopen, maar voor zuivere grammatica‑controle is platte tekst voldoende.

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**Opmerking voor randgevallen:**  
Als het document niet‑Engelse tekens of speciale symbolen bevat, zorg er dan voor dat het LLM‑model dat je gebruikt Unicode ondersteunt. De meeste moderne modellen doen dat, maar oudere kunnen ze afkappen of verkeerd interpreteren.

## Stap 3: Vervang inhoud met de gecorrigeerde tekst

Aspose.Words heeft geen één‑regelige “vervang hele body”‑methode, maar het leegmaken van de node‑boom en het invoegen van één alinea werkt prima. Dit garandeert ook dat eventuele verborgen markup (zoals revisies) wordt verwijderd.

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**Waarom we alle kinderen verwijderen:**  
- Garandeert een schone lei, waardoor achtergebleven opmaak de nieuwe inhoud niet kan beïnvloeden.  
- Vereenvoudigt de code—geen noodzaak om specifieke nodes te zoeken om te vervangen.

Als je liever de originele koppen behoudt, kun je de oorspronkelijke node‑boom parseren en alleen `Run`‑nodes vervangen, maar dat voegt complexiteit toe die buiten de reikwijdte van deze tutorial valt.

## Stap 4: Alles aan elkaar koppelen – Volledig werkend voorbeeld

Hieronder staat het volledige console‑programma. Het demonstreert **how to check grammar** van begin tot eind, inclusief basis‑foutafhandeling en optionele command‑line‑argumenten.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### Verwachte output

Wanneer je het programma uitvoert (`dotnet run`), zal de console iets tonen als:

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

Open `output.docx` in Word—je ziet dezelfde inhoud, maar met gecorrigeerde interpunctie, onderwerp‑werkwoord‑overeenstemming en eventuele duidelijke typefouten die door het LLM zijn gecorrigeerd.

## Veelgestelde vragen & randgevallen

### Wat als het LLM `null` of een lege string retourneert?

De `CheckGrammarAsync`‑methode valt terug op de originele invoer als de response‑payload het `response`‑veld mist. Dit voorkomt dat je per ongeluk het document leegt.

### Hoe groot kan een document zijn voordat het verzoek time‑out?

De meeste lokale LLM‑servers kunnen enkele duizenden tekens zonder problemen verwerken. Voor grotere bestanden (bijv. 100 KB+), overweeg de tekst op te delen in alinea’s, elk fragment apart te versturen, en vervolgens de gecorrigeerde stukken weer samen te voegen. Een chunk‑grootte van ~2 KB is een goed startpunt.

### Behoudt dit afbeeldingen, tabellen of voetnoten?

Nee. Door alle kinderen te wissen verliezen we alle niet‑tekstuele elementen. Als je die wilt behouden, moet je door de node‑boom itereren, alleen `Run`‑nodes (de tekstfragmenten) vervangen en andere nodes ongemoeid laten. Dat is een geavanceerder scenario—voel je vrij de Aspose.Words‑API voor `NodeCollection`‑manipulatie te verkennen.

### Kan ik een cloud‑LLM gebruiken in plaats van een lokale?

Zeker. Vervang gewoon de endpoint‑URL en payload‑formaat in `LocalLargeLanguageModel`. Houd er rekening mee dat cloud‑services vaak rate‑limits en kosten met zich meebrengen, terwijl een lokaal model offline draait en gratis is na de initiële GPU/CPU‑installatie.

## Pro‑tips & best practices

- **Cache de client**: Het hergebruiken van dezelfde `HttpClient`‑instantie voorkomt

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}