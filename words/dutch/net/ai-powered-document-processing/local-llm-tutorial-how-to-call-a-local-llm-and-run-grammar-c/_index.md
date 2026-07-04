---
category: general
date: 2026-06-24
description: Lokale LLM‑tutorial die laat zien hoe je een lokale LLM aanroept, een
  Word‑document laadt en een grammaticacontrole uitvoert met AI‑grammaticacontrole
  in C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: nl
og_description: Lokale LLM‑tutorial legt stap voor stap uit hoe je een lokale LLM
  aanroept, een Word‑document laadt en een AI‑grammatica‑controle uitvoert in C#.
og_title: Lokale LLM‑tutorial – Roep een lokale LLM op en voer een grammaticacontrole
  uit
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Lokale LLM‑tutorial – Hoe een lokale LLM aan te roepen en een grammaticacontrole
  uit te voeren
url: /nl/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lokale LLM Tutorial – Roep een Lokale LLM aan en Voer Grammaticacontrole uit

Heb je je ooit afgevraagd hoe je **grammaticacontrole** op een Word‑bestand kunt uitvoeren zonder iets naar de cloud te sturen? In deze **lokale llm tutorial** gaan we een zelf‑gehost groot taalmodel aansluiten, een `.docx`‑bestand laden, en de AI de tekst laten opruimen. Geen API‑sleutels, geen extern verkeer—alleen je eigen machine die het zware werk doet.

We lopen elke regel code stap voor stap door, leggen uit waarom elk onderdeel belangrijk is, en laten zelfs zien hoe je de gebruikelijke valkuilen (zoals ontbrekende bestanden of een ontoegankelijk eindpunt) kunt afhandelen. Aan het einde heb je een kant‑klaar C# console‑applicatie die een **ai grammar check** uitvoert met een lokaal gehost model.

> **Wat je krijgt:** een volledig, uitvoerbaar programma, een duidelijke uitleg van elke stap, en tips om de oplossing op te schalen naar grotere documenten of andere LLM‑providers.

