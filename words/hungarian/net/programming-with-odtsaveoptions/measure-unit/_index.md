---
"description": "Ismerje meg, hogyan konfigurálhatja a mértékegység funkciót az Aspose.Words for .NET programban a dokumentum formázásának megőrzése érdekében az ODT konvertálás során."
"linktitle": "Mértékegység"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Mértékegység"
"url": "/hu/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mértékegység

## Bevezetés

Előfordult már, hogy Word-dokumentumokat kellett különböző formátumokba konvertálnod, de egy adott mértékegységre volt szükséged az elrendezéshez? Akár hüvelykekkel, centiméterekkel vagy pontokkal dolgozol, kulcsfontosságú, hogy a dokumentum megőrizze integritását a konvertálási folyamat során. Ebben az oktatóanyagban bemutatjuk, hogyan konfigurálhatod a mértékegység funkciót az Aspose.Words for .NET-ben. Ez a hatékony funkció biztosítja, hogy a dokumentum formázása pontosan úgy maradjon meg, ahogyan szükséged van rá, amikor ODT (Open Document Text) formátumba konvertálod.

## Előfeltételek

Mielőtt belemerülnél a kódba, van néhány dolog, amire szükséged lesz az induláshoz:

1. Aspose.Words for .NET: Győződjön meg róla, hogy telepítve van az Aspose.Words for .NET legújabb verziója. Ha még nem telepítette, letöltheti innen: [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Egy Visual Studio-hoz hasonló IDE, amely C# kódot ír és futtat.
3. C# alapismeretek: A C# alapjainak ismerete segít majd a tutoriál követésében.
4. Word-dokumentum: Készítsen elő egy minta Word-dokumentumot, amelyet felhasználhat az átalakításhoz.

## Névterek importálása

Mielőtt elkezdenénk a kódolást, ellenőrizzük, hogy importáltuk-e a szükséges névtereket. Ezeket a kódfájl elejére direktívák segítségével adhatjuk hozzá:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Először is meg kell adnia a dokumentumkönyvtár elérési útját. Itt található a Word-dokumentum, és ide lesz mentve a konvertált fájl.

```csharp
// A dokumentumok könyvtárának elérési útja
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Csere `"YOUR DOCUMENTS DIRECTORY"` a könyvtár tényleges elérési útjával. Ez biztosítja, hogy a kód tudja, hol találja a Word-dokumentumot.

## 2. lépés: Töltse be a Word dokumentumot

Ezután be kell töltenie a konvertálni kívánt Word-dokumentumot. Ezt a következővel teheti meg: `Document` osztály az Aspose.Words-ből.

```csharp
// Töltsd be a Word dokumentumot
Document doc = new Document(dataDir + "Document.docx");
```

Győződjön meg arról, hogy a „Document.docx” nevű Word-dokumentum megtalálható a megadott könyvtárban.

## 3. lépés: A mértékegység konfigurálása

Most pedig konfiguráljuk az ODT konverzió mértékegységét. Itt történik a varázslat. Beállítjuk a `OdtSaveOptions` hüvelyket használni mértékegységként.

```csharp
// A biztonsági mentési beállítások konfigurálása a „Mértékegység” funkcióval
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

Ebben a példában hüvelykben adjuk meg a mértékegységet. Más mértékegységeket is választhat, például `OdtSaveMeasureUnit.Centimeters` vagy `OdtSaveMeasureUnit.Points` az igényeidtől függően.

## 4. lépés: A dokumentum konvertálása ODT formátumra

Végül a Word dokumentumot ODT formátumba konvertáljuk a konfigurált `OdtSaveOptions`.

```csharp
// Dokumentum konvertálása ODT formátumba
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Ez a kódsor az új mértékegységgel együtt menti el a konvertált dokumentumot a megadott könyvtárba.

## Következtetés

És íme! A következő lépéseket követve könnyedén konfigurálhatod az Aspose.Words for .NET mértékegység funkcióját, hogy a dokumentumod elrendezése megmaradjon a konvertálás során. Akár hüvelykkel, centiméterrel vagy pontokkal dolgozol, ez az oktatóanyag megmutatta, hogyan veheted át könnyedén az irányítást a dokumentum formázása felett.

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony függvénytár a Word-dokumentumok programozott kezeléséhez. Lehetővé teszi a fejlesztők számára Word-dokumentumok létrehozását, módosítását, konvertálását és feldolgozását Microsoft Word használata nélkül.

### Használhatok más mértékegységeket is a hüvelyken kívül?
Igen, az Aspose.Words for .NET más mértékegységeket is támogat, például centimétert és pontot. A kívánt mértékegységet a következővel adhatja meg: `OdtSaveMeasureUnit` felsorolás.

### Van ingyenes próbaverzió az Aspose.Words for .NET-hez?
Igen, letöltheti az Aspose.Words for .NET ingyenes próbaverzióját innen: [itt](https://releases.aspose.com/).

### Hol találok dokumentációt az Aspose.Words for .NET-hez?
Az Aspose.Words for .NET átfogó dokumentációját a következő címen érheti el: [ezt a linket](https://reference.aspose.com/words/net/).

### Hogyan kaphatok támogatást az Aspose.Words for .NET-hez?
Támogatásért látogassa meg az Aspose.Words fórumot a következő címen: [ezt a linket](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}