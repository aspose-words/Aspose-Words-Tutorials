---
title: Documenteigenschappen gebruiken in Aspose.Words voor Java
linktitle: Documenteigenschappen gebruiken
second_title: Aspose.Words Java Documentverwerkings-API
description: Optimaliseer documentbeheer met Aspose.Words voor Java. Leer werken met documenteigenschappen, voeg aangepaste metadata toe en meer in deze uitgebreide tutorial.
weight: 32
url: /nl/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Documenteigenschappen gebruiken in Aspose.Words voor Java


## Inleiding tot documenteigenschappen

Documenteigenschappen zijn een essentieel onderdeel van elk document. Ze bieden aanvullende informatie over het document zelf, zoals de titel, auteur, onderwerp, trefwoorden en meer. In Aspose.Words voor Java kunt u zowel ingebouwde als aangepaste documenteigenschappen manipuleren.

## Documenteigenschappen opsommen

### Ingebouwde eigenschappen

Om ingebouwde documenteigenschappen op te halen en ermee te werken, kunt u het volgende codefragment gebruiken:

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

Met deze code worden de naam van het document en de ingebouwde eigenschappen weergegeven, waaronder eigenschappen als 'Titel', 'Auteur' en 'Trefwoorden'.

### Aangepaste eigenschappen

Om met aangepaste documenteigenschappen te werken, kunt u het volgende codefragment gebruiken:

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

Dit codefragment laat zien hoe u aangepaste documenteigenschappen toevoegt, waaronder een Booleaanse waarde, een tekenreeks, een datum, een revisienummer en een numerieke waarde.

## Documenteigenschappen verwijderen

Om specifieke documenteigenschappen te verwijderen, kunt u de volgende code gebruiken:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Met deze code wordt de aangepaste eigenschap 'Geautoriseerde datum' uit het document verwijderd.

## Link naar inhoud configureren

In sommige gevallen wilt u wellicht links in uw document maken. Dit is hoe u dat kunt doen:

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

    // Voeg gekoppelde inhoudseigenschap toe.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Dit codefragment laat zien hoe u een bladwijzer in uw document maakt en een aangepaste documenteigenschap toevoegt die naar die bladwijzer linkt.

## Converteren tussen meeteenheden

In Aspose.Words voor Java kunt u eenvoudig meeteenheden converteren. Hier is een voorbeeld van hoe u dat doet:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Stel de marges in inches in.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Met dit codefragment worden verschillende marges en afstanden in inches ingesteld door ze om te zetten in punten.

## Controlekarakters gebruiken

Control characters kunnen handig zijn bij het werken met tekst. Zo vervangt u een control character in uw tekst:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Vervang het besturingsteken "\r" door "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

In dit voorbeeld vervangen we de wagenretour (`\r`) met een wagenretour gevolgd door een regelterugloop (`\r\n`).

## Conclusie

Documenteigenschappen spelen een belangrijke rol bij het effectief beheren en organiseren van uw documenten in Aspose.Words voor Java. Of u nu werkt met ingebouwde eigenschappen, aangepaste eigenschappen of controlekarakters gebruikt, u hebt een scala aan hulpmiddelen tot uw beschikking om uw documentbeheermogelijkheden te verbeteren.

## Veelgestelde vragen

### Hoe krijg ik toegang tot ingebouwde documenteigenschappen?

 Om toegang te krijgen tot ingebouwde documenteigenschappen in Aspose.Words voor Java, kunt u de`getBuiltInDocumentProperties` methode op de`Document` object. Deze methode retourneert een verzameling ingebouwde eigenschappen waar u doorheen kunt itereren.

### Kan ik aangepaste documenteigenschappen aan een document toevoegen?

 Ja, u kunt aangepaste documenteigenschappen aan een document toevoegen met behulp van de`CustomDocumentProperties` verzameling. U kunt aangepaste eigenschappen definiëren met verschillende gegevenstypen, waaronder strings, booleans, datums en numerieke waarden.

### Hoe kan ik een specifieke aangepaste documenteigenschap verwijderen?

 Om een specifieke aangepaste documenteigenschap te verwijderen, kunt u de`remove` methode op de`CustomDocumentProperties`verzameling, waarbij u de naam van de eigenschap die u wilt verwijderen als parameter doorgeeft.

### Wat is het doel van het linken naar inhoud binnen een document?

Door te linken naar content binnen een document kunt u dynamische verwijzingen naar specifieke delen van het document maken. Dit kan handig zijn voor het maken van interactieve documenten of kruisverwijzingen tussen secties.

### Hoe kan ik in Aspose.Words voor Java converteren tussen verschillende maateenheden?

 U kunt in Aspose.Words voor Java tussen verschillende meeteenheden converteren met behulp van de`ConvertUtil` klasse. Het biedt methoden om eenheden zoals inches naar punten, punten naar centimeters en meer te converteren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
