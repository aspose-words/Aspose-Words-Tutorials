---
category: general
date: 2026-04-28
description: Anslut till en lokal LLM från C# och be den stora språkmodellen att ladda
  ett Word‑dokument, anropa den lokala LLM:n och automatiskt skriva om texten. Steg‑för‑steg‑kod
  inkluderad.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: sv
og_description: Anslut till en lokal LLM från C# och se hur du kan ge en prompt till
  en stor språkmodell, ladda ett Word‑dokument, anropa den lokala LLM:n och automatiskt
  skriva om texten på några minuter.
og_title: Anslut till lokal LLM i C# – Komplett programmeringsguide
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Anslut till lokal LLM i C# – Komplett programmeringsguide
url: /sv/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Anslut till lokal LLM i C# – Komplett programmeringsguide

Har du någonsin behövt **ansluta till lokal llm** från en .NET‑app och funderat på hur du får den att prata med ett Word‑dokument? Du är inte ensam. I den här guiden går vi igenom hela processen – anslut till lokal llm, **prompt large language model**, ladda ett Word‑dokument, **call local llm** och slutligen **rewrite text automatically**. När du är klar har du ett körbart exempel som omvandlar vilket stycke som helst till en formell ton utan några externa API‑nycklar.

## Vad den här handledningen täcker

Vi börjar med att installera de nödvändiga NuGet‑paketen, sedan startar vi en enkel lokal LLM‑endpoint (tänk Ollama på port 11434). Därefter laddar vi en `.docx`‑fil med Aspose.Words, skickar ett stycke till LLM:n, får tillbaka en omskriven version och skriver tillbaka den i samma dokument. Du får också se hur du hanterar vanliga fallgropar – null‑stycken, async‑disposal och kodningsproblem – så att koden fungerar i produktion, inte bara i en demo.

### Förutsättningar

- .NET 6.0 SDK eller senare (du kan också använda .NET 8 om du vill)
- Visual Studio 2022 eller VS Code med C#‑tillägg
- **Aspose.Words for .NET** (gratis provversion räcker)
- En lokalt hostad LLM som följer `/api/generate`‑kontraktet (t.ex. Ollama, LMStudio)
- Grundläggande kunskap om async/await i C#

> **Proffstips:** Om du ännu inte har installerat Ollama, kör `ollama serve` och hämta en modell med `ollama pull llama3`. Standard‑HTTP‑endpointen blir `http://localhost:11434/api/generate`.

---

## Steg 1: Installera nödvändiga paket

Först lägger vi till Aspose.Words‑ och Aspose.Words.AI‑NuGet‑paketen i ditt projekt.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Dessa bibliotek ger oss möjligheten att **load word document** samt ett lätt skal för att **call local llm** utan att manuellt bygga HTTP‑förfrågningar.

---

## Steg 2: Anslut till den lokala LLM‑endpointen

Att ansluta till en lokalt hostad modell är lika enkelt som att instansiera `LocalLargeLanguageModel`. Konstruktorn förväntar sig den fullständiga URL‑en till genererings‑endpointen.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Varför omsluter vi endpointen i en klass? `LocalLargeLanguageModel` sköter JSON‑serialisering, återförsök och strömmande svar åt dig – så att du kan fokusera på prompt‑logiken istället för att trassla med `HttpClient`.

---

## Steg 3: Ladda källdokumentet

Nästa steg är att läsa in dokumentet i minnet. Aspose.Words stödjer praktiskt taget alla Word‑format, så `Document` kan parsas från `input.docx` utan att Office behöver vara installerat.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Om du behöver arbeta med en ström (t.ex. en fil som laddas upp via ASP.NET) ersätter du bara filsökvägen med en `MemoryStream` och skickar den till `Document`‑konstruktorn.

---

## Steg 4: Extrahera texten i det aktuella stycket

Vi använder `DocumentBuilder` för att navigera i dokumentet. I det här exemplet skriver vi om **det första stycket**, men du kan iterera över `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` för att bearbeta många.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

