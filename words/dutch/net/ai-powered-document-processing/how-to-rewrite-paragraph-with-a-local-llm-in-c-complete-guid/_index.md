---
category: general
date: 2026-07-03
description: Hoe een alinea herschrijven met een lokale LLM, tekst vervangen, tekst
  genereren en document opslaan — allemaal in C#. Volg deze stapsgewijze tutorial.
draft: false
keywords:
- how to rewrite paragraph
- use local llm
- how to replace text
- how to generate text
- how to save document
language: nl
og_description: Hoe een alinea herschrijven met een lokale LLM, tekst vervangen, tekst
  genereren en document opslaan in C#. Leer het volledige proces stap voor stap.
og_title: Hoe een alinea te herschrijven met een lokale LLM in C#
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: How to rewrite paragraph using a local LLM, replace text, generate
    text and save document—all in C#. Follow this step‑by‑step tutorial.
  headline: How to Rewrite Paragraph with a Local LLM in C# – Complete Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Loop through `document.GetChildNodes(NodeType.Paragraph, true)`
      and apply the same prompt to each paragraph you need to modify.
    question: Can I rewrite multiple paragraphs at once?
  - answer: That usually means the prompt was ambiguous or the model hit a token limit.
      Try simplifying the prompt or increasing the `max_tokens` setting in the endpoint
      configuration.
    question: What if the LLM returns an empty string?
  - answer: Not directly. You’d first need to convert the PDF to a Word document (Aspose.PDF
      → Aspose.Words) or extract the text, rewrite it, then re‑create the PDF.
    question: Does this approach work with PDFs?
  - answer: 'Just change the instruction in the prompt, e.g., `"Rewrite the following
      in a friendly tone:"`. The LLM follows the natural‑language cue you give it.
      ## Next Steps & Related Topics - **How to replace text** in tables, headers,
      or footers (use `NodeType.Table` and similar loops). - **How to generate '
    question: How do I control the tone beyond “formal”?
  type: FAQPage
tags:
- Aspose.Words
- C#
- LLM
title: Hoe een alinea herschrijven met een lokale LLM in C# – Complete gids
url: /nl/net/ai-powered-document-processing/how-to-rewrite-paragraph-with-a-local-llm-in-c-complete-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een alinea herschrijven met een lokale LLM in C# – Complete gids

Heb je je ooit afgevraagd **hoe je een alinea automatisch kunt herschrijven** zonder je gegevens naar de cloud te sturen? Je bent niet de enige. Veel ontwikkelaars hebben een snelle manier nodig om tekst te herformuleren terwijl alles on‑premises blijft, en het goede nieuws is dat je dit kunt doen met een lokale LLM en Aspose.Words.  

In deze gids verbinden we een lokale LLM, laden we een .docx‑bestand, vragen we het model om **tekst te genereren**, vervangen we de oorspronkelijke inhoud, en slaan we uiteindelijk **het document op** terug naar de schijf. Aan het einde heb je een herbruikbare code‑fragment dat je in elk .NET‑project kunt gebruiken.

> **Pro tip:** Als je al Aspose.Words gebruikt voor andere documenttaken, past dit voorbeeld perfect—geen extra bibliotheken nodig naast de LLM‑client.

## Vereisten

- .NET 6+ (of .NET Framework 4.7.2+) geïnstalleerd.
- Aspose.Words voor .NET ≥ 23.11 (de AI‑extensie maakt deel uit van het pakket).
- Een lokaal OpenAI‑compatibel eindpunt (bijv. Ollama, LM Studio, of een zelf‑gehoste vLLM) bereikbaar op `http://localhost:8000/v1/chat/completions`.
- Een API‑sleutel voor de lokale service (vaak een dummy‑string zoals `"my-local-key"`).

> **Waarom dit belangrijk is:** De **lokale LLM gebruiken** aanpak elimineert netwerklatentie en beschermt gevoelige tekst, terwijl Aspose.Words ons een robuuste manier biedt om Word‑documenten te manipuleren.

## Stap 1: Instantie van LargeLanguageModel instellen  

