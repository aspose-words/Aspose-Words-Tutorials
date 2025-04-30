---
"description": "Lär dig hur du enkelt extraherar innehåll från dokument med Aspose.Words för Java. Vår steg-för-steg-guide och kodexempel förenklar processen."
"linktitle": "Extrahera innehåll från dokument"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Extrahera innehåll från dokument i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Extrahera innehåll från dokument i Aspose.Words för Java


## Introduktion till att extrahera innehåll från dokument i Aspose.Words för Java

dokumentbehandlingens värld är det vanligt att extrahera innehåll från dokument. Oavsett om du behöver extrahera text, tabeller, bilder eller specifika dokumentelement, erbjuder Aspose.Words för Java kraftfulla verktyg för att göra denna uppgift till en barnlek. I den här omfattande guiden guidar vi dig genom processen att extrahera innehåll från dokument med Aspose.Words för Java. 

## Förkunskapskrav

Innan vi går in i extraktionsprocessen, se till att du har följande förutsättningar på plats:

1. Aspose.Words för Java: Du bör ha Aspose.Words för Java installerat och konfigurerat i din Java-utvecklingsmiljö. Du kan ladda ner det från [här](https://releases.aspose.com/words/java/).

2. Ett dokument att extrahera innehåll från: I den här guiden använder vi ett exempeldokument med namnet "Extract content.docx". Se till att du har ett liknande dokument redo för extraktion.

## Extrahera innehåll mellan blocknivånoder

```java
// Java-kodexempel för att extrahera innehåll mellan blocknivånoder
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getLastSection().getChild(NodeType.PARAGRAPH, 2, true);
Table endTable = (Table) doc.getLastSection().getChild(NodeType.TABLE, 0, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endTable, true);
Collections.reverse(extractedNodes);
while (extractedNodes.size() > 0) {
    endTable.getParentNode().insertAfter((Node) extractedNodes.get(0), endTable);
    extractedNodes.remove(0);
}
doc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBlockLevelNodes.docx");
```

## Extrahera innehåll mellan bokmärken

```java
// Java-kodexempel för att extrahera innehåll mellan bokmärken
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("Bookmark1");
BookmarkStart bookmarkStart = bookmark.getBookmarkStart();
BookmarkEnd bookmarkEnd = bookmark.getBookmarkEnd();
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.IncludingBookmark.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.WithoutBookmark.docx");
```

## Extrahera innehåll mellan kommentarintervall

```java
// Java-kodexempel för att extrahera innehåll mellan kommentarintervall
Document doc = new Document("Your Directory Path" + "Extract content.docx");
CommentRangeStart commentStart = (CommentRangeStart) doc.getChild(NodeType.COMMENT_RANGE_START, 0, true);
CommentRangeEnd commentEnd = (CommentRangeEnd) doc.getChild(NodeType.COMMENT_RANGE_END, 0, true);
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.IncludingComment.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.WithoutComment.docx");
```

## Extrahera innehåll mellan stycken

```java
// Java-kodexempel för att extrahera innehåll mellan stycken
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Extrahera innehåll mellan styckeformat

```java
// Java-kodexempel för att extrahera innehåll mellan styckeformat
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Extrahera innehåll mellan körningar

```java
// Java-kodexempel för att extrahera innehåll mellan körningar
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Extrahera innehåll med DocumentVisitor

```java
// Java-kodexempel för att extrahera innehåll med DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Extrahera innehåll med hjälp av fält

```java
// Java-kodexempel för att extrahera innehåll med hjälp av Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Extraherar innehållsförteckning

```java
// Java-kodexempel för att extrahera innehållsförteckning
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
for (Field field : doc.getRange().getFields()) {
    if (field.getType() == FieldType.FIELD_HYPERLINK) {
        FieldHyperlink hyperlink = (FieldHyperlink) field;
        if (hyperlink.getSubAddress() != null && hyperlink.getSubAddress().startsWith("_Toc")) {
            Paragraph tocItem = (Paragraph) field.getStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(tocItem.toString().trim());
            System.out.println("------------------");
            Bookmark bm = doc.getRange().getBookmarks().get(hyperlink.getSubAddress());
            Paragraph pointer = (Paragraph) bm.getBookmarkStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(pointer.toString());
        }
    }
}
```

## Extrahera endast text

```java
// Java-kodexempel för att endast extrahera text
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Extrahera innehåll baserat på stilar

```java
// Java-kodexempel för att extrahera innehåll baserat på stilar
Document doc = new Document("Your Directory Path" + "Styles.docx");
final String PARA_STYLE = "Heading 1";
final String RUN_STYLE = "Intense Emphasis";
ArrayList<Paragraph> paragraphs = paragraphsByStyleName(doc, PARA_STYLE);
System.out.println("Paragraphs with \"{paraStyle}\" styles ({paragraphs.Count}):");
for (Paragraph paragraph : paragraphs)
    System.out.println(paragraph.toString(SaveFormat.TEXT));
ArrayList<Run> runs = runsByStyleName(doc, RUN_STYLE);
System.out.println("\nRuns with \"{runStyle}\" styles ({runs.Count}):");
for (Run run : runs)
    System.out.println(run.getRange().getText());
}

public ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}

public ArrayList<Run> runsByStyleName(Document doc, String styleName) {
    ArrayList<Run> runsWithStyle = new ArrayList<Run>();
    NodeCollection runs = doc.getChildNodes(NodeType.RUN, true);
    for (Run run : (Iterable<Run>) runs) {
        if (run.getFont().getStyle().getName().equals(styleName))
            runsWithStyle.add(run);
    }
    return runsWithStyle;
}
```

## Extrahera och skriva ut text

```java
// Java-kodexempel för att extrahera och skriva ut text
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Extrahera bilder till filer

```java
// Java-kodexempel för att extrahera bilder till filer
Document doc = new Document("Your Directory Path" + "Images.docx");
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = MessageFormat.format("Image.ExportImages.{0}_{1}",
                imageIndex, FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType()));
        shape.getImageData().save("Your Directory Path" + imageFileName);
        imageIndex++;
    }
}
```

## Slutsats

Grattis! Du har lärt dig hur man extraherar innehåll från dokument med Aspose.Words för Java. Den här guiden behandlade olika extraktionstekniker, inklusive innehåll mellan blocknivånoder, bokmärken, kommentarintervall, stycken och mer. Du är nu utrustad för att hantera extraktion av dokumentinnehåll effektivt i dina Java-applikationer.

## Vanliga frågor

### Hur extraherar jag innehåll från specifika dokumentavsnitt?

För att extrahera innehåll från specifika dokumentavsnitt kan du identifiera start- och slutpunkterna för avsnitten och använda lämpliga Aspose.Words för Java-metoder för att extrahera innehåll mellan dem.

### Kan jag extrahera innehåll från lösenordsskyddade dokument?

Ja, Aspose.Words för Java erbjuder funktioner för att extrahera innehåll från lösenordsskyddade dokument. Du kan ange lösenordet när du öppnar dokumentet med hjälp av `Document` klasskonstruktor.

### Hur kan jag extrahera innehåll och spara det i olika format, till exempel vanlig text eller HTML?

Du kan extrahera innehåll från ett dokument och spara det i olika format med hjälp av Aspose.Words för Java. Efter att du har extraherat innehållet kan du använda `Document` klassmetoder för att spara den i format som vanlig text, HTML eller andra.

### Finns det ett sätt att extrahera innehåll från specifika dokumentelement, till exempel tabeller eller bilder?

Ja, du kan extrahera innehåll från specifika dokumentelement, till exempel tabeller eller bilder, med hjälp av Aspose.Words för Java. Identifiera de element du vill extrahera och använd sedan lämpliga metoder för att extrahera deras innehåll.

### Hur kan jag automatisera innehållsutvinningsprocessen i mitt Java-program?

För att automatisera innehållsextraheringsprocessen i ditt Java-program kan du skapa anpassad kod baserat på teknikerna som beskrivs i den här guiden. Du kan också implementera logik för att iterera genom flera dokument och extrahera innehåll efter behov.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}