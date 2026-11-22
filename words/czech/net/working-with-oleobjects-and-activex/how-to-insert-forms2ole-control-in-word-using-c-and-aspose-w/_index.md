---
category: general
date: 2026-11-22
description: Naučte se vložit ovládací prvek Forms2Ole do Wordu pomocí C#. Tento krok‑za‑krokem
  průvodce zahrnuje DocumentBuilder, umístění příkazového tlačítka a ukládání souboru
  .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: cs
lastmod: 2026-11-22
og_description: Vložte ovládací prvek Forms2Ole do Wordu pomocí C#. Postupujte podle
  tohoto návodu, abyste přidali příkazové tlačítko pomocí Aspose.Words a DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Vložení ovládacího prvku Forms2Ole do Wordu pomocí C# – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vložit ovládací prvek Forms2Ole do Wordu pomocí C# a Aspose.Words
url: /cs/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit ovládací prvek Forms2Ole do Wordu pomocí C# a Aspose.Words

Pokud potřebujete **vložit ovládací prvek Forms2Ole do Wordu**, tento tutoriál vám přesně ukáže, jak to provést pomocí C#. Ať už vytváříte vyplnitelnou šablonu nebo automatizujete tvorbu formulářů, níže uvedené řešení vám umožní programově přidat tlačítko příkazu.

Naučíte se, jak vytvořit prázdný dokument, použít `DocumentBuilder` k umístění ovládacího prvku a výsledek uložit jako `.docx`. Průvodce také pokrývá běžné úskalí, jako jsou souřadnicové systémy a kompatibilita se staršími verzemi Wordu.

## Požadavky

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
* Aspose.Words pro .NET (NuGet balíček `Aspose.Words`)
* Základní znalost C# a objektového modelu Wordu
* IDE jako Visual Studio nebo VS Code

## Krok 1: Nastavení projektu a importování jmenných prostorů

Vytvořte novou konzolovou aplikaci a přidejte balíček Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

V souboru `Program.cs` importujte požadované jmenné prostory:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Tip:** Použijte nejnovější verzi Aspose.Words, abyste získali plnou podporu pro API `Forms2OleControl`.

## Krok 2: Vytvoření prázdného dokumentu a inicializace DocumentBuilder

Třída `Document` představuje soubor Word, zatímco `DocumentBuilder` poskytuje metody pro vkládání obsahu.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funguje jako kurzor; po tomto řádku můžete začít umisťovat prvky kdekoliv v dokumentu.

## Krok 3: Definování pozice a velikosti tlačítka

Word měří souřadnice v bodech (1 pt ≈ 1/72 palce). Struktura `Rectangle` z `System.Drawing` popisuje ohraničení ovládacího prvku.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` umístí ovládací prvek do levého horního rohu aktuální stránky.
* Upravením `x` a `y` tlačítko přesunete jinam (např. `new Rectangle(150, 200, 100, 30)`).

## Krok 4: Vložení příkazového tlačítka Forms2Ole

Nyní použijte `InsertForms2OleControl` k přidání ovládacího prvku. Metoda vyžaduje typ ovládacího prvku, název a výše definované ohraničení.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Vrácený objekt `Forms2OleControl` vám umožní měnit vlastnosti jako `Enabled`, `Visible` nebo později přiřadit název makra.

### Proč používat Forms2Ole?

* **Kompatibilita se staršími verzemi** – Ovládací prvky Forms2Ole fungují ve Wordu 97‑2003 (`.doc`) i v novějších souborech `.docx`.
* **Podpora maker** – Mohou spouštět VBA makra, což je činí ideálními pro interaktivní šablony.
* **Přesné umístění** – Na rozdíl od obsahových ovládacích prvků máte kontrolu nad přesnými souřadnicemi.

## Krok 5: Uložení dokumentu

Nakonec zapište soubor na disk. Vyberte složku, do které máte právo zápisu.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Otevřete `output.docx` v Microsoft Wordu. Uvidíte tlačítko označené **ClickMe** v levém horním rohu první stránky. Kliknutí na něj ve Wordu nic neudělá, dokud mu nepřiřadíte makro, ale ovládací prvek je plně funkční.

## Řešení běžných okrajových případů

| Situace | Jak to řešit |
|-----------|-------------------|
| **Tlačítko se zobrazuje mimo stránku** | Ověřte, že souřadnice `Rectangle` jsou v mezích okrajů stránky. Použijte `builder.PageSetup.PageWidth` a `PageHeight` k výpočtu bezpečných ohraničení. |
| **Ovládací prvek není viditelný ve starších verzích Wordu** | Uložte dokument jako `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) pro zajištění kompatibility Forms2Ole s Wordem 97‑2003. |
| **Potřeba změnit popisek** | Po vložení nastavte `commandButton.Caption = "Submit";`. |
| **Přiřadit makro** | Nastavte `commandButton.MacroName = "MyMacro"`; makro musí existovat v VBA projektu dokumentu. |
| **Více tlačítek** | Opakujte Krok 4 s různými hodnotami `Rectangle` a unikátními názvy. |

## Kompletní, spustitelný příklad

Spojením všech částí získáte samostatný program, který můžete zkopírovat, vložit a spustit:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výstup:** Po spuštění programu se `output.docx` otevře ve Wordu s klikacím tlačítkem označeným *Click Me!* umístěným v levém horním rohu první stránky.

## Závěr

Nyní víte, jak **vložit ovládací prvek Forms2Ole do Wordu** pomocí C# a Aspose.Words. Proces zahrnuje vytvoření `Document`, umístění `Rectangle` a volání `InsertForms2OleControl` přes `DocumentBuilder`. S kompletním ukázkovým kódem a radami pro okrajové případy můžete integrovat tlačítka příkazů do jakéhokoli automatizovaného pracovního postupu ve Wordu.

### Další kroky

* Prozkoumejte další hodnoty `ControlType`, jako jsou `CheckBox` nebo `OptionButton`.
* Kombinujte ovládací prvky Forms2Ole s VBA makry pro interaktivní formuláře.
* Použijte `DocumentBuilder.MoveTo` k umístění tlačítek do konkrétních odstavců nebo tabulek.
* Projděte dokumentaci Aspose.Words **Forms2Ole** pro pokročilá nastavení vlastností.

Šťastné programování a užívejte si tvorbu bohatších Word dokumentů s C# a Aspose.Words!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vložit OLE příkazové tlačítko do Word dokumentu pomocí C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [jak přidat ActiveX ovládací prvek do Wordu s Aspose.Words – krok za krokem](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Přidat tlačítko příkazu do Word dokumentu s Aspose.Words – kompletní průvodce](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}