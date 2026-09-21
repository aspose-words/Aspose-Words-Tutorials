---
category: general
date: 2026-09-21
description: Hozzon létre egy üres Word-dokumentumot az Aspose.Words segítségével,
  állítsa be a forma méretét, pozícióját és színét, majd egyetlen lépésben mentse
  el a docx fájlt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: hu
lastmod: 2026-09-21
og_description: Készítsen egy üres Word-dokumentumot, állítsa be az alakzat méretét,
  pozícióját és színét, majd mentse el a docx fájlt az Aspose.Words segítségével percek
  alatt.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Készítsen egy üres Word-dokumentumot, és adjon hozzá színes alakzatokat
  – Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hozzon létre egy üres Word-dokumentumot, és adjon hozzá színes alakzatokat
  az Aspose.Words segítségével
url: /hu/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása és színes alakzatok hozzáadása Aspose.Words segítségével

Ha programozott módon **üres Word dokumentumot kell létrehoznod**, ez az útmutató megmutatja, hogyan teheted meg az Aspose.Words használatával. Megtanulod, hogyan **állítsd be az alakzat méretét**, **állítsd be az alakzat pozícióját**, **állítsd be az alakzat színét**, és végül **mentse el a docx fájlt** anélkül, hogy elhagynád az IDE‑det.

A Word fájlok C#‑ban történő kezelése gyakran alacsony szintű OpenXML hívásokkal jár, de az Aspose.Words elrejti a bonyolultságot. A tutorial végére egy teljesen működő `.docx` fájlod lesz, amely egy csoportos alakzatot tartalmaz két színes téglalappal – tökéletes jelentésekhez, tanúsítványokhoz vagy egyedi sablonokhoz.

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑vel is működik)
- Aspose.Words for .NET 23.9 vagy újabb (telepítés NuGet‑en: `Install-Package Aspose.Words`)
- Alapvető C# és Visual Studio (vagy bármely C# szerkesztő) ismeretek

Nem szükséges meglévő Word fájl; a tutorial **üres Word dokumentum létrehozásával** indul a semmiből.

## Üres Word dokumentum létrehozása Aspose.Words‑szal

Az első lépés egy `Document` objektum példányosítása. Ez az objektum egy üres Word fájlt reprezentál a memóriában.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

A `Document` eleve üres, ami pontosan az, amire szükséged van, amikor **üres Word dokumentumot hozol létre**. A `builder` később arra szolgál, hogy a forma csoportot a jelenlegi kurzorpozícióba illessze be.

## Alakzat méretének beállítása és GroupShape létrehozása

A `GroupShape` egy konténerként működik, amely több egyedi alakzatot is tartalmazhat. Először definiáld a konténer teljes méretét.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Itt **állítjuk be az alakzat méretét** a csoport számára (300 × 200). Ugyanazok a tulajdonságnevek (`Width`, `Height`) minden gyermek alakzatra is vonatkoznak, így finomhangolhatod az egyes elemeket.

## Az első téglalap hozzáadása és az alakzat színének beállítása

Adjunk hozzá egy téglalapot a csoporthoz, és adjunk neki háttérszínt.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

A `FillColor` tulajdonság **állítja be az alakzat színét**. A `System.Drawing.Color` használatával bármely előre definiált vagy egyedi ARGB értéket kiválaszthatsz.

## Második téglalap hozzáadása, méretének, pozíciójának és színének beállítása

A második téglalap bemutatja, hogyan **állítsd be az alakzat pozícióját** a csoporton belül, és hogyan változtasd meg a színét.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Mivel a csoport szélessége 300 pont, a két 120‑pontos téglalap kényelmesen elfér egy 30‑pontos hézaggal. A `Left` és `Top` értékeket módosíthatod, ha más elrendezést szeretnél.

## A GroupShape beszúrása a dokumentumba

Miután a csoport teljesen be van állítva, helyezd el a jelenlegi kurzorpozícióban.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

Az `InsertNode` közvetlenül a dokumentum törzsébe írja be az alakzatot, megőrizve a korábban **beállított alakzat pozícióját**.

