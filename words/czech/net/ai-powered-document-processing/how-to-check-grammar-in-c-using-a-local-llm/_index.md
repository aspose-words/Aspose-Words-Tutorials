---
category: general
date: 2026-02-21
description: Jak zkontrolovat gramatiku v C# načtením souboru DOCX, odesláním jeho
  textu do lokálního LLM a zápisem opravené verze zpět. Obsahuje návod, jak používat
  LLM a číst text z Word dokumentu.
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: cs
og_description: Jak zkontrolovat gramatiku v C# načtením DOCX, odesláním jeho textu
  do lokálního LLM a zápisem opravené verze zpět. Naučte se používat LLM a číst text
  z Word dokumentu.
og_title: Jak zkontrolovat gramatiku v C# pomocí lokálního LLM
tags:
- C#
- LLM
- Aspose.Words
title: Jak zkontrolovat gramatiku v C# pomocí lokálního LLM
url: /cs/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak kontrolovat gramatiku v C# pomocí lokálního LLM

Už jste se někdy zamýšleli **jak kontrolovat gramatiku** ve Word dokumentu, aniž byste opustili svůj C# projekt? Nejste jediní — vývojáři se stále ptají: „Mohu automatizovat korekturu pomocí stejného kódu, který pohání chatboty?“ Krátká odpověď je ano. Načtením DOCX, extrakcí jeho textu a předáním lokálně hostovanému velkému jazykovému modelu (LLM) můžete získat okamžité opravy gramatiky a výsledek zapsat přímo zpět do souboru.

V tomto tutoriálu projdeme celý proces: čtení `.docx` pomocí **load docx in c#**, volání **how to use llm** pro opravu gramatiky a nakonec uložení vyčištěného dokumentu. Na konci budete mít připravenou konzolovou aplikaci, která dělá přesně to, co potřebujete — žádné ruční kopírování, žádné externí API, jen čistý C# a lokální LLM endpoint.

