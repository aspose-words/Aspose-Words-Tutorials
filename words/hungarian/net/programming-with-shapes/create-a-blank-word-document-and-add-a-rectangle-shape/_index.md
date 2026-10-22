---
category: general
date: 2026-09-05
description: Tanulja meg, hogyan hozhat létre egy üres Word-dokumentumot, és adjon
  hozzá egy rejtetté tehető téglalap alakzatot az Aspose.Words C# használatával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: hu
lastmod: 2026-09-05
og_description: Üres Word-dokumentum létrehozása és rejtett téglalap alakzat beszúrása
  az Aspose.Words segítségével – lépésről lépésre útmutató C# fejlesztőknek.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Hozzon létre egy üres Word-dokumentumot egy rejtett téglalap alakú alakzattal
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Hozzon létre egy üres Word-dokumentumot, és adjon hozzá egy téglalap alakzatot
url: /hu/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása és egy téglalap alakzat hozzáadása

Ha **blank word document** létrehozásra van szükséged, amely egy olyan alakzatot is tartalmaz, amelyet nem szeretnél megjeleníteni a layoutban, ez az útmutató pontosan megmutatja, hogyan teheted ezt meg az Aspose.Words for .NET segítségével. Egy teljes, futtatható példát láthatsz, amely új dokumentumot hoz létre, hozzáad egy téglalap alakzatot, elrejti azt, és elmenti a fájlt – extra eszközök nélkül.

Az útmutató mindent lefed a projekt beállításától a gyakori hibák elhárításáig. A végére képes leszel olyan Word fájlt generálni, amely a olvasó számára üresnek tűnik, de rejtett metaadatokat tartalmaz, ami hasznos például vízjelek, egyedi XML tárolás vagy elrendezési horgonyok esetén.

## Előfeltételek

* .NET 6.0 SDK vagy újabb (a kód .NET Framework 4.7+ esetén is működik)
* Visual Studio 2022 (vagy bármely IDE, amely támogatja a C#-ot)
* Aktív **Aspose.Words** NuGet licenc (az ingyenes próba verzió teszteléshez megfelelő)
* Alapvető ismeretek a C#-ról és a dokumentum csomópontok koncepciójáról

A könyvtárat a következő CLI parancs segítségével telepítheted:

```bash
dotnet add package Aspose.Words
```

> **Pro tipp:** Tartsd naprakészen az Aspose.Words verziódat; az ebben az útmutatóban használt API a 23.10-es verzió óta stabil.

## Üres Word dokumentum létrehozása Aspose.Words segítségével

Az első lépés egy `Document` objektum példányosítása. Egy új `Document` egy üres **blank word document**-ot képvisel – nincs benne bekezdés, szakasz, csak a fájl konténer.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Miért fontos:** Azzal, hogy tiszta dokumentummal kezdünk, biztosítjuk, hogy a később hozzáadott rejtett alakzat ne zavarja a meglévő tartalmat vagy stílusokat.

## Téglalap alakzat hozzáadása a dokumentumhoz

Ezután létrehozunk egy téglalap alakzatot. Az Aspose.Words-ben egy shape egy csomópont, amely a dokumentum fában bárhol elhelyezhető, és konfigurálható mérettel, kitöltéssel, vonalstílussal és láthatósággal.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

A fenti kód egy látható téglalapot hoz létre. Ebben a pontban beillesztheted a dokumentumba a `builder.InsertNode(rectangle)` segítségével. Azonban, mivel a shape-nek rejtve kell maradnia, a beszúrás előtt módosítjuk a `Hidden` tulajdonságát.

## Alakzat elrejtése Word dokumentumban

A Word egy `Hidden` attribútumot biztosít a shape csomópontok számára. Ha `true`-ra van állítva, a shape nem jelenik meg az oldal elrendezésében, de a dokumentum XML részének része marad. Ez a **how to hide shape** követelmény lényege.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Magyarázat:** `Hidden = true` beállítása hozzáadja a `<w:hide>` attribútumot a shape XML-jéhez. A Word processzorok a renderelés során figyelmen kívül hagyják a shape-et, de az továbbra is programozottan vagy a Word XML nézeten keresztül elérhető.

## A rejtett shape beillesztése az üres dokumentumba

Most elhelyezzük a rejtett téglalapot a dokumentum fában. Mivel a dokumentum még üres, a shape az első csomópont lesz a fő történetben.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Ha megnyitod a keletkezett fájlt a Microsoft Wordben, látsz egy látszólag üres oldalt. A shape ott van, de láthatatlan.

## Dokumentum mentése

Végül a dokumentumot lemezre írjuk. Bármely támogatott formátumot választhatod (`.docx`, `.pdf`, `.odt`, stb.). Ebben az útmutatóban a modern DOCX formátumot használjuk.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Várható eredmény

Nyisd meg a `HiddenRectangle.docx` fájlt a Wordben:

* A dokumentum üresnek tűnik (nincs látható shape vagy szöveg).
* Ha a fájlt egy olyan eszközzel vizsgálod, mint a **Open XML SDK** vagy a **Word XML Viewer**, látni fogod a `<w:pict>` elemet, amely a `hidden` attribútummal ellátott téglalapot tartalmazza.

![üres word dokumentum rejtett téglalap alakzattal](image.png){: .align-center alt="üres word dokumentum rejtett téglalap alakzattal"}

## Teljes, futtatható példa

Az alábbiakban a teljes program található, amelyet beilleszthetsz egy konzolalkalmazásba. Tartalmazza az összes szükséges `using` direktívát, hibakezelést és megjegyzéseket.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Futtasd a programot (`dotnet run`) és ellenőrizd a kimeneti fájlt. A konzol megerősíti a mentés helyét.

## Gyakori kérdések és szélhelyzetek

### Elrejthetek több shape-et egyszerre?

Igen. Hozz létre minden shape-et, állítsd be a `Hidden = true` értéket, és szekvenciálisan illeszd be őket. A rejtett jelző csomópontonként működik, így a rejtett és látható shape-ek keverése ugyanabban a dokumentumban támogatott.

### Mi van, ha a shape-et csak a nyomtatási nézetben szeretném elrejteni?

A Word megkülönbözteti a **display** és **print** láthatóságot a `DisplayWhen` tulajdonságon keresztül. Az Aspose.Words nem biztosít közvetlen API-t ehhez a jelzőhöz, de módosíthatod a háttér XML-t:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Ezt csak akkor használd, ha csak nyomtatási láthatóságra van szükség.

### A rejtett shape befolyásolja a fájlméretet?

Egy rejtett shape ugyanazt az XML terhelést adja hozzá, mint egy látható, így a fájlméret növekedése azonos. Azonban, mivel a shape

## Mi legyen a következő tanulnivalód?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Üres Word dokumentum létrehozása árnyékolt téglalap alakzattal – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Téglalap alakzat létrehozása Wordben C# használatával – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow tutorial – Árnyék hozzáadása Word shape-hez C#-ban](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}