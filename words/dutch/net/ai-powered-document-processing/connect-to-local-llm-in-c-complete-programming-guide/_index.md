---
category: general
date: 2026-04-28
description: Maak verbinding met een lokale LLM vanuit C# en vraag het grote taalmodel
  om een Word‑document te laden, roep de lokale LLM aan en herschrijf de tekst automatisch.
  Stapsgewijze code inbegrepen.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: nl
og_description: Maak verbinding met een lokale LLM vanuit C# en zie hoe je een groot
  taalmodel kunt aansturen, een Word‑document kunt laden, de lokale LLM kunt aanroepen
  en de tekst automatisch in enkele minuten kunt herschrijven.
og_title: Verbinden met lokale LLM in C# – Volledige programmeergids
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Verbinden met lokale LLM in C# – Complete programmeergids
url: /nl/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verbinden met lokale LLM in C# – Complete programmeergids

Heb je ooit moeten **connect to local llm** vanuit een .NET-app en je afgevraagd hoe je het met een Word‑bestand kunt laten communiceren? Je bent niet de enige. In deze gids lopen we het volledige proces door — connect to local llm, **prompt large language model**, een Word‑document laden, **call local llm**, en uiteindelijk **rewrite text automatically**. Aan het einde heb je een uitvoerbaar voorbeeld dat elke alinea omzet naar een formele toon zonder externe API‑sleutels.

## Wat deze tutorial behandelt

We beginnen met het installeren van de benodigde NuGet‑pakketten, daarna starten we een eenvoudige lokale LLM‑endpoint (denk aan Ollama op poort 11434). Vervolgens laden we een `.docx`‑bestand met Aspose.Words, sturen we een alinea naar de LLM, ontvangen we een herschreven versie, en schrijven we deze terug naar hetzelfde document. Je ziet ook hoe je veelvoorkomende valkuilen kunt afhandelen — lege alinea's, async‑disposing en coderingsproblemen — zodat de code in productie werkt, niet alleen als demo.

### Vereisten

- .NET 6.0 SDK of later (je kunt ook .NET 8 gebruiken als je wilt)
- Visual Studio 2022 of VS Code met C#‑extensie
- **Aspose.Words for .NET** (gratis proefversie werkt prima)
- Een lokaal gehoste LLM die het `/api/generate`‑contract ondersteunt (bijv. Ollama, LMStudio)
- Basiskennis van async/await in C#

> **Pro tip:** Als je Ollama nog niet hebt geïnstalleerd, voer dan `ollama serve` uit en haal een model op met `ollama pull llama3`. Het standaard HTTP‑endpoint zal `http://localhost:11434/api/generate` zijn.

---

## Stap 1: Vereiste pakketten installeren

Voeg eerst de Aspose.Words- en Aspose.Words.AI‑NuGet‑pakketten toe aan je project.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Deze bibliotheken geven ons de **load word document**‑functionaliteit en een dunne wrapper om **call local llm** te gebruiken zonder handmatig HTTP‑verzoeken te maken.

---

## Stap 2: Verbinden met de lokale LLM‑endpoint

Verbinden met een lokaal gehost model is zo simpel als het instantieren van `LocalLargeLanguageModel`. De constructor verwacht de volledige URL van de generatie‑endpoint.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Waarom wikkelen we de endpoint in een klasse? De `LocalLargeLanguageModel` verzorgt JSON‑serialisatie, retries en streaming‑reacties voor je — zodat je je kunt concentreren op de prompt‑logica in plaats van te rommelen met `HttpClient`.

---

## Stap 3: Het bron‑Word‑document laden

Vervolgens brengen we het document in het geheugen. Aspose.Words ondersteunt vrijwel elk Word‑formaat, dus `Document` zal `input.docx` parseren zonder dat Office geïnstalleerd hoeft te zijn.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Als je met een stream moet werken (bijv. een bestand geüpload via ASP.NET), vervang dan gewoon het bestandspad door een `MemoryStream` en geef die door aan de `Document`‑constructor.

---

## Stap 4: De huidige alinea‑tekst extraheren

We gebruiken `DocumentBuilder` om door het document te navigeren. In dit voorbeeld herschrijven we **the first paragraph**, maar je kunt itereren over `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` om er veel te verwerken.

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

De `?.`‑operator voorkomt een `NullReferenceException` als het document toevallig leeg is. Dit is een van die **edge cases** die beginners in de problemen brengen.

