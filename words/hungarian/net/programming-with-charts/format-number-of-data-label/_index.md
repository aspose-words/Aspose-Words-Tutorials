---
"description": "Tanuld meg, hogyan formázhatod az adatcímkéket a diagramokban az Aspose.Words for .NET használatával ezzel a lépésről lépésre haladó útmutatóval. Könnyedén javíthatod Word-dokumentumaidat."
"linktitle": "Az adatcímke számának formázása egy diagramban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Az adatcímke számának formázása egy diagramban"
"url": "/hu/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Az adatcímke számának formázása egy diagramban

## Bevezetés

A lebilincselő és informatív dokumentumok létrehozása gyakran magában foglalja a jól formázott adatcímkékkel ellátott diagramok használatát. Ha .NET-fejlesztőként szeretnéd kifinomult diagramokkal kiegészíteni Word-dokumentumaidat, az Aspose.Words for .NET egy fantasztikus könyvtár, amely segít ebben. Ez az oktatóanyag lépésről lépésre végigvezet a számcímkék formázásán egy diagramban az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belemerülnél a kódba, van néhány előfeltétel, aminek teljesülnie kell:

- Aspose.Words for .NET: Győződjön meg róla, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha még nem telepítette, megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Rendelkeznie kell egy beállított .NET fejlesztői környezettel. A Visual Studio használata erősen ajánlott.
- C# alapismeretek: A C# programozással való ismeret elengedhetetlen, mivel ez az oktatóanyag C# kód írását és megértését foglalja magában.
- Ideiglenes licenc: Az Aspose.Words korlátozás nélküli használatához szerezhet egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

Most pedig nézzük meg lépésről lépésre a számfeliratok formázásának folyamatát egy diagramban.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket az Aspose.Words for .NET használatához. Adjuk hozzá a következő sorokat a C# fájl elejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Mielőtt elkezdenéd a Word-dokumentum szerkesztését, meg kell adnod azt a könyvtárat, ahová a dokumentumot menteni szeretnéd. Ez elengedhetetlen a későbbi mentési művelethez.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Csere `"YOUR DOCUMENT DIRECTORY"` a dokumentumkönyvtár tényleges elérési útjával.

## 2. lépés: A dokumentum és a DocumentBuilder inicializálása

A következő lépés egy új inicializálása `Document` és egy `DocumentBuilder`. A `DocumentBuilder` egy segítő osztály, amely lehetővé teszi számunkra a dokumentum tartalmának létrehozását.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Táblázat beszúrása a dokumentumba

Most illesszünk be egy diagramot a dokumentumba a következő használatával: `DocumentBuilder`Ebben az oktatóanyagban egy vonaldiagramot fogunk használni példaként.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Itt beszúrunk egy vonaldiagramot adott szélességgel és magassággal, és beállítjuk a diagram címét.

## 4. lépés: Alapértelmezett sorozat törlése és új sorozat hozzáadása

Alapértelmezés szerint a diagram néhány előre generált adatsort tartalmaz. Ezeket törölnünk kell, és hozzá kell adnunk a saját adatsorainkat meghatározott adatpontokkal.

```csharp
// Alapértelmezetten generált sorozat törlése.
chart.Series.Clear();

// Új sorozat hozzáadása egyéni adatpontokkal.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## 5. lépés: Adatcímkék engedélyezése

Ahhoz, hogy az adatfeliratok megjelenjenek a diagramon, engedélyeznünk kell azokat a sorozatunkhoz.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## 6. lépés: Adatcímkék formázása

A bemutató lényege az adatcímkék formázása. Minden adatcímkére külön-külön alkalmazhatunk különböző számformátumokat.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Pénznemformátum
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Dátumformátum
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Százalékos formátum
```

Ezenkívül egy adatcímke formátumát összekapcsolhatja egy forráscellával. Összekapcsoláskor a `NumberFormat` általános értékre lesz visszaállítva, és a forráscellától öröklődik.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## 7. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Ez a megadott néven menti a dokumentumot, és biztosítja, hogy a formázott adatfeliratokkal ellátott diagram megmaradjon.

## Következtetés

Az Aspose.Words for .NET segítségével a diagramok adatcímkéinek formázása nagymértékben javíthatja Word-dokumentumai olvashatóságát és professzionalizmusát. A lépésről lépésre haladó útmutató követésével most már képesnek kell lennie diagramok létrehozására, adatsorok hozzáadására és az adatcímkék igényeinek megfelelő formázására. Az Aspose.Words for .NET egy hatékony eszköz, amely lehetővé teszi a Word-dokumentumok széleskörű testreszabását és automatizálását, így felbecsülhetetlen értékű eszköz a .NET-fejlesztők számára.

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony függvénytár, amellyel programozottan, C# nyelven hozhatók létre, módosíthatók és konvertálhatók Word-dokumentumok.

### Formázhatok más típusú diagramokat az Aspose.Words for .NET segítségével?
Igen, az Aspose.Words for .NET számos diagramtípust támogat, beleértve a sáv-, oszlop-, kördiagramokat és egyebeket.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words for .NET-hez?
Ideiglenes jogosítványt szerezhet [itt](https://purchase.aspose.com/temporary-license/).

### Lehetséges adatcímkéket forráscellákhoz csatolni az Excelben?
Igen, az adatfeliratokat csatolhatja a forráscellákhoz, így a számformátum öröklődhet a forráscellától.

### Hol találok részletesebb dokumentációt az Aspose.Words for .NET-hez?
Átfogó dokumentációt találhat [itt](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}