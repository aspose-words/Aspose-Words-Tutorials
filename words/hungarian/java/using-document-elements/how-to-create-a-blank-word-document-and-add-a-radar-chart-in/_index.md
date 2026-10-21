---
category: general
date: 2026-09-21
description: Hozzon létre üres Word-dokumentumot, és tanulja meg, hogyan illesszen
  be radar diagramot egy Word-fájlba a DocumentBuilder segítségével – lépésről lépésre
  útmutató.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: hu
lastmod: 2026-09-21
og_description: Hozzon létre egy üres Word-dokumentumot, és szúrjon be radar diagramot
  egy Word-fájlba az Aspose.Words segítségével. Kövesse ezt az útmutatót, hogy gyorsan
  generáljon diagramot a Word-dokumentumban.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Hozzon létre egy üres Word-dokumentumot, és adjon hozzá radar diagramot
  – teljes C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Hogyan készítsünk egy üres Word-dokumentumot, és adjunk hozzá radar diagramot
  C#-ban
url: /hu/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre üres Word dokumentumot és adjunk hozzá radar diagramot C#-ban

Ha **üres Word dokumentumot** kell létrehozni és beágyazni egy radar (radiális) diagramot, ez a tutorial egy azonnal futtatható megoldást nyújt. Megmutatjuk, hogyan használhatja az Aspose.Words .NET-et a fájl generálásához, a diagram beszúrásához és az eredmény mentéséhez – mindezt néhány tömör lépésben.

Egy üres dokumentum tiszta vásznat biztosít bármilyen automatizált jelentési szituációhoz, és egy radar diagram hozzáadásával közvetlenül a Wordben jelenítheti meg a többdimenziós adatokat. A útmutató végére képes lesz Word dokumentum diagramot generálni manuális szerkesztés nélkül.

## Mit fogsz megtanulni

* Hogyan **hozzunk létre üres Word dokumentumot** programozottan C#-ban.
* A pontos kód a **radar diagram beszúrásához** a `DocumentBuilder` használatával.
* Módszerek a **diagram Word fájlba való beszúrására** és a méretének testreszabására.
* Hogyan **generáljunk Word dokumentum diagramot** és ellenőrizzük a kimenetet.
* Tippek a **radial diagram Word fájlokhoz** való hozzáadáshoz, beleértve a gyakori buktatókat.

### Előfeltételek

* .NET 6.0 vagy újabb (a kód .NET Framework 4.6+ esetén is működik).
* Aspose.Words for .NET (NuGet csomag `Aspose.Words` verzió 23.9 vagy újabb).
* Alapvető ismeretek a C#-ról és a Visual Studio-ról vagy a kedvenc IDE-jéről.

## Üres Word dokumentum létrehozása C#-ban

Az első lépés egy üres `Document` objektum példányosítása. Ez az objektum egy teljesen üres `.docx` fájlt képvisel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` létrehozza a fájlstruktúrát, de még nem tartalmaz szakaszokat vagy oldalakat. Az Aspose.Words automatikusan hozzáad egy alapértelmezett szekciót, amikor tartalmat kezd el hozzáadni, ezért a következő lépés extra konfiguráció nélkül működik.

## Radar diagram beszúrása a Word fájlba

A radar diagram (más néven radiális diagram) adatpontokat jelenít meg olyan tengelyeken, amelyek egy központi pontból sugároznak. Az Aspose.Words erre a célra a `DocumentBuilder.insertChart` metódust biztosítja.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` egy `Chart` objektumot ad vissza, amelyet tovább konfigurálhat. A diagram az üres dokumentum első oldalán jelenik meg, mivel a builder alapértelmezés szerint a dokumentum elején helyezkedik el.

## Diagram beszúrása Word fájlba – adat sorozatok hozzáadása

Az adat nélküli diagram láthatatlan. Töltse fel a radar diagramot egy vagy több sorozattal, hogy értelmes legyen.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Tetszőleges számú sorozatot hozzáadhat. Minden sorozatnak lehet egyedi neve, amely a diagram jelmagyarázatában jelenik meg. Az adatpontok a radiális tengelyekhez tartoznak; a hozzáadásuk sorrendje határozza meg a körön belüli helyzetüket.

## Word dokumentum diagram generálása – a fájl mentése

A diagram összeállítása után mentse a dokumentumot a lemezre. Válasszon egy olyan helyet, ahol írási jogosultsága van.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Amikor megnyitja a keletkezett `.docx` fájlt a Microsoft Wordben, egy üres oldalt fog látni, amelyen egy 400 × 300 pont méretű radar diagram található, a mintaadatokkal feltöltve.

### Várt kimenet

* Egy `RadialChartExample.docx` fájl az asztalán.
* Az első oldal egy radar diagramot tartalmaz, amelyen öt adatpont van, a „Series 1” felirattal.
* Nem jelenik meg további szöveg, mivel a dokumentum üresen indult.

## Radiális diagram Word – gyakori szélhelyzetek kezelése

### 1. Diagram méretének módosítása a beszúrás után

Ha a kezdeti méretek nem illeszkednek a layouthoz, módosítsa a diagram méretét így:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Diagram beszúrása egy meghatározott helyre

A `InsertChart` hívása előtt áthelyezheti a builder kurzorát egy könyvjelzőre, táblázatcellára vagy bekezdésre.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Diagram megjelenésének testreszabása

Az Aspose.Words teljes diagram objektummodellt tesz elérhetővé, amely lehetővé teszi címek, tengelycímkék és színek beállítását.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Hiányzó betűtípusok kezelése

Ha a célkörnyezetben hiányzik a diagramhoz használt betűtípus, az Aspose.Words alapértelmezett betűtípust helyettesít. A konzisztencia biztosításához ágyazza be a szükséges betűtípusokat:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Exportálás más formátumokba

Ugyanaz a dokumentum menthető PDF, HTML vagy PNG formátumban extra kódbeli módosítások nélkül:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Teljes, futtatható példa

Az összes részlet összeállításával egyetlen programot kap, amelyet másolhat, beilleszthet és futtathat.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Futtassa ezt a programot, nyissa meg a generált fájlt, és egy professzionális radar diagramot fog látni, amely készen áll a terjesztésre.

## Következtetés

Most már tudja, hogyan **hozzon létre üres Word dokumentumot**, **szúrjon be radar diagramot**, és **generáljon Word dokumentum diagramot** az Aspose.Words segítségével. A fenti lépések követésével **radiális diagram Word** fájlokat is hozzáadhat bármely automatizált jelentési folyamathoz, testreszabhatja a méretet, a stílust, és exportálhatja további formátumokba.

**Következő lépések**

* Fedezzen fel más diagramtípusokat (`ChartType.Column`, `ChartType.Pie`), hogy bővítse jelentési eszköztárát.
* Több diagram kombinálása egy oldalon a `InsertChart` többszöri meghívásával.
* Adatok integrálása adatbázisból vagy CSV fájlból a sorozatok dinamikus feltöltéséhez.
* Tekintse át az Aspose.Words dokumentációt a fejlett formázási lehetőségekért, például feltételes adatcímkék és diagram sablonok.

Nyugodtan kísérletezzen a kóddal, módosítsa a méreteket, vagy cserélje le a mintaadatokat valós üzleti mutatókkal. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}