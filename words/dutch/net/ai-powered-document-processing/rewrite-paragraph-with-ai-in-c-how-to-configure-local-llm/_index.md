---
category: general
date: 2026-06-17
description: Herformuleer de alinea met AI met behulp van Aspose.Words en leer hoe
  je een lokale LLM configureert voor naadloze integratie in je .NET‑app.
draft: false
keywords:
- rewrite paragraph with ai
- how to configure local llm
- Aspose.Words AI integration
- local LLM endpoint setup
- C# document automation
language: nl
og_description: Herschrijf de alinea met AI in C# en ontdek hoe je lokale LLM‑eindpunten
  kunt configureren voor betrouwbare on‑premise verwerking.
og_title: Paragraaf herschrijven met AI – Snelle gids voor het configureren van een
  lokale LLM
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Rewrite paragraph with AI using Aspose.Words and learn how to configure
    local LLM for seamless integration in your .NET app.
  headline: Rewrite Paragraph with AI in C# – How to Configure Local LLM
  type: TechArticle
- description: Rewrite paragraph with AI using Aspose.Words and learn how to configure
    local LLM for seamless integration in your .NET app.
  name: Rewrite Paragraph with AI in C# – How to Configure Local LLM
  steps:
  - name: Aspose.Words extracts the raw text of the target paragraph.
    text: Aspose.Words extracts the raw text of the target paragraph.
  - name: It builds a request payload that includes the user‑provided `prompt`.
    text: It builds a request payload that includes the user‑provided `prompt`.
  - name: The payload is sent to the local LLM via the `BaseUrl`.
    text: The payload is sent to the local LLM via the `BaseUrl`.
  - name: The model returns the revised text, which Aspose.Words returns as a `string`.
    text: The model returns the revised text, which Aspose.Words returns as a `string`.
  type: HowTo
- questions:
  - answer: Yes. Loop over the desired indices and call `RewriteParagraph` for each.
      Remember to respect rate limits of your LLM—local servers are usually generous,
      but large batches can still overload the CPU.
    question: Can I rewrite multiple paragraphs in one go?
  - answer: For very large files (> 500 MB) consider using `LoadOptions` with `LoadFormat`
      set to `Auto` and enable `LoadOptions.LoadFormat` = `LoadFormat.Docx`. The AI
      call still works on a per‑paragraph basis, keeping memory usage modest.
    question: Does Aspose.Words support streaming large documents?
  - answer: 'Try simplifying the instruction or adding examples. For instance, `"Rewrite
      the following sentence in a formal tone: {text}"` can give the model a clearer
      context. ## Next Steps & Related Topics - **Fine‑tune your local model** for
      domain‑specific rewriting (e.g., legal contracts). - **Combine multi'
    question: What if my local LLM doesn’t understand the prompt?
  type: FAQPage
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Paragraaf herschrijven met AI in C# – Hoe een lokale LLM te configureren
url: /nl/net/ai-powered-document-processing/rewrite-paragraph-with-ai-in-c-how-to-configure-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Paragraaf herschrijven met AI in C# – Complete gids

Heb je je ooit afgevraagd hoe je **paragraaf herschrijven met AI** kunt doen zonder je gegevens naar de cloud te sturen? Je bent niet de enige. Veel ontwikkelaars verlangen naar de controle over een lokaal groot taalmodel (LLM) terwijl ze toch genieten van het gemak van de AI‑helpers van Aspose.Words.  

In deze tutorial lopen we je stap voor stap door een hands‑on voorbeeld dat een specifieke alinea in een .docx‑bestand herschrijft, en laten we je vervolgens zien **hoe je lokale LLM**‑eindpunten zoals Ollama of LM Studio configureert. Aan het einde heb je een zelfstandige C#‑console‑app die communiceert met een lokaal gehost model, de tekst herschrijft en het resultaat afdrukt — allemaal zonder je machine te verlaten.

## Vereisten

- .NET 6+ SDK (je kunt ook .NET Framework 4.8 targeten als je dat liever hebt)
- Aspose.Words for .NET (NuGet‑pakket `Aspose.Words` ≥ 23.12)
- Een lokale LLM‑server die een OpenAI‑compatibele API aanbiedt (Ollama, LM Studio, of vergelijkbaar)
- Basiskennis van C# — niets bijzonders, alleen genoeg om een console‑app te draaien

