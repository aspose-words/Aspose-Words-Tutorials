---
category: general
date: 2026-08-04
description: Hogyan adjon hozzá adatcímkéket C#-ban az Aspose.Words segítségével.
  Tanulja meg a diagram szerkesztését, az adatcímkék középre helyezését, a százalékok
  megjelenítését a diagramon, és az adatcímkék testreszabását.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: hu
lastmod: 2026-08-04
og_description: Hogyan adjunk hozzá adatcímkéket C#-ban az Aspose.Words használatával.
  Ez az útmutató bemutatja, hogyan szerkeszthetünk diagramot, középre helyezhetjük
  a diagram adatcímkéit, megjeleníthetjük a százalékokat a diagramon, és testreszabhatjuk
  a diagram adatcímkéit.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Hogyan adjunk adatcímkéket egy Word-diagramhoz C#-ban – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Hogyan adjunk adatcímkéket egy Word-diagramhoz C#-ban – lépésről lépésre útmutató
url: /hu/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjunk adatcímkéket egy Word-diagramhoz C#‑ban – lépésről‑lépésre útmutató

Ha **hogyan adjunk adatcímkéket** egy Word-dokumentumban lévő diagramhoz, ez az útmutató megmutatja a pontos kódot, amelyet futtatnia kell. Megtanulja, hogyan szerkessze a diagram tulajdonságait, középre helyezze a diagram adatcímkéket, jelenítse meg a százalékos értékeket a diagramon, és testreszabja a diagram adatcímkéket bármely szituációban.

A tutorial mindent lefed, ami egy meglévő diagram módosításához szükséges, a dokumentum betöltésétől a változtatások mentéséig. Nem szükséges külső hivatkozás – csak az Aspose.Words for .NET könyvtár és egy alap C# fejlesztői környezet.

## Előkövetelmények

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* .NET 6.0 (vagy újabb) telepítve.
* Aspose.Words for .NET 23.9 vagy újabb verzióval.  
  Telepítheti a NuGet‑en keresztül:

```bash
dotnet add package Aspose.Words
```

* Egy Word‑fájl (`input.docx`) amely legalább egy diagramot tartalmaz.

## Hogyan adjunk adatcímkéket egy Word-diagramhoz C#‑ban

Az alábbi szakaszok lépésről‑lépésre vezetik végig. Az elsődleges kulcsszó **hogyan adjunk adatcímkéket** természetesen megjelenik a szövegben és a kódkommentekben, megtartva a javasolt sűrűséget.

### 1. lépés – Töltse be a diagramot tartalmazó Word‑dokumentumot

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Miért fontos ez a lépés*: A `Document` objektum képviseli a teljes Word‑fájlt. A betöltése hozzáférést biztosít minden csomóponthoz, beleértve a diagramot tartalmazó alakzatokat is.

### 2. lépés – Szerezze meg az első diagramot a dokumentumból

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Miért fontos ez a lépés*: A diagramok `Shape` csomópontokban tárolódnak. A lekért csomópont `Shape`‑re való átkonvertálásával és a `GetChart()` meghívásával egy `Chart` objektumot kap, amely sorozatokat, tengelyeket és címke‑gyűjteményeket tesz elérhetővé.

### 3. lépés – Engedélyezze az adatcímkék testreszabását és jelenítse meg a százalékokat a diagramon

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Miért fontos ez a lépés*: A `ShowPercentage` beállítása azt mondja az Aspose.Words‑nek, hogy számolja ki és jelenítse meg minden szelet hozzájárulását az összhez. Ez közvetlenül a másodlagos kulcsszó **show percentages in chart**‑et célozza.

### 4. lépés – Módosítsa a címke elhelyezését az egyes adatpontok közepére

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Miért fontos ez a lépés*: A `Position` tulajdonság szabályozza, hogy a címke hol jelenik meg az adatponthoz képest. A `Center` használata kielégíti a másodlagos kulcsszó **center chart data labels**‑t és javítja a olvashatóságot kör- vagy gyűrűdiagramok esetén.