Eerst maken we een `LargeLanguageModel`‑object dat naar ons lokale eindpunt wijst. Dit object abstraheert de HTTP‑aanroep, zodat de rest van de code aanvoelt als een gewone C#‑methodenaanroep.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Create a LargeLanguageModel instance for a local LLM.
var llm = new LargeLanguageModel(
    endpoint: "http://localhost:8000/v1/chat/completions",
    apiKey: "my-local-key");   // Replace with your actual key if needed.
```

*Waarom?* Het éénmalig tot stand brengen van de verbinding houdt de daaropvolgende **tekst genereren**‑aanroepen snel en voorkomt dat de HTTP‑client elke keer opnieuw wordt aangemaakt.

## Stap 2: Brondocument laden  

Vervolgens laden we het Word‑bestand in het geheugen. Aspose.Words leest het volledige document, waardoor we toegang krijgen tot alinea's, tabellen en meer.

```csharp
// Load the .docx file you want to process.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Als het bestand niet wordt gevonden, gooit Aspose een duidelijke `FileNotFoundException`, die je kunt opvangen om een vriendelijke foutmelding te geven.

## Stap 3: Haal de alinea op die je wilt herschrijven  

Voor de demo werken we met de eerste alinea, maar je kunt elke alinea vinden op basis van index, stijl of tekstzoekopdracht.

```csharp
// Retrieve the first paragraph – this is the target for rewriting.
Paragraph originalParagraph = document.FirstParagraph;
```

*Tip:* Om later **tekst te vervangen** in een specifieke alinea, bewaar je een referentie naar het `Paragraph`‑object zoals getoond.

## Stap 4: Vraag de LLM om de alinea te herschrijven  

Nu komt het leuke deel: we sturen de oorspronkelijke tekst naar de LLM en vragen deze om het in een formele toon te herschrijven. De methode `GenerateText` retourneert de respons van het model als een platte string.

```csharp
// Build the prompt – you can tweak the tone or style as needed.
string prompt = $"Rewrite the following for a formal tone:\n{originalParagraph.GetText()}";

// Generate the revised text using the local LLM.
string revisedText = llm.GenerateText(prompt);
```

*Waarom dit werkt:* De LLM ziet de exacte alinea en een duidelijke instructie, zodat de output de gevraagde stijl respecteert. Omdat we een **lokale LLM gebruiken**‑eindpunt aanspreken, verlaat het verzoek nooit je machine.

## Stap 5: Vervang de oorspronkelijke alinea‑tekst  

Met de nieuwe inhoud in de hand, vervangen we de oude tekst. Aspose.Words biedt een krachtige `FindReplaceOptions`‑klasse die ons in staat stelt de bewerking fijn af te stellen, maar de standaardinstelling werkt voor een eenvoudige vervanging.

```csharp
// Perform the replacement – this updates the document in memory.
originalParagraph.Range.Replace(
    originalParagraph.GetText(),
    revisedText,
    new FindReplaceOptions());
```

*Randgeval:* Als de oorspronkelijke alinea verborgen tekens bevat (zoals regeleinden), dan omvat `GetText()` deze, waardoor een exacte overeenkomst wordt gegarandeerd. Als je mismatches opmerkt, overweeg dan om witruimte te trimmen vóór de vervanging.

## Stap 6: Sla het bijgewerkte document op  

Tot slot schrijven we het aangepaste document terug naar de schijf. Je kunt het originele bestand overschrijven of naar een nieuwe locatie schrijven—beide wordt hieronder gedemonstreerd.

```csharp
// Overwrite the original file (use with caution).
document.Save("YOUR_DIRECTORY/input.docx");

// Or save to a new file to keep the original intact.
document.Save("YOUR_DIRECTORY/rewritten.docx");
```

Dat is de volledige **document opslaan**‑stroom. De `Save`‑methode detecteert automatisch het formaat aan de hand van de bestandsextensie, zodat je ook kunt exporteren naar PDF, HTML of ODT met één regel wijziging.

## Volledig werkend voorbeeld  

