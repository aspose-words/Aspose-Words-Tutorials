---
title: Aspose.Words for Java で構造化ドキュメント タグ (SDT) を使用する
linktitle: 構造化ドキュメントタグ (SDT) の使用
second_title: Aspose.Words Java ドキュメント処理 API
description: この包括的なガイドでは、Aspose.Words for Java で構造化ドキュメント タグ (SDT) を使用する方法を学習します。SDT を作成、変更し、カスタム XML データにバインドします。
weight: 19
url: /ja/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java で構造化ドキュメント タグ (SDT) を使用する


## Aspose.Words for Java での構造化ドキュメント タグ (SDT) の使用の概要

構造化ドキュメント タグ (SDT) は、ドキュメント内で構造化コンテンツを作成および操作できる、Aspose.Words for Java の強力な機能です。この包括的なガイドでは、Aspose.Words for Java での SDT の使用に関するさまざまな側面について説明します。初心者でも経験豊富な開発者でも、この記事には貴重な洞察と実用的な例が記載されています。

## はじめる

詳細に入る前に、環境を設定して基本的な SDT を作成しましょう。このセクションでは、次のトピックについて説明します。

- 新しいドキュメントを作成する
- 構造化ドキュメントタグの追加
- ドキュメントを保存する

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//CHECKBOXタイプの構造化ドキュメントタグを作成する
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

//文書を保存する
doc.save("WorkingWithSDT.docx");
```

## チェックボックスSDTの現在の状態を確認する

ドキュメントにチェックボックス SDT を追加したら、プログラムで現在の状態を確認したい場合があります。これは、ユーザー入力を検証したり、チェックボックスの状態に基づいて特定のアクションを実行したりする必要がある場合に役立ちます。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    //チェックボックスがオンになっています
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## コンテンツコントロールの変更

このセクションでは、ドキュメント内のコンテンツ コントロールを変更する方法について説明します。プレーン テキスト、ドロップダウン リスト、画像の 3 種類のコンテンツ コントロールについて説明します。

### プレーンテキストコンテンツコントロールの変更

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    //既存のコンテンツをクリアする
    sdtPlainText.removeAllChildren();

    //新しいテキストを追加
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### ドロップダウン リスト コンテンツ コントロールの変更

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    //リストから2番目の項目を選択します
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### 画像コンテンツコントロールの変更

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    //画像を新しいものに置き換える
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## コンボボックス コンテンツ コントロールの作成

ComboBox コンテンツ コントロールを使用すると、ユーザーは定義済みのオプション リストから選択できます。ドキュメントに 1 つ作成してみましょう。

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## リッチテキストコンテンツコントロールの操作

リッチ テキスト コンテンツ コントロールは、ドキュメントに書式設定されたテキストを追加するのに最適です。 リッチ テキスト コンテンツ コントロールを作成して、そのコンテンツを設定してみましょう。

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## コンテンツコントロールスタイルの設定

コンテンツ コントロールにスタイルを適用して、ドキュメントの外観を向上させることができます。コンテンツ コントロールのスタイルを設定する方法を見てみましょう。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

//カスタムスタイルを適用する
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## SDT をカスタム XML データにバインドする

シナリオによっては、動的なコンテンツを生成するために、SDT をカスタム XML データにバインドする必要がある場合があります。これを実現する方法を見てみましょう。

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## カスタム XML データにマップされた繰り返しセクションを含むテーブルの作成

繰り返しセクションを含むテーブルは、構造化されたデータを表示するのに非常に便利です。このようなテーブルを作成し、カスタム XML データにマップしてみましょう。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## 複数セクション構造化ドキュメントタグの操作

構造化ドキュメント タグは、ドキュメント内の複数のセクションにまたがることができます。このセクションでは、複数セクションの SDT の操作方法について説明します。

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## 結論

Aspose.Words for Java の構造化ドキュメント タグは、ドキュメント内のコンテンツを管理およびフォーマットするための多目的な方法を提供します。テンプレート、フォーム、または動的ドキュメントのいずれを作成する場合でも、SDT は必要な柔軟性と制御を提供します。この記事で紹介する例とガイドラインに従うことで、SDT のパワーを活用してドキュメント処理タスクを強化できます。

## よくある質問

### 構造化ドキュメントタグ (SDT) の目的は何ですか?

構造化ドキュメント タグ (SDT) は、ドキュメント内のコンテンツを整理およびフォーマットする目的で使用され、テンプレート、フォーム、構造化ドキュメントの作成が容易になります。

### Checkbox SDT の現在の状態を確認するにはどうすればよいですか?

チェックボックスSDTの現在の状態を確認するには、`setChecked`記事で説明されている方法。

### コンテンツ コントロールにスタイルを適用できますか?

はい、コンテンツ コントロールにスタイルを適用して、ドキュメント内の外観をカスタマイズできます。

### SDT をカスタム XML データにバインドすることは可能ですか?

はい、SDT をカスタム XML データにバインドして、動的なコンテンツの生成とデータ マッピングが可能になります。

### SDT の繰り返しセクションとは何ですか?

SDT の繰り返しセクションを使用すると、マップされた XML データに基づいて行を繰り返すことができる動的なデータを含むテーブルを作成できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
