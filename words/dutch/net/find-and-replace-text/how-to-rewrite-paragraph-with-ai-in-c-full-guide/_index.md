---
category: general
date: 2026-06-08
description: Hoe een alinea te herschrijven met AI in C# met behulp van Aspose.Words
  en een lokaal LLM‑endpoint. Leer een Word‑document programmatisch te bewerken met
  duidelijke code.
draft: false
keywords:
- how to rewrite paragraph
- rewrite paragraph with ai
- integrate local llm
- edit word document programmatically
- local llm endpoint
language: nl
og_description: Hoe een alinea te herschrijven met AI in C# met Aspose.Words en een
  lokale LLM-endpoint. Beheers het bewerken van Word-documenten via code.
og_title: Hoe een alinea te herschrijven met AI in C# – Volledige gids
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: How to rewrite paragraph with AI in C# using Aspose.Words and a local
    LLM endpoint. Learn to edit Word document programmatically with clear code.
  headline: How to Rewrite Paragraph with AI in C# – Full Guide
  type: TechArticle
- description: How to rewrite paragraph with AI in C# using Aspose.Words and a local
    LLM endpoint. Learn to edit Word document programmatically with clear code.
  name: How to Rewrite Paragraph with AI in C# – Full Guide
  steps:
  - name: 1️⃣ Load the Source Document
    text: First we need to open the Word file we want to touch. Aspose.Words makes
      this a one‑liner.
  - name: 2️⃣ Grab the Paragraph to Rewrite
    text: We’re focusing on the very first paragraph, but you could loop over any
      collection.
  - name: 3️⃣ Build the AI Rewrite Request
    text: Aspose.Words.AI ships with a convenient `AiRewriteRequest` class. We point
      it at our **local llm endpoint**, supply a prompt, and tell it which model to
      hit.
  - name: 4️⃣ Send the Request & Replace the Text
    text: Now the magic happens—Aspose sends the paragraph text to the LLM, receives
      the rewritten version, and we swap it in.
  - name: 5️⃣ Save the Modified Document
    text: Finally we write the updated file back to disk. The same `Document.Save`
      method works for DOCX, PDF, HTML, and more.
  type: HowTo
- questions:
  - answer: Absolutely. Replace `LocalLlModel` with `OpenAiModel("gpt-4")` (or any
      cloud provider) and supply your API key.
    question: Can I use a remote LLM instead?
  - answer: As shown earlier, clear `firstParagraph.Runs` and append a new `Run`.
      This avoids style clashes.
    question: What if the paragraph has more than one run?
  - answer: Yes, each `AiRewriteRequest` creates its own HTTP client under the hood.
      You can fire off multiple rewrites in parallel with `Task.WhenAll`.
    question: Is the rewrite operation thread‑safe?
  - answer: Loop over `document.FirstSection.Body.Paragraphs` and apply the same request.
      Remember to respect rate limits of your **local llm endpoint**.
    question: How do I rewrite *all* paragraphs?
  - answer: The free trial works for development, but a license removes evaluation
      watermarks and unlocks full performance.
    question: Do I need a license for Aspose.Words?
  type: FAQPage
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Hoe je een alinea herschrijft met AI in C# – Volledige gids
url: /nl/net/find-and-replace-text/how-to-rewrite-paragraph-with-ai-in-c-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een alinea herschrijven met AI in C#

Heb je je ooit afgevraagd **hoe je een alinea kunt herschrijven** automatisch zonder zelf Word te openen? Je bent niet de enige. In veel automatiseringspijplijnen moeten we een zin nemen, er een nieuwe toon aan geven, en deze terugplaatsen in hetzelfde DOCX‑bestand — allemaal zonder dat een mens het intypt.  

In deze gids lopen we een compleet, uitvoerbaar voorbeeld door dat laat zien **hoe je een alinea kunt herschrijven** met Aspose.Words, hoe je **alinea kunt herschrijven met AI** door een **lokale llm‑endpoint** aan te roepen, en hoe je **een Word‑document programmatically kunt bewerken**. Aan het einde heb je een zelfstandige C#‑console‑app die de eerste alinea van *input.docx* herschrijft in een formele stijl en het resultaat opslaat als *Rewritten.docx*.

> **Waarom zou je dit willen?**  
> Het automatiseren van toon‑aanpassingen (formeel → informeel, simpel → technisch) kan uren handmatig bewerken besparen, vooral bij het genereren van contracten, rapporten of e‑mailconcepten op schaal.

## Vereisten

