---
category: general
date: 2026-07-29
description: Hogyan szerkesszünk diagramot egy Word-dokumentumban – megtanulhatja
  a diagramcímke pozíciójának módosítását, az oszlopdiagram címkéinek beállítását,
  a diagram adatcímkéinek módosítását, valamint a diagramcímke betűtípusának megváltoztatását.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: hu
lastmod: 2026-07-29
og_description: Hogyan szerkeszd gyorsan a diagramot a Wordben. Tanuld meg a diagramcímke
  pozíciójának módosítását, az oszlopdiagram címkéinek beállítását, a diagram adatcímkéinek
  módosítását, és a diagramcímke betűtípusának változtatását.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Hogyan szerkessz diagramot a Wordben – Címkék és betűtípus módosítása
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Hogyan szerkeszthető a diagram a Wordben: címke pozíciójának, betűtípusának
  és egyebek módosítása'
url: /hu/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szerkessz diagramot Word-ben: Címke pozíció, betűtípus és egyebek módosítása

A diagram szerkesztése egy Word-dokumentumban gyakori igény, ha a jelentéseid professzionális megjelenést szeretnél. Volt már nehézséged a **diagramcímke pozíciójának módosításával** vagy a címkék olvashatóvá tételével anélkül, hogy végtelen menükben keresgélnél? Nem vagy egyedül – a legtöbb fejlesztő ezzel a problémával szembesül a jelentésgenerálás automatizálásakor. Ebben az útmutatóban egy teljes, futtatható példán keresztül mutatjuk be, hogyan **állíthatod be a sávdiagram címkéit**, **módosíthatod a diagram adatcímkéit**, és **változtathatod a diagramcímke betűtípusát** C# és az Aspose.Words könyvtár segítségével.

## Mit fogsz megtanulni

- Betöltesz egy .docx fájlt, amely már tartalmaz egy sávdiagramot.  
- Lekéred az első diagram alakzatot, és hozzáférsz a adatcímke‑gyűjteményéhez.  
- **Megváltoztatod a diagramcímke pozícióját**, hogy a sávok tisztábbak legyenek.  
- **Módosítod a sávdiagram címkéinek** betűméretét a jobb olvashatóság érdekében.  
- Elmented a módosított dokumentumot a lemezre.  

Nincs szükség külső eszközökre, manuális UI‑lépésekre – csak tiszta kód, amely bármely .NET projektbe beilleszthető. A végére egy önálló megoldást kapsz, amelyet tucatnyi dokumentumban újra felhasználhatsz.

> **Előkövetelmények**  
> - .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑on is működik).  
> - Aspose.Words for .NET (elérhető a NuGet‑en keresztül).  
> - Egy Word‑fájl (`BarChart.docx`), amely már tartalmaz egy sávdiagramot.  

Ha valamelyik hiányzik, szerezd be most a legújabb Aspose.Words csomagot:

```bash
dotnet add package Aspose.Words
```

---

## Hogyan szerkessz diagramot: A diagram lekérése a Word-dokumentumból

Az első lépés a **diagram szerkesztése** objektumok esetén a dokumentum betöltése és a diagram alakzat megtalálása. Az Aspose.Words a diagramokat `Shape` csomópontokként kezeli, ezért a `GetChild`‑et a `NodeType.Shape`‑val használva lekérhetjük az első található diagramot.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Miért fontos:**  
> A `Chart` objektum közvetlen elérése nélkül elkerülheted a Word‑ben történő megnyitás és a címkék kézi beállításának terheit. Ez a **diagram adatcímkék módosítása** automatizálásának alappillére.

## Sávdiagram címkék beállítása: Diagramcímke pozíciójának módosítása

Miután megvan a `Chart` példány, iteráljunk a `DataLabelCollection`‑ön. A cél, hogy **megváltoztassuk a diagramcímke pozícióját**, így minden címke szépen a sáv alján helyezkedik el, ahelyett, hogy kényelmetlenül fölötte lebegne.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tipp:**  
> Az `InsideBase` jól működik függőleges sávdiagramoknál. Ha vízszintes sávdiagramot használsz, próbáld ki az `InsideEnd`‑et. A pozíciók kísérletezése egyszerű – csak futtasd újra a kódot, és nyisd meg a mentett dokumentumot.

## Diagramcímke betűtípusának módosítása: Betűméret beállítása az olvashatóságért

