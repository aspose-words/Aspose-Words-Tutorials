---
category: general
date: 2026-09-11
description: Načtěte soubor z adresáře pomocí Aspose.Words s výchozími možnostmi načítání
  a zjistěte, jak nastavit kódování dokumentu nebo přizpůsobit možnosti načítání v
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load file from directory
- default load options
- set document encoding
- set load options
language: cs
lastmod: 2026-09-11
og_description: Načtěte soubor z adresáře pomocí Aspose.Words s výchozími možnostmi
  načítání, nastavte kódování dokumentu a přizpůsobte možnosti načítání pro jakýkoli
  dokument Word.
og_image_alt: Diagram illustrating load file from directory process with Aspose.Words
og_title: Načtení souboru z adresáře pomocí Aspose.Words – kompletní průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Load file from directory with Aspose.Words using default load options
    and learn how to set document encoding or customize load options in C#.
  headline: How to load file from directory using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document processing
title: Jak načíst soubor z adresáře pomocí Aspose.Words v C#
url: /cs/java/document-loading-and-saving/how-to-load-file-from-directory-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak načíst soubor ze složky pomocí Aspose.Words v C#

Pokud potřebujete **načíst soubor ze složky** do pracovního postupu zpracování Wordu, Aspose.Words to usnadňuje. Tento průvodce ukazuje, jak použít **default load options**, **set document encoding** a **set load options** podle vašeho konkrétního scénáře.

Načítání dokumentů často zaskočí vývojáře, když se zdrojový soubor nachází ve vlastní složce nebo používá kódování jiné než UTF‑8. Na konci tohoto tutoriálu budete schopni načíst libovolný soubor `.docx` z jakékoli složky, řídit jeho kódování a upravit chování načítání bez psaní dalšího pomocného kódu.

## Co dosáhnete

- Načtěte Word dokument z libovolné složky pomocí jediného řádku kódu.  
- Pochopte, co poskytuje **default load options** a kdy je potřeba je změnit.  
- Použijte **set document encoding** pro správnou interpretaci starších znakových sad, jako je Big5.  
- Přizpůsobte **set load options** pro jemné ladění využití paměti, zpracování hesel a další.  

### Požadavky

- .NET 6.0 nebo novější (příklad cílí na .NET 6, ale funguje jakákoli aktuální verze .NET).  
- Aspose.Words pro .NET 23.9 nebo novější – přidejte NuGet balíček `Aspose.Words`.  
- Základní znalost C# a Visual Studio nebo vašeho preferovaného IDE.

---

## Jak načíst soubor ze složky pomocí Aspose.Words

Jádrem operace je jediný konstruktor `Document`, který přijímá cestu k souboru a volitelnou instanci `LoadOptions`. Když vynecháte `LoadOptions`, Aspose.Words automaticky použije **default load options**, které jsou dostačující pro většinu moderních dokumentů.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Define the absolute path to the .docx file you want to load.
        string filePath = @"C:\MyDocuments\big5.docx";

        // Step 2: Load the document using the default load options.
        Document doc = new Document(filePath, new LoadOptions());

        // Verify that the document loaded by outputting the page count.
        Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
    }
}
```

**Proč to funguje:**  
- Konstruktor `Document` načte soubor umístěný na `filePath`.  
- Předáním `new LoadOptions()` řeknete Aspose.Words, aby použil **default load options**, které automaticky detekují formát souboru, zvolí vhodné kódování a aplikují standardní bezpečnostní kontroly.

Spuštěním programu se vypíše počet stránek, což potvrzuje, že operace **load file from directory** byla úspěšná.

---

## Použití default load options

I když můžete argument `LoadOptions` úplně vynechat, explicitní vytvoření objektu `LoadOptions` objasní záměr a připraví vás na pozdější úpravy.

```csharp
// Create a LoadOptions instance with the default configuration.
LoadOptions loadOptions = new LoadOptions();

// Load the document with those options.
Document doc = new Document(@"C:\MyDocuments\sample.docx", loadOptions);
```

**Klíčové body o default load options**

| Vlastnost | Výchozí chování |
|-----------|-----------------|
| **Detekce formátu** | Automaticky detekuje DOC, DOCX, ODT, RTF, HTML a mnoho dalších formátů. |
| **Kódování** | Detekuje UTF‑8, UTF‑16 a běžná starší kódování; v případě neúspěchu se vrátí k UTF‑8. |
| **Zpracování hesla** | Vyvolá `IncorrectPasswordException`, pokud je soubor chráněn heslem. |
| **Využití paměti** | Načte celý dokument do paměti, což je optimální pro soubory menší než 100 MB. |

Pokud je váš dokument kódován ve starší znakové sadě (např. Big5) a automatická detekce selže, musíte **set document encoding** nastavit ručně.

## Nastavení kódování dokumentu

Když soubor obsahuje písma nebo text kódovaný starou kódovou stránkou, můžete Aspose.Words sdělit, které kódování použít, pomocí vlastnosti `LoadOptions.Encoding`. Toto je typický způsob, jak **set document encoding** pro soubory, které výchozí detektor nedokáže rozpoznat.

```csharp
using System.Text;

