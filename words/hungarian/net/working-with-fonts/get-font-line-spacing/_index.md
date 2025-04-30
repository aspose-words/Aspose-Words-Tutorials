---
"description": "Tanuld meg, hogyan lehet betűtípus-sorközt beállítani az Aspose.Words for .NET használatával ebben a lépésről lépésre szóló útmutatóban. Tökéletes fejlesztők számára."
"linktitle": "Betűtípus sorközének lekérése"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Betűtípus sorközének lekérése"
"url": "/hu/net/working-with-fonts/get-font-line-spacing/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus sorközének lekérése

## Bevezetés

Az Aspose.Words for .NET egy hatékony függvénykönyvtár, amely lehetővé teszi Word-dokumentumok programozott létrehozását, kezelését és konvertálását. Az egyik gyakori feladat, amelyet el kell végezni, egy adott betűtípus sorközének lekérése egy dokumentumban. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a folyamaton, biztosítva, hogy az Aspose.Words for .NET segítségével könnyen lekérhesse a betűtípus sorközét. 

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

1. Aspose.Words .NET könyvtárhoz: Töltse le és telepítse a legújabb verziót innen: [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Győződjön meg róla, hogy rendelkezik egy Visual Studio-hoz hasonló IDE-vel.
3. C# alapismeretek: Ez az oktatóanyag feltételezi, hogy rendelkezel C# programozási alapismeretekkel.

## Névterek importálása

Először importálnod kell a szükséges névtereket a C# projektedbe. Ezek a névterek lehetővé teszik az Aspose.Words funkciók elérését.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bontsuk le a betűtípus sorközének beállításának folyamatát egyszerű, kezelhető lépésekre.

## 1. lépés: Új dokumentum létrehozása

Az első lépés egy új Word-dokumentumpéldány létrehozása az Aspose.Words for .NET használatával.

```csharp
Document doc = new Document();
```

## 2. lépés: A DocumentBuilder inicializálása

Ezután inicializálnunk kell a `DocumentBuilder` objektum. Ez az objektum segít nekünk a dokumentum tartalmának felépítésében és kezelésében.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Betűtípus-tulajdonságok beállítása

Most beállítjuk a beszúrni kívánt szöveg betűtípus-tulajdonságait. Ebben a példában a "Calibri" betűtípust fogjuk használni.

```csharp
builder.Font.Name = "Calibri";
```

## 4. lépés: Szöveg írása a dokumentumba

A `DocumentBuilder` objektumhoz írj szöveget a dokumentumba. Ez a szöveg az előző lépésben beállított betűtípus-tulajdonságokat fogja használni.

```csharp
builder.Writeln("Sample Text");
```

## 5. lépés: A betűtípus objektum lekérése

A sorköz lekéréséhez hozzá kell férnünk az imént hozzáadott szöveg font objektumához. Ezt úgy tehetjük meg, hogy a dokumentum struktúrájában az első bekezdésig navigálunk.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## 6. lépés: Sorköz meghatározása

Végül a font objektumból lekérjük a sorközt, és kiírjuk a konzolra.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Következtetés

És íme! Az Aspose.Words for .NET segítségével a betűtípus sorközének lekérése pofonegyszerű, ha ezeket az egyszerű lépéseket bontjuk le. Akár új dokumentumot hoz létre, akár egy meglévővel dolgozik, az Aspose.Words minden olyan eszközt biztosít, amelyre szüksége van a betűtípus-tulajdonságok hatékony kezeléséhez.

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony függvénykönyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, kezelését és konvertálását C# használatával.

### Használhatom az Aspose.Words for .NET-et más .NET nyelvekben?
Igen, az Aspose.Words for .NET bármilyen .NET nyelvvel használható, beleértve a VB.NET-et és az F#-ot is.

### Hogyan tudom letölteni az Aspose.Words .NET-hez készült fájlt?
Az Aspose.Words for .NET legújabb verzióját letöltheti innen: [itt](https://releases.aspose.com/words/net/).

### Van ingyenes próbaverzió az Aspose.Words for .NET-hez?
Igen, ingyenes próbaverziót kaphatsz a következőtől: [itt](https://releases.aspose.com/).

### Hol találom az Aspose.Words for .NET dokumentációját?
Az Aspose.Words for .NET dokumentációja elérhető [itt](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}