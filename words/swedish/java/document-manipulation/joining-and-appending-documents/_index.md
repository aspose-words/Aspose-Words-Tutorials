---
"description": "Lär dig hur du enkelt sammanfogar och lägger till dokument med Aspose.Words för Java. Bevara formatering, hantera sidhuvuden, sidfot och mer."
"linktitle": "Sammanfoga och lägga till dokument"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Koppla ihop och lägga till dokument i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Koppla ihop och lägga till dokument i Aspose.Words för Java


## Introduktion till att sammanfoga och lägga till dokument i Aspose.Words för Java

I den här handledningen utforskar vi hur man sammanfogar och lägger till dokument med hjälp av Aspose.Words för Java-biblioteket. Du lär dig hur du sömlöst sammanfogar flera dokument samtidigt som du bevarar formatering och struktur.

## Förkunskapskrav

Innan vi börjar, se till att du har Aspose.Words för Java API konfigurerat i ditt Java-projekt.

## Alternativ för dokumentkoppling

### Enkel tillägg

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
convertNumPageFieldsToPageRef(dstDoc); // Konvertera NUMPAGES-fält
dstDoc.updatePageLayout(); // Uppdatera sidlayouten för korrekt numrering
```

## Hantera olika sidinställningar

När du lägger till dokument med olika sidinställningar:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Se till att inställningarna för sidformat matchar måldokumentet
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

## Behålla källnumrering

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

## Hantera sidhuvuden och sidfot

### Länka sidhuvuden och sidfot

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Ta bort länkar mellan sidhuvuden och sidfot

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Slutsats

Aspose.Words för Java erbjuder flexibla och kraftfulla verktyg för att sammanfoga och lägga till dokument, oavsett om du behöver underhålla formatering, hantera olika sidinställningar eller hantera sidhuvuden och sidfötter. Experimentera med dessa tekniker för att möta dina specifika dokumentbehandlingsbehov.

## Vanliga frågor

### Hur kan jag sammanfoga dokument med olika stilar sömlöst?

För att sammanfoga dokument med olika stilar, använd `ImportFormatMode.USE_DESTINATION_STYLES` när man lägger till.

### Kan jag behålla sidnumreringen när jag lägger till dokument?

Ja, du kan bevara sidnumreringen genom att använda `convertNumPageFieldsToPageRef` metod och uppdatering av sidlayouten.

### Vad är smart stilbeteende?

Smart stilbeteende hjälper till att bibehålla konsekventa stilar när du lägger till dokument. Använd det med `ImportFormatOptions` för bättre resultat.

### Hur kan jag hantera textrutor när jag lägger till dokument?

Uppsättning `importFormatOptions.setIgnoreTextBoxes(false)` att inkludera textrutor vid tillägg.

### Vad händer om jag vill länka/avlänka sidhuvuden och sidfot mellan dokument?

Du kan länka sidhuvuden och sidfot med `linkToPrevious(true)` eller koppla bort dem från `linkToPrevious(false)` efter behov.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}