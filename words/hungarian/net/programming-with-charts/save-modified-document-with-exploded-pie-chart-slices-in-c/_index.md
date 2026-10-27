---
category: general
date: 2026-10-13
description: 'Módosított dokumentum mentése a kördiagram testreszabása után: szeletek
  szétrobbanása, az első szelet szögének módosítása, és a százalékos címkék megjelenítése
  C#‑ban.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: hu
lastmod: 2026-10-13
og_description: Mentsd el a módosított dokumentumot a C#-ban testreszabott kördiagram
  után. Tanuld meg, hogyan robbantsd szét a kördiagram szeleteit, állítsd be az első
  szelet szögét, és jelenítsd meg a százalékos címkéket.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Módosított dokumentum mentése kibontott kördiagram szeletekkel – C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Módosított dokumentum mentése szétrepedt kördiagram szeletekkel C#-ban
url: /hu/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Módosított dokumentum mentése szétrobbanó kördiagram szeletekkel C#-ban

Ha **save modified document**-ot kell menteni egy Word kördiagram finomhangolása után, ez az útmutató pontosan megmutatja, hogyan. Megtanulja, hogyan robbantsa szét a kördiagram szeleteit, módosítsa az első szelet szögét, és jelenítse meg a százalékos címkéket – mindezt néhány C# sorral.

A diagramok testreszabása gyakori követelmény jelentések, számlák vagy műszerfalak programozott generálásakor. A tutorial végére képes lesz betölteni egy DOCX fájlt, módosítani a diagram megjelenését, és **save modified document**-ot elmenteni a terjesztéshez.

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑vel is működik)
- Aspose.Words for .NET 23.10 vagy újabb (ingyenes próba vagy licencelt példány)
- Egy Word fájl (`input.docx`), amely egyetlen kördiagramot tartalmaz
- Visual Studio 2022 vagy bármely C# IDE

> **Tip:** Az Aspose.Words NuGet csomag a `dotnet add package Aspose.Words` paranccsal adható hozzá.

## 1. lépés: A diagramot tartalmazó Word dokumentum betöltése

Az első lépés a forrás DOCX fájl megnyitása. A `Document` osztály a teljes Word fájlt képviseli a memóriában.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

A dokumentum betöltése teljes hozzáférést biztosít minden csomóponthoz, beleértve a diagramokat tartalmazó alakzatokat is.

## 2. lépés: Az első diagram alakzatának lekérése a dokumentumból

A diagramok `Shape` csomópontokban tárolódnak. Az első diagramot a `GetChild` segítségével találhatja meg.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Ha a dokumentum több diagramot tartalmaz, állítsa be az indexet (`0`) vagy iteráljon a gyűjteményen. Ez a sor biztosítja, hogy legyen hivatkozása a módosítani kívánt `Chart` objektumra.

## 3. lépés: A kördiagram szeleteinek szétrobbanása

Egy szelet szétrobbanása elválasztja azt a kör többi részétől, így a diagram könnyebben olvasható. Az `Explode` tulajdonság az egész sorozatra vonatkozik.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Az `Explode` értékének `true`-ra állítása **explodes pie chart slices** az egész sorozatra, ami akkor hasznos, ha minden szeletet ki szeretne emelni.

## 4. lépés: Az első szelet szögének módosítása

Néha szükség van arra, hogy az első szelet egy egyéni szöggel kezdődjön, például egy tervezési irányelvhez igazítva.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

A `FirstSliceAngle` tulajdonság **changes first slice** orientációt, elforgatva a teljes kört, így az első szelet 30 foknál kezdődik.

## 5. lépés: Százalékos címkék megjelenítése a kördiagram szeletein

Az egyes szeletek numerikus hozzájárulásának megjelenítése gyakran szükséges a jelentésekben. A `DataLabel.ShowPercentage` jelző bekapcsolja a százalékos értékeket.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Ez a lépés **show percentage labels** közvetlenül a diagramon, ami kielégíti a **display percentages pie** követelményt is.

## 6. lépés: A módosított dokumentum mentése

Miután az összes testreszabás alkalmazásra került, mentse a változásokat egy új fájlba. A `Save` metódus a frissített DOCX-et a lemezre írja.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Most már rendelkezik egy **save modified document**-tal, amely szétrobbanó kördiagramot, elforgatott első szeletet és látható százalékos címkéket tartalmaz.

![Módosított dokumentum mentése szétrobbanó kördiagrammal](/images/pie-chart-exploded.png "Módosított dokumentum mentése szétrobbanó kördiagram szeletekkel és százalékos címkékkel")

*A képernyőkép a végső kimenetet mutatja a dokumentum mentése után.*

## Teljes, futtatható példa

Az összetevők összeállításával itt a teljes program, amelyet beilleszthet egy konzolos projektbe:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Várt eredmény

`output.docx` megnyitása egy kördiagramot mutat, ahol:

- Minden szelet enyhén el van választva (**exploded pie chart slices**)
- Az első szelet 30 fokos eltolással kezdődik (**change first slice**)
- Minden szelet a hozzájárulását százalékban mutatja (**show percentage labels**, **display percentages pie**)
- A fájl **save modified document** lett, anélkül, hogy az eredetit módosította volna.

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| **Mi van, ha a dokumentumnak nincs diagramja?** | A kód a `GetChild` után `null`-ra ellenőriz. Ha nincs diagram, vagy hozzáadhat egyet programozottan, vagy egyértelmű üzenettel leállíthatja. |
| **Robbantathatok csak egyetlen szeletet?** | Igen. Használja a `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` kifejezést, ahol az `i` a szelet indexe. |
| **Hogyan változtathatom meg a címke formátumát (pl. érték + % megjelenítése)?** | Állítsa be a `chart.PieChart.DataLabel.ShowValue = true;` értéket, és opcionálisan a `chart.PieChart.DataLabel.ShowPercentage = true;`-t, hogy mindkettőt kombinálja. |
| **Megmarad a diagram stílusa a mentés után?** | Az Aspose.Words megőrzi az összes stílust, beleértve a színeket és betűtípusokat, amikor **save modified document**. |
| **Feldolgozhatok több diagramot egy fájlban?** | Iteráljon végig az összes `Shape` csomóponton a `NodeType.Shape` segítségével, és szűrje a `shape.HasChart` alapján. Alkalmazza ugyanazokat a lépéseket minden diagramra. |

## Következtetés

Most már tudja, hogyan **save modified document** a kördiagram Word-ben történő programozott testreszabása után. Az útmutató bemutatta a kördiagram szeleteinek szétrobbanását, az első szelet szögének módosítását és a százalékos címkék megjelenítését – teljesítve a **show percentage labels**, **explode pie chart slices**, **display percentages pie**, és **change first slice** követelményeket.

Ezután érdemes megvizsgálni:

- Adatsorok dinamikus hozzáadása (`chart.Series.Add(...)`)  
- A jelmagyarázat elhelyezésének és a diagram címének testreszabása  
- A DOCX PDF-re konvertálása a diagram stílusának megőrzése mellett  

Nyugodtan kísérletezzen különböző szögekkel, robbantási beállításokkal vagy címkeformátumokkal, hogy megfeleljen jelentési igényeinek. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészletet tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Hogyan mentse a szerkesztett dokumentumot C#-ban az Aspose.Words segítségével – Lépésről‑lépésre útmutató](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Diagram sorozat adatainak frissítése Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/programming-with-charts/modify-chart-series/)
- [Oszlopdiagram beszúrása Word dokumentumba](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}