- .NET 6 SDK (of een recente .NET‑versie)  
- Visual Studio 2022 of VS Code – wat je ook verkiest  
- Aspose.Words for .NET (gratis proefversie of gelicentieerd) – installeren via NuGet  
- Een lokaal gehoste LLM die de OpenAI‑compatibele API ondersteunt (bijv. Ollama, Llama.cpp, of een aangepaste Flask‑wrapper) luisterend op `http://localhost:5000`  

Als je die hebt, kunnen we beginnen.

## Hoe een alinea herschrijven met AI – Stap‑voor‑stap

Hieronder splitsen we het proces in vijf duidelijke stappen. Elke stap heeft een eigen H2‑kop, een beknopt code‑fragment en een uitleg over **waarom** we doen wat we doen.

### 1️⃣ Laad het bron‑document

Eerst moeten we het Word‑bestand openen dat we willen bewerken. Aspose.Words maakt dit een één‑regelige opdracht.

```csharp
using Aspose.Words;

// Load the DOCX that contains the paragraph we’ll rewrite
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the original first paragraph
Console.WriteLine("Original: " + document.FirstSection.Body.Paragraphs[0].GetText());
```

*Waarom dit belangrijk is:*  
De `Document`‑klasse abstraheert het volledige Office‑bestandsformaat, waardoor we directe toegang hebben tot secties, bodies en alinea’s. Geen COM‑interop, geen Office‑installatie nodig — perfect voor server‑side taken.

### 2️⃣ Haal de alinea op om te herschrijven

We richten ons op de allereerste alinea, maar je kunt over elke collectie itereren.

```csharp
// Retrieve the first paragraph object
Paragraph firstParagraph = document.FirstSection.Body.Paragraphs[0];
```

*Pro tip:*  
Als je **lokale llm**‑logica moet **integreren** voor meerdere alinea’s, sla ze dan eerst op in een lijst:

```csharp
var paragraphs = document.FirstSection.Body.Paragraphs
                     .Where(p => !string.IsNullOrWhiteSpace(p.GetText()))
                     .ToList();
```

Zo kun je later itereren zonder het document opnieuw te openen.

### 3️⃣ Bouw het AI‑herformulering‑verzoek

Aspose.Words.AI wordt geleverd met een handige `AiRewriteRequest`‑klasse. We wijzen deze op ons **lokale llm‑endpoint**, geven een prompt op, en vertellen welke model we willen gebruiken.

```csharp
using Aspose.Words.AI;

// Construct the request that tells the LLM what we want
AiRewriteRequest rewriteRequest = new AiRewriteRequest
{
    Prompt = "Rewrite this sentence in a formal tone.",
    // The LocalLlModel class wraps any HTTP‑compatible LLM service
    Model = new LocalLlModel("http://localhost:5000")
};
```

*Waarom dit essentieel is:*  
Door `LocalLlModel` te gebruiken, **integreren we lokale llm** zonder afhankelijk te zijn van externe cloud‑API’s. Dit vermindert latentie, houdt data on‑prem, en omzeilt API‑sleutel‑problemen.

### 4️⃣ Verstuur het verzoek & vervang de tekst

Nu gebeurt de magie — Aspose stuurt de alinea‑tekst naar de LLM, ontvangt de herschreven versie, en we vervangen deze.

```csharp
// Ask the LLM to rewrite the paragraph
string rewrittenText = firstParagraph.Rewrite(rewriteRequest);

// Replace the original run's text with the new content
firstParagraph.Runs[0].Text = rewrittenText;

// Log the outcome for verification
Console.WriteLine("Rewritten: " + rewrittenText);
```

*Afhandeling van randgevallen:*  
Als de alinea meerdere runs bevat (verschillende stijlen, velden, enz.), wil je ze misschien eerst wissen:

```csharp
firstParagraph.Runs.Clear();
firstParagraph.AppendChild(new Run(document, rewrittenText));
```

Dat garandeert een schone vervanging, vooral wanneer het origineel vetgedrukte tekst of hyperlinks bevat die je niet hoeft te behouden.

### 5️⃣ Sla het gewijzigde document op

Tot slot schrijven we het bijgewerkte bestand terug naar schijf. Dezelfde `Document.Save`‑methode werkt voor DOCX, PDF, HTML en meer.

```csharp
// Persist the changes
document.Save("YOUR_DIRECTORY/Rewritten.docx");

// Optional: open the file automatically (Windows only)
System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
{
    FileName = "YOUR_DIRECTORY/Rewritten.docx",
    UseShellExecute = true
});
```

