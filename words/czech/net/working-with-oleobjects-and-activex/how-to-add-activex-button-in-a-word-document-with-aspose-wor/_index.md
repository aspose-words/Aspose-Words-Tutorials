---
category: general
date: 2026-08-14
description: Jak přidat tlačítko ActiveX do dokumentu Word pomocí Aspose.Words – naučte
  se vytvořit prázdný dokument Word a programově vložit tlačítko ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: cs
lastmod: 2026-08-14
og_description: Jak přidat tlačítko ActiveX do dokumentu Word pomocí Aspose.Words.
  Tento tutoriál vám ukáže, jak vytvořit prázdný dokument Word, vložit tlačítko ActiveX
  a uložit výsledek.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Jak přidat tlačítko ActiveX ve Wordu – průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Jak přidat tlačítko ActiveX do dokumentu Word s Aspose.Words
url: /cs/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat ActiveX tlačítko do dokumentu Word pomocí Aspose.Words

Pokud potřebujete **jak přidat ActiveX** ovládací prvky do generovaného souboru Word, tento průvodce vám ukáže přesné kroky. Naučíte se **programově vložit ActiveX tlačítko**, počínaje **vytvořením prázdného dokumentu Word** a konče uloženým souborem, který lze otevřít v Microsoft Word.

Přidání tlačítka, které spouští VBA kód nebo aktivuje makro, je běžnou požadavkem pro automatické generátory reportů, šablony formulářů nebo interaktivní smlouvy. Použití Aspose.Words pro .NET vám umožní vytvořit dokument bez spouštění Office, což proces zrychlí a je přátelské k serverům.

## Požadavky

* .NET 6.0 (nebo novější) SDK nainstalováno.
* Visual Studio 2022 nebo jakékoli IDE kompatibilní s C#.
* NuGet balíček Aspose.Words pro .NET (`Aspose.Words` verze 24.9 nebo novější).  
  Nainstalujte jej pomocí:
  ```bash
  dotnet add package Aspose.Words
  ```
* Windows prostředí, pokud plánujete testovat ActiveX tlačítko, protože ActiveX ovládací prvky vyžadují Windows verzi Microsoft Word.

## Krok 1: Vytvoření prázdného dokumentu Word

Prvním úkolem je **vytvořit prázdný dokument Word** v paměti. Aspose.Words poskytuje třídu `Document` pro tento účel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` představuje celý soubor .docx. V tomto okamžiku dokument neobsahuje žádné stránky, ale můžete okamžitě začít přidávat obsah.

## Krok 2: Inicializace DocumentBuilder

`DocumentBuilder` je pomocník, který vám umožňuje vkládat text, obrázky a další objekty do dokumentu. Pracuje s instancí `Document`, kterou jste právě vytvořili.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder udržuje pozici kurzoru; vše, co vložíte po tomto řádku, se objeví na začátku první stránky.

## Krok 3: Vložení ActiveX CommandButton ovládacího prvku

Aspose.Words poskytuje metodu `InsertForms2OleControl` pro přidání starších formulářových ovládacích prvků, včetně ActiveX. Metoda vyžaduje typ ovládacího prvku a jeho velikost v bodech.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Vrácený objekt `Forms2OleControl` vám umožňuje nastavit vlastnosti, jako je název ovládacího prvku a popisek.

## Krok 4: Konfigurace vlastností tlačítka

Nastavení smysluplného `Name` vám umožní později odkazovat na ovládací prvek z VBA kódu. `Caption` je text, který uživatel vidí na tlačítku.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Tip:** Udržujte název krátký a alfanumerický; Word odmítne názvy, které obsahují mezery nebo speciální znaky.

## Krok 5: Uložení dokumentu

Nakonec dokument zapište na disk. Použijte příponu `.docx` pro moderní soubory Word; ActiveX tlačítko funguje stejně v souborech `.doc`, ale `.docx` je preferovaný formát pro nové projekty.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Když otevřete `ActiveXButton.docx` v Microsoft Word, uvidíte klikatelné **Submit** tlačítko. Pokud povolíte makra, můžete připojit VBA kód k `btnSubmit_Click` a nechat jej spustit, když uživatel na tlačítko klikne.

## Kompletní, spustitelný příklad

Sestavením všech částí dohromady získáte samostatný program, který můžete zkopírovat, vložit a spustit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výstup** – Po spuštění programu konzole vypíše umístění uložení a otevření vygenerovaného souboru ve Wordu zobrazí tlačítko s popiskem **Submit** umístěné v horní části první stránky.

## Řešení častých otázek a okrajových případů

### Funguje tlačítko ve všech verzích Wordu?

ActiveX ovládací prvky jsou podporovány v desktopové verzi Wordu na Windows. V Word Online, Word pro macOS ani v mobilních klientech se nezobrazují. Pokud potřebujete multiplatformní interaktivitu, zvažte místo toho použití obsahových ovládacích prvků nebo HTML‑založených řešení.

### Co když potřebuji jinou velikost nebo pozici?

`InsertForms2OleControl` umístí ovládací prvek na aktuální kurzor builderu. Pro jeho přesunutí upravte kurzor pomocí `builder.MoveTo` před vložením, nebo po vytvoření změňte vlastnosti `Left` a `Top` ovládacího prvku:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Mohu přidat jiné typy ActiveX?

Ano. Výčtový typ `Forms2OleControlType` zahrnuje `CheckBox`, `OptionButton`, `ListBox` a další. Nahraďte `CommandButton` požadovanou hodnotou výčtu a podle toho upravte vlastnosti.

### Je pro funkci tlačítka vyžadováno makro?

Tlačítko samo o sobě nic nedělá, dokud k němu nepřipojíte VBA kód. Ve Wordu stiskněte **Alt+F11** pro otevření VBA editoru, najděte `btnSubmit_Click` a napište požadovanou logiku. Vygenerovaný dokument si zachová VBA projekt, pokud povolíte formát **SaveFormat.Doc** (legacy `.doc`), ale soubory `.docx` nemohou ukládat VBA makra. Použijte formát `.doc`, pokud potřebujete vložené VBA.

## Závěr

Nyní víte **jak přidat ActiveX** ovládací prvky do souboru Word pomocí Aspose.Words. Dodržením kroků **vytvořit prázdný dokument Word**, inicializovat `DocumentBuilder`, **vložit ActiveX tlačítko**, nakonfigurovat jeho vlastnosti a soubor uložit, můžete přímo z vašeho .NET kódu generovat interaktivní šablony Word.

Dále prozkoumejte související témata, jako je **insert ActiveX button** zpracování událostí, přidání **create word document aspose** pro tabulky nebo obrázky a zabezpečení dokumentů s povolenými makry pro podnikové nasazení. Experimentujte s různými typy ovládacích prvků a možnostmi rozvržení, abyste přizpůsobili uživatelský zážitek potřebám vaší aplikace.

Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními krok za krokem, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření dokumentu Word s hlavičkou a patičkou pomocí Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Vytvoření skupinového tvaru v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvoření dokumentu Word s tabulkou pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}