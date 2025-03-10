---
title: Aspose.Words for Java でドキュメントからコンテンツを抽出する
linktitle: ドキュメントからコンテンツを抽出する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用してドキュメントからコンテンツを簡単に抽出する方法を学びます。ステップバイステップのガイドとコード サンプルにより、プロセスが簡素化されます。
weight: 13
url: /ja/java/document-manipulation/extracting-content-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントからコンテンツを抽出する


## Aspose.Words for Java でのドキュメントからのコンテンツ抽出の概要

ドキュメント処理の世界では、ドキュメントからコンテンツを抽出することは一般的な要件です。テキスト、表、画像、または特定のドキュメント要素を抽出する必要がある場合でも、Aspose.Words for Java は、このタスクを簡単に実行できる強力なツールを提供します。この包括的なガイドでは、Aspose.Words for Java を使用してドキュメントからコンテンツを抽出するプロセスを順を追って説明します。 

## 前提条件

抽出プロセスに進む前に、次の前提条件が満たされていることを確認してください。

1.  Aspose.Words for Java: Java開発環境にAspose.Words for Javaをインストールしてセットアップしておく必要があります。ダウンロードはこちらからできます。[ここ](https://releases.aspose.com/words/java/).

2. コンテンツを抽出するドキュメント: このガイドでは、「Extract content.docx」というサンプル ドキュメントを使用します。抽出用に同様のドキュメントを用意しておいてください。

## ブロックレベルノード間のコンテンツの抽出

```java
//ブロックレベルノード間のコンテンツを抽出するための Java コードサンプル
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

## ブックマーク間のコンテンツの抽出

```java
//ブックマーク間のコンテンツを抽出するための Java コード サンプル
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

## コメント範囲間のコンテンツの抽出

```java
//コメント範囲間のコンテンツを抽出するための Java コード サンプル
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

## 段落間のコンテンツの抽出

```java
//段落間のコンテンツを抽出するための Java コード サンプル
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## 段落スタイル間のコンテンツの抽出

```java
//段落スタイル間のコンテンツを抽出するための Java コード サンプル
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## 実行間のコンテンツの抽出

```java
//実行間でコンテンツを抽出するための Java コード サンプル
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## DocumentVisitor を使用したコンテンツの抽出

```java
//DocumentVisitor を使用してコンテンツを抽出する Java コード サンプル
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## フィールドを使用したコンテンツの抽出

```java
//フィールドを使用してコンテンツを抽出するための Java コード サンプル
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## 目次の抽出

```java
//目次を抽出するための Java コード サンプル
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

## テキストのみの抽出

```java
//テキストのみを抽出するための Java コード サンプル
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## スタイルに基づいてコンテンツを抽出する

```java
//スタイルに基づいてコンテンツを抽出するための Java コード サンプル
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

## テキストの抽出と印刷

```java
//テキストを抽出して印刷するための Java コード サンプル
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## 画像をファイルに抽出する

```java
//画像をファイルに抽出するための Java コード サンプル
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

おめでとうございます。Aspose.Words for Java を使用してドキュメントからコンテンツを抽出する方法を学習しました。このガイドでは、ブロック レベル ノード、ブックマーク、コメント範囲、段落などの間のコンテンツを含むさまざまな抽出手法について説明しました。これで、Java アプリケーションでドキュメント コンテンツの抽出を効率的に処理できるようになりました。

## よくある質問

### 特定のドキュメントセクションからコンテンツを抽出するにはどうすればよいですか?

特定のドキュメント セクションからコンテンツを抽出するには、セクションの開始点と終了点を識別し、適切な Aspose.Words for Java メソッドを使用してそれらの間のコンテンツを抽出します。

### パスワードで保護されたドキュメントからコンテンツを抽出できますか?

はい、Aspose.Words for Javaには、パスワードで保護されたドキュメントからコンテンツを抽出する機能があります。`Document`クラスコンストラクター。

### コンテンツを抽出して、プレーンテキストや HTML などのさまざまな形式で保存するにはどうすればよいですか?

 Aspose.Words for Javaを使用すると、ドキュメントからコンテンツを抽出し、さまざまな形式で保存できます。コンテンツを抽出した後は、`Document`クラス メソッドを使用して、プレーン テキスト、HTML などの形式で保存します。

### 表や画像などの特定のドキュメント要素からコンテンツを抽出する方法はありますか?

はい、Aspose.Words for Java を使用して、表や画像などの特定のドキュメント要素からコンテンツを抽出できます。抽出する要素を特定し、適切な方法を使用してそのコンテンツを抽出します。

### Java アプリケーションでコンテンツ抽出プロセスを自動化するにはどうすればよいですか?

Java アプリケーションでコンテンツ抽出プロセスを自動化するには、このガイドで説明されている手法に基づいてカスタム コードを作成します。複数のドキュメントを反復処理し、必要に応じてコンテンツを抽出するロジックを実装することもできます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
