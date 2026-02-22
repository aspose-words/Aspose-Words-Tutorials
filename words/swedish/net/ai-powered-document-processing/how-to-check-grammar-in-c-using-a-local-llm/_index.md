---
category: general
date: 2026-02-21
description: Hur man kontrollerar grammatik i C# genom att ladda en DOCX, skicka dess
  text till en lokal LLM och skriva tillbaka den korrigerade versionen. Inkluderar
  hur man använder LLM och läser text från Word‑dokument.
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: sv
og_description: Hur man kontrollerar grammatik i C# genom att ladda en DOCX, skicka
  dess text till en lokal LLM och skriva tillbaka den korrigerade versionen. Lär dig
  hur du använder LLM och läser text från Word‑dokument.
og_title: Hur man kontrollerar grammatik i C# med en lokal LLM
tags:
- C#
- LLM
- Aspose.Words
title: Hur man kontrollerar grammatik i C# med en lokal LLM
url: /sv/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man kontrollerar grammatik i C# med en lokal LLM

Har du någonsin funderat **hur man kontrollerar grammatik** i ett Word-dokument utan att lämna ditt C#-projekt? Du är inte ensam—utvecklare frågar ständigt, “Kan jag automatisera korrekturläsning med samma kod som driver chatbots?” Det korta svaret är ja. Genom att läsa in en DOCX, extrahera dess text och skicka den till en lokalt‑hostad stor språkmodell (LLM) kan du få omedelbara grammatikfixar och skriva det polerade resultatet direkt tillbaka i filen.

I den här handledningen går vi igenom hela processen: läsa en `.docx` med **load docx in c#**, anropa **how to use llm** för grammatikrättning och slutligen spara det rensade dokumentet. När du är klar har du en färdig‑att‑köra konsolapp som gör exakt det du behöver—ingen manuell kopiering och inklistring, inga externa API:er, bara ren C# och en lokal LLM‑endpoint.

