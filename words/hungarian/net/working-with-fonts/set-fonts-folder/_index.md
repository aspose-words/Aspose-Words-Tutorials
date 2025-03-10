---
title: Állítsa be a Fonts mappát
linktitle: Állítsa be a Fonts mappát
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan állíthat be egyéni betűtípusmappát az Aspose.Words for .NET-ben, hogy a Word-dokumentumok helyesen jelenjenek meg, anélkül, hogy betűtípusok hiányoznának.
weight: 10
url: /hu/net/working-with-fonts/set-fonts-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a Fonts mappát

## Bevezetés

Találkozott már olyan problémákkal, hogy hiányzik a betűtípus, miközben Word-dokumentumokkal dolgozott .NET-alkalmazásában? Nos, nem vagy egyedül. A megfelelő betűtípusmappa beállítása zökkenőmentesen megoldhatja ezt a problémát. Ebben az útmutatóban végigvezetjük, hogyan állíthatja be a fonts mappát az Aspose.Words for .NET használatával. Merüljünk el!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:

- A Visual Studio telepítve van a gépedre
- .NET-keretrendszer beállítása
-  Aspose.Words a .NET könyvtárhoz. Ha még nem tette meg, letöltheti innen[itt](https://releases.aspose.com/words/net/).

## Névterek importálása

Először is importálnia kell a szükséges névtereket az Aspose.Words használatához. Adja hozzá a következő sorokat a kódfájl tetejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

betűtípusmappa beállítása egyszerű, ha gondosan követi ezeket a lépéseket.

## 1. lépés: Határozza meg a dokumentumkönyvtárat

Minden más előtt határozza meg a dokumentumkönyvtár elérési útját. Ez a könyvtár tartalmazza a Word-dokumentumokat és a használni kívánt betűtípusokat.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ügyeljen arra, hogy cserélje ki`"YOUR DOCUMENT DIRECTORY"` a címtár tényleges elérési útjával.

## 2. lépés: A FontSettings inicializálása

 Most inicializálnia kell a`FontSettings` objektum. Ez az objektum lehetővé teszi egyéni betűtípus-mappák megadását.

```csharp
FontSettings fontSettings = new FontSettings();
```

## 3. lépés: Állítsa be a Fonts mappát

 A`SetFontsFolder` módszere a`FontSettings` objektumot, adja meg azt a mappát, ahol az egyéni betűtípusokat tárolja.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

 Itt,`dataDir + "Fonts"` a "Fonts" nevű mappára mutat a dokumentumkönyvtárban. A második paraméter,`false`, azt jelzi, hogy a mappa nem rekurzív.

## 4. lépés: Hozzon létre LoadOptions

 Ezután hozzon létre egy példányt a`LoadOptions` osztály. Ez az osztály segít a dokumentum betöltésében a megadott betűtípus-beállításokkal.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## 5. lépés: Töltse be a dokumentumot

 Végül töltse be a Word dokumentumot a`Document` osztály és a`LoadOptions` objektum.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

 Győződjön meg róla`"Rendering.docx"` a Word dokumentum neve. Lecserélheti a fájl nevére.

## Következtetés

És megvan! Az alábbi lépések követésével könnyedén beállíthat egy egyéni betűtípus-mappát az Aspose.Words for .NET-ben, így biztosítva, hogy az összes betűtípus helyesen jelenik meg. Ezzel az egyszerű beállítással sok fejfájást megkímélhet, és a dokumentumok pontosan úgy néznek ki, ahogy szeretné.

## GYIK

### Miért kell egyéni betűtípus mappát beállítanom?
Egyéni betűtípusmappa beállítása biztosítja, hogy a Word-dokumentumokban használt összes betűtípus helyesen jelenjen meg, elkerülve ezzel a hiányzó betűtípusokkal kapcsolatos problémákat.

### Beállíthatok több betűtípus mappát?
 Igen, használhatod a`SetFontsFolders` módszer több mappa megadására.

### Mi történik, ha a betűtípus nem található?
Az Aspose.Words megpróbálja a hiányzó betűtípust egy hasonlóval helyettesíteni a rendszer betűtípusai közül.

### Az Aspose.Words kompatibilis a .NET Core-al?
Igen, az Aspose.Words támogatja a .NET Core-t és a .NET-keretrendszert.

### Hol kaphatok támogatást, ha problémákkal szembesülök?
 Támogatást kaphat a[Aspose.Words támogatási fórum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
