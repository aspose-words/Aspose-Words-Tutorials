---
category: general
date: 2026-09-14
description: Radar diagram beillesztése Word-be C#-val. Tanulja meg, hogyan állítsa
  be a diagram címét, adjon hozzá több sorozatot, és hozza létre a diagramot programozottan
  néhány sorban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: hu
lastmod: 2026-09-14
og_description: Radar diagram beszúrása Word-be C#-val. Ez az útmutató bemutatja,
  hogyan állítható be a diagram címe, hogyan adhatók hozzá több sorozat, és hogyan
  hozható létre a diagram programozottan.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Radar diagram beillesztése Word-be C#-val – gyors programozási útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Radar diagram beszúrása Word-be C#‑val – lépésről lépésre útmutató
url: /hu/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Radar diagram beszúrása Word-be C#-al – lépésről‑lépésre útmutató

Ha **radar diagramot** kell beszúrni egy Word dokumentumba, ez az útmutató megmutatja, hogyan teheted meg programozottan C#-al. Megtanulod, hogyan **állítsd be a diagram címét**, hogyan adj hozzá **több sorozatos radar diagramot**, és hogyan mentsd el a fájlt anélkül, hogy elhagynád az IDE-t.

Az útmutató mindent lefed a projekt beállításától a végső `doc.Save` hívásig, így a teljes példát egyszerűen másolás‑beillesztéssel futtathatod. Külső dokumentáció keresése nem szükséges.

## Előfeltételek

* .NET 6 (vagy újabb) telepítve.
* Érvényes Aspose.Words for .NET licenc (vagy ideiglenes értékelő kulcs).
* Visual Studio 2022 vagy bármely kedvelt C# IDE.

> **Pro tipp:** Ha ingyenes próbaverziót használsz, ne felejtsd el beállítani a licencet az első `Document` létrehozása előtt, hogy elkerüld az értékelő vízjelet.

## 1. lépés: Radar diagram beszúrása Word dokumentumba

Az első művelet egy új `Document` és egy `DocumentBuilder` létrehozása. A builder hozzáférést biztosít a dokumentum tartalmához, és lehetővé teszi, hogy a **radar diagramot** pontosan oda helyezd, ahol szükséged van rá.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Miért fontos ez a lépés:* `InsertChart` egy diagram objektumot hoz létre, amelyet a dokumentum mentése előtt teljesen konfigurálhatsz. A `ChartType.Radar` használata azt mondja a Wordnek, hogy radiális diagramot jelenítsen meg oszlop vagy vonaldiagram helyett.

## 2. lépés: Diagram címének és tengelygraduálásának beállítása

A cím nélküli diagram zavaró lehet. Itt **beállítjuk a diagram címét** „Sales Radar” értékre, és engedélyezzük a graduálást mindkét tengelyen (az Aspose.Words 24.9-től elérhető).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Miért fontos ez a lépés:* A cím kontextust ad az olvasóknak, és a graduálás javítja az olvashatóságot, mivel megmutatja, hogy az egyes adatpontok hol helyezkednek el a skálán.

## 3. lépés: Több sorozat létrehozása a radar diagramhoz

Egy **több sorozatos radar diagram** lehetővé teszi, hogy különböző időszakokat egymás mellett hasonlíts össze. Az alábbiakban két sorozatot adunk hozzá – Q1 és Q2 – mindegyik három adatponttal.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Miért fontos ez a lépés:* Több sorozat hozzáadása bemutatja, hogyan lehet összehasonlítani adathalmazokat ugyanazon a radaron, ami gyakori igény az értékesítés, teljesítmény vagy felmérések eredményei esetén.

## 4. lépés: Word dokumentum programozott mentése

Végül **programozottan létrehozod a diagramot** és a dokumentumot lemezre mented. A `Save` metódus egy `.docx` fájlt ír, amely megnyitható a Microsoft Wordben.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

Amikor megnyitod a `RadialGraduations.docx` fájlt, egy „Sales Radar” című radar diagramot látsz, két sorozattal (Q1 és Q2), amelyek a Jan‑Mar hónapokra vannak ábrázolva.

### Várható eredmény

![Radar diagram Word-ben](https://example.com/radar-chart.png){: .align-center alt="Word dokumentum, amely radar diagramot mutat két adat sorozattal"}

A képernyőfotó (vagy a tényleges fájl) megerősíti, hogy a diagram helyesen lett beszúrva, címkézve és feltöltve.

## Teljes, futtatható példa

Mindent összevonva, itt egy önálló program, amelyet lefordíthatsz és futtathatsz:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Futtasd a programot, nyisd meg a generált fájlt, és ellenőrizd, hogy a **radar diagram beszúrása** művelet sikeres volt-e.

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| **Megváltoztathatom a diagram típusát a beszúrás után?** | Igen. Az `InsertChart` után egy új `ChartType` értéket adhatunk a `chart.Type`-nak. Azonban a diagramot a megfelelő típussal már a kezdetektől létrehozni hatékonyabb. |
| **Mi van, ha két sorozatnál többre van szükségem?** | Hívja meg a `chart.Series.Add`-t minden további sorozathoz. A diagram automatikusan igazítja a jelmagyarázatot és a színeket. |
| **Hogyan testreszabhatom a színeket vagy a jelölőket?** | Használja a `chart.Series[i].Format.Fill.ForeColor`-t a kitöltőszínekhez és a `chart.Series[i].Marker`-t a jelölő stílusokhoz. |
| **Kompatibilis az API a .NET Framework‑kel?** | Ugyanaz a kód működik a .NET Framework 4.7+ verzióval; csak hivatkozzon a megfelelő Aspose.Words DLL-re. |
| **Mi van, ha egy régebbi Aspose.Words verziót használok?** | A graduálás (`HasGraduations`) a 24.9-es verzióban került bevezetésre. Régebbi verziók esetén manuálisan hozzáadhat rácsvonalakat a `chart.AxisX.MajorGridLines` és `chart.AxisY.MajorGridLines` használatával. |

## Összegzés

Most már tudod, hogyan **szúrj be radar diagramot** egy Word dokumentumba C#-al, **állítsd be a diagram címét**, adj hozzá egy **több sorozatos radar diagramot**, és **hozd létre a diagramot programozottan**. Ez az átfogó megoldás lehetővé teszi jelentések, műszerfalak vagy bármely olyan helyzet automatizálását, ahol a kategóriák vizuális összehasonlítása szükséges.

Ezután fedezd fel a kapcsolódó témákat, például a **diagram színeinek testreszabását**, a **diagramok képként való exportálását**, vagy a **diagramok PDF fájlokba ágyazását**. Kísérletezz különböző adathalmazokkal, hogy lásd, hogyan alkalmazkodik a radar vizualizáció.

Boldog kódolást!

## Mit érdemes következőként megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Oszlopdiagram beszúrása Word-be Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-column-chart/)
- [Buborékdiagram beszúrása Word-be Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Területdiagram beszúrása Word dokumentumba | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}