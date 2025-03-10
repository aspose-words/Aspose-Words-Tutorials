---
title: A diagram adatcímkéjének testreszabása
linktitle: A diagram adatcímkéjének testreszabása
second_title: Aspose.Words Document Processing API
description: A lépésenkénti útmutatóból megtudhatja, hogyan szabhatja testre a diagram adatcímkéit az Aspose.Words for .NET használatával. Tökéletes .NET fejlesztőknek.
weight: 10
url: /hu/net/programming-with-charts/chart-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# A diagram adatcímkéjének testreszabása

## Bevezetés

Dinamikus és testreszabott dokumentumfeldolgozási képességekkel szeretné feldobni .NET-alkalmazásait? Az Aspose.Words for .NET talán csak a válasz! Ebben az útmutatóban részletesen bemutatjuk a diagram adatcímkéinek testreszabását az Aspose.Words for .NET használatával, amely egy hatékony könyvtár Word-dokumentumok létrehozásához, módosításához és konvertálásához. Akár tapasztalt fejlesztő, akár csak most kezdi, ez az oktatóanyag végigvezeti Önt minden lépésen, biztosítva, hogy megértse, hogyan használhatja hatékonyan ezt az eszközt.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:

1. Visual Studio: Telepítse a Visual Studio 2019 vagy újabb verzióját.
2. .NET-keretrendszer: Győződjön meg arról, hogy rendelkezik a .NET-keretrendszer 4.0-s vagy újabb verziójával.
3.  Aspose.Words for .NET: Töltse le és telepítse az Aspose.Words for .NET programot a[letöltési link](https://releases.aspose.com/words/net/).
4. Alapvető C# ismerete: A C# programozás ismerete elengedhetetlen.
5.  Érvényes licenc: Szerezzen be a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) vagy vásároljon egyet a[vásárlás link](https://purchase.aspose.com/buy).

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket a C# projektbe. Ez a lépés kulcsfontosságú, mivel biztosítja, hogy hozzáférjen az Aspose.Words által biztosított összes osztályhoz és metódushoz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

 Word-dokumentumok létrehozásához és kezeléséhez először inicializálnunk kell a`Document` osztály és a`DocumentBuilder` objektum.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Magyarázat

- Dokumentumdokumentum: Létrehoz egy új példányt a Dokumentum osztályból.
- DocumentBuilder builder: A DocumentBuilder segít tartalmat beszúrni a Document objektumba.

## 2. lépés: Helyezzen be egy diagramot

 Ezután beszúrunk egy oszlopdiagramot a dokumentumba a`DocumentBuilder` objektum.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Magyarázat

- Alakzat alakja: A diagramot alakzatként jeleníti meg a dokumentumban.
- builder.InsertChart(ChartType.Bar, 432, 252): Beszúr egy oszlopdiagramot meghatározott méretekkel.

## 3. lépés: Nyissa meg a diagramsorozatot

Az adatcímkék testreszabásához először el kell érnünk a diagram sorozatait.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Magyarázat

- ChartSeries series0: Lekéri a diagram első sorozatát, amelyet személyre szabunk.

## 4. lépés: Az adatcímkék testreszabása

Az adatcímkék testreszabhatók különféle információk megjelenítéséhez. A címkéket úgy konfiguráljuk, hogy a jelmagyarázat kulcsát, a sorozat nevét és értékét mutassák, miközben elrejtik a kategória nevét és százalékát.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Magyarázat

- ChartDataLabelCollection címkék: A sorozat adatcímkéit éri el.
- címkék.ShowLegendKey: Megjeleníti a jelmagyarázat kulcsát.
- labels.ShowLeaderLines: Megjeleníti az adatcímkék vezető vonalait, amelyek messze az adatpontokon kívül helyezkednek el.
- labels.ShowCategoryName: Elrejti a kategória nevét.
- címkék.ShowPercentage: Elrejti a százalékos értéket.
- labels.ShowSeriesName: Megjeleníti a sorozat nevét.
- címkék.ShowValue: Az adatpontok értékét jeleníti meg.
- címkék.Elválasztó: Az adatcímkék elválasztóját állítja be.

## 5. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Magyarázat

- doc.Save: Menti a dokumentumot a megadott néven a megadott könyvtárba.

## Következtetés

 Gratulálok! Sikeresen testreszabta a diagram adatcímkéit az Aspose.Words for .NET használatával. Ez a könyvtár robusztus megoldást kínál a Word-dokumentumok programozott kezelésére, megkönnyítve a fejlesztők számára a kifinomult és dinamikus dokumentumfeldolgozó alkalmazások létrehozását. Merüljön el a[dokumentáció](https://reference.aspose.com/words/net/) további funkciók és képességek felfedezéséhez.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony dokumentumfeldolgozó könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, módosítását és konvertálását.

### Hogyan telepíthetem az Aspose.Words for .NET fájlt?
 Letöltheti és telepítheti a[letöltési link](https://releases.aspose.com/words/net/). Kövesse a mellékelt telepítési utasításokat.

### Kipróbálhatom ingyenesen az Aspose.Words for .NET-et?
 Igen, kaphat a[ingyenes próbaverzió](https://releases.aspose.com/) vagy a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) termék értékeléséhez.

### Az Aspose.Words for .NET kompatibilis a .NET Core-al?
Igen, az Aspose.Words for .NET kompatibilis a .NET Core, a .NET Standard és a .NET Framework programmal.

### Hol kaphatok támogatást az Aspose.Words for .NET-hez?
 Meglátogathatja a[támogatási fórum](https://forum.aspose.com/c/words/8) segítségért és segítségért az Aspose közösségtől és szakértőktől.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
