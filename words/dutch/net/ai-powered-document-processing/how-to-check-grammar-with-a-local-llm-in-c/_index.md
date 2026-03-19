---
category: general
date: 2026-03-19
description: Leer hoe je grammatica controleert in Word met een lokale LLM, registreer
  het model en sla gecorrigeerde documenten op — allemaal in één enkele C#‑tutorial.
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: nl
og_description: Hoe je grammatica controleert in Word met een lokaal LLM, het model
  registreert en gecorrigeerde documenten opslaat—stap‑voor‑stap gids.
og_title: Hoe controleer je grammatica met een lokale LLM in C#
tags:
- Aspose.Words
- AI
- C#
title: Hoe controleer je grammatica met een lokale LLM in C#
url: /nl/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe grammatica te controleren met een lokale LLM in C#

Heb je je ooit afgevraagd **hoe je grammatica** in een Word‑document kunt controleren zonder je tekst naar de cloud te sturen? Je bent niet de enige. Veel ontwikkelaars willen de privacy van een zelf‑gehost model, maar toch AI‑ondersteunde suggesties krijgen. In deze gids lopen we door het registreren van een aangepaste LLM, het configureren van Aspose.Words om deze te gebruiken, en uiteindelijk **hoe je gecorrigeerde** bestanden opslaat — alles in zuivere C#.

We behandelen ook **het opzetten van een lokale llm**, laten zien **hoe je llm‑endpoints registreert**, en demonstreren de exacte stappen om **grammatica te controleren in word**‑documenten. Aan het einde heb je een werkend voorbeeld dat je in elk .NET‑project kunt plaatsen.

## Vereisten

Voordat we beginnen, zorg dat je het volgende hebt:

- .NET 6+ SDK (de code werkt op .NET Core en .NET Framework)
- Visual Studio 2022 of VS Code met C#‑extensies
- Aspose.Words for .NET (v24.12 of nieuwer) — te verkrijgen via NuGet
- Een lokaal draaiende LLM die de OpenAI‑compatibele API ondersteunt (bijv. Ollama op poort 11434)

> **Pro tip:** Als je Ollama gebruikt, start dan `ollama serve`; dit zet automatisch de endpoint `http://localhost:11434/api/generate` op.

## Stap 1 – Hoe een llm te registreren: Voeg het aangepaste model toe aan Aspose.Words

Het eerste wat we moeten doen is Aspose.Words informeren over onze **lokale llm**. Dit gebeurt één keer bij het opstarten van de applicatie.

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

**Waarom dit belangrijk is:** Door het model te registreren geef je Aspose.Words een benoemde handle (`"local-llm"`). Later, wanneer we `CheckGrammar` aanroepen, weet de bibliotheek precies welke endpoint hij moet aanspreken. Als je deze stap overslaat, valt de bibliotheek terug op de ingebouwde cloudservice, waardoor het doel van een private LLM teniet wordt gedaan.

## Stap 2 – Laad het Word‑document dat je wilt analyseren

Nu laden we het bestand in het geheugen. Je kunt elk `.docx`, `.doc` of zelfs `.rtf`‑bestand aanwijzen.

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**Wat er gebeurt:** `Document` is het kernobjectmodel van Aspose.Words. Het parseert het bestand en bouwt een boom van knooppunten (alinea's, tabellen, afbeeldingen, enz.). Hierdoor kan de AI‑engine specifieke tekstreeksen targeten voor grammatica‑analyse.

## Stap 3 – Configureer grammatica‑controle‑opties (het opzetten van een lokale llm)

Hier koppelen we het eerder geregistreerde model aan de grammatica‑controle‑operatie.

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**Waarom we deze opties blootleggen:** Verschillende LLM’s gedragen zich anders. Door `Model` beschikbaar te stellen, laat Aspose.Words je schakelen tussen een lokaal model en een cloud‑model zonder andere code aan te passen. Deze flexibiliteit is essentieel bij **het opzetten van lokale llm**‑omgevingen voor compliance of offline scenario’s.

## Stap 4 – Voer de AI‑gedreven grammatica‑controle uit (grammatica controleren in word)

Met alles aangesloten is de feitelijke grammatica‑controle één enkele regel.

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**Onder de motorkap:** Aspose.Words haalt elke zin op, stuurt deze naar de LLM‑endpoint, ontvangt een JSON‑payload met voorgestelde bewerkingen, en past die bewerkingen vervolgens toe op de documentboom. Het proces wordt hier synchroon uitgevoerd voor de eenvoud; je kunt ook de async‑overload `CheckGrammarAsync` gebruiken voor niet‑blokkende I/O.

## Stap 5 – Hoe gecorrigeerde documenten op te slaan

Nadat de AI zijn magie heeft gedaan, wil je de wijzigingen permanent maken.

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**Wat je kunt verwachten:** Open `checked.docx` in Word en je ziet de grammatica‑problemen gemarkeerd (of automatisch gecorrigeerd, afhankelijk van je `AiGrammarCheckOptions`). Als je tracking hebt ingeschakeld, zie je ook revisiemarkeringen.

## Volledig werkend voorbeeld

Alles bij elkaar, hier is een kant‑klaar console‑app‑voorbeeld:

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

**Verwachte output in de console:**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

Open `checked.docx` en je zou de grammatica‑verbeteringen automatisch toegepast moeten zien.

## Veelgestelde vragen & randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Wat als mijn LLM een API‑sleutel vereist?* | Geef de sleutel door aan `apiKey` in `RegisterModel`. dezelfde code werkt zowel voor services met als zonder sleutel. |
| *Kan ik een ander bestandsformaat gebruiken?* | Zeker. `Document.Save` accepteert `.pdf`, `.html`, `.txt`, enz. Pas gewoon de extensie aan. |
| *Wat als de LLM een fout retourneert?* | Plaats `CheckGrammar` in een try/catch; inspecteer `AiException` voor details. Vaak is het een timeout — overweeg `grammarOptions.Timeout` te verhogen. |
| *Is de operatie thread‑safe?* | De registratiestap is globaal en moet één keer bij opstarten gebeuren. Subsequent `CheckGrammar`‑aanroepen zijn veilig parallel uit te voeren zolang elke thread zijn eigen `Document`‑instantie gebruikt. |

## Volgende stappen

Nu je weet **hoe grammatica te controleren** met een **lokale llm**, kun je het volgende verkennen:

- **Batchverwerking**: Loop over een map met documenten en voer dezelfde pijplijn uit.
- **Aangepaste prompts**: Pas de request‑payload aan door `grammarOptions.PromptTemplate` in te stellen voor stijl‑specifieke controles.
- **Integratie met ASP.NET Core**: Bied een API‑endpoint aan dat geüploade `.docx`‑bestanden accepteert, de grammatica‑controle uitvoert, en het gecorrigeerde bestand terugstuurt.

Deze uitbreidingen stellen je in staat een volledige “grammatica‑als‑een‑service”‑platform te bouwen zonder ooit je eigen infrastructuur te verlaten.

---

*Veel plezier met coderen! Als je ergens tegenaan loopt, laat dan een reactie achter — ik help je graag de configuratie te verfijnen.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}