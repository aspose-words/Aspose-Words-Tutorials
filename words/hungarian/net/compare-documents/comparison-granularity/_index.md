---
title: Összehasonlítás granulárisság Word dokumentumban
linktitle: Összehasonlítás granulárisság Word dokumentumban
second_title: Aspose.Words Document Processing API
description: Tanulja meg a részletesség összehasonlítását az Aspose.Words for .NET Word-dokumentum funkciójában, amely lehetővé teszi a dokumentumok karakterenkénti összehasonlítását, a végrehajtott változtatások jelentésével.
weight: 10
url: /hu/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Összehasonlítás granulárisság Word dokumentumban

Íme egy lépésről lépésre bemutatott útmutató a C# forráskód leírásához, amely az Aspose.Words for .NET-ben a Compare Granularity in Word dokumentum funkcióját használja.

## 1. lépés: Bevezetés

Az Aspose.Words for .NET részletességének összehasonlítása funkciója lehetővé teszi a dokumentumok karakterszintű összehasonlítását. Ez azt jelenti, hogy minden karaktert összehasonlítanak, és a változásokat ennek megfelelően jelentik.

## 2. lépés: A környezet beállítása

Mielőtt elkezdené, be kell állítania a fejlesztői környezetet az Aspose.Words for .NET használatához. Győződjön meg arról, hogy telepítve van az Aspose.Words könyvtár, és van egy megfelelő C# projekt a kód beágyazásához.

## 3. lépés: Adja hozzá a szükséges összeállításokat

Az Aspose.Words for .NET részletességének összehasonlítása funkciójának használatához hozzá kell adnia a szükséges összeállításokat a projekthez. Győződjön meg arról, hogy megfelelő hivatkozásokat tartalmaz az Aspose.Words-re a projektben.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## 4. lépés: Dokumentumok létrehozása

Ebben a lépésben két dokumentumot hozunk létre a DocumentBuilder osztály használatával. Ezeket a dokumentumokat használjuk fel az összehasonlításhoz.

```csharp
// Hozzon létre A dokumentumot.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Hozzon létre B dokumentumot.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## 5. lépés: Összehasonlítási beállítások konfigurálása

Ebben a lépésben az összehasonlítási beállításokat az összehasonlítás részletességének megadásához konfiguráljuk. Itt karakterszintű részletességet fogunk használni.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## 6. lépés: Dokumentumok összehasonlítása

Most hasonlítsuk össze a dokumentumokat a Dokumentum osztály Összehasonlítás metódusával. A változtatások az A dokumentumban lesznek elmentve.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 A`Compare`módszer összehasonlítja az A dokumentumot a B dokumentummal, és elmenti az A dokumentum módosításait. Referenciaként megadhatja a szerző nevét és az összehasonlítás dátumát.

## Következtetés

Ebben a cikkben megvizsgáltuk az Aspose.Words for .NET részletességének összehasonlítása funkcióját. Ez a funkció lehetővé teszi a dokumentumok karakterszintű összehasonlítását és a változások jelentését. Ezt a tudást felhasználhatja projektjei részletes dokumentum-összehasonlítására.

### Minta forráskód a Comparison Granularity számára az Aspose.Words for .NET használatával

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Következtetés

Ebben az oktatóanyagban megvizsgáltuk az Aspose.Words for .NET Comparison Granularity funkcióját. Ez a funkció lehetővé teszi a részletezettség meghatározását a dokumentumok összehasonlításakor. Különböző részletességi szintek kiválasztásával részletes összehasonlításokat végezhet karakter-, szó- vagy blokkszinten, az Ön egyedi igényeitől függően. Az Aspose.Words for .NET rugalmas és hatékony dokumentum-összehasonlítási lehetőséget biztosít, megkönnyítve a dokumentumok közötti különbségek azonosítását különböző részletességű dokumentumokban.

### GYIK

#### K: Mi a célja a Comparison Granularity használatának az Aspose.Words for .NET-ben?

V: Comparison Granularity in Aspose.Words for .NET lehetővé teszi, hogy meghatározza a részletességi szintet a dokumentumok összehasonlításakor. Ezzel a funkcióval különböző szintű dokumentumokat hasonlíthat össze, például karakterszinten, szószinten vagy akár blokkszinten. Az egyes részletességi szintek eltérő részletességet biztosítanak az összehasonlítási eredményekben.

#### K: Hogyan használhatom a Comparison Granularity-t az Aspose.Words for .NET-ben?

V: Az Aspose.Words for .NET-ben a Comparison Granularity használatához kövesse az alábbi lépéseket:
1. Állítsa be fejlesztői környezetét az Aspose.Words könyvtárral.
2. Adja hozzá a szükséges összeállításokat a projekthez az Aspose.Words hivatkozással.
3.  A segítségével hozza létre az összehasonlítani kívánt dokumentumokat`DocumentBuilder` osztály.
4.  Konfigurálja az összehasonlítási beállításokat a létrehozásával`CompareOptions` objektum és beállítás a`Granularity` tulajdonság a kívánt szintre (pl.`Granularity.CharLevel` karakterszintű összehasonlításhoz).
5.  Használja a`Compare`módszer az egyik dokumentumon, átadva a másik dokumentumot és a`CompareOptions` objektum paraméterként. Ez a módszer összehasonlítja a dokumentumokat a megadott részletesség alapján, és elmenti a módosításokat az első dokumentumban.

#### K: Milyen szintek érhetők el az Aspose.Words for .NET-ben az Összehasonlítási részletességnek?

V: Az Aspose.Words for .NET három szintű összehasonlítási részletességet biztosít:
- `Granularity.CharLevel`: Összehasonlítja a dokumentumokat karakterszinten.
- `Granularity.WordLevel`: A dokumentumokat szószinten hasonlítja össze.
- `Granularity.BlockLevel`: A dokumentumokat blokk szinten hasonlítja össze.

#### K: Hogyan értelmezhetem az összehasonlítási eredményeket karakterszintű részletességgel?

V: Karakterszintű részletességgel az összehasonlított dokumentumok minden karakterét elemzi a különbségek szempontjából. Az összehasonlítás eredményei az egyes karakterek szintjén mutatják meg a változásokat, beleértve a kiegészítéseket, törléseket és módosításokat.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