Operatorn `?.` förhindrar ett `NullReferenceException` om dokumentet skulle vara tomt. Detta är ett av de **edge cases** som ofta får nybörjare att fastna.

---

## Steg 5: Prompt LLM:n att skriva om stycket

Nu **prompt large language model** på riktigt. Prompten är skriven på vanlig engelska; wrapper‑klassen skickar den som JSON till den lokala endpointen.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Varför formulerar vi förfrågan på detta sätt? LLM:er svarar bäst på tydliga, enkla instruktioner. En radbrytning efter kolon separerar instruktionen från innehållet och minskar risken för att modellen återupprepar prompten.

**Förväntat resultat** – Om `originalParagraph` var `"Hey, what's up?"` kan LLM:n svara:

> “Good day, how may I assist you?”

Du kan verifiera resultatet genom att skriva ut det:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Steg 6: Sätt in den omskrivna texten i dokumentet

När vi har den nya texten ersätter vi det gamla stycket. `DocumentBuilder.Writeln` skriver en ny rad och flyttar markören framåt, vilket är perfekt för att lägga till text. Om du vill *ersätta* exakt samma stycke kan du först anropa `docBuilder.CurrentParagraph.RemoveAllChildren()` innan du skriver.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Båda metoderna visas så att du kan välja den som passar ditt arbetsflöde bäst.

---

## Steg 7: Spara det uppdaterade dokumentet

Till sist sparar vi ändringarna till en ny fil. Aspose.Words väljer automatiskt format baserat på filändelsen.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Öppna `output.docx` i Word, så ser du att stycket nu har en formell ton.

---

## Fullständigt fungerande exempel

Nedan finns det **kompletta, självständiga programmet**. Kopiera och klistra in i ett konsolprojekt, återställ NuGet‑paketen och kör – ingen extra konfiguration behövs förutom en körande lokal LLM.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Vad du kan förvänta dig när du kör det

1. Konsolen skriver ut både original‑ och omskrivna stycken.  
2. `output.docx` dyker upp bredvid `input.docx`.  
3. När du öppnar filen ser du det nya formella stycket antingen infogat efter originalet (eller ersatt, om du använde den alternativa koden).

---

## Hantera vanliga edge cases

| Situation | Lösning |
|-----------|----------|
| **Tomt eller endast blanksteg‑stycke** | Kontrollera `string.IsNullOrWhiteSpace` innan du promptar (se Steg 3). |
| **LLM returnerar fel eller tom sträng** | Omge `PromptAsync` med `try/catch` och falla tillbaka på originaltexten. |
| **Flera stycken ska skrivas om** | Loopa igenom `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` och applicera samma prompt‑logik. |
| **Stora dokument ger hög latens** | Batcha stycken och skicka dem i en enda förfrågan (max ca 4 KB per anrop). |
| **Icke‑ASCII‑tecken blir felaktiga** | Säkerställ att LLM‑endpointen använder UTF‑8 (de flesta moderna modeller gör det). |

---

## Nästa steg & relaterade ämnen

- **Prompt large language model** med rikare instruktioner (t.ex. stilguider, längdgränser).  
- Använd **call local llm** i ett web‑API för att exponera dokument‑automation som en tjänst.  
- Utforska **load word document** i parallella strömmar för hög genomströmning.  
- Kombinera detta med **rewrite text automatically** för massutskick av e‑mail eller standardisering av rapporter.  

Vill du fördjupa dig mer, kolla in Asposes dokumentation om **document merging** samt Ollama‑API‑referensen för anpassade sampling‑parametrar.

---

## Slutsats

Vi har just visat hur du **connect to local llm** från C#, **prompt large language model**, **load word document**, **call local llm** och **rewrite text automatically** – allt i ett enda körbart konsolprogram. Mönstret är skalbart: byt prompt, iterera över stycken eller exponera logiken via en ASP.NET‑endpoint. Det viktigaste att ta med sig är att lokala AI‑modeller kan integreras tätt med klassiska dokument‑bearbetningsbibliotek, vilket ger kraftfull automation utan att någonsin lämna din säkra on‑prem‑miljö.

Har du frågor om trådar,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}