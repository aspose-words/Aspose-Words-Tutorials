---
"description": "Tanulja meg, hogyan illeszthet össze és fűzhet hozzá dokumentumokat könnyedén az Aspose.Words for Java segítségével. Őrizze meg a formázást, kezelje a fejléceket és lábléceket, és sok mást."
"linktitle": "Dokumentumok összekapcsolása és hozzáfűzése"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok összekapcsolása és hozzáfűzése az Aspose.Words for Java programban"
"url": "/hu/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok összekapcsolása és hozzáfűzése az Aspose.Words for Java programban


## Bevezetés a dokumentumok összekapcsolásába és hozzáfűzésébe az Aspose.Words for Java programban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan lehet dokumentumokat egyesíteni és hozzáfűzni az Aspose.Words for Java könyvtár használatával. Megtanulod, hogyan lehet zökkenőmentesen egyesíteni több dokumentumot a formázás és a szerkezet megőrzése mellett.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy az Aspose.Words for Java API be van állítva a Java projektedben.

## Dokumentum-összeillesztési lehetőségek

### Egyszerű hozzáfűzés

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Hozzáfűzés importálási formátumbeállításokkal

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Hozzáfűzés üres dokumentumhoz

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Oldalszám-átalakítással hozzáfűzés

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // NUMPAGES mező konvertálása
dstDoc.updatePageLayout(); // Oldalelrendezés frissítése a helyes számozás érdekében
```

## Különböző oldalbeállítások kezelése

Eltérő oldalbeállításokkal rendelkező dokumentumok hozzáfűzésekor:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Győződjön meg arról, hogy az oldalbeállítások megegyeznek a céldokumentummal
```

## Különböző stílusú dokumentumok összekapcsolása

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Okos stílusviselkedés

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

Az Aspose.Words for Java rugalmas és hatékony eszközöket kínál dokumentumok egyesítéséhez és hozzáfűzéséhez, legyen szó akár formázás karbantartásáról, különböző oldalbeállítások kezeléséről, vagy fejlécek és láblécek kezeléséről. Kísérletezzen ezekkel a technikákkal, hogy megfeleljen az Ön konkrét dokumentumfeldolgozási igényeinek.

## GYIK

### Hogyan tudok zökkenőmentesen összekapcsolni különböző stílusú dokumentumokat?

Különböző stílusú dokumentumok összekapcsolásához használja a `ImportFormatMode.USE_DESTINATION_STYLES` hozzáfűzéskor.

### Megőrizhetem az oldalszámozást dokumentumok hozzáfűzésekor?

Igen, megőrizheti az oldalszámozást a használatával. `convertNumPageFieldsToPageRef` metódus és az oldal elrendezésének frissítése.

### Mi az intelligens stílusviselkedés?

Az Intelligens stílusviselkedés segít az egységes stílusok megőrzésében a dokumentumok hozzáfűzésekor. Használja a következővel: `ImportFormatOptions` jobb eredmények érdekében.

### Hogyan kezelhetem a szövegdobozokat dokumentumok hozzáfűzésekor?

Készlet `importFormatOptions.setIgnoreTextBoxes(false)` szövegdobozok hozzáadása a hozzáfűzés során.

### Mi van, ha fejléceket és lábléceket szeretnék összekapcsolni/leválasztani a dokumentumok között?

Fejléceket és lábléceket összekapcsolhatsz a következőkkel: `linkToPrevious(true)` vagy válassza le őket a `linkToPrevious(false)` szükség szerint.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}