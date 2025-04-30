---
"description": "Lär dig hur du sparar dokument som textfiler i Aspose.Words för Java. Följ vår steg-för-steg-guide med Java-kodexempel."
"linktitle": "Spara dokument som textfiler"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Spara dokument som textfiler i Aspose.Words för Java"
"url": "/sv/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som textfiler i Aspose.Words för Java


## Introduktion till att spara dokument som textfiler i Aspose.Words för Java

den här handledningen ska vi utforska hur man sparar dokument som textfiler med hjälp av Aspose.Words för Java-biblioteket. Aspose.Words är ett kraftfullt Java API för att arbeta med Word-dokument, och det erbjuder olika alternativ för att spara dokument i olika format, inklusive vanlig text. Vi kommer att gå igenom stegen för att uppnå detta och ge exempel på Java-kod längs vägen.

## Förkunskapskrav

Innan vi börjar, se till att du har följande förutsättningar på plats:

- Java Development Kit (JDK) installerat på ditt system.
- Aspose.Words för Java-biblioteket är integrerat i ditt projekt. Du kan ladda ner det från [här](https://releases.aspose.com/words/java/).
- Grundläggande kunskaper i Java-programmering.

## Steg 1: Skapa ett dokument

För att spara ett dokument som en textfil måste vi först skapa ett dokument med Aspose.Words. Här är ett enkelt Java-kodavsnitt för att skapa ett dokument med lite innehåll:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

I den här koden skapar vi ett nytt dokument och lägger till text i det, inklusive text på olika språk.

## Steg 2: Definiera alternativ för att spara text

Nästa steg är att definiera alternativen för att spara text som anger hur dokumentet ska sparas som en textfil. Vi kan konfigurera olika inställningar, till exempel att lägga till bidi-markeringar, listindrag med mera. Låt oss titta på två exempel:

### Exempel 1: Lägga till bidi-märken

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

I det här exemplet skapar vi en `TxtSaveOptions` objektet och ställ in `AddBidiMarks` egendom till `true` för att inkludera bidi-tecken i textutdata.

### Exempel 2: Använda tabbtecken för listindrag

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Här konfigurerar vi sparalternativen för att använda ett tabbtecken för listindrag med ett antal på 1.

## Steg 3: Spara dokumentet som text

Nu när vi har definierat alternativen för att spara text kan vi spara dokumentet som en textfil. Följande kod visar hur man gör detta:

```java
doc.save("output.txt", saveOptions);
```

Ersätta `"output.txt"` med önskad sökväg där du vill spara textfilen.

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
        // Skapa en lista med tre nivåer av indentering.
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
        // Skapa en lista med tre nivåer av indentering.
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

I den här handledningen har vi lärt oss hur man sparar dokument som textfiler i Aspose.Words för Java. Vi har gått igenom stegen för att skapa ett dokument, definiera alternativ för att spara text och spara dokumentet i textformat. Aspose.Words ger stor flexibilitet när det gäller att spara dokument, vilket gör att du kan skräddarsy resultatet efter dina specifika behov.

## Vanliga frågor

### Hur lägger jag till bidi-markeringar i textutdata?

För att lägga till bidi-markeringar i textutdata, ställ in `AddBidiMarks` egendom av `TxtSaveOptions` till `true`Till exempel:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Kan jag anpassa listans indenteringstecken?

Ja, du kan anpassa listans indragningstecken genom att konfigurera `ListIndentation` egendom av `TxtSaveOptions`Om du till exempel vill använda ett tabbtecken för listindrag kan du göra följande:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Är Aspose.Words för Java lämpligt för att hantera flerspråkig text?

Ja, Aspose.Words för Java är lämpligt för att hantera flerspråkig text. Det stöder olika språk och teckenkodningar, vilket gör det till ett mångsidigt val för att arbeta med dokument på olika språk.

### Hur kan jag få tillgång till mer dokumentation och resurser för Aspose.Words för Java?

Du hittar omfattande dokumentation och resurser för Aspose.Words för Java på Asposes dokumentationswebbplats: [Aspose.Words för Java-dokumentation](https://reference.aspose.com/words/java/).

### Var kan jag ladda ner Aspose.Words för Java?

Du kan ladda ner Aspose.Words för Java-biblioteket från Asposes webbplats: [Ladda ner Aspose.Words för Java](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}