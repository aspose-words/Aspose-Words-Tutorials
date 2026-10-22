---
category: general
date: 2026-09-11
description: Přidejte ovládací prvek obsahu do dokumentu Word pomocí Aspose.Words.
  Postupujte podle tohoto krok‑za‑krokem návodu a programově vložte prostý textový
  Structured Document Tag (SDT).
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: cs
lastmod: 2026-09-11
og_description: Přidejte ovládací prvek obsahu do dokumentu Word pomocí Aspose.Words.
  Tento průvodce vám ukáže, jak programově vložit prostý textový Structured Document
  Tag (SDT) a přizpůsobit jej.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Přidat ovládací prvek obsahu do dokumentu Word – kompletní tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: Přidat ovládací prvek obsahu do dokumentu Word pomocí Aspose.Words
url: /cs/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání ovládacího prvku obsahu do dokumentu Word pomocí Aspose.Words

Pokud potřebujete **přidat ovládací prvek obsahu do dokumentu Word** programově, tento tutoriál vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. Ať už vytváříte službu pro generování dokumentů nebo automatizujete tvorbu formulářů, naučíte se vložit prostý textový Structured Document Tag (SDT) a přiřadit mu smysluplný název.

V tomto průvodci uvidíte kompletní, spustitelný příklad, který zahrnuje všechny potřebné importy, vysvětluje, proč je každé volání API důležité, a ukazuje, jak výsledek ověřit. Nepotřebujete žádné externí odkazy – stačí zkopírovat kód, spustit jej a otevřít vygenerovaný soubor *.docx*.

## Požadavky

* .NET 6.0 SDK nebo novější nainstalovaný  
* Visual Studio 2022 (nebo jakékoli C# IDE)  
* Aspose.Words pro .NET 23.5 nebo novější – můžete získat bezplatný zkušební NuGet balíček  

Tyto položky představují minimální nastavení pro **automatizaci Wordu** s Aspose.Words.

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte nový konzolový projekt a přidejte balíček Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Nyní otevřete `Program.cs` a přidejte požadované direktivy `using`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

Tyto jmenné prostory vám poskytují přístup k `DocumentBuilder`, `StructuredDocumentTag` a dalším základním typům potřebným k **přidání ovládacího prvku obsahu do dokumentu Word**.

## Krok 2: Vytvoření nového dokumentu a DocumentBuilderu

`DocumentBuilder` je hlavní vstupní bod pro tvorbu souborů Word. Uchovává kurzor, který sleduje, kam bude vložen další prvek.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité*: Objekt `Document` představuje celý soubor Word, zatímco `DocumentBuilder` zjednodušuje vkládání odstavců, tabulek a **ovládacích prvků obsahu**, jako jsou Structured Document Tags.

## Krok 3: Vložení prostého textového Structured Document Tag (SDT)

Jádrem našeho řešení je metoda `insertStructuredDocumentTag`. Vytváří **ovládací prvek obsahu**, který může obsahovat prostý text, data, rozbalovací seznamy atd. Zde používáme výčtovou hodnotu `SdtType.PLAIN_TEXT`.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*Proč je to důležité*: Nastavení na `true` způsobí, že se ovládací prvek zobrazí jako světle šedý zástupný text, což uživatelům signalizuje, že mají pole vyplnit.

## Krok 4: Přiřazení názvu SDT pro pozdější identifikaci

Název (nebo tag) vám umožní později ovládací prvek najít, například když potřebujete programově nahradit jeho obsah.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

Název se nezobrazuje v uživatelském rozhraní dokumentu, ale je uložen v podkladovém XML a lze jej dotazovat pomocí API Aspose.Words.

## Krok 5: Přidání zástupného textu do SDT

Aby byl ovládací prvek uživatelsky přívětivější, vložte výchozí běh (run), který uživateli říká, co má napsat.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*Proč je to důležité*: Objekt `Run` představuje kus textu. Připojením k SDT vytvoříte viditelnou nápovědu, která zmizí, jakmile uživatel začne psát.

## Krok 6: Uložení dokumentu

Nakonec zapište dokument na disk, abyste jej mohli otevřít v Microsoft Word.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

Když otevřete `ContentControlExample.docx`, uvidíte šedě zvýrazněný ovládací prvek s názvem **CustomerName** a zástupným textem *Enter name here*.

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat a vložit do `Program.cs`. Obsahuje všechny kroky, komentáře a potřebnou obsluhu chyb.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Očekávaný výstup

Spuštěním programu se vypíše:

```
Document saved to ContentControlExample.docx
```

Otevřením vygenerovaného souboru ve Wordu se zobrazí jediný ovládací prvek se šedým zástupným textem **Enter name here**. Ovládací prvek lze upravit, smazat nebo později programově přistupovat pomocí jeho názvu *CustomerName*.

## Běžné varianty a okrajové případy

| Scenario | How to adapt the code |
|----------|----------------------|
| **Více ovládacích prvků obsahu** | Zavolejte `InsertStructuredDocumentTag` opakovaně a při každém přiřaďte jedinečný `Title`. |
| **Rich‑textový ovládací prvek** | Použijte `SdtType.RichText` místo `PlainText`. |
| **Ovládací prvek výběru data** | Použijte `SdtType.Date` a případně nastavte `sdt.DateDisplayFormat`. |
| **Zamknutí ovládacího prvku** | Nastavte `sdt.LockContentControl = true`, aby uživatelé nemohli prvek odstranit. |
| **Pozdější vyhledání ovládacího prvku** | Použijte `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` a filtrujte podle `Title`. |

Tyto varianty ilustrují flexibilitu **Aspose.Words**, když potřebujete **přidat ovládací prvek obsahu do dokumentu Word** pro různé scénáře vyplňování formulářů.

## Profesionální tipy

* **Výkon** – Pokud generujete mnoho dokumentů ve smyčce, znovu použijte jedinou instanci `DocumentBuilder` a pro každou iteraci zavolejte `doc.Clone()`, abyste se vyhnuli opakovanému vytváření objektů.  
* **Styling** – Můžete použít `ParagraphFormat` nebo `Font` na zástupný `Run`, aby odpovídal vizuálnímu stylu vašeho dokumentu.  
* **Validace** – Po vložení ovládacího prvku můžete zkontrolovat `sdt.IsShowingPlaceholderText`, abyste potvrdili, že zástupný text je správně zobrazen.  

## Závěr

Nyní víte, jak **přidat ovládací prvek obsahu do dokumentu Word** pomocí Aspose.Words, od vytvoření `DocumentBuilder` až po vložení prostého textového `StructuredDocumentTag`, přiřazení názvu a přidání zástupného textu. Kompletní příklad lze rozšířit na další typy SDT, více ovládacích prvků a pokročilé možnosti zamykání nebo stylování.

Připraveni jít dál? Prozkoumejte tato související témata:

* **Práce s tabulkami uvnitř ovládacích prvků** – použijte `DocumentBuilder.InsertTable` po SDT.  
* **Extrahování dat z vyplněných ovládacích prvků** – načtěte uzel `Sdt` podle názvu a přečtěte jeho vlastnost `Text`.  
* **Použití OpenXML SDK** – alternativní přístup, pokud dáváte přednost bezplatné knihovně podporované Microsoftem.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přidání obsahu pomocí Document Builder v Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/)
- [Vložení vloženého obrázku do dokumentu Word pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Vytvoření dokumentu Word s tabulkou pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}