> **Vad du behöver**
> - .NET 6.0 eller senare (koden fungerar även på .NET Framework, men .NET 6 är den bästa versionen)
> - Biblioteket [Aspose.Words for .NET](https://products.aspose.com/words/net/) (gratis provversion fungerar för testning)
> - En körande LLM‑server som exponerar en enkel `CheckGrammar(string)`‑endpoint (t.ex. Ollama, LM Studio eller en egen FastAPI‑wrapper)
> - Grundläggande kunskap om async/await (valfritt men rekommenderas)

Om du undrar **varför du bör bry dig**, tänk på den tid du spenderar på att manuellt rätta stavfel i genererade rapporter. Att automatisera det steget snabbar inte bara upp pipelines utan garanterar också konsekvens över dussintals dokument. Låt oss dyka ner.

---

## Så kontrollerar du grammatik – Översikt

Innan vi sätter igång, här är en snabb färdplan:

1. **Skapa en klient** som kommunicerar med den lokala LLM‑endpointen.  
2. **Läs Word‑dokumentet** med Aspose.Words—detta är det klassiska sättet att **read word document text** i C#.  
3. **Skicka den råa texten** till LLM och ta emot en korrigerad version.  
4. **Ersätt det ursprungliga innehållet** i dokumentet med den korrigerade texten.  
5. **Spara** den uppdaterade filen (valfritt men oftast krävs).

Varje steg är inbäddat i sin egen metod så att du kan återanvända eller ersätta delar senare. Den fullständiga källkoden visas i slutet av artikeln.

---

## Steg 1: Ställ in LLM‑klienten (How to Use LLM)

För att hålla saker organiserade kapslar vi in HTTP‑anropet i en liten wrapper‑klass. Denna klass förutsätter att LLM‑tjänsten accepterar en POST‑förfrågan med en JSON‑payload `{ "prompt": "..."} ` och returnerar `{ "response": "..." }`. Justera serialiseringen om din tjänst skiljer sig.

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

**Varför detta är viktigt:**  
- **Decoupling** – Om du senare byter från Ollama till LM Studio behöver du bara ändra URL‑en eller payload‑formatet.  
- **Async‑friendly** – Nätverks‑I/O blockerar inte ditt UI eller bakgrundsprocess.  
- **Error handling** – `EnsureSuccessStatusCode` kastar ett tydligt undantag om LLM är nere, vilket vi fångar senare.

> **Proffstips:** Om din LLM körs på GPU, håll begärans storlek under ~4 KB för att undvika latensspikar.

---

## Steg 2: Läs in DOCX och extrahera text (Read Word Document Text)

Aspose.Words gör det enkelt att läsa Word‑filer. Metoden `Document.GetText()` returnerar hela den synliga texten och bevarar radbrytningar. Om du behöver rikare formatering (tabeller, fotnoter) måste du gå igenom nodträdet, men för ren grammatikkontroll räcker vanlig text.

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

**Edge case‑anteckning:**  
Om dokumentet innehåller icke‑engelska tecken eller specialsymboler, se till att den LLM‑modell du använder stödjer Unicode. De flesta moderna modeller gör det, men äldre kan trunkera eller misstolka dem.

---

## Steg 3: Ersätt innehåll med den korrigerade texten

Aspose.Words har ingen enradig “ersätt hela kroppen”‑metod, men att rensa nodträdet och infoga ett enda stycke fungerar bra. Detta garanterar också att eventuell dold markup (som spårade ändringar) tas bort.

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

**Varför vi tar bort alla barn:**  
- Garanterar en ren start, vilket förhindrar kvarvarande formatering från att störa det nya innehållet.  
- Förenklar koden—ingen behov av att leta efter specifika noder att ersätta.

Om du föredrar att bevara ursprungliga rubriker kan du parsra det ursprungliga nodträdet, ersätta endast `Run`‑noder, men det ökar komplexiteten utanför denna handlednings räckvidd.

---

## Steg 4: Koppla ihop allt – Fullt fungerande exempel

Nedan är det kompletta konsolprogrammet. Det demonstrerar **how to check grammar** från början till slut, inklusive grundläggande felhantering och valfria kommandoradsargument.

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

### Förväntad utskrift

När du kör programmet (`dotnet run`) kommer konsolen att visa något liknande:

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

Öppna `output.docx` i Word—du kommer att se samma innehåll men med korrigerad interpunktion, subjekt‑verb‑överensstämmelse och eventuella uppenbara stavfel åtgärdade av LLM.

---

## Vanliga frågor & edge‑cases

### Vad händer om LLM returnerar `null` eller en tom sträng?

`CheckGrammarAsync`‑metoden faller tillbaka på originalinmatningen om svarpayloaden saknar `response`‑fältet. Detta förhindrar att du av misstag raderar dokumentet.

### Hur stor kan ett dokument vara innan förfrågan timeoutar?

De flesta lokala LLM‑servrar hanterar några tusen tecken utan problem. För större filer (t.ex. 100 KB+) bör du överväga att dela upp texten i stycken, skicka varje del separat och sedan återmontera de korrigerade delarna. En chunk‑storlek på ~2 KB är en bra startpunkt.

### Bevarar detta bilder, tabeller eller fotnoter?

Nej. Genom att rensa alla barn förlorar vi alla icke‑text‑element. Om du behöver behålla dem måste du iterera genom nodträdet, ersätta endast `Run`‑noder (textfragmenten) och låta andra noder vara orörda. Det är ett mer avancerat scenario—känn dig fri att utforska Aspose.Words‑API:n för `NodeCollection`‑manipulation.

### Kan jag använda en moln‑LLM istället för en lokal?

Absolut. Byt bara endpoint‑URL:en och payload‑formatet i `LocalLargeLanguageModel`. Tänk på att molntjänster ofta har hastighetsgränser och kostnadseffekter, medan en lokal modell körs offline och är gratis efter den initiala GPU/CPU‑installationen.

## Pro‑tips & bästa praxis

- **Cache the client**: Re‑using the same `HttpClient` instance avoids

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}