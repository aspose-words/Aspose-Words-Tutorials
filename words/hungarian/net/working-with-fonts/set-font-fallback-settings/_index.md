---
"description": "Ismerd meg, hogyan állíthatod be a betűtípus-tartalék beállításokat az Aspose.Words for .NET programban. Ez az átfogó útmutató biztosítja, hogy a dokumentumokban minden karakter helyesen jelenjen meg."
"linktitle": "Betűtípus-tartalék beállítások megadása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Betűtípus-tartalék beállítások megadása"
"url": "/hu/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus-tartalék beállítások megadása

## Bevezetés

Amikor olyan dokumentumokkal dolgozunk, amelyek változatos szöveges elemeket, például különböző nyelveket vagy speciális karaktereket tartalmaznak, elengedhetetlen, hogy ezek az elemek helyesen jelenjenek meg. Az Aspose.Words for .NET egy hatékony funkciót kínál, az úgynevezett Betűtípus-tartalékbeállításokat, amely segít szabályok meghatározásában a betűtípusok helyettesítésére, ha az eredeti betűtípus nem támogat bizonyos karaktereket. Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan állíthatjuk be a Betűtípus-tartalékbeállításokat az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belevágnál az oktatóanyagba, győződj meg róla, hogy a következő előfeltételek teljesülnek:

- C# alapismeretek: Jártasság a C# programozási nyelvben és a .NET keretrendszerben.
- Aspose.Words .NET-hez: Töltse le és telepítse a következő címről: [letöltési link](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Egy olyan beállítás, mint a Visual Studio, a kód írásához és futtatásához.
- Mintadokumentum: Készítsen elő egy mintadokumentumot (pl. `Rendering.docx`) tesztelésre kész.
- Betűtípus-tartalék szabályok XML: Készítsen egy XML fájlt, amely meghatározza a betűtípus-tartalék szabályokat.

## Névterek importálása

Az Aspose.Words használatához importálni kell a szükséges névtereket. Ez hozzáférést biztosít a dokumentumfeldolgozáshoz szükséges különféle osztályokhoz és metódusokhoz.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## 1. lépés: A dokumentumkönyvtár meghatározása

Először is, határozza meg a dokumentum tárolási könyvtárát. Ez elengedhetetlen a dokumentum megtalálásához és feldolgozásához.

```csharp
// A dokumentumok könyvtárának elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: A dokumentum betöltése

Töltsd be a dokumentumodat egy Aspose.Words fájlba `Document` objektum. Ez a lépés lehetővé teszi a dokumentum programozott kezelését.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Betűtípus-beállítások konfigurálása

Hozz létre egy újat `FontSettings` objektumot, és töltse be a betűtípus-tartalék beállításait egy XML fájlból. Ez az XML fájl tartalmazza a betűtípus-tartalék szabályait.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## 4. lépés: Betűtípus-beállítások alkalmazása a dokumentumra

Rendelje hozzá a konfigurált `FontSettings` a dokumentumhoz. Ez biztosítja, hogy a betűtípus-tartalék szabályok érvényesek legyenek a dokumentum megjelenítésekor.

```csharp
doc.FontSettings = fontSettings;
```

## 5. lépés: A dokumentum mentése

Végül mentse el a dokumentumot. A mentési művelet során a betűtípus-tartalék beállítások lesznek érvényben a megfelelő betűtípus-helyettesítés biztosítása érdekében.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML-fájl: Betűtípus-tartalék szabályok

Íme egy példa arra, hogyan kell kinéznie a betűtípus-tartalék szabályokat meghatározó XML-fájlnak:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Következtetés

A következő lépéseket követve hatékonyan beállíthatja és használhatja a Betűtípus-tartalék beállításokat az Aspose.Words for .NET programban. Ez biztosítja, hogy a dokumentumok minden karaktert helyesen jelenítsenek meg, még akkor is, ha az eredeti betűtípus nem támogat bizonyos karaktereket. Ezen beállítások alkalmazása nagymértékben javítja a dokumentumok minőségét és olvashatóságát.

## GYIK

### 1. kérdés: Mi az a betűtípus-tartalék?

A Betűkészlet-tartalék egy olyan funkció, amely lehetővé teszi a betűtípusok helyettesítését, ha az eredeti betűtípus nem támogat bizonyos karaktereket, biztosítva az összes szöveges elem megfelelő megjelenítését.

### 2. kérdés: Megadhatok több tartalék betűtípust?

Igen, több tartalék betűtípust is megadhatsz az XML szabályokban. Az Aspose.Words a megadott sorrendben ellenőrzi az egyes betűtípusokat, amíg meg nem találja a karaktert támogatót.

### 3. kérdés: Hol tudom letölteni az Aspose.Words .NET-hez készült verzióját?

Letöltheted innen: [Aspose letöltési oldal](https://releases.aspose.com/words/net/).

### 4. kérdés: Hogyan hozhatom létre az XML fájlt a betűtípus-tartalékszabályokhoz?

Az XML fájl bármilyen szövegszerkesztővel létrehozható. A példában bemutatott struktúrát kell követnie.

### 5. kérdés: Van-e támogatás az Aspose.Words-höz?

Igen, támogatást találhatsz a következő oldalon: [Aspose.Words támogatói fórum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}