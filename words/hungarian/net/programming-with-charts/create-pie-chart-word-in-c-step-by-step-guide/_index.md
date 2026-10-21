---
category: general
date: 2026-08-07
description: Készíts gyorsan kördiagramot C#-ban. Tanuld meg, hogyan illessz be kördiagramot,
  adj hozzá adatcímkéket a kördiagramhoz, jelenítsd meg a százalékos diagramot, és
  testreszabhatod a diagram adatcímkéit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: hu
lastmod: 2026-08-07
og_description: Készítsen kördiagramot Word-ben C#-ban az Aspose.Words segítségével.
  Ez az útmutató bemutatja, hogyan illesszen be kördiagramot, adjon hozzá adatcímkéket
  a kördiagramhoz, és jelenítse meg a százalékos diagramot, miközben testre szabja
  a diagram adatcímkéit.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Kördiagram szó létrehozása C#-ban – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Kördiagram létrehozása C#-ban – lépésről lépésre útmutató
url: /hu/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create pie chart word in C# – step‑by‑step guide

Ha **create pie chart word** dokumentumokat kell készítenie C#‑ban, ez az útmutató egy teljes, azonnal futtatható megoldást nyújt. Megmutatjuk, hogyan **insert pie chart**, **add data labels pie**, és **show percentage chart**, miközben **customize chart data labels**‑t alkalmaz a professzionális megjelenés érdekében.

A diagramok programozott generálása megkímél a kézi szerkesztéstől, különösen akkor, ha jelentéseket vagy irányítópultokat kell automatikusan előállítani. Az alábbi szakaszokban mindent megtanul, ami ahhoz szükséges, hogy egy teljesen felcímkézett kördiagramot ágyazzon be egy Word‑fájlba az Aspose.Words for .NET segítségével.

