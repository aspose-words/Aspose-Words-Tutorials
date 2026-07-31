---
category: general
date: 2026-07-29
description: Téglalap rajzolása a Wordben az Aspose.Words segítségével. Tanulja meg,
  hogyan adjon hozzá téglalap alakzatot, vonal alakzatot, és hogyan kezelje a több
  alakzatot egyetlen dokumentumban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: hu
lastmod: 2026-07-29
og_description: Rajzoljon téglalap alakzatot a Wordben az Aspose.Words segítségével.
  Kövesse ezt a lépésről‑lépésre útmutatót a téglalap alakzat, a vonal alakzat hozzáadásához,
  és a több alakzatot tartalmazó Word dokumentum könnyed kezeléséhez.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: téglalap rajzolása Wordben – A formák hozzáadásának mestere Wordben
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Téglalap rajzolása Wordben – Alakzatok hozzáadása Wordben az Aspose segítségével
url: /hu/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Teljes útmutató a formák hozzáadásához a Wordben

Gondoltad már, hogyan **draw rectangle word** dokumentumokat hozhatsz létre anélkül, hogy minden alkalommal megnyitnád a felhasználói felületet? Nem vagy egyedül. Sok fejlesztőnek kell gyorsan Word‑fájlokat generálnia, és a legegyszerűbb módja, ha egy könyvtár veszi át a nehéz munkát. Ebben a tutorialban pontosan megmutatjuk, **hogyan adjunk hozzá formákat** – konkrétan egy téglalapot és egy vonalat – az Aspose.Words for .NET segítségével, és a *draw rectangle word* kifejezésre fókuszálunk, hogy ne tévedj el.

Gondolj rá úgy, mint egy mini‑művészeti stúdióra, ami a kódodban él. A végére képes leszel **add rectangle shape**, **add line shape** hozzáadására, sőt akár **multiple shapes word** csoportokba is rendezni őket. Nincs UI, nincs kézi beavatkozás, csak tiszta, újrahasználható C#.

## What You’ll Learn

- Új Word‑dokumentum létrehozása Aspose.Words‑szal.  
- **GroupShape** létrehozása, amely több objektumot is tartalmazhat.  
- **Add rectangle shape** és **add line shape** hozzáadása a csoporthoz.  
- A csoportosított formák beillesztése a dokumentum törzsébe.  
- A fájl mentése és az eredmény azonnali megtekintése.  

Ha már ismered az alap C#‑t és rendelkezel egy Aspose.Words példánnyal, készen állsz. Nem szükséges extra NuGet‑csomag a core könyvtáron kívül.

> **Pro tip:** Az Aspose.Words működik a .NET 6, .NET 7 és a .NET Framework 4.6+ verziókkal. Válaszd a projektedhez illő futtatókörnyezetet.

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – Setting Up the Document

Mielőtt **draw rectangle word**-t végrehajtanánk, szükségünk van egy tiszta vászonra. A `Document` osztály ez a vászon; a `DocumentBuilder` a festőecsetünk.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

A fenti két sor egy friss, memóriában lévő `.docx`‑et hoz létre. Egyelőre semmi sem kerül lemezre, így kísérletezhetsz anélkül, hogy a fájlrendszert szennyeznéd.

## How to Add Shapes – Creating a GroupShape Container

Amikor **multiple shapes word**‑t szeretnél egy egységként kezelni – együtt mozgatni, együtt forgatni – egy `GroupShape`‑ba csomagolod őket. A csoport olyan, mint egy mappa, amely más formákat tartalmaz.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Miért csoport? Mert később szeretnéd **add rectangle shape**‑t és **add line shape**‑t együtt mozgatni. Csoport nélkül minden formát egyenként kellene pozícionálni.

## add rectangle shape – Inserting a Rectangle Inside the Group

