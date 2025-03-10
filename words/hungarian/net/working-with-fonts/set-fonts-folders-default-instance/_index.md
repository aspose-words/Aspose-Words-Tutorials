---
title: Állítsa be a Fonts Folders alapértelmezett példányát
linktitle: Állítsa be a Fonts Folders alapértelmezett példányát
second_title: Aspose.Words Document Processing API
description: Ebből a lépésenkénti oktatóanyagból megtudhatja, hogyan állíthat be betűtípusmappákat az Aspose.Words for .NET alapértelmezett példányához. Könnyedén testreszabhatja Word-dokumentumait.
weight: 10
url: /hu/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a Fonts Folders alapértelmezett példányát

## Bevezetés

Szia kódolótárs! Ha Word-dokumentumokkal dolgozik .NET-ben, valószínűleg tisztában van a megfelelő betűtípusok fontosságával. Ma azt vizsgáljuk meg, hogyan állíthatunk be betűtípusmappákat az alapértelmezett példányhoz az Aspose.Words for .NET használatával. Képzelje el, hogy az összes egyéni betűtípus a keze ügyében van, így dokumentumai pontosan úgy néznek ki, ahogyan Ön elképzeli. Jól hangzik, igaz? Kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk a finom részletekbe, győződjünk meg arról, hogy mindennel rendelkezünk, amire szükségünk van:
-  Aspose.Words for .NET: Győződjön meg arról, hogy a könyvtár telepítve van. Ha nem, akkor megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Visual Studio vagy bármely más .NET-kompatibilis IDE.
- C# alapismeretek: Kényelmesnek kell lennie a C# programozásban.
- Fonts mappa: Az egyéni betűtípusokat tartalmazó könyvtár.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez segít elérni a fonts mappa beállításához szükséges osztályokat és metódusokat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bontsuk le a folyamatot egyszerű, emészthető lépésekre.

## 1. lépés: Határozza meg az adatkönyvtárat

Minden nagyszerű utazás egyetlen lépéssel kezdődik, a miénk pedig a dokumentum tárolási könyvtárának meghatározásával kezdődik. Az Aspose.Words itt keresi a Word-dokumentumot.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Tessék, cserélje ki`"YOUR DOCUMENT DIRECTORY"` a dokumentumkönyvtár tényleges elérési útjával. Ez az a hely, ahol a forrásdokumentum található, és ahol a kimenet mentésre kerül.

## 2. lépés: Állítsa be a Fonts mappát

 Most pedig mondjuk meg az Aspose.Words-nek, hogy hol találhatja meg egyéni betűtípusait. Ezt úgy teheti meg, hogy beállítja a fonts mappát a`FontSettings.DefaultInstance.SetFontsFolder` módszer.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 Ebben a sorban`"C:\\MyFonts\\"` az egyéni betűtípusok mappájának elérési útja. A második paraméter,`true`, azt jelzi, hogy a mappában lévő betűtípusokat rekurzívan kell vizsgálni.

## 3. lépés: Töltse be a dokumentumot

 Ha beállította a fonts mappát, a következő lépés a Word-dokumentum betöltése az Aspose.Wordsba. Ez a`Document` osztály.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Itt,`dataDir + "Rendering.docx"` a Word dokumentum teljes elérési útjára utal. Győződjön meg arról, hogy a dokumentum a megadott könyvtárban van.

## 4. lépés: Mentse el a dokumentumot

Az utolsó lépés a dokumentum mentése a betűtípusok mappa beállítása után. Ez biztosítja, hogy az egyéni betűtípusok megfelelően kerüljenek alkalmazásra a kimenetben.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Ez a sor PDF-ként menti a dokumentumot az alkalmazott egyéni betűtípusokkal. A kimeneti fájl ugyanabban a könyvtárban található, mint a forrásdokumentum.

## Következtetés

És megvan! A betűtípusmappák beállítása az Aspose.Words for .NET alapértelmezett példányához gyerekjáték, ha egyszerű lépésekre bontja. Az útmutató követésével biztosíthatja, hogy Word-dokumentumai pontosan úgy nézzenek ki, ahogy szeretné, az összes egyéni betűtípussal. Tehát hajrá, próbálja ki, és tegye fényessé dokumentumait!

## GYIK

### Beállíthatok több betűtípus mappát?
 Igen, több betűtípusmappát is beállíthat a segítségével`SetFontsFolders` metódus, amely mappaútvonalak tömbjét fogadja el.

### Milyen fájlformátumokat támogat az Aspose.Words a dokumentumok mentéséhez?
Az Aspose.Words különféle formátumokat támogat, beleértve a DOCX, PDF, HTML, EPUB és egyebeket.

### Lehetséges online betűtípusok használata az Aspose.Words-ben?
Nem, az Aspose.Words jelenleg csak a helyi fontfájlokat támogatja.

### Hogyan biztosíthatom, hogy egyéni betűtípusaim be legyenek ágyazva a mentett PDF-be?
 Beállításával a`FontSettings` helyesen és biztosítva a betűtípusok elérhetőségét, az Aspose.Words beágyazza azokat a PDF kimenetbe.

### Mi történik, ha egy betűtípus nem található a megadott mappában?
Az Aspose.Words tartalék betűtípust használ, ha a megadott betűtípus nem található.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
