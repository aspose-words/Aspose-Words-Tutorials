---
"description": "Tanulja meg, hogyan adhat hozzá kétirányú (Bidi) jeleket Word-dokumentumokban az Aspose.Words for .NET használatával ebből az útmutatóból. Biztosítsa a megfelelő szövegirányt többnyelvű tartalom esetén."
"linktitle": "Kétirányú jelek hozzáadása Word-dokumentumban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Kétirányú jelek hozzáadása Word-dokumentumban"
"url": "/hu/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kétirányú jelek hozzáadása Word-dokumentumban

## Bevezetés

dokumentumfeldolgozás világában a kétirányú (Bidi) szövegek kezelése gyakran kissé bonyolult lehet. Ez különösen igaz olyan nyelvek esetén, amelyek eltérő szövegirányokkal rendelkeznek, például arab vagy héber. Szerencsére az Aspose.Words for .NET megkönnyíti az ilyen forgatókönyvek kezelését. Ebben az oktatóanyagban bemutatjuk, hogyan adhatunk hozzá kétirányú jeleket egy Word-dokumentumhoz az Aspose.Words for .NET segítségével.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg róla, hogy a következőkkel rendelkezünk:

1. Aspose.Words for .NET: Telepítenie kell az Aspose.Words for .NET programot. Letöltheti innen: [Aspose letöltési oldal](https://releases.aspose.com/words/net/).
2. .NET-keretrendszer vagy .NET Core: Győződjön meg arról, hogy kompatibilis .NET-környezettel rendelkezik a példák futtatásához.
3. C# alapismeretek: Ismeri a C# programozási nyelvet és a .NET alapvető műveleteit.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket. Így illesztheti be őket a projektjébe:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bontsuk le lépésekre a kétirányú jelek Word-dokumentumban való hozzáadásának folyamatát. Minden lépés végigvezet a kódon és annak célján.

## 1. lépés: A dokumentum beállítása

Kezdje egy új példány létrehozásával a `Document` osztály és egy `DocumentBuilder` tartalom hozzáadásához a dokumentumhoz.

```csharp
// A dokumentumok könyvtárának elérési útja
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Dokumentum létrehozása és tartalom hozzáadása
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ebben a lépésben inicializál egy új Word-dokumentumot, és beállít egy `DocumentBuilder` a tartalom beillesztésének megkönnyítése érdekében.

## 2. lépés: Tartalom hozzáadása a dokumentumhoz

Ezután adjon hozzá szöveget a dokumentumhoz. Itt különböző nyelveken hozzáadunk szöveget a kétirányú szöveg kezelésének szemléltetésére.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Itt először egy szabványos angol kifejezést adunk hozzá. Ezután engedélyezzük a kétirányú szövegformázást a következő szöveghez, amely héberül és arabul íródik. Ez bemutatja, hogyan lehet kétirányú szöveget beilleszteni.

## 3. lépés: Kétirányú jelek mentési beállításainak konfigurálása

Annak érdekében, hogy a kétirányú jelek helyesen kerüljenek mentésre a dokumentumban, konfigurálnia kell a `TxtSaveOptions` és engedélyezze a `AddBidiMarks` opció.

```csharp
// Kétirányú jelek hozzáadása
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

Ebben a lépésben létrehozunk egy példányt a következőből: `TxtSaveOptions` és állítsa be a `AddBidiMarks` ingatlan `true`Ez biztosítja, hogy a kétirányú jelek szerepeljenek a dokumentum szövegfájlként történő mentésekor.

## Következtetés

A kétnyelvűség-jelek hozzáadása a Word-dokumentumokhoz kulcsfontosságú lépés lehet, ha többnyelvű, eltérő szövegirányú nyelveket tartalmazó tartalmakkal foglalkozik. Az Aspose.Words for .NET segítségével ez a folyamat egyszerű és hatékony. A fent vázolt lépéseket követve biztosíthatja, hogy dokumentumai helyesen jelenítsék meg a kétnyelvű szöveget, javítva az olvashatóságot és a pontosságot.

## GYIK

### Mik azok a bidi jelek és miért fontosak?
A kétirányú jelek speciális karakterek, amelyek a szöveg irányát szabályozzák a dokumentumokban. Elengedhetetlenek a jobbról balra olvasó nyelvek, például az arab és a héber megfelelő megjelenítéséhez.

### Használhatom az Aspose.Words for .NET-et más típusú szövegirány-problémák kezelésére?
Igen, az Aspose.Words for .NET átfogó támogatást nyújt a különféle szövegirány- és formázási igényekhez, beleértve a jobbról balra és a balról jobbra író nyelveket is.

### Lehetséges a kétirányú formázást csak a dokumentum bizonyos részeire alkalmazni?
Igen, szükség szerint alkalmazhat kétirányú formázást a dokumentum egyes bekezdéseire vagy szakaszaira.

### Milyen formátumokban menthetem el a dokumentumot kétirányú jelölések használatával?
A bemutatott példában a dokumentum szövegfájlként kerül mentésre. Az Aspose.Words azonban támogatja a dokumentumok különböző formátumokban történő mentését a kétirányú jelek megőrzése mellett.

### Hol találok további információt az Aspose.Words for .NET-ről?
Az Aspose.Words for .NET-ről bővebben a következő helyen olvashat: [Aspose dokumentáció](https://reference.aspose.com/words/net/) és hozzáférhet a [Támogatási fórum](https://forum.aspose.com/c/words/8) további segítségért.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}