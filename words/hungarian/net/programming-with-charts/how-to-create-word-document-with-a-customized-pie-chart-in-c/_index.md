---
category: general
date: 2026-10-07
description: Tanulja meg, hogyan hozhat létre Word-dokumentumot és szúrhat be kördiagramot
  az Aspose.Words C# használatával. Az útmutató azt is bemutatja, hogyan generálhat
  Word-fájlt egyedi diagramcímkékkel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: hu
lastmod: 2026-10-07
og_description: Hozzon létre Word-dokumentumot, és szúrjon be kördiagramot C#-ban.
  Kövesse ezt a lépésről‑lépésre útmutatót, hogy teljesen testreszabott diagramcímkékkel
  rendelkező Word-fájlt generáljon.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Word-dokumentum létrehozása testreszabott kördiagrammal C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Hogyan hozzunk létre Word-dokumentumot egy testreszabott kördiagrammal C#-ban
url: /hu/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre Word dokumentumot egy testreszabott kördiagrammal C#-ban

Ha programozott módon kell **word dokumentumot létrehozni**, ez a bemutató megmutatja, hogyan **kördiagramot szúrj be** és testreszabhatod az adatcímkéket az Aspose.Words for .NET használatával. Emellett megtanulod, hogyan **generálj word fájlt**, amely teljesen formázott diagramot tartalmaz, a projekt beállításától a végső dokumentum mentéséig.

Az útmutató végigvezeti a diagram hozzáadásához, a címke pozíciók beállításához, a vezetővonalak engedélyezéséhez szükséges lépéseken, és végül a mentést `.docx` fájlként. Az Aspose.Words könyvtáron kívül nincs szükség külső eszközökre, a teljes forráskód is meg van adva, így azonnal másolhatod, beillesztheted és futtathatod.

## Előkövetelmények

* .NET 6.0 SDK vagy újabb telepítve  
* Érvényes Aspose.Words for .NET licenc (vagy ingyenes értékelő kulcs)  
* Egy IDE, például Visual Studio 2022 vagy Visual Studio Code  

A projektedhez a következő NuGet csomagokat is hozzá kell adnod:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Ezek a csomagok biztosítják a `Document`, `DocumentBuilder` és a diagramokhoz kapcsolódó osztályokat, amelyeket az alábbi példákban használunk.

## Word dokumentum létrehozása és diagram hozzáadása

Az első lépés a **word dokumentum** létrehozása és egy `DocumentBuilder` beszerzése, amely lehetővé teszi a tartalom beszúrását. A builder úgy működik, mint egy kurzor, amely a dokumentum belsejében helyezkedik el.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

A `Document` objektum a teljes Word fájlt képviseli, míg a `DocumentBuilder` olyan metódusokat biztosít, mint a `InsertChart`, amelyek közvetlenül a dokumentum folyamatába helyeznek objektumokat.

## Kördiagram beszúrása a dokumentumba

Miután a builder készen áll, **kördiagramot szúrhatsz be** egy meghatározott mérettel. A diagram a builder aktuális pozíciójában kerül hozzáadásra.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

Az `InsertChart` egy `Chart` objektumot ad vissza, amelyet tovább lehet manipulálni. A mintaadat négy szeletet hoz létre, amelyek a negyedéves eladásokat ábrázolják.

## A kördiagram adatcímkéinek testreszabása

A diagram olvashatóságának javítása érdekében gyakran szükség van a **kördiagram** címkéinek **testreszabására** – a szeletek kívülre helyezésére és a vezetővonalak megjelenítésére. Itt jön képbe a `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

A `Position` `OutsideEnd` értékre állítása minden címkét a szelet szélén túlra helyez, míg a `ShowLeaderLines` egy vonalat rajzol, amely összeköti a címkét a szelettel. A opcionális `ShowValue` és `ShowPercentage` jelzők a felhasználóknak nyers számokat és relatív százalékokat is megjelenítenek.

**Pro tipp:** Ha a címke betűtípusát szeretnéd formázni, használd a `dataLabels.Font`-ot a méret, szín és stílus beállításához. Ez biztosítja, hogy a diagram megfeleljen a vállalati arculatnak.

## Word fájl mentése és generálása

Miután a diagram teljesen be van állítva, **generálhatsz word fájlt** a `Document` példány lemezre mentésével. Válaszd a `.docx` formátumot a modern Word verziókkal való legnagyobb kompatibilitás érdekében.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Amikor megnyitod a `CustomPieChart.docx` fájlt, egy négy szeletből álló kördiagramot látsz, ahol minden szelet címkéje a szelet kívül van, vezetővonalakkal összekötve, és mind az értéket, mind a százalékot megjelenítve.

![Képernyőkép egy Word dokumentumról, amely testreszabott kördiagramot tartalmaz, C#-ban létrehozva](image-placeholder.png)

*A kép a **word dokumentum létrehozása** bemutató végső eredményét mutatja.*

## Gyakori variációk és szélhelyzetek

| Forgatókönyv | Hogyan kell módosítani a kódot |
|--------------|--------------------------------|
| **Több sorozat** | Adj hozzá további `ChartSeries` objektumokat a `pieChart.Series`-hez. Minden sorozat rendelkezhet saját `DataLabels` gyűjteménnyel az önálló stílushoz. |
| **Eltérő diagramméret** | Módosítsd a szélesség és magasság paramétereket az `InsertChart(width, height)` hívásban. Az értékek pontban vannak megadva (1 pt ≈ 1/72 hüvelyk). |
| **Diagramcím** | Használd a `pieChart.Title.Text = "Quarterly Sales"` kifejezést egy leíró cím hozzáadásához. |
| **Exportálás PDF-be** | Hívd meg a `document.Save("Report.pdf", SaveFormat.Pdf);` metódust a diagram elkészülte után. |
| **Licenckezelés** | Helyezd a licencfájlt (`Aspose.Words.lic`) az alkalmazás mappájába, és töltsd be a `new License().SetLicense("Aspose.Words.lic");` hívással a dokumentum létrehozása előtt. |

Ezek a variációk lehetővé teszik, hogy megválaszold a **hogyan adjunk hozzá kördiagramot** kérdést számos valós helyzetben, az egyszerű jelentésektől a komplex műszerfalakig.

## Összegzés

Most már tudod, hogyan **hozz létre word dokumentumot**, **szúrj be kördiagramot**, és **testreszabd a kördiagram** címkéit az Aspose.Words for .NET használatával. A teljes példa egy tiszta munkafolyamatot mutat be: a dokumentum inicializálása, diagram hozzáadása, adatcímke pozíciójának beállítása, vezetővonalak engedélyezése, és végül **word fájl generálása**, amely megosztható bárkivel.

Próbáld kibővíteni ezt a bemutatót különböző diagramtípusok (`ChartType.Column`, `ChartType.Line`) kipróbálásával, vagy egyedi színpaletták alkalmazásával, hogy megfeleljenek a márkádnak. Ha problémába ütközöl, tekintsd meg az Aspose.Words dokumentációt, vagy vizsgáld meg a kapcsolódó témákat, például a “hogyan adjunk hozzá kördiagramot” több sorozattal és dinamikus adatforrásokkal.

Boldog kódolást, és nyugodtan oszd meg az eredményeidet vagy tegyél fel további kérdéseket a megjegyzésekben!

## Mit érdemes legközelebb megtanulni?

A következő bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}