> **Co budete potřebovat**
> - .NET 6.0 nebo novější (kód funguje i na .NET Framework, ale .NET 6 je ideální)
> - Knihovnu [Aspose.Words for .NET](https://products.aspose.com/words/net/) (zdarma zkušební verze stačí pro testování)
> - Běžící LLM server, který vystavuje jednoduchý endpoint `CheckGrammar(string)` (např. Ollama, LM Studio nebo vlastní FastAPI wrapper)
> - Základní znalost async/await (volitelné, ale doporučené)

Pokud se ptáte, **proč by vás to mělo zajímat**, pomyslete na čas, který strávíte ručním opravováním překlepů v generovaných reportech. Automatizace tohoto kroku nejenže urychlí pipeline, ale také zajistí konzistenci napříč desítkami dokumentů. Pojďme na to.

---

## Jak kontrolovat gramatiku – Přehled

Než se pustíme do kódu, zde je rychlý plán:

1. **Vytvořit klienta**, který bude komunikovat s lokálním LLM endpointem.  
2. **Načíst Word dokument** pomocí Aspose.Words — to je klasický způsob, jak **read word document text** v C#.  
3. **Odeslat surový text** LLM a získat opravenou verzi.  
4. **Nahradit původní obsah** v dokumentu opraveným textem.  
5. **Uložit** aktualizovaný soubor (volitelné, ale obvykle nutné).

Každý krok je zabalen do vlastní metody, takže jej můžete později znovu použít nebo nahradit. Kompletní zdrojový kód najdete na konci článku.

---

## Krok 1: Nastavení LLM klienta (Jak používat LLM)

Aby byl kód přehledný, zabalíme HTTP volání do malé wrapper třídy. Tato třída předpokládá, že LLM služba přijímá POST požadavek s JSON payload `{ "prompt": "..."}` a vrací `{ "response": "..." }`. Pokud se váš servis liší, upravte serializaci.

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**Proč je to důležité:**  
- **Decoupling** — Pokud později přejdete z Ollama na LM Studio, stačí změnit URL nebo formát payloadu.  
- **Async‑friendly** — Síťové I/O neblokuje UI ani background worker.  
- **Error handling** — `EnsureSuccessStatusCode` vyhodí jasnou výjimku, pokud je LLM nedostupný, což zachytíme později.

> **Tip:** Pokud váš LLM běží na GPU, udržujte velikost požadavku pod ~4 KB, aby nedošlo k náhlému nárůstu latence.

---

## Krok 2: Načtení DOCX a extrakce textu (Čtení textu z Word dokumentu)

Aspose.Words umožňuje číst Word soubory bez problémů. Metoda `Document.GetText()` vrací celý viditelný text včetně zalomení řádků. Pokud potřebujete bohatší formátování (tabulky, poznámky pod čarou), museli byste projít strom uzlů, ale pro čistou kontrolu gramatiky stačí prostý text.

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**Poznámka k okrajovým případům:**  
Pokud dokument obsahuje ne‑anglické znaky nebo speciální symboly, ujistěte se, že vámi používaný LLM model podporuje Unicode. Většina moderních modelů ano, starší mohou řetězce ořezat nebo špatně interpretovat.

---

## Krok 3: Nahrazení obsahu opraveným textem

Aspose.Words nemá jednorázovou metodu „replace whole body“, ale vymazání stromu uzlů a vložení jediného odstavce funguje dobře. Tím také odstraníme veškerý skrytý markup (např. sledované změny).

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**Proč odstraňujeme všechny podřízené uzly:**  
- Zajišťuje čistý start, zabraňuje zbytkům formátování, které by mohly interferovat s novým obsahem.  
- Zjednodušuje kód — není potřeba hledat konkrétní uzly k nahrazení.

Pokud chcete zachovat původní nadpisy, můžete projít původní strom uzlů a nahrazovat jen `Run` uzly, ale to už přesahuje rozsah tohoto tutoriálu.

---

## Krok 4: Spojení všeho dohromady – Kompletní funkční příklad

Níže je kompletní konzolový program. Ukazuje **how to check grammar** od začátku do konce, včetně základní obsluhy chyb a volitelných argumentů příkazové řádky.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### Očekávaný výstup

Po spuštění programu (`dotnet run`) se v konzoli zobrazí něco podobného:

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

Otevřete `output.docx` ve Wordu — uvidíte stejný obsah, ale s opravenou interpunkcí, shodou podmětu s přísudkem a s opravami zjevně chybujících překlepů provedených LLM.

---

## Často kladené otázky a okrajové případy

### Co když LLM vrátí `null` nebo prázdný řetězec?

Metoda `CheckGrammarAsync` se v takovém případě vrátí k původnímu vstupu, pokud v odpovědi chybí pole `response`. Tím zabráníte nechtěnému vymazání dokumentu.

### Jak velký může být dokument, než požadavek vyprší?

Většina lokálních LLM serverů pohodlně zvládne několik tisíc znaků. U větších souborů (např. 100 KB +) zvažte rozdělení textu na odstavce, odeslání každého úseku zvlášť a následné složení opravených částí. Velikost úseku ~2 KB je dobrý výchozí bod.

### Zachovává to obrázky, tabulky nebo poznámky pod čarou?

Ne. Vymazáním všech podřízených uzlů ztratíte všechny netextové elementy. Pokud je potřebujete zachovat, museli byste iterovat strom uzlů, nahrazovat jen `Run` uzly (textové fragmenty) a ostatní uzly nechat nedotčeny. To je pokročilejší scénář — prozkoumejte Aspose.Words API pro manipulaci s `NodeCollection`.

### Mohu použít cloudový LLM místo lokálního?

Ano. Stačí v `LocalLargeLanguageModel` zaměnit URL endpointu a formát payloadu. Mějte ale na paměti, že cloudové služby často mají limity rychlosti a nákladové implikace, zatímco lokální model běží offline a je po počátečním nastavení GPU/CPU zdarma.

---

## Tipy a osvědčené postupy

- **Ukládejte klienta do cache**: Opětovné používání stejné instance `HttpClient` zabraňuje

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}