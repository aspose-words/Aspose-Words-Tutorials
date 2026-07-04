---
category: general
date: 2026-05-04
description: Hoe je LLM gebruikt om documenten te bewerken met Aspose – leer alinea‑tekst
  te vervangen, verbinding te maken met een lokale LLM en tekst te herschrijven met
  AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: nl
og_description: Hoe je LLM gebruikt om documenten te bewerken met Aspose. Deze gids
  laat zien hoe je verbinding maakt met een lokale LLM, alinea‑tekst vervangt en tekst
  herschrijft met AI.
og_title: Hoe LLM te gebruiken met Aspose.Words – Paragrafen herschrijven in C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Hoe LLM te gebruiken met Aspose.Words – Alinea’s herschrijven in C#
url: /nl/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe LLM te gebruiken met Aspose.Words – Alinea’s herschrijven in C#

Heb je je ooit afgevraagd **hoe je LLM** kunt gebruiken om een Word‑document te polijsten zonder het handmatig te openen? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur aan wanneer ze *alinea‑tekst* programmatically moeten vervangen, maar geen nette AI‑gedreven workflow hebben.

In deze tutorial verbinden we een lokaal large language model, voeren we een fragment uit een `.docx`‑bestand in, vragen we het om **tekst te herschrijven met AI**, en slaan we uiteindelijk het bijgewerkte document op — allemaal met Aspose.Words. Aan het einde heb je een kant‑klaar C# console‑applicatie die de volledige pijplijn demonstreert.

> **Wat je krijgt:** een compleet, uitvoerbaar voorbeeld, uitleg van elke stap, tips voor randgevallen, en ideeën om de oplossing uit te breiden.

## Wat je nodig hebt

- **.NET 6+** (of .NET Framework 4.7.2 – de code werkt op beide)
- **Aspose.Words for .NET** (NuGet‑pakket `Aspose.Words`)
- Een **local LLM server** die een eenvoudige HTTP `/generate`‑endpoint blootstelt (bijv. Ollama, LMStudio, of een aangepaste Flask‑service)
- Een basiskennis van C# en HTTP‑clientcode  

Er zijn geen extra SDK's nodig; alles anders zit in de code die we samen gaan schrijven.

## Stap 1: Hoe LLM te gebruiken om alinea‑tekst te vervangen

Het eerste wat we moeten doen is de alinea identificeren die we willen aanpassen. Aspose.Words maakt dit een fluitje van een cent door een rijk objectmodel bloot te stellen.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Waarom dit belangrijk is:**  
Het selecteren van de juiste node voorkomt dat je per ongeluk koppen of tabellen overschrijft. Door de **replace paragraph text**‑aanpak te gebruiken, behouden we de documentstructuur intact terwijl we alleen de inhoud aanpassen die ons interesseert.

> **Pro tip:** Als je document secties met variabele lengte heeft, gebruik dan `document.GetChildNodes(NodeType.Paragraph, true)` en LINQ om een alinea te vinden op basis van zijn tekst of stijl.

## Stap 2: Verbinden met een lokale LLM‑endpoint

Nu we de tekst hebben, moeten we deze naar de LLM sturen. Het voorbeeld gebruikt een eenvoudige wrapper‑klasse `LocalLargeLanguageModel` die de HTTP‑logica verbergt. Voel je vrij om deze te vervangen door `HttpClient`‑aanroepen als je dat liever hebt.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Waarom we op deze manier verbinden:**  
Een **connect to local llm**‑opstelling elimineert latentie, houdt gegevens on‑premise, en voorkomt API‑kosten. De wrapper maakt de latere code ook schoner, zodat we ons kunnen concentreren op de **rewrite text using ai**‑logica.

## Stap 3: Tekst herschrijven met AI met Aspose.Words

Met de alinea‑tekst in de hand en de LLM gereed, stellen we een prompt op die het model precies vertelt wat we willen — herschrijven in een formele toon. Je kunt de prompt aanpassen voor andere stijlen (vriendelijk, technisch, enz.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Waarom dit werkt:**  
LLM’s zijn prompt‑gedreven; expliciete instructies geven (“Rewrite … in a formal tone”) levert consistente resultaten op. De **rewrite text using ai**‑stap is het hart van de tutorial – het laat zien hoe AI direct in document‑workflows kan worden ingebed.

## Stap 4: Het document bewerken en wijzigingen opslaan

Nu vervangen we de oorspronkelijke runs door de nieuwe inhoud. Aspose.Words slaat tekst op in `Run`‑objecten, dus eerst wissen voorkomt achtergebleven opmaak‑artefacten.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Opmerking voor randgevallen:**  
Als de oorspronkelijke alinea gemengde opmaak (vet, cursief) bevatte, wil je mogelijk de stijlen behouden. Maak in dat geval een nieuwe `Run`, kopieer de oorspronkelijke `Font`‑instellingen, en stel vervolgens de `Text` in op `revisedText`.

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑en‑plakken in een console‑project. Vergeet niet eerst het Aspose.Words‑NuGet‑pakket te installeren (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Verwachte output

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Open `output.docx` – je zult zien dat de derde alinea nu de gepolijste versie bevat.

## Veelgestelde vragen & valkuilen

| Question | Answer |
|----------|--------|
| **Wat als mijn LLM JSON retourneert met extra velden?** | Pas `GenerateText` aan om de juiste eigenschap te deserialiseren of parse de respons handmatig. |
| **Kan ik meerdere alinea's tegelijk verwerken?** | Ja – iterate over `document.FirstSection.Body.Paragraphs` en pas dezelfde prompt‑logica toe, eventueel een alinea‑index aan de prompt toevoegen voor context. |
| **Gebruikt mijn LLM‑server authenticatie?** | Voeg een header toe aan de `HttpClient` vóór de POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Opmaak gaat verloren na vervanging.** | Behoud de oorspronkelijke `Run.Font`‑instellingen: maak een nieuwe `Run`, kopieer `originalRun.Font.Clone()`, en stel vervolgens de `Text` in. |
| **De LLM retourneert soms lege strings.** | Implementeer een fallback – als `revisedText.Trim().Length == 0`, behoud dan de oorspronkelijke tekst of probeer opnieuw met een eenvoudigere prompt. |

## De oplossing uitbreiden

Nu je **how to use llm** voor een enkele alinea onder de knie hebt, overweeg dan de volgende stappen:

- **Batch processing:** Loop door elke alinea en herschrijf in een gekozen stijl (bijv. “maak alle tekst beknopt”).  
- **Style‑aware rewriting:** Geef de oorspronkelijke alinea‑stijlnamen door in de prompt zodat de LLM koppen versus body‑tekst respecteert.  
- **Integration with a CI pipeline:** Automatiseer het polijsten van documenten als onderdeel van een documentatie‑buildproces.  
- **Alternative prompts:** Probeer “summarize this paragraph” of “translate this paragraph to Spanish” om de volledige kracht van **rewrite text using ai** te verkennen.  

## Conclusie

We hebben de volledige stroom van **how to use llm** met Aspose.Words doorlopen: een document laden, **connect to local llm**, een alinea extraheren, **rewrite text using ai**, **replace paragraph text**, en uiteindelijk het resultaat opslaan. De code is zelf‑containend, werkt direct, en laat een praktische manier zien om AI te combineren met traditionele documentautomatisering.

Probeer het, pas de prompts aan, en laat

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}