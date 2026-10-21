---
category: general
date: 2026-09-30
description: Hozzon létre egy üres dokumentumot, és szúrjon be téglalap alakzatot,
  ellipszist, valamint csoportosítson több alakzatot C#-ban az Aspose.Words használatával.
  Tanulja meg, hogyan szúrjon be alakzatokat és hogyan hozzon létre csoportot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: hu
lastmod: 2026-09-30
og_description: Hozzon létre üres dokumentumot C#‑ban, és tanulja meg, hogyan szúrjon
  be alakzatokat, valamint hogyan csoportosítson több alakzatot az Aspose.Words segítségével.
  Kövesse a lépésről‑lépésre útmutatót.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Üres dokumentum létrehozása és alakzatok csoportosítása C#‑ban – Aspose.Words
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Hogyan hozzunk létre üres dokumentumot és adjunk hozzá alakzatokat az Aspose.Words
  segítségével C#-ban
url: /hu/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre üres dokumentumot és adhatunk hozzá alakzatokat az Aspose.Words segítségével C#-ban

Ha **üres dokumentumot kell létrehoznod** és grafikákkal feltölteni, ez az útmutató pontosan megmutatja, hogyan. Meg fogod látni, hogyan **helyezhetsz el egy téglalap alakzatot**, hogyan adhatod hozzá a többi rajzobjektumot, és hogyan **csoportosíthatod több alakzatot** úgy, hogy egy egységként viselkedjenek.

Az alakzatokkal való munka gyakori követelmény szerződések, bizonyítványok vagy egyedi jelentések generálásakor. Ebben az oktatóanyagról megtanulod a teljes munkafolyamatot, a dokumentum inicializálásától a végleges fájl mentéséig, az Aspose.Words API for .NET használatával.

## Előfeltételek

* .NET 6.0 (vagy újabb) SDK telepítve  
* Érvényes Aspose.Words for .NET licenc (az ingyenes próba verzió is működik ebben a példában)  
* Egy IDE, például Visual Studio 2022 vagy Visual Studio Code  

Nem szükséges további NuGet csomag a `Aspose.Words`-en kívül.

## Hogyan hozhatunk létre üres dokumentumot és dolgozhatunk alakzatokkal

Az első lépés egy `Document` objektum példányosítása. Ez az objektum a memóriában lévő Word fájlt képviseli, és hozzáférést biztosít a `DocumentBuilder`-hez, amely az elsődleges eszköz a tartalom beszúrásához.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Miért fontos:** Egy üres dokumentum tiszta vászonként szolgál. A `DocumentBuilder` fenntartja az aktuális beszúrási pontot, így minden hozzáadott alakzat automatikusan a megfelelő oldalra kerül.

## Téglalap alakzat és egyéb alakzatok beszúrása

Ezután hozzáadunk egy téglalapot és egy ellipszist. Mindkét hívás ugyanazt az `InsertShape` metódust használja, amely az Aspose.Words-ben **az alakzatok beszúrásának** ajánlott módja.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Az `InsertShape` metódus automatikusan a jelenlegi kurzorpozícióba helyezi az alakzatot.* Ha pontos elhelyezésre van szükséged, a beszúrás után módosíthatod a `Shape.Left` és `Shape.Top` értékeket.

## Több alakzat csoportosítása egyetlen objektummá

Most a téglalapot és az ellipszist egy logikai egységgé kombináljuk. A csoportosítás hasznos, ha több alakzatot egyszerre szeretnél mozgatni vagy átméretezni.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Hogyan működik:** Az `InsertGroupShape` egy olyan konténert hoz létre, amely úgy viselkedik, mint bármely más `Shape`. Az `AppendChild` hívásával a meglévő alakzatokat a konténerbe helyezed, amely automatikusan frissíti a relatív koordinátáikat.

### Gyakorlati tipp

Ha később programozottan **csoportot kell létrehozni** több mint két alakzat esetén, egyszerűen ismételd meg az `AppendChild` hívást minden további `Shape` példányra. A csoport tetszőleges számú rajzobjektumot tartalmazhat, beleértve képeket, szövegdobozokat vagy akár más csoportokat is.

## Teljes példa – hogyan szúrj be alakzatokat és mentsd a dokumentumot

Az alábbiakban a teljes, futtatható program látható, amely bemutatja a eddig tárgyalt minden lépést. A kód futtatása egy `ShapesDemo.docx` fájlt hoz létre, amely tartalmaz egy téglalapot, egy ellipszist és egy csoportosított alakzatot.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Várható kimenet:** A `ShapesDemo.docx` megnyitása a Microsoft Wordben egyetlen oldalt mutat kék téglalappal, zöld ellipszissel és egy körülvett szürke kerettel, amely a csoportot jelképezi. A csoport mozgatása mindkét alakzatot együtt mozgatja, ezzel megerősítve, hogy a **több alakzat csoportosítása** művelet sikeres volt.

## Gyakori kérdések és szél‑eset kezelése

| Question | Answer |
|----------|--------|
| *Mi van, ha az alakzatokat egy adott oldalra szeretném?* | Hívja a `builder.MoveToDocumentEnd();`-t az alakzatok beszúrása előtt, vagy használja a `builder.MoveToSection(sectionIndex);`-t egy adott szakasz célzásához. |
| *Hozzáadhatok szöveget egy csoportosított alakzathoz?* | Igen. Hozzon létre egy `Shape`-ot `ShapeType.TextBox` típusúként, állítsa be a szöveget, majd `AppendChild`-ként adja hozzá a `GroupShape`-hez. |
| *Az alakzatok méretei pontban vagy pixelben vannak megadva?* | Az Aspose.Words **pontokat** használ (1 pt = 1/72 inch). Ez biztosítja a méretek konzisztenciáját nyomtatók és kijelzők között. |
| *Hogyan változtatható meg a csoport forgatása?* | Állítsa be a `groupShape.RotationAngle = 45;`-t (fok). Az összes gyermek alakzat a csoport origója körül forog. |

## Következtetés

Most már tudod, hogyan **hozz létre üres dokumentumot**, **szúrj be téglalap alakzatot**, **hogyan szúrj be alakzatokat** például ellipszisekkel, és hogyan **csoportosíts több alakzatot** egyetlen objektummá az Aspose.Words for .NET használatával. A teljes kódrészlet bemutatja az ajánlott megközelítést, és a fenti tippek segítenek a megoldás testreszabásában összetettebb helyzetekben, például szövegdobozok hozzáadásában vagy csoportok forgatásában.

Készen állsz a további felfedezésre? Próbáld meg egy kép alakzatot hozzáadni a csoporthoz, kísérletezz különböző kitöltőszínekkel, vagy generálj többoldalas jelentést, ahol minden oldal saját csoportosított diagramot tartalmaz. Ugyanazok az elvek érvényesek, így ezt a mintát bármilyen dokumentum‑automatizálási projekthez skálázhatod.

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Alakzatok beszúrása Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Üres Word dokumentum létrehozása Aspose.Words segítségével – lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}