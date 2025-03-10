---
title: Állítsa be a Fonts mappákat prioritással
linktitle: Állítsa be a Fonts mappákat prioritással
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan állíthat be prioritást a fontmappák számára a Word dokumentumokban az Aspose.Words for .NET használatával. Útmutatónk biztosítja, hogy dokumentumai minden alkalommal tökéletesen jelenjenek meg.
weight: 10
url: /hu/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a Fonts mappákat prioritással

## Bevezetés

A dokumentumkezelés világában az egyéni betűtípus-mappák beállítása világméretű különbséget jelenthet a dokumentumok tökéletes megjelenítésében, függetlenül attól, hogy hol tekintik meg őket. Ma belevetjük magunkat abba, hogyan állíthat be prioritást a fontmappák számára a Word-dokumentumokban az Aspose.Words for .NET segítségével. Ez az átfogó útmutató végigvezeti Önt az egyes lépéseken, így a folyamat a lehető legsimább lesz.

## Előfeltételek

Mielőtt hozzákezdenénk, győződjünk meg arról, hogy mindennel rendelkezünk, amire szükségünk van. Íme egy gyors ellenőrző lista:

-  Aspose.Words for .NET: Telepíteni kell ezt a könyvtárat. Ha még nincs meg, megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Győződjön meg arról, hogy rendelkezik működő .NET fejlesztői környezettel, mint például a Visual Studio.
-  Dokumentumkönyvtár: Győződjön meg arról, hogy rendelkezik könyvtárral a dokumentumok számára. Példáinkhoz használjuk`"YOUR DOCUMENT DIRECTORY"` ennek az útvonalnak a helyőrzőjeként.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ezek a névterek elengedhetetlenek az Aspose.Words által biztosított osztályok és metódusok eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most bontsuk le az egyes lépéseket a betűtípusmappák prioritásának beállításához.

## 1. lépés: Állítsa be a fontforrásokat

Kezdésként meg kell határoznia a betűtípusok forrásait. Itt adja meg az Aspose.Words-nek, hogy hol keressen betűtípusokat. Megadhat több betűtípus-mappát, és még prioritásukat is beállíthatja.

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
- SystemFontSource: Ez az alapértelmezett betűtípus-forrás, amely tartalmazza a rendszerre telepített összes betűtípust.
-  FolderFontSource: Ez egy egyéni betűtípus-mappa, amely a címen található`C:\\MyFonts\\` . A`true` paraméter határozza meg, hogy ezt a mappát rekurzívan kell vizsgálni, és`1` prioritást állít be.

## 2. lépés: Töltse be a dokumentumot

Ezután töltse be azt a dokumentumot, amellyel dolgozni szeretne. Győződjön meg arról, hogy a dokumentum a megadott könyvtárban található.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Ez a kódsor egy nevű dokumentumot tölt be`Rendering.docx` dokumentumkönyvtárából.

## 3. lépés: Mentse el a dokumentumot az új betűtípus-beállításokkal

Végül mentse el a dokumentumot. A dokumentum mentésekor az Aspose.Words az Ön által megadott betűtípus-beállításokat fogja használni.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

 Ezzel a dokumentumot PDF formátumban menti a névvel ellátott dokumentumkönyvtárába`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Következtetés

És megvan! Az Aspose.Words for .NET használatával sikeresen beállította a fontmappákat prioritásokkal. Egyéni betűtípus-mappák és prioritások megadásával biztosíthatja, hogy a dokumentumok következetesen jelenjenek meg, függetlenül attól, hogy hol tekintik meg őket. Ez különösen hasznos olyan környezetekben, ahol alapértelmezés szerint nincsenek bizonyos betűtípusok telepítve.

## GYIK

### Miért kell egyéni betűtípus-mappákat beállítanom?
Az egyéni betűtípusmappák beállítása biztosítja, hogy a dokumentumok megfelelően jelenjenek meg, még akkor is, ha olyan betűtípusokat használnak, amelyek nincsenek telepítve arra a rendszerre, ahol megtekintik őket.

### Beállíthatok több egyéni betűtípus-mappát?
Igen, több betűtípus mappát is megadhat. Az Aspose.Words lehetővé teszi az egyes mappák prioritásának beállítását, biztosítva, hogy először a legfontosabb betűtípusokat találja meg.

### Mi történik, ha egy betűtípus hiányzik az összes megadott forrásból?
Ha egy betűtípus hiányzik az összes megadott forrásból, az Aspose.Words tartalék betűtípust használ annak biztosítására, hogy a dokumentum továbbra is olvasható legyen.

### Módosíthatom a rendszer betűtípusainak prioritását?
A rendszer betűtípusai alapértelmezés szerint mindig szerepelnek, de beállíthatja a prioritásukat az egyéni betűtípusmappákhoz képest.

### Lehetséges-e hálózati útvonalakat használni az egyéni betűtípus-mappákhoz?
Igen, megadhat hálózati elérési útvonalakat egyéni betűtípusmappaként, lehetővé téve a betűkészlet-erőforrások hálózati helyen történő központosítását.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
