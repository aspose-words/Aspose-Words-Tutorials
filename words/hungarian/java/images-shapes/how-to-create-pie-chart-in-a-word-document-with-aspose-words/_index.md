---
category: general
date: 2026-10-20
description: Kördiagram létrehozása Word-dokumentumban az Aspose.Words segítségével
  – lépésről‑lépésre útmutató, amely bemutatja, hogyan állítsuk be a színt, emeljük
  ki a szeletet, és mentsük el a Word-dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: hu
lastmod: 2026-10-20
og_description: Készítsen kördiagramot egy Word-dokumentumban az Aspose.Words segítségével.
  Tanulja meg, hogyan állíthat be színt, hogyan robbantson ki egy szeletet, és hogyan
  mentheti a Word-dokumentumot egyetlen, futtatható példában.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Kördiagram létrehozása egy Word dokumentumban – teljes C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Hogyan készítsünk kördiagramot egy Word-dokumentumban az Aspose.Words segítségével
url: /hu/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan készíts kördiagramot egy Word dokumentumban az Aspose.Words segítségével

Ha **kördiagramot** kell létrehoznod egy Word fájlban, ez az útmutató pontosan megmutatja, hogyan teheted meg. Megtanulod, hogyan állíts be egy egyéni színt, hogyan robbants ki egy szeletet a hangsúlyozáshoz, és végül hogyan **mentsd el a Word dokumentumot** a beágyazott diagrammal.

A diagramok programozott generálása megszünteti a Word megnyitásával, diagram beszúrásával és megjelenésének finomhangolásával járó manuális lépéseket. A tutorial végére egy teljes, futtatható C# konzolalkalmazásod lesz, amely létrehozza a kördiagramot, testreszabja, és a eredményt lemezre írja.

## Előfeltételek

* .NET 6.0 SDK vagy újabb telepítve  
* Érvényes Aspose.Words for .NET licenc (vagy ingyenes értékelő kulcs)  
* Egy IDE, például Visual Studio 2022 vagy VS Code  

A `Aspose.Words`-on kívül nincs szükség további NuGet csomagokra.

## Hogyan készíts kördiagramot egy Word dokumentumban

Az első lépés egy `Document` és egy `DocumentBuilder` példányosítása. A builder hozzáférést biztosít a magas szintű Word funkciókhoz, beleértve a diagram beszúrását.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Ekkor a dokumentum már tartalmaz egy alap kördiagramot. A következő szakaszok bemutatják, hogyan **robban ki egy szeletet**, hogyan **állíts be színt**, és hogyan **mentsd el a Word dokumentumot**.

## Hogyan robbants ki egy szeletet a hangsúlyozáshoz

Egy szelet kirobbanása elválasztja azt a kör többi részétől, így a szem a kívánt területre irányul. Az Aspose.Words API lehetővé teszi, hogy pontokban határozd meg a robbanás távolságát.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Miért robbantsuk ki a szeletet? Az olyan jelentésekben, amelyek egy adott kategóriát emelnek ki – például a „Legjobban eladott termék” – a vizuális elkülönítés az adatpontot azonnal felismerhetővé teszi.

## Hogyan állíts be színt egy diagram szeletén

Az egyéni színek javítják a márka konzisztenciáját és az olvashatóságot. Bármely `System.Drawing.Color` értéket hozzárendelhetsz egy adott adatponthoz.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Nem vagy korlátozva az előre definiált színekre; létrehozhatsz egy `Color.FromArgb` értéket a pontos árnyalatokhoz.

## Hogyan mentsük el a Word dokumentumot a diagrammal

Miután a diagram úgy néz ki, ahogy szeretnéd, a fájl mentése egyszerű. A `Document.Save` metódus a megadott formátumban írja a dokumentumot – itt az alapértelmezett `.docx`-et használjuk.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

A program futtatása létrehozza a `PieChart.docx` fájlt. A Microsoft Word-ben megnyitva egy kördiagramot látsz, ahol az első szelet ki van robbantva és piros színű, pontosan úgy, ahogy a kód meghatározza.

### Várt eredmény

