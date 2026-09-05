---
category: general
date: 2026-09-05
description: Vytvořte obdélníkový tvar v dokumentu Word pomocí Aspose.Words, poté
  se naučte, jak vložit elipsu a seskupit tvary ve Wordu pro bohatší rozvržení.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: cs
lastmod: 2026-09-05
og_description: Vytvořte obdélníkový tvar v dokumentu Word pomocí Aspose.Words, poté
  zjistěte, jak vložit elipsu a seskupit tvary ve Wordu pro složité rozvržení.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Vytvořte obdélníkový tvar a seskupte tvary ve Wordu – průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vytvořit obdélníkový tvar a seskupit tvary ve Wordu pomocí Aspose.Words
url: /cs/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit obdélníkový tvar a seskupit tvary ve Wordu s Aspose.Words

Pokud potřebujete **vytvořit obdélníkový tvar** ve Word dokumentu, tento průvodce vám ukáže přesné kroky s Aspose.Words pro .NET. Také uvidíte, jak vložit elipsu, seskupit tvary ve Wordu a uložit výsledek jako soubor DOCX. Řešení funguje v libovolném projektu .NET 6+ a nevyžaduje, aby byl na serveru nainstalován Microsoft Office.

Tutoriál pokrývá vše od nastavení projektu po řešení běžných problémů s rozvržením, takže můžete kód zkopírovat a okamžitě spustit.

## Požadavky

* .NET 6 SDK nebo novější nainstalováno  
* IDE kompatibilní s NuGet (Visual Studio, Rider nebo VS Code)  
* Licence Aspose.Words pro .NET (nebo dočasný evaluační klíč)  
* Základní znalosti C# a struktury Word dokumentu  

Tyto položky umožní, aby se kód zkompiloval a tvary se vykreslily správně.

## Krok 1: Nastavte projekt a přidejte Aspose.Words

Vytvořte nový konzolový projekt a přidejte balíček Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Balíček poskytuje třídy `Document`, `DocumentBuilder`, `Shape` a `GroupShape`, které jsou používány v celém tomto tutoriálu.

## Krok 2: Inicializujte prázdný dokument a builder

`Document` objekt představuje celý Word soubor, zatímco `DocumentBuilder` vám umožňuje vkládat obsah programově.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Vytvoření dokumentu jako první zajišťuje, že všechny následné operace s tvary mají platný kontejner.

## Krok 3: **Vytvořit obdélníkový tvar** a nastavit jeho rozměry

Obdélník je nejčastějším kontejnerem pro text nebo obrázky. Jeho velikost definujete v bodech (1 pt ≈ 1/72 palce).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Proč je tento krok důležitý: třída `Shape` zapouzdřuje geometrii, výplň a vlastnosti čáry. Nastavení `Width` a `Height` před vložením zaručuje, že se tvar zobrazí s očekávanou velikostí.

## Krok 4: **Jak vložit elipsu** – přidat eliptický tvar

Elipsa může být použita pro ikony, značky nebo dekorativní prvky. Kód je obdobný tvorbě obdélníku, mění se pouze `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Vlastnosti `FillColor` a `Line.Color` ukazují, jak přizpůsobit vzhled bez externích obrázků.

## Krok 5: **Seskupit tvary ve Wordu** – kombinovat obdélník a elipsu

Seskupování vám umožňuje přesouvat, měnit velikost nebo otáčet více tvarů jako jedním celkem. To je nezbytné, když potřebujete složenou grafiku (např. označenou ikonu).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Když zavoláte `AppendChild`, původní tvary jsou odstraněny z hlavního toku dokumentu a stávají se potomky `GroupShape`. Skupina se chová jako jeden tvar, což zjednodušuje následné úpravy rozvržení.

## Krok 6: Uložte dokument

Nakonec zapište dokument na disk. Můžete zvolit libovolný podporovaný formát (`.docx`, `.pdf`, `.html` atd.). Pro tento tutoriál zachováme nativní Word formát.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Po spuštění programu otevřete *GroupShape.docx* v Microsoft Word. Uvidíte obdélník a elipsu seskupené dohromady, umístěné na souřadnicích, které jste zadali.

## Běžné varianty a okrajové případy

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Různé jednotky velikosti** | Use `ConvertUtil.InchToPoint(2.5)` for inches or `ConvertUtil.MillimeterToPoint(30)` for millimetres. | Keeps code readable when you work with non‑point measurements. |
| **Přidání textu do obdélníku** | Create a `Paragraph` node, set its `Text` property, and add it to `rectangleShape` via `AppendChild`. | Allows you to label the shape without separate text boxes. |
| **Otáčení skupiny** | Set `groupShape.Rotation = 45;` (degrees). | Useful for creating diagonal badges or watermarks. |
| **Uložení jako PDF** | Call `doc.Save("GroupShape.pdf");`. | Aspose.Words automatically rasterizes vector shapes for PDF output. |
| **Více skupin** | Create additional `GroupShape` instances and repeat the append/insert steps. | Enables complex page layouts with several independent composites. |

### Profesionální tip

Vždy přidávejte tvary **před** jejich seskupením. Pokud se pokusíte seskupit tvar, který již patří do jiné skupiny, Aspose.Words vyhodí `ArgumentException`. Vytvoření skupiny v jedné metodě tomuto runtime chybě předchází.

### Na co si dát pozor

* **Systém souřadnic** – `Left` a `Top` jsou měřeny od levého a horního okraje stránky, nikoli od okraje dokumentu. Nesprávné pochopení může umístit tvary mimo stránku.
* **Licencování** – Bez platné licence bude uložený dokument obsahovat vodoznak s textem “Aspose.Words for .NET Evaluation”. Aplikujte svou licenci brzy v kódu (`License license = new License(); license.SetLicense("Aspose.Words.lic");`), abyste se tomu vyhnuli.

## Kompletní zdrojový kód (spustitelný)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spuštěním tohoto programu vznikne *GroupShape.docx* se seskupenými tvary přesně tak, jak je popsáno.

## Závěr

Nyní víte, jak **vytvořit obdélníkový tvar**, **vložit elipsu** a **seskupit tvary ve Wordu** pomocí Aspose.Words. Kompletní příklad demonstruje celý pracovní postup – od inicializace dokumentu po uložení finálního souboru – takže můžete začlenit práci s tvary do jakéhokoli automatizovaného reportingu nebo řešení pro generování dokumentů.

### Co dál?

* Prozkoumejte **aspose.words create shapes** pro složitější geometrie jako `Polygon` nebo `Freeform`.  
* Kombinujte seskupené tvary s **content controls** pro tvorbu dynamických šablon.  
* Převádějte DOCX na PDF nebo HTML a podívejte se, jak jsou vektorové tvary vykreslovány v různých formátech.  

Neváhejte experimentovat s různými velikostmi, barvami a rotacemi. Jakmile ovládnete seskupování tvarů, můžete vytvářet sofistikované diagramy, odznaky a vlastní UI prvky přímo ve Word dokumentech.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit skupinový tvar ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vložit tvary do Word dokumentů pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}