Most, hogy a konténer létezik, **add rectangle shape**‑t helyezünk el. A téglalap egy `Shape`, amelynek a `ShapeType` értéke `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Vedd észre, hogy a `Left` és `Top` értékek a csoport origójához viszonyítva vannak, nem az oldalhoz. Ez megkönnyíti a formák pontos igazítását. A téglalap a csoport bal‑felső sarkához közel fog megjelenni.

## add line shape – Adding a Line to the Same Group

A vonal egy másik `Shape`, de a `ShapeType` értéke `Line`. A vonalat a téglalap alá helyezzük.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Mivel a vonal magassága nulla, a `Top` tulajdonság határozza meg, hogy függőlegesen hol helyezkedik el. A `Width` szabályozza, hogy a vonal milyen hosszú legyen vízszintesen.

## multiple shapes word – Inserting the Group into the Document Body

Most már van egy csoportunk, amely tartalmazza a **add rectangle shape**‑t és a **add line shape**‑t. Az utolsó lépés, hogy az egészet beillesszük a dokumentumba.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

Az `InsertNode` pontosan oda helyezi a csoportot, ahol a `DocumentBuilder` jelenleg áll. Ha egy konkrét bekezdéshez szeretnéd, előbb hívd meg a `builder.MoveToParagraph(index)`‑et.

## Saving the Result – Seeing the draw rectangle word Output

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Nyisd meg a generált fájlt a Microsoft Word‑ben, és egyetlen csoportot látsz, amely egy téglalapot és egy vonalat tartalmaz. Kattinthatsz a csoportra, áthúzhatod, vagy akár átméretezheted – minden forma együtt mozog. Ez a **multiple shapes word** ereje.

### Expected Output

- Egy `.docx` fájl `GroupShape.docx` néven.  
- Egy oldal, amelyen egy csoportosított téglalap (120 × 80 pt) a bal‑felső sarok közelében helyezkedik el.  
- Egy vízszintes vonal (150 pt hosszú) közvetlenül a téglalap alatt.  
- Mindkét forma egyetlen objektumként választható ki.

Ha duplán kattintasz a csoportra, a Word lehetővé teszi az egyes formák külön‑külön szerkesztését – tökéletes a finomhangoláshoz.

## Common Questions & Edge Cases

**Mi van, ha több mint két formára van szükség?**  
Csak hívd tovább a `group.AppendChild(yourShape)`‑t minden további objektumhoz. A csoport tetszőleges számú formát tárolhat, így ideális összetett diagramokhoz.

**Meg tudom változtatni a téglalap kitöltőszínét?**  
Természetesen. A téglalap létrehozása után állítsd be `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Ez minden kitöltést támogató formára működik.

**Be kell állítanom `Height = 0`‑t a vonalhoz?**  
Igen, egy egyenes vízszintes vonal esetén a magasságnak nullának kell lennie. Függőleges vonal esetén állítsd `Width = 0`‑t, és adj pozitív értéket a `Height`‑nek.

**Működik ez .doc (Word 97‑2003) fájlokkal?**  
Az Aspose.Words képes menteni a régebbi `.doc` formátumba, de egyes modern formafunkciók korlátozottak lehetnek. A teljes funkcionalitásért maradj a `.docx`‑nél.

**Hogyan forgatom el az egész csoportot?**  
Beállíthatod `group.Rotation = 45;` (fok) a beszúrás előtt. A forgatás minden gyermekformára érvényes lesz.

## Recap – How to Add Shapes in Word Programmatically

- **draw rectangle word** a `Document` és `DocumentBuilder` létrehozásával kezdődik.  
- Készíts egy **GroupShape**‑t, amely a **multiple shapes word**‑t tárolja.  
- **add rectangle shape** és **add line shape** kerülnek a csoportba.  
- A csoportot illeszd be a törzsbe a `builder.InsertNode`‑nal.  
- Mentsd a fájlt, és nyisd meg, hogy ellenőrizd a vizuális eredményt.

Ez a teljes munkafolyamat, egy könnyen olvasható kódlapon összefoglalva.

## Next Steps & Related Topics

Miután már tudod, **hogyan adjunk hozzá formákat**, érdemes tovább kutatni:

- **add rectangle shape** lekerekített sarkokkal (`ShapeType.Rectangle` + `CornerRadius`).  
- Vonalak stílusának változtatása különböző szaggatott mintákkal (`line.LineFormat.DashStyle`).  
- Képek beágyazása formák mellé a gazdagabb jelentésekhez.  
- **multiple shapes word** használata folyamatábrák vagy egyszerű UML diagramok építéséhez.  

Ezek a témák természetesen a most bemutatott alapokra épülnek, és ugyanazt a mintát követik: forma létrehozása, konfigurálása, és szükség esetén csoportosítása.

---

Boldog kódolást! Ha bármilyen furcsaságra bukkansz, vagy van egy izgalmas felhasználási eset, írj egy megjegyzést alul. A visszajelzésed segít mindannyiunknak elsajátítani a **draw rectangle word** művészetét és azon túl is.

## What Should You Learn Next?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutató technikáira épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy további API‑funkciókat saját projektjeidben is könnyedén felfedezhess.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}