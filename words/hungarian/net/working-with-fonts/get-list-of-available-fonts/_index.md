---
"description": "Fedezd fel ebben a részletes, lépésről lépésre szóló útmutatóban, hogyan kérheted le az elérhető betűtípusok listáját az Aspose.Words for .NET használatával. Fejleszd betűtípus-kezelési készségeidet."
"linktitle": "Elérhető betűtípusok listájának lekérése"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Elérhető betűtípusok listájának lekérése"
"url": "/hu/net/working-with-fonts/get-list-of-available-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Elérhető betűtípusok listájának lekérése

## Bevezetés

Nehézséget okozott már a betűtípusok kezelése a Word-dokumentumaidban? Ha .NET-fejlesztő vagy, az Aspose.Words for .NET itt van, hogy megmentsen! Ez a hatékony könyvtár nemcsak a Word-dokumentumok programozott létrehozásában és kezelésében segít, hanem kiterjedt betűtípus-kezelési lehetőségeket is kínál. Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan kérheted le az elérhető betűtípusok listáját az Aspose.Words for .NET segítségével. Könnyed lépésekre bontjuk, hogy biztosan könnyen követhesd. Tehát vágjunk bele, és tegyük a betűtípus-kezelést gyerekjátékká!

## Előfeltételek

Mielőtt belekezdenénk, van néhány dolog, amire szükséged lesz:

- Aspose.Words for .NET: Győződjön meg róla, hogy telepítve van az Aspose.Words for .NET könyvtár. Letöltheti innen: [itt](https://releases.aspose.com/words/net/).
- Visual Studio: Ez a példa a Visual Studio-t használja fejlesztőkörnyezetként.
- .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a gépén.
- Dokumentumkönyvtár: Az a könyvtárútvonal, ahol a dokumentumok tárolva vannak.

## Névterek importálása

Először importáld a szükséges névtereket a projektedbe:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## 1. lépés: Betűtípus-beállítások inicializálása

Az első lépés a betűtípus-beállítások inicializálása. Ez lehetővé teszi a dokumentumok betűtípus-forrásainak kezelését.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Ez az osztály a betűtípus-helyettesítés és a betűtípus-források beállításainak megadására szolgál.
- fontSources: A jelenlegi betűtípus-beállításokból létrehozunk egy listát a meglévő betűtípus-forrásokról.

## 2. lépés: Dokumentumkönyvtár meghatározása

Ezután adja meg a dokumentum könyvtárának elérési útját. Itt fog betűtípusokat keresni az Aspose.Words.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: Ez a karakterlánc-változó a betűtípusokat tartalmazó könyvtár elérési útját tartalmazza. Csere `"YOUR DOCUMENT DIRECTORY"` a tényleges úttal.

## 3. lépés: Egyéni betűtípus-mappa hozzáadása

Most adj hozzá egy új mappaforrást, hogy az Aspose.Words ebben a mappában keressen betűtípusokat.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Ez az osztály egy mappa betűtípus-forrását jelöli. A második paraméter (`true`azt jelzi, hogy a betűtípusok rekurzívan kereshetők-e az almappákban.

## 4. lépés: Betűtípus-források frissítése

Adja hozzá az egyéni betűtípus-mappát a meglévő betűtípus-források listájához, és frissítse a betűtípus-beállításokat.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Hozzáadja az egyéni betűtípus-mappát a meglévő betűtípus-forrásokhoz.
- updatedFontSources: A betűtípus-források listáját tömbbé alakítja.

## 5. lépés: Betűtípusok lekérése és megjelenítése

Végül kérd le az elérhető betűtípusokat, és jelenítsd meg a részleteiket.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Lekéri az elérhető betűtípusok listáját a frissített lista első betűtípusforrásából.
- fontInfo: Egy példánya a következőnek: `PhysicalFontInfo` amely részletes információkat tartalmaz az egyes betűtípusokról.

## Következtetés

Gratulálunk! Sikeresen lekérted az elérhető betűtípusok listáját az Aspose.Words for .NET segítségével. Ez az oktatóanyag végigvezetett minden lépésen, a betűtípus-beállítások inicializálásától a betűtípus részleteinek megjelenítéséig. Ezzel a tudással most könnyedén kezelheted a betűtípusokat a Word-dokumentumaidban. Ne feledd, az Aspose.Words for .NET egy hatékony eszköz, amely jelentősen javíthatja a dokumentumfeldolgozási képességeidet. Tehát fedezz fel további funkciókat, amelyekkel még hatékonyabbá teheted a fejlesztési folyamatot.

## GYIK

### Használhatom az Aspose.Words for .NET-et más .NET keretrendszerekkel?
Igen, az Aspose.Words for .NET kompatibilis számos .NET keretrendszerrel, beleértve a .NET Core-t és a .NET 5+-t.

### Hogyan telepíthetem az Aspose.Words for .NET programot?
Telepítheted a NuGet csomagkezelőn keresztül a Visual Studio-ban az „Aspose.Words” keresésével.

### Lehetséges több egyéni betűtípus-mappát hozzáadni?
Igen, több egyéni betűtípus-mappát is hozzáadhat több létrehozásával `FolderFontSource` példányok és azok hozzáadása a betűtípus-források listájához.

### Lekérhetem a betűtípus részleteit egy adott betűtípusforrásból?
Igen, betűtípus-adatokat bármely betűtípus-forrásból lekérhet a betűtípus-forrás indexének megadásával a `updatedFontSources` sor.

### Az Aspose.Words for .NET támogatja a betűtípus-helyettesítést?
Igen, támogatja a betűtípus-helyettesítést, hogy a szöveg helyesen jelenjen meg, még akkor is, ha az eredeti betűtípus nem érhető el.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}