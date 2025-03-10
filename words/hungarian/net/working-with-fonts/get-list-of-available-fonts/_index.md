---
title: Szerezze meg az elérhető betűtípusok listáját
linktitle: Szerezze meg az elérhető betűtípusok listáját
second_title: Aspose.Words Document Processing API
description: Fedezze fel, hogyan szerezheti meg az elérhető betűtípusok listáját az Aspose.Words for .NET használatával ebben a részletes, lépésről lépésre mutató oktatóanyagban. Növelje fontkezelési készségeit.
weight: 10
url: /hu/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Szerezze meg az elérhető betűtípusok listáját

## Bevezetés

Volt már olyan, hogy nehézségekkel küzd a betűtípusok kezelésével a Word-dokumentumokban? Ha Ön .NET-fejlesztő, az Aspose.Words for .NET megmenti Önt! Ez a hatékony könyvtár nemcsak a Word-dokumentumok programozott létrehozásában és kezelésében segít, hanem kiterjedt betűtípus-kezelési lehetőségeket is kínál. Ebben az útmutatóban lépésről lépésre végigvezetjük az Aspose.Words for .NET használatával elérhető betűtípusok listáját. Könnyen követhető lépésekre bontjuk. Szóval, merüljünk bele, és tegyük gyerekjátékká a betűkészletkezelést!

## Előfeltételek

Mielőtt elkezdenénk, van néhány dolog, amire szüksége lesz:

-  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words for .NET könyvtár. Letöltheti innen[itt](https://releases.aspose.com/words/net/).
- Visual Studio: Ez a példa a Visual Studio-t használja fejlesztői környezetként.
- .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a számítógépen.
- Dokumentumkönyvtár: Az a könyvtár elérési útja, ahol a dokumentumokat tárolják.

## Névterek importálása

Először is importálja a szükséges névtereket a projektbe:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## 1. lépés: Inicializálja a betűtípus-beállításokat

Az első lépés a betűtípus-beállítások inicializálása. Ez lehetővé teszi a dokumentumok betűtípus-forrásainak kezelését.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Ez az osztály a betűkészlet-helyettesítés és a betűtípus-források beállításainak megadására szolgál.
- fontSources: Az aktuális betűkészlet-beállításokból létrehozunk egy listát a meglévő fontforrásokról.

## 2. lépés: Határozza meg a dokumentumkönyvtárat

Ezután adja meg a dokumentumkönyvtár elérési útját. Az Aspose.Words itt fog betűtípusokat keresni.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Ez a karakterlánc-változó tartalmazza annak a könyvtárnak az elérési útját, ahol a betűtípusok találhatók. Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges úttal.

## 3. lépés: Adjon hozzá egyéni betűtípus-mappát

Most adjon hozzá egy új mappaforrást, és utasítsa az Aspose.Words-t, hogy keressen ebben a mappában betűtípusokat.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Ez az osztály egy mappa betűtípus-forrást jelöl. A második paraméter (`true`) jelzi, hogy kell-e rekurzívan keresni a betűtípusokat az almappákban.

## 4. lépés: Frissítse a betűtípusforrásokat

Adja hozzá az egyéni betűtípus mappát a meglévő fontforrások listájához, és frissítse a betűtípus-beállításokat.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Az egyéni betűtípus-mappát hozzáadja a meglévő fontforrásokhoz.
- updatedFontSources: A betűtípus-források listáját tömbbé alakítja.

## 5. lépés: Töltse le és jelenítse meg a betűtípusokat

Végül kérje le az elérhető betűtípusokat, és jelenítse meg azok részleteit.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Lekéri az elérhető betűtípusok listáját a frissített lista első fontforrásából.
-  fontInfo: A`PhysicalFontInfo` részleteket tartalmaz az egyes betűtípusokról.

## Következtetés

Gratulálok! Sikeresen lekérte az elérhető betűtípusok listáját az Aspose.Words for .NET használatával. Ez az oktatóanyag végigvezeti Önt minden lépésen, a betűtípus-beállítások inicializálásától a betűtípus részleteinek megjelenítéséig. Ezzel a tudással most már könnyedén kezelheti a betűtípusokat Word-dokumentumaiban. Ne feledje, az Aspose.Words for .NET egy hatékony eszköz, amely jelentősen javíthatja dokumentumfeldolgozási képességeit. Tehát menjen tovább, és fedezzen fel további funkciókat, hogy még hatékonyabbá tegye fejlesztési folyamatát.

## GYIK

### Használhatom az Aspose.Words for .NET-et más .NET-keretrendszerekkel?
Igen, az Aspose.Words for .NET kompatibilis különféle .NET-keretrendszerekkel, beleértve a .NET Core-t és a .NET 5+-t.

### Hogyan telepíthetem az Aspose.Words for .NET fájlt?
Telepítheti a NuGet Package Manageren keresztül a Visual Studio alkalmazásban az „Aspose.Words” kifejezésre keresve.

### Lehetséges több egyéni betűtípus-mappa hozzáadása?
 Igen, több egyéni betűtípus-mappát is hozzáadhat több létrehozásával`FolderFontSource` példányokat, és hozzáadjuk őket a fontforrások listájához.

### Lekérhetem a betűtípus részleteit egy adott fontforrásból?
 Igen, lekérheti a betűtípus részleteit bármely fontforrásból, ha megadja a betűtípus forrásának indexét a`updatedFontSources` sor.

### Az Aspose.Words for .NET támogatja a betűtípusok helyettesítését?
Igen, támogatja a betűkészlet-helyettesítést, hogy a szöveg akkor is helyesen jelenjen meg, ha az eredeti betűtípus nem elérhető.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
