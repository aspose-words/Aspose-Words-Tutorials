---
category: general
date: 2026-11-18
description: Tanulja meg, hogyan hozhat létre téglalap alakzatot egy Word dokumentumban
  C#-vel. Az útmutató a forma méretének beállítását, a forma pozíciójának beállítását
  és a formák csoportosítását is lefedi a Wordben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: hu
lastmod: 2026-11-18
og_description: Hozzon létre téglalap alakzatot egy Word-fájlban C#-val, és tanulja
  meg beállítani az alakzat méreteit, pozícióját, valamint csoportosítani az alakzatokat
  a Wordben.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Téglalap alakzat létrehozása és alakzatok csoportosítása Wordben C#‑val
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
title: Hogyan hozhatunk létre téglalap alakzatot és csoportosíthatunk alakzatokat
  a Wordben C#‑val
url: /hu/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre téglalap alakzatot és csoportosíthatunk alakzatokat a Wordben C#‑al

Ha **téglalap alakzatot** kell létrehoznod egy Word‑dokumentumban, ez a bemutató egy teljes, azonnal futtatható megoldást mutat. Megtanulod, hogyan állítsd be az alakzat méretét, pozícióját, és hogyan csoportosítsd az alakzatokat a Wordben úgy, hogy egyetlen objektumként viselkedjenek.

Az alakzatok kezelése gyakori követelmény jelentések, számlák vagy diagramok programozott generálásakor. A leírás végére képes leszel egy `.docx` fájlt előállítani, amely tartalmaz egy téglalapot, egy ellipszist és egy csoportosított konténert – mindezt az Aspose.Words for .NET segítségével.

## Előfeltételek

