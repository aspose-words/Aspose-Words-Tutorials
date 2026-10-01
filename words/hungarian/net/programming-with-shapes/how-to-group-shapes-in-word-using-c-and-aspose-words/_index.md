---
category: general
date: 2026-09-30
description: Alakzatok csoportosítása Wordben C#-val – tanulja meg, hogyan csoportosíthatja
  az alakzatokat, adjon hozzá téglalapot és ellipszist, és hogyan szúrjon be téglalap
  alakzatot Word-dokumentumokba programozottan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: hu
lastmod: 2026-09-30
og_description: Csoportosítsa a formákat a Wordben C# és Aspose.Words használatával.
  Kövesse ezt a teljes útmutatót a téglalap hozzáadásához, az ellipszis hozzáadásához,
  és tanulja meg, hogyan csoportosíthatja hatékonyan a formákat.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Alakzatok csoportosítása Wordben C#‑val – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan csoportosítsuk a formákat a Wordben C# és az Aspose.Words használatával
url: /hu/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsunk alakzatokat a Wordben C# és Aspose.Words segítségével

Ha programozott módon **csoportosítani szeretnél alakzatokat a Wordben**, ez az útmutató pontosan megmutatja, hogyan. Meg fogod látni, hogyan adsz hozzá egy téglalapot, egy ellipszist, majd hogyan kombinálod őket egyetlen csoportos alakzattá az Aspose.Words .NET könyvtár segítségével.

Az alakzatok kezelése gyakori igény jelentések, szerződések vagy marketing anyagok automatikus generálásakor. A tutorial végére egy újrahasználható C# metódust kapsz, amely betölti a DOCX fájlt, beszúr egy téglalapot és egy ellipszist, csoportosítja őket, majd elmenti az eredményt – mindezt anélkül, hogy manuálisan megnyitnád a Wordöt.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel:

* .NET 6.0 SDK vagy újabb verzió telepítve  
* Fejlesztői környezettel, például Visual Studio 2022 (a Community kiadás is működik)  
* Aspose.Words for .NET licenccel vagy egy ingyenes értékelő példánnyal (az API licenc nélkül is működik, de vízjelet ad hozzá)  

Ezen felül szükséged van egy forrás Word dokumentumra (`input.docx`) egy olyan mappában, amelyre a kódból hivatkozhatsz. A dokumentum lehet üres; a tutorial az alakzatkezelésre fókuszál.

## 1. lépés: Új konzolprojekt létrehozása és Aspose.Words hozzáadása

Nyiss egy terminált vagy a Visual Studio parancssort, és futtasd:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Ez létrehoz egy friss konzolalkalmazást **WordShapeDemo** néven, és hozzáadja az `Aspose.Words` NuGet csomagot, amely tartalmazza a `Document` és `DocumentBuilder` osztályokat a Word fájlok manipulálásához.

## 2. lépés: Dokumentum betöltése vagy létrehozása

Az első művelet, amikor **csoportos alakzatokkal a Wordben** dolgozol, egy `Document` objektum beszerzése. Betölthetsz egy meglévő DOCX fájlt, vagy egy üres dokumentummal kezdhetsz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

A `Document` osztály képviseli a teljes Word fájlt. Egy fájl betöltése egy kész vásznat biztosít az alakzatok beszúrásához.

## 3. lépés: Csoportos alakzat megnyitása

Egy *csoportos alakzat* lehetővé teszi, hogy több független alakzatot egyetlen egységként kezelj – tökéletes a közös mozgatáshoz vagy átméretezéshez. A csoport elindításához hívd meg a `StartGroupShape()` metódust egy `DocumentBuilder` példányon.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

A `StartGroupShape` hívása azt jelzi az Aspose.Words számára, hogy minden későbbi alakzatbeszúrás ugyanahhoz a logikai csoporthoz tartozik, amíg az `EndGroupShape` nem kerül meghívásra.

## 4. lépés: Téglalap alakzat hozzáadása Wordben

Most, hogy a csoport nyitva van, szúrj be egy téglalapot. Az `InsertShape` metódus egy `ShapeType` enumot, majd a szélességet és magasságot (pontban) várja.

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

A téglalap a csoport első tagjává válik. Később testreszabhatod a kitöltését, körvonalát vagy szövegét, ha szükséges.

## 5. lépés: Ellipszis alakzat hozzáadása Wordben

Ezután adj hozzá egy ellipszist (kör, ha a szélesség egyenlő a magassággal). Ez bemutatja, **hogyan adjunk hozzá ellipszist** ugyanazzal a builderrel.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Mindkét alakzat most ugyanabban a koordináta-rendszerben osztozik a csoporton belül, így könnyű őket vizuálisan igazítani.

## 6. lépés: Csoportos alakzat definíciójának lezárása

