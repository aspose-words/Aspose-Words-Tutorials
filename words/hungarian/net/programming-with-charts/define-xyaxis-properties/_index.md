---
"description": "Tanuld meg, hogyan definiálhatod az XY tengely tulajdonságait egy diagramban az Aspose.Words for .NET használatával ezzel a lépésről lépésre haladó útmutatóval. Tökéletes .NET fejlesztők számára."
"linktitle": "XY tengely tulajdonságainak definiálása egy diagramban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "XY tengely tulajdonságainak definiálása egy diagramban"
"url": "/hu/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# XY tengely tulajdonságainak definiálása egy diagramban

## Bevezetés

diagramok hatékony eszközök az adatok vizualizálására. Ha dinamikus diagramokkal rendelkező professzionális dokumentumokat kell létrehoznia, az Aspose.Words for .NET egy felbecsülhetetlen értékű könyvtár. Ez a cikk végigvezeti Önt az XY tengely tulajdonságainak definiálásának folyamatán egy diagramban az Aspose.Words for .NET használatával, lépésről lépésre lebontva az érthetőség és a könnyű megértés biztosítása érdekében.

## Előfeltételek

Mielőtt belevágnál a kódolásba, van néhány előfeltétel, aminek teljesülnie kell:

1. Aspose.Words .NET-hez: Győződjön meg róla, hogy rendelkezik az Aspose.Words .NET-hez készült könyvtárral. [töltsd le itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Szükséged lesz egy integrált fejlesztői környezetre (IDE), például a Visual Studio-ra.
3. .NET-keretrendszer: Győződjön meg arról, hogy a fejlesztői környezete be van állítva a .NET-fejlesztéshez.
4. C# alapismeretek: Ez az útmutató feltételezi, hogy rendelkezel C# programozási alapismeretekkel.

## Névterek importálása

Először is importálnod kell a szükséges névtereket a projektedbe. Ez biztosítja, hogy hozzáférj az összes osztályhoz és metódushoz, amelyek dokumentumok és diagramok létrehozásához és kezeléséhez szükségesek.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

A folyamatot egyszerű lépésekre bontjuk, amelyek mindegyike a diagram XY tengely tulajdonságainak meghatározásának egy adott részére összpontosít.

## 1. lépés: A dokumentum és a DocumentBuilder inicializálása

Először is inicializálni kell egy új dokumentumot és egy `DocumentBuilder` tárgy. A `DocumentBuilder` segít a tartalom dokumentumba való beillesztésében.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Diagram beszúrása

Ezután beszúr egy diagramot a dokumentumba. Ebben a példában egy területdiagramot fogunk használni. A diagram méreteit szükség szerint testreszabhatja.

```csharp
// Diagram beszúrása
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## 3. lépés: Alapértelmezett sorozat törlése és egyéni adatok hozzáadása

Alapértelmezés szerint a diagram néhány előre definiált adatsort tartalmaz. Ezeket töröljük, és hozzáadjuk az egyéni adatsorainkat.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## 4. lépés: Az X tengely tulajdonságainak meghatározása

Most itt az ideje meghatározni az X tengely tulajdonságait. Ez magában foglalja a kategória típusának beállítását, a tengelymetszés testreszabását, valamint az osztásjelek és feliratok beállítását.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // Az Y tengely megjelenítési egységeiben mérve (százas).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## 5. lépés: Az Y tengely tulajdonságainak meghatározása

Hasonlóképpen állíthatja be az Y tengely tulajdonságait. Ez magában foglalja a jelöléscímke pozícióját, a fő- és mellékmértékegységeket, a megjelenítési mértékegységet és a méretezést.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## 6. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba. Ezzel létrejön a Word dokumentum a testreszabott diagrammal.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Következtetés

A diagramok létrehozása és testreszabása Word-dokumentumokban az Aspose.Words for .NET segítségével egyszerű, ha megérti a szükséges lépéseket. Ez az útmutató végigvezeti Önt az XY tengely tulajdonságainak definiálásának folyamatán egy diagramban, a dokumentum inicializálásától a végeredmény mentéséig. Ezekkel a készségekkel részletes, professzionális megjelenésű diagramokat hozhat létre, amelyek gazdagítják dokumentumait.

## GYIK

### Milyen típusú diagramokat hozhatok létre az Aspose.Words for .NET segítségével?
Különféle típusú diagramokat hozhat létre, beleértve a terület-, sáv-, vonal-, kördiagramokat és egyebeket.

### Hogyan telepíthetem az Aspose.Words for .NET programot?
Az Aspose.Words .NET-hez való verzióját innen töltheti le: [itt](https://releases.aspose.com/words/net/) és kövesse a mellékelt telepítési utasításokat.

### Testreszabhatom a diagramjaim megjelenését?
Igen, az Aspose.Words for .NET lehetővé teszi a diagramok széleskörű testreszabását, beleértve a színeket, betűtípusokat és tengelytulajdonságokat.

### Van ingyenes próbaverzió az Aspose.Words for .NET-hez?
Igen, kérhetsz ingyenes próbaverziót [itt](https://releases.aspose.com/).

### Hol találok további oktatóanyagokat és dokumentációkat?
További oktatóanyagokat és részletes dokumentációt talál a következő címen: [Aspose.Words .NET dokumentációs oldal](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}