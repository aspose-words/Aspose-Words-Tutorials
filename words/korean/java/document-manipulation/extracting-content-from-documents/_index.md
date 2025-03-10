---
title: Java용 Aspose.Words에서 문서에서 콘텐츠 추출
linktitle: 문서에서 콘텐츠 추출
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java를 사용하여 문서에서 콘텐츠를 쉽게 추출하는 방법을 알아보세요. 단계별 가이드와 코드 샘플이 프로세스를 간소화합니다.
weight: 13
url: /ko/java/document-manipulation/extracting-content-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서에서 콘텐츠 추출


## Aspose.Words for Java에서 문서에서 콘텐츠 추출 소개

문서 처리 분야에서 문서에서 콘텐츠를 추출하는 것은 일반적인 요구 사항입니다. 텍스트, 표, 이미지 또는 특정 문서 요소를 추출해야 하는지 여부에 관계없이 Aspose.Words for Java는 이 작업을 쉽게 수행할 수 있는 강력한 도구를 제공합니다. 이 포괄적인 가이드에서는 Aspose.Words for Java를 사용하여 문서에서 콘텐츠를 추출하는 프로세스를 안내합니다. 

## 필수 조건

추출 과정을 시작하기 전에 다음과 같은 전제 조건이 충족되었는지 확인하세요.

1.  Aspose.Words for Java: Java 개발 환경에 Aspose.Words for Java를 설치하고 설정해야 합니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/java/).

2. 콘텐츠를 추출할 문서: 이 가이드에서는 "Extract content.docx"라는 샘플 문서를 사용합니다. 추출할 비슷한 문서가 준비되어 있는지 확인하세요.

## 블록 수준 노드 간 콘텐츠 추출

```java
// 블록 수준 노드 간 콘텐츠 추출을 위한 Java 코드 샘플
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

## 북마크 간 콘텐츠 추출

```java
//북마크 사이의 컨텐츠 추출을 위한 Java 코드 샘플
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

## 주석 범위 사이의 콘텐츠 추출

```java
// 주석 범위 사이의 콘텐츠를 추출하기 위한 Java 코드 샘플
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

## 문단 사이의 내용 추출

```java
// 문단 사이의 내용을 추출하기 위한 Java 코드 샘플
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## 문단 스타일 사이의 콘텐츠 추출

```java
// 문단 스타일 간의 콘텐츠 추출을 위한 Java 코드 샘플
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## 실행 간 콘텐츠 추출

```java
// 실행 간에 콘텐츠를 추출하기 위한 Java 코드 샘플
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## DocumentVisitor를 사용하여 콘텐츠 추출

```java
// DocumentVisitor를 사용하여 콘텐츠를 추출하기 위한 Java 코드 샘플
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## 필드를 사용하여 콘텐츠 추출

```java
// Field를 사용하여 콘텐츠를 추출하기 위한 Java 코드 샘플
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## 목차 추출

```java
// 목차 추출을 위한 Java 코드 샘플
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

## 텍스트만 추출

```java
// 텍스트만 추출하기 위한 Java 코드 샘플
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## 스타일 기반 콘텐츠 추출

```java
// 스타일 기반 콘텐츠 추출을 위한 Java 코드 샘플
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

## 텍스트 추출 및 인쇄

```java
// 텍스트 추출 및 인쇄를 위한 Java 코드 샘플
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## 이미지를 파일로 추출하기

```java
// 이미지를 파일로 추출하기 위한 Java 코드 샘플
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

## 결론

축하합니다! Aspose.Words for Java를 사용하여 문서에서 콘텐츠를 추출하는 방법을 배웠습니다. 이 가이드에서는 블록 수준 노드, 북마크, 주석 범위, 문단 등 간의 콘텐츠를 포함한 다양한 추출 기술을 다루었습니다. 이제 Java 애플리케이션에서 문서 콘텐츠 추출을 효율적으로 처리할 준비가 되었습니다.

## 자주 묻는 질문

### 특정 문서 섹션에서 콘텐츠를 추출하려면 어떻게 해야 하나요?

특정 문서 섹션에서 내용을 추출하려면 섹션의 시작 및 종료 지점을 식별하고 적절한 Aspose.Words for Java 메서드를 사용하여 그 사이의 내용을 추출할 수 있습니다.

### 암호로 보호된 문서에서 콘텐츠를 추출할 수 있나요?

네, Aspose.Words for Java는 암호로 보호된 문서에서 콘텐츠를 추출하는 기능을 제공합니다. 문서를 열 때 암호를 제공할 수 있습니다.`Document` 클래스 생성자.

### 일반 텍스트나 HTML 등 다양한 형식으로 콘텐츠를 추출하여 저장하려면 어떻게 해야 하나요?

 Aspose.Words for Java를 사용하여 문서에서 콘텐츠를 추출하고 다양한 형식으로 저장할 수 있습니다. 콘텐츠를 추출한 후 다음을 사용할 수 있습니다.`Document` 일반 텍스트, HTML 등의 형식으로 저장하기 위한 클래스 메서드.

### 표나 이미지와 같은 특정 문서 요소에서 콘텐츠를 추출하는 방법이 있나요?

네, Aspose.Words for Java를 사용하여 테이블이나 이미지와 같은 특정 문서 요소에서 콘텐츠를 추출할 수 있습니다. 추출하려는 요소를 식별한 다음 적절한 방법을 사용하여 콘텐츠를 추출합니다.

### Java 애플리케이션에서 콘텐츠 추출 프로세스를 자동화하려면 어떻게 해야 합니까?

Java 애플리케이션에서 콘텐츠 추출 프로세스를 자동화하려면 이 가이드에 설명된 기술을 기반으로 사용자 지정 코드를 만들 수 있습니다. 또한 여러 문서를 반복하고 필요에 따라 콘텐츠를 추출하는 논리를 구현할 수도 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