![local llm tutorial diagram](https://example.com/local-llm-tutorial-diagram.png "Diagram illustrating the flow of the local llm tutorial")

## Vereisten

- .NET 6.0 SDK of later (je kunt het downloaden van de site van Microsoft)
- Een lokaal draaiende LLM‑server die een OpenAI‑compatibel eindpunt blootlegt (bijv. Ollama, LM Studio, of een aangepaste FastAPI‑wrapper)
- Het `AiGrammar` NuGet‑pakket (of welke bibliotheek ook `LocalLargeLanguageModel`, `Document`, en `AiModelType`‑klassen levert)
- Een voorbeeld‑Word‑document (`input.docx`) geplaatst in een map die je later zult refereren

Dat is alles—geen extra cloud‑referenties nodig.

## Stap 1: Lokale LLM Tutorial – Het Instellen van het Eindpunt

Het eerste wat we nodig hebben is een **call local llm** object dat weet waar het zijn verzoeken naartoe moet sturen. Beschouw het als het telefoonnummer dat je belt voordat je kunt praten.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Waarom dit belangrijk is:**  
De meeste LLM‑SDK's verwachten een HTTP‑eindpunt dat voldoet aan het OpenAI‑API‑contract. Door `Endpoint` te wijzen op `http://localhost:8000/v1` vertellen we de bibliotheek om **call local llm** te gebruiken in plaats van contact op te nemen met de servers van OpenAI. De dummy‑API‑sleutel is slechts een tijdelijke aanduiding—sommige clients weigeren een null‑waarde, dus geven we iets onschadelijks.

> **Pro tip:** Als je de LLM achter een reverse proxy draait, stel `Endpoint` in op de proxy‑URL en laat de proxy de TLS‑terminatie afhandelen. Dit houdt je console‑app eenvoudig en veilig.

## Stap 2: Laad Word‑document voor Grammaticacontrole

Nu het model bereikbaar is, moeten we de inhoud van het **load word document** in het geheugen laden. De `Document`‑klasse abstraheert het `.docx`‑parsen voor ons.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Waarom dit belangrijk is:**  
Het rechtstreeks voeden van een binair `.docx`‑bestand aan een LLM zou het in de war brengen. De `Document`‑helper haalt de ruwe tekst eruit terwijl alinea‑onderbrekingen behouden blijven, wat de **ai grammar check** een schone invoer geeft om mee te werken. De bestaan‑check voorkomt een vervelende `FileNotFoundException` die de app anders zou laten crashen.

## Stap 3: Voer Grammaticacontrole uit met de LLM

Hier is het hart van de tutorial: we vragen het lokale model om de tekst te proeflezen. De methode `CheckGrammar` verbergt de HTTP‑logica en retourneert een result‑object.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Waarom dit belangrijk is:**  
`AiModelType.Gpt4` is slechts een label dat de externe service vertelt welke prompt‑template te gebruiken. Als je een kleiner model hebt (bijv. `Llama2`), vervang het dan overeenkomstig. De bibliotheek serialiseert de documenttekst, stuurt deze naar `http://localhost:8000/v1/completions`, en parseert de gecorrigeerde output.

> **Randgeval:** Als de LLM een time‑out krijgt, gooit `CheckGrammar` een `TimeoutException`. Plaats de oproep in een `try/catch`‑blok als je grote documenten of een drukke server verwacht.

## Stap 4: Geef de Gecorrigeerde Tekst weer

Tenslotte tonen we de opgeschoonde versie. In een echte app zou je het terug kunnen schrijven naar een nieuw `.docx`‑bestand, maar voor deze tutorial is een console‑dump voldoende.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Verwachte output** (ervan uitgaande dat het oorspronkelijke bestand enkele opzettelijke fouten bevatte):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Als de LLM geen fouten vond, zal de output identiek zijn aan de invoer, wat nog steeds een nuttig signaal is.

## Volledig Werkend Voorbeeld

Alles samenvoegend, hier is het volledige programma dat je kunt kopiëren‑plakken in een nieuw console‑project:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Hoe uit te voeren

1. Open een terminal in de projectmap.  
2. Voer `dotnet run` uit.  
3. Bekijk hoe de console de gecorrigeerde tekst afdrukt.

Dat is de volledige **local llm tutorial** in minder dan 100 regels code.

## Veelgestelde Vragen (FAQ)

### Kan ik een ander LLM‑merk gebruiken?

Zeker. Zolang de server het OpenAI v1 API‑schema respecteert, wijzig je gewoon `Endpoint` en kies je de bijbehorende `AiModelType`‑enum‑waarde (bijv. `AiModelType.Llama2`). De rest van de code blijft identiek.

### Wat als mijn document enorm is (10 MB+)?

Grote payloads kunnen de standaard request‑grootte van veel servers overschrijden. Splits het document in secties en roep `CheckGrammar` per sectie aan, en voeg vervolgens de resultaten samen. Dit verkleint ook de kans op een time‑out.

### Hoe schrijf ik de gecorrigeerde output terug naar een `.docx`‑bestand?

De `Document`‑klasse biedt meestal een `Save(string path, string content)`‑methode. Nadat je `result.CorrectedText` hebt, roep je aan:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Bekijk de documentatie van de bibliotheek voor de exacte handtekening.

### Is de dummy API‑sleutel een beveiligingsrisico?

Nee. De sleutel wordt genegeerd door zelf‑gehoste eindpunten, maar sommige SDK's eisen een niet‑null string. Het gebruik van een placeholder zoals `"dummy"` voldoet aan de SDK zonder enige geheimen bloot te stellen.

## Volgende Stappen en Gerelateerde Onderwerpen

- **Fine‑tune your local LLM** voor domeinspecifieke grammatica (bijv. juridisch of medisch schrijven).  
- **Run a batch job** die een volledige map met Word‑bestanden verwerkt—ideaal voor publicatie‑pijplijnen.  
- Verken **streaming responses** als je realtime suggesties wilt terwijl de gebruiker typt.  
- Combineer dit met **spell‑checking libraries** voor een dubbele kwaliteitscontrole.

Elk van deze ideeën bouwt voort op de kernconcepten die in deze **local llm tutorial** worden behandeld, dus je zult dezelfde patronen terugzien—**call local llm**, **load word document**, **run grammar check**, en **handle results**—die door het geheel heen terugkomen.

---

*Veel plezier met coderen! Als je een probleem tegenkomt, laat dan een reactie achter en we lossen het samen op.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Load Encrypted In Word Document](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}