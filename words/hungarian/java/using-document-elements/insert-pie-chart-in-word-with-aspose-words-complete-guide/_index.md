---
category: general
date: 2026-07-26
description: Kördiagram beszúrása egy Word-dokumentumba az Aspose.Words használatával.
  Tanulja meg, hogyan adjon hozzá diagramot, széttörd a szeletet, és jelenítse meg
  a százalékokat néhány lépésben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: hu
lastmod: 2026-07-26
og_description: Kördiagram beszúrása egy Word-fájlba az Aspose.Words segítségével.
  Kövesse ezt az útmutatót, hogy megtanulja, hogyan adjon hozzá diagramot, szétrobbanó
  szeletet, és gyorsan jelenítse meg a százalékokat.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Kördiagram beszúrása Word-be – Lépésről lépésre Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Kördiagram beszúrása Wordbe az Aspose.Words segítségével – Teljes útmutató
url: /hu/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pie chart beillesztése Word dokumentumba az Aspose.Words segítségével – Teljes útmutató

Valaha is szükséged volt **pie chart beillesztése** egy Word jelentésbe, de nem tudtad, hol kezdjed? Nem vagy egyedül. Sok üzleti alkalmazásban a pie chart vizuális hatása az adatokat azonnal emészthetővé teszi, és az Aspose.Words csak néhány kódsorral teszi ezt lehetővé.

Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan **add chart to Word**, hogyan robbantsunk ki egy szeletet a hangsúlyozáshoz, és hogyan jelenítsük meg a százalékokat az adatcímkékben. A végére egy azonnal futtatható példát kapsz, amelyet bármely .NET projektbe beilleszthetsz.

---

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Core és .NET Framework esetén is működik)
- Az Aspose.Words for .NET NuGet csomag telepítve  
  ```bash
  dotnet add package Aspose.Words
  ```
- Alapvető C# szintaxis ismeret — semmi különleges nem szükséges
- A választott IDE (Visual Studio, Rider vagy VS Code)

Ennyi. Kezdjünk is bele.

---

## Pie chart beillesztése Word dokumentumba

Az első dolog, amire szükségünk van, egy új `Document` objektum és egy `DocumentBuilder`. A builder-t tekinthetjük egy tollnak, amely közvetlenül a Word vászonra ír.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Miért fontos:** A `Document` a teljes .docx fájlt képviseli, míg a `DocumentBuilder` egy kényelmes API-t biztosít az olyan elemek beillesztéséhez, mint diagramok, táblázatok és szöveg. Ez minden **how to add chart** művelet alapja.

---

## Hogyan adjunk diagramot Word-hez

Most, hogy van egy builderünk, valójában **pie chart beillesztése** lehetséges. Az `insertChart` metódus a diagram típusát és a kívánt méreteket pontban (1 pont = 1/72 hüvelyk) veszi át.

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tipp:** Ha más méretre van szükséged, csak módosítsd a szélesség és magasság értékeket. A diagram automatikusan skálázódik, hogy illeszkedjen az oldal margóira.

---

## Hogyan robbantsunk ki egy szeletet a hangsúlyozáshoz

Egy gyakori vizuális trükk, hogy “kibontjuk” a szeletet, hogy kiemelkedjen a körből. Ez a legfontosabb szegmens felé irányítja az olvasó tekintetét.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Miért robbantsunk ki egy szeletet?** Ha egy adott kategóriát szeretnél kiemelni — például a “Q1 revenue” egy pénzügyi jelentésben — a szelet kibontása azonnal láthatóvá teszi azt további szöveg nélkül.

---

## Hogyan jelenítsük meg a százalékokat az adatcímkéken

A legtöbb pie chart jobban néz ki, ha minden szelet megjeleníti a százalékát. Az Aspose.Words egyetlen tulajdonsággal engedélyezi ezt.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Gyors megjegyzés:** A `ShowPercentage` jelző az egész sorozat minden pontjára érvényes, így nem kell egyenként beállítani a szeleteknél.

---

## A diagramot tartalmazó dokumentum mentése

Végül a dokumentumot leírjuk a lemezre. Válassz bármilyen mappát, csak győződj meg róla, hogy az útvonal létezik.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Amikor megnyitod a `PieChart.docx` fájlt a Microsoft Wordben, egy tökéletesen megjelenített pie chart-ot látsz, ahol az első szelet ki van bontva és a százalékok megjelennek — pontosan azt, amit egy kifinomult üzleti jelentéstől várnál.

---

## Teljes működő példa

Az alábbiakban a teljes, másolás‑beillesztésre kész program látható. Futtasd konzolalkalmazásként, és ellenőrizd a kimeneti fájlt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Várt eredmény:** Nyisd meg a generált `PieChart.docx` fájlt. Egy három szeletből álló pie chart-ot látsz “Sales Q1” címmel, ahol az első szelet ki van húzva, és minden szelet “30 %”, “45 %”, illetve “25 %” felirattal rendelkezik. A vizuális megjelenés megfelel a megadott adatoknak.

---

## Gyakori kérdések és speciális esetek

- **Mi van, ha több sorozatra van szükségem?**  
  Csak adj hozzá további `ChartSeries` objektumokat a `chart.Series`-hez. Minden sorozat saját adatkészlettel, színekkel és kibontási beállításokkal rendelkezhet.

- **Megváltoztathatom a diagram színeit?**  
  Igen. Minden `ChartPoint` rendelkezik egy `Format.Fill.ForeColor` tulajdonsággal, amelyet bármely `System.Drawing.Color` értékre beállíthatsz.

- **Mi van a különböző diagramtípusokkal?**  
  A `ChartType` enum tartalmaz bar, line, doughnut és még sok más típust. Cseréld le a `ChartType.Pie`-t arra a diagramra, amelyre szükséged van.

- **A diagram szerkeszthető Wordben a beillesztés után?**  
  Teljesen. A Word a diagramot natív Office diagramként kezeli, így a felhasználók duplán rá kattintva megnyithatják a beépített diagram szerkesztőt.

---

## Összegzés

Most már pontosan tudod, hogyan **pie chart beillesztése** Word dokumentumba az Aspose.Words segítségével, **hogyan adjunk diagramot Word-hez**, **hogyan robbantsunk ki egy szeletet**, és **hogyan jelenítsük meg a százalékokat** az adatcímkéken. A fenti teljes példa készen áll a futtatásra, és kiterjeszthető egyedi adatokkal, stílusokkal vagy további sorozatokkal.

Készen állsz a következő lépésre? Próbáld ki a pie helyett egy doughnut diagramra cserélni, vagy automatikusan generálj egy csomó jelentést különböző adatkészletekkel. Ha érdekelnek más vizualizációk, nézd meg útmutatóinkat a **how to add chart** vonal- és oszlopdiagramokhoz, vagy böngészd a **add chart to word** API referenciát a mélyebb testreszabásokért.

Boldog kódolást, és legyenek a dokumentumaid mindig olyan tiszták, mint egy tökéletesen szeletelt pite!

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódpéldákat tartalmaz lépésről lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}