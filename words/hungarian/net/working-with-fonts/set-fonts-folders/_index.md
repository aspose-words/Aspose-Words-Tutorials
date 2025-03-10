---
title: Állítsa be a Fonts mappákat
linktitle: Állítsa be a Fonts mappákat
second_title: Aspose.Words Document Processing API
description: Ebből az átfogó, lépésenkénti útmutatóból megtudhatja, hogyan állíthat be egyéni betűtípus-mappákat az Aspose.Words for .NET-ben. Tökéletes azoknak a fejlesztőknek, akik javítani szeretnék a dokumentum-betűtípusokat.
weight: 10
url: /hu/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a Fonts mappákat

## Bevezetés

Szia! Készen áll, hogy belemerüljön az egyéni betűtípusok világába az Aspose.Words for .NET-ben? Kezdjük. Ez az oktatóanyag végigvezeti Önt az egyéni betűtípus-mappák beállításának folyamatán, biztosítva, hogy a dokumentumok úgy nézzenek ki, ahogyan szeretné. Akár tapasztalt fejlesztő, akár csak most kezdő, ez az útmutató végigvezeti Önt minden lépésen. Szóval, tegyük csodálatosan a betűtípusokat!

## Előfeltételek

Mielőtt belevágnánk, győződjünk meg arról, hogy mindent megvan, amire szüksége van:

-  Aspose.Words for .NET: Megteheti[letöltés](https://releases.aspose.com/words/net/) ha még nem tetted meg.
- Visual Studio: Bármelyik verzió működik, de mindig a legújabb a legjobb.
- Dokumentum: Ehhez az oktatóanyaghoz egy Word-dokumentumot fogunk használni. Létrehozhat sajátot, vagy használhat egy meglévőt.
- Egyéni betűtípusok: Készítsen néhány egyéni betűtípust. Ezeket a betűtípusmappák beállításának bemutatására fogjuk használni.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez elengedhetetlen az Aspose.Words-ból szükséges osztályok és metódusok eléréséhez.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Miután ezeket a névtereket importáltuk, készen állunk az egyéni betűtípus-mappák beállítására.

## 1. lépés: Határozza meg a dokumentumkönyvtárat

 Kezdjük a dokumentumkönyvtár elérési útjának meghatározásával. Ez az a hely, ahol a Word dokumentumot tárolják. nevű változót fogjuk használni`dataDir` tárolni ezt az utat.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a címtár tényleges elérési útjával. Ez döntő fontosságú, mert az Aspose.Words-nek tudnia kell, hol találja a dokumentumot.

## 2. lépés: Állítsa be a betűtípusok forrásait

 Ezután be kell állítanunk a fontforrásokat. Itt mondjuk meg az Aspose.Wordsnak, hogy hol találhatja meg egyéni betűtípusainkat. Használni fogjuk a`FontSettings.DefaultInstance.SetFontsSources` módszer ennek elérésére.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Íme, mit csinálunk:

- SystemFontSource: Ez arra utasítja az Aspose.Words-t, hogy a rendszer alapértelmezett betűtípusait használja.
-  FolderFontSource: Itt adjuk meg az egyéni betűtípusainkat tartalmazó mappát. Cserélje ki`"C:\\MyFonts\\"` az egyéni betűtípus-könyvtár elérési útjával. A`true` paraméter azt jelzi, hogy az alkönyvtárakat is bele kell foglalni.

## 3. lépés: Töltse be a dokumentumot

Most, hogy beállítottuk a fontforrásainkat, ideje betölteni azt a dokumentumot, amellyel dolgozni szeretnénk. Használjuk a`Document` osztály Aspose-tól.Szavak erre.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Biztosítsd ezt`"Rendering.docx"` a Word dokumentum neve. Ha a dokumentumának más a neve, mindenképpen frissítse ennek megfelelően.

## 4. lépés: Mentse el a dokumentumot PDF formátumban

 Végül mentsük el a dokumentumunkat PDF formátumban, hogy működés közben lássuk az egyéni betűtípusokat. Használjuk a`Save` módszere a`Document` osztály.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Ezzel a dokumentumot PDF formátumban menti a megadott könyvtárba, a korábban beállított egyéni betűtípusok használatával.

## Következtetés

És megvan! Sikeresen beállította az egyéni betűtípus-mappákat az Aspose.Words for .NET-ben, és PDF formátumban mentette a dokumentumot ezekkel az egyéni betűtípusokkal. Nagyon klassz, igaz? A betűtípusok testreszabása óriási változást hozhat a dokumentumok megjelenésében, és most már pontosan tudja, hogyan kell ezt megtenni. Boldog kódolást!

## GYIK

### Hogyan telepíthetem az Aspose.Words for .NET fájlt?

 Megteheti[letöltés](https://releases.aspose.com/words/net/) az Aspose.Words for .NET legújabb verziója a webhelyről.

### Használhatok több egyéni betűtípus-mappát?

 Igen, többször is hozzáadhat`FolderFontSource` példányok a`SetFontsSources`módszer a különböző könyvtárakból származó betűtípusok használatára.

### Szükséges-e rendszerbetűtípusok szerepeltetése?

A rendszerbetűkészletek használata nem kötelező, de ajánlott, hogy az összes szabványos betűtípus elérhető legyen.

### Milyen fájltípusokat támogat az Aspose.Words?

Az Aspose.Words a fájlformátumok széles skáláját támogatja, beleértve a DOCX, DOC, PDF, TXT, HTML és még sok más formátumot.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words számára?

 Megszerezheti a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) az Aspose webhelyéről, hogy kipróbálhassa az Aspose.Words teljes funkcióját.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
