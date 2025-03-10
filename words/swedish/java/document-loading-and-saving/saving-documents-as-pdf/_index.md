---
title: Spara dokument som PDF i Aspose.Words för Java
linktitle: Spara dokument som PDF
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du sparar Word-dokument som PDF med Aspose.Words för Java. Anpassa teckensnitt, egenskaper och bildkvalitet. En omfattande guide för PDF-konvertering.
weight: 22
url: /sv/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som PDF i Aspose.Words för Java


## Introduktion till att spara dokument som PDF i Aspose.Words för Java

I denna steg-för-steg-guide kommer vi att utforska hur man sparar dokument som PDF med Aspose.Words för Java. Vi kommer att täcka olika aspekter av PDF-konvertering och ge kodexempel för att göra processen enklare.

## Förutsättningar

Innan vi börjar, se till att du har följande förutsättningar på plats:

- Java Development Kit (JDK) installerat på ditt system.
-  Aspose.Words för Java-bibliotek. Du kan ladda ner den från[här](https://releases.aspose.com/words/java/).

## Konvertera ett dokument till PDF

För att konvertera ett Word-dokument till PDF kan du använda följande kodavsnitt:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Ersätta`"input.docx"` med sökvägen till ditt Word-dokument och`"output.pdf"` med önskad sökväg till PDF-filen.

## Styra PDF-sparalternativ

 Du kan styra olika PDF-sparalternativ med hjälp av`PdfSaveOptions` klass. Du kan till exempel ställa in visningstiteln för PDF-dokumentet enligt följande:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Bädda in teckensnitt i PDF

För att bädda in teckensnitt i den genererade PDF-filen, använd följande kod:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Anpassa dokumentegenskaper

Du kan anpassa dokumentegenskaperna i den genererade PDF-filen. Till exempel:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Exporterar dokumentstruktur

 För att exportera dokumentstrukturen, ställ in`exportDocumentStructure` möjlighet att`true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Bildkomprimering

Du kan styra bildkomprimeringen med följande kod:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Uppdaterar senast utskrivna egenskap

För att uppdatera egenskapen "Senast utskriven" i PDF:en, använd:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Rendering av DML 3D-effekter

För avancerad rendering av DML 3D-effekter, ställ in renderingsläget:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolera bilder

Du kan aktivera bildinterpolation för att förbättra bildkvaliteten:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Slutsats

Aspose.Words för Java tillhandahåller omfattande funktioner för att konvertera Word-dokument till PDF-format med flexibilitet och anpassningsalternativ. Du kan kontrollera olika aspekter av PDF-utdata, inklusive teckensnitt, dokumentegenskaper, bildkomprimering och mer.

## FAQ's

### Hur konverterar jag ett Word-dokument till PDF med Aspose.Words för Java?

För att konvertera ett Word-dokument till PDF, använd följande kod:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Ersätta`"input.docx"` med sökvägen till ditt Word-dokument och`"output.pdf"` med önskad sökväg till PDF-filen.

### Kan jag bädda in typsnitt i PDF-filen som genereras av Aspose.Words för Java?

 Ja, du kan bädda iteckensnitt i PDF:en genom att ställa in`setEmbedFullFonts` möjlighet att`true` in `PdfSaveOptions`. Här är ett exempel:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Hur kan jag anpassa dokumentegenskaper i den genererade PDF-filen?

 Du kan anpassa dokumentegenskaperna i PDF-filen med hjälp av`setCustomPropertiesExport` alternativ i`PdfSaveOptions`. Till exempel:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Vad är syftet med bildkomprimering i Aspose.Words för Java?

 Bildkomprimering låter dig kontrollera kvaliteten och storleken på bilder i den genererade PDF-filen. Du kan ställa ibildkomprimeringsläget med`setImageCompression` in `PdfSaveOptions`.

### Hur uppdaterar jag egenskapen "Senast utskriven" i PDF-filen?

 Du kan uppdatera egenskapen "Senast utskriven" i PDF-filen genom att ställa in`setUpdateLastPrintedProperty` till`true` i`PdfSaveOptions`. Detta kommer att återspegla det senast utskrivna datumet i PDF-metadata.

### Hur kan jag förbättra bildkvaliteten när jag konverterar till PDF?

 För att förbättra bildkvaliteten, aktivera bildinterpolering genom inställning`setInterpolateImages` till`true` i`PdfSaveOptions`. Detta kommer att resultera i jämnare bilder av högre kvalitet i PDF-filen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
