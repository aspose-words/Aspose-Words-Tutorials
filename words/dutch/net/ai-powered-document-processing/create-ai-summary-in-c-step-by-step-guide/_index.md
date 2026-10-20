---
category: general
date: 2026-08-07
description: Maak een AI-samenvatting in C# om snel een Word‑document samen te vatten
  met OpenAI. Leer hoe je de OpenAI‑API‑sleutel instelt en de document‑samenvatting
  automatiseert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create AI summary
- summarize Word document
- set OpenAI API key
- generate summary OpenAI
- automate document summarization
language: nl
lastmod: 2026-08-07
og_description: Maak een AI-samenvatting in C# om direct een Word‑document samen te
  vatten. Volg deze tutorial om de OpenAI‑API‑sleutel in te stellen, een samenvatting
  met OpenAI te genereren en de document‑samenvatting te automatiseren.
og_image_alt: Console window displaying the generated AI summary of a Word document
og_title: Maak AI‑samenvatting in C# – volledige gids voor ontwikkelaars
schemas:
- author: GroupDocs
  dateModified: '2026-08-07'
  description: Create AI summary in C# to quickly summarize a Word document using
    OpenAI. Learn how to set OpenAI API key and automate document summarization.
  headline: Create AI summary in C# – step‑by‑step guide
  type: TechArticle
tags:
- AI
- C#
- Document processing
- OpenAI
- Automation
title: AI‑samenvatting maken in C# – stapsgewijze handleiding
url: /nl/net/ai-powered-document-processing/create-ai-summary-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak AI‑samenvatting in C# – stapsgewijze handleiding

Als je een **AI‑samenvatting** van een groot Word‑bestand moet maken, laat deze tutorial je precies zien hoe je dat doet met C# en de GroupDocs AI SDK. Je leert hoe je **Word‑document**‑inhoud **samenvat**, **OpenAI API‑sleutel instelt**, en **document‑samenvatting automatiseert** voor herhaalbare workflows.

We lopen elke vereiste stap door, leggen uit waarom elk onderdeel belangrijk is, en bieden een volledige, uitvoerbare console‑applicatie. Aan het einde heb je een zelfstandige oplossing die je in elk .NET‑project kunt gebruiken.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd  
* Een geldige OpenAI API‑sleutel (of Google Gemini‑sleutel als je dat verkiest)  
* Toegang tot het GroupDocs AI for .NET NuGet‑pakket  

Je kunt het pakket installeren met het volgende commando:

```bash
dotnet add package GroupDocs.AI.Summarizer
```

> **Pro tip:** Gebruik een *user‑secret* of omgevingsvariabele om de API‑sleutel op te slaan in plaats van deze hard‑coded in de code te plaatsen.

## Maak AI‑samenvatting met GroupDocs AI SDK

De kern van de oplossing is de `DocumentSummarizer`‑klasse, die een `Document`‑object en een `AiSummarizerOptions`‑instantie accepteert. De opties geven aan welke provider de SDK moet gebruiken en waar de inloggegevens te vinden zijn.

```csharp
using System;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Step 1: Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/LongReport.docx");

        // Step 2: Configure the summarizer (choose provider and supply API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,          // or AiProvider.Google
            ApiKey   = "YOUR_OPENAI_API_KEY"
        };

        // Step 3: Generate the summary using the configured options
        string reportSummary = DocumentSummarizer.Summarize(doc, summarizerOptions);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + reportSummary);
    }
}
```

### Waarom dit werkt

* **Loading the document** converteert het `.docx`‑bestand naar een formaat dat de AI‑engine kan lezen.  
* **AiSummarizerOptions** geeft de SDK aan welke LLM‑provider aangeroepen moet worden en levert het authenticatietoken — dit is waar je **OpenAI API‑sleutel instelt**.  
* **DocumentSummarizer.Summarize** stuurt de documenttekst naar de geselecteerde provider en retourneert een beknopte samenvatting.  
* **Console.WriteLine** drukt het resultaat af, dat je later kunt doorsturen naar een bestand, e‑mail of database.

## Stel OpenAI API‑sleutel in voor samenvatting

Hard‑coderen van de sleutel werkt voor een snelle demo, maar productcode moet geheimen buiten versiebeheer houden. De SDK leest de `ApiKey`‑eigenschap, dus kun je de waarde uit een omgevingsvariabele halen:

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
};
```

Voeg de variabele toe aan je systeem:

```bash
# Windows PowerShell
$Env:OPENAI_API_KEY = "sk-xxxxxxxxxxxxxxxxxxxx"

# macOS / Linux
export OPENAI_API_KEY="sk-xxxxxxxxxxxxxxxxxxxx"
```

> **Waarom dit belangrijk is:** Het veilig opslaan van de sleutel voorkomt onbedoelde blootstelling en voldoet aan de meeste bedrijfs‑beveiligingsbeleid.

## Samenvatten van Word‑document met Generate summary OpenAI

De `DocumentSummarizer` roept intern de **Generate summary OpenAI**‑endpoint aan. Als je de aanvraag fijn wilt afstemmen, kun je extra parameters doorgeven via `AiSummarizerOptions`:

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
    Temperature = 0.3,          // Lower temperature for more deterministic output
    MaxTokens   = 250           // Limit the length of the summary
};
```

