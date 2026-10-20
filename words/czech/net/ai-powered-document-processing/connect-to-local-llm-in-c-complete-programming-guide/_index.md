---
category: general
date: 2026-04-28
description: Připojte se k lokálnímu LLM z C# a požádejte velký jazykový model, aby
  načetl Word dokument, zavolejte lokální LLM a automaticky přepište text. Kód krok
  po kroku je zahrnut.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: cs
og_description: Připojte se k lokálnímu LLM z C# a zjistěte, jak zadat prompt velkému
  jazykovému modelu, načíst Word dokument, zavolat lokální LLM a automaticky přepsat
  text během několika minut.
og_title: Připojení k lokálnímu LLM v C# – Kompletní programovací průvodce
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Připojení k lokálnímu LLM v C# – Kompletní programovací průvodce
url: /cs/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Připojení k lokálnímu LLM v C# – Kompletní programovací průvodce

Už jste někdy potřebovali **připojit se k lokálnímu llm** z .NET aplikace a přemýšleli, jak ji nechat komunikovat se souborem Word? Nejste v tom sami. V tomto průvodci projdeme celý proces – připojení k lokálnímu llm, **prompt large language model**, načtení Word dokumentu, **call local llm** a nakonec **rewrite text automatically**. Na konci budete mít spustitelný příklad, který přemění libovolný odstavec do formálního tónu bez jakýchkoli externích API klíčů.

## Co tento tutoriál pokrývá

Začneme instalací potřebných NuGet balíčků, poté spustíme jednoduchý lokální LLM endpoint (např. Ollama na portu 11434). Pak načteme soubor `.docx` pomocí Aspose.Words, pošleme odstavec LLM, získáme přepsanou verzi a zapíšeme ji zpět do stejného dokumentu. Také uvidíte, jak řešit běžné úskalí – prázdné odstavce, asynchronní uvolňování a zvláštnosti kódování – aby kód fungoval v produkci, ne jen jako demo.

### Požadavky

- .NET 6.0 SDK nebo novější (můžete také použít .NET 8, pokud chcete)
- Visual Studio 2022 nebo VS Code s rozšířením C#
- **Aspose.Words for .NET** (bezplatná zkušební verze funguje dobře)
- Lokálně hostovaný LLM, který podporuje kontrakt `/api/generate` (např. Ollama, LMStudio)
- Základní znalost async/await v C#

> **Pro tip:** Pokud jste ještě nenainstalovali Ollama, spusťte `ollama serve` a stáhněte model pomocí `ollama pull llama3`. Výchozí HTTP endpoint bude `http://localhost:11434/api/generate`.

---

## Krok 1: Instalace potřebných balíčků

Nejprve přidejte do projektu NuGet balíčky Aspose.Words a Aspose.Words.AI.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Tyto knihovny nám poskytují schopnost **load word document** a tenký obal pro **call local llm** bez ručního sestavování HTTP požadavků.

---

## Krok 2: Připojení k lokálnímu LLM endpointu

Připojení k lokálně hostovanému modelu je tak jednoduché, jako vytvořit instanci `LocalLargeLanguageModel`. Konstruktor očekává úplnou URL generovacího endpointu.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Proč obalujeme endpoint do třídy? `LocalLargeLanguageModel` za vás řeší JSON serializaci, opakování požadavků a streamování odpovědí – takže se můžete soustředit na logiku promptu místo manipulace s `HttpClient`.

---

## Krok 3: Načtení zdrojového Word dokumentu

Dále načteme dokument do paměti. Aspose.Words podporuje prakticky každý Word formát, takže `Document` zpracuje `input.docx` bez nutnosti mít nainstalovaný Office.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Pokud potřebujete pracovat se streamem (např. soubor nahraný přes ASP.NET), stačí nahradit cestu k souboru objektem `MemoryStream` a předat jej konstruktoru `Document`.

---

## Krok 4: Extrahování textu aktuálního odstavce

Použijeme `DocumentBuilder` k procházení dokumentu. V tomto příkladu přepisujeme **první odstavec**, ale můžete iterovat přes `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` a zpracovat více.

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

Operátor `?.` zabraňuje `NullReferenceException`, pokud je dokument prázdný. Jedná se o jeden z těch **edge cases**, který nováčky často překvapí.

