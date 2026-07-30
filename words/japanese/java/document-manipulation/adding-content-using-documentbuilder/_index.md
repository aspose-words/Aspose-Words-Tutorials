---
date: 2026-01-01
description: Aspose.Words for Java の DocumentBuilder を使用して、フォームフィールドの作成やテキスト、表、画像、ハイパーリンクなどの追加方法を学びましょう。開発者向けのステップバイステップガイドです。
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java の DocumentBuilder を使用してフォームフィールドを作成し、コンテンツを追加する方法
url: /ja/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java の DocumentBuilder を使用したコンテンツの追加

## Aspose.Words for Java の DocumentBuilder を使用したコンテンツ追加の概要

このステップバイステップ ガイドでは、**フォームフィールドを作成**し、テキスト、テーブル、水平線、HTML、ハイパーリンク、画像など、さまざまなコンテンツを Aspose.Words for Java を使用して Word 文書に追加します。レポート、契約書テンプレート、インタラクティブ フォームのいずれを作成する場合でも、`DocumentBuilder` クラスを使えば、すべての要素を細かく制御できます。さっそく始めましょう！

## クイック回答
- **フォームフィールドはどう作成しますか？** `DocumentBuilder` の `insertTextInput`、`insertCheckBox`、または `insertComboBox` を使用します。
- **プレーンテキストを追加するメソッドは？** `builder.write("Your text")` または `builder.writeln("Your text")` を呼び出します。
- **水平線を挿入できますか？** はい、`builder.insertHorizontalRule()` がライン区切りを追加します。
- **HTML を埋め込むには？** `builder.insertHtml("<p>HTML content</p>")` を使用します。
- **インライン画像を追加するには？** `builder.insertImage("path/to/image.png")` は画像をテキストフロー内に配置します。

## DocumentBuilder とは何か、そしてフォームフィールド作成に使用する理由

`DocumentBuilder` は Aspose.Words のフルエント API で、プログラムから Word 文書を構築・編集できます。低レベルの OpenXML 構造を抽象化し、*何を* 追加したいか（例: **フォームフィールド**）に集中できるようにします。動的なフォームや契約書、ユーザー操作が必要な文書の生成に最適です。

## 前提条件

作業を開始する前に、プロジェクトに Aspose.Words for Java ライブラリがインストールされていることを確認してください。ダウンロードは [here](https://releases.aspose.com/words/java/) から行えます。

## テキストの追加（テキストの追加方法）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## テーブルの追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## 水平線の追加（水平線を追加）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## フォームフィールドの追加（フォームフィールドを作成）

### テキスト入力フォームフィールド

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### チェックボックスフォームフィールド

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### コンボボックスフォームフィールド

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## HTML の追加（HTML を挿入）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## ハイパーリンクの追加（ハイパーリンクの追加方法）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## 目次の追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## 画像の追加

### インライン画像（インライン画像を挿入）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### フローティング画像

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## 段落の追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## カーソルの移動（ステップ 10）

文書内のカーソル位置は、`moveToParagraph`、`moveToCell` などのメソッドで制御できます。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

これらは Aspose.Words for Java の `DocumentBuilder` を使用して実行できる一般的な操作です。ライブラリのドキュメントを参照して、より高度な機能やカスタマイズオプションを探求してください。文書作成をお楽しみください！

## 結論

本ガイドでは、**フォームフィールドを作成**し、テキスト、テーブル、水平線、HTML、ハイパーリンク、目次、画像、書式設定された段落、カーソル操作など、さまざまなコンテンツを Aspose.Words for Java の `DocumentBuilder` を使って追加する方法を示しました。これで、プログラムから動的かつインタラクティブな Word 文書を生成するための確固たる基礎が身につきました。

## FAQ

### Q: Aspose.Words for Java とは何ですか？

A: Aspose.Words for Java は、開発者がプログラムから Microsoft Word 文書を作成、変更、操作できるようにする Java ライブラリです。文書生成、書式設定、コンテンツ挿入など幅広い機能を提供します。

### Q: 文書に目次を追加するにはどうすればよいですか？

A: 目次を追加するには、`DocumentBuilder` を使用して TOC フィールドを挿入し、コンテンツ追加後に `doc.updateFields()` を呼び出します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Aspose.Words for Java を使って文書に画像を挿入するには？

A: `DocumentBuilder` を使用して、インライン画像とフローティング画像の両方を挿入できます。

#### インライン画像:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### フローティング画像:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: コンテンツを追加する際にテキストや段落の書式設定はできますか？

A: はい、`DocumentBuilder` でフォントプロパティや段落の配置、インデントなどを設定してからコンテンツを書き込むことができます。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: カーソルを文書内の特定の位置に移動するには？

A: `moveToParagraph`、`moveToCell` などのメソッドを使用して、カーソルを目的の位置に配置してから新しいコンテンツを挿入します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

これらの回答は、Aspose.Words for Java の `DocumentBuilder` を使用する際に最も一般的なシナリオを網羅しています。詳細は [library's documentation](https://reference.aspose.com/words/java/) を参照するか、Aspose.Words コミュニティに参加してサポートを受けてください。

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}