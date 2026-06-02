---
category: general
date: 2026-06-02
description: Nahraďte text v souboru docx pomocí C#. Naučte se, jak nahradit všechny
  výskyty slova, provést hledání a nahrazení ve Word dokumentu, a osvojte si efektivní
  nahrazování textu v C#.
draft: false
keywords:
- replace text in docx
- replace all occurrences word
- find and replace word document
- how to replace text c#
language: cs
og_description: Nahraďte text v souboru docx pomocí C#. Tento tutoriál ukazuje, jak
  nahradit všechny výskyty slova a provést hledání a nahrazení ve Word dokumentu s
  přehlednými ukázkami kódu.
og_title: Nahraďte text v docx pomocí C# – Kompletní programovací průvodce
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Replace text in docx using C#. Learn how to replace all occurrences
    word, perform find and replace word document, and master how to replace text c#
    efficiently.
  headline: Replace text in docx with C# – Full Step‑by‑Step Guide
  type: TechArticle
- description: Replace text in docx using C#. Learn how to replace all occurrences
    word, perform find and replace word document, and master how to replace text c#
    efficiently.
  name: Replace text in docx with C# – Full Step‑by‑Step Guide
  steps:
  - name: 1. Case‑Insensitive Replacement
    text: 'If you need to ignore case (e.g., replace “Foo”, “FOO”, and “foo” alike),
      tweak the regex options:'
  - name: 2. Replacing Whole Words Only
    text: 'Sometimes “foo” appears inside another word like “food”. To avoid accidental
      changes, anchor the pattern with word boundaries:'
  - name: 3. Using a Callback for Conditional Replacement
    text: Aspose lets you supply a delegate to decide on‑the‑fly whether to replace
      a match. This is handy for scenarios like “replace only if the word is in a
      table”.
  - name: 4. Handling Large Documents Efficiently
    text: For multi‑gigabyte files, consider processing the document in chunks (e.g.,
      per section) to keep memory usage low. Aspose provides `Section` collections
      you can iterate over and call `Replace` on each individually.
  - name: 5. Preserving Formatting
    text: 'The replacement text inherits the formatting of the first character of
      the match. If you need to enforce a specific style (e.g., bold), apply it after
      the replacement:'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words treats `.doc` and `.docx` uniformly. Just change the
      file extension in the load/save paths.
    question: Does this work with `.doc` files?
  - answer: You’ll need to unprotect the document first (`doc.Protect(ProtectionType.NoProtection,
      "password")`) or supply the password when loading.
    question: What if the document contains protected sections?
  - answer: Absolutely. Use `new LoadOptions { Password = "yourPassword" }` when constructing
      the `Document`.
    question: Can I replace text in a password‑protected file?
  - answer: 'The Open XML SDK can perform find/replace, but it lacks the high‑level
      `Range.Replace` convenience and requires more boilerplate. For production‑grade
      reliability, Aspose remains the recommended choice. --- ## Next Steps & Related
      Topics Now that you’ve mastered **replace text in docx**, you might w'
    question: Is there a free alternative to Aspose.Words?
  type: FAQPage
tags:
- C#
- Word Automation
- FindReplace
title: Nahraďte text v docx pomocí C# – Kompletní krok‑za‑krokem průvodce
url: /cs/net/find-and-replace-text/replace-text-in-docx-with-c-full-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nahrazení textu v docx pomocí C# – Kompletní průvodce krok za krokem

Už jste někdy potřebovali nahradit text v souborech docx, ale nevedeli jste, kde začít? Nejste v tom sami. Ať už čistíte hromadu smluv nebo automaticky generujete personalizované dopisy, naučit se **replace text in docx** s C# vám může ušetřit hodiny ruční úpravy.

V tomto průvodci vás provedeme kompletním, připraveným k okamžitému spuštění řešením, které ukazuje, jak nahradit všechny výskyty slova, provést robustní find‑and‑replace ve Word dokumentu a jednou provždy odpovědět na otázku „jak nahradit text c#“. Žádné vágní odkazy – jen solidní kód, jasná vysvětlení a pár tipů, které byste si přáli vědět dříve.

## Co budete potřebovat

Než se pustíme dál, ujistěte se, že máte následující:

- **.NET 6.0** nebo novější (příklad funguje také s .NET Framework 4.6+).  
- **Aspose.Words for .NET** (nebo libovolná srovnatelná knihovna podporující `FindReplaceOptions`). Můžete ji získat z NuGet pomocí `Install-Package Aspose.Words`.  
- Základní znalost syntaxe C# – nic složitého, jen běžné `using` direktivy a metoda `Main`.  
- Vstupní **.docx** soubor umístěný ve složce, na kterou můžete odkazovat (nazveme ho `YOUR_DIRECTORY/input.docx`).  

