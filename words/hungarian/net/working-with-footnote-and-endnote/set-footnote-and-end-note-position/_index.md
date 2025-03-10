---
title: Állítsa be a lábjegyzet és a végjegyzet pozícióját
linktitle: Állítsa be a lábjegyzet és a végjegyzet pozícióját
second_title: Aspose.Words Document Processing API
description: Ebből a részletes, lépésenkénti útmutatóból megtudhatja, hogyan állíthat be lábjegyzetek és végjegyzetek pozícióit a Word dokumentumokban az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a lábjegyzet és a végjegyzet pozícióját

## Bevezetés

Ha Word-dokumentumokkal dolgozik, és hatékonyan kell kezelnie a lábjegyzeteket és a végjegyzeteket, az Aspose.Words for .NET a legjobb könyvtár. Ez az oktatóanyag végigvezeti a lábjegyzetek és a végjegyzetek pozícióinak beállításán egy Word-dokumentumban az Aspose.Words for .NET használatával. Az egyes lépéseket lebontjuk, hogy könnyebben követhető és végrehajtható legyen.

## Előfeltételek

Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy rendelkezik az alábbiakkal:

-  Aspose.Words for .NET Library: Letöltheti innen[itt](https://releases.aspose.com/words/net/).
- Visual Studio: Bármelyik legújabb verziója jól működik.
- Alapvető C# ismerete: Az alapok megértése segít a könnyebb követésben.

## Névterek importálása

Először importálja a szükséges névtereket a C# projektbe:

```csharp
using System;
using Aspose.Words;
```

## 1. lépés: Töltse be a Word-dokumentumot

A kezdéshez be kell töltenie a Word dokumentumot az Aspose.Words Document objektumba. Ez lehetővé teszi a dokumentum tartalmának kezelését.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Ebben a kódban cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési úttal, ahol a dokumentum található.

## 2. lépés: Állítsa be a lábjegyzet pozícióját

Ezután beállíthatja a lábjegyzetek helyzetét. Az Aspose.Words for .NET lehetővé teszi a lábjegyzetek elhelyezését akár az oldal alján, akár a szöveg alatt.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 Itt a lábjegyzeteket úgy állítottuk be, hogy a szöveg alatt jelenjenek meg. Ha jobban szereti őket az oldal alján, használja`FootnotePosition.BottomOfPage`.

## 3. lépés: Állítsa be a végjegyzet pozícióját

Hasonlóképpen beállíthatja a végjegyzetek helyzetét. A végjegyzetek a szakasz vagy a dokumentum végén helyezhetők el.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 Ebben a példában a végjegyzetek az egyes szakaszok végére kerülnek. Ha a dokumentum végére szeretné helyezni őket, használja a`EndnotePosition.EndOfDocument`.

## 4. lépés: Mentse el a dokumentumot

Végül mentse el a dokumentumot a módosítások alkalmazásához. Győződjön meg róla, hogy a megfelelő fájl elérési utat és nevet adta meg a kimeneti dokumentumhoz.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Ez a sor menti a módosított dokumentumot a megadott könyvtárba.

## Következtetés

lábjegyzetek és a végjegyzetek pozíciójának beállítása a Word-dokumentumokban az Aspose.Words for .NET használatával egyszerű, ha ismeri a lépéseket. Ennek az útmutatónak a követésével személyre szabhatja dokumentumait igényeinek megfelelően, biztosítva, hogy a lábjegyzetek és végjegyzetek pontosan a kívánt helyre kerüljenek.

## GYIK

### Beállíthatok különböző pozíciókat az egyes lábjegyzetekhez vagy végjegyzetekhez?

Nem, az Aspose.Words for .NET egységesen beállítja az összes lábjegyzet és végjegyzet pozícióját a dokumentumban.

### Az Aspose.Words for .NET kompatibilis a Word dokumentumok összes verziójával?

Igen, az Aspose.Words for .NET a Word dokumentumformátumok széles skáláját támogatja, beleértve a DOC-t, a DOCX-et, az RTF-et és egyebeket.

### Használhatom az Aspose.Words for .NET-et más programozási nyelvekkel?

Az Aspose.Words for .NET .NET-alkalmazásokhoz készült, de bármilyen .NET által támogatott nyelvvel, például C#, VB.NET stb.

### Létezik ingyenes próbaverzió az Aspose.Words for .NET számára?

 Igen, ingyenes próbaverziót kaphat[itt](https://releases.aspose.com/).

### Hol találhatok részletesebb dokumentációt az Aspose.Words for .NET-hez?

 A részletes dokumentáció elérhető[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