Deze instellingen helpen je de woordigheid en creativiteit van de geretourneerde tekst te beheersen, wat nuttig is wanneer je **document‑samenvatting automatiseert** over veel bestanden.

## Automatiseer document‑samenvatting in een console‑app

Om meerdere bestanden te verwerken zonder handmatige tussenkomst, wikkel je de logica in een lus en lees je bestands‑paden uit een map:

```csharp
string inputFolder = @"YOUR_DIRECTORY";
foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
{
    Document doc = new Document(filePath);
    string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

    string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
    File.WriteAllText(outputPath, summary);
    Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
}
```

### Wat dit toevoegt

* **Batch processing** – je kunt een willekeurig aantal Word‑bestanden in de map plaatsen en voor elk een `.summary.txt` ontvangen.  
* **Error handling** – je kunt de lus omgeven met `try/catch` om corrupte bestanden over te slaan terwijl je problemen logt.  
* **Scalability** – omdat de SDK per document een HTTP‑verzoek maakt, kun je de lus paralleliseren met `Parallel.ForEach` als je OpenAI‑quota het toelaat.

## Verwachte output

Wanneer je het programma uitvoert met een voorbeeld `LongReport.docx`, drukt de console iets vergelijkbaars af:

```
Summary:
The report outlines the quarterly performance of the sales department, highlighting a 12% increase in revenue driven by new product launches. Key challenges include supply‑chain constraints and rising operational costs. Recommendations focus on expanding the digital sales channel and optimizing inventory management.
```

Het gegenereerde `.summary.txt`‑bestand bevat dezelfde tekst, klaar voor downstream‑gebruik (bijv. e‑mail‑meldingen, kennis‑basisinname, of weergave in een UI).

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Symptoom | Oorzaak | Oplossing |
|----------|---------|-----------|
| *Lege samenvatting* | Document bevat alleen afbeeldingen of tabellen zonder extraheerbare tekst. | Gebruik `doc.ExtractText()` vóór het samenvatten of converteer afbeeldingen naar OCR‑geschikte tekst. |
| *Authenticatiefout* | Verkeerde of ontbrekende API‑sleutel. | Controleer de `OPENAI_API_KEY`‑omgevingsvariabele en zorg dat de sleutel de vereiste rechten heeft. |
| *Rate‑limit respons* | Het overschrijden van de OpenAI‑verzoek‑quota. | Voeg een vertraging (`Task.Delay(1000)`) toe tussen verzoeken of vraag een hogere quota aan bij OpenAI. |
| *Onverwachte taal* | Provider gebruikt standaard Engels maar het bron‑document is in een andere taal. | Stel `summarizerOptions.Language = "es"` in (of de juiste ISO‑code) om de doeltaal af te dwingen. |

## Volledige broncode voor copy‑paste

```csharp
using System;
using System.IO;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Configure summarizer options (set OpenAI API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,
            ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
            Temperature = 0.3,
            MaxTokens   = 250
        };

        // Folder containing Word documents to summarize
        string inputFolder = @"YOUR_DIRECTORY";

        foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
        {
            try
            {
                Document doc = new Document(filePath);
                string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

                string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
                File.WriteAllText(outputPath, summary);

                Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to process {Path.GetFileName(filePath)}: {ex.Message}");
            }
        }
    }
}
```

> **Opmerking:** Vervang `YOUR_DIRECTORY` door het absolute pad naar de map die je `.docx`‑bestanden bevat.

![Console‑output die de gegenereerde AI‑samenvatting van een Word‑document toont](console-output.png)

## Conclusie

Je weet nu hoe je een **AI‑samenvatting** van een Word‑bestand in C# maakt met de GroupDocs AI SDK, hoe je **OpenAI API‑sleutel instelt**, en hoe je **document‑samenvatting automatiseert** voor een willekeurig aantal bestanden. De aanpak werkt met zowel OpenAI‑ als Google‑providers, laat je generatie‑parameters aanpassen, en integreert netjes in bestaande .NET‑oplossingen.

**Volgende stappen**

* Verken de **summarize Word document**‑functie met aangepaste prompts voor toon of lengte.  
* Combineer de samenvatting met **Azure Functions** of **AWS Lambda** om een serverless‑samenvattingsservice te bouwen.  
* Vervang de console‑output door een REST‑API met ASP.NET Core voor on‑demand samenvatting.

Veel programmeerplezier, en geniet van de productiviteitsboost die AI‑gedreven samenvatting aan je document‑workflows geeft!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Nieuw Word‑document maken](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Word‑document maken met Aspose.Words voor .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Word‑document maken met inhoudsopgave in .NET](/words/english/net/add-content-using-document-builder/insert-table-contents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}