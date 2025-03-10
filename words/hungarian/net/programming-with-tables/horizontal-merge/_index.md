---
title: Vízszintes összevonás
linktitle: Vízszintes összevonás
second_title: Aspose.Words Document Processing API
description: Ebből a részletes, lépésenkénti oktatóanyagból megtudhatja, hogyan lehet vízszintesen egyesíteni a cellákat egy Word-dokumentumban az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vízszintes összevonás

## Bevezetés

Szia! Készen áll, hogy belemerüljön az Aspose.Words for .NET világába? Ma egy rendkívül hasznos funkcióval fogunk foglalkozni: a táblázatok vízszintes egyesítésével. Ez kissé technikailag hangzik, de ne aggódj, támogatom. Az oktatóanyag végére profi lesz a Word-dokumentumok celláinak programozott egyesítésében. Szóval, feltűrjük az ingujjunkat, és kezdjük!

## Előfeltételek

Mielőtt belevágnánk az apróságokba, van néhány dolog, amit a helyére kell tennie:

1. Aspose.Words for .NET Library: Ha még nem tette meg, töltse le az Aspose.Words for .NET könyvtárat. Megfoghatod[itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Győződjön meg arról, hogy megfelelő fejlesztői környezetet állít be, például a Visual Studio-t.
3. Alapvető C# ismeretek: A C# programozás alapvető ismerete előnyt jelent.

Ha ezeket rendezte, már indulhat is!

## Névterek importálása

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy a szükséges névtereket importálta. A C# projektben feltétlenül tartalmazza:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Rendben, bontsuk le a táblázatcellák vízszintes egyesítésének folyamatát egy Word-dokumentumban az Aspose.Words for .NET használatával.

## 1. lépés: A dokumentum beállítása

 Először is létre kell hoznunk egy új Word-dokumentumot, és inicializálnunk kell a`DocumentBuilder`:

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ez a kódrészlet létrehoz egy új dokumentumot, és előkészíti a`DocumentBuilder` cselekvésre.

## 2. lépés: Az első cella beszúrása

Ezután kezdjük az első cella beszúrásával, és megjelöljük vízszintes egyesítéshez:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Itt beszúrunk egy új cellát, és beállítjuk`HorizontalMerge`tulajdonát`CellMerge.First`, jelezve, hogy ez a cella egy egyesített cellasorozat kezdete.

## 3. lépés: Az egyesített cella beszúrása

Most beillesztjük azt a cellát, amely össze lesz vonva az előzővel:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Ez a cella úgy van beállítva, hogy a használatával egyesüljön az előző cellával`CellMerge.Previous` . Figyeljük meg, hogyan fejezzük be a sort a következővel:`builder.EndRow()`.

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

Itt két cellát szúrunk be vízszintes egyesítés nélkül. Ez megmutatja, hogyan viselkednek a cellák, ha nem részei egy egyesített sorozatnak.

## 5. lépés: A táblázat befejezése

Végül befejezzük a táblázatot és mentjük a dokumentumot:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Ez a kódrészlet kiegészíti a táblázatot, és elmenti a dokumentumot a megadott könyvtárba.

## Következtetés

És megvan! Éppen most sajátította el a cellák vízszintes egyesítésének művészetét egy Word-dokumentumban az Aspose.Words for .NET használatával. Ezen lépések követésével könnyedén hozhat létre összetett táblaszerkezeteket. Folyamatosan kísérletezzen és fedezze fel az Aspose.Words képességeit, hogy dokumentumait olyan dinamikus és rugalmas legyen, amennyire szüksége van. Boldog kódolást!

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, szerkesztését és kezelését .NET-alkalmazásokban.

### Egyesíthetem függőlegesen a cellákat az Aspose.Words for .NET segítségével?
 Igen, a cellákat függőlegesen is egyesítheti a`CellFormat.VerticalMerge` ingatlan.

### Ingyenesen használható az Aspose.Words for .NET?
 Az Aspose.Words for .NET ingyenes próbaverziót kínál, de a teljes funkcionalitás érdekében licencet kell vásárolnia. Kaphat ideiglenes engedélyt[itt](https://purchase.aspose.com/temporary-license/).

### Hogyan tudhatok meg többet az Aspose.Words for .NET-ről?
 Megnézheti a részletes dokumentációt[itt](https://reference.aspose.com/words/net/).

### Hol kaphatok támogatást az Aspose.Words for .NET-hez?
 Bármilyen kérdés vagy probléma esetén keresse fel az Aspose támogatási fórumát[itt](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
