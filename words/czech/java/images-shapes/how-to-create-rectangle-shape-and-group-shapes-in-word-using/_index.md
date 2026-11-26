---
category: general
date: 2026-11-18
description: Naučte se, jak vytvořit obdélníkový tvar ve Word dokumentu pomocí C#.
  Průvodce také pokrývá nastavení velikosti tvaru, nastavení pozice tvaru a seskupování
  tvarů ve Wordu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: cs
lastmod: 2026-11-18
og_description: Vytvořte obdélníkový tvar v souboru Word pomocí C# a naučte se nastavit
  rozměry tvaru, jeho pozici a seskupovat tvary ve Wordu.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Vytvořte obdélníkový tvar a seskupte tvary ve Wordu pomocí C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vytvořit obdélníkový tvar a seskupit tvary ve Wordu pomocí C#
url: /cs/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit obdélníkový tvar a seskupit tvary ve Wordu pomocí C#

Pokud potřebujete **vytvořit obdélníkový tvar** v dokumentu Word, tento tutoriál vám ukáže kompletní, připravené řešení. Uvidíte, jak nastavit velikost tvaru, jeho pozici a jak seskupit tvary ve Wordu tak, aby se chovaly jako jeden objekt.

Práce s tvary je častým požadavkem při programovém generování zpráv, faktur nebo diagramů. Na konci tohoto průvodce budete schopni vygenerovat soubor `.docx`, který obsahuje obdélník, elipsu a seskupený kontejner – vše vytvořené pomocí Aspose.Words pro .NET.

## Požadavky

- .NET 6.0 SDK nebo novější (kód funguje také s .NET Framework 4.7+)
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)
- Editor kódu nebo IDE (Visual Studio, VS Code, Rider, atd.)

Žádné další knihovny nejsou potřeba.

## Jak vytvořit obdélníkový tvar a seskupit tvary ve Wordu

Základní kroky jsou:

1. **Vytvořit prázdný dokument** a `DocumentBuilder`.
2. **Vložit `GroupShape`**, který bude obsahovat jednotlivé tvary.
3. **Vytvořit obdélníkový tvar**, nastavit jeho rozměry a přidat jej do skupiny.
4. **Vytvořit eliptický tvar**, nastavit jeho velikost a pozici a přidat jej do skupiny.
5. **Uložit** dokument.

Každý krok je podrobně vysvětlen níže a kompletní zdrojový kód následuje po vysvětlení.

### Krok 1: Inicializace dokumentu a builderu

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` představuje celý soubor Word, zatímco `DocumentBuilder` poskytuje fluent API pro vkládání obsahu. Jejich inicializace je povinná, než můžete přidat jakékoli tvary.

### Krok 2: Vložení skupinového tvaru

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` funguje jako kontejner; všechny podřízené tvary se pohybují společně. Toto je doporučený způsob, jak **seskupit tvary ve Wordu**, když potřebujete kolektivní transformace (např. přesun, otáčení nebo mazání).

### Krok 3: Vytvoření obdélníku a nastavení jeho velikosti

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Zde **vytváříme obdélníkový tvar** a **nastavujeme velikost tvaru** přiřazením `Width` a `Height`. V Aspose.Words jsou rozměry vyjádřeny v bodech (1 pt ≈ 1/72 in). Explicitní nastavení rozměrů zajišťuje, že se obdélník zobrazí přesně tak, jak má.

### Krok 4: Vytvoření elipsy, nastavení rozměrů a její pozice

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

**Nastavení rozměrů tvaru** pro elipsu je identické pro šířku i výšku, což vytváří dokonalý kruh. Vlastnost `Left` demonstruje **nastavení pozice tvaru**: elipsa začíná 120 pt vpravo od počátku skupiny, takže se nepřekrývá s obdélníkem.

### Krok 5: Uložení dokumentu

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Uložení zapíše soubor Word na disk. Soubor `GroupShape.docx` můžete otevřít v Microsoft Word a ověřit, že obdélník a elipsa jsou seskupeny a správně umístěny.

## Nastavení rozměrů a velikosti tvaru – podrobnější pohled

