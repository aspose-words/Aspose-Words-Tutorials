---
"description": "Lås upp kraften i Aspose.Words för Java. Lär dig att läsa in textdokument, hantera listor, hantera mellanslag och kontrollera textriktning."
"linktitle": "Laddar textfiler med"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Laddar textfiler med Aspose.Words för Java"
"url": "/sv/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Laddar textfiler med Aspose.Words för Java


## Introduktion till att ladda textfiler med Aspose.Words för Java

I den här guiden ska vi utforska hur man laddar textfiler med Aspose.Words för Java och manipulerar dem som Word-dokument. Vi kommer att gå igenom olika aspekter som att identifiera listor, hantera mellanslag och kontrollera textriktning.

## Steg 1: Identifiera listor

För att läsa in ett textdokument och identifiera listor kan du följa dessa steg:

```java
// Skapa ett klartextdokument i form av en sträng med delar som kan tolkas som listor.
// Vid laddning kommer de tre första listorna alltid att detekteras av Aspose.Words,
// och List-objekt skapas för dem efter inläsning.
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
// Den fjärde listan, med mellanslag mellan listnumret och listobjektets innehåll,
// kommer endast att detekteras som en lista om "DetectNumberingWithWhitespaces" i ett LoadOptions-objekt är satt till sant,
// för att undvika att stycken som börjar med siffror felaktigt identifieras som listor.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Ladda dokumentet medan du använder LoadOptions som parameter och verifiera resultatet.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Den här koden visar hur man laddar ett textdokument med olika listformat och använder `DetectNumberingWithWhitespaces` alternativ för att korrekt identifiera listor.

## Steg 2: Hantera mellanslagsalternativ

För att kontrollera inledande och efterföljande mellanslag när du laddar ett textdokument kan du använda följande kod:

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

I det här exemplet laddar vi ett textdokument och tar bort inledande och avslutande mellanslag med hjälp av `TxtLeadingSpacesOptions.TRIM` och `TxtTrailingSpacesOptions.TRIM`.

## Steg 3: Kontrollera textriktning

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

Den här koden ställer in dokumentriktningen på automatisk detektering (`DocumentDirection.AUTO`) och laddar ett textdokument med hebreisk text. Du kan justera dokumentets riktning efter behov.

## Komplett källkod för att ladda textfiler med Aspose.Words för Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Skapa ett klartextdokument i form av en sträng med delar som kan tolkas som listor.
	// Vid laddning kommer de tre första listorna alltid att detekteras av Aspose.Words,
	// och List-objekt skapas för dem efter inläsning.
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
	// Den fjärde listan, med mellanslag mellan listnumret och listobjektets innehåll,
	// kommer endast att detekteras som en lista om "DetectNumberingWithWhitespaces" i ett LoadOptions-objekt är satt till sant,
	// för att undvika att stycken som börjar med siffror felaktigt identifieras som listor.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Ladda dokumentet medan du använder LoadOptions som parameter och verifiera resultatet.
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

I den här guiden har vi utforskat hur man laddar textfiler med Aspose.Words för Java, identifierar listor, hanterar mellanslag och kontrollerar textriktning. Dessa tekniker låter dig manipulera textdokument effektivt i dina Java-applikationer.

## Vanliga frågor

### Vad är Aspose.Words för Java?

Aspose.Words för Java är ett kraftfullt dokumentbehandlingsbibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument programmatiskt i Java-applikationer. Det erbjuder ett brett utbud av funktioner för att arbeta med text, tabeller, bilder och andra dokumentelement.

### Hur kan jag komma igång med Aspose.Words för Java?

För att komma igång med Aspose.Words för Java, följ dessa steg:
1. Ladda ner och installera Aspose.Words för Java-biblioteket.
2. Se dokumentationen på [Aspose.Words för Java API-referens](https://reference.aspose.com/words/java/) för detaljerad information och exempel.
3. Utforska exempelkoden och handledningarna för att lära dig hur du använder biblioteket effektivt.

### Hur laddar jag ett textdokument med Aspose.Words för Java?

För att ladda ett textdokument med Aspose.Words för Java kan du använda `TxtLoadOptions` klass och `Document` klass. Se till att du anger lämpliga alternativ för hantering av mellanslag och textriktning efter behov. Se steg-för-steg-guiden i den här artikeln för ett detaljerat exempel.

### Kan jag konvertera ett laddat textdokument till andra format?

Ja, Aspose.Words för Java låter dig konvertera ett laddat textdokument till olika format, inklusive DOCX, PDF med mera. Du kan använda `Document` klassen för att utföra konverteringar. Kontrollera dokumentationen för specifika konverteringsexempel.

### Hur hanterar jag mellanslag i inlästa textdokument?

Du kan styra hur inledande och efterföljande mellanslag hanteras i inlästa textdokument med hjälp av `TxtLoadOptions`Alternativ som `TxtLeadingSpacesOptions` och `TxtTrailingSpacesOptions` låter dig trimma eller bevara mellanslag efter behov. Se avsnittet "Hantera mellanslagsalternativ" i den här guiden för ett exempel.

### Vilken betydelse har textriktning i Aspose.Words för Java?

Textriktning är avgörande för dokument som innehåller blandade skrifttyper eller språk, såsom hebreiska eller arabiska. Aspose.Words för Java erbjuder alternativ för att ange textriktningen, vilket säkerställer korrekt återgivning och formatering av text på dessa språk. Avsnittet "Kontrollera textriktning" i den här guiden visar hur man ställer in textriktningen.

### Var kan jag hitta fler resurser och support för Aspose.Words för Java?

För ytterligare resurser, dokumentation och support, besök [Aspose.Words för Java-dokumentation](https://reference.aspose.com/words/java/)Du kan också delta i Aspose.Words communityforum eller kontakta Aspose support för hjälp med specifika problem eller frågor.

### Är Aspose.Words för Java lämpligt för kommersiella projekt?

Ja, Aspose.Words för Java är lämpligt för både personliga och kommersiella projekt. Det erbjuder licensalternativ för att tillgodose olika användningsscenarier. Se till att granska licensvillkoren och priserna på Asposes webbplats för att välja rätt licens för ditt projekt.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}