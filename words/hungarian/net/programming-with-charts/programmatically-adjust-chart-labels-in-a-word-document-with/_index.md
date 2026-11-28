---
category: general
date: 2026-10-13
description: Tanulja meg, hogyan állíthatja programozottan a diagramcímkéket egy Word-dokumentumban
  C#-vel. Ez az útmutató az Aspose.Words diagrammanipulációt és a címkeigazítást tárgyalja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: hu
lastmod: 2026-10-13
og_description: Programozottan állítsa be a diagramcímkéket egy Word-dokumentumban
  C#-vel. Kövesse ezt a teljes útmutatót a címke elhelyezésének, igazításának és egyéb
  beállításainak módosításához.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Programozottan állítsa be a diagramcímkéket a Wordben – C# lépésről‑lépésre
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Programozottan állítsa be a diagramcímkéket egy Word-dokumentumban C#-val
url: /hu/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programozott módon állítsa be a diagramcímkéket egy Word dokumentumban C#-al

Ha **programozott módon szeretné módosítani a diagramcímkéket** egy Word dokumentumban, ez az útmutató pontosan megmutatja, hogyan teheti ezt meg C#-al. Akár jelentéseket generál, irányítópultokat automatizál, vagy sablonokat testreszab, egy teljes, futtatható példát láthat, amely megváltoztatja egy .docx fájlban lévő diagram címkéinek elhelyezését és igazítását.

Megtanulja, hogyan használja az **Aspose.Words diagramkezelési** technikákat, hogyan kezeljen több sorozatot, és hogyan kerüljön el gyakori buktatókat a **C# diagram adatcímke** objektumokkal dolgozva.

## Előfeltételek

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik a következőkkel:

* .NET 6.0 (vagy újabb) telepítve  
* Visual Studio 2022 (vagy bármely C# IDE)  
* Az **Aspose.Words for .NET** NuGet csomag (`Install-Package Aspose.Words`)  
* Egy Word dokumentum (`input.docx`), amely legalább egy diagramot tartalmaz  

Ezek az elemek szükségesek a **Word dokumentum diagram példa** módosításához.

## 1. lépés: A projekt beállítása és névtér importálása

Hozzon létre egy új konzolos projektet, és adja hozzá a szükséges `using` direktívákat. Ez előkészíti a környezetet a **programozott módon diagramcímkék beállításához**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Miért ez a lépés?*  
A dokumentum betöltése hozzáférést biztosít a belső **Word dokumentum diagram példa** fához, ahol a diagramok alakzatcsomópontokként vannak tárolva.

## 2. lépés: Az első diagram alakzat megtalálása

A diagramok `Shape` csomópontokként vannak tárolva. Az alábbi kód lekéri a dokumentumban lévő első diagramot, amely a címke módosításaink célpontja.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Miért ez a lépés?*  
A `GetChild` metódus rekurzívan (`true`) keres, és visszaadja az első `Shape` típusú csomópontot. A `Chart` típusra való átkonvertálás lehetővé teszi a diagram‑specifikus API használatát.

## 3. lépés: A módosítandó adatcímke elérése

Minden diagram sorozatnak van egy adatcímke-gyűjteménye. Egy egyszerű diagram esetén az első címke gyakran elegendő. Az alábbi kód megmutatja, hogyan érhető el.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Miért ez a lépés?*  
A `ChartSeries` egy pontsorozatot képvisel. A `DataLabelCollection` tartalmazza az adott sorozat címkéit, lehetővé téve a pontos elhelyezés és igazítás szabályozását.

## 4. lépés: Címke elhelyezésének és igazításának módosítása

Most **programozott módon állítjuk be a diagramcímkéket** a pozíció, a vízszintes igazítás és a függőleges igazítás beállításával. Ezek a tulajdonságok megfelelnek a Word felhasználói felületén látható beállításoknak.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Miért ezek a beállítások?*  

* `OutsideEnd` a címkét közvetlenül a sáv vagy oszlop végén kívül helyezi el, javítva az olvashatóságot.  
* `HorizontalAlignment.Center` középre igazítja a szöveget a pont felett, míg `VerticalAlignment.Top` a címke felső szélét a adatponthoz igazítja, megakadályozva a többi elemmel való átfedést.

### Praktikus tipp
Ha egy diagram több sorozattal rendelkezik, iteráljon a `chart.Series`-en, és alkalmazza ugyanazokat a beállításokat minden `DataLabelCollection`-re. Ez egységes megjelenést biztosít az egész diagramon.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## 5. lépés: A módosított dokumentum mentése

A címkék beállítása után mentse a változtatásokat egy új fájlba. Ezzel befejeződik a **diagramcímke pozíció módosítása** folyamata.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Amikor megnyitja a `output.docx` fájlt, láthatja, hogy minden diagramcímke a saját adatpontja külső végére került, vízszintesen középre, függőlegesen felülre igazítva.

## Szélsőséges esetek és variációk

| Helyzet | Mire figyeljen | Ajánlott megközelítés |
|-----------|-------------------|----------------------|
| **Több diagram** ugyanabban a dokumentumban | A `GetChild` csak az első diagramot adja vissza. | Használja a `doc.GetChildNodes(NodeType.Shape, true)` metódust az összes diagram alakzat bejárásához. |
| **Sorozat adatcímkék nélkül** | A `DataLabelCollection` üres lehet. | Ellenőrizze a `series.HasDataLabels` értéket, mielőtt hozzáférne a gyűjteményhez. |
| **Különböző diagramtípusok** (pie, line, scatter) | Nem minden `DataLabelPosition` érték érvényes. | Használja a `DataLabelPosition.Auto` beállítást olyan diagramoknál, amelyek automatikusan választják a legjobb elhelyezést. |
| **Lokalizáció** | Az igazítási konstansok nyelvfüggetlenek, de a megjelenített szövegnek jobbról balra irányú támogatásra lehet szüksége. | Állítsa be a `dataLabel.TextDirection` értéket, ha RTL nyelveket használ. |

## Teljes, futtatható példa

Az alábbi teljes programot másolja, illessze be, és futtassa. Cserélje le a `YOUR_DIRECTORY`-t egy valós mappára.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Várt eredmény:** A `output.docx` megnyitásakor minden diagramcímke a adatpont külső végén, vízszintesen középre, függőlegesen felülre igazítva jelenik meg – pontosan a **programozott módon diagramcímkék beállítása** által elérni kívánt hatás.

## Összegzés

Most már tudja, hogyan **programozott módon állítsa be a diagramcímkéket** egy Word dokumentumban C#-al. A bemutató lefedte:

* Dokumentum betöltése **Aspose.Words diagramkezeléssel**  
* **C# diagram adatcímke** elérése  
* **Diagramcímke pozíció módosítása** és igazítása  
* Fájl mentése és gyakori szélsőséges esetek kezelése  

Innen tovább felfedezheti a haladóbb forgatókönyveket, például a címke betűtípusának testreszabását, feltételes formázás hozzáadását, vagy több diagram egyszerre történő frissítését kötegelt folyamatban. Kísérletezzen a különböző `DataLabelPosition` beállításokkal, hogy megtalálja a jelentéseihez leginkább illő stílust.

---

*Készen áll arra, hogy fejlessze az automatizált jelentéskészítési folyamatát? Próbáljon meg egyedi számformátumokat hozzáadni a címkékhez, vagy exportálja a diagramot képként PDF-ekhez való felhasználáshoz.*


## Mit érdemes legközelebb megtanulni?


Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}