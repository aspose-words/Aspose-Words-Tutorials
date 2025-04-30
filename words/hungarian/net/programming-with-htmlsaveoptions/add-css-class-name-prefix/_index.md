---
"description": "Ismerd meg, hogyan adhatsz hozzá CSS osztálynév előtagot Word dokumentumok HTML formátumban történő mentésekor az Aspose.Words for .NET használatával. Lépésről lépésre útmutató, kódrészletek és GYIK is találhatók benne."
"linktitle": "CSS osztálynév előtag hozzáadása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "CSS osztálynév előtag hozzáadása"
"url": "/hu/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# CSS osztálynév előtag hozzáadása

## Bevezetés

Üdvözlünk! Ha most merülsz el az Aspose.Words for .NET világában, igazi meglepetésben lesz részed. Ma azt vizsgáljuk meg, hogyan adhatsz hozzá CSS osztálynév-előtagot egy Word-dokumentum HTML-ként történő mentésekor az Aspose.Words for .NET használatával. Ez a funkció rendkívül hasznos, ha el szeretnéd kerülni az osztálynév-ütközéseket a HTML-fájljaidban.

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:

- Aspose.Words .NET-hez: Ha még nem telepítetted, [töltsd le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Visual Studio vagy bármilyen más C# IDE.
- Egy Word-dokumentum: Egy nevű dokumentumot fogunk használni. `Rendering.docx`. Helyezd el a projektkönyvtáradba.

## Névterek importálása

Először is, győződj meg róla, hogy importáltad a szükséges névtereket a C# projektedbe. Add hozzá ezeket a kódfájl elejéhez:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Most pedig lássuk a lépésről lépésre szóló útmutatót!

## 1. lépés: A projekt beállítása

Mielőtt elkezdhetnénk hozzáadni egy CSS osztálynév előtagot, állítsuk be a projektünket.

### 1.1. lépés: Új projekt létrehozása

Indítsd el a Visual Studio-t, és hozz létre egy új Console App projektet. Nevezd el valami figyelemfelkeltővel, például: `AsposeCssPrefixExample`.

### 1.2. lépés: Aspose.Words hozzáadása .NET-hez

Ha még nem tetted meg, add hozzá az Aspose.Words for .NET csomagot a projektedhez a NuGeten keresztül. Egyszerűen nyisd meg a NuGet csomagkezelő konzolt, és futtasd a következőt:

```bash
Install-Package Aspose.Words
```

Remek! Most már készen állunk a kódolás elkezdésére.

## 2. lépés: Töltse be a dokumentumot

Az első dolog, amit tennünk kell, az a Word dokumentum betöltése, amelyet HTML-be szeretnénk konvertálni.

### 2.1. lépés: A dokumentum elérési útjának meghatározása

Állítsa be a dokumentumkönyvtár elérési útját. A bemutató kedvéért tegyük fel, hogy a dokumentum egy mappában található, amelynek neve: `Documents` a projektkönyvtáradban.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### 2.2. lépés: A dokumentum betöltése

Most töltsük be a dokumentumot az Aspose.Words használatával:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: HTML mentési beállítások konfigurálása

Ezután konfigurálnunk kell a HTML mentési beállításait, hogy tartalmazzanak egy CSS osztálynév előtagot.

### 3.1. lépés: HTML mentési beállítások létrehozása

Példányosítsa a `HtmlSaveOptions` objektumot, és állítsa be a CSS stíluslap típusát erre: `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### 3.2. lépés: CSS osztálynév előtagjának beállítása

Most állítsuk be a `CssClassNamePrefix` tulajdonságot a kívánt előtaghoz. Ebben a példában a következőt fogjuk használni: `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## 4. lépés: Mentse el a dokumentumot HTML formátumban

Végül mentsük el a dokumentumot HTML fájlként a konfigurált beállításokkal.


Adja meg a kimeneti HTML fájl elérési útját, és mentse el a dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## 5. lépés: Ellenőrizze a kimenetet

A projekt futtatása után navigáljon a `Documents` mappát. Találnia kell egy HTML fájlt, amelynek neve `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`Nyissa meg ezt a fájlt egy szövegszerkesztőben vagy böngészőben, hogy ellenőrizze, hogy a CSS osztályok rendelkeznek-e az előtaggal. `pfx_`.

## Következtetés

És íme! A következő lépéseket követve sikeresen hozzáadtál egy CSS osztálynév előtagot a HTML-kimenetedhez az Aspose.Words for .NET használatával. Ez az egyszerű, mégis hatékony funkció segít tiszta és ütközésmentes stílusok fenntartásában a HTML-dokumentumaidban.

## GYIK

### Használhatok különböző előtagot minden mentési művelethez?
Igen, minden alkalommal, amikor ment egy dokumentumot, testreszabhatja az előtagot a `CssClassNamePrefix` ingatlan.

### Ez a metódus támogatja az inline CSS-t?
A `CssClassNamePrefix` tulajdonság külső CSS-sel működik. Beágyazott CSS esetén más megközelítésre lesz szükség.

### Hogyan adhatok hozzá további HTML mentési beállításokat?
Különböző tulajdonságokat konfigurálhat `HtmlSaveOptions` a HTML-kimenet testreszabásához. Ellenőrizze a [dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Lehetséges a HTML-t egy adatfolyamba menteni?
Természetesen! A dokumentumot egy adatfolyamba mentheted a stream objektum átadásával a `Save` módszer.

### Hogyan kaphatok támogatást, ha problémákba ütközöm?
Támogatást kaphatsz a [Aspose fórum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}