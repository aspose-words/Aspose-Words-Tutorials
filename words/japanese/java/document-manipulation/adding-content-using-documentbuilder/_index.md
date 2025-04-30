---
"description": "Aspose.Words for Javaでドキュメント作成をマスター。テキスト、表、画像などを追加するステップバイステップガイド。魅力的なWord文書を簡単に作成できます。"
"linktitle": "DocumentBuilderを使用したコンテンツの追加"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java の DocumentBuilder を使用してコンテンツを追加する"
"url": "/ja/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java の DocumentBuilder を使用してコンテンツを追加する


## Aspose.Words for Java の DocumentBuilder を使用してコンテンツを追加する方法の紹介

このステップバイステップガイドでは、Aspose.Words for Java の DocumentBuilder を使用して、Word 文書にさまざまなコンテンツを追加する方法を説明します。テキスト、表、水平罫線、フォームフィールド、HTML、ハイパーリンク、目次、インライン画像とフローティング画像、段落などの挿入方法を説明します。さあ、始めましょう！

## 前提条件

始める前に、プロジェクトにAspose.Words for Javaライブラリがセットアップされていることを確認してください。ダウンロードはこちらから可能です。 [ここ](https://releases。aspose.com/words/java/).

## テキストの追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 簡単なテキスト段落を挿入する
builder.write("This is a simple text paragraph.");

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## テーブルの追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// テーブルを開始する
Table table = builder.startTable();

// セルとコンテンツを挿入する
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// テーブルを終える
builder.endTable();

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## 水平線を追加する

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 水平線を挿入する
builder.insertHorizontalRule();

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## フォームフィールドの追加

### テキスト入力フォームフィールド

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// テキスト入力フォームフィールドを挿入する
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

### チェックボックスフォームフィールド

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// チェックボックスフォームフィールドを挿入する
builder.insertCheckBox("CheckBox", true, true, 0);

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

### コンボボックスフォームフィールド

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// コンボボックスの項目を定義する
String[] items = { "Option 1", "Option 2", "Option 3" };

// コンボボックスフォームフィールドを挿入する
builder.insertComboBox("DropDown", items, 0);

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## HTMLの追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTMLコンテンツを挿入する
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## ハイパーリンクの追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// ハイパーリンクを挿入する
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", 偽);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## 目次を追加する

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 目次を挿入する
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// ドキュメントコンテンツを追加する
// ...

// 目次を更新する
doc.updateFields();

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## 画像の追加

### インライン画像

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// インライン画像を挿入する
builder.insertImage("path/to/your/image.png");

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

### 浮遊画像

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// フローティング画像を挿入する
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## 段落の追加

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 段落の書式を設定する
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

// 段落を挿入する
builder.writeln("This is a formatted paragraph.");

// ドキュメントを保存する
doc.save("path/to/your/document.docx");
```

## ステップ10: カーソルの移動

文書内のカーソル位置は、次のようなさまざまな方法で制御できます。 `moveToParagraph`、 `moveToCell`など。以下に例を示します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// カーソルを特定の段落に移動する
builder.moveToParagraph(2, 0);

// 新しいカーソル位置にコンテンツを追加する
builder.writeln("This is the 3rd paragraph.");
```

Aspose.Words for Java の DocumentBuilder を使って実行できる一般的な操作をいくつかご紹介します。より高度な機能やカスタマイズオプションについては、ライブラリのドキュメントをご覧ください。ドキュメント作成を楽しみましょう！


## 結論

この包括的なガイドでは、Aspose.Words for Java の DocumentBuilder を使って Word 文書に様々なコンテンツを追加する方法について解説しました。テキスト、表、水平罫線、フォームフィールド、HTML、ハイパーリンク、目次、画像、段落、カーソル移動といった機能について解説しました。

## よくある質問

### Q: Aspose.Words for Java とは何ですか?

A: Aspose.Words for Javaは、開発者がMicrosoft Word文書をプログラムで作成、変更、操作できるようにするJavaライブラリです。文書の生成、書式設定、コンテンツの挿入など、幅広い機能を提供します。

### Q: ドキュメントに目次を追加するにはどうすればよいですか?

A: 目次を追加するには、 `DocumentBuilder` ドキュメントに目次フィールドを挿入します。コンテンツを追加した後は、ドキュメント内のフィールドを更新して目次に反映させてください。例を以下に示します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 目次フィールドを挿入する
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// ドキュメントコンテンツを追加する
// ...

// 目次を更新する
doc.updateFields();
```

### Q: Aspose.Words for Java を使用してドキュメントに画像を挿入するにはどうすればよいですか?

A: インラインとフローティングの両方の画像を挿入するには、 `DocumentBuilder`両方の例を以下に示します。

#### インライン画像:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// インライン画像を挿入する
builder.insertImage("path/to/your/image.png");
```

#### フローティングイメージ:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// フローティング画像を挿入する
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: コンテンツを追加するときにテキストと段落をフォーマットできますか?

A: はい、テキストや段落の書式設定は `DocumentBuilder`フォントのプロパティ、段落の配置、インデントなどを設定できます。例を以下に示します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// フォントと段落の書式を設定する
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

// 書式設定された段落を挿入する
builder.writeln("This is a formatted paragraph.");
```

### Q: 文書内の特定の場所にカーソルを移動するにはどうすればよいですか?

A: 次のような方法でカーソルの位置を制御できます。 `moveToParagraph`、 `moveToCell`など。以下に例を示します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// カーソルを特定の段落に移動する
builder.moveToParagraph(2, 0);

// 新しいカーソル位置にコンテンツを追加する
builder.writeln("This is the 3rd paragraph.");
```

Aspose.Words for JavaのDocumentBuilderを使い始める際に役立つよくある質問と回答をご紹介します。さらにご質問やサポートが必要な場合は、 [図書館のドキュメント](https://reference.aspose.com/words/java/) または、Aspose.Words コミュニティおよびサポート リソースから支援を求めてください。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}