---
title: Bekerített kód
linktitle: Bekerített kód
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan adhat hozzá elkerített kódokat és információs karakterláncokat Word-dokumentumokhoz az Aspose.Words for .NET használatával. Lépésről lépésre útmutató mellékelve. Javítsa dokumentumformázási készségeit.
weight: 10
url: /hu/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bekerített kód

## Bevezetés

Szia kódolótárs! Ma az Aspose.Words for .NET világába merülünk, hogy elsajátíthassuk az elkerített kódok és az információs karakterláncokkal ellátott kódok Word-dokumentumaihoz való hozzáadásának művészetét. Képzelje el Word-dokumentumát vászonként, és Ön, a művész, egy tapasztalt fejlesztő pontosságával fog festeni. Az Aspose.Words segítségével programozottan javíthatja dokumentumait strukturált, formázott kódblokkokkal, így műszaki dokumentumai professzionalizmussal és egyértelműséggel ragyognak.

## Előfeltételek

Mielőtt belevágnánk az oktatóanyagba, győződjünk meg arról, hogy mindennel rendelkezik, amire szüksége van:

- A C# alapismeretei: A C# általános ismerete segít a fogalmak gyors megértésében.
-  Aspose.Words for .NET: Az Aspose.Words for .NET-re telepítve kell lennie. Ha még nem vetted meg, vedd meg[itt](https://releases.aspose.com/words/net/).
- Fejlesztési környezet: Visual Studio vagy bármely más C# IDE, amivel jól érzi magát.

## Névterek importálása

Először is importálnia kell a szükséges névtereket. Ez olyan, mintha az összes eszközt összegyűjtené egy projekt elindítása előtt.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Most pedig bontsuk le a folyamatot lépésről lépésre.

## 1. lépés: A projekt beállítása

Mielőtt gyönyörű, formázott kódblokkokat hozhatnánk létre a Word-dokumentumban, be kell állítanunk egy új projektet a Visual Studióban.

1. Új projekt létrehozása: Nyissa meg a Visual Studio-t, és hozzon létre egy új C# konzolalkalmazást.
2. Az Aspose.Words hivatkozás hozzáadása: Az Aspose.Words telepítése a NuGet Package Manager segítségével. Ezt úgy teheti meg, hogy jobb gombbal kattint a projektjére a Solution Explorerben, kiválasztja a „NuGet-csomagok kezelése” lehetőséget, és rákeres az Aspose.Words kifejezésre.

## 2. lépés: Inicializálja a DocumentBuildert

Most, hogy a projekt be van állítva, inicializáljuk a DocumentBuildert, amely a fő eszközünk lesz a Word-dokumentum tartalom hozzáadásához.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## 3. lépés: Hozzon létre egy stílust a bekerített kódhoz

Az elkerített kód hozzáadásához először létre kell hoznunk egy stílust. Tekintsd ezt úgy, mint a kódblokk témáját.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 4. lépés: Adjon hozzá elkerített kódot a dokumentumhoz

Ha készen áll a stílusunk, most már egy elkerített kódblokkot is hozzáadhatunk a dokumentumhoz.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## 5. lépés: Hozzon létre egy stílust a bekerített kódhoz az információs karakterlánccal

Néha érdemes lehet megadni a programozási nyelvet, vagy további információkat kell hozzáadni a kódblokkhoz. Alkossunk ehhez egy stílust.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 6. lépés: Adjon hozzá elkerített kódot az információs karakterlánccal a dokumentumhoz

Most adjunk hozzá egy elkerített kódblokkot egy információs karakterlánccal, amely jelzi, hogy C# kódról van szó.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Következtetés

Gratulálok! Az Aspose.Words for .NET segítségével elkerített kódblokkokat és elkerített kódokat adott hozzá a Word-dokumentumokhoz. Ez csak a jéghegy csúcsa. Az Aspose.Words segítségével automatizálhatja és új magasságokba emelheti dokumentumfeldolgozását. Folytasd a felfedezést és boldog kódolást!

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, kezelését és konvertálását.

### Használhatom az Aspose.Words programot más programozási nyelvekkel?
Az Aspose.Words elsősorban a .NET nyelveket támogatja, de vannak verziók Java, Python és más nyelvekre is.

### Az Aspose.Words ingyenesen használható?
 Az Aspose.Words kereskedelmi termék, de ingyenes próbaverziót is letölthet[itt](https://releases.aspose.com/)jellemzőinek feltárására.

### Hogyan kaphatok támogatást az Aspose.Words számára?
 Támogatást kaphat az Aspose közösségtől és a fejlesztőktől[itt](https://forum.aspose.com/c/words/8).

### Milyen egyéb funkciókat kínál az Aspose.Words?
Az Aspose.Words szolgáltatások széles skáláját kínálja, beleértve a dokumentumkonverziót, a sablon alapú dokumentumgenerálást, a jelentéskészítést és még sok mást.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
