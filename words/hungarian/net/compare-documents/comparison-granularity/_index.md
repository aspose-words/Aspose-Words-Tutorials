---
"description": "Ismerje meg az Aspose.Words for .NET Word-dokumentumokban a részletesség összehasonlítása funkcióját, amely lehetővé teszi a dokumentumok karakterenkénti összehasonlítását, és a végrehajtott módosítások jelentését."
"linktitle": "Összehasonlítási részletesség Word-dokumentumban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Összehasonlítási részletesség Word-dokumentumban"
"url": "/hu/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Összehasonlítási részletesség Word-dokumentumban

Az alábbiakban egy lépésről lépésre bemutatjuk a C# forráskódot, amely az Aspose.Words for .NET „Compare Granularity in Word document” funkcióját használja.

## 1. lépés: Bevezetés

Az Aspose.Words for .NET Compare Granularity funkciója lehetővé teszi a dokumentumok karakterszintű összehasonlítását. Ez azt jelenti, hogy minden karakter összehasonlításra kerül, és a változások ennek megfelelően kerülnek jelentésre.

## 2. lépés: A környezet beállítása

Mielőtt elkezdenéd, be kell állítanod a fejlesztői környezetedet az Aspose.Words for .NET használatához. Győződj meg róla, hogy telepítve van az Aspose.Words könyvtár, és van egy megfelelő C# projekted a kód beágyazásához.

## 3. lépés: Szükséges összeállítások hozzáadása

Az Aspose.Words for .NET Compare Granularity funkciójának használatához hozzá kell adnia a szükséges assembly-ket a projekthez. Győződjön meg arról, hogy a projektben megfelelő hivatkozások szerepelnek az Aspose.Words fájlra.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## 4. lépés: Dokumentumok létrehozása

Ebben a lépésben két dokumentumot fogunk létrehozni a DocumentBuilder osztály segítségével. Ezeket a dokumentumokat fogjuk használni az összehasonlításhoz.

```csharp
// Hozz létre egy A dokumentumot.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Hozd létre a B dokumentumot.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## 5. lépés: Összehasonlítási beállítások konfigurálása

Ebben a lépésben az összehasonlítási beállításokat fogjuk konfigurálni az összehasonlítás részletességének meghatározásához. Itt karakter szintű részletességet fogunk használni.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## 6. lépés: Dokumentum-összehasonlítás

Most hasonlítsuk össze a dokumentumokat a Document osztály Compare metódusával. A módosítások az A dokumentumban lesznek mentve.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

A `Compare` A metódus összehasonlítja az A dokumentumot a B dokumentummal, és menti a módosításokat az A dokumentumban. Megadhatja a szerző nevét és az összehasonlítás dátumát hivatkozásként.

## Következtetés

Ebben a cikkben az Aspose.Words for .NET részletességi összehasonlítás funkcióját vizsgáltuk meg. Ez a funkció lehetővé teszi a dokumentumok karakterszintű összehasonlítását és a változások jelentését. Ezt a tudást felhasználhatja részletes dokumentum-összehasonlítások elvégzésére a projektjeiben.

### Minta forráskód az összehasonlító granularitáshoz az Aspose.Words for .NET használatával

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Következtetés

Ebben az oktatóanyagban az Aspose.Words for .NET Összehasonlító részletesség funkcióját vizsgáltuk meg. Ez a funkció lehetővé teszi a dokumentumok összehasonlításának részletességi szintjének megadását. Különböző részletességi szintek kiválasztásával részletes összehasonlításokat végezhet karakter-, szó- vagy blokkszinten, az adott igényektől függően. Az Aspose.Words for .NET rugalmas és hatékony dokumentum-összehasonlító képességet biztosít, amely megkönnyíti a különböző részletességi szintű dokumentumok közötti különbségek azonosítását.

### GYIK

#### K: Mi a célja az összehasonlítási granularitás használatának az Aspose.Words for .NET-ben?

A: Az Aspose.Words for .NET összehasonlítási részletessége lehetővé teszi a dokumentumok összehasonlításakor a részletesség szintjének megadását. Ezzel a funkcióval különböző szinteken, például karakterszinten, szószinten vagy akár blokkszinten hasonlíthatja össze a dokumentumokat. Minden részletességi szint eltérő részletességet biztosít az összehasonlítási eredményekben.

#### K: Hogyan használhatom az összehasonlítási granularitást az Aspose.Words for .NET-ben?

A: Az összehasonlítási granularitás használatához az Aspose.Words for .NET-ben kövesse az alábbi lépéseket:
1. Állítsd be a fejlesztői környezetedet az Aspose.Words könyvtárral.
2. Add hozzá a szükséges assembly-ket a projektedhez az Aspose.Words fájlra hivatkozva.
3. Hozza létre az összehasonlítani kívánt dokumentumokat a `DocumentBuilder` osztály.
4. Konfigurálja az összehasonlítási beállításokat egy létrehozásával `CompareOptions` tárgy és a beállítás `Granularity` a kívánt szintre (pl. `Granularity.CharLevel` karakter szintű összehasonlításhoz).
5. Használd a `Compare` metódust az egyik dokumentumon, átadva a másik dokumentumot és a `CompareOptions` objektum paraméterként. Ez a metódus a megadott részletesség alapján összehasonlítja a dokumentumokat, és menti a módosításokat az első dokumentumban.

#### K: Milyen összehasonlítási granularitási szintek érhetők el az Aspose.Words for .NET fájlban?

A: Az Aspose.Words for .NET három szintű összehasonlítási részletességet kínál:
- `Granularity.CharLevel`: Karakter szinten hasonlítja össze a dokumentumokat.
- `Granularity.WordLevel`: Szavak szintjén hasonlítja össze a dokumentumokat.
- `Granularity.BlockLevel`: Blokk szinten hasonlítja össze a dokumentumokat.

#### K: Hogyan értelmezhetem a karakter szintű részletességgel végzett összehasonlítás eredményeit?

V: Karakter szintű részletességgel az összehasonlított dokumentumokban minden egyes karaktert elemez a rendszer a különbségek szempontjából. Az összehasonlítás eredményei az egyes karakterek szintjén mutatnak változásokat, beleértve a kiegészítéseket, törléseket és módosításokat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}