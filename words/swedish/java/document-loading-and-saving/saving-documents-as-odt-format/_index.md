---
"description": "Lär dig hur du sparar dokument i ODT-format med Aspose.Words för Java. Säkerställ kompatibilitet med Office-paket med öppen källkod."
"linktitle": "Spara dokument som ODT-format"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Spara dokument som ODT-format i Aspose.Words för Java"
"url": "/sv/java/document-loading-and-saving/saving-documents-as-odt-format/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som ODT-format i Aspose.Words för Java


## Introduktion till att spara dokument som ODT-format i Aspose.Words för Java

I den här artikeln ska vi utforska hur man sparar dokument i ODT-format (Open Document Text) med hjälp av Aspose.Words för Java. ODT är ett populärt öppet standarddokumentformat som används av olika kontorspaket, inklusive OpenOffice och LibreOffice. Genom att spara dokument i ODT-format kan du säkerställa kompatibilitet med dessa programpaket.

## Förkunskapskrav

Innan vi börjar, se till att du har följande förutsättningar på plats:

1. Java-utvecklingsmiljö: Se till att du har Java Development Kit (JDK) installerat på ditt system.

2. Aspose.Words för Java: Ladda ner och installera Aspose.Words för Java-biblioteket. Du hittar nedladdningslänken. [här](https://releases.aspose.com/words/java/).

3. Exempeldokument: Ha ett exempeldokument i Word (t.ex. "Document.docx") som du vill konvertera till ODT-format.

## Steg 1: Ladda dokumentet

Låt oss först ladda Word-dokumentet med Aspose.Words för Java:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

Här, `"Your Directory Path"` ska peka till katalogen där ditt dokument finns.

## Steg 2: Ange ODT-sparalternativ

För att spara dokumentet som ODT måste vi ange ODT-sparalternativ. Dessutom kan vi ställa in måttenheten för dokumentet. Open Office använder centimeter, medan MS Office använder tum. Vi ställer in den till tum:

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## Steg 3: Spara dokumentet

Nu är det dags att spara dokumentet i ODT-format:

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Här, `"Your Directory Path"` ska peka på katalogen där du vill spara den konverterade ODT-filen.

## Komplett källkod för att spara dokument som ODT-format i Aspose.Words för Java

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
// Open Office använder centimeter när man anger längder, bredder och annan mätbar formatering.
// och innehållsegenskaper i dokument medan MS Office använder tum.
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## Slutsats

den här artikeln har vi lärt oss hur man sparar dokument i ODT-format med hjälp av Aspose.Words för Java. Detta kan vara särskilt användbart när du behöver säkerställa kompatibilitet med kontorspaket med öppen källkod som OpenOffice och LibreOffice.

## Vanliga frågor

### Hur kan jag ladda ner Aspose.Words för Java?

Du kan ladda ner Aspose.Words för Java från Asposes webbplats. Besök [den här länken](https://releases.aspose.com/words/java/) för att komma åt nedladdningssidan.

### Vad är fördelen med att spara dokument i ODT-format?

Att spara dokument i ODT-format säkerställer kompatibilitet med kontorspaket med öppen källkod som OpenOffice och LibreOffice, vilket gör det enklare för användare av dessa programpaket att komma åt och redigera dina dokument.

### Behöver jag ange måttenhet när jag sparar i ODT-format?

Ja, det är en bra idé att ange måttenheten. Open Office använder centimeter som standard, så att ställa in den på tum säkerställer enhetlig formatering.

### Kan jag konvertera flera dokument till ODT-format i en batchprocess?

Ja, du kan automatisera konverteringen av flera dokument till ODT-format med Aspose.Words för Java genom att iterera igenom dina dokumentfiler och tillämpa konverteringsprocessen.

### Är Aspose.Words för Java kompatibelt med de senaste Java-versionerna?

Aspose.Words för Java uppdateras regelbundet för att stödja de senaste Java-versionerna, vilket säkerställer kompatibilitet och prestandaförbättringar. Se till att kontrollera systemkraven i dokumentationen för den senaste informationen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}