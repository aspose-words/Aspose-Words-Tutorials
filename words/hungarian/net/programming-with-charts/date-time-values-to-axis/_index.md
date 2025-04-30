---
"description": "Tanuld meg, hogyan adhatsz hozzá dátum- és időértékeket egy diagram tengelyéhez az Aspose.Words for .NET használatával ebben az átfogó, lépésről lépésre haladó útmutatóban."
"linktitle": "Dátum/idő értékek hozzáadása egy diagram tengelyéhez"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Dátum/idő értékek hozzáadása egy diagram tengelyéhez"
"url": "/hu/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dátum/idő értékek hozzáadása egy diagram tengelyéhez

## Bevezetés

A dokumentumokban létrehozott diagramok hatékony módja lehet az adatok vizualizációjának. Idősoros adatok kezelésekor a dátum- és időértékek hozzáadása a diagram tengelyéhez kulcsfontosságú az áttekinthetőség érdekében. Ebben az oktatóanyagban végigvezetünk a dátum- és időértékek diagram tengelyéhez való hozzáadásának folyamatán az Aspose.Words for .NET használatával. Ez a lépésről lépésre szóló útmutató segít beállítani a környezetet, megírni a kódot és megérteni a folyamat minden részét. Vágjunk bele!

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy a következő előfeltételek teljesülnek:

1. Visual Studio vagy bármilyen .NET IDE: Fejlesztői környezetre van szükséged a .NET kódod írásához és futtatásához.
2. Aspose.Words for .NET: Telepítenie kell az Aspose.Words for .NET könyvtárat. Letöltheti innen: [itt](https://releases.aspose.com/words/net/).
3. C# alapismeretek: Ez az oktatóanyag feltételezi, hogy rendelkezel C# programozási alapismeretekkel.
4. Érvényes Aspose licenc: Ideiglenes licencet szerezhet be a következő címen: [itt](https://purchase.aspose.com/temporary-license/).

## Névterek importálása

Kezdésként győződj meg róla, hogy importáltad a szükséges névtereket a projektedbe. Ez a lépés elengedhetetlen az Aspose.Words osztályok és metódusok eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Először is meg kell határoznod azt a könyvtárat, ahová a dokumentumod mentésre kerül. Ez fontos a fájlok rendszerezéséhez és a kód megfelelő futtatásához.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Új dokumentum és DocumentBuilder létrehozása

Ezután hozzon létre egy új példányt a `Document` osztály és egy `DocumentBuilder` objektum. Ezek az objektumok segítenek a dokumentum felépítésében és kezelésében.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Táblázat beszúrása a dokumentumba

Most illesszen be egy diagramot a dokumentumba a `DocumentBuilder` objektum. Ebben a példában oszlopdiagramot használunk, de más típusokat is választhat.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## 4. lépés: Meglévő sorozatok törlése

Törölj minden meglévő adatsort a diagramból, hogy biztosan üres lappal kezdj. Ez a lépés elengedhetetlen az egyéni adatokhoz.

```csharp
chart.Series.Clear();
```

## 5. lépés: Dátum- és időértékek hozzáadása a sorozathoz

Adja hozzá a dátum- és időértékeket a diagramsorozathoz. Ez a lépés tömbök létrehozását foglalja magában a dátumokhoz és a hozzájuk tartozó értékekhez.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## 6. lépés: Az X tengely konfigurálása

Állítsd be az X tengely méretarányát és jelöléseit. Ez biztosítja, hogy a dátumok helyesen és megfelelő időközönként jelenjenek meg.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## 7. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba. Ez a lépés lezárja a folyamatot, és a dokumentumnak most egy diagramot kell tartalmaznia, amelyen a dátum és az idő értékei az X tengelyen szerepelnek.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Következtetés

A dátum- és időértékek hozzáadása egy dokumentumban lévő diagram tengelyéhez egyszerű folyamat az Aspose.Words for .NET segítségével. Az ebben az oktatóanyagban ismertetett lépéseket követve világos és informatív diagramokat hozhat létre, amelyek hatékonyan jelenítik meg az idősoros adatokat. Akár jelentéseket, prezentációkat vagy bármilyen részletes adatábrázolást igénylő dokumentumot készít, az Aspose.Words biztosítja a sikerhez szükséges eszközöket.

## GYIK

### Használhatok más diagramtípusokat az Aspose.Words for .NET programmal?

Igen, az Aspose.Words különféle diagramtípusokat támogat, beleértve a vonal-, sáv-, kördiagramokat és egyebeket.

### Hogyan tudom testreszabni a diagramom megjelenését?

A megjelenést testreszabhatja a diagram tulajdonságainak elérésével, valamint a stílusok, színek és egyebek beállításával.

### Lehetséges több sorozatot hozzáadni egy diagramhoz?

Természetesen! Több sorozatot is hozzáadhatsz a diagramodhoz a `Series.Add` módszert többször, különböző adatokkal.

### Mi van, ha dinamikusan kell frissítenem a diagram adatait?

A diagram adatait dinamikusan frissítheti a sorozat- és tengelytulajdonságok programozott módosításával az igényei szerint.

### Hol találok részletesebb dokumentációt az Aspose.Words for .NET-hez?

Részletesebb dokumentációt találhat [itt](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}