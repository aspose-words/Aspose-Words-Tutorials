---
title: Dokumentumok összekapcsolása és hozzáfűzése az Aspose.Words for Java programban
linktitle: Dokumentumok összekapcsolása és csatolása
second_title: Aspose.Words Java Document Processing API
description: Tanulja meg, hogyan lehet könnyedén összekapcsolni és csatolni dokumentumokat az Aspose.Words for Java használatával. A formázás megőrzése, a fejléc-láblécek kezelése és sok más.
weight: 30
url: /hu/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok összekapcsolása és hozzáfűzése az Aspose.Words for Java programban


## Bevezetés az Aspose.Words for Java dokumentumok összekapcsolásához és hozzáfűzéséhez

Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet dokumentumokat egyesíteni és hozzáfűzni az Aspose.Words for Java könyvtár használatával. Megtanulja, hogyan lehet több dokumentumot zökkenőmentesen egyesíteni a formázás és a szerkezet megőrzése mellett.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy az Aspose.Words for Java API be van állítva a Java projektben.

## Dokumentum csatlakozási lehetőségek

### Egyszerű hozzáfűzés

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Hozzáfűzi az importálási formátumbeállításokat

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Hozzáfűzés az üres dokumentumhoz

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Hozzáfűzés oldalszám-konverzióval

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // NUMPAGES mező konvertálása
dstDoc.updatePageLayout(); // Frissítse az oldalelrendezést a helyes számozás érdekében
```

## Különböző oldalbeállítások kezelése

Különböző oldalbeállításokkal rendelkező dokumentumok csatolásakor:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Győződjön meg arról, hogy az oldalbeállítások megfelelnek a céldokumentumnak
```

## Különböző stílusú dokumentumok összekapcsolása

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Intelligens stílusú viselkedés

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Dokumentumok beszúrása a DocumentBuilder segítségével

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Forrásszámozás megtartása

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Szövegdobozok kezelése

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Fejlécek és láblécek kezelése

### Fejlécek és láblécek összekapcsolása

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Fejlécek és láblécek szétválasztása

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Következtetés

Az Aspose.Words for Java rugalmas és hatékony eszközöket biztosít a dokumentumok egyesítéséhez és hozzáfűzéséhez, legyen szó formázásról, különböző oldalbeállítások kezeléséről vagy fejlécek és láblécek kezeléséről. Kísérletezzen ezekkel a technikákkal, hogy megfeleljen egyedi dokumentumfeldolgozási igényeinek.

## GYIK

### Hogyan lehet zökkenőmentesen összekapcsolni a különböző stílusú dokumentumokat?

 A különböző stílusú dokumentumok összekapcsolásához használja a`ImportFormatMode.USE_DESTINATION_STYLES` hozzáfűzéskor.

### Megőrizhetem az oldalszámozást dokumentumok csatolásakor?

 Igen, megőrizheti az oldalszámozást a`convertNumPageFieldsToPageRef` módszerrel és az oldalelrendezés frissítésével.

### Mi az a Smart Style viselkedés?

 A Smart Style Behavior segít megőrizni a konzisztens stílusokat a dokumentumok csatolásakor. Használd vele`ImportFormatOptions` jobb eredmények érdekében.

### Hogyan kezelhetem a szövegdobozokat dokumentumok csatolásakor?

Készlet`importFormatOptions.setIgnoreTextBoxes(false)` szövegdobozok beillesztésére a hozzáfűzés során.

### Mi a teendő, ha szeretném a fejléceket és a lábléceket összekapcsolni/leválasztani a dokumentumok között?

 A fejléceket és lábléceket összekapcsolhatja a következővel`linkToPrevious(true)` vagy megszünteti a kapcsolatukat`linkToPrevious(false)` szükség szerint.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
