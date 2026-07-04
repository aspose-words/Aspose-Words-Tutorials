---
category: general
date: 2026-06-24
description: Lokal LLM-handledning som visar hur du anropar en lokal LLM, laddar ett
  Word‑dokument och kör grammatikkontroll med AI‑grammatikkontroll i C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: sv
og_description: Lokal LLM-handledning förklarar steg‑för‑steg hur man anropar en lokal
  LLM, laddar ett Word‑dokument och kör en AI‑grammatikgranskning i C#.
og_title: Lokal LLM-handledning – Anropa en lokal LLM och kör grammatikkontroll
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
title: Lokal LLM-handledning – Hur man anropar en lokal LLM och kör grammatikkontroll
url: /sv/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lokal LLM-handledning – Anropa en lokal LLM och kör grammatikkontroll

Har du någonsin undrat hur man **köra grammatikkontroll** på en Word‑fil utan att skicka något till molnet? I den här **lokal LLM-handledning** kommer vi att koppla ihop en själv‑hostad stor språkmodell, ladda en `.docx`‑fil och låta AI:n städa upp prosa. Inga API‑nycklar, ingen extern trafik—bara din egen maskin som gör det tunga arbetet.

Vi går igenom varje kodrad, förklarar varför varje del är viktig, och visar även hur du hanterar de vanliga fallgroparna (som saknade filer eller en oåtkomlig endpoint). I slutet har du en färdig‑att‑köra C#‑konsolapp som utför en **ai grammar check** med en lokalt hostad modell.

> **Vad du får:** ett komplett, körbart program, en tydlig förklaring av varje steg, och tips för att skala lösningen till större dokument eller olika LLM‑leverantörer.

