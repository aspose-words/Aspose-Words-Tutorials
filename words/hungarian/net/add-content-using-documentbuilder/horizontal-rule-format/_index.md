---
title: Vízszintes szabályformátum Word dokumentumban
linktitle: Vízszintes szabályformátum Word dokumentumban
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan illeszthet be testreszabható vízszintes szabályokat Word dokumentumokba az Aspose.Words for .NET használatával. Javítsa dokumentumautomatizálását.
weight: 10
url: /hu/net/add-content-using-documentbuilder/horizontal-rule-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vízszintes szabályformátum Word dokumentumban

## Bevezetés

A .NET-fejlesztés területén a Word-dokumentumok programozott kezelése és formázása ijesztő feladat lehet. Szerencsére az Aspose.Words for .NET robusztus megoldást kínál, amely lehetővé teszi a fejlesztők számára a dokumentumok létrehozásának, szerkesztésének és kezelésének egyszerű automatizálását. Ez a cikk az egyik alapvető funkcióval foglalkozik: a vízszintes szabályok beszúrásával a Word dokumentumokba. Akár tapasztalt fejlesztő, akár csak most kezdi az Aspose.Words-t, ennek a képességnek az elsajátítása javítja a dokumentumgenerálási folyamatot.

## Előfeltételek

Mielőtt belevágna a horizontális szabályok megvalósításába az Aspose.Words for .NET használatával, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:

- Visual Studio: Telepítse a Visual Studio IDE-t a .NET-fejlesztéshez.
- Aspose.Words for .NET: Töltse le és telepítse az Aspose.Words for .NET programot innen:[itt](https://releases.aspose.com/words/net/).
- C# alapismeretek: C# programozási nyelv alapjainak ismerete.
-  DocumentBuilder osztály: A`DocumentBuilder` osztály az Aspose-ban. Words for document manipulation.

## Névterek importálása

A kezdéshez importálja a szükséges névtereket a C# projektbe:

```csharp
using Aspose.Words;
using System.Drawing;
```

Ezek a névterek hozzáférést biztosítanak az Aspose.Words osztályokhoz a dokumentumok kezeléséhez és a szabványos .NET osztályokhoz a színek kezeléséhez.

Bontsuk le átfogó lépésekre a vízszintes szabály Word-dokumentumhoz való hozzáadásának folyamatát az Aspose.Words for .NET használatával:

## 1. lépés: Inicializálja a DocumentBuilder programot és állítsa be a könyvtárat

 Először inicializálja a`DocumentBuilder` objektumot, és állítsa be a könyvtár elérési útját, ahová a dokumentum mentésre kerül.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## 2. lépés: Szúrjon be vízszintes szabályt

 Használja a`InsertHorizontalRule()` módszere a`DocumentBuilder` osztályt vízszintes szabály hozzáadásához.

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## 3. lépés: A vízszintes szabályformátum testreszabása

 Hozzáférés a`HorizontalRuleFormat` a beillesztett alakzat tulajdonsága a vízszintes szabály megjelenésének testreszabásához.

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- Igazítás: Megadja a vízszintes szabály igazítását (`HorizontalRuleAlignment.Center` ebben a példában).
- WidthPercent: A vízszintes szabály szélességét az oldal szélességének százalékában állítja be (ebben a példában 70%).
- Magasság: Meghatározza a vízszintes szabály magasságát pontokban (ebben a példában 3 pont).
- Szín: Beállítja a vízszintes szabály színét (`Color.Blue` ebben a példában).
- NoShade: Megadja, hogy a vízszintes szabálynak legyen-e árnyéka (`true` ebben a példában).

## 4. lépés: Mentse el a dokumentumot

 Végül mentse el a módosított dokumentumot a`Save` módszere a`Document` objektum.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## Következtetés

Az Aspose.Words for .NET segítségével a vízszintes szabályok Word dokumentumokba történő beillesztésének elsajátítása javítja a dokumentumautomatizálási képességeket. Az Aspose.Words rugalmasságának és erejének kihasználásával a fejlesztők hatékonyan ésszerűsíthetik a dokumentum-előállítási és -formázási folyamatokat.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár Word-dokumentumokkal való programozott munkavégzéshez .NET-alkalmazásokban.

### Hogyan tölthetem le az Aspose.Words for .NET fájlt?
 Az Aspose.Words for .NET letölthető innen[itt](https://releases.aspose.com/words/net/).

### Testreszabhatom a vízszintes szabályok megjelenését az Aspose.Wordsben?
Igen, az Aspose.Words használatával testreszabhatja a vízszintes szabályok különböző szempontjait, például igazítását, szélességét, magasságát, színét és árnyékolását.

### Az Aspose.Words alkalmas vállalati szintű dokumentumfeldolgozásra?
Igen, az Aspose.Words széles körben használatos vállalati környezetekben robusztus dokumentumkezelési képességei miatt.

### Hol kaphatok támogatást az Aspose.Words for .NET-hez?
 Támogatásért és közösségi részvételért látogassa meg a[Aspose.Words fórum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
