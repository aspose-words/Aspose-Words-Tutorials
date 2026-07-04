---
category: general
date: 2026-06-24
description: Lokální LLM tutoriál, který vám ukáže, jak zavolat lokální LLM, načíst
  dokument Word a provést kontrolu gramatiky pomocí AI kontroly gramatiky v C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: cs
og_description: Lokální LLM tutoriál krok za krokem vysvětluje, jak zavolat lokální
  LLM, načíst dokument Word a spustit AI kontrolu gramatiky v C#.
og_title: Lokální LLM tutoriál – Zavolejte lokální LLM a spusťte kontrolu gramatiky
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
title: Lokální LLM tutoriál – Jak zavolat lokální LLM a spustit kontrolu gramatiky
url: /cs/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lokální LLM tutoriál – Zavolejte lokální LLM a spusťte kontrolu gramatiky

Už jste se někdy zamysleli, jak **spustit kontrolu gramatiky** na souboru Word, aniž byste něco posílali do cloudu? V tomto **lokálním LLM tutoriálu** připojíme samostatně hostovaný velký jazykový model, načteme soubor `.docx` a necháme AI upravit text. Žádné API klíče, žádný externí provoz – jen váš vlastní počítač, který udělá těžkou práci.

Projdeme každý řádek kódu, vysvětlíme, proč je každá část důležitá, a dokonce vám ukážeme, jak zvládnout běžné úskalí (jako chybějící soubory nebo nedostupný endpoint). Na konci budete mít připravenou spustitelnou C# konzolovou aplikaci, která provádí **AI kontrolu gramatiky** pomocí lokálně hostovaného modelu.

> **Co získáte:** kompletní spustitelný program, jasné vysvětlení každého kroku a tipy, jak škálovat řešení na větší dokumenty nebo různé poskytovatele LLM.

