---
title: Áthúzott
linktitle: Áthúzott
second_title: Aspose.Words Document Processing API
description: lépésenkénti útmutatónkból megtudhatja, hogyan alkalmazhat áthúzott formázást a szövegben az Aspose.Words for .NET használatával. Növelje dokumentumfeldolgozási készségeit.
weight: 10
url: /hu/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Áthúzott

## Bevezetés

Üdvözöljük ebben a részletes útmutatóban arról, hogyan alkalmazhat áthúzott formázást a szövegben az Aspose.Words for .NET használatával. Ha fejleszteni szeretné dokumentumfeldolgozási készségeit, és egyedi hatást szeretne adni szövegének, akkor jó helyen jár. Merüljünk el!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:

-  Aspose.Words for .NET: Töltse le[itt](https://releases.aspose.com/words/net/).
- .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a rendszeren.
- Fejlesztői környezet: Egy IDE, mint a Visual Studio.
- Alapszintű C# ismerete: C# programozás ismerete szükséges.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket. Ezek elengedhetetlenek az Aspose.Words könyvtár és szolgáltatásainak eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Inicializálja a DocumentBuildert

 A`DocumentBuilder` osztály az Aspose.Words hatékony eszköze, amely lehetővé teszi, hogy könnyedén hozzáadjon tartalmat a dokumentumhoz.

```csharp
// Inicializáljon egy DocumentBuilder programot.
DocumentBuilder builder = new DocumentBuilder();
```

## 2. lépés: Állítsa be az áthúzott tulajdonságot

Most alkalmazzuk az áthúzott tulajdonságot a szövegünkre. Ez magában foglalja a`StrikeThrough` tulajdona a`Font` tiltakozik`true`.

```csharp
// Tegye áthúzva a szöveget.
builder.Font.StrikeThrough = true;
```

## 3. lépés: Írjon szöveget áthúzással

 Az áthúzott tulajdonságkészlettel most hozzáadhatjuk a szövegünket. A`Writeln` metódus hozzáadja a szöveget a dokumentumhoz.

```csharp
// Írjon szöveget áthúzással.
builder.Writeln("This text will be StrikeThrough");
```

## Következtetés

És megvan! Sikeresen hozzáadta az áthúzott formázást a szövegéhez az Aspose.Words for .NET segítségével. Ez a nagy teljesítményű könyvtár a lehetőségek világát nyitja meg a dokumentumfeldolgozás és a testreszabás terén. Függetlenül attól, hogy jelentéseket, leveleket vagy bármilyen más típusú dokumentumot készít, ezeknek a funkcióknak az elsajátítása kétségtelenül javítja a termelékenységet és a kimenetek minőségét.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony dokumentumfeldolgozó könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, kezelését és konvertálását.

### Használhatom az Aspose.Words for .NET-et kereskedelmi projektekben?
 Igen, az Aspose.Words for .NET használható kereskedelmi projektekben. A vásárlási lehetőségekért keresse fel a[oldal vásárlása](https://purchase.aspose.com/buy).

### Létezik ingyenes próbaverzió az Aspose.Words for .NET számára?
 Igen, letölthet egy ingyenes próbaverziót[itt](https://releases.aspose.com/).

### Hogyan kaphatok támogatást az Aspose.Words for .NET-hez?
Támogatást kaphat az Aspose közösségtől és a szakértőktől[támogatási fórum](https://forum.aspose.com/c/words/8).

### Alkalmazhatok más szövegformázási beállításokat az Aspose.Words for .NET használatával?
Teljesen! Az Aspose.Words for .NET a szövegformázási lehetőségek széles skáláját támogatja, beleértve a félkövér, dőlt, aláhúzott és egyebeket.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
