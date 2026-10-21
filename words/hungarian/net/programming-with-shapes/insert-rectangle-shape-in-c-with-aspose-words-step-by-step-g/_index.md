---
category: general
date: 2026-08-07
description: Helyezzen be téglalap alakzatot C#-ban az Aspose.Words segítségével,
  és tanulja meg, hogyan lehet elrejteni az alakzatot, beállítani a kitöltőszínt,
  valamint hatékonyan hozzáadni a téglalap alakzatot egy Word dokumentumhoz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: hu
lastmod: 2026-08-07
og_description: Helyezzen el egy téglalap alakzatot egy Word dokumentumban C#-el.
  Tanulja meg, hogyan rejtheti el az alakzatot, állíthatja be a kitöltő színt, és
  adhat hozzá téglalap alakzatot az Aspose.Words segítségével.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Téglalap alakzat beszúrása C#-ban – teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Téglalap alakzat beszúrása C#-ban az Aspose.Words segítségével – lépésről lépésre
  útmutató
url: /hu/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat beszúrása C#-ban az Aspose.Words segítségével – lépésről lépésre útmutató

Ha **téglalap alakzatot** kell beszúrni egy Word dokumentumba C#-ból, ez az útmutató pontosan megmutatja, hogyan teheted meg. Megmutatjuk, hogyan állítsd be a kitöltő színt, hogyan rejtsd el az alakzatot, hogy ne jelenjen meg a végső elrendezésben, és hogyan mentsd el a fájlt – mindezt csak néhány kódsorral.

Az alábbi szakaszokban mindent lefedünk, amit tudnod kell: előkövetelmények, a teljes kódlista, magyarázatok minden egyes lépéshez, valamint tippek a gyakori variációkhoz, például az alakzat újra láthatóvá tételéhez vagy más szín használatához. A végére képes leszel **téglalap alakzatot** hozzáadni bármely .docx fájlhoz programozottan.

## Előkövetelmények

Mielőtt elkezdenéd, győződj meg róla, hogy a következőkkel rendelkezel:

* **Aspose.Words for .NET** (23.10 vagy újabb verzió). Telepítheted NuGet-en keresztül:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK vagy újabb telepítve a gépeden.
* Alapvető C# és Visual Studio (vagy bármely kedvelt IDE) ismeretek.

Nem szükséges további könyvtár – az alakzatokkal kapcsolatos API-k az Aspose.Words alaprészének részei.

## Téglalap alakzat beszúrása Aspose.Words-szel

A megoldás lényege egy rövid, önálló program, amely létrehoz egy üres dokumentumot, beszúr egy téglalapot, színezi, elrejti, majd elmenti a fájlt. Az alábbiakban a teljes forráskód látható beágyazott megjegyzésekkel, amelyek elmagyarázzák az egyes sorok *miértjét*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Mit csinál egyes lépésekkel

| Lépés | Indoklás |
|------|----------|
| **Új dokumentum létrehozása** | Tiszta vászon biztosítása; létező .docx fájlt is betölthetsz a `new Document(path)` fájlúttal. |
| **DocumentBuilder inicializálása** | `DocumentBuilder` egy magas szintű segéd, amely lehetővé teszi szöveg, táblázat és alakzat beszúrását anélkül, hogy alacsony szintű csomópontfákkal kellene foglalkozni. |
| **Téglalap alakzat beszúrása** | Az `InsertShape` metódus egy `Shape` objektumot ad vissza, amelyet tovább testreszabhatsz (méret, pozíció, szegélyek stb.). |
| **Kitöltő szín beállítása** | A `FillColor` tulajdonság szabályozza a belső színt; bármilyen `Color` értéket használhatsz (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, stb.). |
| **Az alakzat elrejtése** | `Hidden = true` azt mondja a Wordnek, hogy hagyja figyelmen kívül az alakzatot az elrendezés során, miközben megtartja azt a dokumentum XML-ben. Ez a szabványos módja a láthatatlan objektumok tárolásának. |
| **Dokumentum mentése** | A változtatásokat .docx fájlba menti. A mentett fájl tartalmazni fogja a rejtett téglalap alakzatot. |

## Hogyan állítsuk be az alakzat kitöltő színét

A kitöltő szín megváltoztatása olyan egyszerű, mint egy `System.Drawing.Color` érték hozzárendelése a `FillColor` tulajdonsághoz. Ha egyedi árnyalatra van szükséged, használd a `Color.FromArgb`-t:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Miért fontos*: A kitöltő szín az alakzat XML-jében (`<w:fill>` attribútum) tárolódik. Amikor az alakzat rejtett, a szín továbbra is létezik, ami hasznos lehet a későbbi feldolgozásoknál (pl. metaadatok kinyerése színkódok alapján).