- .NET 6.0 SDK vagy újabb (a kód .NET Framework 4.7+‑vel is működik)
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`)
- Kódszerkesztő vagy IDE (Visual Studio, VS Code, Rider, stb.)

További könyvtárak nem szükségesek.

## Hogyan hozhatunk létre téglalap alakzatot és csoportosíthatunk alakzatokat a Wordben

A fő lépések:

1. **Üres dokumentum** és egy `DocumentBuilder` létrehozása.
2. **`GroupShape` beszúrása**, amely a különálló alakzatokat tartalmazza.
3. **Téglalap alakzat** létrehozása, méretének beállítása, és hozzáadása a csoporthoz.
4. **Ellipszis alakzat** létrehozása, méretének és pozíciójának beállítása, majd hozzáadása a csoporthoz.
5. **Mentés** a dokumentumra.

Minden lépést részletesen kifejtünk, a teljes forráskód pedig a magyarázat után következik.

### 1. lépés: A dokumentum és a builder inicializálása

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

A `Document` képviseli a teljes Word‑fájlt, míg a `DocumentBuilder` egy folyékony API‑t biztosít a tartalom beszúrásához. Ezek inicializálása kötelező, mielőtt bármilyen alakzatot hozzáadnál.

### 2. lépés: Csoportos alakzat beszúrása

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

A `GroupShape` egy tárolóként működik; az összes gyermekalakzat együtt mozog. Ez az ajánlott mód a **alakzatok csoportosítására a Wordben**, ha közös transzformációkra (pl. mozgatás, forgatás vagy törlés) van szükség.

### 3. lépés: A téglalap létrehozása és méretének beállítása

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Itt **téglalap alakzatot hozunk létre** és **beállítjuk az alakzat méretét** a `Width` és `Height` értékek megadásával. Az Aspose.Words‑ben a méretek pontban (1 pt ≈ 1/72 in) vannak megadva. A méretek explicit megadása biztosítja, hogy a téglalap pontosan úgy jelenjen meg, ahogy szeretnéd.

### 4. lépés: Az ellipszis létrehozása, méretek beállítása és pozicionálása

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Az ellipszis **méretének beállítása** ugyanaz a szélesség és magasság, így tökéletes kör jön létre. A `Left` tulajdonság a **alakzat pozíciójának beállítását** mutatja: az ellipszis a csoport origójától 120 pt-re jobbra kezdődik, így nem fed le a téglalapot.

### 5. lépés: A dokumentum mentése

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

A mentés a Word‑fájlt a lemezre írja. A `GroupShape.docx` fájlt megnyithatod a Microsoft Wordben, hogy ellenőrizd, a téglalap és az ellipszis megfelelően csoportosítva és pozicionálva van-e.

## Az alakzat méreteinek és dimenzióinak beállítása – mélyebb betekintés

- **Pont vs. hüvelyk**: 72 pt = 1 in. Ha hüvelykben szeretnél dolgozni, szorozd meg 72‑vel (pl. `2.5 * 72` a 2,5 in‑hez).
- **Automatikus méretezés**: Ha kihagyod a `Width` vagy `Height` beállítást, az alakzat az alapértelmezett méretét használja. A **alakzat méretének explicit beállítása** elkerüli a váratlan elrendezési problémákat.
- **Képarány**: Az `Ellipse` esetén a `Width` és `Height` egyenlőnek tartása kör alakot eredményez.

## Alakzat pozicionálása a Wordben

A `Left` és `Top` tulajdonságok szabályozzák az alakzat eltolását a tárolón belül (a csoporton vagy az oldalon). A pozitív értékek jobbra/lefelé mozgatják, a negatívak balra/felfelé. Csoportosításkor a pozíciók a csoport origójához viszonyulnak, ami leegyszerűsíti a layout számításokat.

## Alakzatok csoportosítása a Wordben az Aspose.Words segítségével

A csoportosítás elengedhetetlen, ha több alakzatot szeretnél egy egységként kezelni. A `GroupShape` objektum:

- Támogatja az `AppendChild` metódust, amellyel bármilyen `Shape`‑t (téglalap, ellipszis, kép stb.) hozzáadhatsz.
- Lehetővé teszi a teljes csoport mozgatását, forgatását vagy törlését egyetlen hívással.
- A gyermekalakzatok pozícióját a csoporthoz relatívan tartja, így a komplex diagramok kezelése egyszerűbbé válik.

**Pro tipp:** Miután minden gyermekalakzatot hozzáadtál, módosíthatod a csoport `Width`, `Height`, `Left` és `Top` értékeit, hogy egy lépésben áthelyezd az egész gyűjteményt.

## Teljesen futtatható példa

Az alábbiakban megtalálod a teljes programot, amelyet egyszerűen másolhatsz, beilleszthetsz és futtathatsz. Tartalmazza az összes `using` direktívát, egy `Main` metódust, valamint a sorok magyarázatát.

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

**Várt eredmény:** A program futtatása után a `GroupShape.docx` a végrehajtási mappában jelenik meg. A Wordben megnyitva egy 100 pt × 50 pt méretű téglalap látható bal oldalon, valamint egy 80 pt × 80 pt méretű ellipszis, amely 120 pt-re jobbra helyezkedik el – mindkettő egyetlen csoportosított objektumban.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Képernyőkép egy Word‑dokumentumról, amely egy C#‑al létrehozott csoportosított téglalap és ellipszis alakzatot mutat" }

*Az előző kép a végső eredményt szemlélteti; a téglalap és az ellipszis egy csoportként választható ki.*

## Gyakori kérdések és szélhelyzetek

| Kérdés | Válasz |
|----------|--------|
| **Hozzáadhatok több mint két alakzatot?** | Igen. Minden további alakzat esetén hívd meg a `group.AppendChild(yourShape)` metódust. |
| **Hogyan forgathatom meg a csoportot?** | Használd a `group.RotationAngle = 45;` (fok) beállítást a gyermekek hozzáadása után. |
| **Hogyan változtathatom meg a csoport háttérszínét?** | Állítsd be a `group.FillColor = System.Drawing.Color.LightGray;` értéket. |
| **Működik ez .doc fájlokkal is?** | Az Aspose.Words támogatja a `.doc` és `.docx` formátumokat. Ugyanaz a kód működik; csak a `Save` metódusban cseréld ki a fájlkiterjesztést. |
| **Van memóriahatása, ha sok alakzatot csoportosítok?** | Maga a csoportosítás minimális overheadet ad hozzá. A fő szempont a teljes alakzatszám; nagy dokumentumok esetén tartsd ésszerűen. |

## Összegzés

Ebben a bemutatóban megtanultad, hogyan **hozz létre téglalap alakzatot** egy Word‑fájlban C#‑al, hogyan **állítsd be az alakzat méretét**, **dimenzióit**, **pozícióját**, és végül hogyan **csoportosítsd az alakzatokat a Wordben** az Aspose.Words segítségével. A teljes példa egy tiszta, karbantartható megközelítést mutat, amelyet könnyen kiterjeszthetsz összetettebb diagramokra, diagramokra vagy egyedi grafikákra.

A következő lépéseket érdemes felfedezni:

- Szöveg hozzáadása alakzatokhoz (`Shape.TextPath.Text = "Hello"`).
- Képek beszúrása egy `GroupShape`‑be.
- A csoportos alakzatok exportálása PDF‑be a `doc.Save("output.pdf")` metódussal.

Nyugodtan kísérletezz különböző méretekkel, pozíciókkal és további alakzattípusokkal, hogy a projekted igényeinek megfeleljen. Jó kódolást!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek tovább építik a jelen útmutatóban bemutatott technikákat. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy könnyedén elsajátíthasd az API további funkcióit és alternatív megvalósítási módokat a saját projektjeidben.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}