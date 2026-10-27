---
category: general
date: 2026-09-08
description: Nastavte název značky a vytvořte obsahový ovládací prvek (SDT) ve Word
  dokumentu pomocí C#. Naučte se, jak přidat SDT, zapsat text do značky a upravit
  dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: cs
lastmod: 2026-09-08
og_description: Nastavte název značky a vytvořte ovládací prvek obsahu (SDT) ve Word
  dokumentu pomocí C#. Postupujte podle tohoto krok‑za‑krokem průvodce, abyste přidali
  SDT, zapsali text do značky a upravili dokument.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Nastavte název tagu a přidejte SDT do dokumentu Word – průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak nastavit název značky a přidat SDT do dokumentu Word pomocí C#
url: /cs/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit název značky a přidat SDT ve Word dokumentu pomocí C#

Pokud potřebujete **nastavit název značky** pro StructuredDocumentTag (SDT) při práci se soubory Word, tento průvodce vám přesně ukáže, jak na to. Uvidíte kompletní, spustitelný příklad, který **vytvoří ovládací prvek obsahu**, zapíše text do značky a **modifikuje Word dokument** od začátku do konce.

Vývojáři se často ptají, *„jak přidat sdt* do existujícího .docx a pak *zapsat text do značky*?“ – odpověď spočívá v použití Aspose.Words pro .NET API. Na konci tohoto tutoriálu budete schopni otevřít Word soubor, vložit plain‑text SDT, nastavit jeho název značky, naplnit jej obsahem a uložit změny, aniž by zůstaly nepoužité prostředky.

## Požadavky

* .NET 6.0 nebo novější nainstalovaný.
* Platná licence Aspose.Words pro .NET (nebo můžete pracovat s evaluační verzí).
* Visual Studio 2022 (nebo jakékoli IDE podporující C#).
* Vstupní Word dokument (`input.docx`) umístěný ve složce, na kterou můžete odkazovat z kódu.

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte nový projekt typu Console App a přidejte NuGet balíček Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Poté přidejte potřebné `using` direktivy na začátek souboru `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Tyto jmenné prostory vám poskytují přístup k třídám `Document`, `DocumentBuilder` a `StructuredDocumentTag`, které jsou nezbytné pro **modifikaci Word dokumentu**.

## Krok 2: Načtení existujícího Word dokumentu

Prvním krokem je načíst soubor, který chcete upravit. Tento krok je vyžadován v každém scénáři, kde **modifikujete obsah Word dokumentu**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Proč nejprve načítáme dokument** – Objekt `Document` představuje celý .docx balíček v paměti. Teprve po načtení můžete bezpečně vkládat nové uzly, jako je SDT.

## Krok 3: Vložení StructuredDocumentTag (SDT) a nastavení jeho názvu značky

Nyní odpovídáme na hlavní otázku: **jak přidat sdt** a **nastavit název značky**. Použijeme `DocumentBuilder.InsertStructuredDocumentTag` s `SdtType.PlainText`. Druhý argument je název značky, který můžete později odkazovat programově nebo přes uživatelské rozhraní Wordu.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Vysvětlení** – `InsertStructuredDocumentTag` vrací instanci `StructuredDocumentTag`. Předáním `"MyTag"` **nastavíme název značky** přímo při vytvoření. Pokud jej budete potřebovat později změnit, můžete přiřadit novou hodnotu do `sdt.Tag`.

## Krok 4: Zapsání textu do nově vytvořené značky

Po vytvoření SDT obvykle chcete **zapsat text do značky**, aby koncoví uživatelé viděli zástupný nebo výchozí obsah. Metoda `SetText` právě to provádí.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Proč použít SetText** – Přímé přiřazení k vlastnosti `Text` by nahradilo celou hierarchii uzlů. `SetText` bezpečně aktualizuje vnitřní text ovládacího prvku obsahu a zachovává jeho strukturu.

## Krok 5: Uložení upraveného dokumentu

Nakonec uložte změny do nového souboru. Tím se dokončuje workflow **modifikace Word dokumentu**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Když otevřete `output.docx` v Microsoft Word, uvidíte plain‑text ovládací prvek označený **MyTag**, který obsahuje text „Sample content“. Ovládací prvek lze ručně upravit a název značky zůstává přístupný přes vývojářské nástroje Wordu.

## Kompletní zdrojový kód

Níže je kompletní, samostatný program. Zkopírujte jej do `Program.cs` a spusťte; nejsou vyžadovány žádné další úryvky.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Očekávaný výstup v konzoli

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Jak vypadá výsledný Word soubor

![Word dokument zobrazující ovládací prvek obsahu pojmenovaný MyTag s textem “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Příklad nastavení názvu značky ve Word dokumentu"}

*Snímek obrazovky ilustruje SDT s **názvem značky** nastaveným na *MyTag* a viditelným vloženým textem.*

## Běžné varianty a okrajové případy

| Situace | Jak to řešit |
|-----------|------------------|
| **Create a rich‑text SDT** | Použijte `SdtType.RichText` místo `PlainText`. |
| **Set a different tag name after insertion** | `sdt.Tag = "NewTag";` – můžete kdykoli přiřadit nový název značky. |
| **Add the SDT inside a specific paragraph** | Přesuňte kurzor builderu (`builder.MoveToParagraph(index)`) před voláním `InsertStructuredDocumentTag`. |
| **Multiple SDTs in the same document** | Opakujte kroky 3‑4 pro každý ovládací prvek; každý může mít unikátní název značky. |
| **Working with protected documents** | Ujistěte se, že dokument není chráněn (`doc.Unprotect()`), před vložením SDT. |

## Profesionální tipy pro robustní automatizaci Wordu

* **License early** – Zavolejte `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` na začátku `Main`, aby se předešlo vodoznakům evaluační verze.
* **Dispose objects** – Zabalte `Document` do `using` bloku, pokud cílíte na .NET Framework, aby byly uvolněny souborové handly.
* **Validate tag existence** – Při pozdějším čtení dokumentu použijte `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` k nalezení značek podle vlastnosti `Tag`.
* **Performance** – Pro velké dokumenty načítejte jen potřebné sekce pomocí `LoadOptions` s `LoadFormat.Docx` a `LoadFormat.Auto`.  

## Závěr

Nyní víte, jak **nastavit název značky**, **vytvořit ovládací prvek obsahu**, **zapsat text do značky** a **modifikovat Word dokument** pomocí C#. Kompletní příklad ukazuje standardní vzor pro **jak přidat sdt** a bezpečně uložit změny.  

Od tady

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přidání obsahu pomocí Document Builder v Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/)
- [Word dokument – Jak odstranit obsah](/words/english/net/remove-content/)
- [Vytvoření Word dokumentu s Aspose.Words – krok za krokem](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}