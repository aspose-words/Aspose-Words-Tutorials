---
title: Använda rengöringsalternativ i Aspose.Words för Java
linktitle: Använda rengöringsalternativ
second_title: Aspose.Words Java Document Processing API
description: Förbättra dokumenttydligheten med Aspose.Words för Java-rensningsalternativ. Lär dig hur du tar bort tomma stycken, oanvända områden och mer.
weight: 10
url: /sv/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använda rengöringsalternativ i Aspose.Words för Java


## Introduktion till användning av rensningsalternativ i Aspose.Words för Java

den här handledningen kommer vi att utforska hur man använder rensningsalternativ i Aspose.Words för Java för att manipulera och städa upp dokument under kopplingsprocessen. Rensningsalternativ låter dig styra olika aspekter av dokumentrensning, som att ta bort tomma stycken, oanvända områden och mer.

## Förutsättningar

 Innan vi börjar, se till att du har Aspose.Words för Java-biblioteket integrerat i ditt projekt. Du kan ladda ner den från[här](https://releases.aspose.com/words/java/).

## Steg 1: Ta bort tomma stycken

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga sammanslagningsfält
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Ställ in rensningsalternativ
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Aktivera rensningsstycken med skiljetecken
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Kör sammanslagning
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

I det här exemplet skapar vi ett nytt dokument, infogar sammanslagningsfält och ställer in rensningsalternativen för att ta bort tomma stycken. Dessutom möjliggör vi borttagning av stycken med skiljetecken. Efter att ha kört sammankopplingen sparas dokumentet med den angivna rensningen tillämpad.

## Steg 2: Ta bort icke sammanslagna regioner

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Ställ in rensningsalternativ för att ta bort oanvända regioner
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Utför e-postsammanslagning med regioner
doc.getMailMerge().executeWithRegions(data);

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

det här exemplet öppnar vi ett befintligt dokument med sammanslagningsregioner, ställer in rensningsalternativen för att ta bort oanvända regioner och kör sedan sammanslagningen med tomma data. Denna process tar automatiskt bort de oanvända områdena från dokumentet.

## Steg 3: Ta bort tomma fält

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ställ in rensningsalternativ för att ta bort tomma fält
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Kör sammanslagning
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

I det här exemplet öppnar vi ett dokument med kopplingsfält, ställer in rensningsalternativen för att ta bort tomma fält och kör kopplingen med data. Efter sammanslagningen kommer alla tomma fält att tas bort från dokumentet.

## Steg 4: Ta bort oanvända fält

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ställ in rensningsalternativ för att ta bort oanvända fält
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Kör sammanslagning
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

I det här exemplet öppnar vi ett dokument med sammanslagningsfält, ställer in rensningsalternativen för att ta bort oanvända fält och kör sammankopplingen med data. Efter sammanslagningen kommer alla oanvända fält att tas bort från dokumentet.

## Steg 5: Ta bort innehållande fält

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ställ in rensningsalternativ för att ta bort innehållande fält
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Kör sammanslagning
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

det här exemplet öppnar vi ett dokument med kopplingsfält, ställer in rensningsalternativen för att ta bort innehållande fält och kör kopplingen med data. Efter sammanslagningen kommer själva fälten att tas bort från dokumentet.

## Steg 6: Ta bort tomma bordsrader

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ställ in rensningsalternativ för att ta bort tomma tabellrader
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Kör sammanslagning
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Spara dokumentet
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

I det här exemplet öppnar vi ett dokument med en tabell och sammanslagningsfält, ställer in rensningsalternativen för att ta bort tomma tabellrader och kör sammanfogningen med data. Efter sammanslagningen kommer alla tomma tabellrader att tas bort från dokumentet.

## Slutsats

I den här handledningen har du lärt dig hur du använder rensningsalternativ i Aspose.Words för Java för att manipulera och städa upp dokument under kopplingsprocessen. Dessa alternativ ger finkornig kontroll över dokumentrensning, så att du enkelt kan skapa polerade och anpassade dokument.

## FAQ's

### Vilka är rensningsalternativen i Aspose.Words för Java?

Rensningsalternativ i Aspose.Words för Java är inställningar som låter dig styra olika aspekter av dokumentrensning under sammankopplingsprocessen. De gör att du kan ta bort onödiga element som tomma stycken, oanvända regioner och mer, vilket säkerställer att ditt slutdokument är välstrukturerat och polerat.

### Hur kan jag ta bort tomma stycken från mitt dokument?

 För att ta bort tomma stycken från ditt dokument med Aspose.Words för Java, kan du ställa in`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` alternativet till sant. Detta kommer automatiskt att eliminera stycken som inte har något innehåll, vilket resulterar i ett renare dokument.

###  Vad är syftet med`REMOVE_UNUSED_REGIONS` cleanup option?

 De`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` alternativet används för att ta bort regioner i ett dokument som inte har motsvarande data under kopplingsprocessen. Det hjälper till att hålla ditt dokument snyggt genom att ta bort oanvända platshållare.

### Kan jag ta bort tomma tabellrader från ett dokument med Aspose.Words för Java?

 Ja, du kan ta bort tomma tabellrader från ett dokument genom att ställa in`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`rensningsalternativet till sant. Detta tar automatiskt bort alla tabellrader som inte innehåller data, vilket säkerställer en välstrukturerad tabell i ditt dokument.

###  Vad händer när jag ställer in`REMOVE_CONTAINING_FIELDS` option?

 Ställa in`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` alternativet tar bort hela kopplingsfältet, inklusive dess innehållande stycke, från dokumentet under kopplingsprocessen. Detta är användbart när du vill eliminera sammanslagningsfält och deras tillhörande text.

### Hur kan jag ta bort oanvända sammanslagningsfält från mitt dokument?

 För att ta bort oanvända sammanslagningsfält från ett dokument kan du ställa in`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` alternativet till sant. Detta kommer automatiskt att eliminera sammanslagningsfält som inte fylls i under sammankopplingen, vilket resulterar i ett renare dokument.

###  Vad är skillnaden mellan`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 De`REMOVE_EMPTY_FIELDS` alternativet tar bort sammanslagningsfält som inte har några data eller är tomma under sammankopplingsprocessen. Å andra sidan`REMOVE_UNUSED_FIELDS`alternativet tar bort sammanslagningsfält som inte fylls i med data under sammanslagningen. Valet mellan dem beror på om du vill ta bort fält utan innehåll eller de som är oanvända i den specifika sammanfogningsoperationen.

### Hur kan jag aktivera borttagning av stycken med skiljetecken?

 För att möjliggöra borttagning av stycken med skiljetecken kan du ställa in`cleanupParagraphsWithPunctuationMarks` alternativet för att sanna och ange skiljetecken som ska beaktas för rensning. Detta gör att du kan skapa ett mer förfinat dokument genom att ta bort onödiga stycken med endast skiljetecken.

### Kan jag anpassa rensningsalternativen i Aspose.Words för Java?

Ja, du kan anpassa rensningsalternativen efter dina specifika behov. Du kan välja vilka rensningsalternativ som ska tillämpas och konfigurera dem enligt dina krav för dokumentrensning, vilket säkerställer att ditt slutliga dokument uppfyller dina önskade standarder.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
