---
category: general
date: 2026-05-23
description: Anropa OpenAI API i C# för att skriva om en mening i formell stil. Lär
  dig hur du laddar ett Word‑dokument, anropar en lokal LLM och skriver om ett stycke
  i formell stil med Aspose.Words.
draft: false
keywords:
- call openai api
- call local llm
- rewrite sentence formal
- rewrite paragraph formal
- load word document
language: sv
og_description: Anropa OpenAI API i C# för att skriva om mening i formell stil. Fullständig
  steg‑för‑steg‑handledning med kod, förklaringar och tips.
og_title: Anropa OpenAI API från C# – Skriv om Word-paragrafer
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  headline: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  type: TechArticle
- description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  name: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  steps:
  - name: Why This Works
    text: '- **LocalLargeLanguageModel** abstracts the HTTP details, letting you **call
      local llm** exactly the same way you would a cloud OpenAI endpoint. - The prompt
      we send (`Rewrite the following sentence in formal tone:`) is concise, which
      helps the model focus on a **rewrite sentence formal** transforma'
  - name: Expected Output Example
    text: '| Original (informal) | Rewritten (formal) | |---------------------|--------------------|
      | *Hey team, can we get the results ASAP?* | *Dear team, could you please provide
      the results at your earliest convenience?* |'
  - name: Empty Paragraphs
    text: 'Sometimes a Word file contains empty paragraphs that throw off the LLM.
      Guard against this:'
  - name: Large Documents
    text: 'Processing a 100‑page report paragraph‑by‑paragraph can be slow. Batch
      the calls:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LLM
- OpenAI
- Word Automation
title: Anropa OpenAI API från C# – Komplett guide för att skriva om Word-paragrafer
url: /sv/net/ai-powered-document-processing/call-openai-api-from-c-complete-guide-to-rewrite-word-paragr/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Anropa OpenAI API från C# – Komplett guide för att omskriva Word‑stycken

Har du någonsin funderat på hur du **anropar OpenAI API** från en .NET‑app och på ett ögonblick förbättrar en text? Kanske har du ett Word‑dokument som behöver en mer formell ton för en kundrapport, och du vill slippa skriva om allt manuellt. I den här handledningen går vi igenom exakt det: läsa in ett Word‑dokument, skicka ett stycke till en lokalt hostad LLM som efterliknar OpenAI‑kompatibelt API, och få tillbaka en **rewrite paragraph formal**‑version. När du är klar har du en körbar C#‑konsolapp som klarar hela jobbet på några rader.

Vi täcker allt du behöver: de nödvändiga NuGet‑paketen, hur du **load word document** med Aspose.Words, nyanserna kring **call local llm**, och varför prompten “Rewrite the following sentence in formal tone” på ett pålitligt sätt ger ett **rewrite sentence formal**‑resultat. Inga externa dokument, bara en självständig guide som du kan kopiera, klistra in och köra.

## Vad du kommer att uppnå

- Ladda en *.docx*-fil med Aspose.Words.  
- Skapa en klient som kan **call OpenAI API**‑kompatibla endpointar, även om de körs lokalt.  
- Skicka ett stycke till LLM:n och få ett **rewrite paragraph formal**‑svar.  
- Ersätta den ursprungliga texten i Word‑filen och spara det uppdaterade dokumentet.  

Förutsättningarna är minimala: .NET 6+ SDK, Visual Studio eller VS Code, och en instans av en lokal LLM som exponerar en OpenAI‑kompatibel HTTP‑endpoint (t.ex. Ollama, LM Studio). Om du redan har en moln‑nyckel kan du byta endpoint och API‑nyckel – koden förblir densamma.

---

## Steg 1: Skapa projektet och installera paket

För att börja, skapa ett nytt konsolprojekt:

```bash
dotnet new console -n WordLlmRewrite
cd WordLlmRewrite
```

Lägg nu till de två NuGet‑paket vi behöver:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Proffstips:** Aspose.Words.AI levereras med ett tunt wrapper‑bibliotek som vet hur man **call OpenAI API**‑liknande tjänster, så du slipper skriva egna HTTP‑förfrågningar.

## Steg 2: Skriv koden som **Call OpenAI API** (eller en lokal LLM)

Öppna `Program.cs` och ersätt innehållet med följande. Varje rad förklaras nedan, så du går inte vilse.

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;

// ------------------------------------------------------------
// 1️⃣ Create a client for the local LLM that follows the
//    OpenAI‑compatible API. This is the heart of the
//    “call openai api” step.
// ------------------------------------------------------------
var localLlm = new LocalLargeLanguageModel(
    endpoint: "http://localhost:8000/v1", // change if your server runs elsewhere
    apiKey: "dummy",                      // dummy because the local server usually skips auth
    model: "my-llm");                     // name of the model you want to use

// ------------------------------------------------------------
// 2️⃣ Load the source Word document.
// ------------------------------------------------------------
Document doc = new Document("YOUR_DIRECTORY/source.docx");

// ------------------------------------------------------------
// 3️⃣ Grab the first paragraph that we want to rewrite.
// ------------------------------------------------------------
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;

// ------------------------------------------------------------
// 4️⃣ Ask the LLM to rewrite the paragraph in a formal tone.
//    This is where we “rewrite paragraph formal”.
// ------------------------------------------------------------
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in formal tone:\n{paragraph.GetText()}");

