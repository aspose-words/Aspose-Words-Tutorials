---
"description": "Tanuld meg, hogyan exportálhatsz fejléc- és lábléckönyvjelzőket egy Word-dokumentumból PDF-be az Aspose.Words for .NET használatával lépésről lépésre bemutató útmutatónkkal."
"linktitle": "Word dokumentum fejlécének, láblécének könyvjelzőinek exportálása PDF dokumentumba"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Word dokumentum fejlécének, láblécének könyvjelzőinek exportálása PDF dokumentumba"
"url": "/hu/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum fejlécének, láblécének könyvjelzőinek exportálása PDF dokumentumba

## Bevezetés

Word-dokumentumok PDF-be konvertálása gyakori feladat, különösen akkor, ha a dokumentumokat formázásuk megőrzése mellett szeretné megosztani vagy archiválni. Ezek a dokumentumok néha fontos könyvjelzőket tartalmaznak a fejlécekben és a láblécekben. Ebben az oktatóanyagban bemutatjuk, hogyan exportálhatja ezeket a könyvjelzőket egy Word-dokumentumból PDF-be az Aspose.Words for .NET segítségével.

## Előfeltételek

Mielőtt belevágnánk, győződjünk meg róla, hogy a következőkkel rendelkezünk:

- Aspose.Words .NET-hez: Telepítenie kell az Aspose.Words .NET-hez programot. Letöltheti innen: [itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Állítsa be a fejlesztői környezetét. Használhatja a Visual Studio-t vagy bármilyen más .NET-kompatibilis IDE-t.
- C# alapismeretek: A kódpéldák követéséhez C# programozási ismeretek szükségesek.

## Névterek importálása

Először is importálnod kell a szükséges névtereket a C# projektedbe. Add hozzá ezeket a sorokat a kódfájl elejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bontsuk le a folyamatot könnyen követhető lépésekre.

## 1. lépés: A dokumentum inicializálása

Az első lépés a Word-dokumentum betöltése. Így teheted meg:

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

Ebben a lépésben egyszerűen megadod a dokumentumkönyvtár elérési útját, és betöltöd a Word-dokumentumot.

## 2. lépés: PDF mentési beállítások konfigurálása

Ezután konfigurálnia kell a PDF mentési beállításait, hogy a fejlécekben és láblécekben lévő könyvjelzők megfelelően exportálódjanak.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Itt állítjuk be a `PdfSaveOptions`. A `DefaultBookmarksOutlineLevel` tulajdonság beállítja a könyvjelzők vázlatszintjét, és a `HeaderFooterBookmarksExportMode` tulajdonság biztosítja, hogy a fejlécekben és láblécekben lévő könyvjelzőknek csak az első előfordulása kerüljön exportálásra.

## 3. lépés: Mentse el a dokumentumot PDF formátumban

Végül mentse el a dokumentumot PDF formátumban a konfigurált beállításokkal.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

Ebben a lépésben a megadott elérési útra menti a dokumentumot a konfigurált beállításokkal.

## Következtetés

És íme! A következő lépéseket követve könnyedén exportálhatsz könyvjelzőket egy Word-dokumentum fejlécéből és láblécéből PDF-be az Aspose.Words for .NET segítségével. Ez a módszer biztosítja, hogy a dokumentumban található fontos navigációs segédletek megmaradjanak a PDF formátumban, így az olvasók könnyebben eligazodhatnak a dokumentumban.

## GYIK

### Exportálhatom az összes könyvjelzőt a Word dokumentumból PDF-be?

Igen, megteheted. A `PdfSaveOptions`, szükség esetén módosíthatja a beállításokat úgy, hogy az összes könyvjelző szerepeljen.

### Mi van, ha a dokumentum törzséből is szeretnék könyvjelzőket exportálni?

Beállíthatja a `OutlbaneOptions` in `PdfSaveOptions` hogy könyvjelzőket is beillesszen a dokumentum törzséből.

### Lehetséges a könyvjelzők szintjeinek testreszabása a PDF-ben?

Természetesen! Testreszabhatod a `DefaultBookmarksOutlineLevel` tulajdonsággal különböző vázlatszinteket állíthat be a könyvjelzőkhöz.

### Hogyan kezelhetem a könyvjelzők nélküli dokumentumokat?

Ha a dokumentumban nincsenek könyvjelzők, a PDF könyvjelző körvonal nélkül generálódik. Győződjön meg róla, hogy a dokumentum tartalmaz könyvjelzőket, ha szüksége van rájuk a PDF-ben.

### Használhatom ezt a módszert más dokumentumtípusokhoz, például DOCX-hez vagy RTF-hez?

Igen, az Aspose.Words for .NET különféle dokumentumtípusokat támogat, beleértve a DOCX, RTF és másokat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}