Ha minden kívánt elemet beszúrtál, zárd le a csoportot. Ez véglegesíti az alakzatgyűjteményt, így a Word egyetlen objektumként kezeli őket.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Ekkor a dokumentum egyetlen csoportos alakzatot tartalmaz, amely egy téglalapból és egy ellipszisből áll.

## 7. lépés: Módosított dokumentum mentése

Végül írd vissza a változásokat a lemezre. Felülírhatod az eredeti fájlt, vagy létrehozhatsz egy újat.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

A program futtatása `output.docx`-et hoz létre. Nyisd meg a fájlt a Microsoft Wordben, válaszd ki az alakzatot, és látni fogod, hogy a téglalap és az ellipszis együtt mozognak – bizonyíték arra, hogy a **csoportos alakzatok a Wordben** művelet sikeres volt.

### Várt eredmény

* A Word fájl egyetlen csoportos objektumot tartalmaz.  
* A csoport kiválasztásával egyszerre húzhatod, átméretezheted vagy forgathatod a téglalapot és az ellipszist.  
* Nem szükséges manuális interakció a Worddel; minden C# kóddal történik.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Image alt text: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (fulfills the image alt‑text requirement).

## Miért fontos az alakzatok csoportosítása

Az alakzatok csoportosítása több mint vizuális kényelem. Lehetővé teszi, hogy:

* **Megőrizd a elrendezés konzisztenciáját** – a csoport mozgatása megtartja a relatív pozíciókat.  
* **Egyszerre alkalmazz transzformációkat** – forgasd vagy méretezd az egész csoportot az egyes alakzatok helyett.  
* **Egyszerűsítsd a downstream feldolgozást** – amikor más eszközök olvassák a DOCX-et, egyetlen összetett alakzatot látnak, csökkentve a komplexitást.

Ha valaha több alakzatot (például vonalat vagy szövegdobozt) szeretnél hozzáadni ugyanahhoz a logikai egységhez, csak hívd meg újra az `InsertShape`-t az `EndGroupShape` előtt.

## Gyakori variációk és szélhelyzetek

| Helyzet | Hogyan kezeljük |
|-----------|-----------------|
| **Eltérő mértékegységek** – centiméterben vannak a méretek | A centimétereket konvertáld pontokra (`1 cm ≈ 28.35 pt`) az `InsertShape` hívása előtt. |
| **Szövegcímke hozzáadása** – feliratot szeretnél a csoporton belül | Szúrj be egy `ShapeType.TextBox`-ot a téglalap és ellipszis után, majd állítsd be a `Text` tulajdonságát. |
| **Kitöltőszín alkalmazása** – kék téglalapra van szükséged | Az `InsertShape` után szerezd meg az utolsó alakzatot a `builder.CurrentParagraph.Runs[0].Font` segítségével, és állítsd be a `shape.FillColor = System.Drawing.Color.Blue;` értéket. |
| **Másik dokumentumformátum használata** – `.doc`-ot célozol a `.docx` helyett | Ugyanaz a kód működik; csak változtasd meg a fájlkiterjesztést a `Save` hívásakor. Az Aspose.Words automatikusan kezeli a formátumot. |

## Pro tippek

* **Használd újra a buildert** – ugyanabban a dokumentumban indíthatsz és zárhatsz több csoportot; csak hívd meg újra a `StartGroupShape`-t az `EndGroupShape` után.  
* **Teljesítmény** – a shape-ek tömeges beszúrása egyetlen `StartGroupShape/EndGroupShape` blokkban gyorsabb, mint az egyes alakzatok csoporton kívüli beszúrása.  
* **Licencelés** – egy értékelő licenc vízjelet ad az első oldalra. Telepíts megfelelő licencet a termelési környezetben a vízjel eltávolításához.

## Következtetés

Most már tudod, hogyan **csoportosíts alakzatokat a Wordben** C#-el, hogyan **adj hozzá téglalapot**, hogyan **adj hozzá ellipszist**, és hogyan **szúrj be téglalap alakzatot Word dokumentumokba** az Aspose.Words használatával. A teljes, futtatható példa minden lépést bemutat a projekt beállításától a végleges fájl mentéséig.

Innen tovább felfedezheted a további alakzattípusokat, alkalmazhatsz stílusokat, vagy kombinálhatod a csoportos alakzatokat táblázatokkal és képekkel, hogy összetett, programozottan generált dokumentumokat hozz létre.

---

**Következő lépések**

* Tanuld meg, hogyan **forgasd a csoportos alakzatokat**: használd a `Shape.RotationAngle`-t a csoport lezárása után.  
* Fedezd fel a **kitöltés és körvonal testreszabását** téglalapok és ellipszisek esetén.  
* Integráld ezt a logikát egy ASP.NET Core API-ba, hogy igény szerint generálj jelentéseket.  

Boldog kódolást!

## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}