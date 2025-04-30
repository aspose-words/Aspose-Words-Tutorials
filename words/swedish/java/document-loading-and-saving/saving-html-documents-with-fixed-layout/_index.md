---
"description": "Lär dig hur du sparar HTML-dokument med fast layout i Aspose.Words för Java. Följ vår steg-för-steg-guide för sömlös dokumentformatering."
"linktitle": "Spara HTML-dokument med fast layout"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Spara HTML-dokument med fast layout i Aspose.Words för Java"
"url": "/sv/java/document-loading-and-saving/saving-html-documents-with-fixed-layout/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spara HTML-dokument med fast layout i Aspose.Words för Java


## Introduktion till att spara HTML-dokument med fast layout i Aspose.Words för Java

I den här omfattande guiden guidar vi dig genom processen att spara HTML-dokument med en fast layout med Aspose.Words för Java. Med steg-för-steg-instruktioner och kodexempel lär du dig hur du gör detta smidigt. Så, låt oss dyka in direkt!

## Förkunskapskrav

Innan vi börjar, se till att du har följande förutsättningar på plats:

- Java-utvecklingsmiljö konfigurerad.
- Aspose.Words för Java-biblioteket installerat och konfigurerat.

## Steg 1: Ladda dokumentet

Först måste vi ladda dokumentet som vi vill spara i HTML-format. Så här gör du:

```java
Document doc = new Document("Your Directory Path" + "YourDocument.docx");
```

Ersätta `"YourDocument.docx"` med sökvägen till ditt Word-dokument.

## Steg 2: Konfigurera fasta HTML-sparalternativ

För att spara dokumentet med en fast layout måste vi konfigurera `HtmlFixedSaveOptions` klass. Vi ställer in `useTargetMachineFonts` egendom till `true` för att säkerställa att målmaskinens teckensnitt används i HTML-utdata:

```java
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
saveOptions.setUseTargetMachineFonts(true);
```

## Steg 3: Spara dokumentet som HTML

Nu ska vi spara dokumentet som HTML med den fasta layouten med hjälp av de tidigare konfigurerade alternativen:

```java
doc.save("Your Directory Path" + "FixedLayoutDocument.html", saveOptions);
```

Ersätta `"FixedLayoutDocument.html"` med önskat namn för din HTML-fil.

## Komplett källkod för att spara HTML-dokument med fast layout i Aspose.Words för Java

```java
        Document doc = new Document("Your Directory Path" + "Bullet points with alternative font.docx");
        HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
        {
            saveOptions.setUseTargetMachineFonts(true);
        }
        doc.save("Your Directory Path" + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
    }
```

## Slutsats

I den här handledningen har vi lärt oss hur man sparar HTML-dokument med en fast layout med hjälp av Aspose.Words för Java. Genom att följa dessa enkla steg kan du säkerställa att dina dokument har en enhetlig visuell struktur på olika plattformar.

## Vanliga frågor

### Hur kan jag konfigurera Aspose.Words för Java i mitt projekt?

Det är enkelt att installera Aspose.Words för Java. Du kan ladda ner biblioteket från [här](https://releases.aspose.com/words/java/) och följ installationsanvisningarna i dokumentationen [här](https://reference.aspose.com/words/java/).

### Finns det några licenskrav för att använda Aspose.Words för Java?

Ja, Aspose.Words för Java kräver en giltig licens för att användas i en produktionsmiljö. Du kan hämta en licens från Asposes webbplats. Mer information finns i dokumentationen.

### Kan jag anpassa HTML-utdata ytterligare?

Absolut! Aspose.Words för Java erbjuder ett brett utbud av alternativ för att anpassa HTML-utdata för att möta dina specifika krav. Du kan utforska dokumentationen för detaljerad information om anpassningsalternativ.

### Är Aspose.Words för Java kompatibelt med olika Java-versioner?

Ja, Aspose.Words för Java är kompatibelt med olika versioner av Java. Se till att du använder en kompatibel version av Aspose.Words för Java som matchar din Java-utvecklingsmiljö.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}