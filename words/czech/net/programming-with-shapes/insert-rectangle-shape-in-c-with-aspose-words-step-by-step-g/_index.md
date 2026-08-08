---
category: general
date: 2026-08-07
description: Vložte obdélníkový tvar v C# pomocí Aspose.Words a naučte se, jak skrýt
  tvar, nastavit barvu výplně a efektivně přidat obdélníkový tvar do dokumentu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: cs
lastmod: 2026-08-07
og_description: Vložte obdélníkový tvar do dokumentu Word pomocí C#. Naučte se, jak
  skrýt tvar, nastavit barvu výplně a přidat obdélníkový tvar pomocí Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Vložení obdélníkového tvaru v C# – kompletní tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Vložení obdélníkového tvaru v C# s Aspose.Words – krok za krokem
url: /cs/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení obdélníkového tvaru v C# s Aspose.Words – krok za krokem průvodce

Pokud potřebujete **vložit obdélníkový tvar** do dokumentu Word z C#, tento průvodce vám ukáže přesně, jak na to. Uvidíte, jak nastavit barvu výplně, skrýt tvar, aby se neobjevil v konečném rozvržení, a jak soubor uložit – vše pomocí několika řádků kódu.

V následujících sekcích pokryjeme vše, co potřebujete vědět: předpoklady, kompletní výpis kódu, vysvětlení jednotlivých kroků a tipy pro běžné varianty, jako je opětovné zviditelnění tvaru nebo použití jiné barvy. Na konci budete schopni **přidat obdélníkový tvar** do libovolného .docx souboru programově.

## Předpoklady

Než začnete, ujistěte se, že máte:

* **Aspose.Words for .NET** (verze 23.10 nebo novější). Můžete jej nainstalovat přes NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK nebo novější nainstalovaný na vašem počítači.
* Základní znalosti C# a Visual Studio (nebo libovolného IDE, které preferujete).

Žádné další knihovny nejsou potřeba – API související s tvary jsou součástí hlavního balíčku Aspose.Words.

## Vložení obdélníkového tvaru s Aspose.Words

Jádrem řešení je krátký, samostatný program, který vytvoří prázdný dokument, vloží obdélník, obarví jej, skryje a poté soubor uloží. Níže je kompletní zdrojový kód s inline komentáři, které vysvětlují *proč* za každým řádkem.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Co jednotlivé kroky dělají

| Krok | Důvod |
|------|-------|
| **Vytvořit nový dokument** | Poskytuje čisté plátno; můžete také načíst existující .docx zadáním cesty k souboru do `new Document(path)`. |
| **Inicializovat DocumentBuilder** | `DocumentBuilder` je vysoceúrovňový pomocník, který vám umožní vkládat text, tabulky a tvary, aniž byste se museli zabývat nízkoúrovňovými uzly. |
| **Vložit obdélníkový tvar** | Metoda `InsertShape` vrací objekt `Shape`, který můžete dále přizpůsobovat (velikost, pozice, okraje atd.). |
| **Nastavit barvu výplně** | Vlastnost `FillColor` řídí barvu výplně; můžete použít libovolnou hodnotu `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)` atd.). |
| **Skrýt tvar** | `Hidden = true` říká Wordu, aby během rozvržení tvar ignoroval, ale stále jej ponechá v XML dokumentu. Toto je standardní způsob, jak uložit neviditelné objekty. |
| **Uložit dokument** | Uloží změny do souboru .docx. Uložený soubor bude obsahovat skrytý obdélníkový tvar. |

## Jak nastavit barvu výplně pro tvar