## A docx fájl mentése

Az utolsó lépés a dokumentum lemezre írása. Ez bemutatja a **docx fájl mentése** műveletet.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

A program futtatása után nyisd meg a `GroupShape.docx` fájlt a Microsoft Word‑ben. Egy üres oldalt kell látnod, amelyen egy csoportos alakzat található két színes téglalappal, egymás mellett elhelyezve.

### Várt kimenet

- Egyoldalas `.docx` fájl.
- Az oldal egy 100 pts bal‑ és felső margótól elhelyezkedő csoportos alakzatot tartalmaz.
- A csoporton belül egy világoskék téglalap a bal oldalon, egy világoskoral téglalap a jobb oldalon, mindkettő 120 × 80 pts méretű.

## Teljes, futtatható példa

Az alábbi teljes programot egyszerűen másold be egy konzolalkalmazásba. További fájlok nem szükségesek.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

A program futtatása pontosan a fent leírt dokumentumot hozza létre, teljesítve a négy célkitűzést: **üres Word dokumentum létrehozása**, **alakzat méretének beállítása**, **alakzat pozíciójának beállítása**, **alakzat színének beállítása**, és **docx fájl mentése**.

## Gyakori variációk és szélhelyzetek

| Forgatókönyv | Mit kell módosítani | Miért fontos |
|--------------|---------------------|--------------|
| **Eltérő alakzat típusok** | Cseréld le a `ShapeType.Rectangle`‑t `ShapeType.Ellipse`, `ShapeType.Triangle` stb. értékre | Lehetővé teszi összetettebb grafikák építését külső képek nélkül. |
| **Dinamikus méretek** | Számold ki a `Width` és `Height` értékeket felhasználói bemenet vagy konfigurációs fájl alapján. | Újrahasználható megoldást biztosít több dokumentumsablonhoz. |
| **Mentés PDF‑ként** | Hívd meg a `document.Save("output.pdf", SaveFormat.Pdf);` metódust | Ha a címzettek nem szerkeszthető formátumot igényelnek, a PDF biztonságos választás. |
| **Szöveg hozzáadása egy alakzathoz** | Hozz létre egy `TextBox` alakzatot és állítsd be a `TextBox.Text`‑et. | Hasznos címkék vagy felhívások létrehozásához. |
| **Több csoport egy oldalon** | Ismételd meg a 2‑5. lépéseket különböző `Left`/`Top` értékekkel. | Lehetővé teszi irányítópultok vagy több szekciós elrendezések építését. |

### Pro tipp

Amikor pontos igazítást igénylő alakzatokra van szükséged, a `ShapeBase.WrapType = WrapType.Inline` tulajdonságot állítsd be a csoport beszúrása előtt. Ez a csoportot bekezdésként viselkedővé teszi, megakadályozva a váratlan szövegáramlást körülötte.

## Összegzés

Most már tudod, hogyan **hozz létre egy üres Word dokumentumot** az Aspose.Words‑szal, **állítsd be az alakzat méretét**, **állítsd be az alakzat pozícióját**, **állítsd be az alakzat színét**, és **mentsd el a docx fájlt**. A teljes példa egy tiszta, újrahasználható mintát mutat be csoportos grafikák hozzáadásához bármely Word automatizálási projekthez.

Innen tovább felfedezheted:

- További alakzatok vagy képek hozzáadása ugyanahhoz a `GroupShape`‑hez (**alakzat méretének beállítása**, **alakzat színének beállítása** variációk).
- A `ShapeBase.Rotation` használata a téglalapok forgatásához dekoratív hatás érdekében.
- Ugyanannak a dokumentumnak a PDF‑ vagy HTML‑ként való exportálása a terjesztés szélesebb körű lehetőségeiért (**docx fájl mentése** alternatívaként).

Kísérletezz bátran különböző színekkel, méretekkel és elrendezési logikákkal, hogy megfeleljenek a saját jelentési vagy sablonigényeidnek. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?


Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek az API további funkcióinak elsajátításában és alternatív megvalósítási megközelítések felfedezésében saját projektjeidben.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}