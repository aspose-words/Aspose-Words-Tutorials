---
category: general
date: 2026-09-21
description: Ismerje meg, hogyan csoportosíthatja az alakzatokat a Wordben az Aspose.Words
  for C# használatával. Ez a lépésről‑lépésre útmutató bemutatja a csoportosított
  alakzatok létrehozását, elhelyezését és mentését.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: hu
lastmod: 2026-09-21
og_description: Csoportosíts alakzatokat a Wordben az Aspose.Words for C# használatával.
  Kövesd ezt a tömör útmutatót, hogy programozottan létrehozd, elhelyezd és elmentsd
  a csoportosított alakzatokat.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Formák csoportosítása a Wordben az Aspose.Words segítségével – teljes C#
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan csoportosítsuk az alakzatokat a Wordben az Aspose.Words for C#-vel
url: /hu/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsunk alakzatokat a Wordben az Aspose.Words for C# használatával

Ha programozott módon **alakzatokat kell csoportosítania a Wordben**, az Aspose.Words ezt egyszerűvé teszi. Ez a bemutató megmutatja, hogyan hozhat létre két téglalap alakzatot, helyezze őket egymás mellé, kombinálja őket egy `GroupShape`‑ba, és mentse az eredményt DOCX fájlként.

Egy teljes, futtatható példát, a lépések jelentőségéről szóló magyarázatokat, valamint tippeket is láthat a gyakori széljegyek kezeléséhez, például átfedő alakzatok vagy dinamikus méretezés esetén. A útmutató végére képes lesz a forma‑csoportosítást bármely Word‑automatizálási projektbe integrálni.

