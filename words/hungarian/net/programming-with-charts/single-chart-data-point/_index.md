---
title: Egyetlen diagram adatpont testreszabása diagramon
linktitle: Egyetlen diagram adatpont testreszabása diagramon
second_title: Aspose.Words Document Processing API
description: A részletes, lépésről lépésre szóló útmutatóból megtudhatja, hogyan szabhat testre egyetlen diagram adatpontját az Aspose.Words for .NET használatával. Növelje diagramjait egyedi markerekkel és méretekkel.
weight: 10
url: /hu/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Egyetlen diagram adatpont testreszabása diagramon

## Bevezetés

Gondolkozott már azon, hogyan hozhatja ki diagramjait egyedi adatpontokkal? Nos, ma van a szerencsés napod! Egyetlen diagram adatpont testreszabásában dolgozunk az Aspose.Words for .NET használatával. Csatlakozzon egy utazáshoz a lépésenkénti oktatóanyag segítségével, amely nemcsak informatív, hanem szórakoztató és könnyen követhető is.

## Előfeltételek

Mielőtt hozzákezdenénk, győződjön meg arról, hogy minden lényeges elem a helyén van:

-  Aspose.Words for .NET Library: Győződjön meg arról, hogy a legújabb verzióval rendelkezik.[Töltse le itt](https://releases.aspose.com/words/net/).
- .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a számítógépen.
- A C# alapvető ismerete: Hasznos lesz a C# programozás alapszintű ismerete.
- Integrált fejlesztői környezet (IDE): a Visual Studio ajánlott.

## Névterek importálása

Először is importáljuk a szükséges névtereket, hogy gördüljön a labda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

Rendben, kezdjük a dolgokat egy új dokumentum és egy DocumentBuilder inicializálásával. Ez lesz a vászon a diagramunkhoz.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itt,`dataDir` a könyvtár elérési útja, ahová a dokumentumot menteni fogja. A`DocumentBuilder` osztály segít a dokumentum felépítésében.

## 2. lépés: Helyezzen be egy diagramot

Ezután illesszünk be egy vonaldiagramot a dokumentumba. Ez lesz a játszóterünk az adatpontok testreszabásához.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 A`InsertChart` metódus a diagram típusát, szélességét és magasságát veszi paraméterként. Ebben az esetben egy 432 szélességű és 252 magasságú vonaldiagramot szúrunk be.

## 3. lépés: Access Chart Series

Most itt az ideje, hogy hozzáférjen a sorozathoz a diagramunkon. Egy diagramnak több sorozata is lehet, és minden sorozat adatpontokat tartalmaz.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Itt a diagramunk első két sorozatához férünk hozzá. 

## 4. lépés: Az adatpontok testreszabása

Itt történik a varázslat! Testre szabjunk bizonyos adatpontokat a sorozatunkon belül.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Az első sorozat adatpontjait lekérjük. Most pedig szabjuk testre ezeket a pontokat.

### 00. adatpont testreszabása

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 Mert`dataPoint00`, egy robbanást állítunk be (kördiagramoknál hasznos), a jelölő szimbólumát körre változtatjuk, a jelölő méretét pedig 15-re.

### A 01. adatpont testreszabása

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 Mert`dataPoint01`, a jelölő szimbólumot gyémántra cseréljük, a jelölő méretét pedig 20-ra állítjuk.

### Az 1. sorozat adatpontjának testreszabása

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 A harmadik adatponthoz`series1`, akkor beállítjuk, hogy invertálja, ha az érték negatív, a jelölő szimbólumot csillagra cseréljük, a jelölő méretét pedig 20-ra.

## 5. lépés: Mentse el a dokumentumot

Végül mentsük el a dokumentumunkat az összes testreszabással.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 Ez a sor elmenti a dokumentumot az Ön megadott könyvtárába a névvel`WorkingWithCharts.SingleChartDataPoint.docx`.

## Következtetés

És megvan! Sikeresen testreszabta az egyes adatpontokat egy diagramon az Aspose.Words for .NET használatával. Néhány tulajdonság módosításával sokkal informatívabbá és látványosabbá teheti diagramjait. Tehát próbálkozzon különböző jelölőkkel és méretekkel, hogy megtudja, mi a legmegfelelőbb az adatokhoz.

## GYIK

### Testreszabhatom az adatpontokat más típusú diagramokon?

Teljesen! Testreszabhatja az adatpontokat különböző diagramtípusokban, beleértve a sávdiagramokat, kördiagramokat és egyebeket. A folyamat hasonló a különböző diagramtípusoknál.

### Lehetséges egyéni címkéket hozzáadni az adatpontokhoz?

 Igen, egyéni címkéket adhat hozzá az adatpontokhoz a`ChartDataPoint.Label` ingatlan. Ez lehetővé teszi, hogy több kontextust biztosítson az egyes adatpontokhoz.

### Hogyan távolíthatok el adatpontot egy sorozatból?

 Eltávolíthat egy adatpontot, ha a láthatóságát false értékre állítja`dataPoint.IsVisible = false`.

### Használhatok képeket adatpontok jelölőiként?

Bár az Aspose.Words nem támogatja a képek közvetlen jelölőként való használatát, egyéni alakzatokat hozhat létre, és használhatja őket jelölőként.

### Lehetséges adatpontokat animálni a diagramon?

Az Aspose.Words for .NET nem támogatja a diagram adatpontjainak animációját. Azonban más eszközökkel is létrehozhat animált diagramokat, és beágyazhatja azokat Word-dokumentumaiba.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
