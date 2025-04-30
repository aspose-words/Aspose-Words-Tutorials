---
"description": "Tanuld meg, hogyan egyesíthetsz cellákat vízszintesen egy Word-dokumentumban az Aspose.Words for .NET segítségével ebből a részletes, lépésről lépésre haladó oktatóanyagból."
"linktitle": "Vízszintes egyesítés"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Vízszintes egyesítés"
"url": "/hu/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vízszintes egyesítés

## Bevezetés

Sziasztok! Készen álltok belevetni magatokat az Aspose.Words for .NET világába? Ma egy szuper hasznos funkcióval fogunk foglalkozni: a táblázatok vízszintes egyesítésével. Ez talán kicsit technikailag hangzik, de ne aggódjatok, segítek. Mire ezt az oktatóanyagot végighallgatjátok, profik lesztek a Word-dokumentumok celláinak programozott egyesítésében. Szóval, akkor tűrjük fel az ingujjunkat, és kezdjük is el!

## Előfeltételek

Mielőtt belevágnánk a részletekbe, van néhány dolog, amire szükséged lesz:

1. Aspose.Words for .NET könyvtár: Ha még nem tetted meg, töltsd le az Aspose.Words for .NET könyvtárat. Itt letöltheted [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Győződjön meg arról, hogy megfelelő fejlesztői környezettel rendelkezik, például Visual Studio-val.
3. C# alapismeretek: A C# programozás alapvető ismerete előnyös.

Ha ezeket elintézted, akkor már indulásra készen is vagy!

## Névterek importálása

Mielőtt belemerülnénk a kódba, ellenőrizzük, hogy importáltuk-e a szükséges névtereket. A C# projektedben mindenképpen szerepeltesse a következőket:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Rendben, bontsuk le a táblázatcellák vízszintes egyesítésének folyamatát egy Word-dokumentumban az Aspose.Words for .NET használatával.

## 1. lépés: A dokumentum beállítása

Először is létre kell hoznunk egy új Word dokumentumot, és inicializálnunk kell a `DocumentBuilder`:

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ez a kódrészlet létrehoz egy új dokumentumot, és előkészíti a `DocumentBuilder` cselekvésre.

## 2. lépés: Az első cella beszúrása

Ezután beillesztjük az első cellát, és megjelöljük vízszintes egyesítéshez:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Itt beszúrunk egy új cellát, és beállítjuk a `HorizontalMerge` ingatlan `CellMerge.First`, jelezve, hogy ez a cella egy egyesített cellasorozat kezdete.

## 3. lépés: Az egyesített cella beszúrása

Most beillesztjük azt a cellát, amelyet az előzővel egyesíteni fogunk:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

Ez a cella úgy van beállítva, hogy egyesüljön az előző cellával a következő használatával: `CellMerge.Previous`Figyeljük meg, hogyan zárjuk a sort a következővel: `builder.EndRow()`.

## 4. lépés: Nem egyesített cellák beszúrása

A különbség szemléltetésére illesszünk be néhány nem egyesített cellát:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Itt két cellát szúrunk be vízszintes egyesítés nélkül. Ez azt mutatja, hogyan viselkednek a cellák, amikor nem részei egy egyesített sorozatnak.

## 5. lépés: Az asztal befejezése

Végül lezárjuk a táblázatot és mentjük a dokumentumot:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Ez a kódrészlet kiegészíti a táblázatot, és elmenti a dokumentumot a megadott könyvtárba.

## Következtetés

És íme! Most már elsajátítottad a cellák vízszintes egyesítésének művészetét egy Word-dokumentumban az Aspose.Words for .NET segítségével. A következő lépéseket követve könnyedén létrehozhatsz összetett táblázatszerkezeteket. Kísérletezz tovább, és fedezd fel az Aspose.Words képességeit, hogy dokumentumaid olyan dinamikusak és rugalmasak legyenek, amilyenekre csak szükséged van. Jó programozást!

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony függvénytár, amely lehetővé teszi a fejlesztők számára, hogy Word dokumentumokat hozzanak létre, szerkesszenek és manipuláljanak programozottan a .NET alkalmazásokban.

### Egyesíthetek cellákat függőlegesen az Aspose.Words for .NET segítségével?
Igen, függőlegesen is egyesítheti a cellákat a `CellFormat.VerticalMerge` ingatlan.

### Ingyenesen használható az Aspose.Words for .NET?
Az Aspose.Words for .NET ingyenes próbaverziót kínál, de a teljes funkcionalitás eléréséhez licencet kell vásárolnia. Ideiglenes licencet is szerezhet. [itt](https://purchase.aspose.com/temporary-license/).

### Hogyan tudhatok meg többet az Aspose.Words for .NET-ről?
Böngészheted a részletes dokumentációt [itt](https://reference.aspose.com/words/net/).

### Hol kaphatok támogatást az Aspose.Words for .NET-hez?
Bármilyen kérdés vagy probléma esetén látogassa meg az Aspose támogatási fórumot [itt](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}