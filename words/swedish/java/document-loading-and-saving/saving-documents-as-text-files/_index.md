---
title: Spara dokument som textfiler i Aspose.Words för Java
linktitle: Spara dokument som textfiler
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du sparar dokument som textfiler i Aspose.Words för Java. Följ vår steg-för-steg-guide med exempel på Java-kod.
weight: 24
url: /sv/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som textfiler i Aspose.Words för Java


## Introduktion till att spara dokument som textfiler i Aspose.Words för Java

I den här handledningen kommer vi att utforska hur man sparar dokument som textfiler med Aspose.Words för Java-biblioteket. Aspose.Words är ett kraftfullt Java API för att arbeta med Word-dokument, och det ger olika alternativ för att spara dokument i olika format, inklusive vanlig text. Vi kommer att täcka stegen för att uppnå detta och tillhandahålla exempel på Java-kod längs vägen.

## Förutsättningar

Innan vi börjar, se till att du har följande förutsättningar på plats:

- Java Development Kit (JDK) installerat på ditt system.
-  Aspose.Words för Java-bibliotek integrerat i ditt projekt. Du kan ladda ner den från[här](https://releases.aspose.com/words/java/).
- Grundläggande kunskaper i Java-programmering.

## Steg 1: Skapa ett dokument

För att spara ett dokument som en textfil måste vi först skapa ett dokument med Aspose.Words. Här är ett enkelt Java-kodavsnitt för att skapa ett dokument med visst innehåll:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

den här koden skapar vi ett nytt dokument och lägger till lite text till det, inklusive text på olika språk.

## Steg 2: Definiera textsparaalternativ

Därefter måste vi definiera textsparalternativen som anger hur dokumentet ska sparas som en textfil. Vi kan konfigurera olika inställningar som att lägga till bidi-märken, listindrag och mer. Låt oss titta på två exempel:

### Exempel 1: Lägga till Bidi-märken

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 I det här exemplet skapar vi en`TxtSaveOptions` objekt och ställ in`AddBidiMarks`egendom till`true` för att inkludera bidi-märken i textutmatningen.

### Exempel 2: Använda tabbtecken för listindrag

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Här konfigurerar vi sparalternativen för att använda ett tabbtecken för listindrag med ett antal 1.

## Steg 3: Spara dokumentet som text

Nu när vi har definierat textsparalternativen kan vi spara dokumentet som en textfil. Följande kod visar hur du gör detta:

```java
doc.save("output.txt", saveOptions);
```

 Ersätta`"output.txt"` med önskad sökväg där du vill spara textfilen.

## Komplett källkod för att spara dokument som textfiler i Aspose.Words för Java

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
        // Skapa en lista med tre nivåer av indrag.
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
        // Skapa en lista med tre nivåer av indrag.
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

## Slutsats

I den här handledningen har vi lärt oss hur man sparar dokument som textfiler i Aspose.Words för Java. Vi gick igenom stegen för att skapa ett dokument, definiera textsparalternativ och spara dokumentet i textformat. Aspose.Words ger omfattande flexibilitet när det gäller att spara dokument, vilket gör att du kan skräddarsy utskriften efter dina specifika krav.

## FAQ's

### Hur lägger jag till bidi-märken i textutmatningen?

 För att lägga till bidi-märken till textutmatningen, ställ in`AddBidiMarks` egendom av`TxtSaveOptions` till`true`. Till exempel:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Kan jag anpassa listans indrag?

 Ja, du kan anpassa listans indragstecken genom att konfigurera`ListIndentation` egendom av`TxtSaveOptions`. Om du till exempel vill använda ett tabbtecken för indrag i listan kan du göra följande:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Är Aspose.Words för Java lämplig för hantering av flerspråkig text?

Ja, Aspose.Words för Java är lämplig för hantering av flerspråkig text. Den stöder olika språk och teckenkodningar, vilket gör den till ett mångsidigt val för att arbeta med dokument på olika språk.

### Hur får jag tillgång till mer dokumentation och resurser för Aspose.Words för Java?

 Du kan hitta omfattande dokumentation och resurser för Aspose.Words för Java på Aspose-dokumentationswebbplatsen:[Aspose.Words för Java-dokumentation](https://reference.aspose.com/words/java/).

### Var kan jag ladda ner Aspose.Words för Java?

 Du kan ladda ner Aspose.Words for Java-biblioteket från Asposes webbplats:[Ladda ner Aspose.Words för Java](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
