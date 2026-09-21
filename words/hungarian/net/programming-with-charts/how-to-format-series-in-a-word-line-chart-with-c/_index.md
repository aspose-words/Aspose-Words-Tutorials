---
category: general
date: 2026-09-21
description: Hogyan formázzuk a sorozatokat egy Word vonaldiagrammban C#-val. Tanulja
  meg, hogyan hozzon létre Word dokumentumot, szúrjon be egy vonaldiagramot, és alkalmazzon
  egy egyéni számformátumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: hu
lastmod: 2026-09-21
og_description: Hogyan formázzuk a sorozatokat egy Word vonaldiagramon C#-ban. Ez
  az útmutató megmutatja, hogyan hozzunk létre egy Word dokumentumot, szúrjunk be
  egy vonaldiagramot, és alkalmazzunk egy egyéni számformátumot.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Hogyan formázzuk a sorozatokat egy Word vonaldiagramon C#-val – lépésről
  lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Hogyan formázzuk a sorozatokat egy Word vonaldiagramban C#‑val
url: /hu/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan formázzuk a sorozatokat egy Word vonaldiagrammban C#-al

Ha **hogyan formázzuk a sorozatokat** egy Word vonaldiagrammban, ez az útmutató egy teljes, azonnal futtatható megoldást nyújt. Megmutatjuk, hogyan **hozzunk létre egy Word dokumentumot**, **szúrjunk be vonaldiagramot**, és **alkalmazzunk egyedi számformátumot** az Y‑értékekre – mindezt az Aspose.Words for .NET segítségével.

A Word automatizálás egyszerűvé válik, ha megérted a diagram objektummodelljét. A tutorial végére egy Word fájlt kapsz, amely egy vonaldiagramot tartalmaz, és amelynek adat sorozatai százalékos formában, két tizedesjeggyel jelennek meg.

## Mit fogsz elérni

* Generálj egy üres `.docx` fájlt programozott módon.  
* Adj hozzá egy 400 × 300 pont méretű vonaldiagramot.  
* Érj el a diagram első adat sorozatát.  
* Alkalmazd a `#,##0.00%` formátumkódot, hogy az Y‑értékek százalékos formában jelenjenek meg.  

Külső eszközök nem szükségesek az Aspose.Words NuGet csomagon kívül.

## Előfeltételek

* .NET 6.0 SDK vagy újabb.  
* Visual Studio 2022 (vagy bármely C# IDE).  
* Aspose.Words for .NET 23.10 vagy újabb – telepítés: `dotnet add package Aspose.Words`.  

A kód Windows, Linux és macOS rendszereken is működik, mivel az Aspose.Words platformfüggetlen.

## Word dokumentum létrehozása Aspose.Words segítségével

Az első lépés egy `Document` objektum példányosítása. Ez az objektum a teljes Word fájlt reprezentálja a memóriában.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Miért fontos*: A `Document` a belépési pont minden Word‑feldolgozási művelethez. Nélküle nem tudsz bekezdéseket, táblázatokat vagy diagramokat hozzáadni.

## Vonaldiagram beszúrása a dokumentumba

A `DocumentBuilder` tartalmat ír a `Document`‑be. Az `InsertChart` hívása egy diagram alakzatot hoz létre az aktuális oldalon.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Miért fontos*: `InsertChart` egy `Chart` objektumot ad vissza, amely teljes kontrollt biztosít a sorozatok, tengelyek és formázás felett. A méretparaméterek pontban vannak megadva (1 pont = 1/72 hüvelyk).

## Az első adat sorozat elérése

Minden diagram egy vagy több `ChartSeries`‑t tartalmaz. Az első sorozat indexe 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Miért fontos*: A `ChartSeries` objektum tárolja az Y‑értékeket, X‑értékeket és a formázási beállításokat egy vonaldiagram egy vonalához. Ennek módosítása megváltoztatja az adat vizuális megjelenését.

## Egyedi számformátum alkalmazása a sorozatra

A `FormatCode` tulajdonság szabályozza, hogyan jelennek meg a numerikus értékek. Ha `#,##0.00%`‑re állítod, a Word a értékeket két tizedesjegyű százalékokként kezeli.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Miért fontos*: Egyedi formátum nélkül a Word nyers tizedes számokat mutat (pl. `0.15`). A formátumkód átalakítja őket `15.00%`‑ra, ami gyakran szükséges az üzleti jelentésekben.

## Dokumentum mentése és az eredmény ellenőrzése

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Amikor megnyitod a `FormattedSeriesLineChart.docx` fájlt a Microsoft Wordben, egy vonaldiagramot látsz, ahol az Y‑tengely címkéi `15.00%`, `30.00%`, `45.00%` és `60.00%` értékeket mutatják. A diagram mérete megegyezik az `InsertChart`‑ben megadott méretekkel.

### Várt kimenet képernyőképe

> *Kép: Egy Word dokumentum oldal, amely egy vonaldiagramot mutat százalékos formátumú Y‑tengely értékekkel.*  
> *(Alt szöveg: Képernyőkép egy Word dokumentumról, amely egy vonaldiagramot mutat százalékos formátumú Y‑tengely értékekkel)*

## Gyakori variációk és szélső esetek

| Situation | Adjustment |
|-----------|------------|
| **Több sorozat** | Iterálj a `chart.Series` elemein, és állítsd be a `FormatCode`‑t minden sorozatra. |
| **Különböző diagramtípus** | Cseréld le a `ChartType.Line`-t `ChartType.Column`, `ChartType.Pie` stb. értékekre. |
| **Helyspecifikus elválasztók** | Használj `CultureInfo`‑t figyelembe vevő formátum karakterláncokat, például `"# ##0,00 %"` francia helyi beállításokhoz. |
| **Dinamikus adatforrás** | Töltsd fel a `series.YValues`‑t egy adatbázisból vagy CSV fájlból a formátum alkalmazása előtt. |

**Pro tipp:** Mindig a **Y‑értékek** hozzáadása után alkalmazd a formátumot. A formátum előbb történő beállítása, majd az értékek hozzáadása is működik, de későbbi alkalmazása garantálja, hogy a formátum a végső adathalmazra kerüljön.

## Összefoglalás

Most már tudod, **hogyan formázzuk a sorozatokat** egy Word vonaldiagrammban C# használatával. A tutorial a következőket fedte le:

* Word dokumentum létrehozása (`create word document`).  
* Vonaldiagram beszúrása (`insert line chart`, `add chart to word`).  
* A diagram első sorozatának elérése.  
* Egyedi számformátum alkalmazása (`apply custom number format`) a százalékos megjelenítéshez.

## Következő lépések

* Kísérletezz különböző `ChartType` értékekkel, hogy lásd, hogyan viselkednek a többi vizualizáció.  
* Adj hozzá címeket, tengelycímkéket és jelmagyarázatot a `chart.Title`, `chart.AxisX.Title` és `chart.AxisY.Title` használatával.  
* Exportáld a diagramot képként (`chart.Save` a `SaveFormat.Png`‑el) webes jelentésekhez.  

Nyugodtan alkalmazd ezt a mintát irányítópultok, pénzügyi jelentések vagy bármely, programozott diagramot igénylő dokumentum generálásához. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Vonaldiagram létrehozása Wordben az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Oszlopdiagram beszúrása Word dokumentumba](/words/english/net/programming-with-charts/insert-column-chart/)
- [Területdiagram beszúrása Word dokumentumba | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}