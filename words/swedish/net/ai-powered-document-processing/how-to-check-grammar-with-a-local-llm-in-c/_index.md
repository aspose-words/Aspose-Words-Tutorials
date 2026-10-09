---
category: general
date: 2026-03-19
description: Lär dig hur du kontrollerar grammatik i Word med en lokal LLM, registrerar
  modellen och sparar korrigerade dokument – allt i en enda C#‑handledning.
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: sv
og_description: Hur du kontrollerar grammatiken i Word med en lokal LLM, registrerar
  modellen och sparar korrigerade dokument — steg‑för‑steg‑guide.
og_title: Hur man kontrollerar grammatik med en lokal LLM i C#
tags:
- Aspose.Words
- AI
- C#
title: Hur man kontrollerar grammatik med en lokal LLM i C#
url: /sv/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man kontrollerar grammatik med en lokal LLM i C#

Har du någonsin undrat **hur man kontrollerar grammatik** i ett Word‑dokument utan att skicka din text till molnet? Du är inte ensam. Många utvecklare vill ha integriteten hos en själv‑hostad modell samtidigt som de får AI‑drivna förslag. I den här guiden går vi igenom hur du registrerar en anpassad LLM, konfigurerar Aspose.Words för att använda den och slutligen **hur du sparar korrigerade** filer – allt i ren C#.

Vi kommer också att gå igenom **set up local llm**‑detaljer, visa dig **how to register llm**‑endpoints och demonstrera de exakta stegen för att **check grammar in word**‑dokument. När du är klar har du ett körbart exempel som du kan släppa in i vilket .NET‑projekt som helst.

## Förutsättningar

Innan vi dyker ner, se till att du har:

- .NET 6+ SDK (koden fungerar på .NET Core och .NET Framework)
- Visual Studio 2022 eller VS Code med C#‑tillägg
- Aspose.Words for .NET (v24.12 eller nyare) – du kan hämta det från NuGet
- En lokalt körande LLM som talar OpenAI‑kompatibelt API (t.ex. Ollama på port 11434)

> **Pro tip:** Om du använder Ollama så startar kommandot `ollama serve` automatiskt endpointen `http://localhost:11434/api/generate`.

## Steg 1 – How to register llm: Add the custom model to Aspose.Words

Det första vi behöver är att berätta för Aspose.Words om vår **local llm**. Detta görs en gång per applikationsstart.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**Why this matters:** Genom att registrera modellen ger du Aspose.Words ett namngivet handtag (`"local-llm"`). Senare, när vi anropar `CheckGrammar`, vet biblioteket exakt vilken endpoint som ska anropas. Att hoppa över detta steg tvingar biblioteket att falla tillbaka på sin inbyggda molntjänst, vilket motverkar syftet med en privat LLM.

## Steg 2 – Load the Word document you want to analyze

Nu läser vi in filen i minnet. Du kan peka på vilken `.docx`, `.doc` eller till och med `.rtf`‑fil som helst.

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**What’s happening:** `Document` är Aspose.Words kärn‑objektmodell. Den parsar filen och bygger ett träd av noder (paragrafer, tabeller, bilder osv.). Detta låter AI‑motorn rikta in sig på specifika textområden för grammatikkontroll.

## Steg 3 – Configure grammar‑check options (set up local llm)

Här kopplar vi den tidigare registrerade modellen till grammatikkontroll‑operationen.

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**Why we expose these options:** Olika LLM:er har olika beteende. Genom att exponera `Model` låter Aspose.Words dig växla mellan en lokal modell och en molnbaserad utan att ändra någon annan kod. Denna flexibilitet är avgörande när du **set up local llm**‑miljöer för efterlevnad eller offline‑scenarier.

## Steg 4 – Run the AI‑driven grammar check (check grammar in word)

När allt är kopplat är den faktiska grammatikkontrollen en enda rad.

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**Under the hood:** Aspose.Words extraherar varje mening, skickar den till LLM‑endpointen, mottar en JSON‑payload med föreslagna ändringar och applicerar sedan dessa ändringar tillbaka i dokumentträdet. Processen körs synkront här för enkelhetens skull; du kan också anropa den asynkrona overloaden `CheckGrammarAsync` om du föredrar icke‑blockerande I/O.

## Steg 5 – How to save corrected documents

När AI:n har gjort sitt magiska arbete vill du spara förändringarna.

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**What to expect:** Öppna `checked.docx` i Word så ser du grammatikproblemen markerade (eller automatiskt korrigerade, beroende på dina `AiGrammarCheckOptions`). Om du har aktiverat spårning ser du även revisionsmarkeringar.

## Fullt fungerande exempel

När vi sätter ihop allt får vi en färdig konsolapp:

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**Expected output in the console:**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

Öppna `checked.docx` så bör du se grammatikförbättringarna applicerade automatiskt.

## Vanliga frågor & kantfall

| Fråga | Svar |
|----------|--------|
| *What if my LLM requires an API key?* | Skicka nyckeln till `apiKey` i `RegisterModel`. Samma kod fungerar för både nyckel‑ och nyckellösa tjänster. |
| *Can I use a different file format?* | Absolut. `Document.Save` accepterar `.pdf`, `.html`, `.txt` osv. Byt bara filändelsen. |
| *What if the LLM returns an error?* | Omslut `CheckGrammar` i ett try/catch‑block; inspektera `AiException` för detaljer. Ofta är det en timeout – överväg att öka `grammarOptions.Timeout`. |
| *Is the operation thread‑safe?* | Registreringssteget är globalt och bör göras en gång vid start. Efterföljande `CheckGrammar`‑anrop är säkra att köra parallellt så länge varje anrop använder sin egen `Document`‑instans. |

## Nästa steg

Nu när du vet **how to check grammar** med en **local llm**, kan du utforska:

- **Batch processing**: Loopa igenom en mapp med dokument och kör samma pipeline.
- **Custom prompts**: Justera request‑payloaden genom att sätta `grammarOptions.PromptTemplate` för stil‑specifika kontroller.
- **Integration with ASP.NET Core**: Exponera en API‑endpoint som tar emot uppladdade `.docx`‑filer, kör grammatikkontrollen och returnerar den korrigerade filen.

Dessa tillägg låter dig bygga en full‑featured “grammar‑as‑a‑service”‑plattform utan att någonsin lämna dina lokaler.

---

*Happy coding! If you hit any snags, drop a comment below—I'm happy to help you fine‑tune the setup.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}