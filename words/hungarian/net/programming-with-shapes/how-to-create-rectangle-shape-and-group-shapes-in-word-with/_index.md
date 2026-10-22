---
category: general
date: 2026-09-05
description: Hozzon létre téglalap alakzatot egy Word-dokumentumban az Aspose.Words
  használatával, majd tanulja meg, hogyan szúrjon be ellipszis alakzatot és csoportosítson
  alakzatokat a Wordben a gazdagabb elrendezésekhez.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: hu
lastmod: 2026-09-05
og_description: Hozzon létre téglalap alakzatot egy Word-dokumentumban az Aspose.Words
  segítségével, majd tekintse meg, hogyan szúrhat be ellipszis alakzatot és csoportosíthat
  alakzatokat a Wordben összetett elrendezésekhez.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Téglalap alakzat létrehozása és alakzatok csoportosítása Wordben – Aspose.Words
  útmutató
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
title: Hogyan hozhatunk létre téglalap alakzatot és csoportosíthatunk alakzatokat
  a Wordben az Aspose.Words segítségével
url: /hu/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre téglalap alakzatot és csoportosíthatunk alakzatokat a Wordben az Aspose.Words segítségével

Ha szüksége van **téglalap alakzat** létrehozására egy Word dokumentumban, ez az útmutató bemutatja a pontos lépéseket az Aspose.Words for .NET segítségével. Meg fogja látni, hogyan lehet **ellipszis szót** beilleszteni, **alakzatokat csoportosítani** a Wordben, és elmenteni az eredményt DOCX fájlként. A megoldás bármely .NET 6+ projektben működik, és nem igényel Microsoft Office telepítést a szerveren.

Az oktatóanyag mindent lefed a projekt beállításától a gyakori elrendezési hibák kezeléséig, így a kódot egyszerűen másolhatja és azonnal futtathatja.

## Prerequisites

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik a következőkkel:

* .NET 6 SDK vagy újabb telepítve  
* NuGet‑kompatibilis IDE (Visual Studio, Rider vagy VS Code)  
* Aspose.Words for .NET licenc (vagy ideiglenes értékelő kulcs)  
* Alapvető C# és Word dokumentumstruktúra ismeretek  

Ezek az elemek biztosítják, hogy a kód leforduljon, és az alakzatok helyesen jelenjenek meg.

## Step 1: Set up the project and add Aspose.Words

Hozzon létre egy új konzolos projektet, és adja hozzá az Aspose.Words csomagot:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

A csomag biztosítja a `Document`, `DocumentBuilder`, `Shape` és `GroupShape` osztályokat, amelyeket a teljes oktatóanyagban használunk.

## Step 2: Initialize a blank document and a builder

A `Document` objektum a teljes Word fájlt képviseli, míg a `DocumentBuilder` lehetővé teszi a tartalom programozott beszúrását.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

A dokumentum előzetes létrehozása biztosítja, hogy az összes későbbi alakzatműveletnek legyen érvényes tárolója.

## Step 3: **Create rectangle shape** and set its dimensions

A téglalap a leggyakoribb tároló szöveg vagy képek számára. Méretét pontban (1 pt ≈ 1/72 inch) adja meg.

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

Miért fontos ez a lépés: a `Shape` osztály tartalmazza a geometriai, kitöltési és vonal tulajdonságokat. A `Width` és `Height` beállítása beszúrás előtt garantálja, hogy az alakzat a várt mérettel jelenjen meg.

## Step 4: **How to insert ellipse word** – add an ellipse shape

Az ellipszis használható ikonok, jelölők vagy díszítő elemek létrehozásához. A kód tükrözi a téglalap létrehozását, csak a `ShapeType` változik.

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

A `FillColor` és a `Line.Color` tulajdonságok bemutatják, hogyan testreszabhatja a megjelenést külső képek nélkül.

## Step 5: **Group shapes in Word** – combine rectangle and ellipse

A csoportosítás lehetővé teszi, hogy több alakzatot egy egységként mozgassunk, méretezzünk vagy forgassunk. Ez elengedhetetlen, ha összetett grafikát (például feliratos ikont) szeretne létrehozni.

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

