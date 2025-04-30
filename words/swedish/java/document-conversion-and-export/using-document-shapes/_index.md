---
"description": "Lås upp kraften i dokumentformer i Aspose.Words för Java. Lär dig skapa visuellt engagerande dokument med steg-för-steg-exempel."
"linktitle": "Använda dokumentformer"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda dokumentformer i Aspose.Words för Java"
"url": "/sv/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda dokumentformer i Aspose.Words för Java


## Introduktion till användning av dokumentformer i Aspose.Words för Java

den här omfattande guiden fördjupar vi oss i dokumentformernas värld i Aspose.Words för Java. Former är viktiga element när det gäller att skapa visuellt tilltalande och interaktiva dokument. Oavsett om du behöver lägga till callouts, knappar, bilder eller vattenstämplar, tillhandahåller Aspose.Words för Java verktygen för att göra det effektivt. Låt oss utforska hur man använder dessa former steg för steg med källkodsexempel.

## Komma igång med dokumentformer

Innan vi går in i koden, låt oss konfigurera vår miljö. Se till att du har Aspose.Words för Java integrerat i ditt projekt. Om du inte redan har gjort det kan du ladda ner det från Asposes webbplats. [Ladda ner Aspose.Words för Java](https://releases.aspose.com/words/java/)

## Lägga till former i dokument

### Infoga en gruppform

En `GroupShape` låter dig gruppera flera former tillsammans. Så här skapar och infogar du en `GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### Infoga en textruteform

För att infoga en textruteform kan du använda `insertShape` metod som visas i exemplet nedan:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Manipulera formegenskaper

### Hantera bildförhållande

Du kan styra om bildförhållandet för en form är låst eller inte. Så här låser du upp bildförhållandet för en form:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Placera en form i en tabellcell

Om du behöver placera en form inuti en tabellcell kan du göra detta med följande kod:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Visa formen utanför tabellcellen om den ska placeras i en cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Arbeta med SmartArt-former

### Identifiera SmartArt-former

Du kan identifiera SmartArt-former i ett dokument med hjälp av följande kod:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Uppdaterar SmartArt-teckningar

För att uppdatera SmartArt-teckningar i ett dokument, använd följande kod:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Slutsats

I den här guiden har vi utforskat dokumentformernas värld i Aspose.Words för Java. Du har lärt dig hur du lägger till olika former i dina dokument, manipulerar deras egenskaper och arbetar med SmartArt-former. Med denna kunskap kan du enkelt skapa visuellt tilltalande och interaktiva dokument.

## Vanliga frågor

### Vad är Aspose.Words för Java?

Aspose.Words för Java är ett Java-bibliotek som låter utvecklare skapa, modifiera och konvertera Word-dokument programmatiskt. Det erbjuder ett brett utbud av funktioner och verktyg för att arbeta med dokument i olika format.

### Hur kan jag ladda ner Aspose.Words för Java?

Du kan ladda ner Aspose.Words för Java från Asposes webbplats genom att följa den här länken: [Ladda ner Aspose.Words för Java](https://releases.aspose.com/words/java/)

### Vilka är fördelarna med att använda dokumentformer?

Dokumentformer lägger till visuella element och interaktivitet i dina dokument, vilket gör dem mer engagerande och informativa. Med former kan du skapa bildtexter, knappar, bilder, vattenstämplar och mer, vilket förbättrar den övergripande användarupplevelsen.

### Kan jag anpassa utseendet på former?

Ja, du kan anpassa utseendet på former genom att justera deras egenskaper som storlek, position, rotation och fyllningsfärg. Aspose.Words för Java erbjuder omfattande alternativ för anpassning av former.

### Är Aspose.Words för Java kompatibelt med SmartArt?

Ja, Aspose.Words för Java stöder SmartArt-former, vilket gör att du kan arbeta med komplexa diagram och grafik i dina dokument.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}