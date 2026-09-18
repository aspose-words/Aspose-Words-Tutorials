---
date: 2026-01-01
description: Erfahren Sie, wie Sie Text mit Aspose.Words für Java extrahieren. Dieser
  Schritt‑für‑Schritt‑Leitfaden zeigt mehrere Extraktionstechniken mit sofort ausführbaren
  Codebeispielen.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Wie man Text mit Aspose.Words für Java extrahiert
url: /de/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Text mit Aspose.Words für Java extrahiert

## Wie man Text mit Aspose.Words für Java extrahiert

In der Welt der Dokumentenverarbeitung ist **how to extract text using Aspose.Words** eine häufig gestellte Frage für Java‑Entwickler. Egal, ob Sie Klartext, Tabellen, Bilder oder bestimmte Elemente wie Lesezeichen oder Kommentare extrahieren müssen, Aspose.Words für Java bietet eine umfangreiche API, die die Aufgabe unkompliziert macht. In diesem Leitfaden gehen wir zahlreiche Extraktionsszenarien durch, erklären, warum jeder Ansatz wichtig ist, und stellen sofort einsatzbereite Code‑Beispiele bereit, die Sie in Ihr Projekt einbinden können.

## Schnelle Antworten
- **Welche Bibliothek benötige ich?** Aspose.Words für Java (Download von der offiziellen Website).  
- **Kann ich nur Klartext extrahieren?** Ja – verwenden Sie `Document.getText()` oder `DocumentBuilder` mit Feldern.  
- **Ist es möglich, zwischen Lesezeichen zu extrahieren?** Absolut, nutzen Sie `BookmarkStart`/`BookmarkEnd` zusammen mit `ExtractContentHelper`.  
- **Benötige ich eine Lizenz für die Produktion?** Eine kommerzielle Lizenz ist für die Nutzung außerhalb der Testphase erforderlich.  
- **Welche Java‑Versionen werden unterstützt?** Java 8 und neuer sind vollständig kompatibel.

## Voraussetzungen

1. **Aspose.Words für Java** – installieren Sie die Bibliothek und fügen Sie sie Ihrem Projekt hinzu. Sie können sie von [hier](https://releases.aspose.com/words/java/) herunterladen.  
2. **Ein Beispieldokument** – für die Beispiele verwenden wir eine Datei namens `Extract content.docx`. Platzieren Sie sie in einem Ordner, den Sie aus Ihrem Code heraus referenzieren können.

## Extrahieren von Inhalt zwischen Block‑Level‑Knoten

```java
// Java code sample for extracting content between block-level nodes
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

## Extrahieren von Inhalt zwischen Lesezeichen

```java
// Java code sample for extracting content between bookmarks
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

## Extrahieren von Inhalt zwischen Kommentarbereichen

```java
// Java code sample for extracting content between comment ranges
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

## Extrahieren von Inhalt zwischen Absätzen

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Extrahieren von Inhalt zwischen Absatz‑Stilen

```java
// Java code sample for extracting content between paragraph styles
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Extrahieren von Inhalt zwischen Runs

```java
// Java code sample for extracting content between runs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Extrahieren von Inhalt mit DocumentVisitor

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Extrahieren von Inhalt mit Feld

```java
// Java code sample for extracting content using Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Extrahieren des Inhaltsverzeichnisses

```java
// Java code sample for extracting table of contents
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
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Extrahieren von Inhalt basierend auf Stilen

```java
// Java code sample for extracting content based on styles
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

## Extrahieren und Ausgeben von Text

```java
// Java code sample for extracting and printing text
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
// Java code sample for extracting images to files
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

## Fazit

Herzlichen Glückwunsch! Sie verfügen jetzt über ein solides Werkzeugset für **how to extract text using Aspose.Words** in Java. Von Block‑Level‑Knoten über Lesezeichen, Kommentare, Stile bis hin zu Bildern bietet die API Ihnen eine feinkörnige Kontrolle darüber, was Sie aus einem Dokument herausziehen. Nutzen Sie diese Snippets als Grundlage, passen Sie sie an Ihre eigenen Dateistrukturen an und automatisieren Sie den Extraktionsprozess über große Dokumentensammlungen hinweg.

## Häufig gestellte Fragen

**F: Wie extrahiere ich Inhalt aus einem passwortgeschützten Dokument?**  
A: Laden Sie das Dokument mit dem Passwort‑Konstruktor: `new Document(path, new LoadOptions("password"))`, und führen Sie anschließend eine der oben gezeigten Extraktionsmethoden aus.

**F: Kann ich Inhalte aus mehreren Dokumenten in einem Durchlauf extrahieren?**  
A: Ja. Durchlaufen Sie eine Liste von Dateipfaden, instanziieren Sie für jede Datei ein `Document` und wenden Sie die gleiche Extraktionslogik innerhalb der Schleife an.

**F: Gibt es eine Möglichkeit, nur sichtbaren Text (ohne versteckte oder Feld‑Codes) zu extrahieren?**  
A: Verwenden Sie `doc.getText()` für reinen sichtbaren Text. Für mehr Kontrolle iterieren Sie über die Knoten und filtern nach `NodeType.RUN` sowie `Run.getFont().getHidden()`.

**F: In welchen Formaten kann ich den extrahierten Inhalt speichern?**  
A: Nach der Extraktion können Sie ein `Document` als DOCX, PDF, HTML, TXT oder in jedem anderen von Aspose.Words unterstützten Format speichern, z. B. `doc.save("output.pdf")`.

**F: Unterstützt Aspose.Words das Extrahieren von Inhalten aus sehr großen (hundert‑MB) Dateien?**  
A: Ja, jedoch sollten Sie `LoadOptions` mit `LoadFormat` und `MemoryOptimization` verwenden, um den Speicherverbrauch zu reduzieren.

---

**Zuletzt aktualisiert:** 2026-01-01  
**Getestet mit:** Aspose.Words für Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}