## Hogyan rejtsük el az alakzatot a végső dokumentumban

A `Hidden` jelző a `Shape` osztály egy logikai tulajdonsága. `true` értékre állítva a Word elhagyja az alakzatot az elrendezés során.

```csharp
rectangleShape.Hidden = true;
```

**Gyakori buktatók**

* **Rejtett vs. Látható** – Ha később szükség van az alakzat megjelenítésére, egyszerűen állítsd `Hidden = false`-ra.
* **Kompatibilitás** – A Word régebbi verziói (2007 előtti) másként kezelhetik a rejtett rajzobjektumokat. Az Aspose.Words kompatibilitást biztosít a jelző megfelelő OOXML elemben történő tárolásával.

## Alakzat beszúrása programozottan

Bár a példában egy téglalapról van szó, ugyanaz a `InsertShape` metódus sok más alakzatra is működik (ellipszis, háromszög, vonal stb.). Az első argumentum egy `ShapeType` enum érték:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tipp**: Ha a alakzatot egy adott helyen szeretnéd elhelyezni az oldalon, használd a `builder.MoveTo`-t az insertion pont beállításához az `InsertShape` meghívása előtt.

## Téglalap alakzat hozzáadása meglévő dokumentumhoz

Gyakran egy sablont bővítesz, nem pedig a nulláról indulsz. Cseréld le az 1. lépést a következőre:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Az összes további lépés változatlan marad, és a téglalap a builder kurzorának aktuális pozíciójához lesz hozzáadva (alapértelmezés szerint a dokumentum végéhez).

## Szélsőséges esetek és változatok kezelése

### 1. Az alakzat újra láthatóvá tétele

Ha a munkafolyamat későbbi része szükségessé teszi a rejtett téglalap megjelenítését, egyszerűen állítsd vissza a jelzőt:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Szegély (stroke) hozzáadása

Egy rejtett alakzat is rendelkezhet látható szegéllyel, amikor megjeleníted. Állítsd be a `LineColor` és `LineWidth` tulajdonságokat:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. A téglalap abszolút pozicionálása

Precíz elrendezéshez állítsd a forma `WrapType`-ját `WrapType.Inline` (alapértelmezett) vagy `WrapType.TopBottom` értékre, és módosítsd a `Left`/`Top` tulajdonságokat:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Más mérőegység használata

Az Aspose.Words pontokban dolgozik (1 pt = 1/72 inch). Ha centimétert szeretnél használni, először konvertálj:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Teljesen futtatható példa

Az alábbi *teljes* programot másolhatod, beillesztheted és futtathatod. Tartalmazza az összes szükséges `using` direktívát, és abszolút útvonalakat, amelyeket a saját környezetedhez kell igazítanod.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Várható eredmény**: A `HiddenRectangleShape.docx` fájl Microsoft Word-ben *nem látható alakzat* nélkül nyílik meg, de a rejtett téglalap jelen van a dokumentum XML-jében. Ellenőrizheted a létezését úgy, hogy a .docx-et zip-archívumként megnyitod, és a `word/document.xml` fájlban keresel egy `<w:shape>` elemet `w:fill="yellow"` és `w:hidden="true"` attribútumokkal.

## Következtetés

Most már tudod, hogyan **szúrj be téglalap alakzatot** egy Word dokumentumba C# és Aspose.Words segítségével, hogyan **állítsd be a kitöltő színt**, és hogyan **rejtse el az alakzatot**, hogy az a végső elrendezésben láthatatlan maradjon. Ugyanez a minta más alakzatokra, egyedi színekre és meglévő sablonokra is alkalmazható. Kísérletezz szegélyekkel, abszolút pozicionálással és különböző mérőegységekkel, hogy az alakzat pontosan megfeleljen az igényeidnek.

### Következő lépések

* Fedezd fel, **hogyan szúrj be alakzatot** táblázatokba vagy fejlécek/láblécekbe vízjelekhez.
* Kombináld a **téglalap alakzat hozzáadását** tartalomvezérlőkkel, hogy dinamikus helyőrzőket hozz létre.
* Tekintsd át az Aspose.Words **alakzatkezelő** API-ját fejlett funkciókért, mint a forgatás, színátmenetes kitöltések és SVG import.

Nyugodtan adaptáld a kódot a saját projektedhez, és írd meg a hozzászólásokban, melyik alakzat‑kapcsolatos kihívást oldottad meg legközelebb!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek további API‑funkciók elsajátításában és alternatív megvalósítási megközelítések felfedezésében a saját projektjeidben.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}