*Wat je kunt verwachten:*  
Wanneer je *Rewritten.docx* opent, zie je dat de eerste alinea nu formeel klinkt — precies wat de prompt vroeg. Geen handmatig kopiëren‑plakken nodig.

## Volledig werkend voorbeeld

Kopieer het volgende naar een nieuwe Console‑App (`dotnet new console`) en druk op **F5**. Zorg ervoor dat de NuGet‑pakketten `Aspose.Words` en `Aspose.Words.AI` geïnstalleerd zijn (`dotnet add package Aspose.Words` enz.).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;

namespace ParagraphRewriteDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source DOCX
            Document document = new Document("YOUR_DIRECTORY/input.docx");
            Console.WriteLine("Original: " + document.FirstSection.Body.Paragraphs[0].GetText());

            // 2️⃣ Retrieve the first paragraph
            Paragraph firstParagraph = document.FirstSection.Body.Paragraphs[0];

            // 3️⃣ Prepare the rewrite request (local LLM endpoint)
            AiRewriteRequest rewriteRequest = new AiRewriteRequest
            {
                Prompt = "Rewrite this sentence in a formal tone.",
                Model = new LocalLlModel("http://localhost:5000")
            };

            // 4️⃣ Perform the rewrite and replace the text
            string rewrittenText = firstParagraph.Rewrite(rewriteRequest);
            firstParagraph.Runs[0].Text = rewrittenText;
            Console.WriteLine("Rewritten: " + rewrittenText);

            // 5️⃣ Save the updated document
            document.Save("YOUR_DIRECTORY/Rewritten.docx");
            Console.WriteLine("Document saved as Rewritten.docx");
        }
    }
}
```

**Verwachte console‑output** (ervan uitgaande dat de oorspronkelijke zin “Hey, we need this ASAP!” was):

```
Original: Hey, we need this ASAP!
Rewritten: Please expedite this matter at your earliest convenience.
Document saved as Rewritten.docx
```

Als je **lokale llm‑endpoint** een fout retourneert, controleer dan dubbel of het het OpenAI `/v1/completions`‑schema volgt (modelnaam, temperature, max_tokens). Aspose.Words.AI zal het HTTP‑foutbericht tonen, waardoor debuggen eenvoudig is.

## Veelgestelde vragen & Pro‑tips

- **Kan ik in plaats daarvan een remote LLM gebruiken?**  
  Absoluut. Vervang `LocalLlModel` door `OpenAiModel("gpt-4")` (of een andere cloud‑provider) en geef je API‑sleutel op.

- **Wat als de alinea meer dan één run heeft?**  
  Zoals eerder getoond, wis `firstParagraph.Runs` en voeg een nieuwe `Run` toe. Dit voorkomt stijlconflicten.

- **Is de herschrijf‑operatie thread‑safe?**  
  Ja, elke `AiRewriteRequest` maakt onder de motorkap zijn eigen HTTP‑client aan. Je kunt meerdere herschrijvingen parallel uitvoeren met `Task.WhenAll`.

- **Hoe herschrijf ik *alle* alinea’s?**  
  Loop over `document.FirstSection.Body.Paragraphs` en pas hetzelfde verzoek toe. Houd rekening met de rate‑limits van je **lokale llm‑endpoint**.

- **Heb ik een licentie nodig voor Aspose.Words?**  
  De gratis proefversie werkt voor ontwikkeling, maar een licentie verwijdert evaluatiewatermerken en ontgrendelt volledige prestaties.

## Afronding

We hebben zojuist **hoe je een alinea kunt herschrijven** met Aspose.Words, een **lokale llm‑endpoint**, en een paar handige C#‑trucs behandeld. Het kernidee — een alinea naar een AI‑model sturen, een gepolijste versie terugkrijgen, en deze terugplaatsen in het Word‑bestand — kan worden uitgebreid naar bulk‑verwerking, meertalige vertaling, of zelfs het genereren van samenvattingen.

Volgende stappen? Probeer de prompt te wijzigen naar “Maak deze zin informeler” of “Vertaal deze alinea naar het Frans”. Je kunt dezelfde pipeline ook koppelen aan een Azure Function of AWS Lambda om **een Word‑document programmatically te bewerken** on‑the‑fly.

Heb je meer scenario’s waar je nieuwsgierig naar bent? Laat een reactie achter, en happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Inline afbeelding invoegen in Word-document met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Een Word-document met tabel maken met Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Word-document met kop‑ en voettekst maken met Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}