Změna barvy výplně je tak jednoduchá, jako přiřadit `System.Drawing.Color` k vlastnosti `FillColor`. Pokud potřebujete vlastní odstín, použijte `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Proč je to důležité*: Barva výplně je uložena v XML tvaru (`<w:fill>` atribut). Když je tvar skrytý, barva stále existuje, což může být užitečné pro následné zpracování (např. extrakci metadat na základě kódů barev).

## Jak skrýt tvar v konečném dokumentu

Příznak `Hidden` je booleanová vlastnost třídy `Shape`. Nastavením na `true` zajistíte, že tvar bude Wordovým rozvrhovým enginem ignorován.

```csharp
rectangleShape.Hidden = true;
```

**Časté úskalí**

* **Hidden vs. Visible** – Pokud později potřebujete, aby se tvar zobrazil, jednoduše nastavte `Hidden = false`.
* **Kompatibilita** – Starší verze Wordu (před 2007) mohou skryté kreslicí objekty zpracovávat odlišně. Aspose.Words zachovává kompatibilitu ukládáním příznaku do příslušného OOXML elementu.

## Jak programově vložit tvar

I když příklad používá obdélník, stejná metoda `InsertShape` funguje pro mnoho dalších tvarů (elipsa, trojúhelník, čára atd.). Prvním argumentem je hodnota výčtu `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tip**: Pokud potřebujete umístit tvar na konkrétní místo na stránce, použijte `builder.MoveTo` k nastavení vkládacího bodu před voláním `InsertShape`.

## Přidání obdélníkového tvaru do existujícího dokumentu

Často budete rozšiřovat šablonu místo vytváření nového souboru od nuly. Nahraďte krok 1 tímto:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Všechny následující kroky zůstávají beze změny a obdélník bude přidán tam, kde je kurzor builderu umístěn (obvykle na konci dokumentu).

## Řešení okrajových případů a variant

### 1. Zviditelnění tvaru

Pokud pozdější část vašeho workflow potřebuje odhalit skrytý obdélník, můžete přepnout příznak:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Přidání okraje (stroke)

Skrytý tvar může mít stále viditelný okraj, když se rozhodnete jej zobrazit. Nastavte vlastnosti `LineColor` a `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Absolutní umístění obdélníku

Pro přesnou kontrolu rozvržení přepněte `WrapType` tvaru na `WrapType.Inline` (výchozí) nebo `WrapType.TopBottom` a upravte vlastnosti `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Použití jiné jednotky měření

Aspose.Words pracuje v bodech (1 pt = 1/72 palce). Pokud dáváte přednost centimetrům, nejprve proveďte převod:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Kompletní spustitelný příklad

Níže je *úplný* program, který můžete zkopírovat, vložit a spustit. Obsahuje všechny potřebné `using` direktivy a používá absolutní cesty, které byste měli upravit podle svého prostředí.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Očekávaný výsledek**: Soubor `HiddenRectangleShape.docx` se otevře v Microsoft Word s *žádným viditelným tvarem*, ale skrytý obdélník bude přítomen v XML dokumentu. Jeho existenci můžete ověřit otevřením .docx jako zip archivu a kontrolou `word/document.xml` na element `<w:shape>` s atributy `w:fill="yellow"` a `w:hidden="true"`.

## Závěr

Nyní víte, jak **vložit obdélníkový tvar** do dokumentu Word pomocí C# a Aspose.Words, jak **nastavit barvu výplně** a jak **skrýt tvar**, aby zůstal neviditelný v konečném rozvržení. Stejný vzor funguje i pro jiné typy tvarů, vlastní barvy a existující šablony. Experimentujte s okraji, absolutním umístěním a různými jednotkami měření, abyste tvar přizpůsobili přesně svým požadavkům.

### Další kroky

* Prozkoumejte **jak vložit tvar** uvnitř tabulek nebo záhlaví/patiček pro vodoznaky.
* Kombinujte **přidání obdélníkového tvaru** s ovládacími prvky obsahu pro vytvoření dynamických zástupných míst.
* Projděte si API Aspose.Words **shape manipulation** pro pokročilé funkce jako rotace, gradientní výplně a import SVG.

Neváhejte přizpůsobit kód svému projektu a dejte nám vědět v komentářích, jaký další tvar‑souvisící problém jste vyřešili!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}