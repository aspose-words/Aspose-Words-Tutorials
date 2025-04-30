---
"description": "Tanuld meg, hogyan egyesíthetsz két Word-dokumentumot az Aspose.Words for .NET segítségével. Lépésről lépésre útmutató egy dokumentum DocumentBuilderrel történő beszúrásához és a formázás megőrzéséhez."
"linktitle": "Dokumentum beszúrása a Szerkesztővel"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Dokumentum beszúrása a Szerkesztővel"
"url": "/hu/net/join-and-append-documents/insert-document-with-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentum beszúrása a Szerkesztővel

## Bevezetés

Szóval, van két Word-dokumentumod, és szeretnéd őket egybe egyesíteni. Lehet, hogy azon gondolkodsz: "Van erre valami egyszerű módja programozottan?" Természetesen! Ma végigvezetlek azon, hogyan illeszthetsz be egy dokumentumot egy másikba az Aspose.Words for .NET könyvtár segítségével. Ez a módszer rendkívül hasznos, különösen akkor, ha nagy dokumentumokkal dolgozol, vagy automatizálni kell a folyamatot. Vágjunk bele!

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy minden megvan, amire szükséged van:

1. Aspose.Words .NET-hez: Ha még nem tette meg, letöltheti innen: [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Győződjön meg róla, hogy telepítve van a Visual Studio vagy bármilyen más megfelelő IDE.
3. C# alapismeretek: Egy kis C# ismeret sokat segíthet.

## Névterek importálása

Először is importálnod kell a szükséges névtereket az Aspose.Words könyvtár funkcióinak eléréséhez. Így teheted meg:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Most, hogy megvannak az előfeltételeink, bontsuk le a folyamatot lépésről lépésre.

## 1. lépés: A dokumentumkönyvtár beállítása

Mielőtt elkezdenénk a kódolást, be kell állítanod a dokumentumkönyvtár elérési útját. Itt tárolódnak a forrás- és céldokumentumok.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Csere `"YOUR DOCUMENT DIRECTORY"` a dokumentumok tényleges elérési útjával. Ez segít a programnak a fájlok könnyebb megtalálásában.

## 2. lépés: A forrás- és céldokumentumok betöltése

Ezután be kell töltenünk a dokumentumokat, amelyekkel dolgozni szeretnénk. Ebben a példában van egy forrásdokumentumunk és egy céldokumentumunk.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Itt a következőt használjuk: `Document` osztályt az Aspose.Words könyvtárból a dokumentumok betöltéséhez. Győződjön meg róla, hogy a fájlnevek megegyeznek a könyvtárban találhatókkal.

## 3. lépés: DocumentBuilder objektum létrehozása

A `DocumentBuilder` Az osztály egy hatékony eszköz az Aspose.Words könyvtárban. Lehetővé teszi számunkra a dokumentumban való navigálást és annak kezelését.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

Ebben a lépésben létrehoztunk egy `DocumentBuilder` objektum a céldokumentumunkhoz. Ez segít nekünk tartalom beszúrásában a dokumentumba.

## 4. lépés: Ugrás a dokumentum végére

A forrásdokumentum beillesztése előtt a céldokumentum végére kell mozgatnunk a szerkesztő kurzorát.

```csharp
builder.MoveToDocumentEnd();
```

Ez biztosítja, hogy a forrásdokumentum a céldokumentum végére kerüljön beszúrásra.

## 5. lépés: Oldaltörés beszúrása

A rend kedvéért adjunk hozzá egy oldaltörést a forrásdokumentum beillesztése előtt. Ez a forrásdokumentum tartalmát egy új oldalon kezdi.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Az oldaltörés biztosítja, hogy a forrásdokumentum tartalma új oldalon kezdődjön, így az egyesített dokumentum professzionális megjelenésű lesz.

## 6. lépés: A forrásdokumentum beszúrása

Most jön az izgalmas rész – a forrásdokumentum beillesztése a céldokumentumba.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

A `InsertDocument` metódussal beilleszthetjük a teljes forrásdokumentumot a céldokumentumba. `ImportFormatMode.KeepSourceFormatting` biztosítja a forrásdokumentum formázásának megőrzését.

## 7. lépés: Az egyesített dokumentum mentése

Végül mentsük el az egyesített dokumentumot. Ez a forrás- és céldokumentumokat egyetlen fájlba egyesíti.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

A dokumentum mentésével befejeztük a két dokumentum egyesítésének folyamatát. Az új dokumentum elkészült, és mentésre került a megadott könyvtárba.

## Következtetés

És íme! Sikeresen beszúrtál egy dokumentumot egy másikba az Aspose.Words for .NET segítségével. Ez a módszer nemcsak hatékony, de megőrzi mindkét dokumentum formázását is, biztosítva a zökkenőmentes egyesítést. Akár egyszeri projekten dolgozol, akár automatizálnod kell a dokumentumok feldolgozását, az Aspose.Words for .NET segít neked.

## GYIK

### Mi az Aspose.Words .NET-hez?  
Az Aspose.Words for .NET egy hatékony függvénytár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, szerkesszenek, konvertáljanak és manipuláljanak Word dokumentumokat.

### Megtarthatom a forrásdokumentum formázását?  
Igen, a használatával `ImportFormatMode.KeepSourceFormatting`a forrásdokumentum formázása megőrződik, amikor beszúrja a céldokumentumba.

### Szükségem van licencre az Aspose.Words for .NET használatához?  
Igen, az Aspose.Words for .NET teljes funkcionalitásához licenc szükséges. Szerezhet egyet [ideiglenes engedély](https://purchase.aspose.com/temporary-license/) értékeléshez.

### Automatizálhatom ezt a folyamatot?  
Abszolút! A leírt módszer beépíthető nagyobb alkalmazásokba a dokumentumfeldolgozási feladatok automatizálása érdekében.

### Hol találok további forrásokat és támogatást?  
További információkért tekintse meg a [dokumentáció](https://reference.aspose.com/words/net/), vagy látogassa meg a [támogatási fórum](https://forum.aspose.com/c/words/8) segítségért.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}