---
title: Állítsa be a Font Backback beállításokat
linktitle: Állítsa be a Font Backback beállításokat
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan állíthatja be a tartalék betűkészlet-beállításokat az Aspose.Words for .NET-ben. Ez az átfogó útmutató biztosítja, hogy a dokumentumokban szereplő összes karakter helyesen jelenjen meg.
weight: 10
url: /hu/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a Font Backback beállításokat

## Bevezetés

Különböző szövegelemeket, például különböző nyelveket vagy speciális karaktereket tartalmazó dokumentumok használatakor elengedhetetlen, hogy ezek az elemek helyesen jelenjenek meg. Az Aspose.Words for .NET a Font Fallback Settings nevű hatékony funkciót kínálja, amely segít a betűtípusok helyettesítésére vonatkozó szabályok meghatározásában, ha az eredeti betűtípus nem támogat bizonyos karaktereket. Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan állíthatja be a tartalék betűkészlet-beállításokat az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy a következő előfeltételeket teljesítette:

- C# alapismeretek: C# programozási nyelv és .NET keretrendszer ismerete.
-  Aspose.Words for .NET: Töltse le és telepítse a[letöltési link](https://releases.aspose.com/words/net/).
- Fejlesztési környezet: Olyan beállítás, mint a Visual Studio a kód írásához és futtatásához.
-  Dokumentumminta: rendelkezzen mintadokumentummal (pl.`Rendering.docx`) készen áll a tesztelésre.
- Font Fallback Rules XML: Készítsen egy XML-fájlt, amely meghatározza a font backback szabályokat.

## Névterek importálása

Az Aspose.Words használatához importálnia kell a szükséges névtereket. Ez lehetővé teszi a hozzáférést a dokumentumok feldolgozásához szükséges különféle osztályokhoz és módszerekhez.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## 1. lépés: Határozza meg a dokumentumkönyvtárat

Először határozza meg a könyvtárat, ahol a dokumentumot tárolja. Ez elengedhetetlen a dokumentum megkereséséhez és feldolgozásához.

```csharp
// A dokumentumok könyvtárának elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Töltse be a dokumentumot

 Töltse be a dokumentumot egy Aspose.Words-be`Document` objektum. Ez a lépés lehetővé teszi, hogy programozottan dolgozzon a dokumentummal.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Konfigurálja a betűtípus-beállításokat

 Hozzon létre egy újat`FontSettings` objektumot, és töltse be a tartalék font-beállításokat egy XML-fájlból. Ez az XML-fájl tartalmazza a tartalék betűkészlet szabályait.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## 4. lépés: Alkalmazza a Betűtípus-beállításokat a dokumentumra

 Rendelje hozzá a konfigurált`FontSettings` dokumentumhoz. Ez biztosítja, hogy a betűkészlet-visszaállítási szabályok alkalmazásra kerüljenek a dokumentum renderelésekor.

```csharp
doc.FontSettings = fontSettings;
```

## 5. lépés: Mentse el a dokumentumot

Végül mentse el a dokumentumot. A mentési művelet során a rendszer a tartalék betűkészlet-beállításokat használja a megfelelő betűkészlet-csere érdekében.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML fájl: Font Fallback Rules

Íme egy példa arra, hogyan kell kinéznie a font tartalék szabályokat meghatározó XML-fájlnak:

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

Ha követi ezeket a lépéseket, hatékonyan állíthatja be és használhatja az Aspose.Words for .NET betűtípus-visszaállítási beállításait. Ez biztosítja, hogy a dokumentumok minden karaktert helyesen jelenítsenek meg, még akkor is, ha az eredeti betűtípus nem támogat bizonyos karaktereket. Ezeknek a beállításoknak a végrehajtása nagymértékben javítja a dokumentumok minőségét és olvashatóságát.

## GYIK

### 1. kérdés: Mi az a Font Fallback?

A Font Fallback egy olyan funkció, amely lehetővé teszi a betűtípusok helyettesítését, ha az eredeti betűtípus nem támogat bizonyos karaktereket, így biztosítva az összes szövegelem megfelelő megjelenítését.

### 2. kérdés: Megadhatok több tartalék betűtípust?

Igen, több tartalék betűtípust is megadhat az XML-szabályokban. Az Aspose.Words az egyes betűtípusokat a megadott sorrendben ellenőrzi, amíg meg nem találja azt, amelyik támogatja a karaktert.

### 3. kérdés: Honnan tölthetem le az Aspose.Words for .NET fájlt?

 Letöltheti a[Aspose letöltési oldal](https://releases.aspose.com/words/net/).

### 4. kérdés: Hogyan hozhatom létre az XML-fájlt a font tartalék szabályokhoz?

Az XML fájl bármilyen szövegszerkesztővel létrehozható. Az oktatóanyagban található példában látható szerkezetet kell követnie.

### 5. kérdés: Van-e támogatás az Aspose.Words számára?

 Igen, találsz támogatást a[Aspose.Words támogatási fórum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