// ------------------------------------------------------------
// 5️⃣ Replace the original paragraph text with the revised version.
// ------------------------------------------------------------
paragraph.Runs.Clear();                     // remove old runs
paragraph.AppendChild(new Run(doc, revisedText));

// ------------------------------------------------------------
// 6️⃣ Save the updated document.
// ------------------------------------------------------------
doc.Save("YOUR_DIRECTORY/rewritten.docx");

// ------------------------------------------------------------
// 7️⃣ Confirmation output.
// ------------------------------------------------------------
Console.WriteLine("✅ Document rewritten and saved as rewritten.docx");
```

### Varför detta fungerar

- **LocalLargeLanguageModel** döljer HTTP‑detaljerna och låter dig **call local llm** på exakt samma sätt som du skulle anropa en molnbaserad OpenAI‑endpoint.  
- Prompten vi skickar (`Rewrite the following sentence in formal tone:`) är kortfattad, vilket hjälper modellen att fokusera på en **rewrite sentence formal**‑omvandling snarare än att lägga till orelaterat innehåll.  
- Genom att rensa `paragraph.Runs` och lägga till ett nytt `Run` försäkrar vi att Word‑filen bara innehåller den fräscha, formella texten.

## Steg 3: Kör applikationen

Se till att din lokala LLM‑server är igång och lyssnar på `http://localhost:8000/v1`. Kör sedan:

```bash
dotnet run
```

Om allt är rätt konfigurerat får du se:

```
✅ Document rewritten and saved as rewritten.docx
```

Öppna `rewritten.docx` – det första stycket bör nu vara skrivet i en polerad, formell stil.

### Exempel på förväntad utdata

| Original (informell) | Omskrivet (formellt) |
|----------------------|----------------------|
| *Hey team, can we get the results ASAP?* | *Dear team, could you please provide the results at your earliest convenience?* |

Transformationen visar en ren **rewrite sentence formal**‑konvertering, perfekt för affärskommunikation.

## Steg 4: Justera prompten för olika toner

Om du vill ha en mer avslappnad omskrivning, ändra bara prompten:

```csharp
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in a casual tone:\n{paragraph.GetText()}");
```

På samma sätt kan du be modellen att **rewrite paragraph formal** för längre avsnitt, eller till och med att sammanfatta ett helt dokument. Samma **call openai api**‑mönster gäller – byt bara prompten, låt klientkoden vara oförändrad.

## Steg 5: Hantera kantfall

### Tomma stycken

Ibland innehåller en Word‑fil tomma stycken som stör LLM:n. Skydda dig mot detta:

```csharp
if (string.IsNullOrWhiteSpace(paragraph.GetText()))
{
    Console.WriteLine("Skipped empty paragraph.");
}
else
{
    // generate and replace as before
}
```

### Stora dokument

Att bearbeta en 100‑sidig rapport stycke‑för‑stycke kan gå långsamt. Batcha anropen:

```csharp
foreach (Paragraph p in doc.GetChildNodes(NodeType.Paragraph, true))
{
    // same rewrite logic for each paragraph
}
```

Var medveten om hastighetsgränser på din lokala server; du kan behöva lägga till ett litet `Thread.Sleep(200)` mellan anropen.

## Steg 6: Distribuera till produktion

När du flyttar från en utvecklingsmaskin till en CI/CD‑pipeline:

1. Ersätt den dummy‑API‑nyckeln med en riktig om du byter till Azure OpenAI eller OpenAI SaaS.  
2. Spara endpoint och nyckel i miljövariabler (`OPENAI_ENDPOINT`, `OPENAI_KEY`) och läs dem via `Environment.GetEnvironmentVariable`.  
3. Lägg till loggning (t.ex. Serilog) runt **call openai api**‑blocket för att spåra request/response‑payloads.

## Steg 7: Bonus – Lägg till ett enkelt UI

Om du föredrar ett snabbt Windows Forms‑gränssnitt:

```csharp
// inside a button click handler
var filePath = openFileDialog1.FileName;
Document doc = new Document(filePath);
// reuse the same rewriting logic...
```

På så sätt kan icke‑tekniska kollegor dra‑och‑släppa en fil och få en formell omskrivning utan att röra kod.

---

## Slutsats

Vi har just byggt ett litet men kraftfullt C#‑verktyg som **call openai api** (eller någon kompatibel lokal LLM) för att **rewrite paragraph formal** i ett Word‑dokument. Genom att **load word document**, skicka en kort prompt och byta ut stycketexten får du ett polerat dokument på sekunder.  

Från här kan du:

- Utöka verktyget för att hantera tabeller och bilder.  
- Integrera med SharePoint för automatiserad dokumentpolering.  
- Experimentera med andra toner—**rewrite sentence formal**, **rewrite sentence casual**, eller till och med **rewrite sentence persuasive**.

Prova, justera promptarna, och låt LLM:n göra det tunga arbetet åt dig. Lycka till med kodandet!


## Relaterade handledningar

- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)
- [Apply Paragraph Style In Word Document](/words/english/net/document-formatting/apply-paragraph-style/)
- [Move To Paragraph In Word Document](/words/english/net/add-content-using-documentbuilder/move-to-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}