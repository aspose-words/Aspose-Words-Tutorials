---
"description": "Förbättra dokumenttydligheten med Aspose.Words för Java-rensningsalternativ. Lär dig hur du tar bort tomma stycken, oanvända regioner och mer."
"linktitle": "Använda rensningsalternativ"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda rensningsalternativ i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda rensningsalternativ i Aspose.Words för Java


## Introduktion till användning av rensningsalternativ i Aspose.Words för Java

I den här handledningen ska vi utforska hur man använder rensningsalternativ i Aspose.Words för Java för att manipulera och rensa dokument under dokumentkopplingsprocessen. Med rensningsalternativen kan du styra olika aspekter av dokumentrensning, till exempel att ta bort tomma stycken, oanvända områden och mer.

## Förkunskapskrav

Innan vi börjar, se till att du har Aspose.Words för Java-biblioteket integrerat i ditt projekt. Du kan ladda ner det från [här](https://releases.aspose.com/words/java/).

## Steg 1: Ta bort tomma stycken

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga kopplingsfält
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Ställ in rensningsalternativ
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Aktivera rensning av stycken med skiljetecken
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Kör dokumentkoppling
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

I det här exemplet skapar vi ett nytt dokument, infogar kopplingsfält och ställer in rensningsalternativen för att ta bort tomma stycken. Dessutom aktiverar vi borttagning av stycken med skiljetecken. Efter att dokumentkopplingen har körts sparas dokumentet med den angivna rensningen tillämpad.

## Steg 2: Ta bort osammanslagna regioner

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Ställ in rensningsalternativ för att ta bort oanvända regioner
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Utför dokumentkoppling med regioner
doc.getMailMerge().executeWithRegions(data);

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

I det här exemplet öppnar vi ett befintligt dokument med sammanfogningsområden, ställer in rensningsalternativen för att ta bort oanvända områden och kör sedan dokumentkopplingen med tomma data. Denna process tar automatiskt bort de oanvända områdena från dokumentet.

## Steg 3: Ta bort tomma fält

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ställ in rensningsalternativ för att ta bort tomma fält
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Kör dokumentkoppling
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

det här exemplet öppnar vi ett dokument med kopplingsfält, ställer in rensningsalternativen för att ta bort tomma fält och kör dokumentkopplingen med data. Efter kopplingen tas alla tomma fält bort från dokumentet.

## Steg 4: Ta bort oanvända fält

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ställ in rensningsalternativ för att ta bort oanvända fält
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Kör dokumentkoppling
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

I det här exemplet öppnar vi ett dokument med kopplingsfält, ställer in rensningsalternativen för att ta bort oanvända fält och kör dokumentkopplingen med data. Efter kopplingen tas alla oanvända fält bort från dokumentet.

## Steg 5: Ta bort innehållande fält

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ange rensningsalternativ för att ta bort innehållande fält
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Kör dokumentkoppling
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

I det här exemplet öppnar vi ett dokument med kopplingsfält, ställer in rensningsalternativen för att ta bort innehållande fält och kör dokumentkopplingen med data. Efter kopplingen tas själva fälten bort från dokumentet.

## Steg 6: Ta bort tomma tabellrader

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ställ in rensningsalternativ för att ta bort tomma tabellrader
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Kör dokumentkoppling
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

I det här exemplet öppnar vi ett dokument med en tabell och kopplingsfält, ställer in rensningsalternativen för att ta bort tomma tabellrader och kör dokumentkopplingen med data. Efter kopplingen tas alla tomma tabellrader bort från dokumentet.

## Slutsats

I den här handledningen har du lärt dig hur du använder rensningsalternativ i Aspose.Words för Java för att manipulera och rensa dokument under dokumentkopplingsprocessen. Dessa alternativ ger finjusterad kontroll över dokumentrensning, så att du enkelt kan skapa eleganta och anpassade dokument.

## Vanliga frågor

### Vilka rensningsalternativ finns i Aspose.Words för Java?

Rensningsalternativ i Aspose.Words för Java är inställningar som låter dig styra olika aspekter av dokumentrensning under dokumentkopplingsprocessen. De gör att du kan ta bort onödiga element som tomma stycken, oanvända områden och mer, vilket säkerställer att ditt slutliga dokument är välstrukturerat och polerat.

### Hur kan jag ta bort tomma stycken från mitt dokument?

För att ta bort tomma stycken från ditt dokument med Aspose.Words för Java kan du ställa in `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` alternativet till sant. Detta tar automatiskt bort stycken som saknar innehåll, vilket resulterar i ett renare dokument.

### Vad är syftet med `REMOVE_UNUSED_REGIONS` städalternativ?

De `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Alternativet används för att ta bort regioner i ett dokument som inte har motsvarande data under dokumentkopplingsprocessen. Det hjälper till att hålla dokumentet snyggt genom att ta bort oanvända platsmarkörer.

### Kan jag ta bort tomma tabellrader från ett dokument med hjälp av Aspose.Words för Java?

Ja, du kan ta bort tomma tabellrader från ett dokument genom att ställa in `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` rensningsalternativet till sant. Detta tar automatiskt bort alla tabellrader som inte innehåller data, vilket säkerställer en välstrukturerad tabell i ditt dokument.

### Vad händer när jag ställer in `REMOVE_CONTAINING_FIELDS` alternativ?

Inställning av `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` alternativet tar bort hela kopplingsfältet, inklusive det stycke som innehåller det, från dokumentet under dokumentkopplingsprocessen. Detta är användbart när du vill ta bort kopplingsfält och deras tillhörande text.

### Hur kan jag ta bort oanvända kopplingsfält från mitt dokument?

För att ta bort oanvända kopplingsfält från ett dokument kan du ställa in `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` alternativet till sant. Detta tar automatiskt bort kopplingsfält som inte fylls i under kopplingen, vilket resulterar i ett renare dokument.

### Vad är skillnaden mellan `REMOVE_EMPTY_FIELDS` och `REMOVE_UNUSED_FIELDS` städalternativ?

De `REMOVE_EMPTY_FIELDS` alternativet tar bort kopplingsfält som inte innehåller några data eller är tomma under kopplingsprocessen. Å andra sidan, `REMOVE_UNUSED_FIELDS` alternativet tar bort kopplingsfält som inte fylls med data under kopplingen. Valet mellan dem beror på om du vill ta bort fält utan innehåll eller de som inte används i den specifika kopplingsåtgärden.

### Hur kan jag aktivera borttagning av stycken med skiljetecken?

För att aktivera borttagning av stycken med skiljetecken kan du ställa in `cleanupParagraphsWithPunctuationMarks` alternativet till sant och ange vilka skiljetecken som ska användas vid rensning. Detta gör att du kan skapa ett mer förfinat dokument genom att ta bort onödiga stycken med endast skiljetecken.

### Kan jag anpassa rensningsalternativen i Aspose.Words för Java?

Ja, du kan anpassa rensningsalternativen efter dina specifika behov. Du kan välja vilka rensningsalternativ du vill använda och konfigurera dem enligt dina dokumentrensningskrav, vilket säkerställer att ditt slutliga dokument uppfyller dina önskade standarder.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}