## Prerequisites and setup

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* .NET 6.0 SDK vagy újabb telepítve.  
* Érvényes Aspose.Words for .NET licenc (vagy ideiglenes értékelő kulcs).  
* Visual Studio 2022 (vagy bármely C#‑ot támogató IDE).  

Adja hozzá az Aspose.Words NuGet csomagot a projektjéhez:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Ha sok diagramot kell generálnia, engedélyezze a **Free‑Form Drawing** módot (`DocumentBuilder.UseFreeFormDrawing = true`) a jobb teljesítmény érdekében.

## Create pie chart word with Aspose.Words

Az első nagy lépés egy üres Word‑dokumentum és egy `DocumentBuilder` létrehozása. Ez az objektum hajtja végre az összes további beillesztést.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: `Document` képviseli a teljes `.docx` fájlt, míg a `DocumentBuilder` egy folyékony API‑t biztosít bekezdések, táblázatok és diagramok hozzáadásához. Egy tiszta dokumentummal kezdve elkerülhető a rejtett formázás, amely befolyásolhatná a diagram elrendezését.

## Insert pie chart into the document

Most elhelyezünk egy kördiagramot a kívánt méretben. Az `InsertChart` metódus egy `Chart` objektumot ad vissza, amelyet tovább konfigurálhatunk.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Why this matters*: A `ChartType.Pie` jelző azt mondja az Aspose.Words‑nek, hogy kördiagramot generáljon. A szélesség (`400`) és magasság (`300`) pontban van megadva, így pontosan szabályozhatja a vizuális lábnyomot.

## Populate the chart with data

Egy kördiagramnak legalább egy numerikus értékekből álló sorozatra van szüksége. Itt három kategóriát adunk hozzá: “Apples”, “Bananas”, és “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Why this matters*: Minden `AddCategory` hívás egy szeletet hoz létre. A numerikus érték határozza meg a szelet méretét, míg a címke a kategória neve, amely akkor jelenik meg, amikor az adatcímkék be vannak kapcsolva.

## Add data labels pie and show percentage chart

Ahhoz, hogy a diagram informatív legyen, engedélyezzük az adatcímkéket, kívülre helyezzük őket a szeletekhez, és kérjük az Aspose.Words‑t, hogy jelenítse meg a kategória nevét és a százalékot is.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Why this matters*: A `Position` `OutsideEnd`‑re állítása javítja az olvashatóságot, különösen kis szeletek esetén. A `ShowCategoryName` és `ShowPercentage` engedélyezése teljesíti a **show percentage chart** követelményt és kielégíti a **add data labels pie** célt.

## Customize chart data labels further (optional)

Lehet, hogy meg szeretné változtatni a betűtípust, hozzáadni egy vezető vonalat, vagy elrejteni a legendát. Az alábbi kódrészlet a gyakori testreszabásokat mutatja be:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Why this matters*: A címke megjelenésének testreszabása biztosítja, hogy a diagram illeszkedjen a dokumentum stílusirányelveihez. A legenda eltávolítása csökkenti a vizuális zajt, ha az adatcímkék már közlik ugyanazt az információt.

## Save the document with the customized chart

Végül írja a dokumentumot a lemezre. Válasszon egy olyan útvonalat, amelyre írási jogosultsága van.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Amikor megnyitja a `ChartWithCustomLabels.docx` fájlt a Microsoft Word‑ben, egy kördiagramot fog látni, ahol minden szelet a kategória nevével és százalékával van felcímkézve, a szelet kívül helyezkedik el, és a saját betűtípus‑beállításokkal van formázva.

### Expected output

| Slice   | Value | Percentage | Label shown in Word |
|---------|-------|------------|---------------------|
| Apples  | 40    | 40 %       | Apples – 40 %       |
| Bananas | 35    | 35 %       | Bananas – 35 %      |
| Cherries| 25    | 25 %       | Cherries – 25 %     |

A diagram a lenti illusztrációhoz hasonlóan kell, hogy kinézzen:

![Word-dokumentum, amely pie chart-ot mutat százalékos címkékkel minden szelet külső oldalán](pie-chart-word.png "Create pie chart word példa")

*Image alt text includes the primary keyword for SEO.*

## Handling multiple series and edge cases

Az alappélda egyetlen sorozatot használ, ami tipikus egy kördiagram esetén. Ha több sorozatot kell megjelenítenie (például két év összehasonlítását), akkor:

1. Hívja meg a `chart.Series.Add()`‑t minden további sorozathoz.  
2. Győződjön meg róla, hogy minden sorozat ugyanazokat a kategóriákat használja; ellenkező esetben az Aspose.Words `ArgumentException`‑t dob.  
3. Opcionálisan állítsa be a `labels.ShowSeriesName = true`‑t a szeletek megkülönböztetéséhez.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Ha több sorozat létezik, a diagram automatikusan **clustered pie**‑ként (más néven „pie of pies”) jelenik meg. Ellenőrizze a kimenetet, hogy a címkék olvashatóak maradnak-e.

## Common pitfalls and how to avoid them

| Problem | Cause | Fix |
|---------|-------|-----|
| Labels overlap slices | Small chart area or many categories | Increase chart dimensions (`InsertChart(width, height)`) or switch `Position` to `InsideEnd`. |
| Percentages don’t add up to 100 % | Rounding errors in data | Use `labels.ShowPercentage = true` (Aspose.Words automatically normalizes). |
| Chart appears blank in Word | Missing license or evaluation timeout | Ensure a valid Aspose.Words license is loaded before creating the document. |
| Font colors differ from Word theme | Custom font set in code | Remove custom font settings or match Word’s theme colors (`System.Drawing.Color.Black`). |

## Full source code (runnable)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

A program futtatása `ChartWithCustomLabels.docx`‑et hoz létre, amely egy **create pie chart word** példát tartalmaz, és megfelel a tutorialban felsorolt összes követelménynek.

## Conclusion

Most már tudja, hogyan kell **create pie chart word** dokumentumokat készíteni C#‑ban az Aspose.Words segítségével. Az útmutató lefedte a kördiagram beillesztését, a **add data labels pie**, a **show percentage chart**, és a **customize chart data labels** lépéseket, hogy professzionális, adat‑vezérelt Word‑fájlt kapjon.  

Innen tovább felfedezheti a kapcsolódó témákat, például **insert pie chart** meglévő bekezdésekbe, **bar** vagy **line** diagramok generálását, vagy a jelentések kötegelt automatikus létrehozását változó adatkészletekkel. Kísérletezzen különböző címke‑pozíciókkal, betűtípus‑stílusokkal és több‑sorozatos beállításokkal, hogy a kimenetet a saját jelentési igényeihez igazítsa.

Happy charting!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}