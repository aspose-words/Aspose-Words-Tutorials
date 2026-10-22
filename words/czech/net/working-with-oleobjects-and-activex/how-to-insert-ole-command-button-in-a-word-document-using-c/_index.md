---
category: general
date: 2026-10-07
description: Naučte se, jak vložit OLE tlačítko příkazu do dokumentu Word pomocí Aspose.Words
  C#. Podrobný krok‑za‑krokem návod zahrnující DocumentBuilder, vlastnosti a ukládání
  souboru.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: cs
lastmod: 2026-10-07
og_description: Vložte OLE příkazové tlačítko do dokumentu Word pomocí C#. Postupujte
  podle tohoto stručného tutoriálu, abyste přidali, nakonfigurovali a uložili funkční
  CommandButton s Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Vložení OLE příkazového tlačítka do Wordu pomocí C# – kompletní průvodce
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Jak vložit OLE příkazové tlačítko do dokumentu Word pomocí C#
url: /cs/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit OLE tlačítko příkazu do dokumentu Word pomocí C#

Pokud potřebujete **vložit OLE tlačítko příkazu** do souboru Word programově, tento návod vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. Ať už vytváříte zprávu s vyplněnými formuláři nebo automatizujete šablonu, která vyžaduje interakci uživatele, níže uvedené kroky vám poskytnou kompletní, spustitelné řešení.

Dozvíte se, jak vytvořit prázdný dokument, použít `DocumentBuilder` k umístění `Forms2OleControl`, nastavit popisek a název tlačítka a nakonec uložit soubor `.docx`. Kromě knihovny Aspose.Words nebudete potřebovat žádné externí nástroje.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+)
* Platnou licenci Aspose.Words pro .NET nebo bezplatný evaluační klíč
* Visual Studio 2022 (nebo jakékoli jiné C# IDE dle preference)
* Základní znalosti syntaxe C# a konceptů Word OLE

> **Tip:** Pokud používáte bezplatnou evaluační verzi, vygenerovaný dokument bude obsahovat malou vodoznak. Licencovaná verze jej automaticky odstraní.

## Krok 1: Instalace Aspose.Words

Přidejte balíček Aspose.Words do svého projektu pomocí NuGet:

```bash
dotnet add package Aspose.Words
```

Balíček obsahuje jmenné prostory `Aspose.Words.Drawing` a `Aspose.Words.Drawing.Ole`, které jsou potřebné pro OLE ovládací prvky.

## Krok 2: Vložení OLE tlačítka příkazu pomocí DocumentBuilder

Jádrem tutoriálu je metoda `InsertForms2OleControl`. Vytvoří **Forms2 OLE CommandButton** na konkrétním místě a s určenou velikostí.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Proč to funguje

* `DocumentBuilder` je hlavní API pro programové vytváření dokumentů Word.  
* `InsertForms2OleControl` říká Aspose.Words, aby vložil **Forms2 OLE ovládací prvek**, což je starší technologie formulářů Wordu podporující tlačítka příkazu, zaškrtávací políčka atd.  
* Hodnota výčtu `OleControlType.CommandButton` specifikuje, že vložený prvek je **tlačítko příkazu** — přesně ten typ, který jste požadovali při **vkládání OLE tlačítka příkazu**.  
* `Rectangle` určuje vizuální umístění. Upravením souřadnic X/Y nebo šířky/výšky přizpůsobíte rozvržení.

## Krok 3: Uložení dokumentu

Po nastavení tlačítka zapište dokument na disk. Můžete zvolit libovolný formát podporovaný Aspose.Words (`.docx`, `.pdf`, `.odt`, …). Pro tento tutoriál uložíme jako dokument Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Když otevřete `CommandButton.docx` v Microsoft Word, uvidíte klikatelné tlačítko označené **Click Me**. Po jeho stisknutí ve Wordu se spustí výchozí dialog „Run Macro“, protože tlačítko je OLE formulářový ovládací prvek; později můžete připojit makro nebo VBA kód, pokud bude potřeba.

## Krok 4: Ověření výsledku (očekávaný výstup)

Otevřete vygenerovaný soubor:

1. Tlačítko se objeví na souřadnicích, které jste zadali (přibližně 1,4 palce od levého a horního okraje stránky).  
2. Popisek zobrazuje **Click Me**.  
3. Vlastnost `Name` (`cmdSubmit`) je viditelná v panelu **Developer → Properties** ve Wordu, což je užitečné, když potřebujete odkazovat na ovládací prvek z VBA.

![Příklad vložení OLE tlačítka příkazu v dokumentu Word](insert-ole-button.png)

*Text alternativy obrázku*: **Příklad vložení OLE tlačítka příkazu v dokumentu Word** (obsahuje hlavní klíčové slovo pro přístupnost a SEO).

## Okrajové případy a časté otázky

### 1. Co když se tlačítko neobjeví tam, kde očekávám?

* Word používá body, ne pixely. Převod obrazovkových pixelů na body (`points = pixels * 72 / DPI`).  
* Ujistěte se, že obdélník neprotíná okraje stránky; jinak může Word prvek posunout.

### 2. Můžu vložit tlačítko do existujícího dokumentu?

Ano. Načtěte dokument pomocí `new Document("Existing.docx")` a použijte stejný workflow s `DocumentBuilder`. Jen nezapomeňte přesunout kurzor builderu (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` atd.) před voláním `InsertForms2OleControl`.

### 3. Jak připojit makro k tlačítku?

Aspose.Words nevytváří VBA kód, ale po vygenerování dokumentu můžete makro vložit:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Funguje to s .NET Core na Linuxu?

OLE ovládací prvek je specifický pro Windows, protože závisí na COM. Na Linuxu bude tlačítko vloženo, ale zobrazí se jako statický obrázek bez interaktivního chování. Pro multiplatformní interaktivní formuláře zvažte použití obsahových ovládacích prvků (`StructuredDocumentTag`) místo OLE.

### 5. Co když potřebuji jinou velikost nebo více tlačítek?

Vytvořte další objekty `Rectangle` s unikátními souřadnicemi a opakujte volání `InsertForms2OleControl`. Každé tlačítko může mít vlastní `Caption` a `Name`.

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje všechny potřebné `using` direktivy, ošetření chyb a komentáře.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Spusťte program, otevřete vygenerovaný `CommandButton.docx` a uvidíte tlačítko **Click Me** připravené k dalším úpravám.

## Závěr

Nyní víte, jak **vložit OLE tlačítko příkazu** do dokumentu Word pomocí C# a Aspose.Words. Tutoriál pokryl:

* Instalaci balíčku Aspose.Words  
* Použití `DocumentBuilder.InsertForms2OleControl` s `OleControlType.CommandButton`  
* Nastavení vlastností tlačítka (`Caption`, `Name`)  
* Uložení a ověření výstupu  

Odtud můžete zkoumat související témata, jako je **Aspose.Words OLE control** pro zaškrtávací políčka, rozbalovací seznamy nebo vkládání celých Excelových listů. Můžete také experimentovat s automatizací **Word OLE tlačítka příkazu** ve větších šablonách, nebo nahradit OLE ovládací prvky moderními **content controls** pro lepší podporu napříč platformami.

Neváhejte upravit hodnoty obdélníku, přidat více tlačítek nebo připojit VBA makra podle potřeb vaší aplikace. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Vložit Ole objekt do dokumentu Word](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Vložit Ole objekt do dokumentu Word jako ikonu](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Vložit Ole objekt do Wordu s Ole balíčkem](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}