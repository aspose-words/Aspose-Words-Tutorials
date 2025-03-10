---
title: Képarány zárolva
linktitle: Képarány zárolva
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan zárolhatja az alakzatok képarányát a Word dokumentumokban az Aspose.Words for .NET segítségével. Kövesse ezt a lépésenkénti útmutatót, hogy képei és alakjai arányosak legyenek.
weight: 10
url: /hu/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Képarány zárolva

## Bevezetés

Gondolkozott már azon, hogyan lehet megőrizni a képek és formák tökéletes arányát Word-dokumentumaiban? Néha gondoskodnia kell arról, hogy a képek és formák ne torzuljanak el az átméretezéskor. Itt jön jól a képarány rögzítése. Ebben az oktatóanyagban megvizsgáljuk, hogyan állíthatja be a Word-dokumentumok alakzatainak képarányát az Aspose.Words for .NET használatával. Könnyen követhető lépésekre bontjuk, így biztosítva, hogy ezeket a készségeket magabiztosan alkalmazhassa projektjei során.

## Előfeltételek

Mielőtt belemerülnénk a kódba, nézzük meg, mire van szüksége a kezdéshez:

- Aspose.Words for .NET Library: telepíteni kell az Aspose.Words for .NET programot. Ha még nem tette meg, megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Győződjön meg arról, hogy be van állítva egy .NET fejlesztői környezet. A Visual Studio népszerű választás.
- Alapvető C# ismeretek: Hasznos lehet némi C# programozási ismerete.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ezek a névterek hozzáférést biztosítanak számunkra azokhoz az osztályokhoz és metódusokhoz, amelyekre szükségünk van a Word dokumentumokkal és alakzatokkal való munkához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

 Mielőtt elkezdenénk manipulálni az alakzatokkal, be kell állítanunk egy könyvtárat, ahol a dokumentumainkat tároljuk. Az egyszerűség kedvéért helyőrzőt használunk`YOUR DOCUMENT DIRECTORY`. Cserélje ki ezt a dokumentumkönyvtár tényleges elérési útjával.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Hozzon létre egy új dokumentumot

Ezután létrehozunk egy új Word-dokumentumot az Aspose.Words használatával. Ez a dokumentum vászonként szolgál formák és képek hozzáadásához.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itt létrehozzuk a`Document` osztály és használja a`DocumentBuilder` hogy segítsen nekünk a dokumentumtartalom felépítésében.

## 3. lépés: Szúrjon be egy képet

 Most pedig szúrjunk be egy képet a dokumentumunkba. Használjuk a`InsertImage` módszere a`DocumentBuilder`osztály. Győződjön meg arról, hogy van egy kép a megadott könyvtárban.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Cserélje ki`dataDir + "Transparent background logo.png"` a képfájl elérési útjával.

## 4. lépés: Zárolja a képarányt

A kép beillesztése után rögzíthetjük a képarányát. A képarány rögzítése biztosítja, hogy átméretezéskor a kép arányai állandóak maradjanak.

```csharp
shape.AspectRatioLocked = true;
```

 Beállítás`AspectRatioLocked` hogy`true` biztosítja, hogy a kép megőrizze eredeti képarányát.

## 5. lépés: Mentse el a dokumentumot

Végül elmentjük a dokumentumot a megadott könyvtárba. Ez a lépés a dokumentumfájlban végrehajtott összes módosítást beírja.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Következtetés

Gratulálok! Sikeresen megtanulta, hogyan állíthatja be a Word-dokumentumok alakzatainak képarányát az Aspose.Words for .NET segítségével. Ha követi ezeket a lépéseket, biztosíthatja, hogy képei és formái megőrizzék arányaikat, így a dokumentumok professzionális megjelenésűek és csiszoltak. Nyugodtan kísérletezzen különböző képekkel és alakzatokkal, hogy megtudja, hogyan működik a képarány-rögzítés a különböző forgatókönyvekben.

## GYIK

### Feloldhatom a képarány zárolását a zárolás után?
Igen, beállítással feloldhatja a képarányt`shape.AspectRatioLocked = false`.

### Mi történik, ha átméretezek egy képet zárolt képarány mellett?
A kép arányosan átméreteződik, megtartva eredeti szélesség-magasság arányát.

### Alkalmazhatom ezt a képeken kívül más alakzatokra is?
Teljesen! A képarány-rögzítési funkció bármilyen formára alkalmazható, beleértve a téglalapokat, köröket és egyebeket.

### Az Aspose.Words for .NET kompatibilis a .NET Core-al?
Igen, az Aspose.Words for .NET támogatja a .NET-keretrendszert és a .NET Core-t is.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
 Átfogó dokumentációt találhat[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
