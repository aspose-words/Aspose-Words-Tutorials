---
category: general
date: 2026-08-10
description: Vytvořte programově dokument Word pomocí Aspose.Words, poté přidejte
  ovládací prvek ActiveX – tlačítko Word. Vložte příkazové tlačítko ActiveX během
  několika minut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: cs
lastmod: 2026-08-10
og_description: Vytvořte dokument Word programově pomocí Aspose.Words a poté přidejte
  tlačítko ActiveX. Naučte se rychle vložit příkazové tlačítko ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Vytvořte Word dokument programově – přidejte tlačítko ActiveX v C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Vytvořit Word dokument programově a přidat ActiveX tlačítko
url: /cs/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte Word dokument programově a přidejte ActiveX tlačítko

Pokud potřebujete **vytvořit Word dokument programově**, tento průvodce vás provede celým procesem s Aspose.Words pro .NET. Také se naučíte, jak **přidat ActiveX ovládací prvky Wordu** a **vložit ActiveX tlačítko CommandButton** v jednom samostatném příkladu.

Generování souborů Word z kódu odstraňuje ruční krok otevření Microsoft Word, což vám umožní automaticky vytvářet zprávy, faktury nebo smlouvy řízené daty. Na konci tohoto tutoriálu budete mít připravenou spustitelnou C# konzolovou aplikaci, která vytvoří soubor `.docx` obsahující interaktivní ActiveX CommandButton.

## Požadavky

* .NET 6.0 SDK nebo novější (kód také funguje s .NET Framework 4.6+)
* Visual Studio 2022 nebo jakékoli IDE, které podporuje vývoj v .NET
* Platná licence Aspose.Words pro .NET (pro testování můžete použít bezplatný evaluační klíč)
* Základní znalost syntaxe C# a konceptu COM/ActiveX ovládacích prvků

> **Tip:** Pokud plánujete distribuovat vygenerovaný dokument uživatelům, kteří nemají nainstalovaný Word, vložte runtime soubory ActiveX ovládacího prvku vedle souboru `.docx` nebo poskytněte šablonu s povolenými makry.

## Vytvořte Word dokument programově – počáteční nastavení

Nejprve přidejte NuGet balíček Aspose.Words do svého projektu:

```bash
dotnet add package Aspose.Words
```

Poté vytvořte nový konzolový projekt (pokud jej ještě nemáte):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Otevřete vygenerovaný soubor `Program.cs` – nahradíme jeho obsah kompletním řešením níže.

## Krok 1: Importujte jmenné prostory a nakonfigurujte licenci

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Proč je to důležité*: Importování `Aspose.Words.Drawing` vám poskytuje přístup k `Forms2OleControl`, třídě, která představuje ActiveX ovládací prvek uvnitř Word dokumentu. Nastavení licence na začátku zabraňuje varováním během běhu v produkci.

## Krok 2: Vytvořte prázdný dokument a DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Objekt `Document` je v‑paměti reprezentace souboru `.docx`. `DocumentBuilder` funguje jako kurzor, který můžete po dokumentu pohybovat a vkládat do něj prvky.

## Krok 3: Vložte ActiveX CommandButton ovládací prvek

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` vytvoří OLE objekt, který Word považuje za ActiveX ovládací prvek. Souřadnicový systém používá body (1 bod = 1/72 palce), což odpovídá layoutovému enginu Wordu.

## Krok 4: Nastavte popisek tlačítka a volitelné vlastnosti

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Nastavení vlastnosti `Caption` je nejčastější způsob, jak pojmenovat tlačítko. Pokud potřebujete, aby tlačítko spouštělo VBA makro, přiřaďte název makra do `OnAction`. Tento tutoriál se zaměřuje na vizuální část; integrace makra je popsána v sekci „Další kroky“.

## Krok 5: Uložte dokument

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Po spuštění programu uvidíte zprávu v konzoli, která potvrzuje, že soubor `ActiveX_CommandButton.docx` byl zapsán na disk.

### Kompletní zdrojový kód (připravený ke kopírování)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Spuštěním úryvku vznikne Word soubor, který obsahuje klikatelné **ActiveX command button**. Otevřete soubor v Microsoft Word, přepněte do **Design Mode** (karta Developer → Design Mode) a uvidíte tlačítko vykreslené přesně tam, kam jste jej umístili.

## Krok 6: Ověřte výsledek

1. Otevřete `ActiveX_CommandButton.docx` v Microsoft Word.
2. Povolení karty **Developer**, pokud není viditelná (`File → Options → Customize Ribbon → zaškrtněte Developer`).
3. Klikněte na **Design Mode**. Tlačítko by se mělo zobrazit s popiskem „Submit“.
4. Pokud jste přidali makro `OnAction`, klikněte na tlačítko při vypnutém Design Mode, aby se spustilo makro.

Pokud se tlačítko nezobrazí, ujistěte se, že nastavení zabezpečení Wordu povoluje ActiveX ovládací prvky (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Časté otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Mohu vložit jiné typy ActiveX?** | Ano. výčet `Forms2OleControlType` zahrnuje `CheckBox`, `OptionButton`, `ComboBox` atd. Nahraďte `CommandButton` požadovanou hodnotou výčtu |

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit skupinový tvar ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvořit Word dokument s hlavičkou a patičkou pomocí Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Vložit vložený obrázek do Word dokumentu pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}