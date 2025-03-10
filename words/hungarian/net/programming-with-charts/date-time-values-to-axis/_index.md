---
title: Adja hozzá a dátum és idő értékeket a diagram tengelyéhez
linktitle: Adja hozzá a dátum és idő értékeket a diagram tengelyéhez
second_title: Aspose.Words Document Processing API
description: Ebből az átfogó, lépésenkénti útmutatóból megtudhatja, hogyan adhat dátum- és időértékeket a diagram tengelyéhez az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adja hozzá a dátum és idő értékeket a diagram tengelyéhez

## Bevezetés

diagramok dokumentumokban történő létrehozása hatékony módja lehet az adatok megjelenítésének. Az idősorok adatainak kezelésekor a dátum és az idő értékek hozzáadása a diagram tengelyéhez elengedhetetlen az egyértelműség érdekében. Ebben az oktatóanyagban végigvezetjük a dátum- és időértékek diagram tengelyéhez való hozzáadásának folyamatán az Aspose.Words for .NET segítségével. Ez a lépésenkénti útmutató segít a környezet beállításában, a kód megírásában és a folyamat egyes részeinek megértésében. Merüljünk el!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

1. Visual Studio vagy bármely .NET IDE: A .NET-kód írásához és futtatásához fejlesztői környezetre van szüksége.
2.  Aspose.Words for .NET: Az Aspose.Words for .NET könyvtárnak telepítve kell lennie. Letöltheti innen[itt](https://releases.aspose.com/words/net/).
3. Alapvető C# ismeretek: Ez az oktatóanyag feltételezi, hogy rendelkezik a C# programozás alapvető ismereteivel.
4.  Érvényes Aspose licenc: Ideiglenes licencet szerezhet be[itt](https://purchase.aspose.com/temporary-license/).

## Névterek importálása

Kezdésként győződjön meg arról, hogy a szükséges névtereket importálta a projektbe. Ez a lépés kulcsfontosságú az Aspose.Words osztályok és metódusok eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Először is meg kell határoznia azt a könyvtárat, ahová a dokumentumot menteni fogja. Ez fontos a fájlok rendszerezéséhez és a kód megfelelő futásához.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Hozzon létre egy új dokumentumot és DocumentBuildert

 Ezután hozzon létre egy új példányt a`Document` osztály és a`DocumentBuilder` objektum. Ezek az objektumok segítenek a dokumentum elkészítésében és kezelésében.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Szúrjon be egy diagramot a dokumentumba

 Most szúrjon be egy diagramot a dokumentumba a`DocumentBuilder` objektum. Ebben a példában oszlopdiagramot használunk, de választhat más típusokat is.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## 4. lépés: Törölje a meglévő sorozatokat

Töröljön minden létező sorozatot a diagramból, hogy biztosan üres lappal induljon. Ez a lépés elengedhetetlen az egyéni adatokhoz.

```csharp
chart.Series.Clear();
```

## 5. lépés: Adjon hozzá dátum- és időértékeket a sorozathoz

Adja hozzá a dátum és az idő értékeit a diagramsorozathoz. Ebben a lépésben tömböket kell létrehozni a dátumokhoz és a megfelelő értékekhez.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## 6. lépés: Konfigurálja az X-tengelyt

Állítsa be az X-tengely méretezési és pipajeleit. Ez biztosítja, hogy a dátumok helyesen és megfelelő időközönként jelenjenek meg.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## 7. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba. Ez a lépés lezárja a folyamatot, és a dokumentumnak tartalmaznia kell egy diagramot dátum- és időértékekkel az X-tengelyen.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Következtetés

A dátum és az idő értékek hozzáadása a diagram tengelyéhez egy dokumentumban egyszerű folyamat az Aspose.Words for .NET segítségével. Az oktatóanyagban ismertetett lépések követésével világos és informatív diagramokat hozhat létre, amelyek hatékonyan jelenítik meg az idősorok adatait. Függetlenül attól, hogy jelentéseket, prezentációkat vagy bármilyen részletes adatmegjelenítést igénylő dokumentumot készít, az Aspose.Words biztosítja a sikerhez szükséges eszközöket.

## GYIK

### Használhatok más diagramtípusokat az Aspose.Words for .NET-hez?

Igen, az Aspose.Words különféle diagramtípusokat támogat, beleértve a vonalat, oszlopot, kört és egyebeket.

### Hogyan szabhatom testre a diagramom megjelenését?

Testreszabhatja a megjelenést a diagram tulajdonságainak, valamint stílusok, színek és egyebek beállításával.

### Lehetséges több sorozatot hozzáadni egy diagramhoz?

 Teljesen! Több sorozatot is hozzáadhat a diagramjához, ha hívja a`Series.Add` módszer többször különböző adatokkal.

### Mi a teendő, ha dinamikusan kell frissítenem a diagram adatait?

Dinamikusan frissítheti a diagram adatait, ha a sorozat- és tengelytulajdonságokat programozottan módosítja az igényeinek megfelelően.

### Hol találhatok részletesebb dokumentációt az Aspose.Words for .NET-hez?

 Részletesebb dokumentációt találhat[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
