---
category: general
date: 2026-10-04
description: Tanulja meg, hogyan csoportosíthatja a formákat a Wordben C#-al. Ez az
  útmutató bemutatja, hogyan szúrjon be téglalap alakzatot, hogyan csoportosítson
  több alakzatot, és hogyan hozzon létre programozottan egy üres Word-fájlt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: hu
lastmod: 2026-10-04
og_description: C#-vel alakzatok csoportosítása Word-ben. Kövesd ezt a lépésről‑lépésre
  útmutatót a téglalap alakzat beszúrásához, több alakzat csoportosításához, és egy
  üres Word-fájl létrehozásához a DocumentBuilderrel.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Alakzatok csoportosítása Wordben C#‑val – teljes DocumentBuilder útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Hogyan csoportosítsuk a formákat a Wordben C# és a DocumentBuilder segítségével
url: /hu/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsunk alakzatokat a Wordben C# és DocumentBuilder segítségével

Ha **alakzatokat kell csoportosítania a Wordben** egy C# alkalmazásból, ez a bemutató pontosan megmutatja, hogyan teheti meg. Látni fogja, hogyan *szúrjon be egy téglalap alakzatot*, hogyan kombináljon több rajzot egyetlen csoportba, és végül hogyan **hozzon létre egy üres Word fájlt**, amely a csoportosított objektumokat tartalmazza.

Az alakzatok kezelése gyakori követelmény jelentések, számlák vagy egyedi sablonok programozott generálásakor. A útmutató végére egy újrahasználható kódrészletet kap, amelyet bármely .NET projekthez beilleszthet, amely hivatkozik az Aspose.Words-re.

## Mit fog megtanulni

- Üres Word dokumentum létrehozása a semmiből.  
- Téglalap és ellipszis alakzat beszúrása a `DocumentBuilder` segítségével.  
- **Több alakzat csoportosítása** egy `GroupShape`-ba.  
- **append child to group** használata a hierarchia felépítéséhez.  
- A fájl mentése lemezre és az eredmény ellenőrzése.

Nem szükséges előzetes tapasztalat az Aspose.Words használatában, de alapvető C# és .NET fejlesztési ismeretekkel kell rendelkeznie.

## Előfeltételek

| Követelmény | Indoklás |
|-------------|----------|
| .NET 6.0 vagy újabb | Biztosítja a C# kód futtatási környezetét. |
| Aspose.Words for .NET (legújabb verzió) | `Document`, `DocumentBuilder` és alakzat osztályok biztosítása. |
| Egy IDE, például a Visual Studio 2022 (vagy VS Code) | Megkönnyíti a minta lefordítását és futtatását. |
| Írási jogosultság egy mappához a gépén | A `doc.save` híváshoz szükséges. |

Telepítse az Aspose.Words-ot a NuGet-en keresztül:

```bash
dotnet add package Aspose.Words
```

---

## Alakzatok csoportosítása a Wordben – lépésről‑lépésre útmutató

Az alábbiakban a teljes, futtatható program látható. Minden szakasz részletesen magyarázva van, hogy megértse, **miért** íródott így a kód, ne csak **mit** csinál.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Miért fontos minden lépés

1. **Üres Word fájl létrehozása** – Egy tiszta dokumentummal kezdve garantálja, hogy semmilyen rejtett formázás ne befolyásolja az alakzatok elhelyezkedését.  
2. **DocumentBuilder inicializálása** – A `DocumentBuilder` elrejti az alacsony szintű csomópontkezelést, lehetővé téve, hogy a elrendezésre koncentráljon.  
3. **Egyedi alakzatok beszúrása** – Először különálló objektumokra van szükség (`insert rectangle shape` és egy ellipszis), mielőtt csoportosítaná őket. A `Left` és `Top` beállítása biztosítja, hogy egymás mellett jelenjenek meg.  
4. **Több alakzat csoportosítása** – Egy `GroupShape` létrehozásával és a **append child to group** használatával két független rajzot egyetlen logikai egységgé alakít. A csoport mozgatása vagy átméretezése egyszerre mindkét gyermekre hat.  
5. **A dokumentum mentése** – A végső fájl, a `GroupedShapes.docx`, megnyitható a Microsoft Wordben, hogy ellenőrizze, a téglalap és az ellipszis valóban csoportosítva van (kiválasztva az egyiket, mindkettő együtt mozog).

### Várt kimenet

Nyissa meg a `GroupedShapes.docx` fájlt a Microsoft Wordben:

- Egy téglalapot és egy ellipszist fog látni egymás mellett elhelyezve.  
- Bármelyik alakzat kiválasztása mindkettőt kiemeli, megerősítve, hogy ugyanahhoz a csoporthoz tartoznak.  
- A csoport húzható, átméretezhető vagy formázható egyetlen objektumként.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="A csoportosított téglalap és ellipszis diagramja egy Word dokumentumban"}

*A képernyőkép a végső csoportosított alakzatokat mutatja.*

---

## Téglalap alakzat beszúrása – méret és stílus testreszabása

Ha egy adott kitöltőszínnel vagy szegéllyel rendelkező téglalapra van szüksége, módosítsa a `Shape` objektumot a beszúrás után:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Ezek a tulajdonságok a `Shape` osztály részei, és bármely alakzattípusra működnek, nem csak a téglalapokra. A stílus beállítása a **append child to group** előtt biztosítja, hogy a csoport örökölje a megadott vizuális tulajdonságokat.

---

## Több alakzat csoportosítása – több mint két objektum kezelése

A példa egy téglalapot és egy ellipszist csoportosít, de tetszőleges számú alakzatot hozzáadhat:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Pro tipp:** Miután egy összetett csoportot épített, zárolhatja annak elrendezését, hogy megakadályozza a véletlen módosításokat:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – a sorrend számít

Az a sorrend, ahogyan a `AppendChild`-et hívja, meghatározza a Z‑rendet (melyik alakzat jelenik meg felül). A példában a téglalap kerül először hozzáadásra, majd az ellipszis, így az ellipszis a téglalap fölé kerül, ha átfedik egymást. A sorrend módosítása olyan egyszerű, mint a `RemoveChild` hívása és újra hozzáadása:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Üres Word fájl létrehozása – újrahasználható segédfüggvény

Ha az alkalmazása gyakran igényel új dokumentumot, foglalja bele a létrehozási logikát:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Ezután a főprogramban a `new Document()` sort cserélheti a `CreateBlankWordFile()`-ra. Ez egy újrahasználható módon mutatja be a **create blank word file** koncepciót.

---

## Gyakori buktatók és elkerülésük módja

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| Az alakzatok az oldalról kívül jelennek meg | Az alapértelmezett `Left`/`Top` értékek 0, ami az alakzatot a margóba helyezi. | Kifejezetten állítsa be a `Left` és `Top` értékeket a beszúrás után. |
| A csoport elveszíti a formázást | Gyermek alakzat módosítása a csoportba való felvétel után felboríthatja a csoport elrendezését. | Alkalmazza az összes vizuális tulajdonságot **a** `AppendChild` **hívása előtt**. |
| A mentett fájl üres | `DocumentBuilder` soha nem használt csomópont hozzáadására, vagy a `doc.Save` egy másik `Document` példányon lett meghívva. | Ellenőrizze, hogy ugyanazt a `Document`-ot menti, amelyet felépített. |
| Kompatibilitási figyelmeztetések a Wordben | Újabb alakzat funkciók használata, amelyek nem támogatottak |  |

## Mit érdemes következőként megtanulni?

A következő bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Alakzatok beszúrása Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Téglalap alakzat létrehozása Wordben C#-al – lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}