![lokální LLM tutoriál diagram](https://example.com/local-llm-tutorial-diagram.png "Diagram znázorňující tok lokálního LLM tutoriálu")

## Požadavky

- .NET 6.0 SDK nebo novější (můžete si jej stáhnout z webu Microsoftu)
- Lokálně běžící LLM server vystavující OpenAI‑kompatibilní endpoint (např. Ollama, LM Studio nebo vlastní FastAPI wrapper)
- NuGet balíček `AiGrammar` (nebo jakákoli knihovna poskytující třídy `LocalLargeLanguageModel`, `Document` a `AiModelType`)
- Ukázkový Word dokument (`input.docx`) umístěný ve složce, na kterou později odkážete

To je vše – žádné další cloudové přihlašovací údaje nejsou potřeba.

## Krok 1: Lokální LLM tutoriál – Nastavení endpointu

Prvním, co potřebujeme, je objekt **call local llm**, který ví, kam posílat své požadavky. Představte si ho jako telefonní číslo, které vytočíte, než můžete mluvit.

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

**Proč je to důležité:**  
Většina LLM SDK očekává HTTP endpoint, který dodržuje kontrakt OpenAI API. Nastavením `Endpoint` na `http://localhost:8000/v1` říkáme knihovně, aby **call local llm** místo volání serverů OpenAI. Dummy API klíč je jen zástupný – některé klienty odmítají null hodnotu, takže mu dáváme něco neškodného.

> **Pro tip:** Pokud provozujete LLM za reverzním proxy, nastavte `Endpoint` na URL proxy a nechte proxy řešit TLS terminaci. Tím zůstane vaše konzolová aplikace jednoduchá a bezpečná.

## Krok 2: Načtení Word dokumentu pro kontrolu gramatiky

Nyní, když je model dostupný, potřebujeme **load word document** obsah načíst do paměti. Třída `Document` pro nás abstrahuje parsování `.docx`.

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

**Proč je to důležité:**  
Přímé předání binárního souboru `.docx` LLM by ho zmátlo. Pomocník `Document` extrahuje čistý text při zachování odstavcových zalomení, což poskytuje **ai grammar check** čistý vstup. Kontrola existence zabraňuje nepříjemné `FileNotFoundException`, která by jinak aplikaci zhavarovala.

## Krok 3: Spuštění kontroly gramatiky pomocí LLM

Zde je jádro tutoriálu: požádáme lokální model, aby text opravil. Metoda `CheckGrammar` skrývá HTTP komunikaci a vrací objekt s výsledkem.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Proč je to důležité:**  
`AiModelType.Gpt4` je jen štítek, který říká vzdálené službě, jakou šablonu promptu použít. Pokud máte menší model (např. `Llama2`), nahraďte jej odpovídajícím. Knihovna serializuje text dokumentu, pošle jej na `http://localhost:8000/v1/completions` a zpracuje opravený výstup.

> **Okrajový případ:** Pokud LLM vyprší časový limit, `CheckGrammar` vyhodí `TimeoutException`. Zabalte volání do `try/catch` bloku, pokud očekáváte velké dokumenty nebo vytížený server.

## Krok 4: Výstup opraveného textu

Nakonec zobrazíme vyčištěnou verzi. Ve skutečné aplikaci ji můžete zapsat zpět do nového souboru `.docx`, ale pro tento tutoriál stačí výpis do konzole.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Očekávaný výstup** (předpokládáme, že původní soubor obsahoval několik úmyslných chyb):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Pokud LLM nenašel žádné chyby, výstup bude identický s vstupem, což je stále užitečný signál.

## Kompletní funkční příklad

Spojením všeho dohromady získáte kompletní program, který můžete zkopírovat a vložit do nového konzolového projektu:

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

### Jak spustit

1. Otevřete terminál ve složce projektu.  
2. Spusťte `dotnet run`.  
3. Sledujte, jak konzole vypíše opravený text.

To je celý **lokální LLM tutoriál** v méně než 100 řádcích kódu.

## Často kladené otázky (FAQ)

### Můžu použít jinou značku LLM?

Určitě. Dokud server respektuje schéma OpenAI v1 API, stačí změnit `Endpoint` a vybrat odpovídající hodnotu výčtu `AiModelType` (např. `AiModelType.Llama2`). Zbytek kódu zůstane stejný.

### Co když je můj dokument obrovský (10 MB+)?

Velké payloady mohou překročit výchozí velikost požadavku mnoha serverů. Rozdělte dokument na sekce a zavolejte `CheckGrammar` pro každou sekci, poté výsledky spojte. Tím se také sníží pravděpodobnost timeoutu.

### Jak zapíšu opravený výstup zpět do souboru `.docx`?

Třída `Document` obvykle poskytuje metodu `Save(string path, string content)`. Po získání `result.CorrectedText` zavolejte:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Podívejte se do dokumentace knihovny pro přesnou signaturu.

### Je dummy API klíč bezpečnostním rizikem?

Ne. Klíč je ignorován samohostovanými endpointy, ale některé SDK vyžadují nenulový řetězec. Použití zástupného řetězce jako `"dummy"` splní požadavky SDK, aniž by odhalilo jakékoli tajemství.

## Další kroky a související témata

- **Doladit svůj lokální LLM** pro doménově specifickou gramatiku (např. právní nebo medicínské psaní).  
- **Spustit dávkovou úlohu**, která zpracuje celý adresář Word souborů – skvělé pro publikační pipeline.  
- Prozkoumat **streamingové odpovědi**, pokud chcete návrhy v reálném čase během psaní uživatelem.  
- Kombinovat to s **knihovnami pro kontrolu pravopisu** pro dvojitou vrstvu kvality.

Každý z těchto nápadů staví na základních konceptech pokrytých v tomto **lokálním LLM tutoriálu**, takže po celou dobu uvidíte opakování stejných vzorů – **call local llm**, **load word document**, **run grammar check** a **handle results**.

---

*Šťastné kódování! Pokud narazíte na problém, zanechte komentář níže a společně ho vyřešíme.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Načíst s kódováním ve Word dokumentu](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Načíst šifrovaný Word dokument](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Obnovit poškozený DOCX – Otevřít a načíst Word dokument](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}