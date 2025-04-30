---
"description": "Tanuld meg, hogyan szabhatod testre az egydiagramos adatpontokat az Aspose.Words for .NET használatával egy részletes, lépésről lépésre szóló útmutatóban. Dobd fel diagramjaidat egyedi jelölőkkel és méretekkel."
"linktitle": "Egyetlen diagramadatpont testreszabása egy diagramban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Egyetlen diagramadatpont testreszabása egy diagramban"
"url": "/hu/net/programming-with-charts/single-chart-data-point/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Egyetlen diagramadatpont testreszabása egy diagramban

## Bevezetés

Elgondolkodtál már azon, hogyan teheted egyedi adatpontokkal kiemeltté a diagramjaidat? Nos, ma van a szerencséd! Most belevágunk egyetlen diagramadat testreszabásába az Aspose.Words for .NET használatával. Kapcsold be az öved egy lépésről lépésre szóló útmutató keretében, amely nemcsak informatív, hanem szórakoztató és könnyen követhető is.

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy minden alapvető dolog a helyén van:

- Aspose.Words .NET könyvtárhoz: Győződjön meg róla, hogy a legújabb verzióval rendelkezik. [Töltsd le itt](https://releases.aspose.com/words/net/).
- .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a gépén.
- C# alapismeretek: A C# programozás alapjainak ismerete hasznos lesz.
- Integrált fejlesztői környezet (IDE): Visual Studio ajánlott.

## Névterek importálása

Először is importáljuk a szükséges névtereket, hogy beinduljon a folyamat:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1. lépés: A dokumentum és a DocumentBuilder inicializálása

Rendben, kezdjük egy új dokumentum és egy DocumentBuilder inicializálásával. Ez lesz a diagramunk vászonja.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Itt, `dataDir` a könyvtár elérési útja, ahová a dokumentumot menteni fogja. `DocumentBuilder` Az osztály segít a dokumentum elkészítésében.

## 2. lépés: Diagram beszúrása

Következő lépésként illesszünk be egy vonaldiagramot a dokumentumba. Ez lesz a játszóterünk az adatpontok testreszabásához.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

A `InsertChart` A metódus paraméterként fogadja a diagram típusát, szélességét és magasságát. Ebben az esetben egy 432 szélességű és 252 magasságú vonaldiagramot szúrunk be.

## 3. lépés: Hozzáférés diagramsorozathoz

Most pedig nézzük meg a diagramon belüli adatsorokat. Egy diagram több adatsort is tartalmazhat, és minden adatsor adatpontokat tartalmaz.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Itt a diagramunk első két sorozatát érjük el. 

## 4. lépés: Adatpontok testreszabása

Itt történik a varázslat! Szabjuk testre a sorozatunkon belüli egyes adatpontokat.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Az első sorozat adatpontjait kérjük le. Most szabjuk testre ezeket a pontokat.

### 00. adatpont testreszabása

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

Mert `dataPoint00`, egy robbanást állítunk be (kördiagramoknál hasznos), a jelölő szimbólumát körre cseréljük, és a jelölő méretét 15-re állítjuk.

### 01. adatpont testreszabása

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

Mert `dataPoint01`, a jelölő szimbólumát rombuszra cseréljük, a jelölő méretét pedig 20-ra állítjuk.

### Adatpont testreszabása az 1. sorozatban

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

A harmadik adatponthoz `series1`, úgy állítjuk be, hogy negatív érték esetén invertálja a képet, a jelölő szimbólumát csillagra cseréljük, és a jelölő méretét 20-ra állítjuk.

## 5. lépés: A dokumentum mentése

Végül mentsük el a dokumentumunkat az összes testreszabással.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

Ez a sor a megadott könyvtárba menti a dokumentumot a következő néven: `WorkingWithCharts.SingleChartDataPoint.docx`.

## Következtetés

És íme! Sikeresen testre szabtad az egyes adatpontokat egy diagramban az Aspose.Words for .NET használatával. Néhány tulajdonság módosításával sokkal informatívabbá és vizuálisan vonzóbbá teheted a diagramjaidat. Tehát kísérletezz különböző jelölőkkel és méretekkel, hogy lásd, mi működik a legjobban az adataidhoz.

## GYIK

### Testreszabhatom az adatpontokat más típusú diagramokban?

Természetesen! Testreszabhatja az adatpontokat különféle diagramtípusokban, beleértve az oszlopdiagramokat, kördiagramokat és egyebeket. A folyamat hasonló a különböző diagramtípusokban.

### Lehetséges egyéni címkéket hozzáadni az adatpontokhoz?

Igen, egyéni címkéket adhatsz hozzá az adatpontokhoz a `ChartDataPoint.Label` tulajdonság. Ez lehetővé teszi, hogy minden adatponthoz további kontextust adjon meg.

### Hogyan távolíthatok el egy adatpontot egy sorozatból?

Adatpontot úgy távolíthat el, hogy a láthatóságát hamis értékre állítja a következő használatával: `dataPoint.IsVisible = false`.

### Használhatok képeket adatpontok jelölésére?

Bár az Aspose.Words nem támogatja a képek közvetlen jelölőként való használatát, létrehozhat egyéni alakzatokat, és azokat jelölőként használhatja.

### Lehetséges az adatpontok animálása a diagramon?

Az Aspose.Words for .NET nem támogatja a diagram adatpontjainak animációját. Animált diagramokat azonban más eszközökkel is létrehozhat, és beágyazhatja azokat Word-dokumentumaiba.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}