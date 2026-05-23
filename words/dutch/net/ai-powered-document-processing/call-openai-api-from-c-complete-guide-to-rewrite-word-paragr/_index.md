---
category: general
date: 2026-05-23
description: Roep de OpenAI‑API aan in C# om een zin in formele stijl te herschrijven.
  Leer hoe je een Word‑document laadt, een lokale LLM aanroept en een alinea formeel
  herschrijft met Aspose.Words.
draft: false
keywords:
- call openai api
- call local llm
- rewrite sentence formal
- rewrite paragraph formal
- load word document
language: nl
og_description: Roep de OpenAI‑API aan in C# om een zin in formele stijl te herschrijven.
  Volledige stapsgewijze tutorial met code, uitleg en tips.
og_title: OpenAI API aanroepen vanuit C# – Paragrafen in Word herschrijven
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
title: OpenAI API aanroepen vanuit C# – Complete gids voor het herschrijven van Word‑paragrafen
url: /nl/net/ai-powered-document-processing/call-openai-api-from-c-complete-guide-to-rewrite-word-paragr/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# OpenAI API aanroepen vanuit C# – Complete gids voor het herschrijven van Word‑paragrafen

Heb je je ooit afgevraagd hoe je **call OpenAI API** vanuit een .NET‑app kunt aanroepen en direct een stuk tekst kunt polijsten? Misschien heb je een Word‑bestand dat een formelere toon nodig heeft voor een klantrapport, en wil je niet alles zelf opnieuw typen. In deze tutorial lopen we precies dat door: een Word‑document laden, een alinea naar een lokaal gehoste LLM sturen die de OpenAI‑compatibele API nabootst, en een **rewrite paragraph formal** versie terugkrijgen. Aan het einde heb je een uitvoerbare C#‑console‑app die de hele taak in een paar regels uitvoert.

We zullen alles behandelen wat je nodig hebt: de vereiste NuGet‑pakketten, hoe je **load word document** met Aspose.Words doet, de eigenaardigheden van **call local llm**, en waarom de prompt “Rewrite the following sentence in formal tone” consequent een **rewrite sentence formal** resultaat oplevert. Geen externe documentatie, alleen een zelfstandige gids die je kunt copy‑paste en uitvoeren.

## Wat je zult bereiken

- Laad een *.docx*‑bestand met Aspose.Words.  
- Maak een client die **call OpenAI API**‑compatible endpoints kan aanroepen, zelfs als ze lokaal draaien.  
- Stuur een alinea naar de LLM en ontvang een **rewrite paragraph formal** respons.  
- Vervang de originele tekst in het Word‑bestand en sla het bijgewerkte document op.  

De vereisten zijn minimaal: .NET 6+ SDK, Visual Studio of VS Code, en een instantie van een lokale LLM die een OpenAI‑compatibel HTTP‑endpoint exposeert (bijv. Ollama, LM Studio). Als je al een cloud‑sleutel hebt, kun je het endpoint en de API‑sleutel verwisselen – de code blijft hetzelfde.

---

## Stap 1: Het project opzetten en pakketten installeren

Om te beginnen, maak een nieuw console‑project:

```bash
dotnet new console -n WordLlmRewrite
cd WordLlmRewrite
```

Voeg nu de twee NuGet‑pakketten toe die we nodig hebben:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** Aspose.Words.AI wordt geleverd met een dunne wrapper die weet hoe **call OpenAI API**‑style services te gebruiken, zodat je geen handmatige HTTP‑verzoeken hoeft te maken.

## Stap 2: Schrijf de code die **Call OpenAI API** (of een lokale LLM) aanroept

Open `Program.cs` en vervang de inhoud door het volgende. Elke regel wordt hieronder uitgelegd, zodat je niet verdwaalt.

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

### Waarom dit werkt

- **LocalLargeLanguageModel** abstraheert de HTTP‑details, waardoor je **call local llm** precies op dezelfde manier kunt gebruiken als een cloud‑OpenAI‑endpoint.  
- De prompt die we sturen (`Rewrite the following sentence in formal tone:`) is beknopt, wat het model helpt zich te concentreren op een **rewrite sentence formal** transformatie in plaats van ongewenste inhoud toe te voegen.  
- Door `paragraph.Runs` te wissen en een nieuwe `Run` toe te voegen, garanderen we dat het Word‑bestand alleen de nieuwe, formele tekst bevat.

