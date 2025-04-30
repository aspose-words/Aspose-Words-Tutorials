---
"description": "Leer hoe je eenvoudig inhoud uit documenten kunt halen met Aspose.Words voor Java. Onze stapsgewijze handleiding en codevoorbeelden vereenvoudigen het proces."
"linktitle": "Inhoud uit documenten extraheren"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Inhoud uit documenten extraheren in Aspose.Words voor Java"
"url": "/nl/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inhoud uit documenten extraheren in Aspose.Words voor Java


## Inleiding tot het extraheren van inhoud uit documenten in Aspose.Words voor Java

In de wereld van documentverwerking is het extraheren van inhoud uit documenten een veelvoorkomende vereiste. Of u nu tekst, tabellen, afbeeldingen of specifieke documentelementen wilt extraheren, Aspose.Words voor Java biedt krachtige tools om deze taak een fluitje van een cent te maken. In deze uitgebreide handleiding leiden we u door het proces van het extraheren van inhoud uit documenten met Aspose.Words voor Java. 

## Vereisten

Voordat we aan het extractieproces beginnen, moet u ervoor zorgen dat u aan de volgende voorwaarden voldoet:

1. Aspose.Words voor Java: Aspose.Words voor Java moet geïnstalleerd en ingesteld zijn in uw Java-ontwikkelomgeving. U kunt het downloaden van [hier](https://releases.aspose.com/words/java/).

2. Een document om inhoud uit te halen: voor deze handleiding gebruiken we een voorbeelddocument met de naam 'Inhoud uitpakken.docx'. Zorg ervoor dat u een soortgelijk document klaar hebt staan om te extraheren.

## Inhoud extraheren tussen knooppunten op blokniveau

```java
// Java-codevoorbeeld voor het extraheren van inhoud tussen knooppunten op blokniveau
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

## Inhoud tussen bladwijzers extraheren

```java
// Java-codevoorbeeld voor het extraheren van inhoud tussen bladwijzers
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

## Inhoud extraheren tussen commentaarbereiken

```java
// Java-codevoorbeeld voor het extraheren van inhoud tussen commentaarbereiken
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

## Inhoud tussen alinea's extraheren

```java
// Java-codevoorbeeld voor het extraheren van inhoud tussen alinea's
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Inhoud extraheren tussen alineastijlen

```java
// Java-codevoorbeeld voor het extraheren van inhoud tussen alinea-stijlen
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Inhoud extraheren tussen runs

```java
// Java-codevoorbeeld voor het extraheren van inhoud tussen uitvoeringen
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Inhoud extraheren met DocumentVisitor

```java
// Java-codevoorbeeld voor het extraheren van inhoud met DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Inhoud extraheren met behulp van veld

```java
// Java-codevoorbeeld voor het extraheren van inhoud met behulp van Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Inhoudsopgave extraheren

```java
// Java-codevoorbeeld voor het extraheren van de inhoudsopgave
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

## Alleen tekst extraheren

```java
// Java-codevoorbeeld voor het extraheren van alleen tekst
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Inhoud extraheren op basis van stijlen

```java
// Java-codevoorbeeld voor het extraheren van inhoud op basis van stijlen
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

## Tekst extraheren en afdrukken

```java
// Java-codevoorbeeld voor het extraheren en afdrukken van tekst
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Afbeeldingen naar bestanden extraheren

```java
// Java-codevoorbeeld voor het extraheren van afbeeldingen naar bestanden
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

## Conclusie

Gefeliciteerd! Je hebt geleerd hoe je inhoud uit documenten kunt extraheren met Aspose.Words voor Java. Deze handleiding behandelde verschillende extractietechnieken, waaronder inhoud tussen knooppunten op blokniveau, bladwijzers, opmerkingenreeksen, alinea's en meer. Je bent nu in staat om de extractie van documentinhoud efficiënt uit te voeren in je Java-applicaties.

## Veelgestelde vragen

### Hoe haal ik inhoud uit specifieke secties van het document?

Als u inhoud uit specifieke documentsecties wilt extraheren, kunt u de begin- en eindpunten van de secties identificeren en de juiste Aspose.Words voor Java-methoden gebruiken om inhoud ertussen te extraheren.

### Kan ik inhoud uit wachtwoordbeveiligde documenten halen?

Ja, Aspose.Words voor Java biedt functionaliteit om inhoud uit wachtwoordbeveiligde documenten te halen. U kunt het wachtwoord opgeven bij het openen van het document met behulp van de `Document` klasseconstructor.

### Hoe kan ik inhoud extraheren en opslaan in verschillende formaten, zoals platte tekst of HTML?

Met Aspose.Words voor Java kunt u inhoud uit een document halen en in verschillende formaten opslaan. Nadat u de inhoud hebt uitgepakt, kunt u de `Document` klassemethoden om het op te slaan in formaten zoals platte tekst, HTML of andere.

### Is er een manier om inhoud uit specifieke documentelementen te halen, zoals tabellen of afbeeldingen?

Ja, u kunt inhoud extraheren uit specifieke documentelementen, zoals tabellen of afbeeldingen, met Aspose.Words voor Java. Identificeer de elementen die u wilt extraheren en gebruik vervolgens de juiste methoden om de inhoud ervan te extraheren.

### Hoe kan ik het proces van inhoudsextractie in mijn Java-applicatie automatiseren?

Om het proces van contentextractie in uw Java-applicatie te automatiseren, kunt u aangepaste code maken op basis van de technieken die in deze handleiding worden beschreven. U kunt ook logica implementeren om door meerdere documenten te itereren en content naar behoefte te extraheren.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}