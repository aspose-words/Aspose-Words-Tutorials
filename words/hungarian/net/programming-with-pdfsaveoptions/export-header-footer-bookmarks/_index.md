---
title: Word-dokumentum fejléc-lábléc könyvjelzőinek exportálása PDF-dokumentumba
linktitle: Word-dokumentum fejléc-lábléc könyvjelzőinek exportálása PDF-dokumentumba
second_title: Aspose.Words Document Processing API
description: A lépésenkénti útmutatónkból megtudhatja, hogyan exportálhat fejléc- és lábléc-könyvjelzőket Word-dokumentumból PDF-be az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-dokumentum fejléc-lábléc könyvjelzőinek exportálása PDF-dokumentumba

## Bevezetés

A Word-dokumentumok PDF-be konvertálása gyakori feladat, különösen akkor, ha dokumentumokat szeretne megosztani vagy archiválni, miközben megőrzi a formázásukat. Néha ezek a dokumentumok fontos könyvjelzőket tartalmaznak a fejlécekben és láblécekben. Ebben az oktatóanyagban végigvezetjük a könyvjelzők Word-dokumentumból PDF-be való exportálásának folyamatát az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belemerülnénk, győződjön meg arról, hogy rendelkezik az alábbiakkal:

- Aspose.Words for .NET: Az Aspose.Words for .NET-re telepítve kell lennie. Letöltheti innen[itt](https://releases.aspose.com/words/net/).
- Fejlesztési környezet: Állítsa be fejlesztői környezetét. Használhatja a Visual Studio-t vagy bármely más .NET-kompatibilis IDE-t.
- Alapvető C# ismerete: A kódpéldák követéséhez a C# programozás ismerete szükséges.

## Névterek importálása

Először is importálnia kell a szükséges névtereket a C# projektbe. Adja hozzá ezeket a sorokat a kódfájl tetejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bontsuk le a folyamatot könnyen követhető lépésekre.

## 1. lépés: Inicializálja a dokumentumot

Az első lépés a Word dokumentum betöltése. A következőképpen teheti meg:

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

Ebben a lépésben egyszerűen megadja a dokumentumkönyvtár elérési útját, és betölti a Word dokumentumot.

## 2. lépés: Konfigurálja a PDF mentési beállításokat

Ezután konfigurálnia kell a PDF mentési beállításait, hogy biztosítsa a fejlécekben és láblécekben lévő könyvjelzők megfelelő exportálását.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Itt beállítjuk a`PdfSaveOptions` . A`DefaultBookmarksOutlineLevel` tulajdonság beállítja a könyvjelzők körvonalának szintjét, és a`HeaderFooterBookmarksExportMode` tulajdonság biztosítja, hogy csak a fejlécekben és láblécekben lévő könyvjelzők első előfordulása kerüljön exportálásra.

## 3. lépés: Mentse el a dokumentumot PDF formátumban

Végül mentse a dokumentumot PDF-ként a konfigurált beállításokkal.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

Ebben a lépésben elmenti a dokumentumot a megadott elérési útra az Ön által konfigurált beállításokkal.

## Következtetés

És megvan! Ha követi ezeket a lépéseket, az Aspose.Words for .NET segítségével egyszerűen exportálhat könyvjelzőket egy Word-dokumentum fejlécéből és láblécéből PDF-be. Ez a módszer biztosítja, hogy a dokumentumon belüli fontos navigációs segédanyagok PDF formátumban megmaradjanak, így az olvasók könnyebben navigálhatnak a dokumentumban.

## GYIK

### Exportálhatok minden könyvjelzőt a Word-dokumentumból PDF-be?

 Igen, megteheti. A`PdfSaveOptions`, szükség esetén módosíthatja a beállításokat úgy, hogy az összes könyvjelzőt tartalmazza.

### Mi a teendő, ha a dokumentumtörzsből is szeretnék könyvjelzőket exportálni?

 Beállíthatja a`OutlineOptions` be`PdfSaveOptions` hogy könyvjelzőket vegyen fel a dokumentum törzséből.

### Testreszabható a könyvjelző szintje a PDF-ben?

 Teljesen! Testreszabhatja a`DefaultBookmarksOutlineLevel` tulajdonságot a könyvjelzők különböző körvonalainak beállításához.

### Hogyan kezelhetem a könyvjelzők nélküli dokumentumokat?

Ha a dokumentumban nincsenek könyvjelzők, a PDF-fájl könyvjelzővázlatok nélkül jön létre. Győződjön meg róla, hogy a dokumentum tartalmaz könyvjelzőket, ha szüksége van rájuk a PDF-ben.

### Használhatom ezt a módszert más dokumentumtípusokhoz, például DOCX vagy RTF?

Igen, az Aspose.Words for .NET különféle dokumentumtípusokat támogat, beleértve a DOCX-et, az RTF-et és másokat.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
