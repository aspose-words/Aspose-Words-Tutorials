---
category: general
date: 2026-05-04
description: Vat Word‑documenten snel samen en vertaal tekst met Google. Leer hoe
  je Anthropic Claude gebruikt, een samenvatting maakt van een rapport, en tekst vertaalt
  met Google in één C#‑tutorial.
draft: false
keywords:
- summarize word document
- translate text with google
- summarize document with ai
- how to use anthropic claude
- create summary from report
language: nl
og_description: Vat Word-document direct samen en vertaal tekst met Google. Deze gids
  laat zien hoe je Anthropic Claude en Aspose.Words kunt gebruiken om een samenvatting
  van een rapport te maken.
og_title: Samenvatten van Word‑document in C# – Stap‑voor‑stap met Anthropic Claude
tags:
- Aspose.Words
- C#
- AI summarization
- Google Translator
title: Word-document samenvatten in C# – Complete gids met Anthropic Claude
url: /nl/net/ai-powered-document-processing/summarize-word-document-in-c-complete-guide-using-anthropic/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Samenvatten van Word-document in C# – Complete gids met Anthropic Claude

Heb je ooit een **samenvatten van een Word-document** nodig gehad maar zat je vast met het jongleren met API's en omslachtige code? Je bent niet alleen. In veel projecten—jaarrapporten, juridische stukken of onderzoeksartikelen—het extraheren van een beknopt overzicht is een dagelijks pijnpunt. Gelukkig maakt de combinatie van Aspose.Words en Anthropic Claude het een fluitje van een cent, en je kunt zelfs een snelle Google‑vertaling toevoegen terwijl je er toch mee bezig bent.

In deze tutorial lopen we alles door wat je moet weten: een groot .docx laden, het Claude V2‑model aanroepen om een samenvatting te genereren, een zin vertalen met Google, en de meest voorkomende valkuilen afhandelen. Aan het einde kun je **een samenvatting van een rapport maken** met slechts een paar regels C#.

## Vereisten

- .NET 6+ (of .NET Core 3.1) geïnstalleerd  
- Een Aspose.Words voor .NET-licentie (of een gratis proefversie)  
- Toegang tot de Anthropic Claude V2 API (je hebt een API‑sleutel nodig)  
- Internetverbinding voor Google Translator  
- Visual Studio 2022 of je favoriete C#‑IDE  

Geen extra NuGet‑pakketten zijn vereist naast `Aspose.Words` en `Aspose.Words.AI`; de vertaler‑klasse wordt meegeleverd met dezelfde bibliotheek.

## Stap 1 – Laad het bron‑Word‑document

Het eerste wat we moeten doen is het .docx‑bestand in het geheugen laden. Aspose.Words maakt dit eenvoudig en dankzij de robuuste parser werkt het met complexe lay-outs, tabellen en zelfs ingesloten afbeeldingen.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Adjust the path to point at your actual file
string sourcePath = Path.Combine(Environment.CurrentDirectory, "LongReport.docx");

// Load the document – this throws if the file is missing or corrupted
Document sourceDoc = new Document(sourcePath);
Console.WriteLine($"✅ Loaded document: {sourceDoc.BuiltInDocumentProperties.Title ?? "Untitled"}");
```

> **Waarom dit belangrijk is:** Het document vroegtijdig laden stelt je in staat eigenschappen (auteur, woordtelling) te inspecteren en te bepalen of een samenvatting zelfs nodig is. Grote bestanden > 10 MB kunnen veel geheugen verbruiken, dus overweeg `LoadOptions` met `LoadFormat.Docx` als je prestatieproblemen ondervindt.

## Stap 2 – Samenvatten van het document met Anthropic Claude

Nu komt het leuke deel: we geven het document door aan Claude V2. De `Summarizer`‑klasse abstraheert de HTTP‑aanroep, token‑afhandeling en retries.

```csharp
// SummarizerModel enum includes several providers; we pick AnthropicClaudeV2
string summaryText = Summarizer.Summarize(
    sourceDoc,
    SummarizerModel.AnthropicClaudeV2
);

