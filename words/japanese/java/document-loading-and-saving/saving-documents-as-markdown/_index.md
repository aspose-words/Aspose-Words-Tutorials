---
"description": "Aspose.Words for Javaを使ってWord文書をMarkdownに変換する方法を学びましょう。このステップバイステップガイドでは、表の配置、画像の扱い方などについて詳しく説明します。"
"linktitle": "ドキュメントをMarkdownとして保存する"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でドキュメントを Markdown として保存する"
"url": "/ja/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントを Markdown として保存する


## Aspose.Words for Java でドキュメントを Markdown として保存する方法の紹介

このステップバイステップガイドでは、Aspose.Words for Java を使用してドキュメントを Markdown 形式で保存する方法を説明します。Markdown は、テキストドキュメントの書式設定によく使用される軽量マークアップ言語です。Aspose.Words for Java を使えば、Word ドキュメントを簡単に Markdown 形式に変換できます。表のコンテンツの配置や画像の扱いなど、Markdown ファイルの保存に関するさまざまな側面について説明します。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

- Java Development Kit (JDK) がシステムにインストールされています。
- Aspose.Words for Javaライブラリ。こちらからダウンロードできます。 [ここ](https://releases。aspose.com/words/java/).

## ステップ1：Word文書を作成する

まずWord文書を作成し、後でMarkdown形式に変換します。この文書は必要に応じてカスタマイズできます。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2つのセルを持つ表を挿入する
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// ドキュメントをMarkdownとして保存する
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

この例では、2つのセルを持つシンプルな表を作成し、これらのセル内の段落の配置を設定します。次に、 `MarkdownSaveOptions`。

## ステップ2: 表のコンテンツの配置をカスタマイズする

Aspose.Words for Java では、Markdown 形式で保存する際に表のコンテンツの配置をカスタマイズできます。表のコンテンツを左揃え、右揃え、中央揃えにしたり、各表の列の最初の段落に基づいて自動的に配置を決めたりすることも可能です。

表のコンテンツの配置をカスタマイズする方法は次のとおりです。

```java
// 表の内容を左揃えにする
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// 表の内容を右揃えにする
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// 表のコンテンツの配置を中央に設定する
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// 表の内容の配置を自動（最初の段落によって決定）に設定します
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

変更することで `TableContentAlignment` プロパティを使用すると、Markdown に変換するときにテーブル内のコンテンツをどのように配置するかを制御できます。

## ステップ3: 画像の処理

Markdown文書に画像を含めるには、画像が保存されているフォルダを指定する必要があります。Aspose.Words for Javaでは、画像フォルダを `MarkdownSaveOptions`。

画像フォルダを設定し、画像付きのドキュメントを保存する方法は次のとおりです。

```java
// 画像を含むドキュメントを読み込む
Document doc = new Document("document_with_images.docx");

// 画像フォルダのパスを設定する
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// 画像付きのドキュメントを保存する
doc.save("document_with_images.md", saveOptions);
```

必ず交換してください `"document_with_images.docx"` 画像を含むWord文書へのパスと `"images_folder/"` 画像が保存されているフォルダーへの実際のパスを入力します。

## Aspose.Words for Java でドキュメントを Markdown として保存するための完全なソースコード

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
	// 表内のすべての段落を揃えます。
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// この場合の配置は、対応する表の列の最初の段落から取得されます。
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

## 結論

このガイドでは、Aspose.Words for Java を使用してドキュメントを Markdown 形式で保存する方法を説明しました。Word 文書の作成、表の配置のカスタマイズ、Markdown ファイル内の画像の扱い方について説明しました。これで、Word 文書を効率的に Markdown 形式に変換し、様々な出版プラットフォームやドキュメントのニーズに適した形式にすることができます。

## よくある質問

### Aspose.Words for Java をインストールするにはどうすればよいですか?

Aspose.Words for Javaは、Javaプロジェクトにライブラリを含めることでインストールできます。ライブラリは以下からダウンロードできます。 [ここ](https://releases.aspose.com/words/java/) ドキュメントに記載されているインストール手順に従ってください。

### 表や画像を含む複雑な Word 文書を Markdown に変換できますか?

はい、Aspose.Words for Java は、表、画像、さまざまな書式要素を含む複雑な Word 文書を Markdown 形式に変換できます。文書の複雑さに応じて、Markdown 出力をカスタマイズできます。

### Markdown ファイル内の画像をどのように処理すればよいですか?

Markdownファイルに画像を含めるには、画像フォルダのパスを `setImagesFolder` 方法 `MarkdownSaveOptions`画像ファイルが指定されたフォルダーに保存されていることを確認すると、Aspose.Words for Java がそれに応じて画像参照を処理します。

### Aspose.Words for Java の試用版はありますか?

はい、Aspose.Words for Javaの試用版はAsposeのウェブサイトから入手できます。試用版では、ライセンスを購入する前にライブラリの機能を評価することができます。

### さらに詳しい例やドキュメントはどこで見つかりますか?

Aspose.Words for Javaのその他の例、ドキュメント、および詳細情報については、 [ドキュメント](https://reference。aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}