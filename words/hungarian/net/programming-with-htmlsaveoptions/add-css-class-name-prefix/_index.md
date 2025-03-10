---
title: Adja hozzá a Css osztálynév előtagot
linktitle: Adja hozzá a Css osztálynév előtagot
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan adhat hozzá CSS-osztálynév-előtagot Word-dokumentumok HTML-ként történő mentésekor az Aspose.Words for .NET használatával. Részletes útmutató, kódrészletek és GYIK mellékelve.
weight: 10
url: /hu/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adja hozzá a Css osztálynév előtagot

## Bevezetés

Üdvözöljük! Ha belemerül az Aspose.Words for .NET világába, egy csemege vár rád. Ma megvizsgáljuk, hogyan adhatunk hozzá CSS-osztálynév-előtagot egy Word-dokumentum HTML formátumban történő mentésekor az Aspose.Words for .NET használatával. Ez a funkció rendkívül hasznos, ha el szeretné kerülni az osztálynév-ütközést a HTML-fájlokban.

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg arról, hogy rendelkezik a következőkkel:

-  Aspose.Words for .NET: Ha még nem telepítette,[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Visual Studio vagy bármely más C# IDE.
-  Word-dokumentum: Egy nevű dokumentumot fogunk használni`Rendering.docx`. Helyezze el a projektkönyvtárába.

## Névterek importálása

Először győződjön meg arról, hogy a szükséges névtereket importálta a C# projektbe. Adja hozzá ezeket a kódfájl tetejéhez:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Most pedig merüljünk el a lépésről lépésre szóló útmutatóban!

## 1. lépés: Állítsa be projektjét

Mielőtt elkezdhetnénk hozzáadni egy CSS-osztálynév előtagot, állítsuk be projektünket.

### 1.1. lépés: Hozzon létre egy új projektet

 Indítsa el a Visual Studio-t, és hozzon létre egy új Console App projektet. Nevezd valami fülbemászónak, mint pl`AsposeCssPrefixExample`.

### 1.2. lépés: Adja hozzá az Aspose.Words for .NET-et

Ha még nem tette meg, adja hozzá az Aspose.Words for .NET-et projektjéhez a NuGet segítségével. Egyszerűen nyissa meg a NuGet Package Manager konzolt, és futtassa:

```bash
Install-Package Aspose.Words
```

Nagy! Most készen állunk a kódolás megkezdésére.

## 2. lépés: Töltse be a dokumentumot

Az első dolog, amit tennünk kell, hogy betöltsük azt a Word dokumentumot, amelyet HTML-be szeretnénk konvertálni.

### 2.1. lépés: Határozza meg a dokumentum elérési útját

 Állítsa be a dokumentumkönyvtár elérési útját. Az oktatóanyag kedvéért tegyük fel, hogy a dokumentuma egy nevű mappában található`Documents` projektkönyvtárában.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### 2.2. lépés: Töltse be a dokumentumot

Most töltsük be a dokumentumot az Aspose.Words használatával:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Konfigurálja a HTML mentési beállításokat

Ezután konfigurálnunk kell a HTML-mentési beállításokat, hogy tartalmazzák a CSS-osztálynév előtagját.

### 3.1. lépés: Hozzon létre HTML mentési beállításokat

 Példányosítsa a`HtmlSaveOptions` objektumot, és állítsa be a CSS stíluslap típusát`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### 3.2. lépés: Állítsa be a CSS-osztálynév előtagját

 Most állítsuk be a`CssClassNamePrefix` tulajdonságot a kívánt előtaghoz. Ebben a példában használjuk`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## 4. lépés: Mentse el a dokumentumot HTML-ként

Végül mentsük el a dokumentumot HTML fájlként a beállított opciókkal.


Adja meg a kimeneti HTML fájl elérési útját, és mentse a dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## 5. lépés: Ellenőrizze a kimenetet

 A projekt futtatása után navigáljon a sajátjához`Documents` mappát. Meg kell találnia egy nevű HTML-fájlt`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` . Nyissa meg ezt a fájlt egy szövegszerkesztőben vagy böngészőben, és ellenőrizze, hogy a CSS-osztályok rendelkeznek-e az előtaggal`pfx_`.

## Következtetés

És megvan! Az alábbi lépések végrehajtásával sikeresen hozzáadott egy CSS-osztálynév előtagot a HTML-kimenethez az Aspose.Words for .NET használatával. Ez az egyszerű, de hatékony funkció segítségével tiszta és konfliktusmentes stílusokat tarthat fenn HTML-dokumentumaiban.

## GYIK

### Használhatok más előtagot minden mentési művelethez?
 Igen, személyre szabhatja az előtagot minden egyes dokumentum mentésekor, ha módosítja a`CssClassNamePrefix` ingatlan.

### Ez a módszer támogatja a beépített CSS-t?
 A`CssClassNamePrefix` tulajdonság külső CSS-sel működik. A beépített CSS-hez más megközelítésre lesz szüksége.

### Hogyan vehetek fel más HTML mentési lehetőségeket?
 Különféle tulajdonságait konfigurálhatja`HtmlSaveOptions` a HTML-kimenet testreszabásához. Ellenőrizze a[dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Elmenthető a HTML adatfolyamba?
 Teljesen! A dokumentumot adatfolyamba mentheti, ha átadja a stream objektumot a`Save` módszer.

### Hogyan kaphatok támogatást, ha problémákba ütközöm?
 Támogatást kaphat a[Aspose fórum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
