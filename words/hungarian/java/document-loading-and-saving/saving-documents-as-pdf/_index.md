---
title: Dokumentumok mentése PDF formátumban az Aspose.Words for Java programban
linktitle: Dokumentumok mentése PDF formátumban
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan menthet Word dokumentumokat PDF formátumban az Aspose.Words for Java használatával. Testreszabhatja a betűtípusokat, a tulajdonságokat és a képminőséget. Átfogó útmutató a PDF konvertáláshoz.
weight: 22
url: /hu/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése PDF formátumban az Aspose.Words for Java programban


## Bevezetés a dokumentumok PDF formátumban történő mentésébe az Aspose.Words for Java programban

Ebben a lépésenkénti útmutatóban megvizsgáljuk, hogyan menthet el dokumentumokat PDF formátumban az Aspose.Words for Java használatával. Kitérünk a PDF-konverzió különböző szempontjaira, és kódpéldákat adunk a folyamat megkönnyítése érdekében.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

- Java Development Kit (JDK) telepítve a rendszerére.
-  Aspose.Words for Java könyvtár. Letöltheti innen[itt](https://releases.aspose.com/words/java/).

## Dokumentum konvertálása PDF-be

Word-dokumentum PDF-be konvertálásához használhatja a következő kódrészletet:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Cserélje ki`"input.docx"` a Word-dokumentum elérési útjával és`"output.pdf"` a kívánt kimeneti PDF fájl elérési útjával.

## A PDF mentési opciók vezérlése

 Különféle PDF mentési beállításokat vezérelhet a`PdfSaveOptions` osztály. Például a következőképpen állíthatja be a PDF-dokumentum megjelenítési címét:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Betűtípusok beágyazása PDF-be

Betűtípusok beágyazásához a létrehozott PDF-be használja a következő kódot:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## dokumentum tulajdonságainak testreszabása

Testreszabhatja a dokumentum tulajdonságait a létrehozott PDF-ben. Például:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Dokumentumstruktúra exportálása

 A dokumentumstruktúra exportálásához állítsa be a`exportDocumentStructure` opciót`true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Képtömörítés

A képtömörítést a következő kóddal szabályozhatja:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Az utolsó nyomtatott tulajdonság frissítése

A PDF-fájl „Utolsó nyomtatása” tulajdonságának frissítéséhez használja:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## DML 3D effektusok megjelenítése

A DML 3D effektusok speciális megjelenítéséhez állítsa be a renderelési módot:

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

Az Aspose.Words for Java átfogó lehetőségeket biztosít Word dokumentumok PDF formátumba konvertálásához, rugalmas és testreszabási lehetőségekkel. A PDF-kimenet különféle aspektusait szabályozhatja, beleértve a betűtípusokat, a dokumentum tulajdonságait, a képtömörítést és még sok mást.

## GYIK

### Hogyan konvertálhatok Word-dokumentumot PDF-be az Aspose.Words for Java használatával?

Word-dokumentum PDF-be konvertálásához használja a következő kódot:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Cserélje ki`"input.docx"` a Word-dokumentum elérési útjával és`"output.pdf"` a kívánt kimeneti PDF fájl elérési útjával.

### Beágyazhatok betűtípusokat az Aspose.Words for Java által generált PDF-be?

 Igen, beágyazhat betűtípusokat a PDF-be a`setEmbedFullFonts` opciót`true` be`PdfSaveOptions`. Íme egy példa:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Hogyan szabhatom testre a dokumentum tulajdonságait a generált PDF-ben?

 Testreszabhatja a PDF dokumentum tulajdonságait a`setCustomPropertiesExport` opció be`PdfSaveOptions`. Például:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Mi a célja a képtömörítésnek az Aspose.Words for Java programban?

 A képtömörítés lehetővé teszi a létrehozott PDF-ben lévő képek minőségének és méretének szabályozását. A képtömörítési módot a segítségével állíthatja be`setImageCompression` be`PdfSaveOptions`.

### Hogyan frissíthetem az "Utoljára nyomtatott" tulajdonságot a PDF-ben?

 Beállítással frissítheti az "Utoljára nyomtatott" tulajdonságot a PDF-ben`setUpdateLastPrintedProperty` hogy`true` be`PdfSaveOptions`. Ez tükrözi az utolsó nyomtatás dátumát a PDF metaadatokban.

### Hogyan javíthatom a képminőséget PDF-be konvertálva?

 A képminőség javítása érdekében beállítással engedélyezze a képinterpolációt`setInterpolateImages` hogy`true` be`PdfSaveOptions`. Ez simább és jobb minőségű képeket eredményez a PDF-ben.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
