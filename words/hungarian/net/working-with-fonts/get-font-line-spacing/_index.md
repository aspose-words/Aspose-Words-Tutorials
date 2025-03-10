---
title: Szerezze be a betűtípus sorközt
linktitle: Szerezze be a betűtípus sorközt
second_title: Aspose.Words Document Processing API
description: Ebből a lépésenkénti oktatóanyagból megtudhatja, hogyan állíthatja be a betűtípusok sorközét az Aspose.Words for .NET használatával. Tökéletes fejlesztőknek.
weight: 10
url: /hu/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Szerezze be a betűtípus sorközt

## Bevezetés

Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi Word-dokumentumok programozott létrehozását, kezelését és konvertálását. Az egyik gyakori feladat, amelyet el kell végeznie, egy adott betűtípus sorközének lekérése a dokumentumban. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a folyamaton, biztosítva, hogy könnyen beállíthassa a betűtípusok sorközét az Aspose.Words for .NET használatával. 

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

1.  Aspose.Words for .NET Library: Töltse le és telepítse a legújabb verziót innen[itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Győződjön meg arról, hogy be van állítva egy olyan IDE, mint a Visual Studio.
3. Alapvető C# ismeretek: Ez az oktatóanyag feltételezi, hogy rendelkezik alapvető ismeretekkel a C# programozásról.

## Névterek importálása

Először is importálnia kell a szükséges névtereket a C# projektbe. Ezek a névterek lehetővé teszik az Aspose.Words funkciók elérését.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bontsuk le egyszerű, kezelhető lépésekre a betűtípus-sortávolság meghatározásának folyamatát.

## 1. lépés: Hozzon létre egy új dokumentumot

Az első lépés egy új Word-dokumentumpéldány létrehozása az Aspose.Words for .NET használatával.

```csharp
Document doc = new Document();
```

## 2. lépés: Inicializálja a DocumentBuilder programot

Ezután inicializálnunk kell a`DocumentBuilder` objektum. Ez az objektum segít nekünk a dokumentum tartalmának felépítésében és kezelésében.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Állítsa be a betűtípus tulajdonságait

Most beállítjuk a betűtípus tulajdonságait a beszúrni kívánt szöveghez. Ebben a példában a "Calibri" betűtípust fogjuk használni.

```csharp
builder.Font.Name = "Calibri";
```

## 4. lépés: Írjon szöveget a dokumentumba

 A`DocumentBuilder` objektumot, írjon be szöveget a dokumentumba. Ez a szöveg az előző lépésben beállított betűtípus-tulajdonságokat fogja használni.

```csharp
builder.Writeln("Sample Text");
```

## 5. lépés: A betűtípus objektum lekérése

A sorköz eléréséhez el kell érnünk az imént hozzáadott szöveg font objektumát. Ezt úgy teheti meg, hogy a dokumentum szerkezetében navigál az első bekezdés futtatásához.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## 6. lépés: Állítsa be a sorközt

Végül a font objektumból lekérjük a sortávolságot, és kinyomtatjuk a konzolra.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Következtetés

És megvan! A betűtípus sorközének lekérése az Aspose.Words for .NET használatával egyszerű, ha ezeket az egyszerű lépéseket lebontja. Akár új dokumentumot hoz létre, akár egy meglévővel dolgozik, az Aspose.Words minden eszközt biztosít a betűtípus-tulajdonságok hatékony kezeléséhez.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott C# használatával történő létrehozását, kezelését és konvertálását.

### Használhatom az Aspose.Words for .NET programot más .NET nyelveken?
Igen, az Aspose.Words for .NET bármely .NET nyelvvel használható, beleértve a VB.NET-et és az F#-ot is.

### Hogyan tölthetem le az Aspose.Words for .NET fájlt?
 Letöltheti az Aspose.Words for .NET legújabb verzióját innen[itt](https://releases.aspose.com/words/net/).

### Létezik ingyenes próbaverzió az Aspose.Words for .NET számára?
 Igen, ingyenes próbaverziót kaphat a webhelyen[itt](https://releases.aspose.com/).

### Hol találom az Aspose.Words for .NET dokumentációját?
 Az Aspose.Words for .NET dokumentációja elérhető[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
