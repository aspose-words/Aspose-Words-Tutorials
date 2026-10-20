---
category: general
date: 2026-05-04
description: Hur man använder LLM för att redigera dokument med Aspose – lär dig att
  ersätta stycke­text, ansluta till en lokal LLM och skriva om text med AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: sv
og_description: Hur man använder LLM för att redigera dokument med Aspose. Denna guide
  visar hur man ansluter till en lokal LLM, ersätter stycke‑text och skriver om text
  med AI.
og_title: Hur man använder LLM med Aspose.Words – Skriva om stycken i C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Hur man använder LLM med Aspose.Words – Skriva om stycken i C#
url: /sv/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man använder LLM med Aspose.Words – Skriva om stycken i C#

Har du någonsin undrat **hur man använder LLM** för att putsa ett Word‑dokument utan att öppna det manuellt? Du är inte ensam. Många utvecklare fastnar när de behöver *ersätta stycke‑text* programatiskt men saknar ett rent AI‑drivet arbetsflöde.  

I den här handledningen kopplar vi upp en lokal stor språkmodell, matar den med ett utdrag från en `.docx`‑fil, ber den **skriva om text med AI**, och sparar slutligen det uppdaterade dokumentet – allt med Aspose.Words. När du är klar har du en färdig C#‑konsolapp som demonstrerar hela pipeline:n.

> **Vad du får:** ett komplett, körbart exempel, förklaringar av varje steg, tips för kantfall och idéer för att utöka lösningen.

## Vad du behöver

- **.NET 6+** (eller .NET Framework 4.7.2 – koden fungerar på båda)
- **Aspose.Words for .NET** (NuGet‑paket `Aspose.Words`)
- En **lokal LLM‑server** som exponerar ett enkelt HTTP‑endpoint `/generate` (t.ex. Ollama, LMStudio eller en egen Flask‑tjänst)
- Grundläggande kunskap om C# och HTTP‑klientkod  

Inga extra SDK:er krävs; allt annat lever i den kod vi skriver tillsammans.

## Steg 1: Hur man använder LLM för att ersätta stycke‑text

Det första vi måste göra är att identifiera det stycke vi vill ändra. Aspose.Words gör detta enkelt genom att exponera en rik objektsmodell.

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

**Varför detta är viktigt:**  
Att välja rätt nod förhindrar att du av misstag skriver över rubriker eller tabeller. Genom att använda **replace paragraph text**‑metoden behåller vi dokumentets struktur intakt och ändrar bara det innehåll vi bryr oss om.

> **Proffstips:** Om ditt dokument har sektioner med variabel längd, använd `document.GetChildNodes(NodeType.Paragraph, true)` och LINQ för att lokalisera ett stycke via dess text eller stil.

## Steg 2: Anslut till ett lokalt LLM‑endpoint

Nu när vi har texten måste vi skicka den till LLM:n. Exemplet använder en enkel wrapper‑klass `LocalLargeLanguageModel` som döljer HTTP‑detaljerna. Byt gärna ut den mot direkta `HttpClient`‑anrop om du föredrar det.

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

**Varför vi ansluter på detta sätt:**  
En **connect to local llm**‑uppsättning eliminerar latens, håller data på plats och undviker API‑kostnader. Wrappern gör också den efterföljande koden renare, så vi kan fokusera på logiken för **rewrite text using ai**.

## Steg 3: Skriva om text med AI med Aspose.Words

Med stycke‑texten i handen och LLM:n redo, bygger vi en prompt som talar om för modellen exakt vad vi vill – skriva om i en formell ton. Du kan justera prompten för andra stilar (vänlig, teknisk osv.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Varför detta fungerar:**  
LLM:er är prompt‑drivna; tydliga instruktioner (“Rewrite … in a formal tone”) ger konsekventa resultat. Steget **rewrite text using ai** är hjärtat i handledningen – det visar hur AI kan integreras direkt i dokumentarbetsflöden.

## Steg 4: Redigera dokumentet och spara ändringarna

Nu ersätter vi de ursprungliga runs med det nya innehållet. Aspose.Words lagrar text i `Run`‑objekt, så att rensa dem först undviker kvarvarande formateringsartefakter.

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

**Kantfalls‑anmärkning:**  
Om det ursprungliga stycket innehöll blandad formatering (fet, kursiv) kan du vilja bevara stilarna. Skapa i så fall ett nytt `Run`, kopiera de ursprungliga `Font`‑inställningarna och sätt sedan dess `Text` till `revisedText`.

## Fullt fungerande exempel

Nedan är hela programmet som du kan kopiera‑klistra in i ett konsolprojekt. Kom ihåg att först installera Aspose.Words‑NuGet‑paketet (`dotnet add package Aspose.Words`).

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

### Förväntad output

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Öppna `output.docx` – du kommer att se att det tredje stycket nu visar den putsade versionen.

## Vanliga frågor & fallgropar

| Fråga | Svar |
|----------|--------|
| **Vad händer om min LLM returnerar JSON med extra fält?** | Anpassa `GenerateText` så att den deserialiserar rätt egenskap eller parsar svaret manuellt. |
| **Kan jag bearbeta flera stycken samtidigt?** | Ja – iterera över `document.FirstSection.Body.Paragraphs` och tillämpa samma prompt‑logik, eventuellt med ett stycke‑index i prompten för kontext. |
| **Min LLM‑server använder autentisering?** | Lägg till en header i `HttpClient` innan POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Formateringen försvinner efter ersättningen.** | Bevara de ursprungliga `Run.Font`‑inställningarna: skapa ett nytt `Run`, kopiera `originalRun.Font.Clone()`, och sätt sedan dess `Text`. |
| **LLM:n returnerar ibland tomma strängar.** | Implementera en fallback – om `revisedText.Trim().Length == 0`, behåll originaltexten eller gör ett nytt försök med en enklare prompt. |

## Utöka lösningen

Nu när du har bemästrat **how to use llm** för ett enskilt stycke, fundera på följande nästa steg:

- **Batch‑bearbetning:** Loopa igenom varje stycke och skriv om i en vald stil (t.ex. “make all text concise”).  
- **Stil‑medveten omskrivning:** Skicka med det ursprungliga styckets stilnamn i prompten så att LLM:n kan respektera rubriker kontra brödtext.  
- **Integration i en CI‑pipeline:** Automatisera dokumentputsning som en del av en dokumentations‑byggprocess.  
- **Alternativa prompts:** Prova “summarize this paragraph” eller “translate this paragraph to Spanish” för att utforska hela kraften i **rewrite text using ai**.

## Slutsats

Vi har gått igenom hela flödet för **how to use llm** med Aspose.Words: ladda ett dokument, **connect to local llm**, extrahera ett stycke, **rewrite text using ai**, **replace paragraph text**, och slutligen spara resultatet. Koden är självständig, fungerar direkt ur lådan och visar ett praktiskt sätt att kombinera AI med traditionell dokumentautomatisering.

Ge det ett försök, justera promptarna, och låt

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}