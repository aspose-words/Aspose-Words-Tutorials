---
category: general
date: 2026-09-08
description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí C#. Naučte se nastavit
  velikost tvaru, seskupit více tvarů a programově vytvořit prázdný Word dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: cs
lastmod: 2026-09-08
og_description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí C#. Tento návod
  ukazuje, jak nastavit velikost tvaru, seskupit více tvarů a programově vytvořit
  prázdný Word dokument.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Vytvořte obdélníkový tvar a seskupte tvary ve Wordu pomocí C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořte obdélníkový tvar a seskupte tvary ve Wordu pomocí C#
url: /cs/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru a seskupení tvarů ve Wordu pomocí C#

Pokud potřebujete **create rectangle shape** uvnitř souboru Word, tento tutoriál vám poskytne kompletní, připravené řešení. Uvidíte, jak nastavit velikost tvaru, seskupit více tvarů a vytvořit prázdný dokument Word od nuly — vše pomocí knihovny Aspose.Words pro .NET.

Práce s dokumenty Word programově se často připomíná žonglování mnoha drobnými detaily. Na konci tohoto průvodce budete mít jedinou metodu, která vytvoří soubor `.docx` obsahující obdélník a elipsu seskupené dohromady, připravené k dalším úpravám nebo tisku.

## Požadavky

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
* Licencovaná kopie **Aspose.Words for .NET** (můžete použít bezplatný evaluační klíč)
* IDE, například Visual Studio 2022 nebo Visual Studio Code
* Základní znalost syntaxe C#

Žádné další NuGet balíčky nejsou potřeba kromě `Aspose.Words`.

## Krok 1: Vytvoření prázdného dokumentu Word

Prvním krokem je vytvořit prázdný dokument, který bude hostit tvary. Tím se splňuje požadavek *create blank word document*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Vytvoření prázdného dokumentu vám poskytne čisté plátno. Objekt `Document` představuje celý soubor `.docx` a jeho `FirstSection.Body.FirstParagraph` je výchozí místo pro vkládání nových uzlů.

## Krok 2: Vytvoření obdélníkového tvaru

Nyní můžete přidat obdélník. Zde probíhá operace **create rectangle shape**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Nastavení rozměrů přímo odpovídá klíčovému slovu **set shape size**. Všechny hodnoty velikosti jsou vyjádřeny v bodech, což poskytuje přesnou kontrolu nad tím, jak se tvar zobrazí v konečném dokumentu.

## Krok 3: Vytvoření dalšího tvaru (elipsa)

Typickým případem použití je kombinace několika tvarů. Zde přidáváme elipsu, která bude později sdílet stejný kontejner.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Oba tvary jsou v tomto okamžiku stále nezávislé. Další krok ukazuje, jak **group multiple shapes** dohromady.

## Krok 4: Seskupení tvarů ve Wordu

Seskupení tvarů vám umožní je přesouvat, měnit jejich velikost nebo formátovat jako jednotku. Tím se splňují požadavky **group shapes in word** a **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

Vlastnost `GroupShape.Bounds` určuje souřadnicový systém pro podřízené tvary. Umístěním obdélníku a elipsy do stejného `GroupShape` je můžete později přesouvat nebo otáčet společně jedním voláním.

## Krok 5: Uložení dokumentu

Nakonec zapíšete dokument na disk. Soubor bude obsahovat seskupené tvary, které jste právě vytvořili.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Po spuštění programu otevřete `GroupedShapes.docx` v Microsoft Word. Měli byste vidět obdélník a elipsu seskupené dohromady; výběrem jednoho tvaru se vybere i druhý, což potvrzuje úspěšné seskupení.

## Kompletní zdrojový kód

Zkopírujte následující kompletní program do nového projektu typu console‑app a spusťte jej. Žádný další kód není potřeba.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Očekávaný výstup

Spuštěním programu se vytvoří `GroupedShapes.docx`. Otevřením souboru ve Wordu se zobrazí:

* **Obdélník** (100 pt × 50 pt) s modrým okrajem a světle šedým výplní.
* **Elipsa** (80 pt × 80 pt) s tmavě zeleným okrajem a světle žlutým výplní.
* Oba tvary jsou uvnitř jedné skupiny, takže přesunutí jednoho přesune i druhý.

## Časté otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Mohu do skupiny přidat více než dva tvary?** | Ano. Vytvořte další objekty `Shape` a pro každý zavolejte `group.AppendChild(yourShape)`. |
| **Co když potřebuji otočit skupinu?** | Nastavte `group.RotationAngle = 45;` (stupně). Všechny podřízené tvary se otočí společně. |
| **Je možné seskupit tvary po uložení dokumentu?** | Musíte upravit strukturu dokumentu před uložením; jinak byste museli načíst soubor, najít tvary a skupinu znovu vytvořit. |
| **Musím uvolnit nějaké objekty?** | Aspose.Words spravuje své vlastní zdroje, ale měli byste uvolnit objekty `FileStream`, pokud otevřete proudy ručně. |
| **Bude kód fungovat s formátem .doc (binárním)?** | Ano, změňte `doc.Save("output.doc")`. Chování seskupení je identické. |

## Závěr

Nyní víte, jak **create rectangle shape**, **set shape size** a **group multiple shapes** uvnitř souboru Word pomocí C#. Tento přístup vám umožní programově vytvářet složité diagramy, vodoznaky nebo zprávy založené na šablonách bez ruční úpravy.

### Další kroky

* Dále prozkoumejte **group shapes in word** přidáním textových polí nebo obrázků do stejné skupiny.
* Použijte vzor `SetShapeSize` k dynamickému výpočtu rozměrů na základě rozvržení stránky.
* Kombinujte tuto techniku s poli hromadné korespondence pro generování personalizovaných dokumentů ve velkém měřítku.

Neváhejte experimentovat s různými typy tvarů, barvami a transformacemi skupiny. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření skupinového tvaru v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvoření prázdného dokumentu Word se stínovaným obdélníkovým tvarem – krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Vytvoření dokumentu Word se stínovaným obdélníkem – krok za krokem](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}