Alle onderdelen samenvoegen levert een zelfstandige applicatie op die je vanaf de opdrachtregel kunt uitvoeren of kunt inbedden in een grotere service.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize the local LLM client.
        var llm = new LargeLanguageModel(
            endpoint: "http://localhost:8000/v1/chat/completions",
            apiKey: "my-local-key");

        // 2️⃣ Load the document you want to edit.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 3️⃣ Pick the paragraph to rewrite (first paragraph in this case).
        Paragraph para = doc.FirstParagraph;

        // 4️⃣ Ask the LLM to rewrite it in a formal tone.
        string prompt = $"Rewrite the following for a formal tone:\n{para.GetText()}";
        string newText = llm.GenerateText(prompt);

        // 5️⃣ Replace the old text with the new, formal version.
        para.Range.Replace(para.GetText(), newText, new FindReplaceOptions());

        // 6️⃣ Save the updated document.
        doc.Save("YOUR_DIRECTORY/rewritten.docx");

        Console.WriteLine("Paragraph rewritten and document saved successfully.");
    }
}
```

### Verwachte output

Wanneer je het programma uitvoert, print de console:

```
Paragraph rewritten and document saved successfully.
```

En het bestand `rewritten.docx` bevat nu dezelfde inhoud als het origineel, behalve dat de eerste alinea is herschreven in een formele toon—precies wat we vroegen.

## Veelgestelde vragen (FAQ's)

**Q: Kan ik meerdere alinea's tegelijk herschrijven?**  
A: Absoluut. Loop door `document.GetChildNodes(NodeType.Paragraph, true)` en pas dezelfde prompt toe op elke alinea die je moet aanpassen.

**Q: Wat als de LLM een lege string retourneert?**  
A: Dat betekent meestal dat de prompt dubbelzinnig was of dat het model een token‑limiet heeft bereikt. Probeer de prompt te vereenvoudigen of verhoog de `max_tokens`‑instelling in de endpoint‑configuratie.

**Q: Werkt deze aanpak met PDF's?**  
A: Niet rechtstreeks. Je moet eerst de PDF converteren naar een Word‑document (Aspose.PDF → Aspose.Words) of de tekst extraheren, herschrijven en vervolgens de PDF opnieuw maken.

**Q: Hoe kan ik de toon regelen naast “formeel”?**  
A: Verander gewoon de instructie in de prompt, bijv. `"Rewrite the following in a friendly tone:"`. De LLM volgt de natuurlijke‑taal aanwijzing die je geeft.

## Volgende stappen & gerelateerde onderwerpen

- **Hoe tekst te vervangen** in tabellen, kopteksten of voetteksten (gebruik `NodeType.Table` en soortgelijke lussen).  
- **Hoe tekst te genereren** met rijkere prompts, inclusief opsommingstekens of markdown.  
- **Hoe alinea te herschrijven** op voorwaarde van lengte of trefwoorddichtheid (voeg een pre‑check toe vóór het aanroepen van de LLM).  
- Verken **lokale LLM gebruiken**‑prestatietuning: pas temperatuur, top‑p of max‑tokens aan voor meer deterministische output.  
- Leer **document op te slaan** in andere formaten zoals PDF (`doc.Save("out.pdf")`) of HTML (`doc.Save("out.html")`).

---

### Samenvatting

Je weet nu **hoe je een alinea kunt herschrijven** met een lokale LLM, **hoe je tekst kunt vervangen**, **hoe je tekst kunt genereren**, en **hoe je een document kunt opslaan** — alles in een nette, productie‑klare C#‑codefragment. Voel je vrij om te experimenteren met verschillende prompts, meerdere bestanden in batch te verwerken, of deze logica te integreren in een web‑API voor realtime documentbewerking.

Als je tegen problemen aanloopt, laat dan een reactie achter—veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word‑document - Tekst zoeken en vervangen](/words/english/net/find-and-replace-text/)
- [Document opslaan als TXT – Complete C#‑gids om DOCX naar platte tekst te converteren](/words/english/net/programming-with-txtsaveoptions/save-document-as-txt-complete-c-guide-to-convert-docx-to-pla/)
- [Tekst‑watermerk toevoegen in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}