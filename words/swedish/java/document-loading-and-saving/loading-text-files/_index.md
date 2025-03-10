---
title: Laddar textfiler med Aspose.Words för Java
linktitle: Laddar textfiler med
second_title: Aspose.Words Java Document Processing API
description: Lås upp kraften i Aspose.Words för Java. Lär dig att ladda textdokument, hantera listor, hantera utrymmen och styra textriktning.
weight: 13
url: /sv/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Laddar textfiler med Aspose.Words för Java


## Introduktion till att ladda textfiler med Aspose.Words för Java

I den här guiden kommer vi att utforska hur man laddar textfiler med Aspose.Words för Java och manipulerar dem som Word-dokument. Vi kommer att täcka olika aspekter som att upptäcka listor, hantera utrymmen och styra textriktning.

## Steg 1: Upptäck listor

För att ladda ett textdokument och upptäcka listor kan du följa dessa steg:

```java
// Skapa ett klartextdokument i form av en sträng med delar som kan tolkas som listor.
// Vid laddning kommer de tre första listorna alltid att upptäckas av Aspose.Words,
// och Listobjekt kommer att skapas för dem efter laddning.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
//Den fjärde listan, med blanksteg mellan listnumret och listobjektets innehåll,
// kommer bara att upptäckas som en lista om "DetectNumberingWithWhitespaces" i ett LoadOptions-objekt är satt till true,
// för att undvika att stycken som börjar med siffror av misstag upptäcks som listor.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Ladda dokumentet medan du använder LoadOptions som en parameter och verifiera resultatet.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 Den här koden visar hur man laddar ett textdokument med olika listformat och använder`DetectNumberingWithWhitespaces` alternativ för att upptäcka listor korrekt.

## Steg 2: Hantera utrymmesalternativ

För att kontrollera inledande och avslutande mellanslag när du laddar ett textdokument kan du använda följande kod:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

 I det här exemplet laddar vi ett textdokument och trimmar inledande och efterföljande mellanslag med hjälp av`TxtLeadingSpacesOptions.TRIM` och`TxtTrailingSpacesOptions.TRIM`.

## Steg 3: Styra textriktning

För att ange textriktningen när du laddar ett textdokument kan du använda följande kod:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Den här koden ställer in dokumentriktningen till automatisk upptäckt (`DocumentDirection.AUTO`och laddar ett textdokument med hebreisk text. Du kan justera dokumentriktningen efter behov.

## Komplett källkod för att ladda textfiler med Aspose.Words för Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Skapa ett klartextdokument i form av en sträng med delar som kan tolkas som listor.
	// Vid laddning kommer de tre första listorna alltid att upptäckas av Aspose.Words,
	// och Listobjekt kommer att skapas för dem efter laddning.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Den fjärde listan, med blanksteg mellan listnumret och listobjektets innehåll,
	// kommer bara att upptäckas som en lista om "DetectNumberingWithWhitespaces" i ett LoadOptions-objekt är satt till true,
	// för att undvika att stycken som börjar med siffror av misstag upptäcks som listor.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Ladda dokumentet medan du använder LoadOptions som en parameter och verifiera resultatet.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Slutsats

I den här guiden har vi utforskat hur man laddar textfiler med Aspose.Words för Java, upptäcker listor, hanterar mellanslag och styr textriktning. Dessa tekniker låter dig manipulera textdokument effektivt i dina Java-program.

## FAQ's

### Vad är Aspose.Words för Java?

Aspose.Words för Java är ett kraftfullt dokumentbehandlingsbibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument programmatiskt i Java-applikationer. Det ger ett brett utbud av funktioner för att arbeta med text, tabeller, bilder och andra dokumentelement.

### Hur kommer jag igång med Aspose.Words för Java?

För att komma igång med Aspose.Words för Java, följ dessa steg:
1. Ladda ner och installera Aspose.Words for Java-biblioteket.
2.  Se dokumentationen på[Aspose.Words för Java API Referens](https://reference.aspose.com/words/java/) för detaljerad information och exempel.
3. Utforska exempelkoden och självstudierna för att lära dig hur du använder biblioteket effektivt.

### Hur laddar jag ett textdokument med Aspose.Words för Java?

 För att ladda ett textdokument med Aspose.Words för Java kan du använda`TxtLoadOptions` klass och`Document` klass. Se till att du anger lämpliga alternativ för hantering av mellanslag och textriktning efter behov. Se steg-för-steg-guiden i den här artikeln för ett detaljerat exempel.

### Kan jag konvertera ett laddat textdokument till andra format?

 Ja, Aspose.Words för Java låter dig konvertera ett laddat textdokument till olika format, inklusive DOCX, PDF och mer. Du kan använda`Document` klass för att utföra konverteringar. Se dokumentationen för specifika konverteringsexempel.

### Hur hanterar jag mellanslag i laddade textdokument?

 Du kan styra hur inledande och efterföljande mellanslag hanteras i laddade textdokument med`TxtLoadOptions` . Alternativ som`TxtLeadingSpacesOptions` och`TxtTrailingSpacesOptions`låter dig trimma eller bevara utrymmen efter behov. Se avsnittet "Alternativ för hanteringsutrymmen" i den här guiden för ett exempel.

### Vad är betydelsen av textriktning i Aspose.Words för Java?

Textriktning är viktigt för dokument som innehåller blandade skript eller språk, som hebreiska eller arabiska. Aspose.Words för Java tillhandahåller alternativ för att specificera textriktningen, vilket säkerställer korrekt rendering och formatering av text på dessa språk. Avsnittet "Kontrollera textriktning" i den här guiden visar hur du ställer in textriktningen.

### Var kan jag hitta fler resurser och support för Aspose.Words för Java?

 För ytterligare resurser, dokumentation och support, besök[Aspose.Words för Java-dokumentation](https://reference.aspose.com/words/java/). Du kan också delta i Aspose.Words community-forum eller kontakta Asposes support för hjälp med specifika frågor eller förfrågningar.

### Är Aspose.Words för Java lämpligt för kommersiella projekt?

Ja, Aspose.Words för Java lämpar sig för både personliga och kommersiella projekt. Den erbjuder licensieringsalternativ för att tillgodose olika användningsscenarier. Se till att granska licensvillkoren och prissättningen på Asposes webbplats för att välja rätt licens för ditt projekt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
