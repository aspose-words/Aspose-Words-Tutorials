---
"description": "この包括的なガイドでは、Aspose.Words for Javaで構造化ドキュメントタグ（SDT）を使用する方法を学びます。SDTを作成、変更し、カスタムXMLデータにバインドする方法を学びます。"
"linktitle": "構造化文書タグ（SDT）の使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java で構造化ドキュメントタグ (SDT) を使用する"
"url": "/ja/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java で構造化ドキュメントタグ (SDT) を使用する


## Aspose.Words for Java での構造化ドキュメントタグ (SDT) の使用入門

構造化ドキュメントタグ（SDT）は、Aspose.Words for Javaの強力な機能であり、ドキュメント内で構造化されたコンテンツを作成および操作できます。この包括的なガイドでは、Aspose.Words for JavaにおけるSDTの様々な使用方法を詳しく説明します。初心者の方から経験豊富な開発者の方まで、この記事には貴重な洞察と実用的な例が満載です。

## はじめる

詳細に入る前に、環境をセットアップして基本的なSDTを作成しましょう。このセクションでは、以下のトピックについて説明します。

- 新しいドキュメントを作成する
- 構造化文書タグの追加
- ドキュメントを保存する

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// CHECKBOXタイプの構造化ドキュメントタグを作成する
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// ドキュメントを保存する
doc.save("WorkingWithSDT.docx");
```

## チェックボックスSDTの現在の状態を確認する

ドキュメントにチェックボックスSDTを追加したら、プログラムで現在の状態を確認したい場合があります。これは、ユーザー入力を検証したり、チェックボックスの状態に基づいて特定のアクションを実行したりする必要がある場合に役立ちます。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // チェックボックスがオンになっています
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## コンテンツコントロールの変更

このセクションでは、ドキュメント内のコンテンツコントロールを変更する方法について説明します。プレーンテキスト、ドロップダウンリスト、画像の3種類のコンテンツコントロールについて説明します。

### プレーンテキストコンテンツコントロールの変更

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // 既存のコンテンツをクリアする
    sdtPlainText.removeAllChildren();

    // 新しいテキストを追加
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### ドロップダウンリストコンテンツコントロールの変更

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // リストから2番目の項目を選択します
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
    // 画像を新しいものに置き換える
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## コンボボックスコンテンツコントロールの作成

ComboBoxコンテンツコントロールを使用すると、ユーザーは定義済みのオプションリストから選択できます。ドキュメントに1つ作成してみましょう。

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

リッチテキストコンテンツコントロールは、ドキュメントにフォーマットされたテキストを追加するのに最適です。実際に作成して、その内容を設定してみましょう。

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

コンテンツコントロールにスタイルを適用することで、ドキュメントの見た目を向上させることができます。コンテンツコントロールのスタイルを設定する方法を見てみましょう。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// カスタムスタイルを適用する
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## SDT をカスタム XML データにバインドする

シナリオによっては、動的なコンテンツを生成するために、SDTをカスタムXMLデータにバインドする必要があるかもしれません。その方法を見ていきましょう。

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## カスタム XML データにマップされた繰り返しセクションを含むテーブルの作成

繰り返しセクションを含む表は、構造化されたデータを提示するのに非常に便利です。そのような表を作成し、カスタムXMLデータにマッピングしてみましょう。

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

## 複数セクション構造化文書タグの操作

構造化文書タグは、文書内の複数のセクションにまたがって使用できます。このセクションでは、複数セクションのSDTの操作方法について説明します。

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## 結論

Aspose.Words for Javaの構造化ドキュメントタグ（SDT）は、ドキュメント内のコンテンツを管理およびフォーマットするための多様な方法を提供します。テンプレート、フォーム、あるいは動的なドキュメントを作成する場合でも、SDTは必要な柔軟性と制御性を提供します。この記事で紹介する例とガイドラインに従うことで、SDTの力を最大限に活用し、ドキュメント処理タスクを強化できます。

## よくある質問

### 構造化ドキュメントタグ (SDT) の目的は何ですか?

構造化ドキュメント タグ (SDT) は、ドキュメント内のコンテンツを整理およびフォーマットする目的で使用され、テンプレート、フォーム、構造化ドキュメントの作成が容易になります。

### Checkbox SDT の現在の状態を確認するにはどうすればよいですか?

チェックボックスSDTの現在の状態を確認するには、 `setChecked` 記事で説明されている方法。

### コンテンツ コントロールにスタイルを適用できますか?

はい、コンテンツ コントロールにスタイルを適用して、ドキュメント内での外観をカスタマイズできます。

### SDT をカスタム XML データにバインドすることは可能ですか?

はい、SDT をカスタム XML データにバインドして、動的なコンテンツ生成とデータ マッピングが可能になります。

### SDT の繰り返しセクションとは何ですか?

SDT の繰り返しセクションを使用すると、マップされた XML データに基づいて行を繰り返すことができる動的なデータを含むテーブルを作成できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}