---
title: Erőforrások exportálása
linktitle: Erőforrások exportálása
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan exportálhat erőforrásokat, például CSS-t és betűtípusokat, miközben Word-dokumentumokat menthet HTML-ként az Aspose.Words for .NET használatával. Kövesse lépésenkénti útmutatónkat.
weight: 10
url: /hu/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erőforrások exportálása

## Bevezetés

Üdvözlet, technológiai rajongó kollégám! Ha valaha is azon kapta magát, hogy Word-dokumentumokat kell konvertálnia HTML-be, akkor jó helyen jár. Ma az Aspose.Words for .NET csodálatos világába merülünk. Ezzel a hatékony könyvtárral gyerekjáték a Word-dokumentumokkal programozottan dolgozni. Ebben az oktatóanyagban végigvezetjük az erőforrások, például a betűtípusok és a CSS exportálásának lépéseit, amikor egy Word-dokumentumot HTML-ként mentünk az Aspose.Words for .NET használatával. Csatlakozzon egy szórakoztató, informatív utazáshoz!

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg arról, hogy mindennel megvan, ami az induláshoz szükséges. Íme egy gyors ellenőrző lista:

1.  Visual Studio: Győződjön meg arról, hogy a Visual Studio telepítve van a gépen. Letöltheti a[Visual Studio webhely](https://visualstudio.microsoft.com/).
2.  Aspose.Words for .NET: Szüksége lesz az Aspose.Words for .NET könyvtárra. Ha még nem szerezted meg, szerezd be az ingyenes próbaverziót[Aspose Releases](https://releases.aspose.com/words/net/) vagy vásárolja meg a[Aspose Store](https://purchase.aspose.com/buy).
3. Alapvető C# ismerete: A C# alapvető ismerete segít a kódpéldák követésében.

Megvan az egész? Nagy! Térjünk át a szükséges névterek importálására.

## Névterek importálása

Az Aspose.Words for .NET használatához fel kell vennie a megfelelő névtereket a projektbe. Íme, hogyan kell csinálni:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ezek a névterek kulcsfontosságúak az Aspose.Words osztályok és metódusok eléréséhez, amelyeket oktatóanyagunkban fogunk használni.

Bontsuk le az erőforrások exportálásának folyamatát, amikor egy Word-dokumentumot HTML-ként mentünk. Lépésről lépésre tesszük, így könnyen követhető.

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Először is meg kell adnia a dokumentumkönyvtár elérési útját. Ez az a hely, ahol a Word-dokumentum található, és ahol a HTML-fájl mentésre kerül.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a címtár tényleges elérési útjával.

## 2. lépés: Töltse be a Word-dokumentumot

 Ezután töltsük be a HTML-be konvertálni kívánt Word-dokumentumot. Ebben az oktatóanyagban egy dokumentumot fogunk használni`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Ez a kódsor betölti a dokumentumot a megadott könyvtárból.

## 3. lépés: Konfigurálja a HTML mentési beállításokat

Az erőforrások, például a CSS és a betűtípusok exportálásához konfigurálnia kell a`HtmlSaveOptions`. Ez a lépés kulcsfontosságú annak biztosításához, hogy a HTML-kimenet jól strukturált legyen, és tartalmazza a szükséges erőforrásokat.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

Nézzük meg, mit csinálnak az egyes lehetőségek:
- `CssStyleSheetType = CssStyleSheetType.External`: Ez a beállítás azt határozza meg, hogy a CSS-stílusokat külső stíluslapon kell menteni.
- `ExportFontResources = true`: Ez lehetővé teszi a font erőforrások exportálását.
- `ResourceFolder = dataDir + "Resources"`: Megadja azt a helyi mappát, ahová az erőforrások (például a betűtípusok és CSS-fájlok) mentésre kerülnek.
- `ResourceFolderAlias = "http://example.com/resources"`: Beállít egy álnevet a HTML-fájlban használt erőforrásmappához.

## 4. lépés: Mentse el a dokumentumot HTML-ként

A konfigurált mentési beállításokkal az utolsó lépés a dokumentum HTML-fájlként történő mentése. Íme, hogyan kell csinálni:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Ez a kódsor HTML formátumban menti a dokumentumot az exportált erőforrásokkal együtt.

## Következtetés

És megvan! Sikeresen exportálta az erőforrásokat, miközben egy Word-dokumentumot mentett HTML-ként az Aspose.Words for .NET használatával. Ezzel a hatékony könyvtárral a Word-dokumentumok programozott kezelése egy szelet tortát jelent. Akár egy webalkalmazáson dolgozik, akár csak dokumentumokat kell konvertálnia offline használatra, az Aspose.Words mindent megtesz.

## GYIK

### Exportálhatok képeket betűtípusokkal és CSS-sel együtt?
 Igen, lehet! Az Aspose.Words for .NET támogatja a képek exportálását is. Csak ügyeljen arra, hogy konfigurálja a`HtmlSaveOptions` ennek megfelelően.

### Van mód CSS beágyazására külső stíluslap használata helyett?
 Teljesen. Beállíthatod`CssStyleSheetType` hogy`CssStyleSheetType.Embedded` ha jobban szereti a beágyazott stílusokat.

### Hogyan szabhatom testre a kimeneti HTML-fájl nevét?
 Tetszőleges fájlnevet megadhat a`doc.Save` módszer. Például,`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Az Aspose.Words a HTML-en kívül más formátumokat is támogat?
 Igen, különféle formátumokat támogat, beleértve a PDF, DOCX, TXT és még sok más formátumot. Nézze meg a[dokumentáció](https://reference.aspose.com/words/net/) a teljes listáért.

### Hol kaphatok több támogatást és forrást?
További segítségért keresse fel a[Aspose.Words támogatási fórum](https://forum.aspose.com/c/words/8) . Részletes dokumentációt és példákat is találhat a[Aspose honlapja](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
