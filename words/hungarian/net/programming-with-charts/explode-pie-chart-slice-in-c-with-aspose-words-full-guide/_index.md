---
category: general
date: 2026-07-19
description: Törje szét a kördiagram szeletét az Aspose.Words for C# használatával.
  Tanulja meg, hogyan robbantsa szét a körszeletet, állítsa be a fánk lyuk méretét,
  és gyorsan módosítsa a diagram adatpontjait.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: hu
lastmod: 2026-07-19
og_description: Robbantsa fel a kördiagram szeletét az Aspose.Words for C# segítségével.
  Ez az útmutató megmutatja, hogyan robbantsa fel a körszeletet, állítsa be a gyűrűs
  diagram lyukméretét, és módosítsa hatékonyan a diagram adatpontjait.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Kördiagram szeletének kiemelése C#-ban – Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Kördiagram szeletének kifújása C#-ban az Aspose.Words segítségével – Teljes
  útmutató
url: /hu/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tört szelet kiemelése kördiagramon C#-ban az Aspose.Words segítségével – Teljes útmutató

Gondolkodtál már azon, hogyan **explodálhatod a kördiagram szeletét** egy Word dokumentumban C#-t használva? Nem vagy egyedül. Akár egy értékesítési prezentációt készítesz, akár felmérési eredményeket ábrázolsz, egy kiemelt szelet pontosan oda vonja a figyelmet, ahová szeretnéd. Ebben az útmutatóban végigvezetünk a teljes folyamaton – a dokumentum betöltésétől, a diagram lekérésén, az első szelet kiemelésén, a fánklyuk finomhangolásán, egészen a diagram adatpontjainak módosításáig.

Bele fogunk szőni a másodlagos fogalmakat is, amiket kereshetsz: **how to explode pie slice**, **adjust doughnut hole size**, és **change chart data points**. Nincs felesleges részlet, csak egy teljes, másolás‑beillesztés‑kész megoldás.

---

## Amire szükséged lesz

- **Aspose.Words for .NET** (a legújabb verzió 2026‑07‑19-ig). Letöltheted a NuGet‑ből a `Install-Package Aspose.Words` paranccsal.
- Egy **.NET 6+** projekt (vagy .NET Framework 4.7.2+, ha még régi környezetet használsz).
- Egy Word fájl (`Chart.docx`), amely már tartalmaz egy kör- vagy fánkdiagramot. Ha nincs, készíts egy gyors diagramot a Wordben, és mentsd el.

Ennyi—nincs extra könyvtár, nincs COM interop, csak tiszta managed kód.

## Tört szelet kiemelése – Lépésről‑lépésre megvalósítás

Az alábbiakban a feladatot kisebb lépésekre bontjuk. Minden szakasznak van egyértelmű címe, egy kódrészlete, és egy rövid magyarázat arra, *miért* csináljuk, amit csinálunk.

### 1. lépés: Aspose.Words telepítése és hivatkozása

Először is, add hozzá az Aspose.Words csomagot a projektedhez. A Package Manager Console‑ban:

```powershell
Install-Package Aspose.Words
```

> **Pro tipp:** Ha a Visual Studio beépített NuGet UI‑ját használod, keresd a „Aspose.Words” kifejezést, és kattints az Install gombra. Ez biztosítja, hogy a legújabb hibajavításokat és a diagramokkal való azonnali munkavégzést kapod.

### 2. lépés: A diagramot tartalmazó Word dokumentum betöltése

Szükségünk van egy `Document` objektumra, amely a módosítani kívánt diagramot tartalmazó `.docx` fájlra mutat.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Miért fontos:** A `Document` az Aspose.Words minden műveletének belépési pontja. A diagramok korai ellenőrzésével elkerülünk egy későbbi null referenciát, amikor a szelet kiemelését próbáljuk.

### 3. lépés: Az első diagramcsomópont lekérése

A legtöbb példa egyetlen diagramot feltételez, ezért az elsőt fogjuk lekérni. Ha több diagramod van, módosítsd az indexet ennek megfelelően.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Megjegyzés:** A `Chart` típusra való átkasztás biztonságos, miután megerősítettük, hogy létezik diagram. Ez az objektum hozzáférést biztosít a sorozatokhoz, adatpontokhoz és a diagramtípus‑specifikus beállításokhoz.

### 4. lépés: A kördiagram első szeletének kiemelése

Most a főszereplő—**how to explode pie slice**. Beállítjuk az első adatpont `Exploded` tulajdonságát.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Miért működik:** Az `Exploded` azt mondja a Wordnek, hogy húzza el a szeletet a középponttól, létrehozva a klasszikus „kifújt kör” hatást. A tulajdonság boolean, így `true`‑ra állítva megvalósul.

