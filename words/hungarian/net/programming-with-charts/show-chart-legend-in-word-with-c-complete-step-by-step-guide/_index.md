---
category: general
date: 2026-06-02
description: Mutassa a diagrammagyarázatot egy Word-dokumentumban C#-vel. Tanulja
  meg, hogyan adjon hozzá magyarázatot, alkalmazzon előre beállított diagramstílust,
  és testreszabja a Word-diagramok megjelenését percek alatt.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: hu
og_description: A diagram legenda megjelenítése egy Word-dokumentumban azonnal. Ez
  az útmutató végigvezet a legenda hozzáadásán, az előre beállított diagramstílus
  alkalmazásán és a szélhelyzetek kezelésén.
og_title: Diagrammagyarázat megjelenítése Wordben – Teljes C# oktató
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Diagrammagyarázat megjelenítése Wordben C#‑val – Teljes lépésről‑lépésre útmutató
url: /hu/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diagram jelmagyarázat megjelenítése Word-ben C#‑val – Teljes lépésről‑lépésre útmutató

Gondolkodtál már **arról, hogyan lehet jelmagyarázatot hozzáadni** egy Word‑dokumentumban lévő diagramhoz? Nem vagy egyedül. Sok jelentésben a hiányzó jelmagyarázat titokzatosá teszi az adatokat, és ennek javítása nem lehet fejfájás.

Ebben az útmutatóban **megmutatjuk, hogyan jeleníthető meg a diagram jelmagyarázata** egy Word‑fájlban az Aspose.Words for .NET segítségével, alkalmazunk egy előre definiált diagramstílust, és biztosítjuk, hogy a jelmagyarázat pontosan ott jelenjen meg, ahol szükséges. A végére egy kész, futtatható példát kapsz, amelyet bármely C# projektbe beilleszthetsz.

## Mit fed le ez az útmutató

Áttekintjük a teljes munkafolyamatot:

1. Betöltünk egy meglévő *.docx* fájlt, amely már tartalmaz egy diagramot.  
2. Lekérjük az első diagramot (vagy bármelyik diagramot, amelyet célozni szeretnél).  
3. **Alkalmazunk egy előre definiált diagramstílust**, hogy a megjelenés professzionális legyen.  
4. **Megjelenítjük a diagram jelmagyarázatát**, a jobb oldalra helyezzük, és kezeljük a speciális eseteket, például a Waterfall diagramokat.  
5. Elmentjük a módosított dokumentumot.

Nincs szükség külső eszközökre, nincs kézi UI‑manipuláció – csak tiszta kód. Az egyetlen előfeltétel az Aspose.Words NuGet csomag (23.10 vagy újabb) hivatkozása és a C# alapvető ismerete.

---

## Előkövetelmények

- .NET 6.0 vagy újabb (a minta .NET Framework 4.7.2‑vel is működik).  
- Aspose.Words for .NET könyvtár telepítve (`Install-Package Aspose.Words`).  
- Egy Word‑fájl (`input.docx`), amely már tartalmaz legalább egy diagramot.  
- Visual Studio, Rider vagy bármely kedvenc IDE.

---

## 1. lépés: A projekt beállítása és a dokumentum betöltése

Először hozz létre egy konzolos alkalmazást (vagy integráld a kódot egy meglévő projektbe). Add hozzá a `using` direktívákat és töltsd be a `.docx` fájlt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Miért fontos:** A dokumentum betöltése az alap. `Document` példány nélkül nem érheted el az Aspose.Words által biztosított diagramobjektumokat.

---

## 2. lépés: A céldiagram lekérése

A diagramok a dokumentumfa csomópontjaiként tárolódnak. A `GetChild` metódus mély keresést végez, így az első diagramot bármely helyen (fejléc, törzs, lábléc stb.) le tudjuk kérni.

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Tipp:** Ha több diagramod van, változtasd meg a `0` indexet `1`, `2`, … értékre, vagy iterálj a `doc.GetChildNodes(NodeType.Chart, true)` segítségével.

---

## 3. lépés: Előre definiált vizuális stílus alkalmazása

Egy jól kinéző diagram gyakran egy stílussal kezdődik. Az Aspose.Words több tucat beépített stílussal érkezik; a `ChartStyle.Style12` egy tiszta, modern opció.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Hogyan működik:** A `Style` tulajdonság a Word UI‑jában látható beépített diagramstílusokra mutat. Egy előre definiált stílus használata megspórolja a színek, betűtípusok és jelölők kézi beállítását.

---

## 4. lépés: A jelmagyarázat engedélyezése és elhelyezése

Most jön a főszereplő – **diagram jelmagyarázat megjelenítése**. Bekapcsoljuk a jelmagyarázatot, majd a diagram jobb oldalához rögzítjük.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Miért jobb oldal?** A jelmagyarázat jobb oldali elhelyezése szélesebb adatterületet biztosít, ami különösen hasznos oszlop- vagy sávdiagramoknál.

