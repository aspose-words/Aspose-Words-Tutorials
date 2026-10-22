---
category: general
date: 2026-07-20
description: Adj hozzá kördiagram címkéket az Aspose.Words for .NET segítségével.
  Tanulja meg, hogyan módosíthatja a kördiagram címkéit, hogyan jelenítheti meg a
  százalékos címkéket, és hogyan frissítheti gyorsan a diagram sorozat címkéit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: hu
lastmod: 2026-07-20
og_description: Adj hozzá kördiagramcímkéket C#-ban az Aspose.Words segítségével.
  Tanuld meg a kördiagramcímkék módosítását, a százalékcímkék megjelenítését, és a
  diagram sorozatcímkéinek frissítését néhány lépésben.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Kördiagram címkék hozzáadása C#-ban – Aspose.Words teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Kördiagram címkék hozzáadása C#-ban az Aspose.Words használatával – Teljes
  útmutató
url: /hu/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#‑os kördiagramcímkék hozzáadása Aspose.Words‑szel – Teljes útmutató

Szükséged van **kördiagramcímkék** hozzáadására egy Word‑dokumentumba C#‑ban? Az Aspose.Words segítségével egyszerűen **módosíthatod a kördiagramcímkéket** és **megjelenítheted a kördiagram százalékos értékeit** közvetlenül a fájlban – anélkül, hogy manuálisan kellene szerkesztened a Word‑ben.  

Ebben az útmutatóban lépésről‑lépésre bemutatjuk, hogyan **jelenítsd meg a százalékcímkéket**, hogyan helyezd el őket, és akár **frissítsd a diagram sorozatcímkéit** dinamikus adatokhoz. A végére egy újrahasználható kódrészletet kapsz, amelyet bármely .NET projektbe beilleszthetsz.

> **Gyors előzetes:** A leírás követése után a mentett `.docx` megnyitásakor egy kördiagramot látsz, ahol minden szelet a saját százalékával van felcímkézve, a szelet külső oldalán a legjobb olvashatóság érdekében.

---

## Amire szükséged lesz

- **Aspose.Words for .NET** (a legújabb verzió 2026‑ig). NuGet‑ről telepíthető: `Install-Package Aspose.Words`.
- Egy **Word‑dokumentum**, amely már tartalmaz kör‑ vagy gyűrűdiagramot (nevezzük `Chart.docx`‑nek).
- Alapvető ismeretek **C#‑ról** és a Visual Studio‑ról (vagy a kedvenc IDE‑dról).

Ennyi – nincs szükség extra könyvtárakra, COM‑interfészre, csak tiszta menedzselt kódra.

---

## Kördiagramcímkék hozzáadása – Teljes megvalósítás

Az alábbi **teljes, futtatható** C# konzolprogram betölti a dokumentumot, módosítja az első kördiagramot, és elmenti az eredményt. Minden sor meg van kommentálva, hogy megértsd **miért** csináljuk, ne csak **mit**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Várt eredmény

Nyisd meg a `ChartWithCustomLabels.docx` fájlt a Microsoft Word‑ben. A kördiagram **százalékcímkékkel lesz ellátva, amelyek a szeletek kívül helyezkednek el**. A címkék például „35 %”, „20 %” formában jelennek meg, így a diagram azonnal érthető.

---

## Kördiagramcímkék módosítása: elhelyezés és formázás

Ha csak **kördiagramcímkéket szeretnél módosítani** százalékok megjelenítése nélkül, állítsd be a `Position` tulajdonságot az alábbiak egyikére:

| Position Enum | Vizualizációs hatás |
|---------------|----------------------|
| `InsideEnd`   | A címkék a szelet belsejében, a szélén helyezkednek el. |
| `Center`      | A címkék a szelet közepén jelennek meg (kis diagramoknál hasznos). |
| `OutsideEnd`  | A címkék a szelet kívül, vezető vonallal kapcsolódnak (alapértelmezett). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Pro tipp:** `OutsideEnd` a legtöbb szelettel rendelkező diagramoknál a legjobb, mert elkerüli a szöveg átfedését.

---

## Százalékcímkék megjelenítése egy kördiagramon

A `ShowPercentage` egy **logikai jelző**. `true` értékre állítva az Aspose.Words kiszámítja minden szelet hozzájárulását a mögöttes adatforrás alapján.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Kombinálhatod a `ShowValue`‑val is, ha egyszerre szeretnéd látni a nyers számokat **és** a százalékokat:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Ha mindkét jelző be van kapcsolva, a címke például „45 % (120)” formában jelenik meg.

---

## Diagram sorozatcímkék frissítése dinamikus adatokhoz

Gyakran kell diagramokat generálni „on the fly” – például havi eladások vagy felmérési eredmények. A **diagram sorozatcímkék** programozott frissítéséhez módosítsd a `Series` gyűjteményt, mielőtt a adatcímkéket kezelnéd:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Ez a kódrészlet bemutatja, hogyan **frissítheted a diagram sorozatcímkéit** bármely sorozatra, nem csak az elsőre. Hasznos, ha olyan jelentéseket készítesz, amelyek valós és előrejelzett adatokat egyaránt tartalmaznak.

---

## Szélsőséges esetek és gyakori buktatók

| Helyzet | Mire figyelj | Megoldás |
|-----------|-------------------|-----|
| **A diagram nem kör/gyűrű** | `Position` esetleg nem jár vizuális változással. | Ellenőrizd, hogy `chart.Type` értéke `ChartType.Pie` vagy `ChartType.Doughnut`. |
| **Nem található diagram** | `GetChild` `null`‑t ad vissza. | Adj hozzá egy védelmi ágat (lásd a kódban) és naplózz egy hasznos üzenetet. |
| **Régebbi Word‑verzió** | Egyes címkefunkciók figyelmen kívül maradhatnak. | Ments `.docx`‑ként (a modern formátumot), hogy teljes támogatást kapj. |
| **Sok szelet** | A címkék átfedhetnek még `OutsideEnd` esetén is. | Csökkentsd a szeletek számát vagy növeld a diagram méretét. |

---

## Teljes működő példa (másold be)

Az alábbi **teljes program** beilleszthető egy új konzolprojektbe. Csak cseréld ki a `YOUR_DIRECTORY`‑t arra a mappára, ahol a `Chart.docx` található.



## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódnak ehhez a leíráshoz, és tovább építik a bemutatott technikákat. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy könnyedén elsajátíthasd az API további funkcióit, illetve alternatív megvalósítási módokat a saját projektjeidben.

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}