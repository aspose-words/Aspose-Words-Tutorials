---
"description": "Tanuld meg, hogyan szabhatod testre a diagram adatcímkéit az Aspose.Words for .NET használatával egy lépésről lépésre szóló útmutatóban. Tökéletes .NET fejlesztők számára."
"linktitle": "Diagram adatcímkéjének testreszabása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Diagram adatcímkéjének testreszabása"
"url": "/hu/net/programming-with-charts/chart-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Diagram adatcímkéjének testreszabása

## Bevezetés

Szeretnéd dinamikus és testreszabott dokumentumfeldolgozási képességekkel feldobni .NET-es alkalmazásaidat? Az Aspose.Words for .NET lehet a megoldás! Ebben az útmutatóban mélyrehatóan belemerülünk a diagramadat-feliratok testreszabásába az Aspose.Words for .NET segítségével, amely egy hatékony könyvtár Word-dokumentumok létrehozásához, módosításához és konvertálásához. Akár tapasztalt fejlesztő vagy, akár csak most kezded, ez az oktatóanyag végigvezet a lépéseken, biztosítva, hogy megértsd, hogyan használd hatékonyan ezt az eszközt.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:

1. Visual Studio: Telepítse a Visual Studio 2019-es vagy újabb verzióját.
2. .NET-keretrendszer: Győződjön meg róla, hogy a .NET-keretrendszer 4.0-s vagy újabb verziója van telepítve.
3. Aspose.Words .NET-hez: Töltse le és telepítse az Aspose.Words .NET-hez programot a következő helyről: [letöltési link](https://releases.aspose.com/words/net/).
4. C# alapismeretek: A C# programozásban való jártasság elengedhetetlen.
5. Érvényes jogosítvány: Szerezzen be egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/) vagy vásároljon egyet a [vásárlási link](https://purchase.aspose.com/buy).

## Névterek importálása

A kezdéshez importálnod kell a szükséges névtereket a C# projektedbe. Ez a lépés kulcsfontosságú, mivel biztosítja, hogy hozzáférj az Aspose.Words által biztosított összes osztályhoz és metódushoz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## 1. lépés: A dokumentum és a DocumentBuilder inicializálása

Word dokumentumok létrehozásához és kezeléséhez először inicializálnunk kell a Word egy példányát. `Document` osztály és egy `DocumentBuilder` objektum.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Magyarázat

- Dokumentum doc: Létrehozza a Dokumentum osztály egy új példányát.
- DocumentBuilder készítő: A DocumentBuilder segít a tartalom Document objektumba való beszúrásában.

## 2. lépés: Diagram beszúrása

Ezután beszúrunk egy oszlopdiagramot a dokumentumba a következő használatával: `DocumentBuilder` objektum.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Magyarázat

- Alakzat alakzat: A diagramot alakzatként ábrázolja a dokumentumban.
- builder.InsertChart(ChartType.Bar, 432, 252): Beszúr egy oszlopdiagramot a megadott méretekkel.

## 3. lépés: Hozzáférés a diagramsorozathoz

Az adatcímkék testreszabásához először hozzá kell férnünk a diagramban található sorozathoz.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Magyarázat

- ChartSeries series0: Lekéri a diagram első sorozatát, amelyet testreszabunk.

## 4. lépés: Adatcímkék testreszabása

Az adatcímkék testreszabhatók különféle információk megjelenítéséhez. A címkéket úgy konfiguráljuk, hogy megjelenítsék a jelmagyarázat kulcsát, az adatsor nevét és az értéket, miközben elrejtik a kategória nevét és a százalékos értéket.

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

- ChartDataLabelCollection címkék: Hozzáfér az adatsor adatcímkéihez.
- labels.ShowLegendKey: Megjeleníti a jelmagyarázat kulcsát.
- labels.ShowLeaderLines: Megjeleníti az adatpontokon kívül elhelyezkedő adatcímkék vezető vonalait.
- labels.ShowCategoryName: Elrejti a kategória nevét.
- labels.ShowPercentage: Elrejti a százalékos értéket.
- labels.ShowSeriesName: Megjeleníti a sorozat nevét.
- labels.ShowValue: Megjeleníti az adatpontok értékét.
- labels.Separator: Beállítja az adatcímkék elválasztóját.

## 5. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Magyarázat

- doc.Save: Elmenti a dokumentumot a megadott néven a megadott könyvtárba.

## Következtetés

Gratulálunk! Sikeresen testre szabta a diagram adatcímkéit az Aspose.Words for .NET használatával. Ez a könyvtár robusztus megoldást kínál a Word dokumentumok programozott kezelésére, megkönnyítve a fejlesztők számára a kifinomult és dinamikus dokumentumfeldolgozó alkalmazások létrehozását. Merüljön el a... [dokumentáció](https://reference.aspose.com/words/net/) további funkciók és lehetőségek felfedezéséhez.

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony dokumentumfeldolgozó könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, módosítsanak és konvertáljanak Word dokumentumokat.

### Hogyan telepíthetem az Aspose.Words for .NET programot?
Letöltheted és telepítheted innen: [letöltési link](https://releases.aspose.com/words/net/)Kövesse a mellékelt telepítési utasításokat.

### Kipróbálhatom ingyen az Aspose.Words for .NET-et?
Igen, kaphatsz egy [ingyenes próba](https://releases.aspose.com/) vagy egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/) hogy értékelje a terméket.

### Kompatibilis az Aspose.Words for .NET a .NET Core-ral?
Igen, az Aspose.Words for .NET kompatibilis a .NET Core, a .NET Standard és a .NET Framework rendszerekkel.

### Hol kaphatok támogatást az Aspose.Words for .NET-hez?
Meglátogathatod a [támogatási fórum](https://forum.aspose.com/c/words/8) segítségért és támogatásért az Aspose közösségtől és a szakértőktől.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}