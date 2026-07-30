---
date: 2025-12-24
description: Lär dig hur du skapar en ren textfil från Word‑dokument med Aspose.Words
  för Java. Den här guiden visar hur du konverterar Word till txt, använder tabbindrag
  och sparar Word som txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Hur man skapar en vanlig textfil med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to create plain text file with Aspose.Words for Java

## Introduction to Saving Documents as Text Files in Aspose.Words for Java

I den här handledningen kommer du att lära dig **hur man skapar en vanlig textfil** från ett Word-dokument med hjälp av Aspose.Words för Java-biblioteket. Oavsett om du behöver **konvertera word till txt**, automatisera rapportgenerering, eller helt enkelt extrahera råtext för vidare bearbetning, så guidar den här guiden dig genom hela arbetsflödet—från dokumentskapande till finjustering av sparalternativ som **använd tab-indentering** eller lägga till bidi-märken. Låt oss börja!

## Quick Answers

- **Vad är den primära klassen för att skapa ett dokument?** `Document` från Aspose.Words.
- **Vilket alternativ lägger till bidi-märken för språk som skrivs från höger till vänster?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Hur kan jag indentera listobjekt med tabbar?** Sätt `ListIndentation.Character` till `'\t'`.
- **Behöver jag en licens för utveckling?** En gratis provversion fungerar för testning; en licens krävs för produktion.
- **Kan jag spara filen med ett eget namn och sökväg?** Ja—skicka hela sökvägen till `doc.save()`.

## Prerequisites

Innan vi börjar, se till att du har följande förutsättningar på plats:

- Java Development Kit (JDK) installerat på ditt system.  
- Aspose.Words för Java-biblioteket integrerat i ditt projekt. Du kan ladda ner det från [here](https://releases.aspose.com/words/java/).  
- Grundläggande kunskaper i Java-programmering.

## Step 1: Create a Document

För att **spara word som txt**, behöver vi först en `Document`-instans. Nedan är ett enkelt Java‑exempel som skapar ett dokument och skriver några rader med flerspråkig text:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

I den här koden skapar vi ett nytt dokument, lägger till engelsk, hebreisk och arabisk text, och aktiverar höger‑till‑vänster‑formatering för det hebreiska stycket.

## Step 2: Define Text Save Options

Därefter konfigurerar vi hur dokumentet ska sparas som en vanlig textfil. Aspose.Words tillhandahåller klassen `TxtSaveOptions`, som låter dig styra allt från bidi-märken till listindentering.

### Example 1: Adding Bidi Marks (how to save txt with proper RTL support)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Att sätta `AddBidiMarks` till `true` säkerställer att höger‑till‑vänster‑tecken representeras korrekt i den resulterande **vanliga textfilen**.

### Example 2: Using Tab Character for List Indentation (use tab indentation)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Här instruerar vi Aspose.Words att lägga till ett tab‑tecken (`'\t'`) före varje listnivå, vilket gör textutdata lättare att läsa.

## Step 3: Save the Document as Text

Nu när sparalternativen är klara kan du spara dokumentet som en **vanlig textfil**:

```java
doc.save("output.txt", saveOptions);
```

Byt ut `"output.txt"` mot den fullständiga sökvägen där du vill lagra filen.

## Complete Source Code For Saving Documents as Text Files in Aspose.Words for Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Common Issues and Solutions

| Issue | Solution |
|-------|----------|
| **Bidi-tecken visas som förvrängd text** | Se till att `setAddBidiMarks(true)` är aktiverat och att utdatafilen öppnas med UTF‑8‑kodning. |
| **Listindentering ser felaktig ut** | Verifiera att `ListIndentation.Count` och `Character` är inställda på önskade värden (tab `'\t'` eller mellanslag `' '` ). |
| **Filen skapades inte** | Kontrollera att katalogsökvägen finns och att applikationen har skrivrättigheter. |

## Frequently Asked Questions

### How do I add bidi marks to the text output?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Can I customize the list indentation character?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Is Aspose.Words for Java suitable for handling multilingual text?

Ja, Aspose.Words för Java stöder ett brett spektrum av språk och teckenkodningar, vilket gör det idealiskt för att extrahera och spara flerspråkigt innehåll som vanlig text.

### How can I access more documentation and resources for Aspose.Words for Java?

Du kan hitta omfattande dokumentation och resurser på Aspose.Words för Java-dokumentationssidan: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Where can I download Aspose.Words for Java?

Du kan ladda ner biblioteket från den officiella webbplatsen: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### What if I need to **convert word to txt** in a batch process?

Vad händer om jag behöver **konvertera word till txt** i en batch‑process? Placera koden ovan i en loop som laddar varje `.docx`‑fil, tillämpar samma `TxtSaveOptions` och sparar varje som `.txt`. Se till att hantera resurser genom att avyttra `Document`‑objekt efter varje iteration.

### Does the API support saving directly to a stream instead of a file?

Stöder API:et att spara direkt till en ström istället för en fil? Ja, du kan skicka en `OutputStream` till `doc.save(outputStream, saveOptions)` för minnesbaserad bearbetning eller när du integrerar med webbtjänster.

---

**Last Updated:** 2025-12-24  
**Tested With:** Aspose.Words for Java 24.12 (senaste)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}