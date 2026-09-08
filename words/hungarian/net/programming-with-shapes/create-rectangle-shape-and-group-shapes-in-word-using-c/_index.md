---
category: general
date: 2026-09-08
description: Hozzon létre téglalap alakzatot egy Word-dokumentumban C#-bal. Tanulja
  meg beállítani az alakzat méretét, több alakzat csoportosítását, és programozottan
  üres Word-dokumentum létrehozását.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: hu
lastmod: 2026-09-08
og_description: Hozzon létre téglalap alakzatot egy Word dokumentumban C#-val. Ez
  az útmutató bemutatja, hogyan állíthatja be az alakzat méretét, csoportosíthat több
  alakzatot, és hogyan hozhat létre programozottan egy üres Word dokumentumot.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Téglalap alakzat létrehozása és alakzatok csoportosítása Wordben C#‑val
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
title: Téglalap alakzat létrehozása és alakzatok csoportosítása Wordben C#-val
url: /hu/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása és alakzatok csoportosítása Word-ben C#-al

Ha **téglalap alakzatot** kell létrehoznod egy Word‑fájlban, ez a bemutató egy teljes, azonnal futtatható megoldást nyújt. Megmutatjuk, hogyan állítsd be az alakzat méretét, hogyan csoportosíts több alakzatot, és hogyan hozz létre egy üres Word‑dokumentumot a semmiből – mindezt az Aspose.Words for .NET könyvtárral.

A Word‑dokumentumok programozott kezelése gyakran olyan, mintha sok apró részletet kellene egyensúlyban tartani. A leírás végére egyetlen metódusod lesz, amely egy `.docx` fájlt hoz létre, benne egy téglalappal és egy ellipszissel, csoportosítva, készen állva a további szerkesztésre vagy nyomtatásra.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következők rendelkezésre állnak:

* .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑vel is működik)
* Az **Aspose.Words for .NET** licencelt példánya (használhatsz ingyenes értékelő kulcsot is)
* Fejlesztői környezet, például Visual Studio 2022 vagy Visual Studio Code
* Alapvető C#‑szintaxis ismeret

További NuGet‑csomagokra nincs szükség az `Aspose.Words`‑en kívül.

## 1. lépés: Üres Word‑dokumentum létrehozása

Az első lépés egy üres dokumentum létrehozása, amely a formákat fogja tartalmazni. Ezzel teljesül a *create blank word document* követelmény.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Egy üres dokumentum tiszta vászonként szolgál. A `Document` objektum képviseli a teljes `.docx` fájlt, és a `FirstSection.Body.FirstParagraph` az alapértelmezett beszúrási pont az új csomópontok számára.

## 2. lépés: Téglalap alakzat létrehozása

Most hozzáadhatod a téglalapot. Itt történik a **create rectangle shape** művelet.

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

A méretek közvetlen beállítása megválaszolja a **set shape size** kulcsszót. Minden méretérték pontban van megadva, ami precíz vezérlést biztosít az alakzat megjelenéséhez a végső dokumentumban.

## 3. lépés: Egy további alakzat (ellipszis) létrehozása

Tipikus eset több alakzat kombinálása. Itt egy ellipszist adunk hozzá, amely később ugyanabban a tárolóban lesz.

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

Mindkét alakzat még független ebben a pontban. A következő lépés megmutatja, hogyan **group multiple shapes** együtt.

## 4. lépés: Alakzatok csoportosítása Word‑ben

Az alakzatok csoportosítása lehetővé teszi, hogy egy egységként mozgass, átméretezz vagy formázz őket. Ezzel teljesül a **group shapes in word** és a **group multiple shapes** követelmény.

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

A `GroupShape.Bounds` tulajdonság határozza meg a gyermekalakzatok koordináta‑rendszerét. A téglalap és az ellipszis ugyanabban a `GroupShape`‑ben helyezve később egyetlen hívással mozgathatók vagy forgathatók együtt.

## 5. lépés: Dokumentum mentése

Végül írjuk a dokumentumot a lemezre. A fájl tartalmazni fogja a most létrehozott csoportosított alakzatokat.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

A program futtatása után nyisd meg a `GroupedShapes.docx` fájlt a Microsoft Word‑ben. Látnod kell egy téglalapot és egy ellipszist, amelyek csoportosítva vannak; az egyik alakzat kiválasztása automatikusan a másikat is kijelöli, ezzel igazolva, hogy a csoportosítás sikeres volt.

## Teljes forráskód

Másold a következő teljes programot egy új konzol‑alkalmazás projektbe, és futtasd. További kódra nincs szükség.

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

### Várt kimenet

A program futtatása `GroupedShapes.docx`‑et hoz létre. A fájl megnyitása Word‑ben a következőket mutatja:

* Egy **téglalap** (100 pt × 50 pt) kék szegéllyel és világosszürke kitöltéssel.
* Egy **ellipszis** (80 pt × 80 pt) sötétzöld szegéllyel és világossárga kitöltéssel.
* Mindkét alakzat egyetlen csoportban van, így az egyik mozgatása a másikat is elmozdítja.

## Gyakori kérdések és speciális esetek

| Kérdés | Válasz |
|----------|--------|
| **Hozzáadhatok több mint két alakzatot a csoporthoz?** | Igen. Hozz létre további `Shape` objektumokat, és minden egyeshez hívd meg a `group.AppendChild(yourShape)` metódust. |
| **Mi van, ha el kellene forgatni a csoportot?** | Állítsd be a `group.RotationAngle = 45;` értéket (fokban). Minden gyermekalakzat együtt forog. |
| **Lehetséges a csoportosítás a dokumentum mentése után?** | A dokumentum szerkezetét a mentés előtt kell módosítani; egyébként be kell tölteni a fájlt, meg kell találni az alakzatokat, és újra kell létrehozni a csoportot. |
| **Kell-e valamilyen objektumot feloldani?** | Az Aspose.Words saját erőforrásait kezeli, de a manuálisan megnyitott `FileStream` objektumokat érdemes feloldani. |
| **A kód működik .doc (bináris) formátummal is?** | Igen, csak változtasd meg a `doc.Save("output.doc")` sort. A csoportosítás viselkedése azonos. |

## Következtetés

Most már tudod, hogyan **create rectangle shape**, **set shape size**, és **group multiple shapes** egy Word‑fájlban C#‑al. Ez a megközelítés lehetővé teszi, hogy programozottan építs összetett diagramokat, vízjeleket vagy sablon‑alapú jelentéseket manuális szerkesztés nélkül.

### Következő lépések

* Fedezd fel a **group shapes in word** lehetőségeket további szövegdobozok vagy képek hozzáadásával ugyanabba a csoportba.
* Használd a `SetShapeSize` mintát a méretek dinamikus kiszámításához az oldalelrendezés alapján.
* Kombináld ezt a technikát a körlevél‑mezőkkel, hogy nagyméretű, személyre szabott dokumentumokat generálj.

Nyugodtan kísérletezz különböző alakzat‑típusokkal, színekkel és csoport‑transzformációkkal. Jó kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy könnyedén elsajátíthasd az API további funkcióit és alternatív megvalósítási módokat a saját projektjeidben.

- [Csoportos alakzat létrehozása Word‑dokumentumban Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Üres Word‑dokumentum létrehozása árnyékolt téglalap alakzattal – lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Word‑dokumentum létrehozása árnyékolt téglalappal – lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}