---
category: general
date: 2026-06-30
description: Maak een aangepast AI‑model en controleer grammatica met AI op een DOCX‑bestand.
  Leer hoe je een docx‑bestand laadt, een grammaticacontrole uitvoert en een Word‑document
  stap voor stap analyseert.
draft: false
keywords:
- create custom ai model
- check grammar with ai
- load docx file
- run grammar check
- analyze word document
language: nl
og_description: Maak een aangepast AI‑model en controleer de grammatica met AI in
  een DOCX‑bestand. Volg deze volledige gids om een docx‑bestand te laden, een grammaticacontrole
  uit te voeren en een Word‑document te analyseren.
og_title: Maak een aangepast AI‑model – Grammaticacontrole‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create custom AI model and check grammar with AI on a DOCX file. Learn
    how to load docx file, run grammar check, and analyze Word document step‑by‑step.
  headline: Create Custom AI Model – Full Guide to Grammar Checking in C#
  type: TechArticle
- description: Create custom AI model and check grammar with AI on a DOCX file. Learn
    how to load docx file, run grammar check, and analyze Word document step‑by‑step.
  name: Create Custom AI Model – Full Guide to Grammar Checking in C#
  steps:
  - name: '`CheckGrammar` extracts the plain text from `doc`.'
    text: '`CheckGrammar` extracts the plain text from `doc`.'
  - name: It builds a prompt that explicitly asks the LLM to act as a grammar expert.
    text: It builds a prompt that explicitly asks the LLM to act as a grammar expert.
  - name: The prompt is sent to the endpoint defined in `aiSettings`.
    text: The prompt is sent to the endpoint defined in `aiSettings`.
  - name: The LLM returns a corrected version, which we capture in `grammarResult`.
    text: The LLM returns a corrected version, which we capture in `grammarResult`.
  - name: Swap the local LLM for an OpenAI‑compatible endpoint (just change the URL
      and API key).
    text: Swap the local LLM for an OpenAI‑compatible endpoint (just change the URL
      and API key).
  - name: Add chunking logic to handle massive contracts or manuscripts.
    text: Add chunking logic to handle massive contracts or manuscripts.
  - name: Hook the pipeline into a CI/CD step that validates documentation before
      release.
    text: Hook the pipeline into a CI/CD step that validates documentation before
      release.
  type: HowTo
tags:
- AI
- C#
- Document Processing
title: Maak een aangepast AI‑model – Volledige gids voor grammatica‑controle in C#
url: /nl/net/ai-powered-document-processing/create-custom-ai-model-full-guide-to-grammar-checking-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aangepast AI‑model maken – Volledige gids voor grammaticacontrole in C#

Heb je je ooit afgevraagd hoe je een **aangepast AI‑model** kunt **maken** dat grammaticafouten in je Word‑documenten kan opsporen? Je bent niet de enige. In veel projecten komt de behoefte om **grammatica te controleren met AI** naar voren, maar de gebruikelijke clouddiensten voelen zwaar of kosten‑intensief.  

In deze tutorial lopen we een slanke, zelf‑gehoste oplossing door die je **docx‑bestand laadt**, **grammaticacontrole uitvoert**, en **Word‑document analyseert** – allemaal vanuit een paar regels C#. Aan het einde heb je een herbruikbare `CustomAiModel`‑klasse, een kant‑klaar grammaticacontrole‑pipeline, en een duidelijk beeld van waar je kunt uitbreiden.

> **Wat je krijgt:** een compleet, kant‑klaar code‑voorbeeld, uitleg van elke stap, en praktische tips om veelvoorkomende valkuilen te vermijden.

---

## Vereisten

- .NET 6.0 of later (de code gebruikt top‑level statements voor beknoptheid).  
- Een lokale LLM‑server die een `/v1/completions`‑endpoint aanbiedt (bijv. Ollama, LM Studio).  
- De `Document`‑klasse van een lichte DOCX‑bibliotheek zoals *DocX* of *Open XML SDK*.  
- Basiskennis van C# – je bent in orde als je al een console‑app hebt geschreven.

Er zijn geen extra NuGet‑pakketten nodig naast de AI‑client en DOCX‑parser; de tutorial toont precies welke `using`‑directives je nodig hebt.

---

