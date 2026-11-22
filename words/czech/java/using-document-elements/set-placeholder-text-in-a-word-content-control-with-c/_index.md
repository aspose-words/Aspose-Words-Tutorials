---
category: general
date: 2026-11-22
description: Nastavte text zástupného místa v ovládacím prvku Word pomocí C#. Naučte
  se, jak vytvořit vlastní značku, vložit ovládací prvek prostého textu a přidat zástupný
  text ke značce pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: cs
lastmod: 2026-11-22
og_description: Nastavte text zástupného symbolu v ovládacím prvku obsahu Wordu pomocí
  C#. Tento tutoriál vám ukáže, jak vytvořit vlastní značku, vložit ovládací prvek
  prostého textu a přidat zástupný text ke značce pro lepší interaktivitu dokumentu.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Nastavte zástupný text v ovládacím prvku Word – průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Nastavte zástupný text v ovládacím prvku Word pomocí C#
url: /cs/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte text zástupného znaku v ovládacím prvku obsahu Word pomocí C#

Pokud potřebujete **nastavit text zástupného znaku** v dokumentu Word programově, tento průvodce vám přesně ukáže, jak na to. Pomocí Aspose.Words pro .NET můžete vytvořit vlastní značku, vložit ovládací prvek prostého textu a přidat zástupný znak ke značce, aby byl dokument připraven pro vstup uživatele.

V tomto tutoriálu se naučíte, jak **vytvořit vlastní značku**, **vložit ovládací prvek obsahu** a **přidat zástupný znak ke značce**, přičemž kód zůstane stručný a připravený pro produkci. Nejsou potřeba žádné externí nástroje – stačí .NET projekt a knihovna Aspose.Words.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK nebo novější nainstalováno  
* Platná licence Aspose.Words pro .NET (nebo bezplatný evaluační klíč)  
* Základní znalost C# a Visual Studio (nebo libovolného IDE, které preferujete)  

Následující sekce předpokládají, že jste vytvořili konzolový projekt pojmenovaný `WordPlaceholderDemo`.

## Step 1: Install Aspose.Words

Add the NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Tip:** Použijte příznak `--version` k uzamčení balíčku na nejnovější stabilní verzi (např. `Aspose.Words.NET 24.9`).

## Step 2: Load the source document and create a `DocumentBuilder`

The first thing you do is load an existing `.docx` file (or create a new empty document) and instantiate a `DocumentBuilder`. The builder gives you a fluent API to insert controls and text.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

This code **sets the stage** for inserting a content control. The `DocumentBuilder` works directly on the `doc` object, so any changes you make are automatically reflected.

## Step 3: Create a custom tag (StructuredDocumentTag)

A *custom tag* in Word is called a **StructuredDocumentTag (SDT)**. You can think of it as a content control that carries a unique identifier. Creating one is the core of the **create custom tag** step.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

The `InsertStructuredDocumentTag` method takes two arguments:

1. Typ ovládacího prvku (`PlainText` v tomto případě).  
2. Řetězec, který jedinečně identifikuje značku (`"MyTag"`).  

Použitím **vlastní značky** můžete později ovládací prvek najít nebo s ním programově manipulovat.

## Step 4: Set a title for accessibility

A title improves accessibility and makes the control easier to find in the Word UI.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

Vlastnost `Title` je volitelná, ale její přidání je osvědčený postup, když **add placeholder to tag** pro lepší uživatelský zážitek.

## Step 5: Add placeholder text to the tag

Now comes the main goal: **set placeholder text**. This text appears when the control is empty, guiding the user on what to type.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

Vlastnost `PlaceholderText` je přesně to, co potřebujete k **add placeholder to tag**. Chová se jako šedý náznak, který vidíte v moderních polích formulářů.

## Step 6: Save the modified document

After configuring the control, write the document back to disk.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Když otevřete `output.docx` v Microsoft Word, uvidíte ovládací prvek prostého textu označený „CustomerName“ se zástupným znakem „Enter name…“. Kliknutím do ovládacího prvku se zástupný znak odstraní a uživatel může psát.

### Expected output

* Soubor Word (`output.docx`) obsahující jediný ovládací prvek prostého textu.  
* Ovládací prvek zobrazuje zástupný znak „Enter name…“, dokud uživatel něco nenapíše.  
* Identifikátor značky ovládacího prvku je `MyTag`, který můžete později dotazovat pomocí `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Step 7: How to insert content control elsewhere (advanced)

If you need to **how to insert content control** at a specific location—say, after a particular paragraph—use the `MoveTo` method before inserting the tag:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

This snippet demonstrates **insert plain text control** multiple times within the same document.

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Zástupný znak není viditelný | Ovládací prvek již obsahuje text (i mezera) | Ujistěte se, že `sdt.Text` je prázdný před nastavením `PlaceholderText`. |
| Kolize identifikátoru značky | Opakované použití stejného názvu značky (`MyTag`) ve stejném dokumentu | Používejte jedinečné identifikátory pro každou `StructuredDocumentTag`. |
| Výjimka licence | Spuštění bez platné licence Aspose.Words | Aplikujte soubor licence (`license.SetLicense("Aspose.Words.lic")`) na začátku `Main`. |
| Dokument není uložen | Zapomenutí zavolat `doc.Save` nebo použití cesty jen pro čtení | Ověřte, že výstupní cesta je zapisovatelná, a zavolejte `doc.Save`. |

## Full working example

Below is the complete program you can copy‑paste into `Program.cs`. It includes all steps—**create custom tag**, **how to insert content control**, **add placeholder to tag**, and **insert plain text control**—in one cohesive flow.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Run the program with `dotnet run`. After execution, open `output.docx` to verify that both controls display their respective placeholders.

## Next steps

* **Přizpůsobte vzhled** – Použijte `sdt.Font` ke změně velikosti písma, barvy nebo stylu uvnitř ovládacího prvku.  
* **Vazba na XML data** – Prozkoumejte `sdt.XmlMapping`, pokud potřebujete, aby se ovládací prvek mapoval


## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Vytvořte dokument Word programově – přidejte ovládací prvek a zástupný znak](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Nastavte text zástupného znaku v Aspose.Words – kompletní průvodce pro C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Vytvořte nový dokument Word a vložte ovládací prvek v C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}