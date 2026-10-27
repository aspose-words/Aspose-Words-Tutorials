---
category: general
date: 2026-08-10
description: Készítsen kördiagramot tartalmazó Word-dokumentumot az Aspose.Words segítségével.
  Tanulja meg, hogyan szúrjon be diagramot, testreszabja a kördiagram színeit, és
  hogyan változtassa meg a körszelet színét C#‑ban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: hu
lastmod: 2026-08-10
og_description: Készítsen kördiagramot tartalmazó Word dokumentumot az Aspose.Words
  segítségével. Ez az útmutató bemutatja, hogyan illesszen be diagramot, testreszabja
  a kördiagram színeit, és módosítsa a körszelet színét egy C# alkalmazásban.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Kördiagram készítése Word dokumentumban – Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Kördiagram létrehozása Word dokumentumban az Aspose.Words segítségével
url: /hu/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum kördiagram létrehozása az Aspose.Words segítségével

Ha programozott módon **kördiagram Word dokumentumot** kell létrehoznod, ez a bemutató pontosan megmutatja, hogyan. Végigvezetünk a diagram beszúrásán, a **kördiagram színeinek testreszabásán**, és a **körszelet színének megváltoztatásán** az Aspose.Words for .NET használatával.

Egy teljes, futtatható példát láthatsz, amelyet átmásolhatsz a Visual Studio-ba, futtathatsz, és azonnal megnyithatod a generált *.docx* fájlt a formázott kördiagram ellenőrzéséhez. Külső dokumentációra nincs szükség – minden, amire szükséged van, ebben az útmutatóban található.

## Előfeltételek

* .NET 6.0 SDK vagy újabb telepítve  
* Érvényes Aspose.Words for .NET licenc (vagy ideiglenes értékelő kulcs)  
* Visual Studio 2022 (vagy bármely C# IDE)  

A kód csak a `Aspose.Words` és `Aspose.Words.Drawing.Charts` névtereket használja, így az Aspose.Words könyvtáron kívül nincs szükség további NuGet csomagokra.

## Word dokumentum kördiagram létrehozása – teljes példa

Az alábbi C# program új Word dokumentumot hoz létre, beszúr egy kördiagramot, formázza az első két szeletet, és elmenti a fájlt. Minden lépést részletesen magyarázunk.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Az egyes lépések magyarázata

| Lépés | Mit csinál | Miért fontos |
|------|------------|--------------|
| **1** | Létrehoz egy új `Document`-ot és egy `DocumentBuilder`-t. | A `DocumentBuilder` folyékony (fluent) metódusokat biztosít a tartalom, például diagramok, beszúrásához a Word fájlba. |
| **2** | Meghívja az `InsertChart`-et a `ChartType.Pie`-val és egy rögzített mérettel. | `InsertChart` a **diagram beszúrásának módja**; a szélesség/magasság megadása biztosítja, hogy a diagram szépen illeszkedjen az oldalra. |
| **3** | Hozzáad egy adat sorozatot három kategóriával és numerikus értékekkel. | Egy adat nélküli kördiagram láthatatlan; az adatok feltöltése bemutatja a formázási lépéseket. |
| **4** | Beállítja az `Explosion`-t az első ponton. | Egy szelet kiemelése felhívja a figyelmet egy adott szegmensre – hasznos a kulcsadatok kiemeléséhez. |
| **5** | Beállítja a `ForeColor`-t az első két pontnál. | Ez a **kördiagram színeinek testreszabása** középpontja; bármilyen `System.Drawing.Color` használható. |
| **6** | Megmutatja, hogyan **változtatható a körszelet színe** további szeletek esetén. | Bemutatja, hogy a formázás nem korlátozódik csak az első két szeletre; minden szeletet egyénileg színezhetsz. |
| **7** | Elmenti a dokumentumot `PieChartStyled.docx` néven. | A végső kimenet megnyitható a Microsoft Word, a Google Docs vagy bármely kompatibilis megjelenítő programban. |

#### Várható kimenet

A `PieChartStyled.docx` megnyitása egyetlen oldalt jelenít meg egy 400 × 300 pt kördiagrammal:

* 1. szelet (narancssárga) ki van emelve kifelé.  
* 2. szelet (zöld) a kiemelt szelet mellett jelenik meg.  
* 3. szelet (acélkék) kitölti a maradék szegmenst.

A diagram a (30, 45, 25) adatértékeket és a megadott egyedi színeket tükrözi.

## Hogyan formázzuk a kördiagramot – további tippek

* **Használj témaszíneket** – a `Color.Orange` kemény kódolása helyett a dokumentum témájából is lekérheted a színeket:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Adj hozzá adatcímkéket** – ha a diagramon százalékok megjelenítését szeretnéd:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Méretezés dinamikusan** – számold ki a diagram méretét az oldal margóinak alapján:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Ezek a változatok bemutatják a **kördiagram formázásának** rugalmasságát az alap példán túl.

## Gyakran feltett kérdések megválaszolva

**K: Működik ez .NET Core-val?**  
V: Igen. Az Aspose.Words for .NET kompatibilis a .NET Core, .NET 5, .NET 6 és későbbi verziókkal. Csak hivatkozz ugyanarra a NuGet csomagra.

**K: Mi van, ha egy gyűrűdiagramra van szükségem a kördiagram helyett?**  
V: Cseréld le a `ChartType.Pie`-t `ChartType.Doughnut`-ra. Ugyanazok a formázási API-k (`Explosion`, `ForeColor`) alkalmazhatók.

**K: Beszúrhatom a diagramot egy meglévő dokumentumba?**  
V: Nyisd meg a meglévő fájlt a `new Document("Existing.docx")`-vel, hozz létre egy `DocumentBuilder`-t ehhez a dokumentumhoz, és hívd meg az `InsertChart`-et a kívánt kurzorpozíción.

**K: Hogyan kezeljem a nagy adathalmazokat?**  
V: A kördiagramok leginkább korlátozott számú kategóriához (általában < 10) alkalmasak. Sok kategória esetén inkább oszlop- vagy sávdiagramot érdemes használni.

## Teljes forráskód összefoglaló

Az alábbiakban a teljes program egy blokkban található, könnyű másoláshoz és beillesztéshez:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

A kód futtatása előállítja a korábban leírt formázott kördiagramot tartalmazó Word dokumentumot.

## Összegzés

Most már tudod, hogyan **hozz létre kördiagram Word** dokumentumokat az Aspose.Words segítségével, **testreszabhatod a kördiagram színeit**, és **programozottan megváltoztathatod a körszelet színét**. Az útmutató bemutatta a diagram beszúrását, az adatok feltöltését, egy szelet kiemelését, egyedi színek alkalmazását és az eredmény mentését.

Innen tovább felfedezheted a kapcsolódó témákat, például a **diagram beszúrásának** módját más típusoknál, a jelmagyarázatok hozzáadását, vagy többoldalas jelentések generálását több diagrammal. Kísérletezz különböző színsémákkal és adathalmazokkal, hogy megfeleljenek a jelentési igényeidnek.

Boldog kódolást!

## Mit érdemes még megtanulnod?

Az alábbi bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat, és alternatív megvalósítási megközelítéseket fedezhess fel saját projektjeidben.

- [Oszlopdiagram beszúrása Word-be az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-column-chart/)
- [Területdiagram beszúrása Word dokumentumba | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Szórásdiagram létrehozása Word-ben az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}