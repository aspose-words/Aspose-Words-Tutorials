---
category: general
date: 2026-09-05
description: Radar diagram létrehozása Word-ben C#-val. Tanulja meg, hogyan generáljon
  egy üres Word-dokumentumot, adjon hozzá radar diagramot, állítsa be a diagram méretét,
  és gyorsan engedélyezze a jelölőket.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: hu
lastmod: 2026-09-05
og_description: Radar diagram létrehozása Wordben C#-val. Ez az útmutató megmutatja,
  hogyan generáljunk egy üres Word-dokumentumot, adjunk hozzá radar diagramot, állítsuk
  be a diagram méretét, és engedélyezzük a jelölőket – mindezt percek alatt.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Radar diagram létrehozása Wordben – lépésről lépésre C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Hogyan készítsünk radar diagramot, és adjuk hozzá a diagramot a Wordhöz C#‑al
url: /hu/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre radar diagramot és adjunk diagramot a Word dokumentumhoz C#-ban

Ha **radar diagramot** kell létrehoznod egy Word fájlban, ez az útmutató végigvezet a teljes folyamaton. Megtanulod, hogyan **generálj üres Word dokumentumot**, hogyan illessz be egy radar diagramot, **állítsd be a diagram méretét Wordben**, és hogyan engedélyezd a tengely felosztásait – mindezt néhány C# sorral.

A vizuális adatok jelentéseken való hozzáadása gyakori követelmény, és az Aspose.Words használata egyszerűvé teszi. Az alábbi lépésekben azt is bemutatjuk, hogyan **add chart to word** dokumentumokba programozottan, így automatizálhatod a műszerfalakat, pénzügyi összefoglalókat vagy bármilyen adat‑vezérelt tartalmat.

## Előkövetelmények

* .NET 6.0 vagy újabb telepítve  
* Aspose.Words for .NET licenc (vagy ingyenes próba) – a könyvtár biztosítja a `Document`, `DocumentBuilder` és diagram API-kat, amelyeket ebben az útmutatóban használunk  
* Visual Studio 2022 (vagy bármely C# IDE)  

> **Pro tip:** Ha tesztelsz, helyezd az Aspose.Words DLL-t a projekt `bin` mappájába, és hivatkozz rá a NuGet-en keresztül (`Install-Package Aspose.Words`).

## Hogyan hozzunk létre radar diagramot egy Word dokumentumban

Az első lépés a **generate blank word document** létrehozása, amely a diagramot fogja tartalmazni. Ez egy tiszta vásznat biztosít, és lehetővé teszi a dokumentum metaadatai (szerző, cím) vezérlését, mielőtt bármilyen tartalom hozzáadódna.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Miért fontos:* Egy üres `Document` objektum biztosítja, hogy rejtett stílusok vagy szakaszok ne zavarják a diagram elrendezését. Emellett lehetővé teszi a dokumentum tulajdonságainak (szerző, cím) későbbi beállítását, ha szükséges.

## Hogyan adjunk diagramot a Word dokumentumhoz az Aspose.Words használatával

Ezután hozz létre egy `DocumentBuilder`-t. A builder a munkagépe, amely lehetővé teszi szöveg, kép és diagram beszúrását a dokumentumba.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Most már **add radar chart** közvetlenül ott, ahol a kurzor áll. Az `InsertChart` metódus egy `ChartType` enumot, valamint a szélességet és magasságot pontokban fogadja.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Miért 400 × 300?* Ezek a méretek tiszta, olvasható diagramot eredményeznek egy szabványos A4 lapon. A méretet később a **set chart size word** lépéssel módosíthatod, ha az elrendezés más képarányt igényel.

## Diagram méretének beállítása Wordben

Ha a beillesztés után finomhangolni szeretnéd a méretet, módosíthatod a diagram `Width` és `Height` tulajdonságait. Ez akkor hasznos, ha a környező szöveg vagy az oldal margói más vizuális egyensúlyt követelnek.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Megjegyzés:** Az `InsertChart` túlterhelés már beállítja a méretet, így a fenti kód opcionális és a teljesség kedvéért van bemutatva.

## Jelölővonalak engedélyezése a radiális tengelyen

A radar diagram a leghasznosabb, ha a radiális tengely egyértelmű felosztásokat mutat. A következő beállítások bekapcsolják a jelölővonalakat és 30 fokos intervallumra állítják őket, ami megfelel a tipikus iránytű‑stílusú radar kijelzőknek.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Miért fontos:* A felosztások segítik az olvasókat az egyes szögek értékeinek felmérésében, javítva a érthetőséget azok számára, akik nem ismerik az adatokat.

## A diagramot tartalmazó dokumentum mentése

Végül írd a dokumentumot a lemezre. Bármely mappát választhatod; csak győződj meg róla, hogy az útvonal létezik.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Amikor megnyitod a `RadialChart.docx` fájlt a Microsoft Wordben, egy teljesen megjelenített radar diagramot látsz, amely a lap közepén helyezkedik el, a megadott mérettel, és 30 fokonként jelölővonalakkal rendelkezik.

### Várt kimenet

* Egy `.docx` fájl, amelynek neve **RadialChart.docx**  
* Az első oldal egy 400 × 300 pont méretű radar diagramot tartalmaz  
* Az X‑tengely (radiális tengely) 0°, 30°, 60°, …, 330° jelölővonalakat jelenít meg  

Most már kicserélheted a helyőrző adat sorozatot a saját értékeidre a `radarChart.Series` elérésével – de ez már túlmutat az alap **add radar chart** útmutató keretein.

## Gyakori variációk és szélhelyzetek

| Forgatókönyv | Módosítás |
|--------------|-----------|
| **Másik diagramtípus** | Replace `ChartType.Radar` with `ChartType.Column`, `ChartType.Pie`, etc. |
| **Több diagram** | Call `InsertChart` repeatedly; each call positions the new chart after the previous one. |
| **Nagy adatállományok** | Use `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` to populate many points. |
| **Mentés PDF‑ként** | Call `document.Save("RadialChart.pdf", SaveFormat.Pdf);` after the chart is added. |
| **Futtatás .NET Core‑on** | Ensure you reference `Aspose.Words.NETCore` package; API usage is identical. |

## Teljes, futtatható példa

Az alábbiakban a teljes program található, amelyet beilleszthetsz egy konzolalkalmazásba. Tartalmazza az összes lépést, az opcionális méretmódosításokat és a magyarázó megjegyzéseket.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Futtasd a programot, nyisd meg a keletkezett fájlt, és a radar diagramot pontosan úgy fogod látni, ahogy le van írva.

## Következtetés

Most már tudod, hogyan **create radar chart** és **add chart to Word** dokumentumokba C# használatával. Az útmutató bemutatta egy **blank word document** generálását, egy radar diagram beszúrását, a **set chart size word** beállítását, valamint a tengely felosztásainak engedélyezését. Ezzel az alapokkal kibővítheted a megoldást több diagramra, egyedi adat sorozatokra vagy PDF‑ként való exportálásra.

### Következő lépések

* Fedezz fel más diagramtípusokat a `ChartType` segítségével (pl. `Bar`, `Line`) – lásd a **add radar chart** kulcsszót a kapcsolódó példákhoz.

## Mit érdemes még megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}