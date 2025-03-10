---
title: Hitta och ersätta text i Aspose.Words för Java
linktitle: Hitta och ersätta text
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du hittar och ersätter text i Word-dokument med Aspose.Words för Java. Steg-för-steg guide med kodexempel. Förbättra dina färdigheter i Java-dokumenthantering.
weight: 15
url: /sv/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hitta och ersätta text i Aspose.Words för Java


## Introduktion till att hitta och ersätta text i Aspose.Words för Java

Aspose.Words för Java är ett kraftfullt Java API som låter dig arbeta med Word-dokument programmatiskt. En av de vanligaste uppgifterna när man hanterar Word-dokument är att hitta och ersätta text. Oavsett om du behöver uppdatera platshållare i mallar eller utföra mer komplexa textmanipulationer kan Aspose.Words för Java hjälpa dig att nå dina mål effektivt.

## Förutsättningar

Innan vi dyker in i detaljerna för att hitta och ersätta text, se till att du har följande förutsättningar på plats:

- Java utvecklingsmiljö
- Aspose.Words för Java-bibliotek
- Ett exempel på Word-dokument att arbeta med

 Du kan ladda ner Aspose.Words for Java-biblioteket från[här](https://releases.aspose.com/words/java/).

## Hitta och ersätta enkel text

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Hitta och ersätt text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

 I det här exemplet laddar vi ett Word-dokument, skapar en`DocumentBuilder` , och använd`replace` metod för att hitta och ersätta "gammal text" med "ny text" i dokumentet.

## Använda reguljära uttryck

Reguljära uttryck ger kraftfulla mönstermatchningsmöjligheter för textsökning och ersättning. Aspose.Words för Java stöder reguljära uttryck för mer avancerade sök- och ersätt-operationer.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Använd reguljära uttryck för att hitta och ersätta text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet använder vi ett reguljärt uttrycksmönster för att hitta och ersätta text i dokumentet.

## Ignorera text i fält

Du kan konfigurera Aspose.Words att ignorera text i fält när du utför sök- och ersätt-operationer.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ställ in IgnoreFields på sant
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta är användbart när du vill utesluta att text i fält, till exempel sammanslagningsfält, ersätts.

## Ignorera text inuti Ta bort versioner

Du kan konfigurera Aspose.Words att ignorera text i raderingsversioner under sök- och ersättningsoperationer.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ställ in IgnoreDeleted till true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utesluta text som har markerats för radering i spårade ändringar från att ersättas.

## Ignorera text inuti Infoga ändringar

Du kan konfigurera Aspose.Words att ignorera text i infogningsrevisioner under sök- och ersättningsoperationer.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ställ in IgnoreInserted till true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utesluta text som har markerats som infogat i spårade ändringar från att ersättas.

## Ersätta text med HTML

Du kan använda Aspose.Words för Java för att ersätta text med HTML-innehåll.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans med en anpassad ersättande återuppringning
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

 I det här exemplet använder vi en anpassad`ReplaceWithHtmlEvaluator` för att ersätta text med HTML-innehåll.

## Ersätter text i sidhuvuden och sidfötter

Du kan hitta och ersätta text i sidhuvuden och sidfötter i ditt Word-dokument.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Få samlingen av sidhuvuden och sidfötter
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Välj den typ av sidhuvud eller sidfot som du vill ersätta text i (t.ex. HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Skapa en FindReplaceOptions-instans och tillämpa den på sidfotens intervall
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utföra textersättningar specifikt i sidhuvuden och sidfötter.

## Visar ändringar för sidhuvuds- och sidfotsbeställningar

Du kan använda Aspose.Words för att visa ändringar för sidhuvuden och sidfötter i ditt dokument.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skaffa det första avsnittet
Section firstPageSection = doc.getFirstSection();

//Skapa en FindReplaceOptions-instans och tillämpa den på dokumentets intervall
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Ersätt text som påverkar ordning på sidhuvuden och sidfötter
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta låter dig visualisera ändringar relaterade till sidhuvuds- och sidfotsordningar i ditt dokument.

## Ersätter text med fält

Du kan ersätta text med fält med Aspose.Words för Java.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ställ in en anpassad ersättande återuppringning för fält
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Använd alternativ när du ersätter text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

 I det här exemplet ersätter vi text med fält och anger fälttypen (t.ex.`FieldType.FIELD_MERGE_FIELD`).

## Ersätt med en utvärderare

Du kan använda en anpassad utvärderare för att bestämma ersättningstexten dynamiskt.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ställ in en anpassad ersättande återuppringning
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Använd alternativ när du ersätter text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet använder vi en anpassad utvärderare (`MyReplaceEvaluator`) för att ersätta text.

## Ersätter med Regex

Aspose.Words för Java låter dig ersätta text med reguljära uttryck.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Använd reguljära uttryck för att hitta och ersätta text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet använder vi ett reguljärt uttrycksmönster för att hitta och ersätta text i dokumentet.

## Identifiering och ersättningar inom ersättningsmönster

Du kan känna igen och göra ersättningar inom ersättningsmönster med Aspose.Words för Java.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans med UseSubstitutions inställd på true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Använd alternativ när du ersätter text med ett mönster
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utföra ersättningar inom ersättningsmönstren för mer avancerade ersättningar.

## Byt ut med en sträng

Du kan ersätta text med en enkel sträng med Aspose.Words för Java.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Ersätt text med en sträng
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet ersätter vi "text-att-ersätta" med "ny-sträng" i dokumentet.

## Använder Legacy Order

Du kan använda äldre ordning när du utför sök- och ersättningsåtgärder.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ställ in UseLegacyOrder på true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Använd alternativ när du ersätter text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan använda äldre ordning för att hitta och ersätta operationer.

## Ersätta text i en tabell

Du kan hitta och ersätta text i tabeller i ditt Word-dokument.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skaffa en specifik tabell (t.ex. den första tabellen)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//Använd FindReplaceOptions för att ersätta text i tabellen
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utföra textersättningar specifikt inom tabeller.

## Slutsats

Aspose.Words för Java tillhandahåller omfattande möjligheter för att hitta och ersätta text i Word-dokument. Oavsett om du behöver utföra enkla textersättningar eller mer avancerade operationer med reguljära uttryck, fältmanipulationer eller anpassade utvärderare, har Aspose.Words för Java dig täckt. Se till att utforska den omfattande dokumentationen och exemplen som tillhandahålls av Aspose för att utnyttja den fulla potentialen i detta kraftfulla Java-bibliotek.

## FAQ's

### Hur laddar jag ner Aspose.Words för Java?

 Du kan ladda ner Aspose.Words för Java från webbplatsen genom att besöka[denna länk](https://releases.aspose.com/words/java/).

### Kan jag använda reguljära uttryck för textersättning?

Ja, du kan använda reguljära uttryck för textersättning i Aspose.Words för Java. Detta gör att du kan utföra mer avancerade och flexibla sök- och ersättningsoperationer.

### Hur kan jag ignorera text i fält under ersättning?

För att ignorera text i fält under ersättning, kan du ställa in`IgnoreFields` egendom av`FindReplaceOptions` till`true`. Detta säkerställer att text i fält, såsom sammanfogningsfält, utesluts från ersättningen.

### Kan jag ersätta text i sidhuvuden och sidfötter?

 Ja, du kan ersätta text i sidhuvuden och sidfötter i ditt Word-dokument. Gå bara till lämplig sidhuvud eller sidfot och använd`replace` metod med önskad`FindReplaceOptions`.

### Vad är alternativet UseLegacyOrder till för?

 De`UseLegacyOrder` alternativ i`FindReplaceOptions` låter dig använda äldre ordning när du utför sök- och ersätt-operationer. Detta kan vara användbart i vissa scenarier där äldre orderbeteende önskas.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
