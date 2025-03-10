---
title: Extrahieren von Inhalten aus Dokumenten in Aspose.Words für Java
linktitle: Extrahieren von Inhalten aus Dokumenten
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java ganz einfach Inhalte aus Dokumenten extrahieren. Unsere Schritt-für-Schritt-Anleitung und Codebeispiele vereinfachen den Vorgang.
weight: 13
url: /de/java/document-manipulation/extracting-content-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Extrahieren von Inhalten aus Dokumenten in Aspose.Words für Java


## Einführung in das Extrahieren von Inhalten aus Dokumenten in Aspose.Words für Java

In der Welt der Dokumentenverarbeitung ist das Extrahieren von Inhalten aus Dokumenten eine häufige Anforderung. Egal, ob Sie Text, Tabellen, Bilder oder bestimmte Dokumentelemente extrahieren müssen, Aspose.Words für Java bietet leistungsstarke Tools, die diese Aufgabe zum Kinderspiel machen. In dieser umfassenden Anleitung führen wir Sie durch den Prozess des Extrahierens von Inhalten aus Dokumenten mit Aspose.Words für Java. 

## Voraussetzungen

Bevor wir mit dem Extraktionsprozess beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1.  Aspose.Words für Java: Sie sollten Aspose.Words für Java in Ihrer Java-Entwicklungsumgebung installiert und eingerichtet haben. Sie können es herunterladen von[Hier](https://releases.aspose.com/words/java/).

2. Ein Dokument, aus dem Inhalte extrahiert werden: Für diese Anleitung verwenden wir ein Beispieldokument mit dem Namen „Inhalt extrahieren.docx“. Stellen Sie sicher, dass Sie ein ähnliches Dokument zum Extrahieren bereit haben.

## Extrahieren von Inhalten zwischen Knoten auf Blockebene

```java
// Java-Codebeispiel zum Extrahieren von Inhalten zwischen Knoten auf Blockebene
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

## Extrahieren von Inhalten zwischen Lesezeichen

```java
//Java-Codebeispiel zum Extrahieren von Inhalten zwischen Lesezeichen
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

## Extrahieren von Inhalten zwischen Kommentarbereichen

```java
// Java-Codebeispiel zum Extrahieren von Inhalten zwischen Kommentarbereichen
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

## Extrahieren von Inhalten zwischen Absätzen

```java
// Java-Codebeispiel zum Extrahieren von Inhalten zwischen Absätzen
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Extrahieren von Inhalten zwischen Absatzformaten

```java
// Java-Codebeispiel zum Extrahieren von Inhalten zwischen Absatzstilen
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Extrahieren von Inhalten zwischen Ausführungen

```java
// Java-Codebeispiel zum Extrahieren von Inhalten zwischen Ausführungen
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Extrahieren von Inhalten mit DocumentVisitor

```java
// Java-Codebeispiel zum Extrahieren von Inhalten mit DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Extrahieren von Inhalten mithilfe von Feldern

```java
// Java-Codebeispiel zum Extrahieren von Inhalten mit Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Inhaltsverzeichnis extrahieren

```java
// Java-Codebeispiel zum Extrahieren eines Inhaltsverzeichnisses
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

## Nur Text extrahieren

```java
// Java-Codebeispiel zum Extrahieren von reinem Text
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Extrahieren von Inhalten basierend auf Stilen

```java
// Java-Codebeispiel zum Extrahieren von Inhalten basierend auf Stilen
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

## Extrahieren und Drucken von Text

```java
// Java-Codebeispiel zum Extrahieren und Drucken von Text
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Extrahieren von Bildern in Dateien

```java
// Java-Codebeispiel zum Extrahieren von Bildern in Dateien
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

## Abschluss

Herzlichen Glückwunsch! Sie haben gelernt, wie Sie mit Aspose.Words für Java Inhalte aus Dokumenten extrahieren. In diesem Handbuch wurden verschiedene Extraktionstechniken behandelt, darunter Inhalte zwischen Blockknoten, Lesezeichen, Kommentarbereichen, Absätzen und mehr. Sie sind jetzt in der Lage, die Extraktion von Dokumentinhalten in Ihren Java-Anwendungen effizient durchzuführen.

## Häufig gestellte Fragen

### Wie extrahiere ich Inhalte aus bestimmten Dokumentabschnitten?

Um Inhalte aus bestimmten Dokumentabschnitten zu extrahieren, können Sie die Start- und Endpunkte der Abschnitte identifizieren und die entsprechenden Aspose.Words für Java-Methoden verwenden, um Inhalte zwischen ihnen zu extrahieren.

### Kann ich Inhalte aus passwortgeschützten Dokumenten extrahieren?

Ja, Aspose.Words für Java bietet Funktionen zum Extrahieren von Inhalten aus passwortgeschützten Dokumenten. Sie können das Passwort beim Öffnen des Dokuments mithilfe des`Document` Klassenkonstruktor.

### Wie kann ich Inhalte extrahieren und in verschiedenen Formaten speichern, beispielsweise als einfachen Text oder HTML?

 Sie können Inhalte aus einem Dokument extrahieren und in verschiedenen Formaten speichern, indem Sie Aspose.Words für Java verwenden. Nachdem Sie den Inhalt extrahiert haben, können Sie den`Document` Klassenmethoden, um es in Formaten wie reinem Text, HTML oder anderen zu speichern.

### Gibt es eine Möglichkeit, Inhalte aus bestimmten Dokumentelementen wie Tabellen oder Bildern zu extrahieren?

Ja, Sie können mit Aspose.Words für Java Inhalte aus bestimmten Dokumentelementen wie Tabellen oder Bildern extrahieren. Identifizieren Sie die Elemente, die Sie extrahieren möchten, und verwenden Sie dann die entsprechenden Methoden, um deren Inhalt zu extrahieren.

### Wie kann ich den Inhaltsextraktionsprozess in meiner Java-Anwendung automatisieren?

Um den Inhaltsextraktionsprozess in Ihrer Java-Anwendung zu automatisieren, können Sie basierend auf den in diesem Handbuch beschriebenen Techniken benutzerdefinierten Code erstellen. Sie können auch Logik implementieren, um mehrere Dokumente zu durchlaufen und Inhalte nach Bedarf zu extrahieren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
