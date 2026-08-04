---
category: general
date: 2026-08-04
description: Az egyéni adatcímke‑elhelyezés a C# diagramokhoz lehetővé teszi, hogy
  a címkéket a diagram szeletek közepére helyezze. Kövesse ezt a lépésről‑lépésre
  útmutatót az Aspose.Words diagram API használatával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: hu
lastmod: 2026-08-04
og_description: Egyéni adatcímke‑pozicionálás diagramokhoz C#‑ban megmutatja, hogyan
  helyezze középre az összes adatcímkét a Word-diagram egyes szeletein. Mesteri szintű
  adatcímke‑pozicionálás a diagramoknál az Aspose.Words segítségével.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Egyedi adatcímke elhelyezés diagramokhoz C#-ban – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Egyéni adatcímke elhelyezése diagramokhoz C#‑ban
url: /hu/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Egyéni adatcímke‑elhelyezés diagramokhoz C#‑ban

**Egyéni adatcímke‑elhelyezés diagramokhoz** lehetővé teszi, hogy pontosan meghatározd, hol jelenjen meg minden címke egy Word‑dokumentumban lévő diagramon. Ebben az útmutatóban megtanulod, hogyan helyezd középre az összes adatcímkét minden szeletnél C#‑ban és az Aspose.Words diagram‑API‑val.

Megkapod a teljes, futtatható példát, amely betölti a `.docx` fájlt, eléri az első diagram alakzatot, minden címke `Position` tulajdonságát `Center`‑re állítja, majd elmenti a módosított dokumentumot. Nincs szükség külső hivatkozásokra – csak az Aspose.Words for .NET könyvtárra és egy alap C# fejlesztői környezetre.

**Mit fogsz megtanulni**

* Hogyan tölts be egy Word‑dokumentumot, amely diagramot tartalmaz.  
* Hogyan találjuk meg a diagram alakzatot az Aspose.Words diagram‑API‑val.  
* Hogyan alkalmazzuk a **diagram adatcímke‑pozicionálást** minden sorozatra a diagramon.  
* Hogyan mentsük el a dokumentumot, hogy a középre helyezett címkék megjelenjenek Word‑ben.  

**Előfeltételek**

* .NET 6.0 (vagy újabb) telepítve.  
* Visual Studio 2022 (vagy bármely C# IDE).  
* Hivatkozás a `Aspose.Words` NuGet csomagra.  
* Egy Word‑fájl (`Chart.docx`), amely legalább egy diagramot tartalmaz.

---

## Egyéni adatcímke‑elhelyezés diagramokhoz – 1. lépés: a dokumentum betöltése

Az első teendő a diagramot tartalmazó Word‑fájl megnyitása. A `Document` az Aspose.Words‑nél minden manipuláció kiindulópontja.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Miért fontos ez a lépés*: A dokumentum betöltése nélkül nem érheted el a diagram objektumot. A validáció biztosítja, hogy egyértelmű hibát kapj, ha a fájl nem tartalmaz diagramot, ezzel elkerülve a későbbi null‑referenciát.

---

## Az Aspose.Words diagram‑API használata diagram alakzatok eléréséhez

Az Aspose.Words a diagramot egy `Chart` objektumként kezeli, amely egy `Shape`‑en belül van. A megfelelő gyermekcsomópont átkapcsolásával érheted el.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Miért fontos ez a lépés*: A `Chart` közvetlen elérése teljes irányítást ad a sorozatok, adatpontok és címke‑tulajdonságok felett. Ha a shape nem diagram, a kód korán leáll egy tájékoztató üzenettel.

---

## Diagram adatcímke‑pozicionálás beállítása C#‑ban

Most iterálj végig minden sorozaton és minden adatcímkén, állítsd be a `Position` értékét `Center`‑re. Ez a **Egyéni adatcímke‑elhelyezés diagramokhoz** lényege.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Pro tipp**: Ha más elhelyezést szeretnél (pl. `InsideEnd` oszlopdiagramnál), módosítsd az enum értékét ennek megfelelően. A `ChartDataLabelPosition` enum tartalmazza a Word által támogatott összes szabványos pozíciót.

*Miért fontos ez a lépés*: A `label.Position` módosítása frissíti az alatta lévő OOXML reprezentációt, így a címke középre kerül, amikor a dokumentumot a Microsoft Word‑ben megnyitod.

---

## A Word‑dokumentum mentése a frissített címkékkel

A diagram módosítása után írd vissza a változásokat egy fájlba. Felülírhatod az eredetit, vagy létrehozhatsz egy új másolatot.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Miért fontos ez a lépés*: A mentés az frissített OOXML‑t a lemezre írja. A `ChartLabelsCentered.docx` megnyitása Word‑ben minden szelet címkéjét középre helyezve mutatja, bizonyítva, hogy a **Egyéni adatcímke‑elhelyezés diagramokhoz** sikeres volt.

---

## Szélsőséges esetek és variációk

| Helyzet | Hogyan kezeljük |
|-----------|---------------|
| **Több diagram** ugyanabban a dokumentumban | Iterálj a `doc.GetChildNodes(NodeType.Shape, true)` föl, és ellenőrizd minden shape‑nél a `shape.HasChart` értékét. |
| **Különböző diagramtípusok** (pie, doughnut, bar) | A `ChartDataLabelPosition.Center` ugyanúgy működik kördiagramoknál. Oszlop‑/sávdiagramoknál esetleg a `InsideEnd` vagy `OutsideEnd` a megfelelőbb. |
| **A címkeszöveg formázása szükséges** | Érd el a `label.TextProperties`‑t a betűméret, szín vagy félkövér beállításához. |
| **.NET Core környezetben futtatás** | Győződj meg róla, hogy a .NET Standard verzióra hivatkozol az Aspose.Words‑ből; az API azonos. |

---

## Teljes működő példa

Az alábbiakban a teljes program látható, amelyet egyszerűen beilleszthetsz egy konzolalkalmazásba. Tartalmazza az összes szükséges `using` direktívát és a hibakezelést.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Várt eredmény**: Nyisd meg a `ChartLabelsCentered.docx` fájlt a Microsoft Word‑ben. A diagram minden szelete most a saját adatcímkéjét közvetlenül a szelet közepén jeleníti meg, tisztább vizuális megjelenést biztosítva.

---

## Összegzés

Most már rendelkezel egy teljes **Egyéni adatcímke‑elhelyezés diagramokhoz** megoldással C#‑ban. A dokumentum betöltésével, a diagram elérésével az Aspose.Words diagram‑API‑val, a `ChartDataLabelPosition.Center` beállításával minden címkére, majd a fájl mentésével automatizálhatod a címke‑pozicionálást bármely Word‑alapú diagramon.

Ezután fedezd fel a további **diagram adatcímke‑pozicionálási** lehetőségeket, például a `InsideEnd` vagy `OutsideEnd` opciókat, vagy kísérletezz **C# diagrammanipulációval**, hogy színeket változtass, jelmagyarázatot adj hozzá, vagy teljesen új diagramokat generálj. Ezek a kiterjesztések közvetlenül az itt bemutatott technikákra épülnek, és bővítik a Word‑dokumentum diagram‑automatizálási képességeidet. Boldog kódolást!

## Mit érdemes még tanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy könnyedén elsajátíthasd az API további funkcióit, illetve alternatív megvalósítási módszereket a saját projektjeidben.

- [Diagram adatcímke testreszabása](/words/english/net/programming-with-charts/chart-data-label/)
- [Diagram adatcímke számformátumának beállítása](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Diagram adatcímke](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}