---

## Krok 5: Prompt LLM pro přepsání odstavce

Nyní skutečně **prompt large language model**. Prompt je v prosté angličtině; obal jej pošle jako JSON na lokální endpoint.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Proč formulovat požadavek tímto způsobem? LLM reagují nejlépe na jasné, jednorázové instrukce. Přidání nového řádku po dvojtečce oddělí instrukci od obsahu a snižuje šanci, že model vrátí samotný prompt.

**Očekávaný výstup** – Pokud `originalParagraph` byl `"Hey, what's up?"`, LLM může vrátit:

> “Good day, how may I assist you?”

Výsledek můžete ověřit vytištěním:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Krok 6: Vložení přepsaného textu zpět do dokumentu

S novým textem v ruce nahradíme starý odstavec. `DocumentBuilder.Writeln` zapíše nový řádek a posune kurzor dopředu, což je ideální pro přidání. Pokud potřebujete *nahradit* přesně ten samý odstavec, můžete před zápisem použít `docBuilder.CurrentParagraph.RemoveAllChildren()`.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Oba přístupy jsou ukázány, abyste si mohli vybrat ten, který lépe odpovídá vašemu workflow.

---

## Krok 7: Uložení aktualizovaného dokumentu

Nakonec změny uložíme do nového souboru. Aspose.Words automaticky zvolí formát podle přípony souboru.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Otevřete `output.docx` ve Wordu a uvidíte, že odstavec nyní zní formálně.

---

## Kompletní funkční příklad

Níže je **complete, self‑contained program**. Zkopírujte jej do konzolového projektu, obnovte NuGet balíčky a spusťte – žádná další konfigurace není potřeba kromě běžícího lokálního LLM.

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

### Co očekávat při spuštění

1. Konzole vypíše původní a přepsaný odstavec.  
2. `output.docx` se objeví vedle `input.docx`.  
3. Po otevření souboru uvidíte nový formální odstavec vložený za původní (nebo nahrazený, pokud jste použili alternativní kód).

---

## Řešení běžných okrajových případů

| Situace | Řešení |
|-----------|----------|
| **Prázdný nebo jen s bílými znaky odstavec** | Zkontrolujte `string.IsNullOrWhiteSpace` před odesláním promptu (viz Krok 3). |
| **LLM vrátí chybu nebo prázdný řetězec** | Zabalte `PromptAsync` do `try/catch` a v případě chyby použijte původní text. |
| **Více odstavců vyžaduje přepsání** | Procházejte `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` a aplikujte stejnou logiku promptu. |
| **Velké dokumenty způsobují latenci** | Sesbírejte odstavce do dávky a pošlete je v jednom požadavku (prompt až 4 KB na volání). |
| **Ne‑ASCII znaky se zkomolí** | Ujistěte se, že LLM endpoint používá UTF-8 (většina moderních modelů to dělá). |

---

## Další kroky a související témata

- **Prompt large language model** s podrobnějšími instrukcemi (např. stylové příručky, omezení délky).  
- Použijte **call local llm** ve webovém API k vystavení automatizace dokumentů jako služby.  
- Prozkoumejte **load word document** v paralelních streamech pro scénáře s vysokou propustností.  
- Kombinujte tento přístup s **rewrite text automatically** pro hromadnou generaci e‑mailů nebo standardizaci reportů.  

Pokud se chcete ponořit hlouběji, podívejte se na dokumentaci Aspose k **document merging** a na Ollama API reference pro vlastní parametry vzorkování.

---

## Závěr

Právě jsme vám ukázali, jak **connect to local llm** z C#, **prompt large language model**, **load word document**, **call local llm** a **rewrite text automatically** – vše v jedné spustitelné konzolové aplikaci. Tento vzor je škálovatelný: můžete měnit prompt, iterovat přes odstavce nebo exponovat logiku přes ASP.NET endpoint. Hlavní výsledek je, že lokální AI modely lze úzce integrovat s klasickými knihovnami pro zpracování dokumentů, což vám poskytne výkonnou automatizaci bez opuštění důvěryhodného on‑prem prostředí.

Máte otázky ohledně vláken,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}