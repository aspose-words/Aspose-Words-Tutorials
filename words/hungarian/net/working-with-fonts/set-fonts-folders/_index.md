---
"description": "Tanuld meg, hogyan állíthatsz be egyéni betűtípus-mappákat az Aspose.Words for .NET programban ezzel az átfogó, lépésről lépésre haladó útmutatóval. Tökéletes azoknak a fejlesztőknek, akik a dokumentumok betűtípusait szeretnék fejleszteni."
"linktitle": "Betűtípusok beállítása mappák"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Betűtípusok beállítása mappák"
"url": "/hu/net/working-with-fonts/set-fonts-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípusok beállítása mappák

## Bevezetés

Sziasztok! Készen állsz belemerülni az Aspose.Words for .NET egyéni betűtípusainak világába? Kezdjük is! Ez az útmutató végigvezet az egyéni betűtípus-mappák beállításának folyamatán, biztosítva, hogy dokumentumaid pontosan úgy nézzenek ki, ahogyan szeretnéd. Akár tapasztalt fejlesztő vagy, akár most kezded, ez az útmutató végigvezet a lépéseken. Szóval, nézzük meg, hogyan varázsoljuk mesésen kinézetű betűtípusokat!

## Előfeltételek

Mielőtt belevágnánk, győződjünk meg róla, hogy minden megvan, amire szükséged van:

- Aspose.Words .NET-hez: Meg tudod csinálni [letöltés](https://releases.aspose.com/words/net/) ha még nem tetted meg.
- Visual Studio: Bármelyik verzió működik, de a legújabb mindig a legjobb.
- Dokumentum: Ehhez az oktatóanyaghoz egy Word-dokumentumot fogunk használni. Létrehozhatsz sajátot, vagy használhatsz egy meglévőt.
- Egyéni betűtípusok: Készíts elő néhány egyéni betűtípust. Ezekkel fogjuk bemutatni, hogyan állíthatod be a betűtípusmappákat.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez elengedhetetlen ahhoz, hogy az Aspose.Words-ből elérhessük a szükséges osztályokat és metódusokat.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Miután importáltuk ezeket a névtereket, készen állunk az egyéni betűtípus-mappák beállításának megkezdésére.

## 1. lépés: Dokumentumkönyvtár meghatározása

Kezdjük a dokumentumkönyvtár elérési útjának meghatározásával. Ez az a hely, ahol a Word-dokumentum tárolódik. Egy úgynevezett változót fogunk használni. `dataDir` hogy tárolja ezt az útvonalat.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Csere `"YOUR DOCUMENT DIRECTORY"` a könyvtár tényleges elérési útjával. Ez azért kulcsfontosságú, mert az Aspose.Words-nek tudnia kell, hol találja a dokumentumot.

## 2. lépés: Betűtípus-források beállítása

Ezután be kell állítanunk a betűtípus-forrásokat. Itt adjuk meg az Aspose.Words-nek, hogy hol találja az egyéni betűtípusokat. A következőt fogjuk használni: `FontSettings.DefaultInstance.SetFontsSources` módszer ennek elérésére.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Íme, mit csinálunk:

- SystemFontSource: Ez utasítja az Aspose.Words-t, hogy a rendszer alapértelmezett betűtípusait használja.
- FolderFontSource: Itt adjuk meg az egyéni betűtípusokat tartalmazó mappát. Csere `"C:\\MyFonts\\"` az egyéni betűtípusok könyvtárának elérési útjával. `true` paraméter azt jelzi, hogy az alkönyvtárakat is bele kell foglalni.

## 3. lépés: Töltse be a dokumentumot

Most, hogy beállítottuk a betűtípus-forrásokat, itt az ideje betölteni a dokumentumot, amellyel dolgozni szeretnénk. A következőt fogjuk használni: `Document` osztály az Aspose-tól. Szavak erre.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Győződjön meg róla, hogy `"Rendering.docx"` a Word-dokumentum neve. Ha a dokumentumnak más a neve, akkor frissítse azt megfelelően.

## 4. lépés: Mentse el a dokumentumot PDF formátumban

Végül mentsük el a dokumentumot PDF formátumban, hogy működés közben is láthassuk az egyéni betűtípusokat. Használni fogjuk a `Save` a módszer `Document` osztály.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Ez PDF formátumban menti a dokumentumot a megadott könyvtárba, a korábban beállított egyéni betűtípusok használatával.

## Következtetés

És íme! Sikeresen beállítottál egyéni betűtípus-mappákat az Aspose.Words for .NET-ben, és PDF-ként mentetted a dokumentumodat ezekkel az egyéni betűtípusokkal. Elég klassz, ugye? A betűtípusok testreszabása hatalmas különbséget jelenthet a dokumentumok megjelenésében, és most már pontosan tudod, hogyan kell csinálni. Jó kódolást!

## GYIK

### Hogyan telepíthetem az Aspose.Words for .NET programot?

Megteheted [letöltés](https://releases.aspose.com/words/net/) az Aspose.Words for .NET legújabb verzióját a weboldalról.

### Használhatok több egyéni betűtípus-mappát?

Igen, többet is hozzáadhatsz `FolderFontSource` példányok a `SetFontsSources` módszer különböző könyvtárakból származó betűtípusok használatára.

### Szükséges rendszerbetűtípusokat használni?

A rendszerbetűtípusok használata opcionális, de ajánlott, hogy minden szabványos betűtípus elérhető legyen.

### Milyen fájltípusokat támogat az Aspose.Words?

Az Aspose.Words számos fájlformátumot támogat, beleértve a DOCX, DOC, PDF, TXT, HTML és sok mást.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words-höz?

Szerezhetsz egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/) az Aspose weboldaláról, hogy kipróbálhassa az Aspose.Words összes funkcióját.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}