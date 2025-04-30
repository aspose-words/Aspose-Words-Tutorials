---
"description": "Ismerje meg, hogyan menthet Word dokumentumokat PDF formátumban az Aspose.Words for Java segítségével. Testreszabhatja a betűtípusokat, tulajdonságokat és a képminőséget. Átfogó útmutató a PDF konvertáláshoz."
"linktitle": "Dokumentumok mentése PDF formátumban"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok mentése PDF formátumban az Aspose.Words for Java programban"
"url": "/hu/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése PDF formátumban az Aspose.Words for Java programban


## Bevezetés a dokumentumok PDF formátumban történő mentéséhez az Aspose.Words for Java programban

Ebben a lépésről lépésre bemutató útmutatóban megvizsgáljuk, hogyan menthet dokumentumokat PDF formátumban az Aspose.Words for Java segítségével. Áttekintjük a PDF-konvertálás különböző aspektusait, és kódpéldákat is bemutatunk a folyamat megkönnyítése érdekében.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

- Java fejlesztőkészlet (JDK) telepítve van a rendszerére.
- Aspose.Words Java könyvtárhoz. Letöltheted innen: [itt](https://releases.aspose.com/words/java/).

## Dokumentum konvertálása PDF-be

Word dokumentum PDF-be konvertálásához a következő kódrészletet használhatja:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Csere `"input.docx"` a Word-dokumentum elérési útjával és `"output.pdf"` a kívánt kimeneti PDF fájl elérési útjával.

## PDF mentési beállítások vezérlése

A PDF mentési beállításait a következővel vezérelheti: `PdfSaveOptions` osztály. Például a PDF dokumentum megjelenítendő címét a következőképpen állíthatja be:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Betűtípusok beágyazása PDF-be

Betűtípusok beágyazásához a létrehozott PDF-be, használja a következő kódot:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Dokumentumtulajdonságok testreszabása

A létrehozott PDF dokumentum tulajdonságait testreszabhatja. Például:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Dokumentumstruktúra exportálása

A dokumentumstruktúra exportálásához állítsa be a `exportDocumentStructure` lehetőség `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Képtömörítés

A képtömörítést a következő kóddal szabályozhatod:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Utolsó nyomtatott tulajdonság frissítése

A PDF „Utolsó nyomtatás” tulajdonságának frissítéséhez használja a következőt:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## DML 3D effektek renderelése

A DML 3D effektek speciális rendereléséhez állítsa be a renderelési módot:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Képek interpolálása

A képminőség javítása érdekében engedélyezheti a képinterpolációt:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Következtetés

Az Aspose.Words for Java átfogó képességeket kínál a Word dokumentumok PDF formátumba konvertálásához, rugalmassággal és testreszabási lehetőségekkel. A PDF kimenet különböző aspektusait, például a betűtípusokat, a dokumentum tulajdonságait, a képtömörítést és egyebeket szabályozhatja.

## GYIK

### Hogyan konvertálhatok egy Word dokumentumot PDF-be az Aspose.Words for Java használatával?

Word dokumentum PDF-be konvertálásához használja a következő kódot:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Csere `"input.docx"` a Word-dokumentum elérési útjával és `"output.pdf"` a kívánt kimeneti PDF fájl elérési útjával.

### Beágyazhatok betűtípusokat az Aspose.Words for Java által generált PDF-be?

Igen, beágyazhat betűtípusokat a PDF-be a beállítással `setEmbedFullFonts` lehetőség `true` ban `PdfSaveOptions`Íme egy példa:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Hogyan szabhatom testre a dokumentum tulajdonságait a létrehozott PDF-ben?

A PDF dokumentum tulajdonságait a következővel szabhatja testre: `setCustomPropertiesExport` opció `PdfSaveOptions`Például:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Mi a képtömörítés célja az Aspose.Words for Java programban?

A képtömörítés lehetővé teszi a létrehozott PDF-ben található képek minőségének és méretének szabályozását. A képtömörítési módot a következővel állíthatja be: `setImageCompression` ban `PdfSaveOptions`.

### Hogyan frissíthetem a PDF „Utolsó nyomtatás” tulajdonságát?

A PDF „Utolsó nyomtatás” tulajdonságát a következő beállítással frissítheti: `setUpdateLastPrintedProperty` hogy `true` ban `PdfSaveOptions`Ez a PDF metaadataiban az utolsó nyomtatás dátumát fogja tükrözni.

### Hogyan javíthatom a képminőséget PDF-be konvertáláskor?

A képminőség javításához engedélyezze a képinterpolációt a következő beállítással: `setInterpolateImages` hogy `true` ban `PdfSaveOptions`Ez simább és jobb minőségű képeket eredményez a PDF-ben.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}