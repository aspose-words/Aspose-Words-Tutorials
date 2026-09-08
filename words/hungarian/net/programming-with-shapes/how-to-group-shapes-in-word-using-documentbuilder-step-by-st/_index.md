---
category: general
date: 2026-09-08
description: Tanulja meg, hogyan csoportosíthatja a formákat a Wordben egy DocumentBuilder
  segítségével, hogyan hozhat létre egy üres Word‑dokumentumot, és hogyan illeszthet
  be egy téglalap alakzatot néhány C# kódsorral.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: hu
lastmod: 2026-09-08
og_description: Alakzatok csoportosítása Word-ben a DocumentBuilder-rel. Ez a bemutató
  megmutatja, hogyan lehet üres Word-dokumentumot létrehozni, egy téglalap alakzatot
  beszúrni, és az alakzatokat egy GroupShape-ba egyesíteni.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Alakzatok csoportosítása a Wordben a DocumentBuilderrel – teljes C# példa
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan csoportosítsuk a formákat a Wordben a DocumentBuilder segítségével –
  lépésről lépésre útmutató
url: /hu/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsunk alakzatokat a Wordben a DocumentBuilder használatával – lépésről‑lépésre útmutató

Ha programozott módon **csoportosítani szeretnél alakzatokat a Wordben**, ez az útmutató egy teljes megoldást mutat be C#-ban. Megmutatjuk, hogyan **hozz létre egy üres Word dokumentumot**, használj **DocumentBuilder**-t, és **illessz be egy téglalap alakzatot**, mielőtt egy ellipszissel csoportosítanád. Az eredmény egyetlen `GroupShape`, amelyet mozgathatsz, átméretezhetsz vagy stílusozhatsz egy objektumként.

Ez az útmutató mindent lefed, amit tudnod kell a Word dokumentum csoportosított grafikákkal való előállításához az Aspose.Words for .NET könyvtár használatával. A cikk végére egy futtatható projekted lesz, amely `GroupedShapes.docx` fájlt hoz létre, benne egy téglalappal és egy ellipszissel, amelyek egyetlen alakzatba vannak kombinálva.

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7.2+‑vel is működik)
- Aspose.Words for .NET NuGet csomag (`Aspose.Words`) – 23.12 vagy újabb verzió
- C# IDE, például Visual Studio 2022 vagy Visual Studio Code
- Alapvető ismeretek a C# szintaxisról és az objektum‑orientált programozásról

> **Pro tipp:** Telepítsd a NuGet csomagot a parancssorból, hogy a projekted rendezett maradjon:  
> `dotnet add package Aspose.Words --version 23.12.0`

## 1. lépés: Üres Word dokumentum létrehozása

Az első művelet egy `Document` objektum példányosítása, amely egy üres Word fájlt képvisel, valamint egy `DocumentBuilder` létrehozása, amely lehetővé teszi tartalom hozzáadását.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Miért fontos:** A `Document` biztosítja a fájl konténerét, míg a `DocumentBuilder` egy folyékony API-t kínál szöveg, kép és alakzat beillesztéséhez. `DocumentBuilder` nélkül a dokumentum csomópontfáját kellene manuálisan manipulálni, ami hibára hajlamos.

## 2. lépés: Téglalap alakzat beillesztése

A téglalap gyakori építőeleme a diagramoknak. Használd az `InsertShape`-t a `ShapeType.Rectangle` típussal, és add meg a szélességet és magasságot pontban (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Miért fontos:** A `Left` és `Top` beállítása pontosan a téglalapot helyezi el az oldalon, ami elengedhetetlen, amikor később más alakzatokkal csoportosítod. Az `InsertShape` metódus automatikusan hozzáadja az alakzatot az aktuális bekezdéshez.

## 3. lépés: Ellipszis alakzat beillesztése

Ezután adj hozzá egy ellipszist, amely a téglalap mellett helyezkedik el.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Miért fontos:** Egy másik `ShapeType` használata azt mutatja be, hogyan hozhat a ugyanazon `DocumentBuilder` API különféle grafikákat. Az ellipszis úgy történő elhelyezése, hogy átfedje a téglalapot, nyilvánvalóvá teszi a csoportosítás hatását.

## 4. lépés: A két alakzat csoportosítása

A `GroupShape` egy tárolóként működik. A téglalap és az ellipszis gyermekként való hozzáadásával egyetlen objektumként viselkednek.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Miért fontos:** A `Bounds` tulajdonság megmondja a Wordnek, hol helyezkedik el a csoport az oldalon. A gyermekalakzatok hozzáadásával megőrzöd az egyéni formázásukat, miközben lehetővé teszed a közös transzformációkat (mozgatás, forgatás, átméretezés).

## 5. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. A fájl útvonalát bármely általad preferált mappára módosíthatod.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Amikor megnyitod a `GroupedShapes.docx` fájlt a Microsoft Wordben, egy téglalapot és egy ellipszist látsz, amelyek együtt vannak csoportosítva. A csoport kiválasztása mindkét alakzatot kiemeli, lehetővé téve, hogy egy egységként húzd vagy átméretezd őket.

### Várt kimenet

- Egy **GroupedShapes.docx** nevű Word fájl
- Az első oldal egy **téglalapot** (100 pt × 50 pt) tartalmaz a (50, 50) pozícióban
- Egy **ellipszist** (80 pt × 80 pt) a (200, 70) pozícióban
- Mindkét alakzat egy **GroupShape** része, amelynek határoló kerete 300 pt × 200 pt

## Gyakori változatok és szélhelyzetek

| Szenárió | Módosítás |
|----------|------------|
| **Eltérő oldalméret** | Állítsd be a `document.Sections[0].PageSetup.PageWidth` és `PageHeight` értékeket a alakzatok beillesztése előtt. |
| **Kétnél több alakzat** | Hozz létre további `Shape` objektumokat, és minden egyeshez hívd meg a `groupShape.AppendChild(newShape)` metódust. |
| **Kitöltőszín alkalmazása** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **A csoport forgatása** | `groupShape.Rotation = 45;` (degrees) |
| **Exportálás PDF‑be** | A DOCX mentése után hívd meg a `document.Save("GroupedShapes.pdf");` metódust. |

## Teljes forráskód (kész a futtatásra)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Másold a kódot egy új konzolprojektbe, állítsd vissza az Aspose.Words NuGet csomagot, és futtasd. A konzol megerősíti a fájl helyét, a fájl megnyitása pedig megjeleníti a csoportosított grafikákat.

## Következtetés

Most már tudod, **hogyan csoportosíts alakzatokat a Wordben** az Aspose.Words `DocumentBuilder` segítségével. Az útmutató végigvezette a **üres Word dokumentum** létrehozásán, a **téglalap alakzat** beillesztésén, egy ellipszis hozzáadásán és azok `GroupShape`‑be kombinálásán. Ezzel az alapokkal gazdagabb diagramokat, folyamatábrákat vagy egyedi grafikákat építhetsz közvetlenül C#‑ból.

### Mi a következő lépés?

- Fedezd fel, **hogyan használhatod a DocumentBuilder‑t** táblázatok, fejlécek és láblécek létrehozásához.
- Kombináld a **insert rectangle shape Word** technikákat szövegdobozokkal a megjegyzett diagramokhoz.
- Használd a **create blank word doc**-ot sablonként az automatizált jelentéskészítéshez.

Nyugodtan kísérletezz színekkel, átmenetekkel és további alakzatokkal. Boldog kódolást!

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Alakzatok beillesztése Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Téglalap alakzat létrehozása Wordben C#‑val – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}