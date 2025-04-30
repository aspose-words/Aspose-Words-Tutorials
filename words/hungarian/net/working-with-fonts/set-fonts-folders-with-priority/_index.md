---
"description": "Tanuld meg, hogyan állíthatsz be betűtípus-mappákat prioritás szerint a Word-dokumentumokban az Aspose.Words for .NET használatával. Útmutatónk biztosítja, hogy dokumentumaid minden alkalommal tökéletesen jelenjenek meg."
"linktitle": "Betűtípusok mappáinak prioritás szerinti beállítása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Betűtípusok mappáinak prioritás szerinti beállítása"
"url": "/hu/net/working-with-fonts/set-fonts-folders-with-priority/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípusok mappáinak prioritás szerinti beállítása

## Bevezetés

A dokumentumkezelés világában az egyéni betűtípus-mappák beállítása óriási különbséget jelenthet annak biztosításában, hogy a dokumentumok tökéletesen jelenjenek meg, függetlenül attól, hogy hol tekintik meg őket. Ma belemerülünk abba, hogyan állíthat be prioritást a betűtípus-mappáknak a Word-dokumentumokban az Aspose.Words for .NET használatával. Ez az átfogó útmutató végigvezeti Önt minden lépésen, hogy a folyamat a lehető legzökkenőmentesebb legyen.

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy mindenünk megvan, amire szükségünk van. Íme egy gyors ellenőrzőlista:

- Aspose.Words .NET-hez: Telepítenie kell ezt a könyvtárat. Ha még nincs telepítve, megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Győződjön meg arról, hogy rendelkezik egy működő .NET fejlesztői környezettel, például a Visual Studio-val.
- Dokumentumkönyvtár: Győződjön meg róla, hogy van egy könyvtára a dokumentumainak. Példáinkban a következőt fogjuk használni: `"YOUR DOCUMENT DIRECTORY"` helyőrzőként ehhez az útvonalhoz.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ezek a névterek elengedhetetlenek az Aspose.Words által biztosított osztályok és metódusok eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most bontsuk le az egyes lépéseket a betűtípus-mappák prioritásának beállításához.

## 1. lépés: Betűtípus-források beállítása

Először is meg kell határoznod a betűtípus-forrásokat. Itt tudod megadni az Aspose.Words számára, hogy hol keresse a betűtípusokat. Több betűtípus-mappát is megadhatsz, sőt, akár a prioritásukat is beállíthatod.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

Ebben a példában két betűtípus-forrást állítunk be:
- SystemFontSource: Ez az alapértelmezett betűtípusforrás, amely tartalmazza a rendszerre telepített összes betűtípust.
- FolderFontSource: Ez egy egyéni betűtípus-mappa, amely a következő címen található: `C:\\MyFonts\\`. A `true` paraméter meghatározza, hogy ezt a mappát rekurzívan kell beolvasni, és `1` prioritását határozza meg.

## 2. lépés: Töltse be a dokumentumot

Ezután töltse be a dokumentumot, amellyel dolgozni szeretne. Győződjön meg arról, hogy a dokumentum a megadott könyvtárban található.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Ez a kódsor betölt egy nevű dokumentumot. `Rendering.docx` a dokumentumkönyvtáradból.

## 3. lépés: Mentse el a dokumentumot az új betűtípus-beállításokkal

Végül mentse el a dokumentumot. A mentéskor az Aspose.Words a megadott betűtípus-beállításokat fogja használni.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

Ez PDF formátumban menti a dokumentumot a dokumentumkönyvtárba a következő néven: `WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Következtetés

És íme! Sikeresen beállítottad a betűtípus-mappák prioritását az Aspose.Words for .NET használatával. Egyéni betűtípus-mappák és prioritások megadásával biztosíthatod, hogy a dokumentumok konzisztensen jelenjenek meg, függetlenül attól, hogy hol tekintik meg őket. Ez különösen hasznos olyan környezetekben, ahol bizonyos betűtípusok nincsenek alapértelmezés szerint telepítve.

## GYIK

### Miért kellene egyéni betűtípus-mappákat beállítanom?
Az egyéni betűtípus-mappák beállítása biztosítja, hogy a dokumentumok helyesen jelenjenek meg, még akkor is, ha olyan betűtípusokat használnak, amelyek nincsenek telepítve azon a rendszeren, amelyen megtekintik őket.

### Beállíthatok több egyéni betűtípus-mappát?
Igen, több betűtípus-mappát is megadhat. Az Aspose.Words lehetővé teszi az egyes mappák prioritásának beállítását, biztosítva, hogy a legfontosabb betűtípusok legyenek először megtalálhatók.

### Mi történik, ha egy betűtípus hiányzik az összes megadott forrásból?
Ha egy betűtípus hiányzik az összes megadott forrásból, az Aspose.Words egy tartalék betűtípust használ annak biztosítására, hogy a dokumentum továbbra is olvasható maradjon.

### Meg lehet változtatni a rendszerbetűtípusok prioritását?
A rendszerbetűtípusok alapértelmezés szerint mindig szerepelnek, de beállíthatja a prioritásukat az egyéni betűtípusmappákhoz képest.

### Lehetséges hálózati elérési utakat használni egyéni betűtípus-mappákhoz?
Igen, megadhat hálózati elérési utakat egyéni betűtípus-mappákként, így központosíthatja a betűtípus-erőforrásokat egy hálózati helyen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}