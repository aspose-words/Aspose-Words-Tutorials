---
category: general
date: 2026-09-18
description: Hozzon létre téglalap alakzatot egy Word-dokumentumban C#-vel. Ismerje
  meg, hogyan adhat hozzá több alakzatot, hogyan csoportosíthatja az alakzatokat,
  és hogyan illeszthet be csoportos alakzatot az Aspose.Words segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: hu
lastmod: 2026-09-18
og_description: Hozzon létre téglalap alakzatot egy Word fájlban C#-val. Ez az útmutató
  bemutatja, hogyan adhat hozzá több alakzatot, hogyan csoportosíthatja az alakzatokat,
  és hogyan illeszthet be csoportos alakzatot az Aspose.Words használatával.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Téglalap alak létrehozása és alakok csoportosítása C#-ban
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Téglalap alakzat létrehozása és több alakzat csoportosítása C#‑ban
url: /hu/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rectangle alakzat létrehozása és több alakzat csoportosítása C#‑ban

Ha **rectangle shape**‑t kell létrehoznod egy Word dokumentumban, ez a bemutató egy komplett megoldást mutat. Megtanulod, hogyan **add multiple shapes**, **add shapes to a group**, és **insert group shape** az Aspose.Words API for .NET segítségével.

Az alakzatok kezelése gyakori követelmény jelentés, szerződés vagy marketing anyagok programozott generálásakor. A útmutató végére egy futtatható C# konzolalkalmazásod lesz, amely egy `.docx` fájlt hoz létre, benne egy téglalappal, egy ellipszissel és egy csoporttal, amely mindkét alakzatot tartalmazza.

Az egyetlen előfeltétel egy friss .NET SDK (6.0 vagy újabb) és egy licencelt példány az Aspose.Words for .NET‑ből. Egyéb eszközre nincs szükség.

## Prerequisites

- .NET 6.0 SDK vagy újabb  
- Aspose.Words for .NET (NuGet csomag `Aspose.Words`)  
- Alapvető C# szintaxis ismeret  

A csomagot a következő paranccsal telepítheted:

```bash
dotnet add package Aspose.Words
```

## 1. lépés: Rectangle alakzat létrehozása az Aspose.Words‑szal

Az első lépés egy `Shape` objektum létrehozása `Rectangle` típusúként. Ez az objektum a dokumentumban megjelenő vizuális téglalapot képviseli.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Miért fontos:** A `ShapeType.Rectangle` azt mondja az Aspose.Words‑nek, hogy egy geometriai téglalapot rajzoljon. A `Width` és `Height` beállítása meghatározza a méretét pontban (1 pont = 1/72 hüvelyk). A kitöltő és körvonal színek hozzáadása láthatóvá teszi az alakzatot anélkül, hogy további stílusra lenne szükség.

## 2. lépés: Több alakzat hozzáadása a dokumentumhoz

A téglalap után tetszőleges számú további alakzatot hozhatsz létre. Ebben a példában egy ellipszist adunk hozzá, hogy bemutassuk, hogyan működik a **add multiple shapes**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Miért fontos:** Minden `new Shape` hívás egy független rajzobjektumot hoz létre. Sorozatos beszúrásukkal egy alakzatgyűjteményt építesz fel, amely később csoportosítható vagy egyenként pozicionálható.

## 3. lépés: Alakzatok hozzáadása a csoporthoz

Az alakzatok csoportosítása egyszerűsíti a elrendezéskezelést, mivel a csoport egyetlen csomópontként viselkedik. Ez a lépés megmutatja, hogyan **add shapes to group** a `GroupShape` használatával.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Miért fontos:** A `GroupShape` egy tárolóként működik. Amikor a csoportot mozgatod, forgatod vagy átméretezed, az összes gyermekalakzat automatikusan követi. A határoló keret (200 × 200 pont) meghatározza a gyermekalakzatok koordináta-terét.

## 4. lépés: Csoportos alakzat beszúrása a dokumentumba

Miután a csoport tartalmazza a téglalapot és az ellipszist, **insert group shape**‑t kell elhelyezned a kívánt helyen. A builder már elhelyezte az üres csoportot, de szükség esetén máshová is beszúrhatod.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Miért fontos:** A `Left` és `Top` értékek módosítása az egész csoportot a lapon belül mozgatja. A dokumentum mentése a shape hierarchiát egy `.docx` fájlba írja, amely megnyitható a Microsoft Word‑ben, LibreOffice‑ban vagy bármely kompatibilis megjelenítőben.

## Teljesen futtatható példa

Az alábbi program az összes lépést egyesíti. Másold a kódot egy új konzolprojektbe, és futtasd, hogy létrejöjjön a `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Várható kimenet:**  
A `GroupShapeExample.docx` megnyitása egyetlen csoportot mutat, amely egy világoskék téglalapot és egy világoskorróz ellipszist tartalmaz, mindkettő egy 200 × 200 pont méretű konténeren belül helyezkedik el. A csoport egy objektumként kiválasztható a Word‑ben, ami megerősíti, hogy a **add shapes to group** sikeres volt.

## Gyakori variációk és szélhelyzetek

| Situation | Recommended adjustment |
|-----------|------------------------|
| Különböző alakzat típusok (pl. `ShapeType.Line`) | Hozd létre az alakzatot a kívánt `ShapeType`‑val, és állítsd be a geometriáját ennek megfelelően. |
| Alakzat forgatása szükséges | Használd a `shape.Rotation = 45;` (fok) beállítást a csoportba való felvétel előtt. |
| Nagyobb dokumentumok sok csoporttal | Használd újra ugyanazt a `DocumentBuilder` példányt; kerüld el új builder létrehozását minden csoporthoz a memóriahasználat csökkentése érdekében. |
| Mentés PDF‑ként DOCX helyett | Hívd meg a `doc.Save("output.pdf", SaveFormat.Pdf);` metódust a csoport beszúrása után. |

**Pro tipp:** Mindig állíts be explicit `Left` és `Top` értékeket a csoport számára, ha pontos elhelyezésre van szükség. Ha ezeket kihagyod, a csoport a builder aktuális kurzorpozícióját örökli, ami váratlan elrendezési eredményeket okozhat.

## Conclusion

Most már tudod, hogyan **create rectangle shape**, **add multiple shapes**, **add shapes to group**, és **insert group shape** egy Word dokumentumban C#‑ban. A komplett példa bemutatja a teljes munkafolyamatot a dokumentum létrehozásától a végleges fájl mentéséig.

Ezután fedezd fel a kapcsolódó témákat, például **positioning shapes relative to text**, **applying text wrapping**, és **exporting grouped shapes to PDF**. Ezek a kiegészítések lehetővé teszik, hogy kifinomult, programozott dokumentumelrendezéseket építs fel az Aspose.Words segítségével.

## What Should You Learn Next?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}