- **Body vs. palce**: 72 pt = 1 in. Pokud dáváte přednost palcům, vynásobte 72 (např. `2.5 * 72` pro 2,5 in).
- **Automatické škálování**: Pokud vynecháte `Width` nebo `Height`, tvar použije výchozí velikost. Explicitně **nastavte velikost tvaru**, abyste předešli překvapením v rozvržení.
- **Poměr stran**: U tvarů jako `Ellipse` zachování stejných hodnot `Width` a `Height` udržuje kruhový vzhled.

## Umístění tvaru ve Wordu

Vlastnosti `Left` a `Top` řídí posun tvaru uvnitř jeho kontejneru (skupiny nebo stránky). Kladné hodnoty posouvají tvar doprava/dolů; záporné hodnoty ho posunou doleva/nahoru. Při seskupování jsou pozice relativní k počátku skupiny, což usnadňuje výpočty rozvržení.

## Seskupování tvarů ve Wordu pomocí Aspose.Words

Seskupování je nezbytné, když chcete, aby více tvarů fungovalo jako jediná jednotka. Objekt `GroupShape`:

- Podporuje `AppendChild` pro přidání libovolného `Shape` (obdélník, elipsa, obrázek atd.).
- Umožňuje přesunout, otočit nebo smazat celou skupinu jedním voláním.
- Udržuje pozice podřízených tvarů relativně ke skupině, což usnadňuje správu složitých diagramů.

**Tip:** Po přidání všech podřízených tvarů můžete upravit `Width`, `Height`, `Left` a `Top` skupiny a tak přemístit celou kolekci najednou.

## Kompletní spustitelný příklad

Níže je celý program, který můžete zkopírovat, vložit a spustit. Obsahuje všechny `using` direktivy, metodu `Main` a komentáře, které vysvětlují každý řádek.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Očekávaný výstup:** Po spuštění programu se v pracovním adresáři objeví `GroupShape.docx`. Po otevření ve Wordu uvidíte obdélník (100 pt × 50 pt) vlevo a elipsu (80 pt × 80 pt) umístěnou 120 pt vpravo, oba uvnitř jednoho seskupeného objektu.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Snímek obrazovky dokumentu Word zobrazujícího seskupený obdélník a eliptický tvar vytvořený pomocí C#" }

*Výše uvedený obrázek ilustruje konečný výsledek; obdélník a elipsa jsou vybratelné jako jedna skupina.*

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Mohu přidat více než dva tvary?** | Ano. Zavolejte `group.AppendChild(yourShape)` pro každý další tvar. |
| **Co když potřebuji otočit skupinu?** | Použijte `group.RotationAngle = 45;` (stupně) po přidání všech podřízených. |
| **Jak změním barvu pozadí skupiny?** | Nastavte `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Bude to fungovat i se soubory .doc?** | Aspose.Words podporuje `.doc` i `.docx`. Stejný kód funguje; stačí změnit příponu v `Save`. |
| **Má seskupování vliv na paměť při velkém počtu tvarů?** | Seskupování samo o sobě přidává minimální režii. Hlavní starostí je celkový počet tvarů; u velkých dokumentů jej udržujte na rozumné úrovni. |

## Závěr

V tomto tutoriálu jste se naučili, jak **vytvořit obdélníkový tvar** v souboru Word pomocí C#, jak **nastavit velikost tvaru**, **nastavit rozměry tvaru**, **nastavit pozici tvaru** a nakonec jak **seskupit tvary ve Wordu** s Aspose.Words. Kompletní příklad ukazuje čistý, udržovatelný přístup, který můžete rozšířit na složitější diagramy, grafy nebo vlastní grafiku.

Dále můžete zkusit:

- Přidání textu uvnitř tvarů (`Shape.TextPath.Text = "Hello"`).
- Vkládání obrázků do `GroupShape`.
- Export seskupených tvarů do PDF pomocí `doc.Save("output.pdf")`.

Neváhejte experimentovat s různými velikostmi, pozicemi a dalšími typy tvarů, aby vyhovovaly potřebám vašeho projektu. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich vlastních projektech.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}