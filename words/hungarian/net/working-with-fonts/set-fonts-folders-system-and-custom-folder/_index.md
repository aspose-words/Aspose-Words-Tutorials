---
title: Set Fonts Folders System és egyéni mappa
linktitle: Set Fonts Folders System és egyéni mappa
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan állíthat be rendszer- és egyéni betűtípus-mappákat a Word-dokumentumokban az Aspose.Words for .NET segítségével, így biztosítva, hogy a dokumentumok megfelelően jelenjenek meg a különböző környezetekben.
weight: 10
url: /hu/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set Fonts Folders System és egyéni mappa

## Bevezetés

Képzelje el, hogy egy dokumentumot készít egyedi betűstílussal, de csak azt tapasztalja, hogy a betűtípusok nem jelennek meg megfelelően egy másik gépen. Frusztráló, igaz? Itt jön képbe a betűtípusmappák konfigurálása. Az Aspose.Words for .NET segítségével rendszer- és egyéni betűtípus-mappákat definiálhat, így biztosíthatja, hogy dokumentumai mindig a kívánt módon nézzenek ki. Nézzük meg, hogyan érheti el ezt.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

-  Aspose.Words for .NET Library: Ha még nem tette meg, töltse le[itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Egy IDE, mint a Visual Studio.
- Alapvető C# ismerete: A C# ismerete segít a kódpéldák követésében.

## Névterek importálása

Először is importálja a szükséges névtereket a projektbe:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most bontsuk le a folyamatot egyszerű lépésekre.

## 1. lépés: Töltse be a dokumentumot

 Kezdésként töltse be a Word-dokumentumot egy Aspose.Words-be`Document` objektum. Ez a dokumentum lesz az, ahol be szeretné állítani a font mappákat.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## 2. lépés: Inicializálja a betűtípus-beállításokat

 Hozzon létre egy új példányt a`FontSettings`. Ez az objektum lehetővé teszi a betűtípus-források kezelését.

```csharp
FontSettings fontSettings = new FontSettings();
```

## 3. lépés: A rendszer betűtípus-forrásainak lekérése

Az alapértelmezett rendszer-betűtípus-források lekérése. Windows rendszerű gépen ez általában a „Windows\Fonts\" könyvtárat.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## 4. lépés: Adjon hozzá egy egyéni betűtípus-mappát

Adjon hozzá egy egyéni mappát, amely tartalmazza a további betűtípusokat. Ez akkor hasznos, ha bizonyos betűtípusok nincsenek telepítve a rendszer betűkészlet-könyvtárába.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## 5. lépés: Frissítse a betűtípusforrásokat

 Alakítsa vissza a fontforrások listáját tömbbé, és állítsa be a`FontSettings` objektum.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## 6. lépés: Alkalmazza a betűtípus-beállításokat a dokumentumra

 Végül alkalmazza a konfigurált`FontSettings` a dokumentumba, és mentse el a kívánt formátumban, például PDF-ben.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Következtetés

És megvan! Az alábbi lépések követésével biztosíthatja, hogy Word-dokumentumai a megfelelő betűtípusokat használják, legyenek azok rendszer- vagy egyéni betűtípusok, amelyeket egy adott könyvtárban tárolnak. Ez a beállítás segít megőrizni a dokumentum megjelenésének integritását a különböző környezetekben.

## GYIK

### Mi történik, ha egy betűtípus hiányzik a rendszerben és az egyéni mappákban is?

Az Aspose.Words alapértelmezett betűtípust használ a hiányzó betűtípus pótlására, biztosítva a dokumentum olvashatóságát.

### Hozzáadhatok több egyéni betűtípus-mappát?

 Igen, több egyéni betűtípus-mappát is hozzáadhat a létrehozási folyamat megismétlésével`FolderFontSource` objektumokat, és hozzáadjuk őket a fontforrások listájához.

### Lehetséges-e hálózati útvonalakat használni az egyéni betűtípus-mappákhoz?

 Igen, megadhat hálózati elérési utat a`FolderFontSource` konstruktőr.

### Milyen fájlformátumokat támogat az Aspose.Words a dokumentumok mentéséhez?

Az Aspose.Words különféle formátumokat támogat, beleértve a DOCX, PDF, HTML és egyebeket.

### Hogyan kezelhetem a betűtípuscsere-értesítéseket?

 A betűtípus-helyettesítési értesítéseket a következővel kezelheti`FontSettings` osztályé`FontSubstitutionWarning`esemény.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