A túl kicsi betű a jelentés tisztaságának csendes gyilcse. A **diagramcímke betűtípusának módosításához** egyszerűen állítsd be a `Font.Size` tulajdonságot minden egyes `ChartDataLabel`‑nél. 9 pt‑re növeljük, ami a legtöbb nyomtatott jelentésnél ideális.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Miért csináljuk:**  
> A betűméret állítása a **diagram adatcímkék módosítása** legjobb gyakorlatai közé tartozik. A nagyobb betűk javítják a hozzáférhetőséget és csökkentik a kézi utófeldolgozás szükségességét.

## A módosított dokumentum mentése

A pozíciók és betűtípusok finomhangolása után a **diagram szerkesztése** utolsó lépése a változások mentése. Az Aspose.Words ezt egyetlen sorban megoldja.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Nyisd meg a `BarChartCustomLabels.docx` fájlt Wordben, és láthatod, hogy a címkék szorosan a sávok belsejében, tiszta 9 pt‑os betűtípussal jelennek meg. Nincs többé a kicsi számokra való pislogás.

---

## Teljes működő példa (Minden lépés egy fájlban)

Az alábbi kód egy komplett, futtatható konzolprogram, amely bemutatja a teljes folyamatot – a dokumentum betöltésétől a módosított verzió mentéséig. Másold be egy új .NET konzolprojektbe, és nyomd meg az **F5**‑öt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Várható kimenet** a program futtatásakor:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Nyisd meg a létrehozott fájlt, és láthatod, hogy a **sávdiagram címkék beállítása** a sávok belsejében, kényelmes betűmérettel történt.

---

## Gyakori kérdések és széljegyek

### Mi van, ha a dokumentum több diagramot tartalmaz?

A fenti kód az *első* diagramot veszi (`GetChild(NodeType.Shape, 0, true)`). Az összes diagram szerkesztéséhez cseréld le az egyetlen lekérést egy ciklusra:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Hogyan **változtassuk meg a diagramcímke betűtípusát** csak egy adott sorozatra?

Minden `ChartSeries` saját `DataLabelCollection`‑nal rendelkezik. Célzott sorozatot index alapján érhetsz el:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Működik ez kör vagy vonaldiagramokkal is?

Igen – a `ChartDataLabelPosition` támogatja az `InsideEnd`, `OutsideEnd` és `BestFit` értékeket. Egy kördiagramnál gyakran az `OutsideEnd` a legolvasóbb.

### Mi a helyzet a lokalizációval (pl. különböző tizedeselválasztókkal)?

Az Aspose.Words tiszteletben tartja a dokumentum helyi beállításait. Ha egy konkrét formátumot kell kényszeríteni, állítsd be a `label.NumberFormat`‑t a mentés előtt.

---

## Összefoglalás és következő lépések

Áttekintettük a **diagram szerkesztése** objektumok Word-dokumentumban lépésről‑lépésre: a fájl betöltése, a diagram lekérése, **diagramcímke pozíciójának módosítása**, **sávdiagram címkék beállítása**, **diagram adatcímkék módosítása**, majd végül **diagramcímke betűtípusának módosítása** a mentés előtt. A teljes példa termelés‑kész, és bármely automatizálási folyamatba beilleszthető.

Készen állsz a továbblépésre? Íme néhány ötlet:

- **Adj hozzá adatcímke színeket** (`dataLabel.Font.Color = Color.Blue;`).  
- **Jelenítsd meg az értékeket százalékban** (`dataLabel.NumberFormat = "0%";`).  
- **Készíts diagramokat programozottan** a meglévők betöltése helyett.  

Mindez ugyanazon API‑felületre épül, amelyet ma használtunk, így otthonosan fogod tudni alkalmazni.

Ha bármilyen problémába ütköztél, írj egy megjegyzést alább, vagy nézd meg az Aspose.Words dokumentációját a mélyebb diagram‑testreszabási lehetőségekért. Boldog kódolást, és élvezd a gyönyörűen címkézett diagramokat!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy további API‑funkciókat saját projektjeidben is könnyedén elsajátíthasd.

- [Diagram adatcímke testreszabása](/words/english/net/programming-with-charts/chart-data-label/)
- [Diagram adatcímke számformátumának beállítása](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Diagram adatcímke](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}