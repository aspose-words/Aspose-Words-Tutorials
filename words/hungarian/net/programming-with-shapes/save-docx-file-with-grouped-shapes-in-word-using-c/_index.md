---
category: general
date: 2026-08-04
description: Mentse el a docx fájlt programozottan, miközben téglalap alakzatot ad
  hozzá és csoportosítja az alakzatokat a Wordben. Tanulja meg, hogyan állíthatja
  be az alakzat méreteit, és hogyan hozhat létre szövegdobozt programozottan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: hu
lastmod: 2026-08-04
og_description: DOCX fájl mentése C#-ban téglalap alakzat hozzáadásával, alakzatok
  csoportosításával a Wordben, alakzat méreteinek beállításával és szövegdoboz programozott
  létrehozásával.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: DOCX fájl mentése csoportosított alakzatokkal a Wordben – C# lépésről‑lépésre
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: DOCX fájl mentése csoportosított alakzatokkal a Wordben C#-val
url: /hu/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX fájl mentése csoportosított alakzatokkal a Wordben C# használatával

Ha **docx fájlt kell menteni**, amely több, egymás mellé rendezett alakzatot tartalmaz, ez az útmutató megmutatja, hogyan teheted ezt C#-ben. Megtanulod, hogyan **adj hozzá téglalap alakzatot**, csoportosíts több alakzatot egy Word dokumentumban, **állítsd be az alakzat méreteit**, és **hozz létre szövegdobozt programozottan**. A megoldás a legújabb Aspose.Words for .NET verzióval működik, és .NET 6 vagy újabb környezetben fut.

Az útmutató minden lépésen végigvezet, a projekt beállításától a végső `doc.Save` hívásig. A végére egy újrahasználható kódrészletet kapsz, amelyet bármely konzol vagy ASP.NET projektbe beilleszthetsz. Nem szükséges külső szkript vagy a DOCX fájl manuális szerkesztése.

## Előkövetelmények

* .NET 6 SDK (vagy újabb) telepítve.
* Érvényes licenc a **Aspose.Words for .NET**-hez (az ingyenes próba verzió teszteléshez használható).
* Visual Studio 2022, VS Code vagy bármely IDE, amely .NET projekteket tud építeni.

A kód csak az Aspose.Words névteret használja, így nincs szükség további NuGet csomagokra.

## DOCX fájl mentése csoportosított alakzatokkal a Wordben

A megoldás központja egy `GroupShape` létrehozása, amely tartalmaz egy téglalapot és egy szövegdobozt, majd a csoport beszúrása a dokumentumba és a `doc.Save` meghívása. A következő szakaszok a folyamatot kezelhető részekre bontják.

### 1. Új dokumentum és builder létrehozása

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Miért fontos ez a lépés* – Egy új `Document` objektum egy üres *.docx* fájlt képvisel. A `DocumentBuilder` magas szintű metódusokat biztosít, például az `InsertNode`-t, amelyet a csoportos alakzat elhelyezésére használunk.

### 2. Téglalap alakzat hozzáadása a csoporthoz

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Miért fontos ez a lépés* – A **téglalap alakzat hozzáadása** művelet bemutatja, hogyan definiáljunk egy vizuális elemet pontos mérettel és pozícióval. A téglalap a `group`-on belül él, így a csoport későbbi mozgatása automatikusan a téglalapot is mozgatja.

### 3. Alakzatok csoportosítása a Word dokumentumban

A `GroupShape` osztály több rajzobjektumot aggregál. A csoportosítás hasznos, ha több objektumot egy egységként szeretnél kezelni (pl. mozgatás, forgatás vagy közös másolás).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Miért csoportosítunk* – A csoportosítás csökkenti az elrendezés bonyolultságát. Ahelyett, hogy minden alakzatot egyenként pozicionálnál az oldalon, egyszer állítod be a csoport `Left`, `Top`, `Width` és `Height` értékeit.

### 4. Alakzat méreteinek beállítása a pontos elrendezéshez

