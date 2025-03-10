---
title: Mértékegység
linktitle: Mértékegység
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan konfigurálhatja a mértékegység funkciót az Aspose.Words for .NET-ben, hogy megőrizze a dokumentum formázását az ODT-konverzió során.
weight: 10
url: /hu/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mértékegység

## Bevezetés

Előfordult már, hogy Word-dokumentumait különböző formátumokba kellett konvertálnia, de szüksége volt egy meghatározott mértékegységre az elrendezéshez? Legyen szó hüvelykekről, centiméterekről vagy pontokról, kulcsfontosságú annak biztosítása, hogy a dokumentum megőrizze sértetlenségét az átalakítási folyamat során. Ebben az oktatóanyagban bemutatjuk, hogyan konfigurálhatja a mértékegység funkciót az Aspose.Words for .NET-ben. Ez a hatékony funkció biztosítja, hogy a dokumentum formázása pontosan úgy maradjon meg, ahogyan szüksége van rá, amikor ODT (Open Document Text) formátumba konvertálja.

## Előfeltételek

Mielőtt belemerülne a kódba, néhány dolgot meg kell tennie az induláshoz:

1. Aspose.Words for .NET: Győződjön meg arról, hogy az Aspose.Words for .NET legújabb verziója telepítve van. Ha még nincs meg, letöltheti innen[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Olyan IDE, mint a Visual Studio a C# kód írásához és végrehajtásához.
3. Alapvető C# ismerete: A C# alapjainak megértése segít az oktatóanyag követésében.
4. Word-dokumentum: Készítsen Word-mintadokumentumot, amelyet felhasználhat a konvertáláshoz.

## Névterek importálása

Mielőtt elkezdené a kódolást, győződjön meg arról, hogy a szükséges névtereket importálta. Adja hozzá ezeket a kódfájl tetején található direktívák használatával:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Először is meg kell határoznia a dokumentumkönyvtár elérési útját. Ez az a hely, ahol a Word-dokumentum található, és ahol a konvertált fájl mentésre kerül.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENTS DIRECTORY"` a címtár tényleges elérési útjával. Ez biztosítja, hogy a kód tudja, hol találja a Word-dokumentumot.

## 2. lépés: Töltse be a Word-dokumentumot

 Ezután be kell töltenie a konvertálni kívánt Word-dokumentumot. Ez a`Document` osztály Aspose-tól.Words.

```csharp
// Töltse be a Word dokumentumot
Document doc = new Document(dataDir + "Document.docx");
```

Győződjön meg arról, hogy a „Document.docx” nevű Word-dokumentum megtalálható a megadott könyvtárban.

## 3. lépés: Konfigurálja a mértékegységet

 Most állítsuk be az ODT-konverzió mértékegységét. Itt történik a varázslat. Felállítjuk a`OdtSaveOptions` hogy a hüvelyket használjuk mértékegységként.

```csharp
// Biztonsági opciók konfigurálása a "Mértékegység" funkcióval
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 Ebben a példában a mértékegységet hüvelykre állítjuk be. Választhat más egységeket is, mint pl`OdtSaveMeasureUnit.Centimeters` vagy`OdtSaveMeasureUnit.Points` az Ön igényeitől függően.

## 4. lépés: Alakítsa át a dokumentumot ODT-vé

 Végül konvertáljuk a Word dokumentumot ODT formátumba a konfigurált formátum használatával`OdtSaveOptions`.

```csharp
// Alakítsa át a dokumentumot ODT-re
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Ez a kódsor elmenti a konvertált dokumentumot a megadott könyvtárba az új mértékegység alkalmazásával.

## Következtetés

És megvan! Az alábbi lépések követésével könnyedén konfigurálhatja az Aspose.Words for .NET mértékegység funkcióját, hogy biztosítsa a dokumentum elrendezésének megőrzését az átalakítás során. Akár hüvelykekkel, centiméterekkel vagy pontokkal dolgozik, ez az oktatóanyag megmutatja, hogyan veheti át könnyedén a dokumentum formázását.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár Word-dokumentumokkal való programozott munkavégzéshez. Lehetővé teszi a fejlesztők számára Word dokumentumok létrehozását, módosítását, konvertálását és feldolgozását Microsoft Word nélkül.

### Használhatok más mértékegységeket a hüvelyken kívül?
 Igen, az Aspose.Words for .NET támogatja az egyéb mértékegységeket, például a centimétereket és a pontokat. A kívánt mértékegységet a gombbal adhatja meg`OdtSaveMeasureUnit` felsorolás.

### Létezik ingyenes próbaverzió az Aspose.Words for .NET számára?
 Igen, letöltheti az Aspose.Words for .NET ingyenes próbaverzióját a webhelyről[itt](https://releases.aspose.com/).

### Hol találom az Aspose.Words for .NET dokumentációját?
 Az Aspose.Words for .NET átfogó dokumentációját a következő címen érheti el[ezt a linket](https://reference.aspose.com/words/net/).

### Hogyan kaphatok támogatást az Aspose.Words for .NET-hez?
 Támogatásért keresse fel az Aspose.Words fórumot a címen[ezt a linket](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
