---
title: Formátum Adatcímke száma Egy diagramon
linktitle: Formátum Adatcímke száma Egy diagramon
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan formázhat adatcímkéket diagramokban az Aspose.Words for .NET használatával. Javítsa Word-dokumentumait könnyedén.
weight: 10
url: /hu/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formátum Adatcímke száma Egy diagramon

## Bevezetés

A vonzó és informatív dokumentumok létrehozása gyakran magában foglalja a jól formázott adatcímkéket tartalmazó diagramok beépítését. Ha Ön .NET-fejlesztő, aki kifinomult diagramokkal szeretné bővíteni Word-dokumentumait, az Aspose.Words for .NET egy fantasztikus könyvtár, amely segít elérni ezt. Ez az oktatóanyag lépésről lépésre végigvezeti a számcímkék diagramon történő formázásán az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belemerülne a kódba, meg kell felelnie néhány előfeltételnek:

-  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha még nem telepítette, megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Be kell állítania egy .NET fejlesztői környezetet. A Visual Studio erősen ajánlott.
- Alapvető C# ismerete: A C# programozás ismerete elengedhetetlen, mivel ez az oktatóanyag a C# kód írását és megértését foglalja magában.
-  Ideiglenes licenc: Az Aspose.Words korlátozás nélküli használatához beszerezheti a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

Most pedig nézzük meg a számcímkék diagramon való formázásának lépésről lépésre történő folyamatát.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket az Aspose.Words for .NET használatához. Adja hozzá a következő sorokat a C# fájl tetejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Mielőtt elkezdené kezelni a Word-dokumentumot, meg kell adnia azt a könyvtárat, ahová a dokumentumot menteni fogja. Ez elengedhetetlen a későbbi mentési művelethez.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a dokumentumkönyvtár tényleges elérési útjával.

## 2. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

 A következő lépés egy új inicializálása`Document` és a`DocumentBuilder` . A`DocumentBuilder` egy segítő osztály, amely lehetővé teszi a dokumentum tartalmának felépítését.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Szúrjon be egy diagramot a dokumentumba

 Most szúrjunk be egy diagramot a dokumentumba a`DocumentBuilder`. Ebben az oktatóanyagban egy vonaldiagramot használunk példaként.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Itt beszúrunk egy vonaldiagramot meghatározott szélességgel és magassággal, és beállítjuk a diagram címét.

## 4. lépés: Alapértelmezett sorozat törlése és új sorozat hozzáadása

Alapértelmezés szerint a diagramnak néhány előre generált sorozata lesz. Ezeket törölnünk kell, és hozzá kell adnunk saját sorozatunkat konkrét adatpontokkal.

```csharp
// Alapértelmezett generált sorozat törlése.
chart.Series.Clear();

// Új sorozat hozzáadása egyéni adatpontokkal.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## 5. lépés: Engedélyezze az adatcímkéket

Az adatcímkék diagramon való megjelenítéséhez engedélyeznünk kell őket a sorozatunkban.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## 6. lépés: Formázza meg az adatcímkéket

Ennek az oktatóanyagnak a lényege az adatcímkék formázása. Minden adatcímkére külön-külön különböző számformátumokat alkalmazhatunk.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Pénznem formátuma
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Dátumformátum
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Százalékos formátum
```

 Ezenkívül összekapcsolhatja az adatcímke formátumát egy forráscellával. Ha linkeljük, a`NumberFormat` vissza lesz állítva általánosra, és a forráscellából öröklődik.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## 7. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Ez elmenti a dokumentumot a megadott néven, és biztosítja a formázott adatcímkékkel ellátott diagram megőrzését.

## Következtetés

Az adatcímkék diagramon való formázása az Aspose.Words for .NET használatával nagymértékben javíthatja Word-dokumentumai olvashatóságát és professzionalizmusát. A lépésenkénti útmutató követésével most már képesnek kell lennie diagram létrehozására, adatsorok hozzáadására és az adatcímkék igényeinek megfelelő formázására. Az Aspose.Words for .NET egy hatékony eszköz, amely lehetővé teszi a Word-dokumentumok széles körű testreszabását és automatizálását, így a .NET-fejlesztők számára felbecsülhetetlen értékű eszköz.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár Word-dokumentumok programozott, C# használatával történő létrehozásához, kezeléséhez és konvertálásához.

### Formázhatok más típusú diagramokat az Aspose.Words for .NET segítségével?
Igen, az Aspose.Words for .NET számos diagramtípust támogat, beleértve a sávot, oszlopot, kört és egyebeket.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words for .NET-hez?
Kaphat ideiglenes engedélyt[itt](https://purchase.aspose.com/temporary-license/).

### Lehetséges adatcímkéket kapcsolni a forráscellákhoz az Excelben?
Igen, csatolhat adatcímkéket a forráscellákhoz, lehetővé téve a számformátum öröklését a forráscellából.

### Hol találhatok részletesebb dokumentációt az Aspose.Words for .NET-hez?
 Átfogó dokumentációt találhat[itt](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