---

## 5. lépés: Waterfall diagramok kezelése (különleges eset)

A Waterfall diagramok kicsit másképp viselkednek; a jelmagyarázat alapértelmezés szerint rejtve lehet. Az alábbi védelmi feltétel biztosítja, hogy a jelmagyarázat látható legyen, ha a diagram típusa Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Külön eset megjegyzés:** Néhány régebbi Word‑verzió figyelmen kívül hagyja a `HasLegend` beállítást Waterfall diagramoknál, ezért a `Legend.Show` explicit beállítása garantálja a láthatóságot.

---

## 6. lépés: A módosított dokumentum mentése

Végül írjuk vissza a változtatásokat a lemezre. Felülírhatod az eredeti fájlt, vagy létrehozhatsz egy újat.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

A program futtatása `output.docx`‑t hoz létre, amelynek jobb oldalán látható a jelmagyarázat, a `Style12` stílussal. Nyisd meg a fájlt Word‑ben a végeredmény ellenőrzéséhez.

---

## Teljes működő példa (az összes lépés egyben)

Az alábbi kódrészlet a kész, futtatható megoldást tartalmazza. Másold be a `Program.cs`‑be (vagy bármely C# fájlba), és állítsd be a fájlútvonalakat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Várható kimenet:** Az `output.docx` megnyitásakor az eredeti diagram jobb‑igazított jelmagyarázattal, a modern `Style12`‑vel jelenik meg. Minden adat sor egyértelműen fel van címkézve, így a diagram azonnal érthető.

---

## Gyakran Ismételt Kérdések (GYIK)

### Hogyan adhatok jelmagyarázatot egy konkrét diagramhoz (nem az elsőhöz)?

Cseréld le a `0` indexet a `GetChild(NodeType.Chart, 0, true)`‑ben a cél diagramod null‑alapú pozíciójára, vagy iterálj az összes diagramcsomóponton:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Elhelyezhetem a jelmagyarázatot alul a jobb oldal helyett?

Természetesen. Csak módosítsd a `LegendPosition` enumerációt:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Mi van, ha a diagram már rendelkezik jelmagyarázattal, de el akarom rejteni?

Állítsd a `HasLegend` értékét `false`‑ra:

```csharp
chart.HasLegend = false;
```

### Működik ez Word 2010, 2016 és újabb verziókkal?

Igen. Az Aspose.Words elrejti a mögöttes Word‑verziót, így ugyanaz a kód minden modern .docx fájlon működik.

---

## Pro tippek és gyakori buktatók

- **Pro tipp:** Stílus alkalmazása után is módosíthatod az egyes elemeket (színek, adatcímkék) a `Chart.Series` gyűjteményen keresztül. A stílus szilárd alapot ad.
- **Figyelmeztetés:** Ha a diagram egy táblázatcellában van, a jelmagyarázat szorult lehet. Fontold meg a diagram méretének (`chart.Width`, `chart.Height`) növelését a jelmagyarázat elhelyezése előtt.
- **Teljesítmény megjegyzés:** Nagy dokumentumok (százak MB) betöltése memóriaigényes lehet. Használd a `LoadOptions`‑t `LoadFormat.Docx`‑el, ha csak diagramkezelésre van szükséged, így csökkentheted a terhelést.

---

## Következő lépések

Most, hogy tudod **hogyan adj hozzá jelmagyarázatot** és **alkalmazz előre definiált diagramstílust** Word‑ben, érdemes tovább mélyedni:

- **Egyedi diagramszínek** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Adatcímke formázás** (`chart.Series[i].HasDataLabel = true`).  
- **Diagram képként való exportálása** (`chart.ToImage()`), ami hasznos más helyeken való beágyazáshoz.  

Ezek a témák ugyanazon objektummodellre épülnek, így a tanulási görbe enyhe marad.

---

## Összegzés

Bemutattuk, hogyan valósítható meg egy tiszta, vég‑től‑végig megoldás a **diagram jelmagyarázat megjelenítésére** Word‑dokumentumban C#‑val. A dokumentum betöltésével, a diagram lekérésével, egy előre definiált stílus alkalmazásával, a jelmagyarázat engedélyezésével és a Waterfall sajátosságok kezelésével egy kifinomult diagramot kapsz, amely minden üzleti jelentéshez tökéletes.  

Nyugodtan kísérletezz más `ChartStyle` értékekkel vagy jelmagyarázat‑pozíciókkal – az adataid megérdemlik a legjobb megjelenítést. Ha elakadsz, hagyj kommentet alább; jó kódolást!

## Mit tanulj meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy könnyedén elsajátíthasd az API további funkcióit és alternatív megvalósítási módokat a saját projektjeidben.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}