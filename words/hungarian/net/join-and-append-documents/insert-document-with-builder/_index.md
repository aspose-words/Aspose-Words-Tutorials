---
title: Dokumentum beszúrása a Builder segítségével
linktitle: Dokumentum beszúrása a Builder segítségével
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan egyesíthet két Word-dokumentumot az Aspose.Words for .NET használatával. Útmutató lépésről lépésre a dokumentum beszúrásához a DocumentBuilder segítségével és a formázás megőrzéséhez.
weight: 10
url: /hu/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentum beszúrása a Builder segítségével

## Bevezetés

Tehát van két Word-dokumentuma, és egybe szeretné egyesíteni őket. Lehet, hogy azt gondolja: "Van ennek egyszerű módja programozottan?" Teljesen! Ma az Aspose.Words for .NET könyvtár használatával egy dokumentum beszúrásának folyamatán fogok végigvezetni. Ez a módszer rendkívül praktikus, különösen akkor, ha nagy dokumentumokkal foglalkozik, vagy automatizálni kell a folyamatot. Egyből merüljünk bele!

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy mindennel rendelkezik, amire szüksége van:

1.  Aspose.Words for .NET: Ha még nem tette meg, letöltheti a webhelyről[itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Győződjön meg arról, hogy telepítve van a Visual Studio vagy bármely más megfelelő IDE.
3. Alapvető C# ismerete: Egy kis C# ismerete sokat segíthet.

## Névterek importálása

Először is importálnia kell a szükséges névtereket az Aspose.Words könyvtár funkcióinak eléréséhez. A következőképpen teheti meg:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Most, hogy megvannak az előfeltételeink, bontsuk le a folyamatot lépésről lépésre.

## 1. lépés: A dokumentumkönyvtár beállítása

kódolás megkezdése előtt be kell állítania a dokumentumkönyvtár elérési útját. Ez az a hely, ahol a forrás- és céldokumentumok tárolódnak.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési úttal, ahol a dokumentumok találhatók. Ez segít a programnak könnyen megtalálni a fájlokat.

## 2. lépés: A forrás- és céldokumentumok betöltése

Ezután be kell töltenünk azokat a dokumentumokat, amelyekkel dolgozni szeretnénk. Ebben a példában van egy forrásdokumentum és egy céldokumentum.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

 Itt a`Document` osztályt az Aspose.Words könyvtárból dokumentumaink betöltéséhez. Győződjön meg arról, hogy a fájlnevek megegyeznek a könyvtárában lévőkkel.

## 3. lépés: DocumentBuilder objektum létrehozása

 A`DocumentBuilder` osztály egy hatékony eszköz az Aspose.Words könyvtárban. Segítségével navigálhatunk és kezelhetjük a dokumentumot.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

 Ebben a lépésben létrehoztunk egy`DocumentBuilder` objektum céldokumentumunkhoz. Ez segít nekünk tartalmat beilleszteni a dokumentumba.

## 4. lépés: Ugrás a dokumentum végére

A forrásdokumentum beszúrása előtt az építő kurzort a céldokumentum végére kell mozgatnunk.

```csharp
builder.MoveToDocumentEnd();
```

Ez biztosítja, hogy a forrásdokumentum a céldokumentum végére kerüljön beszúrásra.

## 5. lépés: Oldaltörés beszúrása

A dolgok rendezettsége érdekében a forrásdokumentum beszúrása előtt adjunk meg egy oldaltörést. Ezzel egy új oldalon kezdődik a forrásdokumentum tartalma.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Az oldaltörés biztosítja, hogy a forrásdokumentum tartalma egy új oldalon kezdődik, így az egyesített dokumentum professzionális megjelenésű.

## 6. lépés: A forrásdokumentum beszúrása

Most jön az izgalmas rész – tulajdonképpen a forrásdokumentum beillesztése a céldokumentumba.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

 A`InsertDocument` módszerrel a teljes forrásdokumentumot beilleszthetjük a céldokumentumba. A`ImportFormatMode.KeepSourceFormatting` biztosítja a forrásdokumentum formázásának megőrzését.

## 7. lépés: Az egyesített dokumentum mentése

Végül mentsük el az egyesített dokumentumot. Ez egy fájlba fogja egyesíteni a forrás- és céldokumentumot.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

A dokumentum elmentésével befejezzük a két dokumentum egyesítésének folyamatát. Az új dokumentum készen áll, és a megadott könyvtárba mentve.

## Következtetés

És megvan! Sikeresen beszúrt egy dokumentumot a másikba az Aspose.Words for .NET használatával. Ez a módszer nemcsak hatékony, hanem megőrzi mindkét dokumentum formázását, biztosítva a zökkenőmentes egyesítést. Akár egyszeri projekten dolgozik, akár automatizálnia kell a dokumentumfeldolgozást, az Aspose.Words for .NET megoldást nyújt Önnek.

## GYIK

### Mi az Aspose.Words for .NET?  
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, szerkesztését, konvertálását és kezelését.

### Megtarthatom a forrásdokumentum formázását?  
 Igen, használatával`ImportFormatMode.KeepSourceFormatting`, a forrásdokumentum formázása megmarad, amikor beillesztik a céldokumentumba.

### Szükségem van licencre az Aspose.Words for .NET használatához?  
 Igen, az Aspose.Words for .NET szolgáltatáshoz licenc szükséges a teljes funkcionalitáshoz. Kaphatsz a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) értékeléshez.

### Automatizálhatom ezt a folyamatot?  
Teljesen! A leírt módszer beépíthető nagyobb alkalmazásokba a dokumentumfeldolgozási feladatok automatizálása érdekében.

### Hol találhatok további forrásokat és támogatást?  
 További információkért ellenőrizze a[dokumentáció](https://reference.aspose.com/words/net/) , vagy látogassa meg a[támogatási fórum](https://forum.aspose.com/c/words/8) segítségért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