* A **PieChart.docx** nevű Word fájl a `C:\Temp` könyvtárban.  
* A dokumentum egyetlen kördiagramot tartalmaz, mérete 400 × 300 pont.  
* A 0‑s szelet 20 ponttal van eltolva és piros színű, míg a többi szelet az alapértelmezett színt megtartja.  

A robbanás és a szín ellenőrzéséhez válaszd ki a diagramot a Wordben, és vizsgáld meg a szelet tulajdonságait.

## Pro tippek és gyakori buktatók

* **Pro tip:** Ha módosítanod kell a diagram címét vagy jelmagyarázatát, a mentés előtt használd a `pieChart.Title.Text` és `pieChart.Legend` tulajdonságokat.  
* **Watch out for:** Ha elfelejted törölni az alapértelmezett adatpontokat, felesleges, nem kívánt szeletek jelenhetnek meg. Mindig hívd meg a `Series[0].DataPoints.Clear()` metódust, mielőtt saját adatot adnál hozzá.  
* **Performance tip:** Nagy dokumentumok esetén használd újra egyetlen `DocumentBuilder` példányt a sok builder létrehozása helyett; ez csökkenti a memóriahasználatot.

## Hogyan készíts diagramot az Aspose.Words segítségével (további kontextus)

Az `InsertChart` metódus számos diagramtípust támogat a kördiagramok mellett, például oszlop-, vonal- és területdiagramokat. Más típusra váltáshoz cseréld le a `ChartType.Pie` értéket a kívánt enum értékre, pl. `ChartType.Column`. A testreszabási lépések többi része (szeletek robbantása, színek beállítása) ugyanazt a mintát követi, bár nem minden diagramtípus rendelkezik „robbanás” tulajdonsággal.

## Hogyan robbantsuk ki a szeletet más diagramtípusokban

Csak a kördiagramok teszik elérhetővé a `SetExplosion` metódust. Ha oszlopdiagramon próbálod meghívni, az API `ArgumentException`-t dob. Ilyen esetekben fontold meg adatcímkék vagy felhívások használatát egy adott oszlop kiemeléséhez.

## Hogyan állíts be színt egy sorozatra egyetlen szelet helyett

Ha azt szeretnéd, hogy egy sorozat minden szelete ugyanazt a színt kapja, iterálj a adatpontokon:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Ez a megközelítés hasznos, ha több diagramon egységes színsémát szeretnél.

## Hogyan mentsük el a Word dokumentumot más formátumokban

Az Aspose.Words exportálhat PDF, HTML és számos más formátumba. A `Save` metódusban módosítsd a fájl kiterjesztését, és opcionálisan adj át egy `SaveOptions` objektumot:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

A diagram renderelő motor automatikusan átalakítja a diagramot a célformátumba, megőrizve a színeket és a robbanás beállításait.

## Összegzés

Most már tudod, hogyan **készíts kördiagramot** egy Word dokumentumban, hogyan testreszabhatod megjelenését **szelet robbantásával** és **szín beállításával**, és végül hogyan **mentsd el a Word dokumentumot** a beágyazott diagrammal. Ez az átfogó példa szilárd alapot nyújt a jelentéskészítés, műszerfalak vagy bármely olyan helyzet automatizálásához, ahol a vizuális adatokat programozottan kell beilleszteni.

### Következő lépések

* Fedezz fel más diagramtípusokat (`ChartType.Column`, `ChartType.Line`), hogy bővítsd a jelentéskészítő eszköztáradat.  
* Kombinálj több diagramot egyetlen dokumentumban, hogy átfogó műszerfalakat építs.  
* Kísérletezz a `ChartDataLabel` használatával, hogy a százalékokat vagy értékeket közvetlenül a szeleteken jelenítsd meg.  

Nyugodtan igazítsd a kódot a saját adatforrásaidhoz – legyen szó adatbázisról, API-ról vagy CSV-fájlról, ugyanaz a Aspose.Words munkafolyamat érvényes. Jó diagramkészítést!

## Mit érdemes következőként megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Kördiagram szelet robbantása C#-ban az Aspose.Words segítségével – Teljes útmutató](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Egyéni oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET használatával](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Diagram sorozat adatainak frissítése Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}