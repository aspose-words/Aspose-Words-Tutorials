---
title: Határozza meg az XY tengely tulajdonságait egy diagramon
linktitle: Határozza meg az XY tengely tulajdonságait egy diagramon
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan határozhatja meg az XY tengely tulajdonságait egy diagramban az Aspose.Words for .NET használatával. Tökéletes .NET fejlesztőknek.
weight: 10
url: /hu/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Határozza meg az XY tengely tulajdonságait egy diagramon

## Bevezetés

A diagramok hatékony eszközt jelentenek az adatok megjelenítésére. Ha professzionális dokumentumokat kell létrehoznia dinamikus diagramokkal, az Aspose.Words for .NET felbecsülhetetlen értékű könyvtár. Ez a cikk végigvezeti az XY tengely tulajdonságainak diagramon történő meghatározásának folyamatán az Aspose.Words for .NET használatával, az egyes lépéseket lebontva az egyértelműség és a könnyebb érthetőség érdekében.

## Előfeltételek

Mielőtt belemerülne a kódolásba, meg kell felelnie néhány előfeltételnek:

1. Aspose.Words for .NET: Győződjön meg arról, hogy rendelkezik az Aspose.Words for .NET könyvtárral. Megteheti[töltse le itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Szüksége van egy integrált fejlesztői környezetre (IDE), például a Visual Studiora.
3. .NET-keretrendszer: Győződjön meg arról, hogy a fejlesztői környezete be van állítva a .NET-fejlesztéshez.
4. Alapvető C# ismerete: Ez az útmutató feltételezi, hogy rendelkezik a C# programozás alapvető ismereteivel.

## Névterek importálása

Először is importálnia kell a szükséges névtereket a projektbe. Ez biztosítja, hogy hozzáférjen a dokumentumok és diagramok létrehozásához és kezeléséhez szükséges összes osztályhoz és módszerhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

A folyamatot egyszerű lépésekre bontjuk, amelyek mindegyike az XY tengely tulajdonságainak diagramban történő meghatározásának egy-egy részére összpontosít.

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

 Először is inicializálnia kell egy új dokumentumot, és a`DocumentBuilder` objektum. A`DocumentBuilder` segít a tartalom beillesztésében a dokumentumba.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Helyezzen be egy diagramot

Ezután beszúr egy diagramot a dokumentumba. Ebben a példában egy területdiagramot fogunk használni. Szükség szerint testreszabhatja a diagram méreteit.

```csharp
// Diagram beszúrása
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## 3. lépés: Alapértelmezett sorozat törlése és egyéni adatok hozzáadása

Alapértelmezés szerint a diagramnak néhány előre meghatározott sorozata lesz. Töröljük ezeket, és hozzáadjuk egyéni adatsorainkat.

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

## 4. lépés: Határozza meg az X tengely tulajdonságait

Most itt az ideje, hogy meghatározzuk az X tengely tulajdonságait. Ez magában foglalja a kategória típusának beállítását, a tengely keresztezésének testreszabását, valamint a pipajelek és címkék beállítását.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; //Az Y tengely kijelzési egységeiben mérve (száz).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## 5. lépés: Határozza meg az Y tengely tulajdonságait

Hasonlóképpen beállíthatja az Y tengely tulajdonságait. Ez magában foglalja a pipa címke pozíciójának, a fő- és mellékegységek, a megjelenítési egység és a méretezés beállítását.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## 6. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba. Ez létrehozza a Word dokumentumot a testreszabott diagrammal.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Következtetés

Word-dokumentumok diagramjainak létrehozása és testreszabása az Aspose.Words for .NET használatával egyszerű, ha megértette a szükséges lépéseket. Ez az útmutató végigvezeti az XY tengely tulajdonságainak diagramban történő meghatározásának folyamatán, a dokumentum inicializálásától a végtermék mentéséig. Ezekkel a készségekkel részletes, professzionális megjelenésű diagramokat hozhat létre, amelyek javítják dokumentumait.

## GYIK

### Milyen típusú diagramokat hozhatok létre az Aspose.Words for .NET segítségével?
Különféle típusú diagramokat hozhat létre, beleértve a területet, oszlopot, vonalat, kört és még sok mást.

### Hogyan telepíthetem az Aspose.Words for .NET fájlt?
 Az Aspose.Words for .NET letölthető innen[itt](https://releases.aspose.com/words/net/)és kövesse a mellékelt telepítési utasításokat.

### Testreszabhatom a diagramjaim megjelenését?
Igen, az Aspose.Words for .NET lehetővé teszi a diagramok széles körű testreszabását, beleértve a színeket, a betűtípusokat és a tengelytulajdonságokat.

### Létezik ingyenes próbaverzió az Aspose.Words for .NET számára?
 Igen, ingyenes próbaverziót kaphat[itt](https://releases.aspose.com/).

### Hol találok további oktatóanyagokat és dokumentációt?
 További oktatóanyagokat és részletes dokumentációt találhat a[Aspose.Words for .NET dokumentációs oldal](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