> **Pro tip:** Als je nog geen lokale LLM hebt geïnstalleerd, start Ollama met `ollama serve` en haal een model (`ollama pull llama2`). De server luistert standaard op `http://localhost:11434/v1`, wat overeenkomt met de onderstaande code.

## Stap 1: Laad het bron‑document  

Het eerste wat we nodig hebben is een Word‑document om mee te werken. Aspose.Words maakt dit een één‑regel‑code.

```csharp
using Aspose.Words;

// Load the DOCX file from the file system
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Waarom dit belangrijk is:* Het `Document`‑object vertegenwoordigt het volledige bestand in het geheugen, waardoor we willekeurige toegang hebben tot elke alinea, tabel of afbeelding. Het vroeg laden van het bestand zorgt ervoor dat de AI‑engine de omringende context kan raadplegen als je later besluit meer dan één alinea te herschrijven.

## Stap 2: Stel de lokale LLM‑configuratie in  

Hier beantwoorden we **hoe je lokale llm configureert** voor Aspose.Words AI. De bibliotheek verwacht een `AiModelConfig`‑object dat het OpenAI‑API‑contract weerspiegelt.

```csharp
using Aspose.Words.AI;

var aiConfig = new AiModelConfig
{
    BaseUrl = "http://localhost:11434/v1", // Ollama or LM Studio endpoint
    ModelName = "my-llm",                  // The model identifier you pulled
    // Optional settings you might tweak:
    // ApiKey = "YOUR_API_KEY",           // Not needed for local servers
    // Temperature = 0.7,                // Controls randomness
    // MaxTokens = 512                   // Limits response length
};
```

**Uitleg:**  
- `BaseUrl` wijst naar het HTTP‑adres waar je LLM luistert.  
- `ModelName` geeft de server aan welk model moet worden aangeroepen.  
- De optionele velden laten je de generatie fijn afstemmen zonder server‑side standaardinstellingen te wijzigen.

Als je **LM Studio** gebruikt, is de standaard‑URL `http://localhost:1234/v1`. Vervang deze gewoon — er zijn geen code‑aanpassingen nodig, behalve de URL‑string.

## Stap 3: Herschrijf een specifieke alinea  

Nu het leuke gedeelte — het model vertellen om alinea 2 (nul‑gebaseerde index) te herschrijven met een aangepaste prompt.

```csharp
// Ask the AI to rewrite paragraph #2 with a formal, concise tone
string rewrittenParagraph = document.AI.RewriteParagraph(
    paragraphIndex: 2,
    config: aiConfig,
    prompt: "Make the tone more formal and concise."
);

// Output the result to the console
Console.WriteLine(rewrittenParagraph);
```

**Wat gebeurt er onder de motorkap?**  
1. Aspose.Words haalt de ruwe tekst van de doel‑alinea op.  
2. Het bouwt een request‑payload die de door de gebruiker opgegeven `prompt` bevat.  
3. De payload wordt verzonden naar de lokale LLM via de `BaseUrl`.  
4. Het model retourneert de herziene tekst, die Aspose.Words teruggeeft als een `string`.

### Randgevallen & Tips

- **Ongeldige index:** Als `paragraphIndex` de alinea‑telling van het document overschrijdt, wordt een `ArgumentOutOfRangeException` gegooid. Bescherm hiertegen met `if (paragraphIndex < document.GetChildNodes(NodeType.Paragraph, true).Count)`.
- **Lege prompt:** Een lege `prompt` valt terug op het standaardgedrag van het model, dat mogelijk simpelweg de invoer echoot. Lever altijd een duidelijke instructie.
- **Netwerkproblemen:** Omdat we een lokaal HTTP‑eindpunt aanspreken, leidt een verkeerd getypte `BaseUrl` tot een `WebException`. Plaats de aanroep in een `try/catch` en log de URL voor snelle foutopsporing.

## Stap 4: Bewaar de wijzigingen (optioneel)  

Als je wilt dat de herschreven alinea de oorspronkelijke tekst in het document vervangt, kun je de alinea‑node direct bijwerken.

```csharp
// Retrieve the paragraph node
Paragraph target = (Paragraph)document.GetChildNodes(NodeType.Paragraph, true)[2];

// Replace its text with the AI‑generated version
target.Range.Text = rewrittenParagraph;

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");
```

Nu bevat het bestand op schijf de formele, beknopte versie, klaar voor verdere verwerking of distributie.

## Volledig werkend voorbeeld

Hieronder staat een compleet, kant‑klaar console‑programma dat alles samenvoegt. Het bevat foutafhandeling en commentaar voor duidelijkheid.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;