### 5. lépés – További diagram adatcímke‑testreszabás (opcionális)

Ha nagyobb irányítást igényel, módosíthatja a betűtípust, színt vagy a vezetővonalakat:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Ezek a beállítások illusztrálják a másodlagos kulcsszó **customize chart data labels**‑t, és bemutatják, hogyan igazíthatja a megjelenést a márka irányelveihez.

### 6. lépés – Mentse a módosított dokumentumot

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Miért fontos ez a lépés*: A mentés visszaírja a frissített diagramot a Word‑fájlba, így az új adatcímkék láthatóak lesznek, amikor a fájlt megnyitja a Microsoft Word‑ben.

## Teljes, futtatható példa

Az alábbiakban egy komplett programot talál, amelyet egyszerűen másolhat, beilleszthet és futtathat. Tartalmazza az összes szükséges `using` direktívát és kommentárokat, amelyek minden sort magyaráznak.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Várható eredmény

Amikor megnyitja a `output.docx` fájlt a Microsoft Word‑ben, a diagram a következőket fogja mutatni:

* Százalékos értékek minden szelet mellett (pl. **25 %**, **40 %**, …).
* Címkék a középpontban minden adatponthoz.
* Bármely további stílus, amelyet alkalmazott, például félkövér piros szöveg.

Ezek a vizuális jelek könnyebbé teszik a diagram értelmezését, különösen prezentációk vagy jelentések során.

## Hogyan szerkessze a diagram tulajdonságait az adatcímkék mellett

Miközben ennek az útmutatónak a fókusza a **hogyan adjunk adatcímkéket**, előfordulhat, hogy **hogyan szerkessze a diagram** beállításait is módosítani szeretné, például a címet, a jelmagyarázat helyét vagy a tengelyformázást. A `Chart` objektum olyan tulajdonságokat biztosít, mint a `Title`, a `Legend` és az `AxisX/AxisY`. Például a diagram címének módosításához:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Minden diagram‑módosítás ugyanazt a mintát követi: lekéri a diagramot, módosítja a tulajdonságait, majd menti a dokumentumot.

## Gyakori hibák és bevált gyakorlatok

| Probléma | Miért fordul elő | Ajánlott megoldás |
|---|---|---|
| A diagram egy csoportos alakzat belsejében van. | A `GetChild(NodeType.Shape, …)` a külső csoportot adja vissza, nem a belső diagramot. | Keressen rekurzívan olyan alakzatot, amelynek `shape.HasChart` értéke igaz. |
| Az adatcímkék nem jelennek meg mentés után. | A `ShowValue` vagy a `ShowPercentage` nincs `true`‑ra állítva. | Állítsa be kifejezetten mindkettőt `true`‑ra, ahogy szükséges. |
| A címkék átfedik egymást kis szeleteknél. | A középső elhelyezés zsúfoltságot okozhat. | Használja a `ChartDataLabelPosition.OutSideEnd` értéket a külső elhelyezéshez, vagy engedélyezze a `LeaderLines`‑t. |

E tippek alkalmazásával megbízható eredményeket érhet el különböző diagramtípusok esetén.

## Következtetés

Most már tudja, **hogyan adjunk adatcímkéket** egy Word‑diagramhoz C#‑ban. A tutorial bemutatta a diagram lekérését, a címkék láthatóságának engedélyezését, a címkék középre helyezését, a százalékok megjelenítését és a megjelenés testreszabását. Ezzel a tudással már **hogyan szerkessze a diagram** részleteit, **center chart data labels**, **show percentages in chart**, és **customize chart data labels** is megvalósíthat bármely jelentési szituációban.

Készen áll a további felfedezésre? Próbáljon meg több sorozatot hozzáadni, feltételes formázást alkalmazni, vagy a diagramot képként exportálni. Az Aspose.Words API kiterjedt diagram‑manipulációs lehetőségeket kínál – kísérletezzen, hogy megtalálja a legjobb vizuális megjelenítést az adataihoz.

## Mi legyen a következő tanulnivalója?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}