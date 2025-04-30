---
"description": "Tanuld meg, hogyan állíthatsz be lábjegyzeteket és végjegyzeteket Word-dokumentumokban az Aspose.Words for .NET segítségével ebből a részletes, lépésről lépésre haladó útmutatóból."
"linktitle": "Lábjegyzet és zárójegyzet pozíciójának beállítása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Lábjegyzet és végjegyzet pozíciójának beállítása"
"url": "/hu/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lábjegyzet és végjegyzet pozíciójának beállítása

## Bevezetés

Ha Word dokumentumokkal dolgozol, és hatékonyan kell kezelned a lábjegyzeteket és végjegyzeteket, az Aspose.Words for .NET a tökéletes választás. Ez az oktatóanyag végigvezet a lábjegyzetek és végjegyzetek pozícióinak beállításán egy Word dokumentumban az Aspose.Words for .NET használatával. Lépésről lépésre lebontjuk a folyamatot, hogy könnyen követhesd és megvalósíthasd.

## Előfeltételek

Mielőtt belevágnál az oktatóanyagba, győződj meg róla, hogy a következőkkel rendelkezel:

- Aspose.Words .NET könyvtárhoz: Letöltheti innen: [itt](https://releases.aspose.com/words/net/).
- Visual Studio: Bármely újabb verzió jól fog működni.
- C# alapismeretek: Az alapok ismerete segít abban, hogy könnyen követni tudd a tanultakat.

## Névterek importálása

Először importáld a szükséges névtereket a C# projektedbe:

```csharp
using System;
using Aspose.Words;
```

## 1. lépés: Töltse be a Word dokumentumot

Kezdéshez be kell töltened a Word dokumentumodat az Aspose.Words Document objektumba. Ez lehetővé teszi a dokumentum tartalmának manipulálását.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Ebben a kódban cserélje ki `"YOUR DOCUMENT DIRECTORY"` a dokumentum tényleges elérési útjával.

## 2. lépés: Lábjegyzet pozíciójának beállítása

Ezután beállíthatod a lábjegyzetek pozícióját. Az Aspose.Words for .NET lehetővé teszi a lábjegyzetek elhelyezését az oldal alján vagy a szöveg alatt.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

Itt úgy állítottuk be, hogy a lábjegyzetek a szöveg alatt jelenjenek meg. Ha jobban szeretnéd, hogy az oldal alján jelenjenek meg, használd a következőt: `FootnotePosition.BottomOfPage`.

## 3. lépés: Végjegyzet pozíciójának beállítása

Hasonlóképpen beállíthatja a végjegyzetek pozícióját is. A végjegyzetek elhelyezhetők a szakasz vagy a dokumentum végén.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

Ebben a példában a végjegyzetek minden szakasz végére kerülnek. A dokumentum végére helyezéséhez használja a következőt: `EndnotePosition.EndOfDocument`.

## 4. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a módosítások alkalmazásához. Győződjön meg arról, hogy a kimeneti dokumentumhoz a helyes fájlelérési utat és nevet adta meg.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Ez a sor elmenti a módosított dokumentumot a megadott könyvtárba.

## Következtetés

A lábjegyzetek és végjegyzetek pozícióinak beállítása Word-dokumentumokban az Aspose.Words for .NET segítségével egyszerű, ha már ismeri a lépéseket. Ezt az útmutatót követve testreszabhatja dokumentumait az igényeinek megfelelően, biztosítva, hogy a lábjegyzetek és végjegyzetek pontosan a kívánt helyen legyenek.

## GYIK

### Beállíthatok különböző pozíciókat az egyes lábjegyzetekhez vagy végjegyzetekhez?

Nem, az Aspose.Words for .NET egységesen állítja be az összes lábjegyzet és végjegyzet pozícióját a dokumentumban.

### Az Aspose.Words for .NET kompatibilis a Word dokumentumok összes verziójával?

Igen, az Aspose.Words for .NET számos Word dokumentumformátumot támogat, beleértve a DOC, DOCX, RTF és egyebeket.

### Használhatom az Aspose.Words for .NET-et más programozási nyelvekkel?

Az Aspose.Words for .NET-et .NET alkalmazásokhoz tervezték, de bármilyen .NET által támogatott nyelven használható, például C#-val, VB.NET-tel stb.

### Van ingyenes próbaverzió az Aspose.Words for .NET-hez?

Igen, kérhetsz ingyenes próbaverziót [itt](https://releases.aspose.com/).

### Hol találok részletesebb dokumentációt az Aspose.Words for .NET-hez?

Részletes dokumentáció elérhető [itt](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}