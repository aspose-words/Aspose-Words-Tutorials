---
category: general
date: 2026-05-04
description: Jak používat LLM k úpravě dokumentů s Aspose – naučte se nahrazovat text
  odstavců, připojit se k lokálnímu LLM a přepisovat text pomocí AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: cs
og_description: Jak použít LLM k úpravě dokumentů pomocí Aspose. Tento průvodce ukazuje,
  jak se připojit k lokálnímu LLM, nahradit text odstavce a přepsat text pomocí AI.
og_title: Jak používat LLM s Aspose.Words – Přepisovat odstavce v C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Jak používat LLM s Aspose.Words – Přepisovat odstavce v C#
url: /cs/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak používat LLM s Aspose.Words – Přepsat odstavce v C#

Už jste se někdy zamýšleli **jak používat LLM** k vylepšení dokumentu Word, aniž byste jej otevírali ručně? Nejste v tom jediní. Mnoho vývojářů narazí na problém, když potřebují *nahradit text odstavce* programově, ale postrádají čistý AI‑řízený workflow.  

V tomto tutoriálu připojíme lokální velký jazykový model, pošleme mu úryvek ze souboru `.docx`, požádáme jej o **přepsání textu pomocí AI** a nakonec uložíme aktualizovaný dokument — vše pomocí Aspose.Words. Na konci budete mít připravenou spustitelnou C# konzolovou aplikaci, která demonstruje celý proces.

> **Co získáte:** kompletní, spustitelný příklad, vysvětlení každého kroku, tipy pro okrajové případy a nápady, jak řešení rozšířit.

## Co budete potřebovat

- **.NET 6+** (nebo .NET Framework 4.7.2 – kód funguje na obou)
- **Aspose.Words for .NET** (NuGet balíček `Aspose.Words`)
- **lokální LLM server** vystavující jednoduchý HTTP `/generate` endpoint (např. Ollama, LMStudio nebo vlastní Flask službu)
- Základní znalost C# a kódu HTTP klienta  

Žádné další SDK nejsou potřeba; vše ostatní je obsaženo v kódu, který napíšeme společně.

## Krok 1: Jak používat LLM k nahrazení textu odstavce

Prvním krokem je identifikovat odstavec, který chceme upravit. Aspose.Words to usnadňuje tím, že poskytuje bohatý objektový model.

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

**Proč je to důležité:**  
Výběr správného uzlu zabraňuje neúmyslnému přepsání nadpisů nebo tabulek. Použitím přístupu **replace paragraph text** zachováme strukturu dokumentu nedotčenou a zasáhneme jen do obsahu, který nás zajímá.

> **Tip:** Pokud má váš dokument sekce proměnné délky, použijte `document.GetChildNodes(NodeType.Paragraph, true)` a LINQ k nalezení odstavce podle jeho textu nebo stylu.

## Krok 2: Připojení k lokálnímu LLM endpointu

Nyní, když máme text, musíme jej poslat LLM. Příklad používá jednoduchou obalovou třídu `LocalLargeLanguageModel`, která skrývá HTTP komunikaci. Klidně ji můžete nahradit voláními `HttpClient`, pokud chcete.

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

**Proč se takto připojujeme:**  
Nastavení **connect to local llm** eliminuje latenci, udržuje data na místě a vyhýbá se nákladům na API. Obalová třída také zjednodušuje následný kód, což nám umožňuje soustředit se na logiku **rewrite text using ai**.

## Krok 3: Přepsání textu pomocí AI s Aspose.Words

S textem odstavce v ruce a připraveným LLM vytvoříme prompt, který modelu přesně řekne, co chceme — přepsat v formálním tónu. Prompt můžete upravit pro jiné styly (přátelský, technický, atd.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Proč to funguje:**  
LLM jsou řízeny promptem; poskytnutí explicitních instrukcí (“Rewrite … in a formal tone”) přináší konzistentní výsledky. Krok **rewrite text using ai** je jádrem tutoriálu — ukazuje, jak lze AI vložit přímo do pracovních postupů s dokumenty.

## Krok 4: Úprava dokumentu a uložení změn

Nyní nahradíme původní runy novým obsahem. Aspose.Words ukládá text do objektů `Run`, takže jejich předchozí vymazání zabraňuje zbytkům formátování.

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

**Poznámka k okrajovým případům:**  
Pokud původní odstavec obsahoval smíšené formátování (tučné, kurzíva), možná budete chtít zachovat styly. V takovém případě vytvořte nový `Run`, zkopírujte nastavení původního `Font` a nastavte jeho `Text` na `revisedText`.

## Kompletní funkční příklad

Níže je celý program, který můžete zkopírovat a vložit do konzolového projektu. Nezapomeňte nejprve nainstalovat NuGet balíček Aspose.Words (`dotnet add package Aspose.Words`).

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

### Očekávaný výstup

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Otevřete `output.docx` — uvidíte, že třetí odstavec nyní obsahuje vylepšenou verzi.

## Časté otázky a úskalí

| Otázka | Odpověď |
|----------|--------|
| **Co když moje LLM vrátí JSON s extra poli?** | Upravte `GenerateText`, aby deserializoval správnou vlastnost, nebo odpověď zpracujte ručně. |
| **Mohu zpracovat více odstavců najednou?** | Ano — iterujte přes `document.FirstSection.Body.Paragraphs` a použijte stejnou logiku promptu, případně přidejte index odstavce do promptu pro kontext. |
| **Můj LLM server používá autentizaci?** | Přidejte hlavičku do `HttpClient` před POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Formátování se po nahrazení ztratí.** | Zachovejte původní nastavení `Run.Font`: vytvořte nový `Run`, zkopírujte `originalRun.Font.Clone()`, a pak nastavte jeho `Text`. |
| **LLM někdy vrací prázdné řetězce.** | Implementujte záložní řešení — pokud `revisedText.Trim().Length == 0`, ponechte původní text nebo zkuste jednodušší prompt. |

## Rozšíření řešení

Nyní, když jste zvládli **how to use llm** pro jeden odstavec, zvažte následující kroky:

- **Batch processing:** Procházet každý odstavec a přepsat jej ve zvoleném stylu (např. „zkrátit celý text“).  
- **Style‑aware rewriting:** Předat do promptu název původního stylu odstavce, aby LLM rozpoznal rozdíl mezi nadpisy a tělem textu.  
- **Integration with a CI pipeline:** Automatizovat vylepšování dokumentů jako součást procesu sestavení dokumentace.  
- **Alternative prompts:** Vyzkoušejte „shrň tento odstavec“ nebo „přelož tento odstavec do španělštiny“, abyste prozkoumali plný potenciál **rewrite text using ai**.

## Závěr

Prošli jsme celý proces **how to use llm** s Aspose.Words: načtení dokumentu, **connect to local llm**, extrakci odstavce, **rewrite text using ai**, **replace paragraph text** a nakonec uložení výsledku. Kód je samostatný, funguje ihned a ukazuje praktický způsob, jak spojit AI s tradiční automatizací dokumentů.

Give it a spin, tweak the prompts, and let

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}