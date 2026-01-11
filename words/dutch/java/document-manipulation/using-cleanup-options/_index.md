---
date: 2026-01-11
description: Leer hoe je een Word‑document kunt opschonen met behulp van de opruimopties
  van Aspose.Words voor Java, inclusief het verwijderen van lege alinea’s, lege tabelrijen
  en ongebruikte velden.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Word-document opschonen met Aspose.Words‑opruimopties (Java)
url: /nl/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word-document opschonen met Aspose.Words Cleanup‑opties (Java)

In deze tutorial ontdek je hoe je **Word‑documenten** kunt opschonen met Aspose.Words voor Java. Of je nu facturen, contracten of bulk‑mail‑merge‑rapporten genereert, ongewenste lege alinea’s, ongebruikte velden of lege tabelrijen kunnen het eindresultaat onprofessioneel laten lijken. We lopen stap‑voor‑stap elke opschoonoptie door, laten je de exacte code zien die je nodig hebt, en leggen *waarom* elke instelling belangrijk is zodat je elke keer gepolijste documenten kunt produceren.

## Snelle antwoorden
- **Wat betekent “Word‑document opschonen”?** Het verwijderen van lege alinea’s, ongebruikte merge‑regio’s, lege tabelrijen en andere overbodige elementen na een mail‑merge‑bewerking.  
- **Welke opschoonoptie verwijdert lege alinea’s?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Hoe kan ik lege tabelrijen verwijderen?** Gebruik `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Kan ik velden verwijderen die nooit zijn ingevuld?** Ja – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` of `REMOVE_EMPTY_FIELDS`.  
- **Heb ik een licentie nodig om deze voorbeelden uit te voeren?** Een gratis proefversie werkt voor evaluatie; een commerciële licentie is vereist voor productiegebruik.

## Wat betekent “Word‑document opschonen” in de context van Mail Merge?
Wanneer je een mail‑merge uitvoert, voegt Aspose.Words gegevens in merge‑velden en -regio’s in. Als sommige velden `null` of lege strings ontvangen, kan het document eindigen met losse alinea’s, lege tabellen of placeholder‑regio’s. De **opschoonopties** verwijderen deze artefacten automatisch, waardoor een schoon, klaar‑om‑te‑printen document ontstaat.

## Waarom opschoonopties gebruiken?
- **Professionele uitstraling:** Geen lege regels of verweesde tabellen.  
- **Kleinere bestandsgrootte:** Het verwijderen van ongebruikte elementen vermindert het documentgewicht.  
- **Vereenvoudigde downstream‑verwerking:** Schone documenten zijn makkelijker te converteren naar PDF, HTML of andere formaten.  
- **Tijdbesparing:** Eén‑regelige instellingen vervangen handmatige post‑processing‑scripts.

## Vereisten
- Java‑ontwikkelomgeving (JDK 8+).  
- Aspose.Words voor Java‑bibliotheek – download deze van [hier](https://releases.aspose.com/words/java/).  
- Basiskennis van mail‑merge‑concepten.

## Stapsgewijze handleiding

### Stap 1: Lege alinea’s verwijderen (Java)
Eerst laten we zien hoe je alinea’s die geen zichtbare tekst bevatten, kunt elimineren. Dit is vooral nuttig wanneer een merge‑veld `null` oplevert.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Wat gebeurt er hier?**  
- `REMOVE_EMPTY_PARAGRAPHS` vertelt Aspose.Words om elke alinea die na de merge leeg is, te verwijderen.  
- Het inschakelen van `cleanupParagraphsWithPunctuationMarks` verwijdert ook alinea’s die uitsluitend uit interpunctie bestaan (bijv. “?”).

### Stap 2: Niet‑samengevoegde regio’s verwijderen
Als een mail‑merge‑regio geen bijbehorende gegevens heeft, kun je deze volledig weggooien.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Waarom dit belangrijk is:**  
Ongebruikte regio’s laten vaak lege secties of losse koppen achter. De vlag `REMOVE_UNUSED_REGIONS` verwijdert ze automatisch.

### Stap 3: Lege velden verwijderen
Wanneer een veld een lege string ontvangt, wil je misschien het hele veld verwijderen in plaats van een lege placeholder achter te laten.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Stap 4: Ongebruikte velden verwijderen
Als bepaalde velden nooit worden aangeroepen tijdens de merge, kun je ze volledig weghalen.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Stap 5: Bevatte velden verwijderen
Soms bevindt een merge‑veld zich binnen een alinea die je ook wilt verwijderen.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Stap 6: Lege tabelrijen verwijderen
Tabellen eindigen vaak met rijen die alleen lege velden bevatten. Deze optie snoeit die rijen weg.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Veelvoorkomende problemen & foutopsporing
- **Alinea’s worden niet verwijderd:** Zorg ervoor dat `setCleanupParagraphsWithPunctuationMarks(true)` wordt aangeroepen *na* het instellen van de opschoonoptie.  
- **Lege tabelrijen blijven bestaan:** Controleer of de tabelcellen echt lege strings bevatten (geen spaties).  
- **Ongebruikte velden blijven staan:** Controleer of je de juiste enum (`REMOVE_UNUSED_FIELDS`) gebruikt en dat de merge‑velden niet per ongeluk elders worden gevuld.

## Veelgestelde vragen

**V: Wat is het verschil tussen `REMOVE_EMPTY_FIELDS` en `REMOVE_UNUSED_FIELDS`?**  
A: `REMOVE_EMPTY_FIELDS` verwijdert velden die tijdens de merge een lege string of `null` ontvangen, terwijl `REMOVE_UNUSED_FIELDS` velden verwijdert die nooit door de merge‑operatie zijn aangeroepen.

**V: Kan ik meerdere opschoonopties combineren?**  
A: Ja. De methode `setCleanupOptions` accepteert een bitwise OR van enum‑waarden, zodat je alinea’s, tabellen en regio’s in één oproep kunt opschonen.

**V: Heeft het inschakelen van `cleanupParagraphsWithPunctuationMarks` invloed op normale tekst?**  
A: Het verwijdert alleen alinea’s die uitsluitend uit interpunctietekens bestaan (bijv. “?” of “---”). Reguliere zinnen blijven onaangetast.

**V: Is het mogelijk om zelf te bepalen welke interpunctietekens worden beschouwd?**  
A: De huidige API gebruikt een vooraf gedefinieerde set interpunctietekens. Voor aangepast gedrag moet je het document na de merge zelf post‑processen.

**V: Werken deze opschoonopties ook bij PDF-conversie?**  
A: Absoluut. Zodra het Word‑document is opgeschoond, kun je het converteren naar PDF, HTML of elk ander ondersteund formaat zonder de ongewenste elementen mee te nemen.

## Conclusie
Je beschikt nu over een volledige toolbox om **Word‑documenten** tijdens mail‑merge op te schonen met Aspose.Words voor Java. Door de juiste `MailMergeCleanupOptions` te selecteren, kun je automatisch lege alinea’s, lege tabelrijen, ongebruikte velden en meer verwijderen – waardoor je elke keer een strak, productie‑klaar document krijgt.

---

**Laatst bijgewerkt:** 2026-01-11  
**Getest met:** Aspose.Words voor Java 24.11  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}