### 5. lépés: A fánk lyuk méretének beállítása (ha fánkdiagramról van szó)

Ha a diagramod fánk, akkor **adjust doughnut hole size**-t szeretnél alkalmazni. A lyuk mérete a diagram sugárának százaléka.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Mit jelent a szám:** A `30` érték azt jelenti, hogy a belső kör a teljes sugár 30 %-át foglalja el, így vastagabb külső gyűrű marad.

### 6. lépés: Diagram adatpontok módosítása (opcionális)

Néha szükség van a **change chart data points**-ra – lehet, hogy frissítetted az alapul szolgáló számokat, és a vizuálisan is ezt szeretnéd látni.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Miért csinálod:** Egy adatpont értékének módosítása automatikusan újraszámolja a szeletek százalékait, így a diagram pontos marad, anélkül, hogy manuálisan szerkesztenéd a Wordben.

### 7. lépés: A módosított dokumentum mentése

Végül írd vissza a változtatásokat a lemezre. Felülírhatod az eredetit vagy létrehozhatsz egy új fájlt – a te döntésed.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Tipp:** Használd a `SaveFormat.Docx`-et, ha explicit módon szeretnéd megadni, de a `Save(string)` automatikusan felismeri a formátumot a fájl kiterjesztéséből.

---

## Várható eredmény

Amikor megnyitod a `FormattedChart.docx` fájlt a Microsoft Wordben, a következőket kell látnod:

- A kördiagram első szelete **kifújt** kifelé.
- Ha a diagram fánk, a középső lyuk most a sugár **30 %**-át foglalja el.
- Bármely módosított adatpont a beállított új értékeket tükrözi.

![Exploded pie chart slice létrehozva Aspose.Words használatával C#-ban](exploded-pie-slice.png)

*Alt text:* **exploded pie chart slice** mutat egy kifújt szegmenst egy Word dokumentumban.

## Gyakori kérdések és szélhelyzetek

**Mi van, ha a diagram nem kör vagy fánk?**  
A kód ellenőrzi a `ChartType`-ot, mielőtt az `Exploded` vagy `HoleSize` beállításokat alkalmazná. Oszlop-, vonal- vagy területdiagramok esetén ezek a tulajdonságok egyszerűen nem léteznek, így a logika biztonságosan kihagyja őket.

**Tudok több szeletet is kiemelni?**  
Természetesen. Iterálj a `chart.PieChartData.Series[0].DataPoints` elemein, és állítsd be a `Exploded = true` értéket a kívánt indexeknél.

**Aggódom-e a kultúraspecifikus számformátumok miatt?**  
Az Aspose.Words numerikus értékeket double‑ként tárol, a helyi beállításoktól függetlenül, így nem kell aggódnod a vessző‑ és pont‑különbségek miatt.

**Mi a helyzet a fejlécben/láblécben beágyazott diagramokkal?**  
Használd a `doc.GetChildNodes(NodeType.Chart, true)` metódust az összes diagram lekéréséhez, majd vizsgáld meg minden node `ParentNode`‑ját, hogy hol helyezkedik el. Ugyanaz a kiemelési logika alkalmazandó.

## Következtetés

Most már egy stabil, másolás‑beillesztés‑kész megoldással rendelkezel a **explode pie chart slice** végrehajtásához Aspose.Words használatával C#-ban. Áttekintettük a teljes munkafolyamatot – a dokumentum betöltésétől, a diagram lekérésén, a szelet kiemelésén, **adjust doughnut hole size**-ra, **change chart data points**-ra, egészen a fájl mentéséig.

Nyugodtan kísérletezz: próbálj ki egy másik szelet kiemelését, állítsd be a lyuk méretét 45 %-ra, vagy frissíts egyszerre több adatpontot. Az Aspose.Words API-val ezek a módosítások könnyedek, és a változások azonnal láthatóak, amikor megnyitod a Word fájlt.

### Mi a következő?

- **Style the exploded slice** (változtasd a kitöltő színt, a szegélyt, vagy adj hozzá adatcímkét). Keresd a „Aspose.Words chart formatting” kifejezést.
- **Automate batch processing** több dokumentumra – iterálj egy mappán, emeld ki a szeleteket, és mentsd el az új verziókat.
- **Combine with Aspose.Slides**, ha ugyanazt a diagramot PowerPoint prezentációban is szükséged van.

Van még kérdésed a diagramok manipulálásával kapcsolatban, vagy mélyebben szeretnél belemerülni más diagramtípusokba? Hagyj egy megjegyzést alább, és jó kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Oszlopdiagram beszúrása Wordbe Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-column-chart/)
- [Egyszerű oszlopdiagram beszúrása Wordbe Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Területdiagram beszúrása Word dokumentumba | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}