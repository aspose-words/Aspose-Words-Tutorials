---
date: 2025-12-22
description: Lär dig hur du exporterar markdown genom att konvertera Word‑dokument
  till Markdown med Aspose.Words för Java. Denna steg‑för‑steg‑guide täcker tabelljustering,
  bildhantering och mer.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Hur man exporterar Markdown med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Så exporterar du Markdown med Aspose.Words för Java

## Introduktion till export av Markdown i Aspose.Words för Java

I den här steg‑för‑steg‑handledningen **kommer du att lära dig hur du exporterar markdown** från Word‑dokument med hjälp av Aspose.Words för Java. Markdown är ett lättviktigt markeringsspråk som är perfekt för dokumentation, statiska webbplatsgeneratorer och många publiceringsplattformar. I slutet av guiden kommer du att kunna **konvertera Word till markdown**, anpassa tabelljustering och **hantera bilder i markdown** utan ansträngning.

## Snabba svar
- **Vad är den primära klassen för att spara som Markdown?** `MarkdownSaveOptions`
- **Kan bilder bäddas in automatiskt?** Ja – ange bildmappen via `setImagesFolder`.
- **Hur styr jag tabelljustering?** Använd `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Vad är minimikraven?** JDK 8+ och Aspose.Words för Java‑biblioteket.
- **Finns en provversion tillgänglig?** Ja, ladda ner den från Aspose‑webbplatsen.

## Vad är “hur man exporterar markdown”?
Att exportera markdown innebär att ta ett rik‑text Word‑dokument (`.docx`) och skapa en ren‑text `.md`‑fil som bevarar rubriker, tabeller och bilder i Markdown‑syntax.

## Varför använda Aspose.Words för Java för att konvertera docx med bilder?
Aspose.Words hanterar komplexa layouter, inbäddade bilder och tabellstrukturer utan att förlora kvalitet. Det ger dig också fin‑granulär kontroll över Markdown‑utdata, såsom tabelljustering och hantering av bildmapp.

## Förutsättningar

- Java Development Kit (JDK) installerat på ditt system.
- Aspose.Words för Java‑biblioteket. Du kan ladda ner det från [here](https://releases.aspose.com/words/java/).

## Steg 1: Skapa ett enkelt Word‑dokument

Först bygger vi ett litet dokument som innehåller en tabell. Detta låter oss demonstrera **anpassa tabelljustering** senare.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

I kodsnutten ovan gör vi:

1. Skapa ett nytt `Document`.
2. Använd `DocumentBuilder` för att infoga en två‑celler‑tabell.
3. Applicera **right** och **center** styckejustering i varje cell.
4. Spara filen som Markdown med `MarkdownSaveOptions`.

## Steg 2: Anpassa tabellinnehållsjustering

Aspose.Words låter dig bestämma hur tabellceller renderas i den slutgiltiga Markdown‑filen. Du kan tvinga vänster-, höger- eller centerjustering, eller låta biblioteket bestämma automatiskt baserat på det första stycket i varje kolumn.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Genom att byta `TableContentAlignment`‑egenskapen styr du **anpassa tabelljustering** för Markdown‑utdata.

## Steg 3: Hantera bilder vid export till markdown

När ett dokument innehåller bilder vill du att dessa bilder ska visas korrekt i den genererade `.md`‑filen. Ange den mapp där Aspose.Words ska lagra de extraherade bilderna.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Byt ut `"document_with_images.docx"` mot sökvägen till din källfil och `"images_folder/"` mot den plats där du vill lagra bilderna. Den resulterande Markdown‑filen kommer att innehålla bildlänkar som pekar på denna mapp, vilket gör att du kan **hantera bilder i markdown** sömlöst.

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## Vanliga problem och lösningar

| Problem | Lösning |
|---------|----------|
| Bilder visas inte i `.md`‑filen | Verifiera att `setImagesFolder` pekar på en skrivbar katalog och att mappen refereras korrekt i den genererade Markdown‑filen. |
| Tabelljustering ser felaktig ut | Använd `TableContentAlignment.AUTO` för att låta Aspose.Words avgöra den bästa justeringen baserat på det första stycket i varje kolumn. |
| Utdatafilen är tom | Se till att `Document`‑objektet faktiskt innehåller innehåll innan du anropar `save`. |

## Vanliga frågor

**Q: Hur installerar jag Aspose.Words för Java?**  
A: Aspose.Words för Java kan installeras genom att inkludera biblioteket i ditt Java‑projekt. Du kan ladda ner biblioteket från [here](https://releases.aspose.com/words/java/) och följa installationsinstruktionerna som finns i dokumentationen.

**Q: Kan jag konvertera komplexa Word‑dokument med tabeller och bilder till Markdown?**  
A: Ja, Aspose.Words för Java stödjer konvertering av komplexa Word‑dokument med tabeller, bilder och olika formateringselement till Markdown. Du kan anpassa Markdown‑utdata enligt ditt dokuments komplexitet.

**Q: Hur kan jag hantera bilder i Markdown‑filer?**  
A: Ange bildmappens sökväg med `setImagesFolder`‑metoden i `MarkdownSaveOptions`. Se till att bildfilerna lagras i den angivna mappen; Aspose.Words kommer att generera lämpliga Markdown‑bildlänkar.

**Q: Finns en provversion av Aspose.Words för Java tillgänglig?**  
A: Ja, du kan få en provversion av Aspose.Words för Java från Aspose‑webbplatsen. Provversionen låter dig utvärdera bibliotekets funktioner innan du köper en licens.

**Q: Var kan jag hitta fler exempel och dokumentation?**  
A: För fler exempel, dokumentation och detaljerad information om Aspose.Words för Java, besök gärna [documentation](https://reference.aspose.com/words/java/).

---

**Senast uppdaterad:** 2025-12-22  
**Testat med:** Aspose.Words för Java 24.12 (senaste vid skrivtillfället)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}