---
category: general
date: 2026-09-08
description: Tanulja meg, hogyan hozhat létre üres Word-dokumentumot, szúrjon be téglalap
  alakzatot, és csoportosítson több alakzatot C#‑ban. Kövesse ezt a lépésről‑lépésre
  útmutatót.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: hu
lastmod: 2026-09-08
og_description: Hozzon létre üres Word-dokumentumot, szúrjon be téglalap alakzatot,
  és csoportosítson több alakzatot C#-ban. Ez az útmutató végigvezet a teljes folyamaton.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Üres Word-dokumentum létrehozása csoportosított alakzatokkal C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hogyan készítsünk üres Word-dokumentumot csoportosított alakzatokkal
url: /hu/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása csoportosított alakzatokkal

Ha **üres Word dokumentumot** kell létrehoznod, amely egyedi grafikákat tartalmaz, ez az útmutató pontosan megmutatja, hogyan. Megtanulod, hogyan **helyezz be egy téglalap alakzatot**, **csoportosíts több alakzatot**, és **adj hozzá alakzatokat a csoporthoz** az Aspose.Words for .NET használatával.

Egy üres dokumentum tiszta vásznat biztosít, és az alakzatok csoportosítása lehetővé teszi, hogy egy egységként mozgass, átméretezz vagy elforgass őket. Ez az oktatóanyag minden lépést lefed – a dokumentum inicializálásától a végleges fájl mentéséig – így a kódot átmásolhatod a saját projektedbe, és azonnali eredményeket láthatsz.

## Amire szükséged lesz

* .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑vel is működik)
* Érvényes Aspose.Words for .NET licenc (az ingyenes értékelés teszteléshez használható)
* IDE, például Visual Studio 2022 vagy Visual Studio Code
* Alapvető ismeretek a C# szintaxisról

Nem szükséges további NuGet csomag a `Aspose.Words`-en kívül.

## Üres Word dokumentum létrehozása

Az első lépés egy `Document` objektum példányosítása. Ez az objektum egy üres `.docx` fájlt képvisel, amelyet egy `DocumentBuilder`‑rel szerkeszthetsz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` konstruktor **üres Word dokumentumot** hoz létre a memóriában. A `DocumentBuilder` egy folyékony API‑t biztosít szöveg, kép és rajzobjektumok beszúrásához.

## Téglalap alakzat beszúrása a dokumentumba

Ezután adj hozzá egy téglalap alakzatot. A téglalap lesz a csoport első gyermekeleme, amelyet később létrehozunk.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

`InsertShape` hívása `ShapeType.Rectangle`‑el **beszúr egy téglalap alakzatot** az aktuális kurzorpozícióba. A szélesség és magasság pontban van megadva (1 pt ≈ 1/72 in).

## Több alakzat csoportosítása együtt

A `GroupShape` egy tárolóként működik. A csoporton belüli összes gyermek alakzat együtt mozog és alakul. Először hozd létre a csoportot, majd add hozzá a most épített téglalapot.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Az `InsertGroupShape` metódus egy üres csoportot helyez el a builder kurzoránál. A téglalap hozzáfűzésével **csoportosítunk több alakzatot** – a téglalap a csoport belső csomópontgyűjteményének részévé válik.

## Alakzatok hozzáadása a csoporthoz és a fájl mentése

Most adj hozzá egy második alakzatot – egy ellipszist – hogy bemutasd, hogyan osztoznak több objektum ugyanazon a tárolón. Ezután mentsd a dokumentumot.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Az `InsertShape` hívás **alakzatokat ad a csoporthoz**, amikor a visszaadott `Shape`‑t a `GroupShape`‑hez fűzöd. A `Document` mentése egy `.docx` fájlt ír, amelyet megnyithatsz a Microsoft Word, a LibreOffice vagy bármely kompatibilis megjelenítő programban.

### Várható eredmény

Amikor megnyitod a *GroupShapeDemo.docx* fájlt, egy üres oldalt látsz egy csoportosított objektummal, amely egy világoskék téglalapot és egy rózsaszín ellipszist tartalmaz. A csoport kiválasztása lehetővé teszi, hogy mindkét alakzatot együtt mozgass, ami megerősíti, hogy a **csoportosított több alakzat** a várt módon működött.

## Miért használjunk GroupShape‑t?

* **Atomikus transzformációk** – A csoport méretezése, forgatása vagy mozgatása minden gyermeket egyenletesen érint.
* **Logikai szervezés** – Kapcsolódó grafikákat együtt tart, megkönnyítve a dokumentumszerkezet karbantartását.
* **Teljesítmény** – Egyetlen tároló renderelése gyakran gyorsabb, mint sok önálló alakzat kezelése.

Ha később egyetlen gyermeket kell módosítanod, lekérheted azt a `group.ChildNodes`‑ból index vagy a `Name` tulajdonsága alapján.

## Gyakori variációk és szélhelyzetek

| Forgatókönyv                              | Hogyan módosítsd a kódot                                                       |
|-------------------------------------------|---------------------------------------------------------------------------------|
| **Különböző alakzat típusok**             | Cseréld le a `ShapeType.Rectangle` vagy `ShapeType.Ellipse` értékeket bármely más `ShapeType`‑ra |
| **Szöveg hozzáadása egy alakzathoz**      | Használd a `Shape.TextPath.Text = "Hello"`-t az alakzat beszúrása után          |
| **Forgatási szög beállítása**             | `group.Rotation = 45;` (fokban)                                                 |
| **Mentés PDF‑ként a DOCX helyett**        | `doc.Save("GroupShapeDemo.pdf");`                                               |
| **Keretszín alkalmazása a csoportra**     | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Pro tippek

* **Nevezd el az alakzatokat** – `rectangle.Name = "MyRect";` megkönnyíti a későbbi megtalálásukat.
* **Használj relatív pozicionálást** – Állítsd be a `group.RelativeHorizontalPosition` értékét `RelativeHorizontalPosition.Page`‑re, ha azt szeretnéd, hogy a csoport a lap margójához legyen rögzítve.
* **Erőforrások felszabadítása** – A `Document`‑et `using` blokkba tedd nagyobb alkalmazásoknál, hogy a nem kezelt memória gyorsan felszabaduljon.

## Teljes forráskód gyors másoláshoz

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Másold a kódot egy új konzolprojektbe, állítsd vissza a `Aspose.Words` NuGet csomagot, és futtasd. A kimeneti fájl a projekt `bin/Debug/net6.0` (vagy ekvivalens) mappájában jelenik meg.

## Következő lépések

Most, hogy **üres Word dokumentumot tudsz létrehozni**, **téglalap alakzatot beszúrni**, és **több alakzatot csoportosítani**, érdemes lehet felfedezni:

* **Szövegdobozok** hozzáadása a csoporthoz címkézett diagramok létrehozásához.
* A csoportosított grafika exportálása képként a `doc.Save("image.png", SaveFormat.Png)` használatával.
* Csoportok kombinálása táblázatokkal gazdag formátumú jelentésekhez.

Kísérletezz különböző alakzat tulajdonságokkal, csoport hierarchiákkal és export formátumokkal, hogy teljes mértékben kiaknázd az Aspose.Words rajzolási képességeit.

--- 

*Emlékezz*: az alakzatok csoportosítása hatékony módja a Word dokumentumok rendezett tartásának és a kód karbantarthatóságának. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Téglalap alakzat létrehozása Word-ben C#‑val – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Alakzatok beszúrása Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Csoportos alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}