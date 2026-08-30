---
category: general
date: 2026-08-04
description: Helyezzen be téglalap alakzatot egy Word-dokumentumba C#-val. Tanulja
  meg, hogyan csoportosíthatók az alakzatok Wordben, hogyan menthető a dokumentum
  docx formátumban, és hogyan használható a DocumentBuilder fejlett elrendezésekhez.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: hu
lastmod: 2026-08-04
og_description: Helyezzen be egy téglalap alakzatot egy Word-fájlba C#-val, majd csoportosítsa
  az alakzatokat fejlett elrendezésekhez. Ez az útmutató azt is bemutatja, hogyan
  mentse a dokumentumot docx formátumban, és hogyan használja hatékonyan a DocumentBuilder-t.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Téglalap alakzat beszúrása a Wordben – C# lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Téglalap alakzat beszúrása Wordbe C#-val – teljes útmutató
url: /hu/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat beszúrása Word dokumentumba C#-val – teljes útmutató

Ha **téglalap alakzatot** kell beszúrni egy Word dokumentumba C#-val, ez a bemutató pontosan megmutatja, hogyan teheted. Emellett megtanulod, **hogyan csoportosíts alakzatokat** a Wordben, **hogyan mentsd a dokumentumot docx formátumban**, és **hogyan használd a Builder-t** a tiszta, karbantartható kód érdekében.

Az alakzatokkal való munka gyakori követelmény jelentések, bizonyítványok vagy egyedi elrendezések programozott generálásakor. A útmutató végére egy teljesen futtatható példát kapsz, amely létrehoz egy téglalapot, hozzáad egy ellipszist, csoportosítja őket, és a végeredményt DOCX fájlként menti.

## Előfeltételek

* .NET 6.0 vagy újabb telepítve  
* Visual Studio 2022 (vagy bármely IDE, amely támogatja a C#-t)  
* Az **Aspose.Words for .NET** könyvtár (elérhető a NuGet-en keresztül)  

A könyvtárat a következő paranccsal adhatod hozzá:

```bash
dotnet add package Aspose.Words
```

## Téglalap alakzat beszúrása DocumentBuilder-rel

Az első lépés egy új `Document` és egy `DocumentBuilder` létrehozása. A builder egy folyékony API-t biztosít a tartalom, köztük az alakzatok beszúrásához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

A `DocumentBuilder` példány a fő objektum, amelyet a **téglalap alakzat** és egyéb elemek beszúrásához használsz. Nyomon követi a dokumentumban lévő aktuális kurzorpozíciót, így minden beszúrás pontosan ott történik, ahol szükséges.

## Hogyan szúrj be egy téglalap alakzatot

Miután a builder készen áll, hívd a `InsertShape` metódust. Megadod a `ShapeType`-ot, a szélességet és a magasságot pontban (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Miért fontos*: A `FillColor` és a `StrokeColor` beállítása vizuálisan megkülönböztethetővé teszi a téglalapot, ami segít, amikor később más alakzatokkal csoportosítod.

## Hogyan csoportosíts alakzatokat a Wordben

Az alakzatok csoportosítása lehetővé teszi több objektum mozgatását, forgatását vagy formázását egyetlen egységként. A téglalap beszúrása után adj hozzá egy másik alakzatot (ebben a példában egy ellipszist), majd hozd létre a `GroupShape`-t.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Az `InsertGroupShape` hívás egy helyőrzőt hoz létre, amely tetszőleges számú gyermek alakzatot tarthat. A téglalap és az ellipszis hozzáadásával hatékonyan **csoportosítod az alakzatokat a Wordben**. A csoport egyetlen alakzatként viselkedik – áthelyezheted, szegélyt alkalmazhatsz rá, vagy átméretezheted anélkül, hogy befolyásolná a gyermekek belső elrendezését.

### Pro tipp

A csoportosítás után megváltoztathatod a csoport pozícióját az oldalhoz képest:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Dokumentum mentése docx formátumban

Miután az alakzatok el vannak helyezve, a fájlt el kell menteni. A `Document.Save` metódus automatikusan a fájlkiterjesztés alapján határozza meg a formátumot. A **dokumentum docx formátumban történő mentéséhez** adj meg egy `.docx`-re végződő elérési utat.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

A program futtatása létrehozza a `output.docx` fájlt. Nyisd meg a fájlt a Microsoft Wordben, és láthatod, hogy egy világoskék téglalap és egy világos korall színű ellipszis van együtt csoportosítva. Rákattintva a csoportra egyetlen objektumként mozgathatod.

## Hogyan használd hatékonyan a DocumentBuilder-t

A `DocumentBuilder` nem csak alakzat beszúró; kezel szöveget, táblázatokat, fejléceket és lábléceket is. Amikor alakzat létrehozását szöveggel kombinálod, ne felejtsd el visszaállítani a kurzort, ha máshová kell tartalom beszúrni:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

A builder állapotának explicit kezelése elkerüli a véletlen felülírásokat, és a kód karbantartását is egyszerűbbé teszi.

## Szélsőséges esetek és változatok

| Helyzet | Ajánlott megközelítés |
|-----------|----------------------|
| **Kétnél több alakzat** | Szúrj be minden alakzatot, majd a mentés előtt hívd meg a `AppendChild`-et minden alakzatra. |
| **Egymásba ágyazott csoportok** | Hozz létre egy csoportot, adj hozzá alakzatokat, majd illeszd be ezt a csoportot egy másik `GroupShape`-ba. |
| **Eltérő mérőegységek** | Használd a `builder.ConvertPixelsToPoints`-ot, ha a méreteket pixelekben adod meg. |
| **Kompatibilitás régebbi Word verziókkal** | Mentsd `.doc` formátumban a kiterjesztés megváltoztatásával; a legtöbb alakzat funkció továbbra is működik. |

## Teljes működő példa

Az alábbiakban a teljes programot találod, amelyet beilleszthetsz egy új konzolprojektbe. További kódrészletek nem szükségesek.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Várható eredmény**: A `output.docx` megnyitása egy világoskék téglalapot és egy világos korall színű ellipszist mutat, amelyek együtt csoportosítva vannak, 150 pt-re a bal margótól és 100 pt-re a tetejétől. A felirat a csoport alatt jelenik meg.

## Összegzés

Most már tudod, hogyan **szúrj be téglalap alakzatot** egy Word fájlba C#-val, **hogyan csoportosíts alakzatokat a Wordben**, és **hogyan mentsd a dokumentumot docx formátumban** az Aspose.Words `DocumentBuilder` segítségével. E lépések elsajátításával összetett elrendezéseket – bizonyítványokat, jelentéseket vagy egyedi űrlapokat – teljesen kódból építhetsz.

Ezután fedezd fel a kapcsolódó témákat, például **szövegdobozok hozzáadása**, **táblázatok kezelése**, vagy **PDF-be exportálás**. Mindegyik az általad most gyakorolt `DocumentBuilder` alapokra épül.

Készen állsz a Word dokumentumok automatizálására? Próbáld meg kibővíteni a példát több alakzattal, színátmenetek alkalmazásával, vagy adatciklusokkal, hogy egyetlen futtatás során teljes jelentést generálj. Jó kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Alakzatok beszúrása Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Téglalap alakzat létrehozása Word-ben az Aspose.Words segítségével – lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}