A csoportnak és annak gyermek alakzatainak is explicit méretekre van szükségük; ellenkező esetben a Word alapértelmezett méreteket alkalmaz, amelyek nem feltétlenül egyeznek a tervezéseddel.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Miért állítjuk be a méreteket* – A pontos mérés biztosítja, hogy a téglalap és a szövegdoboz ne fedjék egymást véletlenül, és hogy a végső **docx fájl mentése** megfeleljen a tervezett elrendezésnek.

### 5. Szövegdoboz létrehozása programozottan a csoporton belül

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Miért fontos ez a lépés* – A **szövegdoboz programozott létrehozása** rész bemutatja, hogyan ágyazz be gazdag szöveget egy alakzatba. A `Paragraph` és `Run` használata teljes irányítást ad a formázás felett később.

### 6. Csoportos alakzat beszúrása és **docx fájl mentése**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Miért fontos ez az utolsó lépés* – Az `InsertNode` hívás pontosan oda helyezi a csoportos alakzatokat, ahol a builder kurzora áll. A `doc.Save` metódus végrehajtja a **docx fájl mentése** műveletet, és egy teljes funkcionalitású Word dokumentumot ír a lemezre.

> **Eredmény:** A *GroupShape.docx* megnyitása a Microsoft Wordben bal oldalon egy téglalapot, jobb oldalon egy szövegdobozt jelenít meg, mindkettő egyetlen csoportban rögzítve. A csoportot egységként mozgathatod, átméretezheted, vagy további formázást alkalmazhatsz.

## Teljes, futtatható példa

Másold az alábbi kódot egy új konzol projektbe (`dotnet new console`), és futtasd a `dotnet run` parancsot. A program létrehozza a `GroupShape.docx` fájlt a projekt kimeneti mappájában.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Várt kimenet

* Egy **GroupShape.docx** nevű fájl jelenik meg a kimeneti könyvtárban.
* A fájl megnyitása bal oldalon egy téglalap alakzatot, jobb oldalon egy „Grouped text” szöveget tartalmazó szövegdobozt mutat, mindkettő együtt rögzítve.
* Bármelyik alakzat kiválasztása az egész csoportot mozgatja, megerősítve, hogy a **group shapes word** funkció a várt módon működik.

## Gyakori variációk és szélhelyzetek

| Situation | Recommendation |
|-----------|----------------|
| Több mint két alakzatra van szükség | Adj hozzá további `Shape` objektumokat a `group`-hoz, mielőtt meghívod a `builder.InsertNode`-t. |
| A csoportot egy adott oldalon szeretnéd megjeleníteni | Mozgasd a builder kurzorát a `builder.MoveToDocumentEnd()` vagy a `builder.MoveToPage(pageNumber)` segítségével. |
| Más mértékegységek (pl. centiméter) szükségesek | Használd a `ConvertUtil.InchToPoint(1.0)`-t a hüvelyk pontokra való átváltáshoz, a Word által elvárt mértékegységhez. |
| A szövegdoboznak szeretnél szöveget körbefuttatni | Állítsd be a `textBox.TextBoxWrap = TextBoxWrapType.Square` értéket a szövegdoboz létrehozása után. |
| Régebbi .NET Framework verziókkal való munka | Ugyanez az API működik a .NET Framework 4.7+ verziókkal, de győződj meg róla, hogy a megfelelő Aspose.Words verzióra hivatkozol. |

**Pro tipp:** Mindig a gyermek alakzatok hozzáadása *után* állítsd be a csoport `Width` és `Height` értékeit. Ez garantálja, hogy a csoport teljesen körülöleli a tartalmát, megakadályozva a levágást, amikor a dokumentumot Wordben megnyitod.

## Következtetés

Most már tudod, hogyan **menthetsz docx fájlt**, miközben **téglalap alakzatot adsz hozzá**, **csoportosítod az alakzatokat Wordben**, **beállítod az alakzat méreteit**, és **szövegdobozt hozol létre programozottan** az Aspose.Words for .NET használatával. A teljes példa egy tiszta, újrahasználható mintát mutat, amelyet összetettebb elrendezésekhez, például diagramokhoz, képekhez is adaptálhatsz,

## Mit érdemes még megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Téglalap alakzat létrehozása Wordben C# használatával – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Csoportos alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words alakzat árnyék tutorial – Árnyék hozzáadása Word alakzathoz C#-ban](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}