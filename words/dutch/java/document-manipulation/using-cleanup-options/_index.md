---
title: Opruimopties gebruiken in Aspose.Words voor Java
linktitle: Opruimopties gebruiken
second_title: Aspose.Words Java Documentverwerkings-API
description: Verbeter de duidelijkheid van documenten met Aspose.Words voor Java Cleanup Options. Leer hoe u lege alinea's, ongebruikte regio's en meer verwijdert.
weight: 10
url: /nl/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opruimopties gebruiken in Aspose.Words voor Java


## Inleiding tot het gebruik van opschoonopties in Aspose.Words voor Java

In deze tutorial gaan we onderzoeken hoe je opruimopties in Aspose.Words voor Java kunt gebruiken om documenten te manipuleren en op te schonen tijdens het samenvoegproces. Met opruimopties kun je verschillende aspecten van het opschonen van documenten beheren, zoals het verwijderen van lege alinea's, ongebruikte regio's en meer.

## Vereisten

 Voordat we beginnen, zorg ervoor dat je de Aspose.Words voor Java-bibliotheek in je project hebt geïntegreerd. Je kunt het downloaden van[hier](https://releases.aspose.com/words/java/).

## Stap 1: Lege alinea's verwijderen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Samenvoegvelden invoegen
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Opruimopties instellen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Schakel opruiming van alinea's met leestekens in
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Mail merge uitvoeren
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Sla het document op
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

In dit voorbeeld maken we een nieuw document, voegen we samenvoegvelden in en stellen we de opschoonopties in om lege alinea's te verwijderen. Daarnaast schakelen we het verwijderen van alinea's met leestekens in. Na het uitvoeren van de samenvoeging wordt het document opgeslagen met de opgegeven opschoning toegepast.

## Stap 2: Niet-samengevoegde regio's verwijderen

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Stel opruimopties in om ongebruikte regio's te verwijderen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Mail merge uitvoeren met regio's
doc.getMailMerge().executeWithRegions(data);

// Sla het document op
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

In dit voorbeeld openen we een bestaand document met merge regions, stellen de cleanup-opties in om ongebruikte regions te verwijderen en voeren vervolgens de mail merge uit met lege data. Dit proces verwijdert automatisch de ongebruikte regions uit het document.

## Stap 3: Lege velden verwijderen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Stel opruimopties in om lege velden te verwijderen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Mail merge uitvoeren
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Sla het document op
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

In dit voorbeeld openen we een document met samenvoegvelden, stellen we de opschoonopties in om lege velden te verwijderen en voeren we de samenvoeging met gegevens uit. Na de samenvoeging worden alle lege velden uit het document verwijderd.

## Stap 4: Ongebruikte velden verwijderen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Stel opruimopties in om ongebruikte velden te verwijderen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Mail merge uitvoeren
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Sla het document op
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

In dit voorbeeld openen we een document met samenvoegvelden, stellen we de opschoonopties in om ongebruikte velden te verwijderen en voeren we de samenvoeging met gegevens uit. Na de samenvoeging worden alle ongebruikte velden uit het document verwijderd.

## Stap 5: Bevattende velden verwijderen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Stel opruimopties in om velden te verwijderen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Mail merge uitvoeren
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Sla het document op
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

In dit voorbeeld openen we een document met samenvoegvelden, stellen we de opschoonopties in om de bevattende velden te verwijderen en voeren we de samenvoeging met gegevens uit. Na de samenvoeging worden de velden zelf uit het document verwijderd.

## Stap 6: Lege tabelrijen verwijderen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Stel opruimopties in om lege tabelrijen te verwijderen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Mail merge uitvoeren
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Sla het document op
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

In dit voorbeeld openen we een document met een tabel en merge fields, stellen de cleanup-opties in om lege tabelrijen te verwijderen en voeren de mail merge uit met data. Na de merge worden alle lege tabelrijen uit het document verwijderd.

## Conclusie

In deze tutorial hebt u geleerd hoe u opschoonopties in Aspose.Words voor Java kunt gebruiken om documenten te manipuleren en op te schonen tijdens het samenvoegproces. Deze opties bieden nauwkeurige controle over het opschonen van documenten, zodat u eenvoudig gepolijste en aangepaste documenten kunt maken.

## Veelgestelde vragen

### Wat zijn de opschoonopties in Aspose.Words voor Java?

Opruimopties in Aspose.Words voor Java zijn instellingen waarmee u verschillende aspecten van het opschonen van documenten kunt beheren tijdens het samenvoegproces. Hiermee kunt u onnodige elementen verwijderen, zoals lege alinea's, ongebruikte gebieden en meer, zodat uw uiteindelijke document goed gestructureerd en gepolijst is.

### Hoe kan ik lege alinea's uit mijn document verwijderen?

 Om lege alinea's uit uw document te verwijderen met Aspose.Words voor Java, kunt u de volgende instellingen gebruiken:`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` optie op true. Dit zal automatisch paragrafen zonder inhoud verwijderen, wat resulteert in een schoner document.

###  Wat is het doel van de`REMOVE_UNUSED_REGIONS` cleanup option?

 De`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` optie wordt gebruikt om regio's in een document te verwijderen die geen corresponderende gegevens hebben tijdens het samenvoegproces. Het helpt uw document opgeruimd te houden door ongebruikte tijdelijke aanduidingen te verwijderen.

### Kan ik lege tabelrijen uit een document verwijderen met Aspose.Words voor Java?

 Ja, u kunt lege tabelrijen uit een document verwijderen door de`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`opschoonoptie op true. Hiermee worden automatisch alle tabelrijen verwijderd die geen gegevens bevatten, wat zorgt voor een goed gestructureerde tabel in uw document.

###  Wat gebeurt er als ik de`REMOVE_CONTAINING_FIELDS` option?

 Het instellen van de`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` optie verwijdert het gehele samenvoegveld, inclusief de alinea die het bevat, uit het document tijdens het samenvoegproces. Dit is handig als u samenvoegvelden en de bijbehorende tekst wilt verwijderen.

### Hoe kan ik ongebruikte samenvoegvelden uit mijn document verwijderen?

 Om ongebruikte samenvoegvelden uit een document te verwijderen, kunt u de volgende instellingen gebruiken:`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` optie op true. Dit zal automatisch samenvoegvelden verwijderen die niet zijn ingevuld tijdens de mail merge, wat resulteert in een schoner document.

###  Wat is het verschil tussen`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 De`REMOVE_EMPTY_FIELDS` optie verwijdert samenvoegvelden die geen gegevens bevatten of leeg zijn tijdens het samenvoegproces. Aan de andere kant, de`REMOVE_UNUSED_FIELDS`optie verwijdert samenvoegvelden die niet zijn gevuld met gegevens tijdens de samenvoeging. De keuze tussen deze twee hangt af van of u velden zonder inhoud wilt verwijderen of velden die niet worden gebruikt in de specifieke samenvoegbewerking.

### Hoe kan ik het verwijderen van alinea's met leestekens inschakelen?

 Om het verwijderen van alinea's met leestekens mogelijk te maken, kunt u de volgende instellingen gebruiken:`cleanupParagraphsWithPunctuationMarks` optie op true en specificeer de leestekens die in aanmerking komen voor opschoning. Hiermee kunt u een verfijnder document maken door onnodige alinea's met alleen leestekens te verwijderen.

### Kan ik de opschoonopties in Aspose.Words voor Java aanpassen?

Ja, u kunt de opschoonopties aanpassen aan uw specifieke behoeften. U kunt kiezen welke opschoonopties u wilt toepassen en ze configureren volgens uw documentopschoonvereisten, zodat uw uiteindelijke document voldoet aan uw gewenste normen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
