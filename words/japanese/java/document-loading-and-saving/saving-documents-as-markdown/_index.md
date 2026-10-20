---
date: 2025-12-22
description: Aspose.Words for Java を使用して Word 文書を Markdown に変換し、マークダウンをエクスポートする方法を学びましょう。このステップバイステップガイドでは、テーブルの配置や画像の処理などをカバーしています。
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for JavaでMarkdownをエクスポートする方法
url: /ja/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用した Markdown のエクスポート方法

## Aspose.Words for Java における Markdown エクスポートの概要

このステップバイステップのチュートリアルでは、**Aspose.Words for Java を使用して Word ドキュメントから Markdown をエクスポートする方法**を学びます。Markdown は、ドキュメント作成、静的サイトジェネレータ、さまざまな出版プラットフォームに最適な軽量マークアップ言語です。本ガイドの最後までに、**Word を Markdown に変換**し、テーブルの配置をカスタマイズし、**Markdown で画像を扱う**ことが簡単にできるようになります。

## クイック回答
- **Markdown として保存するための主要クラスは何ですか？** `MarkdownSaveOptions`
- **画像を自動的に埋め込むことはできますか？** はい – `setImagesFolder` で画像フォルダーを設定します。
- **テーブルの配置を制御するにはどうすればよいですか？** `TableContentAlignment`（LEFT、RIGHT、CENTER、AUTO）を使用します。
- **最低要件は何ですか？** JDK 8 以上と Aspose.Words for Java ライブラリです。
- **試用版は利用可能ですか？** はい、Aspose のウェブサイトからダウンロードできます。

## 「Markdown のエクスポート方法」とは何ですか？

Markdown のエクスポートとは、リッチテキストの Word ドキュメント（`.docx`）を取得し、見出し、テーブル、画像を Markdown 構文で保持したプレーンテキストの `.md` ファイルを生成することを意味します。

## 画像付き docx を変換する際に Aspose.Words for Java を使用する理由

Aspose.Words は、複雑なレイアウト、埋め込み画像、テーブル構造を忠実に処理します。また、テーブルの配置や画像フォルダーの管理など、Markdown 出力に対する細かな制御も提供します。

## Prerequisites

- システムに Java Development Kit（JDK）がインストールされていること。
- Aspose.Words for Java ライブラリ。[here](https://releases.aspose.com/words/java/) からダウンロードできます。

## 手順 1: シンプルな Word ドキュメントを作成する

まず、テーブルを含む小さなドキュメントを作成します。これにより、後で **テーブルの配置をカスタマイズ** する方法を実演できます。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

上記のスニペットでは次のことを行っています:

1. 新しい `Document` を作成します。
2. `DocumentBuilder` を使用して 2 列のテーブルを挿入します。
3. 各セル内で **右揃え** と **中央揃え** の段落配置を適用します。
4. `MarkdownSaveOptions` を使用してファイルを Markdown として保存します。

## 手順 2: テーブルコンテンツの配置をカスタマイズする

Aspose.Words を使用すると、最終的な Markdown でテーブルセルがどのようにレンダリングされるかを指定できます。左揃え、右揃え、中央揃えを強制するか、各列の最初の段落に基づいてライブラリに自動的に判断させることができます。

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

`TableContentAlignment` プロパティを切り替えることで、Markdown 出力の **テーブル配置のカスタマイズ** を制御できます。

## 手順 3: Markdown へのエクスポート時に画像を処理する

ドキュメントに画像が含まれている場合、生成された `.md` ファイルに画像が正しく表示されるようにしたいでしょう。Aspose.Words が抽出した画像を出力するフォルダーを設定します。

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

`"document_with_images.docx"` をソースファイルへのパスに、`"images_folder/"` を画像を保存したい場所に置き換えてください。生成された Markdown にはこのフォルダーを指す画像リンクが含まれ、**Markdown で画像をシームレスに処理**できるようになります。

## Aspose.Words for Java でドキュメントを Markdown として保存する完全なソースコード

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## よくある問題と解決策

| 問題 | 解決策 |
|------|--------|
| `.md` ファイルに画像が表示されない | `setImagesFolder` が書き込み可能なディレクトリを指していること、生成された Markdown でフォルダーが正しく参照されていることを確認してください。 |
| テーブルの配置がずれている | `TableContentAlignment.AUTO` を使用して、各列の最初の段落に基づき Aspose.Words に最適な配置を推測させます。 |
| 出力ファイルが空です | `save` を呼び出す前に、`Document` オブジェクトに実際にコンテンツが含まれていることを確認してください。 |

## よくある質問

**Q: Aspose.Words for Java のインストール方法は？**  
A: Aspose.Words for Java は、Java プロジェクトにライブラリを組み込むことでインストールできます。[here](https://releases.aspose.com/words/java/) からライブラリをダウンロードし、ドキュメントに記載されたインストール手順に従ってください。

**Q: 複雑なテーブルや画像を含む Word ドキュメントを Markdown に変換できますか？**  
A: はい、Aspose.Words for Java は、テーブルや画像、さまざまな書式要素を含む複雑な Word ドキュメントの Markdown への変換をサポートしています。ドキュメントの複雑さに応じて Markdown 出力をカスタマイズできます。

**Q: Markdown ファイルで画像をどのように扱えばよいですか？**  
A: `MarkdownSaveOptions` の `setImagesFolder` メソッドで画像フォルダーのパスを設定します。画像ファイルが指定したフォルダーに保存されていることを確認してください。Aspose.Words が適切な Markdown 画像リンクを生成します。

**Q: Aspose.Words for Java の試用版は利用可能ですか？**  
A: はい、Aspose のウェブサイトから Aspose.Words for Java の試用版を入手できます。試用版では、ライセンスを購入する前にライブラリの機能を評価できます。

**Q: さらに多くのサンプルやドキュメントはどこで見つけられますか？**  
A: Aspose.Words for Java のサンプル、ドキュメント、詳細情報については、[documentation](https://reference.aspose.com/words/java/) をご覧ください。

---

**最終更新日:** 2025-12-22  
**テスト環境:** Aspose.Words for Java 24.12（執筆時点での最新）  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}