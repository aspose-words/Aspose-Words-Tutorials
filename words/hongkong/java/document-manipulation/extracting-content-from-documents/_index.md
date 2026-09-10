---
date: 2026-01-01
description: 學習如何使用 Aspose.Words for Java 提取文字。此一步一步的指南展示多種提取技術，並附有可直接執行的程式碼範例。
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 提取文字
url: /zh-hant/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 提取文字

## 如何使用 Aspose.Words for Java 提取文字

在文件處理的世界裡，**如何使用 Aspose.Words 提取文字** 是 Java 開發者常見的問題。無論您需要提取純文字、表格、圖片，或是書籤、批註等特定元素，Aspose.Words for Java 都提供了功能豐富的 API，讓工作變得簡單直觀。本指南將帶您逐一瀏覽多種提取情境，說明每種方法的適用原因，並提供可直接放入專案的即用程式碼範例。

## 快速答覆
- **需要哪個函式庫？** Aspose.Words for Java（從官方網站下載）。  
- **我可以只提取純文字嗎？** 可以 – 使用 `Document.getText()` 或搭配 `DocumentBuilder` 取得欄位。  
- **是否可以在書籤之間提取內容？** 完全可以，使用 `BookmarkStart`/`BookmarkEnd` 搭配 `ExtractContentHelper`。  
- **生產環境需要授權嗎？** 商業授權是非試用版的必要條件。  
- **支援哪些 Java 版本？** 完全相容於 Java 8 及更新版本。

## 先決條件

1. **Aspose.Words for Java** – 安裝函式庫並加入專案。您可以從 [here](https://releases.aspose.com/words/java/) 下載。  
2. **範例文件** – 本範例使用名為 `Extract content.docx` 的檔案。請將它放在程式碼可參照的資料夾中。

## 在區塊層級節點之間提取內容

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

## 在書籤之間提取內容

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

## 在批註範圍之間提取內容

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

## 在段落之間提取內容

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## 在段落樣式之間提取內容

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

## 在 Run 之間提取內容

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

## 使用 DocumentVisitor 提取內容

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## 使用 Field 提取內容

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

## 提取目錄

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

## 僅提取文字

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## 依樣式提取內容

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

## 提取並列印文字

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

## 提取圖片至檔案

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

## 結論

恭喜！您現在已擁有一套完整的 **如何使用 Aspose.Words 提取文字** 的工具箱。無論是區塊層級節點、書籤、批註、樣式，甚至圖片，API 都能讓您精細控制要從文件中抽取的內容。請以這些程式碼片段為基礎，依照自己的檔案結構進行調整，並在大量文件上自動化提取流程。

## 常見問題

**Q: 如何從受密碼保護的文件中提取內容？**  
A: 使用帶密碼的建構子載入文件：`new Document(path, new LoadOptions("password"))`，然後執行上述任一提取方法。

**Q: 能否在一次執行中從多個文件提取內容？**  
A: 可以。遍歷檔案路徑清單，為每個檔案建立 `Document`，在迴圈內套用相同的提取邏輯。

**Q: 有沒有辦法只提取可見文字（忽略隱藏或欄位代碼）？**  
A: 使用 `doc.getText()` 取得純可見文字。若需更細緻的控制，可遍歷節點，並以 `NodeType.RUN` 以及 `Run.getFont().getHidden()` 進行過濾。

**Q: 提取的內容可以儲存為哪些格式？**  
A: 提取後，您可以使用 `doc.save("output.pdf")` 將 `Document` 儲存為 DOCX、PDF、HTML、TXT 或 Aspose.Words 支援的任何其他格式。

**Q: Aspose.Words 能否處理大型（數百 MB）檔案的內容提取？**  
A: 能，但建議使用 `LoadOptions` 搭配 `LoadFormat` 與 `MemoryOptimization` 以降低記憶體使用量。

---

**最後更新：** 2026-01-01  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}