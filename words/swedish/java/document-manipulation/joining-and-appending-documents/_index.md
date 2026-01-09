---
date: 2026-01-09
description: Lär dig hur du slår ihop dokument med Aspose.Words för Java samtidigt
  som du bevarar formatering, länkar sidhuvuden och sidfötter, och mer.
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: Hur man slår ihop dokument med Aspose.Words för Java
url: /sv/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hur man slår ihop dokument med Aspose.Words för Java

Att programatiskt slå ihop Word‑filer kan vara en huvudvärk—särskilt när du måste behålla stilar, sidnummer och sidhuvuden/sidfötter intakta. I den här handledningen kommer du att upptäcka **hur man slår ihop dokument** med Aspose.Words for Java‑biblioteket, steg för steg. Vi kommer att gå igenom enkla tillägg, avancerade importalternativ, hantering av olika sidinställningar och de knep du behöver för att **bevara formateringssammanfogning** resultat i en mängd olika verkliga scenarier.

## Snabba svar
- **Vad är det enklaste sättet att slå ihop Word‑dokument?** Använd `Document.appendDocument` med `ImportFormatMode.KEEP_SOURCE_FORMATTING`.  
- **Kan jag behålla de ursprungliga stilarna i varje källfil?** Ja—sätt `ImportFormatMode.USE_DESTINATION_STYLES` eller aktivera Smart Style Behavior.  
- **Hur behåller jag korrekta sidnummer efter en sammanslagning?** Konvertera `NUMPAGES`‑fält till sidreferenser och anropa `updatePageLayout()`.  
- **Följer sidhuvuden och sidfötter automatiskt?** Du kan länka eller avlänka dem med `linkToPrevious(true/false)`.  
- **Vad behöver jag innan du börjar?** Aspose.Words for Java tillagt i ditt projekt och käll‑`.docx`‑filerna redo.

## Introduktion till att gå samman och lägga till dokument i Aspose.Words for Java

I den här handledningen kommer vi att utforska hur man går samman och lägger till dokument med hjälp av Aspose.Words for Java‑biblioteket. Du kommer att lära dig hur du sömlöst slår ihop flera dokument samtidigt som du bevarar formatering och struktur.

## Förutsättningar

Innan vi börjar, se till att du har Aspose.Words for Java‑API konfigurerat i ditt Java‑projekt.

## Alternativ för dokumentsammanfogning

### Enkelt tillägg

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Tillägg med importformatalternativ

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Tillägg till tomt dokument

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Tillägg med sidnummerkonvertering

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## Hantera olika sidinställningar

När du lägger till dokument med olika sidinställningar:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## Sammanfoga dokument med olika stilar

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Smart Style Behavior

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

## Hantera sidhuvuden och sidfötter

### Länka sidhuvuden och sidfötter

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Avlänka sidhuvuden och sidfötter

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Varför detta är viktigt för “merge word documents java”‑projekt

När du behöver **merge word documents java**‑stil, är det avgörande att bevara varje fils utseende och känsla för juridiska, publicerings‑ eller rapporteringsarbetsflöden. Genom att använda teknikerna ovan säkerställer du att:
* Stilar från varje källa förblir intakta (eller förenas, beroende på ditt val).  
* Sidnumrering och sektionsbrytningar beter sig förutsägbart.  
* Sidhuvuden och sidfötter kan länkas eller hållas oberoende med en enda kodrad.  

## Vanliga fallgropar & tips

| Problem | Varför det händer | Hur man åtgärdar |
|---------|-------------------|------------------|
| Förlorad numrering efter sammanslagning | `NUMPAGES`‑fält pekar fortfarande på originalsektioner | Anropa `convertNumPageFieldsToPageRef` och `updatePageLayout()` |
| Stilkonflikt | Användning av `KEEP_SOURCE_FORMATTING` med motstridiga stilar | Byt till `USE_DESTINATION_STYLES` eller aktivera Smart Style Behavior |
| Tomma sidor visas | Olika `SectionStart`‑värden | Sätt `SectionStart.CONTINUOUS` på källsektioner innan du lägger till |

## Vanliga frågor

**Q: Hur kan jag sömlöst gå samman dokument med olika stilar?**  
A: Använd `ImportFormatMode.USE_DESTINATION_STYLES` vid tillägg, eller aktivera `SmartStyleBehavior` för smartare sammanslagning.

**Q: Kan jag bevara sidnumrering när jag lägger till dokument?**  
A: Ja, konvertera `NUMPAGES`‑fält till sidreferenser med `convertNumPageFieldsToPageRef` och anropa sedan `updatePageLayout()`.

**Q: Vad är Smart Style Behavior?**  
A: Det mappar automatiskt källstilar till destinationsstilar när det är möjligt, vilket hjälper till att behålla ett enhetligt utseende i sammanslaget innehåll.

**Q: Hur hanterar jag textrutor när jag lägger till dokument?**  
A: Sätt `importFormatOptions.setIgnoreTextBoxes(false)` så att textrutor behålls under sammanslagningen.

**Q: Vad händer om jag vill länka eller avlänka sidhuvuden och sidfötter mellan dokument?**  
A: Använd `linkToPrevious(true)` för att länka, eller `linkToPrevious(false)` för att hålla dem separata innan du anropar `appendDocument`.

## Slutsats

Aspose.Words for Java erbjuder flexibla och kraftfulla verktyg för **hur man slår ihop dokument**, oavsett om du behöver behålla exakt formatering, hantera varierande sidinställningar eller kontrollera länken för sidhuvuden/sidfötter. Experimentera med kodsnuttarna ovan för att anpassa dem till ditt specifika dokument‑bearbetningsflöde, så kommer du att kunna **slå ihop Word-dokument java**‑stil med självförtroende.

---

**Senast uppdaterad:** 2026-01-09  
**Testad med:** Aspose.Words for Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}