---
category: general
date: 2026-09-21
description: Tanulja meg, hogyan készítsen kördiagramot, és szúrja be a diagramot
  a Wordbe az Aspose.Words használatával, adjon hozzá adatcímkéket a kördiagramhoz,
  és jelenítse meg a százalékokat a kördiagramon néhány lépésben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: hu
lastmod: 2026-09-21
og_description: Készítsen kördiagramot Wordben az Aspose.Words használatával, illessze
  be a diagramot Wordbe, adjon hozzá adatcímkéket a kördiagramhoz, és jelenítse meg
  a százalékos értékeket a kördiagramon – mindezt világos kódrészletekkel.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Kördiagram létrehozása Wordben az Aspose.Words segítségével – lépésről lépésre
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Hogyan készítsünk kördiagramot egy Word dokumentumban az Aspose.Words segítségével
url: /hu/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre kördiagramot egy Word dokumentumban az Aspose.Words segítségével

Ha programozott módon **create pie chart**-t kell létrehoznod, az Aspose.Words egyszerűvé teszi. Ebben az oktatóanyagban megmutatjuk, hogyan **insert chart into Word**, hogyan konfiguráljuk a sorozatot, **add data labels to pie chart**, és végül **show percentages on pie chart**, hogy a vizualizáció pontos értékeket közvetítsen. A végére egy teljes, futtatható példát kapsz, amelyet bármely .NET projektbe beilleszthetsz.

Ez az útmutató mindent lefed, amit tudnod kell: a szükséges NuGet csomagok, a teljes C# forrás, magyarázatok arra, hogy miért fontos minden API hívás, valamint tippek a diagram testreszabásához. Nem szükséges külső dokumentáció – csak másold, futtasd, és adaptáld.

## Előfeltételek

* .NET 6.0 SDK vagy újabb telepítve.  
* Visual Studio 2022 (vagy bármely .NET-et támogató IDE).  
* Aspose.Words for .NET licenc (az ingyenes próba a teszteléshez megfelelő).  
* Alapvető ismeretek C#-ról és a Word dokumentum struktúráiról.

Ha már rendelkezel ezekkel, közvetlenül a kódra léphetsz.

## 1. lépés: A projekt beállítása és az Aspose.Words importálása

Create a new console project and add the Aspose.Words NuGet package:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

A csomag tartalmazza az `Aspose.Words.Drawing.Charts` névteret, amely a `Chart` és `ChartSeries` osztályokat tartalmazza, amelyeket használni fogunk.

> **Pro tip:** Tartsd a licencfájlt (`Aspose.Words.lic`) a projekt gyökerében, és töltsd be indításkor, hogy elkerüld a kiértékelési vízjeleket.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## 2. lépés: Üres dokumentum és DocumentBuilder létrehozása

A `Document` a Word fájlt képviseli, míg a `DocumentBuilder` egy folyékony API-t biztosít a tartalom beszúrásához.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos:** A `DocumentBuilder` fenntartja a jelenlegi beszúrási pontot, biztosítva, hogy a diagram pontosan ott jelenjen meg, ahol a dokumentum áramlásában szeretnéd.

## 3. lépés: Kördiagram beszúrása a Word dokumentumba

Most **insert chart into Word**-t hajtunk végre. Az `InsertChart` metódus a diagram típusát, a szélességet és a magasságot (pontban) veszi át.

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Ekkor a diagram egy alapértelmezett adat sorozatot tartalmaz helyőrző értékekkel (25, 25, 25, 25). Szükség esetén később felülírhatod őket.

## 4. lépés: Az első sorozat elérése és az adatcímkék testreszabása

A kördiagram általában egy sorozattal rendelkezik. A **add data labels to pie chart** érdekében lekérjük azt, és engedélyezzük a százalékos megjelenítést.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Miért állítjuk be a `ShowPercentage`-t:** Ez a jelző azt mondja az Aspose.Words-nek, hogy számolja ki minden szelet hozzájárulását, és jelenítse meg százalékban. A `Position` tulajdonság biztosítja, hogy a címke ne fedje a szeletet, ami javítja az olvashatóságot – különösen kis szeletek esetén.

## 5. lépés: (Opcionális) Helyőrző adatok cseréje

If you want specific values, replace the default points:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

A megjelenő százalékok automatikusan igazodnak az új értékekhez.

## 6. lépés: Dokumentum mentése

Finally, write the document to disk. The extension determines the format; `.docx` creates a modern Word file.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

A program futtatása egy **PieChart.docx** nevű fájlt hoz létre a kimeneti mappában. A Microsoft Word-ben megnyitva egy kördiagramot látsz, ahol minden szelet a százalékával van felcímkézve, a szeletek kívül helyezkedik el.

### Várt kimenet

When you open the generated document, you should see:

* Egyetlen kördiagram, 400 × 300 pt méretben.  
* Négy szelet (vagy annyi pont, amennyit hozzáadtál).  
* Százalékos címkék, például “40 %”, “30 %”, stb., a szeletek kívül megjelenítve.

Ha a címkék a szeletek belsejében jelennek meg, ellenőrizd, hogy a `ChartDataLabelPosition.OutsideEnd` megfelelően lett-e beállítva.

## 7. lépés: Gyakori variációk és szélsőséges esetek

### Diagram címének hozzáadása

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Szelet színeinek módosítása

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Üres sorozat kezelése

If your data source might be empty, guard against `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exportálás PDF-be a Word helyett

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

Ugyanez a diagram renderelési logika érvényes; az Aspose.Words automatikusan a Word elrendezést PDF-be konvertálja.

## Teljes forráskód

Below is the complete, ready‑to‑run program. Copy it into `Program.cs` and execute `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Következtetés

Now you know how to **create pie chart** in a Word file using Aspose.Words, **insert chart into Word**, **add data labels to pie chart**, and **show percentages on pie chart**. The example demonstrates the full workflow—from project setup to final document—so you can adapt it for dashboards, reports, or automated invoice generation.

Next, explore related topics such as **how to display percentages in chart** legends, customizing chart colors, or converting the Word document to PDF for distribution. Experiment with different chart types (Bar, Line) using the same `InsertChart` method to broaden your automation capabilities.

Boldog diagramkészítést!

## Mit érdemes legközelebb megtanulni?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}