To je vše. Žádné extra konfigurační soubory, žádná COM interop a naprosto žádná potřeba spouštět Microsoft Office na serveru.

> **Pro tip:** Pokud běžíte v CI/CD pipeline, uzamkněte verzi Aspose.Words ve vašem `csproj`, abyste se vyhnuli neočekávaným breaking changes.

## Krok 1 – Načtení zdrojového dokumentu

První věc, kterou uděláme, je načíst Word soubor do paměti. Představte si to jako otevření sešitu; knihovna nám poskytne objekt `Document`, který představuje celý soubor.

```csharp
using Aspose.Words;
using System.Text.RegularExpressions;

class Program
{
    static void Main()
    {
        // Load the source document (replace YOUR_DIRECTORY with your actual path)
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx");
```

Proč je to důležité: načtení dokumentu vytvoří strukturu podobnou DOM, která nám umožní procházet odstavce, tabulky, záhlaví i skryté objekty Office Math. Pokud soubor nelze najít, Aspose vyhodí jasnou `FileNotFoundException`, takže okamžitě uvidíte, kde je problém.

## Krok 2 – Nastavení Find/Replace možností

Dále nastavíme `FindReplaceOptions`. Tento objekt říká enginu, *co* má ignorovat a *jak* má zacházet s nalezenými shodami. Ve většině scénářů budete chtít ponechat výchozí hodnoty, ale zde ukazujeme, jak zakázat hledání uvnitř Office Math objektů – něco, co mnohé vývojáře překvapí.

```csharp
        // Create find/replace options
        FindReplaceOptions replaceOptions = new FindReplaceOptions();

        // Skip math objects during the search (optional but often useful)
        replaceOptions.IgnoreOfficeMath = true;
```

> **Proč ignorovat Office Math?**  
> Rovnice jsou uloženy jako samostatné XML fragmenty. Pokud hledáte termín, který se vyskytuje uvnitř vzorce, engine může rovnici poškodit. Nastavením `IgnoreOfficeMath` na `true` tomuto riziku předchází, přičemž běžný text zůstane nedotčen.

## Krok 3 – Nahrazení všech výskytů slova (příklad s Regex)

Nyní přichází jádro **replace text in docx**: skutečná výměna starého řetězce za nový. Metoda `Range.Replace` přijímá `Regex`, náhradní řetězec a možnosti, které jsme právě vytvořili.

```csharp
        // Replace every occurrence of "foo" with "bar"
        doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
```

Několik poznámek:

- Vzor `Regex` může být tak jednoduchý jako doslovný řetězec (`@"foo"`) nebo plnohodnotný regulární výraz (`@"\bfoo\b"` pro shodu pouze celých slov).  
- Protože používáme `Range.Replace`, hledání pokrývá celý dokument – včetně záhlaví, zápatí, poznámek pod čarou a dokonce i textu uvnitř tvarů.  
- Metoda vrací počet provedených náhrad, který můžete zachytit, pokud potřebujete operaci logovat:

```csharp
        int count = doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        Console.WriteLine($"{count} occurrence(s) replaced.");
```

Tento řádek přímo splňuje požadavek **replace all occurrences word** a přitom zůstává čitelný.

## Krok 4 – Uložení upraveného dokumentu

Nakonec změny uložíme. Můžete přepsat původní soubor nebo zapsat do nového umístění. Přepis je v pořádku pro rychlé skripty; pro produkční pipeline je lepší zapisovat do nového souboru, aby byl zachován auditní záznam.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY/output.docx");
    }
}
```

To je celý workflow pro **how to replace text c#** ve Word dokumentu. Spusťte program a uvidíte `output.docx` s každým výskytem „foo“ přeměněným na „bar“.

---

## Pokročilá témata a okrajové případy

### 1. Náhrada bez rozlišení velikosti písmen

Pokud potřebujete ignorovat velikost (např. nahradit „Foo“, „FOO“ i „foo“), upravte možnosti regexu:

```csharp
        var pattern = new Regex(@"foo", RegexOptions.IgnoreCase);
        doc.Range.Replace(pattern, "bar", replaceOptions);
```

### 2. Náhrada jen celých slov

Někdy se „foo“ objeví uvnitř jiného slova jako „food“. Aby nedošlo k nechtěným změnám, ohraničte vzor pomocí hranic slova:

```csharp
        var wholeWord = new Regex(@"\bfoo\b");
        doc.Range.Replace(wholeWord, "bar", replaceOptions);
```

### 3. Použití callbacku pro podmíněnou náhradu

Aspose vám umožní předat delegáta, který rozhodne za běhu, zda nahradit shodu. To je užitečné např. pro „nahradit pouze, pokud je slovo v tabulce“.

```csharp
        replaceOptions.ReplacingCallback = new ReplaceEvaluator((match, isInsideHeaderFooter, isInsideTable) =>
        {
            // Only replace when inside a table
            return isInsideTable ? "bar" : match.Value;
        });
        doc.Range.Replace(new Regex(@"foo"), "", replaceOptions);
