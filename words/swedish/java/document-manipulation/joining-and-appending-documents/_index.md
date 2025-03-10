---
title: Sammanfoga och lägga till dokument i Aspose.Words för Java
linktitle: Sammanfoga och bifoga dokument
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du går med i och lägger till dokument utan ansträngning med Aspose.Words för Java. Bevara formatering, hantera sidhuvuden, sidfötter och mer.
weight: 30
url: /sv/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sammanfoga och lägga till dokument i Aspose.Words för Java


## Introduktion till att sammanfoga och lägga till dokument i Aspose.Words för Java

I den här handledningen kommer vi att undersöka hur du går med i och lägger till dokument med Aspose.Words för Java-biblioteket. Du lär dig hur du sömlöst sammanfogar flera dokument samtidigt som du bevarar formatering och struktur.

## Förutsättningar

Innan vi börjar, se till att du har Aspose.Words för Java API inställt i ditt Java-projekt.

## Alternativ för dokumentkoppling

### Enkelt Bifoga

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Lägg till med importformatalternativ

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Lägg till i tomt dokument

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Lägg till med sidnummerkonvertering

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Konvertera NUMPAGES fält
dstDoc.updatePageLayout(); // Uppdatera sidlayout för korrekt numrering
```

## Hantera olika sidinställningar

När du lägger till dokument med olika sidinställningar:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Se till att sidinställningarna matchar måldokumentet
```

## Sammanfoga dokument med olika stilar

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Smart stilbeteende

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Infoga dokument med DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Att behålla källnumrering

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Hantera textrutor

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Hantera sidhuvuden och sidfötter

### Länka sidhuvuden och sidfötter

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Avlänkning av sidhuvuden och sidfötter

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Slutsats

Aspose.Words för Java tillhandahåller flexibla och kraftfulla verktyg för att sammanfoga och lägga till dokument, oavsett om du behöver underhålla formatering, hantera olika sidinställningar eller hantera sidhuvuden och sidfötter. Experimentera med dessa tekniker för att möta dina specifika dokumentbehandlingsbehov.

## FAQ's

### Hur kan jag sammanfoga dokument med olika stilar sömlöst?

 För att sammanfoga dokument med olika stilar, använd`ImportFormatMode.USE_DESTINATION_STYLES` vid tillägg.

### Kan jag behålla sidnumreringen när jag lägger till dokument?

 Ja, du kan bevara sidnumreringen genom att använda`convertNumPageFieldsToPageRef` metod och uppdatering av sidlayouten.

### Vad är Smart Style Beteende?

 Smart Style Behavior hjälper till att upprätthålla konsekventa stilar när du lägger till dokument. Använd den med`ImportFormatOptions` för bättre resultat.

### Hur kan jag hantera textrutor när jag lägger till dokument?

Uppsättning`importFormatOptions.setIgnoreTextBoxes(false)` att inkludera textrutor när du lägger till.

### Vad händer om jag vill länka/ta bort länkhuvuden och sidfötter mellan dokument?

 Du kan länka sidhuvuden och sidfötter med`linkToPrevious(true)` eller ta bort länken till dem`linkToPrevious(false)` efter behov.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
