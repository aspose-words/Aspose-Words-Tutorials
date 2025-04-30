---
"description": "Optimera dokumenthanteringen med Aspose.Words för Java. Lär dig arbeta med dokumentegenskaper, lägga till anpassade metadata och mer i den här omfattande handledningen."
"linktitle": "Använda dokumentegenskaper"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda dokumentegenskaper i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda dokumentegenskaper i Aspose.Words för Java


## Introduktion till dokumentegenskaper

Dokumentegenskaper är en viktig del av alla dokument. De ger ytterligare information om själva dokumentet, såsom titel, författare, ämne, nyckelord och mer. I Aspose.Words för Java kan du manipulera både inbyggda och anpassade dokumentegenskaper.

## Uppräkning av dokumentegenskaper

### Inbyggda egenskaper

För att hämta och arbeta med inbyggda dokumentegenskaper kan du använda följande kodavsnitt:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Den här koden visar dokumentets namn och inbyggda egenskaper, inklusive egenskaper som "Titel", "Författare" och "Nyckelord".

### Anpassade egenskaper

För att arbeta med anpassade dokumentegenskaper kan du använda följande kodavsnitt:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Det här kodavsnittet visar hur man lägger till anpassade dokumentegenskaper, inklusive ett booleskt värde, en sträng, ett datum, ett revisionsnummer och ett numeriskt värde.

## Ta bort dokumentegenskaper

För att ta bort specifika dokumentegenskaper kan du använda följande kod:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Den här koden tar bort den anpassade egenskapen "Auktoriserat datum" från dokumentet.

## Konfigurera länk till innehåll

I vissa fall kanske du vill skapa länkar i ditt dokument. Så här gör du:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Lägg till länkad till innehållsegenskap.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Det här kodavsnittet visar hur du skapar ett bokmärke i ditt dokument och lägger till en anpassad dokumentegenskap som länkar till det bokmärket.

## Konvertera mellan måttenheter

I Aspose.Words för Java kan du enkelt konvertera måttenheter. Här är ett exempel på hur du gör det:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Ange marginaler i tum.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Det här kodavsnittet anger olika marginaler och avstånd i tum genom att konvertera dem till punkter.

## Använda kontrolltecken

Kontrolltecken kan vara användbara när man hanterar text. Så här ersätter du ett kontrolltecken i din text:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Ersätt kontrolltecknet "\r" med "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

I det här exemplet ersätter vi vagnreturen (`\r`) med en vagnretur följt av en radmatning (`\r\n`).

## Slutsats

Dokumentegenskaper spelar en viktig roll för att hantera och organisera dina dokument effektivt i Aspose.Words för Java. Oavsett om du arbetar med inbyggda egenskaper, anpassade egenskaper eller använder kontrolltecken, har du en rad verktyg till ditt förfogande för att förbättra dina dokumenthanteringsfunktioner.

## Vanliga frågor

### Hur får jag tillgång till inbyggda dokumentegenskaper?

För att komma åt inbyggda dokumentegenskaper i Aspose.Words för Java kan du använda `getBuiltInDocumentProperties` metod på `Document` objekt. Den här metoden returnerar en samling inbyggda egenskaper som du kan iterera igenom.

### Kan jag lägga till anpassade dokumentegenskaper i ett dokument?

Ja, du kan lägga till anpassade dokumentegenskaper till ett dokument med hjälp av `CustomDocumentProperties` samling. Du kan definiera anpassade egenskaper med olika datatyper, inklusive strängar, booleska värden, datum och numeriska värden.

### Hur kan jag ta bort en specifik anpassad dokumentegenskap?

För att ta bort en specifik anpassad dokumentegenskap kan du använda `remove` metod på `CustomDocumentProperties` samlingen och skicka namnet på den egenskap du vill ta bort som en parameter.

### Vad är syftet med att länka till innehåll i ett dokument?

Genom att länka till innehåll i ett dokument kan du skapa dynamiska referenser till specifika delar av dokumentet. Detta kan vara användbart för att skapa interaktiva dokument eller korsreferenser mellan avsnitt.

### Hur kan jag konvertera mellan olika måttenheter i Aspose.Words för Java?

Du kan konvertera mellan olika måttenheter i Aspose.Words för Java genom att använda `ConvertUtil` klass. Den tillhandahåller metoder för att konvertera enheter som tum till punkter, punkter till centimeter och mer.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}