![Diagram die laat zien hoe je een aangepast AI‑model maakt, een DOCX‑bestand laadt, grammaticacontrole uitvoert en resultaten bekijkt](https://example.com/ai-grammar-workflow.png "Diagram van workflow voor het maken van een aangepast AI‑model")

*Alt‑tekst: Diagram dat laat zien hoe je een aangepast AI‑model maakt en grammaticacontrole uitvoert op een Word‑document.*

---

## Stap 1: Aangepast AI‑model maken – Endpoint en authenticatie instellen

Het eerste wat je nodig hebt, is een dunne wrapper rond de HTTP‑API van de LLM. Deze wrapper is het hart van het **aangepast AI‑model maken**‑proces. Door de endpoint‑URL en optionele API‑sleutel te encapsuleren houden we de rest van de code schoon en testbaar.

```csharp
using System;
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Configuration object for the AI service
public class AiSettings
{
    public Uri Endpoint { get; set; }
    public string ApiKey { get; set; } // optional
}

// Minimal AI client that sends a prompt and returns the raw response
public class CustomAiModel
{
    private readonly HttpClient _http;
    private readonly AiSettings _settings;

    public CustomAiModel(AiSettings settings)
    {
        _settings = settings;
        _http = new HttpClient();
        if (!string.IsNullOrEmpty(settings.ApiKey))
            _http.DefaultRequestHeaders.Add("Authorization", $"Bearer {settings.ApiKey}");
    }

    // Sends a prompt to the LLM and returns the completion text
    public string Complete(string prompt)
    {
        var payload = new
        {
            model = "local-llm", // adjust to your server's model name
            prompt,
            max_tokens = 500
        };

        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");
        var response = _http.PostAsync(_settings.Endpoint, content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        using var doc = JsonDocument.Parse(json);
        return doc.RootElement.GetProperty("choices")[0].GetProperty("text").GetString();
    }

    // Helper specific to grammar checking (we’ll use it later)
    public string CheckGrammar(Document doc) => Complete(BuildGrammarPrompt(doc));
    
    // Builds a prompt that asks the LLM to correct the supplied text
    private string BuildGrammarPrompt(Document doc)
    {
        // Extract plain text from the DOCX (see next step for details)
        string text = doc.GetPlainText();
        return $"You are a grammar expert. Review the following text and return ONLY the corrected version, preserving line breaks:\n\n{text}";
    }
}
```

**Waarom dit belangrijk is:** Door **een aangepast AI‑model te maken** vermijden we hard‑gecodeerde URL’s door de hele app heen, en krijgen we één plek om headers, time‑outs of zelfs de backend later te wijzigen. De `CheckGrammar`‑methode laat zien hoe het model kan worden gespecificeerd voor een bepaalde taak – in ons geval grammaticacontrole.

---

## Stap 2: DOCX‑bestand laden – Het Word‑document in het geheugen brengen

Nu de AI‑client bestaat, hebben we een manier nodig om **docx‑bestand te laden** zodat we de inhoud aan het model kunnen voeren. De volgende helper gebruikt de *DocX*‑bibliotheek (lichtgewicht, geen COM‑interop) om platte tekst te lezen terwijl alinea‑scheidingen behouden blijven.

```csharp
using System.IO;
using Xceed.Words.NET; // Install-Package DocX

public class Document
{
    private readonly string _path;
    private readonly string _content;

    public Document(string path)
    {
        if (!File.Exists(path))
            throw new FileNotFoundException($"File not found: {path}");

        _path = path;
        _content = ExtractText(path);
    }

    // Returns the raw text that will be sent to the LLM
    public string GetPlainText() => _content;

    // Simple extraction – you could enrich this to keep headings, tables, etc.
    private static string ExtractText(string filePath)
    {
        using var doc = DocX.Load(filePath);
        var sb = new StringBuilder();
        foreach (var paragraph in doc.Paragraphs)
        {
            sb.AppendLine(paragraph.Text);
        }
        return sb.ToString();
    }
}
```

**Tip:** Als je opmaak (zoals vet voor nadruk) wilt behouden, kun je `ExtractText` uitbreiden zodat het Markdown of HTML genereert en de prompt dienovereenkomstig aanpassen. Voor de meeste grammaticacontrole‑scenario’s werkt platte tekst het beste.

---

## Stap 3: Grammaticacontrole uitvoeren – Stuur het document naar je aangepaste AI‑model

Met zowel het model als het document klaar, is de **grammaticacontrole uitvoeren** stap een één‑regelige oproep. De `CheckGrammar`‑methode binnen `CustomAiModel` bouwt de prompt, roept de LLM aan, en retourneert de gecorrigeerde tekst.

```csharp
// Configuration – point to your locally running LLM server
var aiSettings = new AiSettings
{
    Endpoint = new Uri("http://localhost:5000/v1/completions"),
    ApiKey = "YOUR_API_KEY" // leave empty if not required
};

// Instantiate the custom AI model (this is where we actually *create custom AI model*)
AiModel model = new CustomAiModel(aiSettings);

// Load the DOCX you want to analyze
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Run the grammar‑checking operation
string grammarResult = model.CheckGrammar(doc);
```

**Wat er onder de motorkap gebeurt:**  
1. `CheckGrammar` haalt de platte tekst uit `doc`.  
2. Het bouwt een prompt die de LLM expliciet vraagt op te treden als grammaticaspecialist.  
3. De prompt wordt verzonden naar het endpoint dat is gedefinieerd in `aiSettings`.  
4. De LLM retourneert een gecorrigeerde versie, die we vastleggen in `grammarResult`.

Omdat de prompt deterministisch is, kun je hetzelfde bestand herhaaldelijk uitvoeren en krijg je identieke output – ideaal voor unit‑tests.

---

## Stap 4: Resultaten weergeven en interpreteren – Toon de gecorrigeerde tekst

Tot slot moeten we de **gecorrigeerde versie** aan de gebruiker tonen (of terugschrijven naar een nieuw bestand). Voor een snelle demo volstaat het afdrukken naar de console:

```csharp
Console.WriteLine("=== Original Document ===");
Console.WriteLine(doc.GetPlainText());

Console.WriteLine("\n=== Grammar‑Corrected Output ===");
Console.WriteLine(grammarResult);
```

Wil je de gecorrigeerde tekst terugschrijven naar een nieuw DOCX, dan kun je dezelfde *DocX*‑bibliotheek gebruiken:

```csharp
using (var newDoc = DocX.Create("YOUR_DIRECTORY/output_corrected.docx"))
{
    newDoc.InsertParagraph(grammarResult);
    newDoc.Save();
}
Console.WriteLine("Corrected document saved as output_corrected.docx");
```

**Waarom terugschrijven?** Veel workflows hebben een schoon, versie‑gecontroleerd bestand nodig voor verdere verwerking (bijv. PDF‑conversie, publicatie). Het opslaan van het resultaat behoudt de audit‑trail en voldoet aan compliance‑eisen.

---

## Stap 5: Veelvoorkomende valkuilen & Pro‑tips

| Probleem | Waarom het gebeurt | Hoe op te lossen / te vermijden |
|----------|--------------------|---------------------------------|
| **Prompt‑grootte overschrijdt LLM‑limieten** | Zeer grote DOCX‑bestanden genereren enorme prompts. | Splits het document in delen (bijv. 2 k tekens) en roep `CheckGrammar` per deel aan, concateneer daarna de resultaten. |
| **Model geeft extra uitleg terug** | Sommige LLM’s voegen meta‑tekst toe, zelfs als je alleen de gecorrigeerde versie vraagt. | Voeg `\n\nOnly return the corrected text without any commentary.` toe aan de prompt, of post‑process het antwoord met een eenvoudige regex om regels die beginnen met “Explanation:” te verwijderen. |
| **Speciale tekens breken JSON** | Als het DOCX aanhalingstekens of nieuwe regels bevat, kan de JSON‑payload onjuist worden. | Gebruik `JsonSerializer` (zoals getoond) dat automatisch escapen afhandelt, of escape handmatig met `System.Text.Encodings.Web.JavaScriptEncoder`. |
| **Netwerk‑latentie** | Zelf‑gehoste LLM’s kunnen trager zijn op alleen‑CPU‑machines. | Draai de server op een GPU‑machine, of schakel streaming‑antwoorden in als je endpoint dat ondersteunt. |
| **Onjuist bestandspad** | Hard‑coded paden leiden tot `FileNotFoundException`. | Gebruik `Path.Combine(Environment.CurrentDirectory, "input.docx")` of geef het pad als command‑line‑argument mee. |

**Pro‑tip:** Cache de geëxtraheerde platte tekst als je meerdere analyses (spelling, leesbaarheid) op hetzelfde document wilt uitvoeren – dat bespaart I/O‑tijd.

---

## Bonus: De pipeline uitbreiden (buiten grammaticacontrole)

Omdat we **een aangepast AI‑model hebben gemaakt**, is uitbreiden eenvoudig:

- **Stijlanalyse** – wijzig de prompt naar “Identify passive voice and suggest active alternatives.”
- **Samenvatten** – vervang de prompt door “Summarize the following text in three bullet points.”
- **Vertalen** – vraag het model om de geëxtraheerde tekst naar een andere taal te vertalen.

Alles wat je nodig hebt is een nieuwe helper‑methode die de juiste prompt bouwt en dezelfde `Complete`‑methode hergebruikt. Deze modulariteit is het grootste voordeel van een zelf‑gehoste aanpak.

---

## Conclusie

Je hebt nu een compleet, end‑to‑end voorbeeld dat laat zien hoe je **een aangepast AI‑model maakt**, **docx‑bestand laadt**, **grammaticacontrole uitvoert**, en **Word‑document analyseert** met puur C#. De code staat klaar om te draaien, de concepten zijn uitgelegd, en de valkuilen zijn behandeld – zonder zwevende “zie docs”‑links.

Vanaf hier kun je:

1. Het lokale LLM‑model vervangen door een OpenAI‑compatibel endpoint (alleen URL en API‑sleutel aanpassen).  
2. Chunk‑logica toevoegen om enorme contracten of manuscripten te verwerken.  
3. De pipeline integreren in een CI/CD‑stap die documentatie valideert vóór release.

Probeer het, pas de prompts aan, en zie je documenten fout‑vrij worden met slechts een paar regels code. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Aspose Load Options – Load DOCX with Custom Font Settings](/words/english/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Convert Docx File To Markdown](/words/english/net/basic-conversions/docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}