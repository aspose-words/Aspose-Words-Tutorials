---
date: 2026-01-01
description: Lär dig hur du extraherar text med Aspose.Words för Java. Denna steg‑för‑steg‑guide
  visar flera extraktionstekniker med färdiga kodexempel som kan köras direkt.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Hur man extraherar text med Aspose.Words för Java
url: /sv/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hur man extraherar text med Aspose.Words för Java

## Hur man extraherar text med Aspose.Words för Java

I dokumentbehandlingsvärlden är **how to extract text using Aspose.Words** en vanlig fråga för Java‑utvecklare. Oavsett om du behöver hämta vanlig text, tabeller, bilder eller specifika element som bokmärken eller kommentarer, erbjuder Aspose.Words för Java ett rikt API som gör jobbet enkelt. I den här guiden går vi igenom dussintals extraktionsscenarier, förklarar varför varje metod är viktig och tillhandahåller färdiga kodexempel som du kan klistra in i ditt projekt.

## Snabba svar
- **Vilket bibliotek behöver jag?** Aspose.Words for Java (ladda ner från den officiella webbplatsen).  
- **Kan jag bara extrahera vanlig text?** Ja – använd `Document.getText()` eller `DocumentBuilder` med fält.  
- **Är det möjligt att extrahera mellan bokmärken?** Absolut, använd `BookmarkStart`/`BookmarkEnd` med `ExtractContentHelper`.  
- **Behöver jag en licens för produktion?** En kommersiell licens krävs för icke‑testanvändning.  
- **Vilka Java‑versioner stöds?** Java 8 och nyare är fullt kompatibla.

## Förutsättningar

1. **Aspose.Words for Java** – installera biblioteket och lägg till det i ditt projekt. Du kan ladda ner det från [here](https://releases.aspose.com/words/java/).  
2. **Ett exempel på dokument** – för exemplen använder vi en fil med namnet `Extract content.docx`. Placera den i en mapp som du kan referera till från din kod.

## Extrahera innehåll mellan block‑nivå‑noder

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

## Extrahera innehåll mellan bokmärken

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

## Extrahera innehåll mellan kommentarsområden

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

## Extrahera innehåll mellan stycken

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Extrahera innehåll mellan stycke‑stilar

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

## Extrahera innehåll mellan körningar

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

## Extrahera innehåll med DocumentVisitor

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Extrahera innehåll med Field

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

## Extrahera innehållsförteckning

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

## Extrahera endast text

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Extrahera innehåll baserat på stilar

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

## Extrahera och skriva ut text

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

## Extrahera bilder till filer

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

## Slutsats

Grattis! Du har nu en solid verktygslåda för **how to extract text using Aspose.Words** i Java. Från block‑nivå‑noder till bokmärken, kommentarer, stilar och till och med bilder ger API‑et dig fin‑granulerad kontroll över vad du drar ut ur ett dokument. Använd dessa kodsnuttar som grund, anpassa dem till dina egna filstrukturer och automatisera extraktionsprocessen över stora dokumentuppsättningar.

## Vanliga frågor

**Q: Hur extraherar jag innehåll från ett lösenordsskyddat dokument?**  
A: Ladda dokumentet med lösenordskonstruktorn: `new Document(path, new LoadOptions("password"))`, och kör sedan någon av extraktionsmetoderna som visas ovan.

**Q: Kan jag extrahera innehåll från flera dokument i ett och samma körning?**  
A: Ja. Loopa igenom en lista med filsökvägar, skapa ett `Document` för varje och tillämpa samma extraktionslogik inom loopen.

**Q: Finns det ett sätt att bara extrahera synlig text (ignorera dold eller fältkod)?**  
A: Använd `doc.getText()` för vanlig synlig text. För mer kontroll, iterera genom noder och filtrera på `NodeType.RUN` samt `Run.getFont().getHidden()`.

**Q: Vilka format kan jag spara det extraherade innehållet till?**  
A: Efter extraktion kan du spara ett `Document` som DOCX, PDF, HTML, TXT eller något annat format som stöds av Aspose.Words via `doc.save("output.pdf")`.

**Q: Stöder Aspose.Words att extrahera innehåll från stora (hundratals MB) filer?**  
A: Ja, men överväg att använda `LoadOptions` med `LoadFormat` och `MemoryOptimization` för att minska minnesförbrukningen.

**Senast uppdaterad:** 2026-01-01  
**Testad med:** Aspose.Words for Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}