// Show the result in the console
Console.WriteLine("\n--- Document Summary ---");
Console.WriteLine(summaryText);
```

> **Hoe het werkt:**  
> 1. **Chunking** – Aspose splitst automatisch het document in beheersbare stukken (≈ 2 KB elk) om binnen de token‑limieten van Claude te blijven.  
> 2. **Prompt engineering** – De bibliotheek stuurt een prompt zoals “Provide a concise executive summary of the following text:” gevolgd door elk stuk.  
> 3. **Aggregation** – Claude retourneert gedeeltelijke samenvattingen die aan elkaar worden gekoppeld tot de uiteindelijke `summaryText`.

### Randgevallen & Tips

- **Zeer grote rapporten** (> 100 pagina's) kunnen het contextvenster van Claude overschrijden. Als je verkorte output ziet, stel `SummarizerOptions.MaxChunkSize` in op kleinere waarden.  
- **Bron in een andere taal dan Engels** – Claude werkt het beste met Engels; voor andere talen eerst vertalen (zie Stap 4) en daarna samenvatten.  
- **Rate limits** – Anthropic legt per‑minuut limieten op. Plaats de aanroep in een retry‑lus met exponentiële back‑off als je een `429`‑respons krijgt.

## Stap 3 – Verifieer de samenvatting

Voordat we doorgaan, is het een goede gewoonte om te controleren of de samenvatting niet leeg is en voldoet aan de lengte‑verwachtingen (bijv. 5‑10 % van het oorspronkelijke aantal woorden).

```csharp
int originalWordCount = sourceDoc.GetText().Split(
    new[] { ' ', '\n', '\r' }, StringSplitOptions.RemoveEmptyEntries).Length;

int summaryWordCount = summaryText.Split(
    new[] { ' ', '\n', '\r' }, StringSplitOptions.RemoveEmptyEntries).Length;

Console.WriteLine($"\nOriginal words: {originalWordCount}");
Console.WriteLine($"Summary words : {summaryWordCount} ({(double)summaryWordCount / originalWordCount:P1})");
```

Als de verhouding te laag lijkt (< 2 %), wil je misschien de eigenschap `SummarizerOptions.SummaryLength` aanpassen om een langere output aan te vragen.

## Stap 4 – Tekst vertalen met Google

Nu we een heldere Engelse samenvatting hebben, laten we een snelle vertaling toevoegen. De `Translator`‑klasse gebruikt Google's openbare vertaal‑endpoint (geen API‑sleutel vereist voor korte zinnen, maar voor productie moet je overstappen op de betaalde Cloud Translation API).

```csharp
// Example phrase – you could also translate the whole summary if needed
string phrase = "Hello world!";
string spanishText = Translator.Translate(
    phrase,
    Language.English,
    Language.Spanish
);

Console.WriteLine("\n--- Translation ---");
Console.WriteLine($"{phrase} → {spanishText}");
```

> **Waarom Google?** Het is snel, breed ondersteund, en het gratis endpoint verwerkt korte strings zonder authenticatie. Voor bulk‑vertalingen, batch de oproepen en respecteer de gebruikslimieten van Google.

### De volledige samenvatting vertalen (optioneel)

Als je de volledige samenvatting in het Spaans (of een andere taal) nodig hebt, geef dan `summaryText` door aan `Translator.Translate`. Houd rekening met de limiet van 5 KB per verzoek; je moet de samenvatting mogelijk in kleinere stukken splitsen.

```csharp
string spanishSummary = Translator.Translate(
    summaryText,
    Language.English,
    Language.Spanish
);
Console.WriteLine("\n--- Spanish Summary ---");
Console.WriteLine(spanishSummary);
```

## Stap 5 – Sla de samenvatting op in een Word‑bestand (bonus)

Vaak verwacht de eindgebruiker een downloadbaar document in plaats van console‑output. Laten we een nieuw `.docx`‑bestand maken dat zowel de Engelse als de Spaanse versie bevat.

```csharp
// Create a fresh document for the summary
Document summaryDoc = new Document();
DocumentBuilder builder = new DocumentBuilder(summaryDoc);

// Title
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Title;
builder.Writeln("Executive Summary");

// English summary
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Normal;
builder.Writeln(summaryText);

// Spanish version
builder.Writeln("\nResumen Ejecutivo (Español)");
builder.Writeln(spanishSummary);