---

## Stap 5: De LLM prompten om de alinea te herschrijven

Nu **prompt large language model** we daadwerkelijk. De prompt is gewoon Engels; de wrapper zal deze als JSON naar de lokale endpoint sturen.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Waarom de aanvraag op deze manier formuleren? LLM's reageren het beste op duidelijke, enkel‑taak instructies. Het toevoegen van een nieuwe regel na de dubbele punt scheidt de instructie van de inhoud, waardoor de kans verkleint dat het model de prompt terug echoot.

**Verwachte output** – Als `originalParagraph` `"Hey, what's up?"` was, kan de LLM teruggeven:

> “Good day, how may I assist you?”

Je kunt het resultaat verifiëren door het af te drukken:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Stap 6: De herschreven tekst terug in het document invoegen

Met de nieuwe tekst in de hand, vervangen we de oude alinea. `DocumentBuilder.Writeln` schrijft een nieuwe regel en verplaatst de cursor vooruit, wat perfect is voor toevoegen. Als je de exacte dezelfde alinea moet *vervangen*, kun je `docBuilder.CurrentParagraph.RemoveAllChildren()` gebruiken vóór het schrijven.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Beide benaderingen worden getoond zodat je de methode kunt kiezen die bij je workflow past.

---

## Stap 7: Het bijgewerkte document opslaan

Tot slot slaan we de wijzigingen op in een nieuw bestand. Aspose.Words kiest automatisch het formaat op basis van de bestandsextensie.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Open `output.docx` in Word, en je zult zien dat de alinea nu in een formele toon staat.

---

## Volledig werkend voorbeeld

Hieronder staat het **complete, zelf‑containende programma**. Kopieer‑en‑plak het in een console‑project, herstel de NuGet‑pakketten, en voer het uit — geen extra configuratie nodig behalve een draaiende lokale LLM.

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

### Wat je kunt verwachten bij het uitvoeren

1. De console print de originele en herschreven alinea's.  
2. `output.docx` verschijnt naast `input.docx`.  
3. Het openen van het bestand toont de nieuwe formele alinea ingevoegd na de originele (of vervangen, als je bent overgeschakeld naar de alternatieve code).

---

## Veelvoorkomende randgevallen afhandelen

| Situation | Solution |
|-----------|----------|
| **Lege of alleen uit whitespace bestaande alinea** | Controleer `string.IsNullOrWhiteSpace` vóór het prompten (zie Stap 3). |
| **LLM retourneert een fout of lege string** | Wikkel `PromptAsync` in een `try/catch` en val terug op de originele tekst. |
| **Meerdere alinea's moeten worden herschreven** | Loop door `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` en pas dezelfde prompt‑logica toe. |
| **Grote documenten veroorzaken latentie** | Batch alinea's en stuur ze in één verzoek (prompt tot 4 KB per call). |
| **Niet‑ASCII tekens worden vervormd** | Zorg ervoor dat de LLM‑endpoint UTF‑8 gebruikt (de meeste moderne modellen doen dat). |

---

## Volgende stappen & gerelateerde onderwerpen

- **Prompt large language model** met uitgebreidere instructies (bijv. stijlgidsen, lengtebeperkingen).  
- Gebruik **call local llm** in een web‑API om document‑automatisering als service beschikbaar te maken.  
- Verken **load word document** in parallelle streams voor high‑throughput scenario's.  
- Combineer deze aanpak met **rewrite text automatically** voor bulk‑e‑mailgeneratie of rapportstandaardisatie.  

Als je dieper wilt duiken, bekijk dan de documentatie van Aspose over **document merging** en de Ollama API‑referentie voor aangepaste sampling‑parameters.

---

## Conclusie

We hebben je zojuist laten zien hoe je **connect to local llm** vanuit C# kunt gebruiken, **prompt large language model**, **load word document**, **call local llm**, en **rewrite text automatically** — allemaal in één uitvoerbare console‑app. Het patroon schaalt: wissel de prompt, itereer over alinea's, of maak de logica beschikbaar via een ASP.NET‑endpoint. De belangrijkste conclusie is dat lokale AI‑modellen nauw geïntegreerd kunnen worden met klassieke document‑verwerkingsbibliotheken, waardoor je krachtige automatisering krijgt zonder ooit je vertrouwde on‑prem omgeving te verlaten.

Heb je vragen over threading,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}