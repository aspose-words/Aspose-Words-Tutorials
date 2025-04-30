---
"description": "Ismerje meg, hogyan állíthat be rendszer- és egyéni betűtípusmappákat a Word-dokumentumokban az Aspose.Words for .NET használatával, biztosítva, hogy a dokumentumok megfelelően jelenjenek meg különböző környezetekben."
"linktitle": "Betűtípusok beállítása Mappák Rendszer és Egyéni mappa"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Betűtípusok beállítása Mappák Rendszer és Egyéni mappa"
"url": "/hu/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípusok beállítása Mappák Rendszer és Egyéni mappa

## Bevezetés

Képzeld el, hogy egy egyedi betűtípussal rendelkező dokumentumot írsz, majd rájössz, hogy a betűtípusok nem jelennek meg megfelelően egy másik gépen. Frusztráló, ugye? Itt jön képbe a betűtípus-mappák konfigurálása. Az Aspose.Words for .NET segítségével rendszer- és egyéni betűtípus-mappákat definiálhatsz, hogy a dokumentumok mindig a kívánt módon nézzenek ki. Nézzük meg, hogyan érheted el ezt.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy a következők megvannak:

- Aspose.Words .NET könyvtárhoz: Ha még nem tetted meg, töltsd le [itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Egy IDE, mint például a Visual Studio.
- C# alapismeretek: A C# ismerete segít a kódpéldák követésében.

## Névterek importálása

Először importáld a szükséges névtereket a projektedbe:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most pedig bontsuk le a folyamatot egyszerű lépésekre.

## 1. lépés: A dokumentum betöltése

Kezdésként töltsd be a Word dokumentumodat egy Aspose.Words fájlba. `Document` objektum. Ebben a dokumentumban szeretnéd beállítani a betűtípus-mappákat.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## 2. lépés: Betűtípus-beállítások inicializálása

Hozzon létre egy új példányt a következőből: `FontSettings`Ez az objektum lehetővé teszi a betűtípus-források kezelését.

```csharp
FontSettings fontSettings = new FontSettings();
```

## 3. lépés: Rendszerbetűtípus-források lekérése

Az alapértelmezett rendszerbetűtípus-források lekérése. Windowsos gépen ez általában a „Windows\Fonts” könyvtárat tartalmazza.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## 4. lépés: Egyéni betűtípus-mappa hozzáadása

Adjon hozzá egy egyéni mappát, amely a további betűtípusokat tartalmazza. Ez akkor hasznos, ha bizonyos betűtípusok nincsenek telepítve a rendszerbetűtípusok könyvtárában.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## 5. lépés: Betűtípus-források frissítése

Alakítsa vissza a betűtípus-források listáját tömbbé, és állítsa be a következőre: `FontSettings` objektum.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## 6. lépés: Betűtípus-beállítások alkalmazása a dokumentumra

Végül alkalmazza a konfigurált `FontSettings` a dokumentumodba, és mentsd el a kívánt formátumban, például PDF-ben.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Következtetés

És íme! A következő lépések követésével biztosíthatja, hogy Word-dokumentumai a megfelelő betűtípusokat használják, legyenek azok rendszerbetűtípusok vagy egy adott könyvtárban tárolt egyéni betűtípusok. Ez a beállítás segít megőrizni a dokumentum megjelenésének integritását különböző környezetekben.

## GYIK

### Mi történik, ha egy betűtípus hiányzik mind a rendszer-, mind az egyéni mappákból?

Az Aspose.Words egy alapértelmezett betűtípust fog használni a hiányzó betűtípus helyettesítésére, biztosítva, hogy a dokumentum olvasható maradjon.

### Hozzáadhatok több egyéni betűtípus-mappát?

Igen, több egyéni betűtípus-mappát is hozzáadhat a létrehozási folyamat megismétlésével. `FolderFontSource` objektumok és azok hozzáadása a betűtípusforrások listájához.

### Lehetséges hálózati elérési utakat használni egyéni betűtípus-mappákhoz?

Igen, megadhat egy hálózati útvonalat a `FolderFontSource` konstruktőr.

### Milyen fájlformátumokat támogat az Aspose.Words a dokumentumok mentéséhez?

Az Aspose.Words számos formátumot támogat, beleértve a DOCX-et, PDF-et, HTML-t és egyebeket.

### Hogyan kezelhetem a betűtípus-helyettesítési értesítéseket?

A betűtípus-helyettesítési értesítéseket a következővel kezelheti: `FontSettings` osztály `FontSubstitutionWarning` esemény.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}