// Save to disk
string outputPath = Path.Combine(Environment.CurrentDirectory, "ReportSummary.docx");
summaryDoc.Save(outputPath);
Console.WriteLine($"\n✅ Summary saved to: {outputPath}");
```

### Praktische tip

Wanneer je de samenvatting in een nieuw Word‑bestand opneemt, houd de oorspronkelijke opmaak minimaal (gebruik `Normal`‑stijl). Complexe stijlen uit de bron kunnen onverwachte lay‑outverschuivingen veroorzaken.

## Volledig werkend voorbeeld

Hieronder staat het **volledige, kant‑klaar‑te‑kopiëren‑en‑plakken** programma dat alles samenbrengt. Het compileert met een enkele `dotnet run` nadat je de Aspose‑pakketten hebt toegevoegd.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // ---------- Load the source document ----------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "LongReport.docx");
        Document sourceDoc = new Document(sourcePath);
        Console.WriteLine($"✅ Loaded: {sourceDoc.BuiltInDocumentProperties.Title ?? "Untitled"}");

        // ---------- Generate summary with Anthropic Claude ----------
        string summaryText = Summarizer.Summarize(sourceDoc, SummarizerModel.AnthropicClaudeV2);
        Console.WriteLine("\n--- Document Summary ---");
        Console.WriteLine(summaryText);

        // ---------- Verify summary length ----------
        int originalWords = sourceDoc.GetText().Split(
            new[] { ' ', '\n', '\r' }, StringSplitOptions.RemoveEmptyEntries).Length;
        int summaryWords = summaryText.Split(
            new[] { ' ', '\n', '\r' }, StringSplitOptions.RemoveEmptyEntries).Length;
        Console.WriteLine($"\nOriginal words: {originalWords}");
        Console.WriteLine($"Summary words : {summaryWords} ({(double)summaryWords / originalWords:P1})");

        // ---------- Translate a phrase (or the whole summary) ----------
        string phrase = "Hello world!";
        string spanishPhrase = Translator.Translate(phrase, Language.English, Language.Spanish);
        Console.WriteLine("\n--- Translation ---");
        Console.WriteLine($"{phrase} → {spanishPhrase}");

        // Optional: translate the whole summary
        string spanishSummary = Translator.Translate(summaryText, Language.English, Language.Spanish);
        Console.WriteLine("\n--- Spanish Summary ---");
        Console.WriteLine(spanishSummary);

        // ---------- Save both versions to a new Word file ----------
        Document summaryDoc = new Document();
        DocumentBuilder builder = new DocumentBuilder(summaryDoc);
        builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Title;
        builder.Writeln("Executive Summary");
        builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Normal;
        builder.Writeln(summaryText);
        builder.Writeln("\nResumen Ejecutivo (Español)");
        builder.Writeln(spanishSummary);
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ReportSummary.docx");
        summaryDoc.Save(outputPath);
        Console.WriteLine($"\n✅ Summary saved to: {outputPath}");
    }
}
```

**Verwachte console‑output** (afgekapt voor beknoptheid):

```
✅ Loaded: Quarterly Financial Review
--- Document Summary ---
The report shows a 12% YoY revenue increase driven by...
Original words: 8420
Summary words : 842 (10.0%)
--- Translation ---
Hello world! → ¡Hola mundo!
--- Spanish Summary ---
El informe muestra un aumento del 12%...
✅ Summary saved to: C:\Projects\ReportSummary.docx
```

## Veelgestelde vragen

| Vraag | Antwoord |
|----------|--------|
| *Kan ik een ander AI‑model gebruiken?* | Ja. Vervang `SummarizerModel.AnthropicClaudeV2` door `SummarizerModel.OpenAIGPT4` (vereist een OpenAI‑sleutel) of een andere provider die in de enum staat. |
| *Wat als het document beveiligde secties bevat?* | Aspose zal een `ProtectedDocumentException` werpen. Ontgrendel het eerst met `LoadOptions.Password` of vraag een onbeveiligde kopie aan. |
| *Heb ik een betaalde Aspose‑licentie nodig voor productie?* | De gratis proefversie werkt tot 20 pagina's. Voor grotere rapporten verwijdert een licentie de paginalimiet en voegt prestatie‑optimalisaties toe. |
| *Is de Google‑vertaler betrouwbaar voor grote blokken?* | Voor korte strings is het prima. Voor bulk‑vertaling, schakel over naar de Cloud Translation API om verzoek‑grootte‑limieten te vermijden en betere taalherkenning te krijgen. |

## Conclusie

We hebben zojuist **samenvatten van een Word-document** gedaan met Aspose.Words samen met het Anthropic Claude V2‑model, vervolgens **tekst vertalen met Google** naar

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}