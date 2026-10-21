---
category: general
date: 2026-09-21
description: Naučte se, jak vytvořit ActiveX tlačítko příkazu v dokumentu Wordu pomocí
  Aspose.Words a C#. Průvodce krok po kroku zahrnuje vložení, umístění a uložení.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: cs
lastmod: 2026-09-21
og_description: Vytvořte ActiveX příkazové tlačítko v dokumentu Word pomocí C# a Aspose.Words.
  Postupujte podle tohoto kompletního tutoriálu, abyste tlačítko vložili, umístili
  a uložili programově.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Vytvořte tlačítko příkazu ActiveX ve Wordu pomocí C# – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Jak vytvořit ActiveX tlačítko příkazu ve Wordu pomocí C#
url: /cs/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit tlačítko příkazu ActiveX ve Wordu pomocí C#

Pokud potřebujete **vytvořit tlačítko příkazu ActiveX** uvnitř souboru Word, tento průvodce vám ukáže přesné kroky. Pomocí Aspose.Words pro .NET můžete tlačítko přidat, umístit a nakonfigurovat kompletně z C# kódu.

Programatické vložení tlačítka ActiveX eliminuje ruční práci s UI a umožňuje automatizovanou tvorbu dokumentů pro formuláře, zprávy nebo interaktivní šablony. V tomto tutoriálu se naučíte, jak použít **DocumentBuilder**, metodu **InsertForms2OleControl** a související vlastnosti k vytvoření plně funkčního tlačítka.

## Co budete potřebovat

* .NET 6.0 SDK nebo novější (kód také funguje s .NET Framework 4.7+)
* Aspose.Words pro .NET (NuGet balíček `Aspose.Words`)
* IDE, např. Visual Studio 2022 nebo VS Code
* Základní znalost C# a konceptů Word dokumentů

Další instalace Office není vyžadována, protože Aspose.Words funguje nezávisle na Microsoft Word.

## Krok 1: Nastavení projektu C#

Vytvořte nový konzolový projekt a přidejte balíček Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Knihovna `Aspose.Words` poskytuje třídu **DocumentBuilder**, kterou použijeme k manipulaci s dokumentem.

## Krok 2: Inicializace dokumentu a builderu

První blok kódu vytvoří prázdný dokument a instanci `DocumentBuilder`. Tento objekt je vstupním bodem pro všechny operace zpracování Wordu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:** `DocumentBuilder` udržuje aktuální pozici kurzoru, takže jakékoli následné vložení se objeví přesně tam, kde kurzor umístíte.

## Krok 3: Vložení tlačítka příkazu ActiveX

Metoda **InsertForms2OleControl** vytvoří ActiveX ovládací prvek požadovaného typu. Zde požadujeme `CommandButton` a specifikujeme jeho velikost v bodech (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Vysvětlení:**  
* `OleControlType.CommandButton` říká Aspose.Words, aby vytvořil tlačítko místo jiného typu ovládacího prvku.  
* Metoda vrací objekt `Forms2OleControl`, který poskytuje pole pro pozicování a vlastnosti.

## Krok 4: Umístění tlačítka a nastavení jeho vlastností

Po vložení můžete tlačítko přesunout na libovolné místo na stránce a přiřadit mu programový název a viditelný popisek.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Tip:** Souřadnicový systém začíná v levém horním rohu stránky. Upravit `Left` a `Top` pro zarovnání tlačítka s ostatními formulářovými poli.

## Krok 5: Uložení dokumentu

Nakonec zapíšete dokument na disk. Soubor bude obsahovat tlačítko ActiveX, připravené k otevření v Microsoft Word, kde se tlačítko stane interaktivním.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Když otevřete `ActiveXCommandButton.docx` ve Wordu, uvidíte tlačítko označené **Submit** na určeném místě. Kliknutí na něj ve Wordu spustí výchozí chování tlačítka (které můžete později přizpůsobit pomocí VBA nebo doplňků Word).

## Kompletní, spustitelný příklad

Sestavením všech částí dohromady získáte samostatný program, který můžete zkopírovat, vložit a spustit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Očekávaný výstup:** Konzole vypíše *„Document created successfully.“* a složka nyní obsahuje `ActiveXCommandButton.docx`. Otevřením souboru v Microsoft Word se zobrazí klikatelné tlačítko **Submit** umístěné 100 pt od levého okraje a 150 pt od horního okraje stránky.

## Časté úskalí a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|---------|---------------------|--------|
| Tlačítko se zobrazuje mimo stránku | Hodnoty `Left`/`Top` překračují rozměry stránky | Použijte `doc.FirstSection.PageSetup.PageWidth` a `PageHeight` k výpočtu bezpečných souřadnic |
| Tlačítko není ve Wordu viditelné | Dokument byl uložen ve formátu, který odstraňuje ActiveX ovládací prvky (např. `.txt`) | Vždy ukládejte jako `.docx` nebo `.doc` |
| Chyba běhu `ArgumentOutOfRangeException` | Šířka nebo výška je nastavena na nulu nebo zápornou hodnotu | Zajistěte, aby argumenty velikosti předávané do `InsertForms2OleControl` byly kladná čísla |

## Rozšíření řešení

Můžete tlačítko dále přizpůsobit nastavením dalších vlastností, jako jsou `Enabled`, `Visible`, nebo připojením makra pomocí VBA. Třída **Forms2OleControl** vám také umožní vložit jiné ActiveX ovládací prvky, jako jsou zaškrtávací políčka (`OleControlType.CheckBox`) nebo rozbalovací seznamy (`OleControlType.ComboBox`).

Pokud potřebujete v cyklu generovat více tlačítek, zabalte logiku vkládání do pomocné metody:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Závěr

Nyní víte, jak **vytvořit tlačítko příkazu ActiveX** v dokumentu Word pomocí C# a Aspose.Words. Tutoriál pokryl nastavení projektu, vložení tlačítka pomocí `InsertForms2OleControl`, jeho umístění a uložení finálního souboru. S tímto základem můžete automatizovat složité formuláře, vkládat interaktivní ovládací prvky a integrovat Word dokumenty do větších .NET řešení.

Dále prozkoumejte související témata, jako jsou **Aspose.Words ActiveX** formulářová pole, pokročilé stylování **C# DocumentBuilder**, nebo programové přidávání **ActiveX ovládacího prvku ve Wordu** pro zaškrtávací políčka a rozbalovací seznamy. Experimentujte s různými souřadnicemi a velikostmi, aby vyhovovaly vašim konkrétním požadavkům na rozvržení. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Word dokument pomocí Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Vytvořit obdélníkový tvar ve Wordu s Aspose.Words – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Vytvořit Word dokument s tabulkou pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}