## Stap 3: De applicatie uitvoeren

Zorg ervoor dat je lokale LLM‑server actief is en luistert op `http://localhost:8000/v1`. Voer vervolgens uit:

```bash
dotnet run
```

Als alles correct is ingesteld, zie je:

```
✅ Document rewritten and saved as rewritten.docx
```

Open `rewritten.docx` – de eerste alinea zou nu in een gepolijste, formele stijl moeten staan.

### Voorbeeld van verwachte output

| Origineel (informeel) | Herschreven (formeel) |
|-----------------------|-----------------------|
| *Hey team, kunnen we de resultaten zo snel mogelijk krijgen?* | *Geacht team, zou u alstublieft de resultaten zo spoedig mogelijk kunnen verstrekken?* |

De transformatie laat een nette **rewrite sentence formal** conversie zien, perfect voor zakelijke communicatie.

## Stap 4: De prompt aanpassen voor verschillende tonen

Als je een meer informele herschrijving nodig hebt, wijzig dan simpelweg de prompt:

```csharp
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in a casual tone:\n{paragraph.GetText()}");
```

Evenzo kun je het model vragen om **rewrite paragraph formal** voor langere secties, of zelfs om een heel document samen te vatten. Hetzelfde **call openai api** patroon geldt – verwissel de prompt, houd de clientcode ongewijzigd.

## Stap 5: Randgevallen afhandelen

### Lege alinea's

Soms bevat een Word‑bestand lege alinea's die de LLM in de war brengen. Bescherm hiertegen:

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

### Grote documenten

Het verwerken van een rapport van 100 pagina's alinea voor alinea kan traag zijn. Batch de oproepen:

```csharp
foreach (Paragraph p in doc.GetChildNodes(NodeType.Paragraph, true))
{
    // same rewrite logic for each paragraph
}
```

Wees je bewust van snelheidslimieten op je lokale server; je moet mogelijk een kleine `Thread.Sleep(200)` tussen de oproepen toevoegen.

## Stap 6: Deployen naar productie

1. Vervang de dummy API‑sleutel door een echte als je overschakelt naar Azure OpenAI of OpenAI SaaS.  
2. Sla het endpoint en de sleutel op in omgevingsvariabelen (`OPENAI_ENDPOINT`, `OPENAI_KEY`) en lees ze via `Environment.GetEnvironmentVariable`.  
3. Voeg logging toe (bijv. Serilog) rond het **call openai api**‑blok om request/response‑payloads te traceren.

## Stap 7: Bonus – Een eenvoudige UI toevoegen

Als je een snelle Windows Forms‑frontend verkiest:

```csharp
// inside a button click handler
var filePath = openFileDialog1.FileName;
Document doc = new Document(filePath);
// reuse the same rewriting logic...
```

Zo kunnen niet‑technische teamleden een bestand slepen en laten herschrijven in formele stijl zonder code aan te raken.

---

## Conclusie

We hebben zojuist een klein maar krachtig C#‑hulpmiddel gebouwd dat **call openai api** (of elke compatibele lokale LLM) gebruikt om **rewrite paragraph formal** in een Word‑bestand te doen. Door **load word document** te gebruiken, een beknopte prompt te sturen en de alinea‑tekst te vervangen, krijg je binnen enkele seconden een gepolijst document.

Vanaf hier kun je:

- Het hulpmiddel uitbreiden om tabellen en afbeeldingen te verwerken.  
- Integreren met SharePoint voor geautomatiseerde documentpolijsting.  
- Experimenteren met andere tonen — **rewrite sentence formal**, **rewrite sentence casual**, of zelfs **rewrite sentence persuasive**.

Probeer het, pas de prompts aan, en laat de LLM het zware werk voor je doen. Veel programmeerplezier!

## Gerelateerde tutorials

- [Een Word‑document maken en opmaken in Aspose.Words voor .NET](/words/english/net/document-styling/apply-paragraph-style/)
- [Paragraafstijl toepassen in Word‑document](/words/english/net/document-formatting/apply-paragraph-style/)
- [Naar alinea verplaatsen in Word‑document](/words/english/net/add-content-using-documentbuilder/move-to-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}