namespace RewriteParagraphDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source DOCX
            string inputPath = "YOUR_DIRECTORY/input.docx";
            Document document;
            try
            {
                document = new Document(inputPath);
                Console.WriteLine($"Loaded document: {inputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // 2️⃣ Configure the local LLM (adjust URL/model as needed)
            var aiConfig = new AiModelConfig
            {
                BaseUrl = "http://localhost:11434/v1", // Ollama default
                ModelName = "my-llm",
                Temperature = 0.6
            };

            // 3️⃣ Choose which paragraph to rewrite (zero‑based)
            int paragraphIndex = 2;
            var paragraphs = document.GetChildNodes(NodeType.Paragraph, true);
            if (paragraphIndex < 0 || paragraphIndex >= paragraphs.Count)
            {
                Console.WriteLine("Paragraph index out of range.");
                return;
            }

            // 4️⃣ Ask the AI to rewrite it
            string prompt = "Make the tone more formal and concise.";
            string rewrittenParagraph;
            try
            {
                rewrittenParagraph = document.AI.RewriteParagraph(
                    paragraphIndex: paragraphIndex,
                    config: aiConfig,
                    prompt: prompt);
                Console.WriteLine("\n--- Rewritten Paragraph ---");
                Console.WriteLine(rewrittenParagraph);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"AI request failed: {ex.Message}");
                return;
            }

            // 5️⃣ (Optional) Replace the original paragraph and save
            Paragraph target = (Paragraph)paragraphs[paragraphIndex];
            target.Range.Text = rewrittenParagraph;
            string outputPath = "YOUR_DIRECTORY/output.docx";
            document.Save(outputPath);
            Console.WriteLine($"\nDocument saved with changes: {outputPath}");
        }
    }
}
```

**Verwachte output** (ervan uitgaande dat de oorspronkelijke alinea luidde “We need to finish the report soon.”):

```
--- Rewritten Paragraph ---
The report should be completed promptly.
```

Het opgeslagen `output.docx` bevat nu die verfijnde zin in plaats van de oorspronkelijke.

## Veelgestelde vragen

**V: Kan ik meerdere alinea's in één keer herschrijven?**  
A: Ja. Loop over de gewenste indices en roep `RewriteParagraph` voor elk aan. Houd rekening met de snelheidslimieten van je LLM — lokale servers zijn meestal ruimhartig, maar grote batches kunnen de CPU nog steeds overbelasten.

**V: Ondersteunt Aspose.Words het streamen van grote documenten?**  
A: Voor zeer grote bestanden (> 500 MB) kun je overwegen `LoadOptions` te gebruiken met `LoadFormat` ingesteld op `Auto` en `LoadOptions.LoadFormat` = `LoadFormat.Docx` in te schakelen. De AI‑aanroep werkt nog steeds per alinea, waardoor het geheugenverbruik bescheiden blijft.

**V: Wat als mijn lokale LLM de prompt niet begrijpt?**  
A: Probeer de instructie te vereenvoudigen of voorbeelden toe te voegen. Bijvoorbeeld, `"Rewrite the following sentence in a formal tone: {text}"` kan het model een duidelijkere context geven.

## Volgende stappen & gerelateerde onderwerpen

- **Fijn‑stem je lokale model** voor domeinspecifieke herschrijvingen (bijv. juridische contracten).  
- **Combineer meerdere AI‑functies** zoals `SummarizeDocument` of `GenerateCoverPage` van Aspose.Words AI.  
- **Beveilig je eindpunt** met een API‑sleutel of TLS als je de LLM buiten localhost blootstelt.  
- Verken **batch‑verwerking** met `Parallel.ForEach` om grootschalige documenttransformaties te versnellen.

---

Dat is het! Je weet nu hoe je **paragraaf herschrijven met AI** kunt doen met Aspose.Words en de exacte stappen **hoe je lokale llm configureert** voor een soepele on‑premise workflow. Probeer het, pas de prompt aan, en zie hoe je documenten direct verfijnder worden.  

Als je ergens tegenaan loopt, laat dan een reactie achter of raadpleeg de Aspose.Words‑documentatie voor diepere API‑inzichten. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Randen en schaduwen toepassen op alinea in Aspose.Words voor .NET](/words/english/net/document-styling/apply-border-and-shading/)
- [Titel & beschrijving toevoegen aan tabel in Word met Aspose.Words](/words/english/net/working-with-table-styles-and-formatting/table-tittle-and-description/)
- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}