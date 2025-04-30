---
"description": "Ismerje meg, hogyan rögzítheti az alakzatok képarányát Word-dokumentumokban az Aspose.Words for .NET segítségével. Kövesse ezt a lépésenkénti útmutatót a képek és alakzatok arányosságának megőrzéséhez."
"linktitle": "Képarány rögzítve"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Képarány rögzítve"
"url": "/hu/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Képarány rögzítve

## Bevezetés

Elgondolkodtál már azon, hogyan őrizheted meg a képek és alakzatok tökéletes arányait a Word-dokumentumaidban? Néha ügyelned kell arra, hogy a képek és alakzatok ne torzuljanak átméretezéskor. Itt jön jól a képarány zárolása. Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan állíthatod be az alakzatok képarányát a Word-dokumentumokban az Aspose.Words for .NET segítségével. Könnyen követhető lépésekre bontjuk, hogy biztosan magabiztosan alkalmazhasd ezeket a készségeket a projektjeidben.

## Előfeltételek

Mielőtt belemerülnénk a kódba, nézzük át, mire van szükséged a kezdéshez:

- Aspose.Words for .NET könyvtár: Telepítenie kell az Aspose.Words for .NET programot. Ha még nem tette meg, megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Győződjön meg róla, hogy rendelkezik beállított .NET fejlesztői környezettel. A Visual Studio népszerű választás.
- C# alapismeretek: A C# programozásban való jártasság előnyös lesz.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ezek a névterek hozzáférést biztosítanak számunkra azokhoz az osztályokhoz és metódusokhoz, amelyekre szükségünk van a Word-dokumentumokkal és alakzatokkal való munkához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Mielőtt elkezdenénk az alakzatok kezelését, létre kell hoznunk egy könyvtárat, ahová a dokumentumainkat tárolni fogjuk. Az egyszerűség kedvéért egy helykitöltőt fogunk használni. `YOUR DOCUMENT DIRECTORY`Cserélje le ezt a dokumentumkönyvtár tényleges elérési útjára.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Új dokumentum létrehozása

Következő lépésként létrehozunk egy új Word dokumentumot az Aspose.Words segítségével. Ez a dokumentum fog szolgálni vászonként az alakzatok és képek hozzáadásához.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Itt létrehozunk egy példányt a következőből: `Document` osztály és használj egy `DocumentBuilder` hogy segítsen nekünk a dokumentum tartalmának felépítésében.

## 3. lépés: Kép beszúrása

Most illesszünk be egy képet a dokumentumunkba. Használjuk a `InsertImage` a módszer `DocumentBuilder` osztály. Győződjön meg róla, hogy van egy kép a megadott könyvtárban.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Csere `dataDir + "Transparent background logo.png"` a képfájl elérési útjával.

## 4. lépés: Rögzítse a képarányt

Miután a kép be van illesztve, rögzíthetjük a képarányát. A képarány rögzítése biztosítja, hogy a kép arányai állandóak maradjanak átméretezéskor.

```csharp
shape.AspectRatioLocked = true;
```

Beállítás `AspectRatioLocked` hogy `true` biztosítja, hogy a kép megtartsa eredeti képarányát.

## 5. lépés: A dokumentum mentése

Végül mentjük a dokumentumot a megadott könyvtárba. Ez a lépés az összes módosítást kiírja a dokumentumfájlba.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Következtetés

Gratulálunk! Sikeresen megtanultad, hogyan állíthatod be az alakzatok képarányát Word-dokumentumokban az Aspose.Words for .NET segítségével. A következő lépéseket követve biztosíthatod, hogy képeid és alakzataid megtartsák arányaikat, így dokumentumaid professzionális és kifinomult megjelenésűek lesznek. Kísérletezz különböző képekkel és alakzatokkal, hogy lásd, hogyan működik a képarány-zárolási funkció különböző forgatókönyvekben.

## GYIK

### Feloldhatom a képarányt a zárolás után?
Igen, a képarány feloldható a beállítással `shape.AspectRatioLocked = false`.

### Mi történik, ha rögzített képarányú képet méretezek át?
A kép mérete arányosan átalakul, megtartva az eredeti szélesség-magasság arányt.

### Alkalmazhatom ezt képeken kívül más alakzatokra is?
Abszolút! A képarány-rögzítési funkció bármilyen alakzatra alkalmazható, beleértve a téglalapokat, köröket és egyebeket.

### Kompatibilis az Aspose.Words for .NET a .NET Core-ral?
Igen, az Aspose.Words for .NET támogatja mind a .NET Framework, mind a .NET Core verziókat.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
Átfogó dokumentációt találhat [itt](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}