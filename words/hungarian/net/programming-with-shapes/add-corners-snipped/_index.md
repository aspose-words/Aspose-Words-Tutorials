---
title: Adja hozzá a levágott sarkokat
linktitle: Adja hozzá a levágott sarkokat
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan adhat hozzá sarkokkal levágott alakzatot Word-dokumentumaihoz az Aspose.Words for .NET használatával. Ez a lépésenkénti útmutató biztosítja a dokumentumok egyszerű javítását.
weight: 10
url: /hu/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adja hozzá a levágott sarkokat

## Bevezetés

Egyéni alakzatok hozzáadása a Word-dokumentumokhoz szórakoztató és tetszetős módja lehet a fontos információk kiemelésének, vagy egy kis hangulat hozzáadásának a tartalomhoz. Ebben az oktatóanyagban azt mutatjuk be, hogyan illeszthet be "Corners Snipped" alakzatokat Word-dokumentumaiba az Aspose.Words for .NET használatával. Ez az útmutató végigvezeti Önt minden lépésen, biztosítva, hogy könnyedén hozzáadhassa ezeket az alakzatokat és személyre szabhassa dokumentumait, mint egy profi.

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjünk meg arról, hogy mindennel rendelkezünk, ami az induláshoz szükséges:

1.  Aspose.Words for .NET: Ha még nem tette meg, töltse le a legújabb verziót a[Az Aspose kiadási oldala](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Állítsa be fejlesztői környezetét. A Visual Studio népszerű választás, de bármilyen IDE-t használhat, amely támogatja a .NET-et.
3.  Licenc: Ha csak kísérletezik, használhatja a[ingyenes próbaverzió](https://releases.aspose.com/) vagy kap a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) a teljes funkcionalitás feloldásához.
4. A C# alapvető ismerete: A C# programozás ismerete segít a példák követésében.

## Névterek importálása

Mielőtt elkezdhetnénk dolgozni az Aspose.Words for .NET programmal, importálnunk kell a szükséges névtereket. Adja hozzá ezeket a C# fájl tetejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Most bontsuk le több lépésre a „Corners Snipped” alakzat hozzáadásának folyamatát. Kövesse pontosan ezeket a lépéseket, hogy minden zökkenőmentesen működjön.

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

 Az első dolog, amit tennünk kell, hogy létrehozunk egy új dokumentumot, és inicializáljuk a`DocumentBuilder` objektum. Ez az építő segít nekünk tartalmat hozzáadni a dokumentumunkhoz.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ebben a lépésben beállítottuk a dokumentumunkat és az építőt. Gondolj a`DocumentBuilder` digitális tollként, írásra és rajzolásra készen a Word-dokumentumban.

## 2. lépés: Helyezze be a sarkok levágott alakját

 Ezután a`DocumentBuilder` "Sarkok levágott" alakzat beszúrásához. Ez az alakzattípus előre meghatározott az Aspose.Words-ben, és egyszerűen beilleszthető egyetlen kódsorral.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Itt megadjuk az alakzat típusát és méreteit (50x50). Képzelje el, hogy egy kicsi, tökéletesen levágott sarokmatricát helyez el a dokumentumára. 

## 3. lépés: Határozza meg a mentési beállításokat a megfelelőséggel

 dokumentumunk mentése előtt meg kell határoznunk a mentési beállításokat, hogy biztosítsuk, hogy dokumentumunk megfelel-e bizonyos szabványoknak. Használjuk a`OoxmlSaveOptions` osztály erre.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Ezek a mentési lehetőségek biztosítják, hogy dokumentumunk megfeleljen az ISO/IEC 29500:2008 szabványnak, ami kulcsfontosságú a kompatibilitás és a dokumentumok hosszú élettartama szempontjából.

## 4. lépés: Mentse el a dokumentumot

Végül a korábban meghatározott mentési beállításokkal a megadott könyvtárba mentjük a dokumentumunkat.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

Hasonlóképpen, a dokumentuma mostantól egy egyéni „Sarkok levágott” alakzatot tartalmaz, amely a szükséges megfelelőségi beállításokkal mentve van.

## Következtetés

Megvan! Egyéni alakzatok hozzáadása a Word-dokumentumokhoz az Aspose.Words for .NET használatával egyszerű, és nagymértékben javíthatja a dokumentumok vizuális vonzerejét. Ha követi ezeket a lépéseket, egyszerűen beilleszthet egy „Sarkok levágott” alakzatot, és biztosíthatja, hogy a dokumentum megfeleljen a szükséges szabványoknak. Boldog kódolást!

## GYIK

### Testreszabhatom a „Corners Snipped” alakzat méretét?
Igen, módosíthatja a méretet a méretek módosításával a`InsertShape` módszer.

### Lehetséges más típusú formák hozzáadása?
 Teljesen! Az Aspose.Words különféle alakzatokat támogat. Csak változtasd meg a`ShapeType` a kívánt alakra.

### Szükségem van engedélyre az Aspose.Words használatához?
Bár használhat ingyenes próbaverziót vagy ideiglenes licencet, a korlátlan használathoz teljes licenc szükséges.

### Hogyan alakíthatom tovább a formákat?
Az Aspose.Words által biztosított további tulajdonságok és módszerek segítségével személyre szabhatja az alakzatok megjelenését és viselkedését.

### Az Aspose.Words kompatibilis más formátumokkal?
Igen, az Aspose.Words többféle dokumentumformátumot támogat, beleértve a DOCX, PDF, HTML és egyebeket.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
