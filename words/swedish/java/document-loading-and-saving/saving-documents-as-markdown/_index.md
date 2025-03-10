---
title: Spara dokument som Markdown i Aspose.Words för Java
linktitle: Spara dokument som Markdown
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du konverterar Word-dokument till Markdown med Aspose.Words för Java. Den här steg-för-steg-guiden täcker tabelljustering, bildhantering och mer.
weight: 18
url: /sv/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som Markdown i Aspose.Words för Java


## Introduktion till att spara dokument som Markdown i Aspose.Words för Java

I denna steg-för-steg-guide kommer vi att visa hur man sparar dokument som Markdown med Aspose.Words för Java. Markdown är ett lättviktigt märkningsspråk som vanligtvis används för att formatera textdokument. Med Aspose.Words för Java kan du enkelt konvertera dina Word-dokument till Markdown-format. Vi kommer att täcka olika aspekter av att spara Markdown-filer, inklusive justering av tabellinnehåll och hantering av bilder.

## Förutsättningar

Innan du börjar, se till att du har följande förutsättningar:

- Java Development Kit (JDK) installerat på ditt system.
-  Aspose.Words för Java-bibliotek. Du kan ladda ner den från[här](https://releases.aspose.com/words/java/).

## Steg 1: Skapa ett Word-dokument

Låt oss börja med att skapa ett Word-dokument som vi senare kommer att konvertera till Markdown-format. Du kan anpassa detta dokument enligt dina krav.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en tabell med två celler
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Spara dokumentet som Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 I det här exemplet skapar vi en enkel tabell med två celler och ställer in justeringen av styckena i dessa celler. Sedan sparar vi dokumentet som Markdown med hjälp av`MarkdownSaveOptions`.

## Steg 2: Anpassa justering av tabellinnehåll

Aspose.Words för Java låter dig anpassa justeringen av tabellinnehåll när du sparar som Markdown. Du kan justera tabellinnehållet till vänster, höger, centrera eller låta det bestämmas automatiskt baserat på det första stycket i varje tabellkolumn.

Så här anpassar du justering av tabellinnehåll:

```java
// Ställ in tabellinnehållsjusteringen till vänster
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Ställ tabellinnehållsjusteringen till höger
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Ställ in justeringen av tabellinnehållet till mitten
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Ställ in justering av tabellinnehåll till auto (bestäms av första stycket)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Genom att ändra`TableContentAlignment` egenskap, kan du styra hur innehållet i tabeller justeras när du konverterar till Markdown.

## Steg 3: Hantera bilder

 För att inkludera bilder i ditt Markdown-dokument måste du ange mappen där bilderna finns. Aspose.Words för Java låter dig ställa in bildmappen i`MarkdownSaveOptions`.

Så här ställer du in bildmappen och sparar dokumentet med bilder:

```java
// Ladda ett dokument som innehåller bilder
Document doc = new Document("document_with_images.docx");

// Ställ in bildmappens sökväg
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Spara dokumentet med bilder
doc.save("document_with_images.md", saveOptions);
```

 Se till att byta ut`"document_with_images.docx"` med sökvägen till ditt Word-dokument som innehåller bilder och`"images_folder/"` med den faktiska sökvägen till mappen där dina bilder lagras.

## Komplett källkod för att spara dokument som Markdown i Aspose.Words för Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Gör att alla stycken i tabellen justeras.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Justeringen i detta fall kommer att tas från första stycket i motsvarande tabellkolumn.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Slutsats

den här guiden har vi utforskat hur man sparar dokument som Markdown med Aspose.Words för Java. Vi täckte skapandet av ett Word-dokument, anpassning av tabellinnehållsjustering och hantering av bilder i Markdown-filer. Du kan nu effektivt konvertera dina Word-dokument till Markdown-format, vilket gör dem lämpliga för olika publiceringsplattformar och dokumentationsbehov.

## FAQ's

### Hur installerar jag Aspose.Words för Java?

 Aspose.Words för Java kan installeras genom att inkludera biblioteket i ditt Java-projekt. Du kan ladda ner biblioteket från[här](https://releases.aspose.com/words/java/) och följ installationsinstruktionerna i dokumentationen.

### Kan jag konvertera komplexa Word-dokument med tabeller och bilder till Markdown?

Ja, Aspose.Words för Java stöder konvertering av komplexa Word-dokument med tabeller, bilder och olika formateringselement till Markdown. Du kan anpassa Markdown-utdata efter ditt dokuments komplexitet.

### Hur kan jag hantera bilder i Markdown-filer?

 För att inkludera bilder i Markdown-filer, ställ in bildmappens sökväg med hjälp av`setImagesFolder`metod i`MarkdownSaveOptions`. Se till att bildfilerna lagras i den angivna mappen, och Aspose.Words för Java kommer att hantera bildreferenserna därefter.

### Finns det en testversion av Aspose.Words för Java tillgänglig?

Ja, du kan få en testversion av Aspose.Words för Java från Asposes webbplats. Testversionen låter dig utvärdera bibliotekets kapacitet innan du köper en licens.

### Var kan jag hitta fler exempel och dokumentation?

 För mer exempel, dokumentation och detaljerad information om Aspose.Words för Java, vänligen besök[dokumentation](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
