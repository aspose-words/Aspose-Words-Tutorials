---
date: 2026-01-11
description: Lär dig hur du rensar upp Word-dokument med Aspose.Words för Java:s rensningsalternativ,
  inklusive att ta bort tomma stycken, tomma tabellrader och oanvända fält.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Rensa upp Word-dokument med Aspose.Words rensningsalternativ (Java)
url: /sv/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rensa Word‑dokument med Aspose.Words Cleanup‑alternativ (Java)

I den här handledningen får du lära dig hur du **rengör Word‑dokument** med Aspose.Words för Java. Oavsett om du genererar fakturor, kontrakt eller massiva mail‑merge‑rapporter, kan oönskade tomma stycken, oanvända fält eller tomma tabellrader göra det slutgiltiga resultatet oprofessionellt. Vi går igenom varje cleanup‑alternativ steg‑för‑steg, visar exakt kod du behöver och förklarar *varför* varje inställning är viktig så att du kan producera välpolerade dokument varje gång.

## Snabba svar
- **Vad betyder “clean up Word document”?** Att ta bort tomma stycken, oanvända merge‑regioner, tomma tabellrader och andra överflödiga element efter en mail‑merge‑operation.  
- **Vilket cleanup‑alternativ tar bort tomma stycken?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Hur kan jag ta bort tomma tabellrader?** Använd `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Kan jag bli av med fält som aldrig fylldes i?** Ja – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` eller `REMOVE_EMPTY_FIELDS`.  
- **Behöver jag en licens för att köra dessa exempel?** En gratis provversion fungerar för utvärdering; en kommersiell licens krävs för produktionsanvändning.

## Vad betyder “Clean Up Word Document” i samband med Mail Merge?
När du utför en mail‑merge infogar Aspose.Words data i merge‑fält och -regioner. Om vissa fält får `null` eller tomma strängar kan dokumentet sluta med lösa stycken, tomma tabeller eller platshållar‑regioner. **Cleanup‑alternativen** tar automatiskt bort dessa artefakter och lämnar ett rent, utskriftsklart dokument.

## Varför använda Cleanup‑alternativ?
- **Professionellt utseende:** Inga tomma rader eller föräldralösa tabeller.  
- **Mindre filstorlek:** Borttagning av oanvända element minskar dokumentets vikt.  
- **Förenklad efterbehandling:** Rena dokument är enklare att konvertera till PDF, HTML eller andra format.  
- **Tidsbesparande:** En‑rad‑inställningar ersätter manuella efterbearbetningsskript.

## Förutsättningar
- Java‑utvecklingsmiljö (JDK 8+).  
- Aspose.Words för Java‑bibliotek – ladda ner det från [here](https://releases.aspose.com/words/java/).  
- Grundläggande kunskap om mail‑merge‑koncept.

## Steg‑för‑steg‑guide

### Steg 1: Så tar du bort tomma stycken (Java)
Först visar vi hur du eliminerar stycken som inte innehåller någon synlig text. Detta är särskilt användbart när ett merge‑fält blir `null`.

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

**Vad händer här?**  
- `REMOVE_EMPTY_PARAGRAPHS` instruerar Aspose.Words att ta bort alla stycken som blir tomma efter merge.  
- Att aktivera `cleanupParagraphsWithPunctuationMarks` tar även bort stycken som endast består av skiljetecken (t.ex. “?”).

### Steg 2: Så tar du bort o‑merge‑ade regioner
Om en mail‑merge‑region saknar motsvarande data kan du kasta bort den helt.

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

**Varför är detta viktigt:**  
Oanvända regioner lämnar ofta tomma sektioner eller lösa rubriker. Flaggan `REMOVE_UNUSED_REGIONS` rensar dem automatiskt.

### Steg 3: Så tar du bort tomma fält
När ett fält får en tom sträng vill du kanske ta bort hela fältet istället för att lämna ett tomt platshållare.

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

### Steg 4: Så tar du bort oanvända fält
Om vissa fält aldrig refereras under merge kan du ta bort dem helt.

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

### Steg 5: Så tar du bort omgivande fält
Ibland finns ett merge‑fält inuti ett stycke som du också vill kasta bort.

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

### Steg 6: Så tar du bort tomma tabellrader
Tabeller får ofta rader som bara innehåller tomma fält. Detta alternativ rensar bort sådana rader.

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

## Vanliga problem & felsökning
- **Stycken tas inte bort:** Säkerställ att `setCleanupParagraphsWithPunctuationMarks(true)` anropas *efter* att cleanup‑alternativet har satts.  
- **Tomma tabellrader kvarstår:** Kontrollera att tabellcellerna verkligen innehåller tomma strängar (inte bara blanksteg).  
- **Oanvända fält finns kvar:** Dubbelkolla att du använder rätt enum (`REMOVE_UNUSED_FIELDS`) och att merge‑fälten inte av misstag fylls i någon annanstans.

## Vanliga frågor

**Q: Vad är skillnaden mellan `REMOVE_EMPTY_FIELDS` och `REMOVE_UNUSED_FIELDS`?**  
A: `REMOVE_EMPTY_FIELDS` tar bort fält som får en tom sträng eller `null` under merge, medan `REMOVE_UNUSED_FIELDS` tar bort fält som aldrig refererades av merge‑operationen.

**Q: Kan jag kombinera flera cleanup‑alternativ?**  
A: Ja. Metoden `setCleanupOptions` accepterar en bitvis OR av enum‑värden, så du kan rensa stycken, tabeller och regioner i ett enda anrop.

**Q: Påverkar aktivering av `cleanupParagraphsWithPunctuationMarks` normal text?**  
A: Det tar endast bort stycken som enbart består av skiljetecken (t.ex. “?” eller “---”). Vanliga meningar lämnas orörda.

**Q: Är det möjligt att anpassa vilka skiljetecken som räknas?**  
A: Det nuvarande API:t använder en fördefinierad uppsättning skiljetecken. För anpassat beteende måste du efterbehandla dokumentet efter merge.

**Q: Fungerar dessa cleanup‑alternativ med PDF‑konvertering?**  
A: Absolut. När Word‑dokumentet är rensat kan du konvertera det till PDF, HTML eller något annat stödd format utan att de oönskade elementen följer med.

## Slutsats
Du har nu ett komplett verktyg för **cleaning up Word document**‑filer under mail‑merge med Aspose.Words för Java. Genom att välja rätt `MailMergeCleanupOptions` kan du automatiskt ta bort tomma stycken, tomma tabellrader, oanvända fält och mer – vilket ger dig ett slimmat, produktionsklart dokument varje gång.

---

**Senast uppdaterad:** 2026-01-11  
**Testat med:** Aspose.Words för Java 24.11  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}