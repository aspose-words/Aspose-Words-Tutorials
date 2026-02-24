---
date: 2026-02-24
description: Lär dig hur du konverterar Word till Markdown med Aspose.Words för Java.
  Denna guide täcker tabelljustering, bildhantering och hur du sparar dokumentet som
  Markdown.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Konvertera Word till Markdown med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera Word till Markdown med Aspose.Words för Java

## Introduktion till konvertera Word till Markdown med Aspose.Words för Java

I den här steg‑för‑steg‑handledningen kommer du att lära dig **hur du konverterar Word till Markdown** med det kraftfulla Aspose.Words för Java‑API:et. Markdown är ett lättviktigt märkningsspråk som många utvecklare och innehållsplattformar förlitar sig på för ren, läsbar dokumentation. I slutet av guiden kan du ta vilken `.docx`‑fil som helst, bevara tabeller, bilder och formatering, och exportera den som en `.md`‑fil som är klar för statiska webbplatsgeneratorer, GitHub‑README‑filer eller något markdown‑vänligt arbetsflöde.

## Snabba svar
- **Vilket bibliotek behöver jag?** Aspose.Words för Java (`aspose-words.jar`).
- **Kan jag anpassa tabelljustering?** Ja – använd `TableContentAlignment` i `MarkdownSaveOptions`.
- **Hur hanteras bilder?** Ange en bildmapp med `setImagesFolder()`; biblioteket skapar relativa länkar.
- **Behöver jag en licens för produktion?** En kommersiell licens krävs för icke‑testanvändning.
- **Är detta kompatibelt med Java 17?** Ja, biblioteket stöder Java 8 och högre.

## Vad innebär konvertering av Word till Markdown?

Att konvertera Word till Markdown betyder att ta den rika formateringen i ett Microsoft Word‑dokument och översätta den till ren markdown‑syntax. Denna process behåller rubriker, listor, tabeller och bildreferenser samtidigt som binär formatering tas bort, vilket gör innehållet portabelt och versionskontrollvänligt.

## Varför använda Aspose.Words för Java för att spara dokument som markdown?

* **Fullständig trohet** – tabeller, bilder och komplexa layouter bevaras.
* **Finjusterad kontroll** – du kan anpassa tabelljustering, bildvägar och mer.
* **Inga externa beroenden** – biblioteket fungerar direkt utan att Office måste vara installerat.
* **Korsplattform** – fungerar på Windows, Linux och macOS med vilken Java‑runtime som helst.

## Förutsättningar

Innan du börjar, se till att du har:

- Java Development Kit (JDK) installerat på ditt system.
- Aspose.Words för Java‑biblioteket. Du kan ladda ner det [här](https://releases.aspose.com/words/java/).

## Steg‑för‑steg‑guide

### Steg 1: Skapa ett Word‑dokument som ska konverteras

Först bygger vi ett enkelt Word‑dokument som innehåller en två‑cellig tabell. Detta exempel visar hur styckejustering i tabellceller respekteras när vi senare **sparar dokumentet som markdown**.

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

### Steg 2: Anpassa tabellens innehållsjustering

Aspose.Words för Java låter dig styra hur tabellceller justeras i den genererade markdownen. Använd egenskapen `TableContentAlignment` för att **anpassa tabelljustering** till vänster, höger, centrerad, eller låt biblioteket bestämma automatiskt baserat på det första stycket i varje kolumn.

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

Genom att växla denna inställning kan du **exportera Word‑tabeller till markdown** med exakt den justering du behöver för efterföljande renderingsmotorer.

### Steg 3: Hantera bilder under konvertering

När ditt käll‑Word‑dokument innehåller bilder måste du tala om för Aspose.Words var de exporterade bildfilerna ska placeras. Metoden `setImagesFolder` på `MarkdownSaveOptions` definierar den mapp som ska hålla bildresurserna, och markdown‑filen kommer att innehålla relativa länkar till dessa filer.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Byt ut `"document_with_images.docx"` mot sökvägen till din källfil och `"images_folder/"` mot den önskade utmatningsmappen för bilderna.

### Fullständig källkod för alla scenarier

Nedan följer ett samlat exempel som visar hur man **auto‑justerar tabeller**, **anpassar justering** och **anger en bildmapp** i en metod. Detta kodsnutt speglar den ursprungliga handledningens kod och fungerar oförändrad.

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

| Problem | Orsak | Lösning |
|---------|-------|---------|
| Bilder visas som brutna länkar | `setImagesFolder` ej angivet eller felaktig mappväg | Verifiera att mappvägen är korrekt och att mappen är skrivbar |
| Tabelljustering ser felaktig ut | Fel `TableContentAlignment`‑värde | Använd `TableContentAlignment.AUTO` för att låta det första stycket bestämma, eller ange explicit LEFT/RIGHT/CENTER |
| Utdatafil är tom | Spara‑alternativ har inte skickats till `doc.save()` | Säkerställ att du passerar `MarkdownSaveOptions`‑instansen till `save`‑metoden |
| Word‑funktioner stöds ej (t.ex. SmartArt) | Markdown kan inte representera vissa komplexa objekt | Konvertera dessa element till bilder innan du sparar, eller förenkla källdokumentet |

## Vanliga frågor

**Q: Hur installerar jag Aspose.Words för Java?**  
A: Aspose.Words för Java kan installeras genom att inkludera biblioteket i ditt Java‑projekt. Du kan ladda ner biblioteket från [här](https://releases.aspose.com/words/java/) och följa installationsinstruktionerna i dokumentationen.

**Q: Kan jag konvertera komplexa Word‑dokument med tabeller och bilder till Markdown?**  
A: Ja, Aspose.Words för Java stödjer konvertering av komplexa Word‑dokument med tabeller, bilder och olika formateringselement till Markdown. Du kan anpassa Markdown‑utdata enligt ditt dokuments komplexitet.

**Q: Hur hanterar jag bilder i Markdown‑filer?**  
A: För att inkludera bilder i Markdown‑filer, ange bildmappens sökväg med `setImagesFolder`‑metoden i `MarkdownSaveOptions`. Se till att bildfilerna lagras i den angivna mappen, så hanterar Aspose.Words för Java bildreferenserna automatiskt.

**Q: Finns det en provversion av Aspose.Words för Java?**  
A: Ja, du kan skaffa en provversion av Aspose.Words för Java från Aspose‑webbplatsen. Provversionen låter dig utvärdera bibliotekets funktioner innan du köper en licens.

**Q: Var kan jag hitta fler exempel och dokumentation?**  
A: För fler exempel, dokumentation och detaljerad information om Aspose.Words för Java, besök gärna [dokumentationen](https://reference.aspose.com/words/java/).

## Slutsats

I den här guiden har vi gått igenom allt du behöver för att **konvertera Word till Markdown** med Aspose.Words för Java: skapa ett källdokument, **anpassa tabelljustering** och hantera bilder med korrekt mappkonfiguration. Med dessa tekniker kan du på ett pålitligt sätt exportera Word‑innehåll till markdown för bloggar, dokumentationssajter eller någon plattform som använder markdown.

---

**Senast uppdaterad:** 2026-02-24  
**Testad med:** Aspose.Words för Java 24.12 (senaste vid skrivtillfället)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}