```

### 4. Efektivní zpracování velkých dokumentů

U souborů o velikosti několika gigabajtů zvažte zpracování po částech (např. po sekcích), aby se snížila spotřeba paměti. Aspose poskytuje kolekce `Section`, přes které můžete iterovat a volat `Replace` na každé zvlášť.

```csharp
        foreach (Section sec in doc.Sections)
        {
            sec.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        }
```

### 5. Zachování formátování

Náhradní text zdědí formátování prvního znaku shody. Pokud potřebujete vynutit konkrétní styl (např. tučné), aplikujte jej po náhradě:

```csharp
        doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        foreach (Run run in doc.GetChildNodes(NodeType.Run, true))
        {
            if (run.Text.Contains("bar"))
                run.Font.Bold = true; // Force bold on replaced text
        }
```

---

## Kompletní zdrojový kód (připravený ke kopírování)

Níže najdete kompletní, samostatný program, který můžete vložit do konzolové aplikace a spustit okamžitě. Žádné skryté závislosti, žádné externí konfigurační soubory.

```csharp
using Aspose.Words;
using System;
using System.Text.RegularExpressions;

namespace DocxReplaceDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

            // 2️⃣ Set up find/replace options
            FindReplaceOptions replaceOptions = new FindReplaceOptions
            {
                // Skip Office Math objects – optional but safe
                IgnoreOfficeMath = true
            };

            // 3️⃣ Perform the replacement (replace all occurrences word)
            // Change the pattern or replacement as needed
            var pattern = new Regex(@"foo", RegexOptions.IgnoreCase); // case‑insensitive
            int replacedCount = doc.Range.Replace(pattern, "bar", replaceOptions);

            Console.WriteLine($"{replacedCount} occurrence(s) replaced.");

            // 4️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY/output.docx");
        }
    }
}
```

**Očekávaný výstup:**  
Pokud `input.docx` obsahuje tři instance „foo“ (v jakékoli velikosti), konzole vypíše `3 occurrence(s) replaced.` a `output.docx` bude obsahovat „bar“ na těchto třech místech, přičemž zachová původní styl.

---

## Často kladené otázky

**Q: Funguje to i se soubory `.doc`?**  
A: Ano. Aspose.Words zachází s `.doc` i `.docx` jednotně. Stačí změnit příponu v cestách pro načtení/uložení.

**Q: Co když dokument obsahuje chráněné sekce?**  
A: Nejprve musíte dokument odemknout (`doc.Protect(ProtectionType.NoProtection, "password")`) nebo při načítání zadat heslo.

**Q: Můžu nahrazovat text v souboru chráněném heslem?**  
A: Rozhodně. Použijte `new LoadOptions { Password = "yourPassword" }` při vytváření objektu `Document`.

**Q: Existuje bezplatná alternativa k Aspose.Words?**  
A: Open XML SDK umí provádět find/replace, ale postrádá pohodlí `Range.Replace` a vyžaduje více boilerplate kódu. Pro produkční spolehlivost zůstává Aspose doporučenou volbou.

---

## Další kroky a související témata

Po zvládnutí **replace text in docx** můžete chtít prozkoumat:

- **Vkládání obrázků programově** – naučte se vkládat obrázky do zástupných míst.  
- **Vytváření tabulek za běhu** – užitečné pro generování faktur nebo reportů.  
- **Dávkové zpracování** – procházejte složku s `.docx` soubory a aplikujte stejnou logiku find‑and‑replace.  

Každé z těchto témat staví na stejném objektovém modelu `Document`, který jste právě použili, takže se budete cítit jako doma.

---

## Závěr

Probrali jsme vše, co potřebujete vědět o **replace text in docx** pomocí C#. Od načtení dokumentu, nastavení `FindReplaceOptions`, výměny každého výskytu slova až po uložení výsledku – tento tutoriál vám poskytuje kompletní, připravené řešení. Také jsme ukázali, jak řešit rozlišení velikosti písmen, shodu celých slov a velké soubory, což doplňuje scénáře **replace all occurrences word** a **find and replace word document**.  

Vyzkoušejte to, upravte regex vzory a sledujte, jak se vaše úlohy automatizace Wordu zkrátí z hodin na sekundy. Máte nápad, který chcete implementovat? Zanechte komentář – šťastné kódování!

![Screenshot of C# code replacing text in a DOCX file](replace-text-in-docx.png "příklad nahrazení textu v docx")

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Simple Text Find And Replace In Word](/words/english/net/find-and-replace-text/simple-find-replace/)
- [Word Replace Text Containing Meta Characters](/words/english/net/find-and-replace-text/replace-text-containing-meta-characters/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}