## Előfeltételek

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* .NET 6.0 (vagy újabb) telepítve – az Aspose.Words támogatja a .NET Standard 2.0+, .NET Core és .NET Framework verziókat.
* Érvényes Aspose.Words for .NET licenccel (vagy ideiglenes értékelő kulccsal) – a könyvtár licenc nélkül is működik, de vízjelet ad.
* Visual Studio 2022‑vel (vagy bármely C# IDE‑vel) a minta lefordításához és futtatásához.

Nem szükséges további NuGet csomag a `Aspose.Words`‑en kívül.

## Hogyan csoportosítsunk alakzatokat a Wordben az Aspose.Words használatával

A megoldás központja egy **`GroupShape`** objektum, amely egy konténerként működik az egyes alakzatok számára. Az alábbiakban a folyamatot egyértelmű lépésekre bontjuk.

### 1. lépés: Üres dokumentum és `DocumentBuilder` létrehozása

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Miért ez a lépés?*  
A `Document` képviseli az egész DOCX fájlt, míg a `DocumentBuilder` folyékony metódusokat (pl. `InsertShape`) biztosít, amelyek automatikusan az aktuális kurzorpozícióba helyezik az új elemeket.

### 2. lépés: Az első téglalap alakzat beszúrása

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Az `InsertShape` hívás hozzáadja az alakzatot a dokumentumhoz, és visszaad egy `Shape` objektumot, amelyet tovább konfigurálhat (szín, keret stb.). A méret pontban van megadva (1 pt ≈ 1/72 in).

### 3. lépés: A második téglalap beszúrása és eltolása

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

A `Left` beállítása a forma bal pozícióját a lap margójához viszonyítva határozza meg. Az eltolásnak nagyobbnak kell lennie az első alakzat szélességénél (100 pt), hogy elkerüljük az átfedést; 120 pt‑et használunk, hogy kis hézag maradjon.

### 4. lépés: `GroupShape` létrehozása, amely elég nagy mindkét téglalaphoz

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

A `GroupShape` megkapja a tulajdonos `Document`‑et és a konténer méreteit. A konténer szélességének meghaladnia kell a legtávolabbi alakzat jobb szélét; ellenkező esetben a második alakzat levágásra kerülne.

### 5. lépés: Az egyes alakzatok hozzáadása a csoporthoz

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

A hozzáadás áthelyezi az alakzatokat a csoport belső gyűjteményébe. Ez a hívás után az alakzatok már nem önálló objektumok a dokumentumfában – a csoporthoz tartoznak.

### 6. lépés: A csoportosított alakzat visszaillesztése a dokumentumba

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

Az `InsertNode` a teljes `GroupShape`‑t a kurzor aktuális helyére helyezi. Ha a csoportot egy adott bekezdésben szeretné, előbb mozgassa a builder‑t arra a bekezdésre.

### 7. lépés: Dokumentum mentése

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Az eredményül kapott fájl két téglalapot tartalmaz, amelyek egyetlen objektumként viselkednek – együtt mozgathatja, átméretezheti vagy törölheti őket a Microsoft Word‑ben.

## Teljes forráskód

Az összes lépés egyesítése egy önálló programot eredményez:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Várható kimenet:** A *GroupedShapes.docx* megnyitása a Microsoft Word‑ben két egymás mellett elhelyezkedő téglalapot mutat, amely egyetlen kiválasztható objektumként jelenik meg. A csoport húzása mindkét téglalapot egyszerre mozgatja.

## Gyakori változatok és széljegyek

| Szituáció | Javasolt módosítás |
|-----------|--------------------|
| **Több mint két alakzat** | Hozzon létre további `Shape` objektumokat, helyezze el őket megfelelően, és minden egyes alakzatot adjon hozzá ugyanahhoz a `GroupShape`‑hez. |
| **Dinamikus méret** | Számolja ki a csoport szélességét/magasságát a gyermekalakzatok legnagyobb `Right` és `Bottom` értékei alapján. |
| **Különböző alakzattípusok** | `ShapeType.Ellipse`, `ShapeType.Triangle` stb. ugyanúgy beszúrhatók; a csoportkonténer nem érdeklődik a típus iránt. |
| **Forgatott alakzatok** | Állítsa be a `shape.Rotation = 45;` értéket a hozzáadás előtt; a forgatás megmarad a csoporton belül. |
| **Mentés PDF‑ként** | Hívja meg a `doc.Save("GroupedShapes.pdf");`‑t – a csoport megmarad a PDF renderelésben. |

**Pro tipp:** A csoportosítás után is módosíthatja az egyes alakzatokat a `group.GetChildNodes(NodeType.Shape, true)` elérésével. Ez akkor hasznos, ha egy téglalap kitöltőszínét szeretné megváltoztatni anélkül, hogy felbontaná a csoportot.

## Hogyan ellenőrizze a csoportosítást programozottan

Ha meg kell erősítenie, hogy az alakzatok helyesen lettek csoportosítva (pl. egységtesztekben), vizsgálja meg a dokumentum csomóponthierarchiáját:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

A kimenetnek a következőnek kell lennie:

```
Number of groups: 1
Children in first group: 2
```

Ez megerősíti, hogy a **group shapes in Word** a várt módon jöttek létre.

## Összegzés

Most már tudja, hogyan **csoportosítsa az alakzatokat a Wordben** az Aspose.Words for C#‑vel. A folyamat magában foglalja az egyes alakzatok létrehozását, pozicionálását, egy `GroupShape`‑ba csomagolását, majd a csoport visszaillesztését a dokumentumba. A fenti teljes példával a technikát bármennyi alakzatra, különböző típusokra vagy akár szövegdobozokkal és képekkel való kombinálásra is kiterjesztheti.

Ezután fedezze fel a kapcsolódó témákat, például **Aspose.Words shape grouping**, **C# Word shape manipulation**, és **DocumentBuilder insert shape**, hogy még fejlettebb dokumentum‑automatizálási forgatókönyveket valósítson meg. Kísérletezzen dinamikus méretezéssel, feltételes csoportosítással és PDF‑exportálással, hogy teljes mértékben kiaknázza az Aspose.Words erejét.

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}