Amikor a `AppendChild` metódust hívja, az eredeti alakzatok eltávolításra kerülnek a fő dokumentumfolyamból, és a `GroupShape` gyermekei lesznek. A csoport egyetlen alakzatként viselkedik, ami egyszerűsíti a későbbi elrendezési módosításokat.

## Step 6: Save the document

Végül írja a dokumentumot a lemezre. Bármely támogatott formátumot választhat (`.docx`, `.pdf`, `.html`, stb.). Ebben az oktatóanyagban a natív Word formátumot használjuk.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

A program futtatása után nyissa meg a *GroupShape.docx* fájlt a Microsoft Wordben. Látni fog egy téglalapot és egy ellipszist, amelyek együtt vannak csoportosítva, a megadott koordinátákon.

## Common variations and edge cases

| Helyzet | Mit kell módosítani | Ok |
|-----------|----------------|--------|
| **Különböző méret egységek** | Használja a `ConvertUtil.InchToPoint(2.5)`-t hüvelykhez vagy a `ConvertUtil.MillimeterToPoint(30)`-t milliméterhez. | Olvashatóbbá teszi a kódot, ha nem‑pont mértékegységekkel dolgozik. |
| **Szöveg hozzáadása a téglalapba** | Hozzon létre egy `Paragraph` csomópontot, állítsa be a `Text` tulajdonságát, és adja hozzá a `rectangleShape`-hez az `AppendChild` segítségével. | Lehetővé teszi, hogy felcímkézze az alakzatot külön szövegdobozok nélkül. |
| **A csoport forgatása** | Állítsa be a `groupShape.Rotation = 45;`-t (fok). | Hasznos átlós jelvények vagy vízjelek létrehozásához. |
| **Mentés PDF‑ként** | Hívja meg a `doc.Save("GroupShape.pdf");`-t. | Az Aspose.Words automatikusan raszterizálja a vektoros alakzatokat PDF kimenethez. |
| **Több csoport** | Hozzon létre további `GroupShape` példányokat, és ismételje meg a hozzáfűzési/beszúrási lépéseket. | Lehetővé teszi összetett oldalelrendezések létrehozását több független összetétellel. |

### Pro tip

Mindig adjon hozzá alakzatokat **a csoportosítás előtt**. Ha megpróbál egy már egy másik csoport része lévő alakzatot csoportosítani, az Aspose.Words `ArgumentException`‑t dob. A csoport egyetlen metódusban történő felépítése megakadályozza ezt a futásidejű hibát.

### Watch out for

* **Koordináta rendszer** – A `Left` és `Top` a lap bal és felső margójától mérve van, nem a dokumentum szélétől. Ennek félreértése az alakzatok oldalról való kilógását eredményezheti.  
* **Licenc** – Érvényes licenc nélkül a mentett dokumentum vízjelet tartalmaz, amely azt írja: “Aspose.Words for .NET Evaluation”. Alkalmazza a licencet korán a kódban (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) a probléma elkerülése érdekében.

## Full source code (runnable)

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

A program futtatása *GroupShape.docx* fájlt hoz létre a leírt módon csoportosított alakzatokkal.

## Conclusion

Most már tudja, hogyan **hozzon létre téglalap alakzatot**, **hogyan illesszen be ellipszis szót**, és **hogyan csoportosítsa az alakzatokat a Wordben** az Aspose.Words segítségével. A teljes példa bemutatja a teljes munkafolyamatot – a dokumentum inicializálásától a végleges fájl mentéséig – így bármely automatizált jelentés- vagy dokumentum‑generálási megoldásba beépítheti az alakzatkezelést.

### What’s next?

* Fedezze fel az **aspose.words create shapes** funkciót összetettebb geometriákhoz, például `Polygon` vagy `Freeform`.  
* Kombinálja a csoportosított alakzatokat **content controls**‑al dinamikus sablonok építéséhez.  
* Konvertálja a DOCX-et PDF‑re vagy HTML‑re, hogy lássa, hogyan jelennek meg a vektoros alakzatok különböző formátumokban.  

Kísérletezzen különböző méretekkel, színekkel és forgatásokkal. Amikor elsajátítja az alakzatcsoportosítást, összetett diagramokat, jelvényeket és egyedi UI elemeket építhet közvetlenül Word dokumentumokba.

## What Should You Learn Next?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Csoportos alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Alakzatok beszúrása Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Téglalap alakzat létrehozása Wordben C#‑vel – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}