// Step 1: Create LoadOptions and specify the encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Big5 is code page 950.
    Encoding = Encoding.GetEncoding(950)
};

// Step 2: Load the document from the target directory.
Document doc = new Document(@"C:\MyDocuments\big5.docx", loadOptions);

// Step 3: Verify that the special characters are preserved.
Console.WriteLine($"First paragraph text: {doc.FirstSection.Body.Paragraphs[0].GetText()}");
```

**Proč to potřebujete:**  
- Bez explicitního nastavení `Encoding` může Aspose.Words interpretovat bajty jako UTF‑8, což vede k poškozeným znakům.  
- Poskytnutím správné kódové stránky knihovna načte text přesně tak, jak jej autor zamýšlel.

**Tip:** Použijte `Encoding.GetEncoding("big5")` nebo číselnou kódovou stránku (`950`) pro tradiční čínské (Big5) dokumenty.

## Přizpůsobení load options (set load options)

Kromě kódování `LoadOptions` poskytuje mnoho vlastností, které vám umožní **set load options** pro pokročilé scénáře:

```csharp
// Create a LoadOptions object with several custom settings.
LoadOptions loadOptions = new LoadOptions
{
    // Force the document to be treated as a DOCX file, even if the extension is wrong.
    LoadFormat = LoadFormat.Docx,

    // Limit memory usage for very large files (e.g., 200 MB+).
    LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory,

    // Provide a password if the file is encrypted.
    Password = "MySecretPassword"
};

// Load the document using the customized options.
Document doc = new Document(@"C:\MyDocuments\protected.docx", loadOptions);
```

**Vysvětlení vybraných vlastností**

| Vlastnost | Účel |
|-----------|------|
| `LoadFormat` | Vynutí konkrétní formát, obchází automatickou detekci. Užitečné, když jsou přípony souborů zavádějící. |
| `LoadOptionsMemoryUsage` | Zvolí strategii šetřící paměť (`LowMemory`) pro obrovské dokumenty. |
| `Password` | Poskytne heslo pro šifrované soubory, čímž zabrání výjimce. |
| `ValidateDocumentStructure` | Když je `true`, načítač ověří vnitřní XML strukturu a vyvolá výjimku, pokud je poškozena. |

Můžete kombinovat kterékoliv z nich s **set document encoding**, abyste zvládli nejnáročnější importní pipeline.

## Kompletní spustitelný příklad

Níže je samostatný program, který demonstruje všechny koncepty v jednom toku:

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;

class LoadFileDemo
{
    static void Main()
    {
        // ------------------------------------------------------------------
        // 1️⃣ Define the directory and file name.
        // ------------------------------------------------------------------
        string directory = @"C:\MyDocuments";
        string fileName   = "big5.docx";               // Change as needed.
        string fullPath   = System.IO.Path.Combine(directory, fileName);

        // ------------------------------------------------------------------
        // 2️⃣ Create LoadOptions with explicit encoding (Big5) and low‑memory mode.
        // ------------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            Encoding = Encoding.GetEncoding(950), // Big5 code page.
            LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory
        };

        // ------------------------------------------------------------------
        // 3️⃣ Load the document from the directory using the custom options.
        // ------------------------------------------------------------------
        Document doc = new Document(fullPath, loadOptions);

        // ------------------------------------------------------------------
        // 4️⃣ Verify the load succeeded.
        // ------------------------------------------------------------------
        Console.WriteLine($"Document loaded from \"{fullPath}\"");
        Console.WriteLine($"Page count: {doc.PageCount}");
        Console.WriteLine($"First paragraph: {doc.FirstSection.Body.Paragraphs[0].GetText().Trim()}");

        // ------------------------------------------------------------------
        // 5️⃣ (Optional) Save as PDF to confirm visual fidelity.
        // ------------------------------------------------------------------
        string pdfPath = System.IO.Path.ChangeExtension(fullPath, ".pdf");
        doc.Save(pdfPath);
        Console.WriteLine($"Saved PDF version to \"{pdfPath}\"");
    }
}
```

**Očekávaný výstup v konzoli**

```
Document loaded from "C:\MyDocuments\big5.docx"
Page count: 3
First paragraph: 這是一個測試文件
Saved PDF version to "C:\MyDocuments\big5.pdf"
```

Spuštěním programu se ukáže, jak **load file from directory**, **set document encoding** a **set load options** v jednom jasném pracovním postupu.

## Časté úskalí a jak se jim vyhnout

| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| Poškozené čínské znaky | Kódování není nastaveno nebo je špatná kódová stránka | **Set document encoding** na `Encoding.GetEncoding(950)` pro Big5. |
| `IncorrectPasswordException` i když soubor není chráněn heslem | Načítač mylně detekoval binární soubor jako šifrovaný | Explicitně nastavte `LoadFormat` na správný typ (např. `LoadFormat.Docx`). |
| Out

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [obnovit poškozený docx pomocí Aspose.Words – nastavit režim obnovy a load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Jak načíst RTF dokumenty s konfigurací RTF Load Options v Aspose.Words pro Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)
- [Mistrovství v Markdown Load Options s Aspose.Words pro Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}