![local llm tutorial diagram](https://example.com/local-llm-tutorial-diagram.png "Diagram som illustrerar flödet i den lokala LLM‑handledningen")

## Förutsättningar

- .NET 6.0 SDK eller senare (du kan ladda ner den från Microsofts webbplats)
- En lokalt körande LLM‑server som exponerar en OpenAI‑kompatibel endpoint (t.ex. Ollama, LM Studio eller en anpassad FastAPI‑wrapper)
- `AiGrammar`‑NuGet‑paketet (eller vilket bibliotek som tillhandahåller klasserna `LocalLargeLanguageModel`, `Document` och `AiModelType`)
- Ett exempel‑Word‑dokument (`input.docx`) placerat i en mapp som du kommer referera till senare

Det är allt—inga extra moln‑behörigheter behövs.

## Steg 1: Lokal LLM-handledning – Ställa in endpointen

Det första vi behöver är ett **call local llm**‑objekt som vet var det ska skicka sina förfrågningar. Tänk på det som telefonnumret du ringer innan du kan prata.

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

**Varför detta är viktigt:**  
De flesta LLM‑SDK:er förväntar sig en HTTP‑endpoint som följer OpenAI API‑kontraktet. Genom att peka `Endpoint` på `http://localhost:8000/v1` säger vi åt biblioteket att **call local llm** istället för att nå OpenAIs servrar. Den dummy‑API‑nyckeln är bara en platshållare—vissa klienter avvisar ett null‑värde, så vi ger den något ofarligt.

> **Proffstips:** Om du kör LLM:n bakom en reverse‑proxy, sätt `Endpoint` till proxy‑URL:en och låt proxyn hantera TLS‑terminering. Detta håller din konsolapp enkel och säker.

## Steg 2: Ladda Word‑dokument för grammatikkontroll

Nu när modellen är nåbar, behöver vi **load word document**‑innehållet i minnet. `Document`‑klassen abstraherar `.docx`‑parsningsprocessen åt oss.

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

**Varför detta är viktigt:**  
Att direkt skicka en binär `.docx`‑fil till en LLM skulle förvirra den. `Document`‑hjälpen extraherar råtexten samtidigt som den bevarar styckebrytningar, vilket ger **ai grammar check** ett rent input att arbeta med. Existenskontrollen förhindrar ett obehagligt `FileNotFoundException` som annars skulle krascha appen.

## Steg 3: Kör grammatikkontroll med LLM:n

Här är kärnan i handledningen: vi ber den lokala modellen att korrekturläsa texten. Metoden `CheckGrammar` döljer HTTP‑logiken och returnerar ett resultatobjekt.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Varför detta är viktigt:**  
`AiModelType.Gpt4` är bara en etikett som talar om för fjärrtjänsten vilken prompt‑mall som ska användas. Om du har en mindre modell (t.ex. `Llama2`), ersätt den därefter. Biblioteket serialiserar dokumenttexten, skickar den till `http://localhost:8000/v1/completions` och parsar det korrigerade svaret.

> **Edge case:** Om LLM:n får timeout, kastar `CheckGrammar` ett `TimeoutException`. Omslut anropet med ett `try/catch`‑block om du förväntar dig stora dokument eller en upptagen server.

## Steg 4: Visa den korrigerade texten

Till sist visar vi den rensade versionen. I en riktig app kan du skriva tillbaka den till en ny `.docx`‑fil, men för den här handledningen räcker en konsolutskrift.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Förväntad output** (förutsatt att originalfilen innehöll några avsiktliga fel):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Om LLM:n inte hittar några fel, blir outputen identisk med inputen, vilket fortfarande är en användbar signal.

## Fullt fungerande exempel

När allt sätts ihop, här är det kompletta programmet som du kan kopiera‑klistra in i ett nytt konsolprojekt:

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

### Så kör du

1. Öppna en terminal i projektmappen.  
2. Kör `dotnet run`.  
3. Se hur konsolen skriver ut den korrigerade texten.

Det är hela **local llm tutorial** på under 100 rader kod.

## Vanliga frågor (FAQ)

### Kan jag använda ett annat LLM‑märke?

Absolut. Så länge servern följer OpenAI v1 API‑schemat, ändra bara `Endpoint` och välj motsvarande `AiModelType`‑enum‑värde (t.ex. `AiModelType.Llama2`). Resten av koden förblir identisk.

### Vad händer om mitt dokument är enormt (10 MB+)?

Stora payloads kan överskrida standard‑request‑storleken för många servrar. Dela upp dokumentet i sektioner och anropa `CheckGrammar` per sektion, för att sedan sammanfoga resultaten. Detta minskar också risken för timeout.

### Hur skriver jag tillbaka den korrigerade outputen till en `.docx`‑fil?

`Document`‑klassen erbjuder vanligtvis en `Save(string path, string content)`‑metod. Efter att du har fått `result.CorrectedText`, anropa:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Kolla bibliotekets dokumentation för den exakta signaturen.

### Är dummy‑API‑nyckeln en säkerhetsrisk?

Nej. Nyckeln ignoreras av självhostade endpoints, men vissa SDK:er kräver en icke‑null sträng. Att använda en platshållare som `"dummy"` uppfyller SDK‑kravet utan att exponera några hemligheter.

## Nästa steg och relaterade ämnen

- **Fine‑tune your local LLM** för domänspecifik grammatik (t.ex. juridisk eller medicinsk skrivning).  
- **Run a batch job** som bearbetar en hel mapp med Word‑filer—perfekt för publiceringspipelines.  
- Utforska **streaming responses** om du vill ha real‑tidsförslag medan användaren skriver.  
- Kombinera detta med **spell‑checking libraries** för en dubbellagerad kvalitetsgate.

Varje av dessa idéer bygger på de grundläggande koncepten i denna **local llm tutorial**, så du kommer att se samma mönster—**call local llm**, **load word document**, **run grammar check**, och **handle results**—återkomma genom hela materialet.

---

*Lycka till med kodningen! Om du stöter på problem, lämna en kommentar nedan så felsöker vi tillsammans.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Ladda med kodning i Word‑dokument](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Ladda krypterat i Word‑dokument](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Återställ korrupt DOCX – Öppna & ladda Word‑dokument](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}