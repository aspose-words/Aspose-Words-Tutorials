---
category: general
date: 2026-09-08
description: Hozzon létre egy üres Word dokumentumot, és adjon hozzá diagramot a Wordhöz
  az Aspose.Words segítségével. Ismerje meg, hogyan szúrjon be radar diagramot, engedélyezze
  a fokozatokat, és mentse a fájlt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: hu
lastmod: 2026-09-08
og_description: Hozzon létre egy üres Word-dokumentumot, és adjon hozzá diagramot
  a Wordhöz az Aspose.Words használatával. Ez az útmutató bemutatja, hogyan szúrjon
  be radar diagramot, konfigurálja a tengelyeket, és mentse a dokumentumot.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Készítsen egy üres Word-dokumentumot, és adjon hozzá radar diagramot – lépésről
  lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Hogyan hozzunk létre üres Word-dokumentumot, és adjunk hozzá diagramot a Wordben
url: /hu/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre üres Word dokumentumot és adjunk hozzá diagramot a Wordhöz

Ha **üres Word dokumentumot** kell létrehoznod egy jelentéshez, sablonhoz vagy automatizált levél-összevonáshoz, ez az útmutató végigvezet a teljes folyamaton C#‑vel és az Aspose.Words‑szel. Megtanulod, hogyan **adj diagramot a Wordhöz**, különösen hogyan **illessz be radar diagramot**, kapcsolj be fokozatokat, és mentsd el az eredményt .docx fájlként.

Ez a tutorial mindent lefed a projekt beállításától a végső ellenőrzési lépésig. A végére egy újrahasználható kódrészletet kapsz, amely bármely .NET alkalmazásba beilleszthető. Nem szükséges előzetes tapasztalat az Aspose.Words‑szel, de alapvető C# ismeretekkel és egy friss .NET SDK‑val kell rendelkezned.

## Előfeltételek

- .NET 6.0 SDK vagy újabb  
- Aspose.Words for .NET (NuGet csomag `Aspose.Words`)  
- IDE, például Visual Studio 2022 vagy VS Code  
- Írási jogosultság a mappához, ahová a dokumentumot menteni fogod  

A könyvtárat a következő paranccsal telepítheted:

```bash
dotnet add package Aspose.Words
```

## 1. lépés: Üres Word dokumentum létrehozása

Az első lépés a **üres Word dokumentum** memóriában való **létrehozása**. A `Document` osztály képviseli az egész fájlt, míg a `DocumentBuilder` egy folyékony API‑t biztosít a tartalom hozzáadásához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

A `Document` üresen indul, így egy tiszta vászon áll rendelkezésedre a diagram elhelyezéséhez. A dokumentum ebben a szakaszban üresen tartása megkönnyíti a kód újrahasználatát különböző sablonokhoz.

## 2. lépés: Diagram hozzáadása a Wordhöz

Ezután **diagramot adunk a Wordhöz** az `InsertChart` hívásával. A metódus megköveteli a diagram típusát és a kívánt méreteket pontban (1 pont = 1/72 hüvelyk).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

A `ChartType.Radar` azt mondja az Aspose.Words‑nek, hogy radiális diagramot generáljon, ami ideális a többváltozós adatok körkörös elrendezésben történő megjelenítéséhez. A méretértékek (400 × 300) a legtöbb álló oldalhoz jól illeszkednek, de igény szerint módosíthatók.

## 3. lépés: Radar diagram beillesztése és fokozatok beállítása

Most **beillesztünk egy radar diagramot**, és engedélyezzük a fokozatokat (jelölőket) mind a kategória (X), mind az érték (Y) tengelyen. A fokozatok javítják az olvashatóságot, mivel pontos pozíciókat mutatnak minden adatponthoz.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

A `HasGraduations` `true`‑ra állítása jelölőket rajzol a tengelyekre. Az opcionális `GraduationStep` szabályozza a jelölők közti távolságot a radiális tengelyen; a 10-es lépés azt jelenti, hogy minden 10 fokban egy jelölő jelenik meg.

### Profi tipp
Ha adatcímkéket szeretnél megjeleníteni, hívd meg a `radarChart.Series[0].HasDataLabel = true;` kódot. Ez a numerikus értéket helyezi el minden pont mellett, ami prezentációkhoz hasznos.

## 4. lépés: Diagram feltöltése mintaadatokkal (opcionális)

Egy adat nélküli radar diagram láthatatlan. Az alábbi gyors módszerrel adhatunk hozzá egy sor mintaértéket. Ezt a blokkot saját adatforrásoddal helyettesítheted.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Minden `Add` hívás egy pontot szúr be a sorozatba. A pontok sorrendje megfelel a kör körüli szögi pozícióknak.

## 5. lépés: A diagramot tartalmazó dokumentum mentése

Végül mentsük a dokumentumot a lemezre. A `Save` metódus automatikusan kiírja a .docx fájlt, megőrizve a diagramot és minden formázást.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

A program futtatása **üres Word dokumentumot** hoz létre, amely most már egy teljesen működő radar diagramot tartalmaz. Nyisd meg a fájlt a Microsoft Wordben, hogy lásd az eredményt.

![Radar chart in Word document](radar_chart.png){alt="Radar diagram beillesztve egy üres Word dokumentumba"}

## Gyakori variációk és szélhelyzetek

| Helyzet | Mit kell módosítani |
|-----------|----------------|
| **Eltérő diagramméret** | Állítsd be az `InsertChart` szélesség/magasság paramétereit. |
| **Más diagramtípusok** | Cseréld le a `ChartType.Radar`‑t `ChartType.Column`, `ChartType.Pie` stb.-re, és tartsd meg a fokozatlogikát. |
| **Mentés stream‑be** | Használd a `document.Save(Stream, SaveFormat.Docx)` metódust. |

## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}