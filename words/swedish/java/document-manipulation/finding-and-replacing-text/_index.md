---
"description": "Lär dig hur du hittar och ersätter text i Word-dokument med Aspose.Words för Java. Steg-för-steg-guide med kodexempel. Förbättra dina kunskaper i hantering av Java-dokument."
"linktitle": "Hitta och ersätta text"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Hitta och ersätta text i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/finding-and-replacing-text/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hitta och ersätta text i Aspose.Words för Java


## Introduktion till att hitta och ersätta text i Aspose.Words för Java

Aspose.Words för Java är ett kraftfullt Java API som låter dig arbeta med Word-dokument programmatiskt. En av de vanligaste uppgifterna när man hanterar Word-dokument är att hitta och ersätta text. Oavsett om du behöver uppdatera platshållare i mallar eller utföra mer komplexa textmanipulationer kan Aspose.Words för Java hjälpa dig att uppnå dina mål effektivt.

## Förkunskapskrav

Innan vi går in på detaljerna kring att hitta och ersätta text, se till att du har följande förutsättningar på plats:

- Java-utvecklingsmiljö
- Aspose.Words för Java-biblioteket
- Ett exempel på ett Word-dokument att arbeta med

Du kan ladda ner Aspose.Words för Java-biblioteket från [här](https://releases.aspose.com/words/java/).

## Hitta och ersätta enkel text

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en dokumentbyggare
DocumentBuilder builder = new DocumentBuilder(doc);

// Hitta och ersätt text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet laddar vi ett Word-dokument, skapar ett `DocumentBuilder`, och använd `replace` metod för att hitta och ersätta "gammal-text" med "ny-text" i dokumentet.

## Använda reguljära uttryck

Reguljära uttryck ger kraftfulla mönstermatchningsfunktioner för textsökning och -ersättning. Aspose.Words för Java stöder reguljära uttryck för mer avancerade sök- och ersättningsoperationer.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en dokumentbyggare
DocumentBuilder builder = new DocumentBuilder(doc);

// Använd reguljära uttryck för att söka efter och ersätta text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet använder vi ett reguljärt uttrycksmönster för att söka efter och ersätta text i dokumentet.

## Ignorera text inuti fält

Du kan konfigurera Aspose.Words så att text i fält ignoreras när du utför sök- och ersättningsåtgärder.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och sätt IgnoreFields till true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta är användbart när du vill undanta text inuti fält, till exempel kopplingsfält, från att ersättas.

## Ignorera text inuti Ta bort revisioner

Du kan konfigurera Aspose.Words så att text i borttagningsversioner ignoreras under sök- och ersättningsåtgärder.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och sätt IgnoreDeleted till true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utesluta text som har markerats för borttagning i spårade ändringar från att ersättas.

## Ignorera text inuti infogade revisioner

Du kan konfigurera Aspose.Words så att text i infogningsrevisioner ignoreras under sök- och ersättningsåtgärder.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och sätt IgnoreInserted till true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utesluta text som har markerats som infogad i spårade ändringar från att ersättas.

## Ersätta text med HTML

Du kan använda Aspose.Words för Java för att ersätta text med HTML-innehåll.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans med ett anpassat ersättningsanrop
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Använd alternativ när du ersätter text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet använder vi en anpassad `ReplaceWithHtmlEvaluator` för att ersätta text med HTML-innehåll.

## Ersätta text i sidhuvuden och sidfot

Du kan söka efter och ersätta text i sidhuvuden och sidfoten i ditt Word-dokument.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Hämta samlingen av sidhuvuden och sidfot
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Välj den typ av sidhuvud eller sidfot du vill ersätta text med (t.ex. HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Skapa en FindReplaceOptions-instans och tillämpa den på sidfotens intervall
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utföra textersättningar specifikt i sidhuvuden och sidfot.

## Visar ändringar för sidhuvud- och sidfotsordning

Du kan använda Aspose.Words för att visa ändringar för sidhuvud- och sidfotsordning i ditt dokument.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Hämta det första avsnittet
Section firstPageSection = doc.getFirstSection();

// Skapa en FindReplaceOptions-instans och tillämpa den på dokumentets intervall
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Ersätt text som påverkar ordningen för sidhuvud och sidfot
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan visualisera ändringar relaterade till sidhuvud- och sidfotsordning i ditt dokument.

## Ersätta text med fält

Du kan ersätta text med fält med hjälp av Aspose.Words för Java.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ange ett anpassat ersättningsanrop för fält
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Använd alternativ när du ersätter text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet ersätter vi text med fält och anger fälttypen (t.ex. `FieldType.FIELD_MERGE_FIELD`).

## Ersätta med en utvärderare

Du kan använda en anpassad utvärderare för att dynamiskt bestämma ersättningstexten.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och ange en anpassad ersättningsanropsfunktion
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Använd alternativ när du ersätter text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet använder vi en anpassad utvärderare (`MyReplaceEvaluator`) för att ersätta text.

## Ersätta med Regex

Aspose.Words för Java låter dig ersätta text med reguljära uttryck.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Använd reguljära uttryck för att söka efter och ersätta text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

I det här exemplet använder vi ett reguljärt uttrycksmönster för att söka efter och ersätta text i dokumentet.

## Igenkänning och substitutioner inom ersättningsmönster

Du kan känna igen och göra substitutioner inom ersättningsmönster med hjälp av Aspose.Words för Java.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans med UseSubstitutions inställt på sant
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Använd alternativ när du ersätter text med ett mönster
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utföra substitutioner inom ersättningsmönstren för mer avancerade ersättningar.

## Ersätta med en sträng

Du kan ersätta text med en enkel sträng med hjälp av Aspose.Words för Java.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Ersätt text med en sträng
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

det här exemplet ersätter vi "text-att-ersätta" med "new-string" i dokumentet.

## Använda äldre order

Du kan använda äldre ordning när du utför sök- och ersättningsåtgärder.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Skapa en FindReplaceOptions-instans och sätt UseLegacyOrder till true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Använd alternativ när du ersätter text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan använda äldre ordning för sök- och ersättningsåtgärder.

## Ersätta text i en tabell

Du kan söka efter och ersätta text i tabeller i ditt Word-dokument.

```java
// Ladda dokumentet
Document doc = new Document("your-document.docx");

// Hämta en specifik tabell (t.ex. den första tabellen)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Använd FindReplaceOptions för att ersätta text i tabellen
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Spara det ändrade dokumentet
doc.save("modified-document.docx");
```

Detta gör att du kan utföra textersättningar specifikt inom tabeller.

## Slutsats

Aspose.Words för Java erbjuder omfattande funktioner för att söka efter och ersätta text i Word-dokument. Oavsett om du behöver utföra enkla textersättningar eller mer avancerade operationer med reguljära uttryck, fältmanipulationer eller anpassade utvärderare, har Aspose.Words för Java det du behöver. Se till att utforska den omfattande dokumentationen och exemplen som Aspose tillhandahåller för att utnyttja den fulla potentialen hos detta kraftfulla Java-bibliotek.

## Vanliga frågor

### Hur laddar jag ner Aspose.Words för Java?

Du kan ladda ner Aspose.Words för Java från webbplatsen genom att besöka [den här länken](https://releases.aspose.com/words/java/).

### Kan jag använda reguljära uttryck för textersättning?

Ja, du kan använda reguljära uttryck för textersättning i Aspose.Words för Java. Detta gör att du kan utföra mer avancerade och flexibla sök- och ersättningsoperationer.

### Hur kan jag ignorera text i fält vid ersättning?

För att ignorera text inuti fält under ersättning kan du ställa in `IgnoreFields` egendomen tillhörande `FindReplaceOptions` till `true`Detta säkerställer att text i fält, till exempel kopplingsfält, exkluderas från ersättningen.

### Kan jag ersätta text i sidhuvuden och sidfoten?

Ja, du kan ersätta text i sidhuvuden och sidfoten i ditt Word-dokument. Gå bara till lämplig sidhuvud eller sidfot och använd `replace` metod med önskad `FindReplaceOptions`.

### Vad är alternativet UseLegacyOrder till för?

De `UseLegacyOrder` alternativ i `FindReplaceOptions` låter dig använda äldre ordning när du utför sök- och ersättningsåtgärder. Detta kan vara användbart i vissa scenarier där äldre ordningsföljder önskas.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}