---
"description": "Tanuld meg, hogyan exportálhatsz erőforrásokat, például CSS-t és betűtípusokat, miközben Word-dokumentumokat mentesz HTML-ként az Aspose.Words for .NET segítségével. Kövesd lépésről lépésre szóló útmutatónkat."
"linktitle": "Export erőforrások"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Export erőforrások"
"url": "/hu/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Export erőforrások

## Bevezetés

Szia, tech-rajongó társam! Ha valaha is szükséged volt Word-dokumentumok HTML-be konvertálására, jó helyen jársz. Ma az Aspose.Words for .NET csodálatos világába kalauzolunk el. Ez a hatékony könyvtár megkönnyíti a Word-dokumentumok programozott kezelését. Ebben az oktatóanyagban végigvezetünk az erőforrások, például a betűtípusok és a CSS exportálásának lépésein, amikor egy Word-dokumentumot HTML-ként mentesz az Aspose.Words for .NET segítségével. Csatold be az öved egy szórakoztató, informatív utazáshoz!

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg róla, hogy minden megvan, amire szükséged van az induláshoz. Íme egy gyors ellenőrzőlista:

1. Visual Studio: Győződjön meg róla, hogy a Visual Studio telepítve van a gépén. Letöltheti innen: [Visual Studio weboldal](https://visualstudio.microsoft.com/).
2. Aspose.Words for .NET: Szükséged lesz az Aspose.Words for .NET könyvtárra. Ha még nem szerezted meg, töltsd le az ingyenes próbaverziót innen: [Aspose kiadások](https://releases.aspose.com/words/net/) vagy vásárolja meg a [Aspose Áruház](https://purchase.aspose.com/buy).
3. C# alapismeretek: A C# alapvető ismerete segít a kódpéldák követésében.

Mindez megvan? Remek! Térjünk át a szükséges névterek importálására.

## Névterek importálása

Az Aspose.Words .NET-hez való használatához a projektben szerepeltetni kell a releváns névtereket. Így teheti ezt meg:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ezek a névterek kulcsfontosságúak az Aspose.Words osztályok és metódusok eléréséhez, amelyeket a bemutatónkban használni fogunk.

Nézzük meg részletesebben, hogyan exportáljuk az erőforrásokat egy Word-dokumentum HTML-ként történő mentésekor. Lépésről lépésre bemutatjuk, hogy könnyen követhető legyen.

## 1. lépés: Dokumentumkönyvtár beállítása

Először is meg kell adnia a dokumentumok könyvtárának elérési útját. Itt található a Word-dokumentum, és itt lesz mentve a HTML-fájl.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Csere `"YOUR DOCUMENT DIRECTORY"` a könyvtár tényleges elérési útjával.

## 2. lépés: Töltse be a Word dokumentumot

Ezután töltsük be a HTML-lé konvertálni kívánt Word-dokumentumot. Ebben az oktatóanyagban egy nevű dokumentumot fogunk használni. `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Ez a kódsor betölti a dokumentumot a megadott könyvtárból.

## 3. lépés: HTML mentési beállítások konfigurálása

Erőforrások, például CSS és betűtípusok exportálásához konfigurálnia kell a `HtmlSaveOptions`Ez a lépés kulcsfontosságú annak biztosításához, hogy a HTML-kimenet jól strukturált legyen, és tartalmazza a szükséges erőforrásokat.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://példa.com/erőforrások"
};
```

Nézzük meg, hogy mit csinálnak az egyes opciók:
- `CssStyleSheetType = CssStyleSheetType.External`: Ez a beállítás meghatározza, hogy a CSS stílusokat egy külső stíluslapban kell menteni.
- `ExportFontResources = true`: Ez lehetővé teszi a betűtípus-erőforrások exportálását.
- `ResourceFolder = dataDir + "Resources"`: Megadja a helyi mappát, ahová az erőforrások (például betűtípusok és CSS-fájlok) mentésre kerülnek.
- `ResourceFolderAlias = "http://example.com/resources"`: Beállít egy aliast az erőforrásmappához, amelyet a HTML fájlban fog használni.

## 4. lépés: Mentse el a dokumentumot HTML formátumban

A mentési beállítások konfigurálása után az utolsó lépés a dokumentum HTML-fájlként történő mentése. Így teheti meg:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Ez a kódsor HTML formátumban menti a dokumentumot az exportált erőforrásokkal együtt.

## Következtetés

És íme! Sikeresen exportáltál erőforrásokat, miközben egy Word-dokumentumot HTML-ként mentettél az Aspose.Words for .NET segítségével. Ezzel a hatékony könyvtárral a Word-dokumentumok programozott kezelése gyerekjáték. Akár egy webes alkalmazáson dolgozol, akár csak offline használatra kell konvertálnod a dokumentumokat, az Aspose.Words segít neked.

## GYIK

### Exportálhatok képeket betűtípusokkal és CSS-sel együtt?
Igen, lehetséges! Az Aspose.Words for .NET képexportálást is támogat. Csak győződjön meg róla, hogy konfigurálja a `HtmlSaveOptions` ennek megfelelően.

### Van mód CSS beágyazására külső stíluslap használata helyett?
Teljesen. Beállíthatod. `CssStyleSheetType` hogy `CssStyleSheetType.Embedded` ha a beágyazott stílusokat részesíted előnyben.

### Hogyan tudom testreszabni a kimeneti HTML fájl nevét?
Bármilyen fájlnevet megadhatsz a `doc.Save` módszer. Például, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Az Aspose.Words támogat más formátumokat is a HTML-en kívül?
Igen, számos formátumot támogat, beleértve a PDF, DOCX, TXT és egyebeket. Nézd meg a [dokumentáció](https://reference.aspose.com/words/net/) a teljes listáért.

### Hol kaphatok további támogatást és forrásokat?
További segítségért látogassa meg a [Aspose.Words támogatói fórum](https://forum.aspose.com/c/words/8)Részletes dokumentációt és példákat is találhat a következő címen: [Aspose weboldal](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}