---
date: 2026-02-24
description: Aspose.Words for Java を使用して Word を Markdown に変換する方法を学びましょう。このガイドでは、テーブルの配置、画像の処理、そしてドキュメントを
  Markdown として保存する方法を取り上げています。
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for JavaでWordをMarkdownに変換
url: /ja/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用した Word から Markdown への変換

## Aspose.Words for Java を使用した Word から Markdown への変換の概要

このステップバイステップのチュートリアルでは、強力な Aspose.Words for Java API を使用して **Word を Markdown に変換する方法** を学びます。Markdown は軽量マークアップ言語で、多くの開発者やコンテンツプラットフォームがクリーンで読みやすいドキュメント作成に利用しています。本ガイドを最後まで読むと、任意の `.docx` ファイルをテーブル、画像、書式を保持したまま `.md` ファイルにエクスポートでき、静的サイトジェネレータや GitHub README、その他 Markdown 対応のワークフローで利用できるようになります。

## Quick Answers
- **必要なライブラリは？** Aspose.Words for Java（`aspose-words.jar`）。
- **テーブルの配置をカスタマイズできますか？** はい – `MarkdownSaveOptions` の `TableContentAlignment` を使用します。
- **画像はどのように扱われますか？** `setImagesFolder()` で画像フォルダーを指定すると、ライブラリが相対リンクを作成します。
- **本番環境でライセンスは必要ですか？** トライアル以外の使用には商用ライセンスが必要です。
- **Java 17 と互換性がありますか？** はい、ライブラリは Java 8 以降をサポートしています。

## Word を Markdown に変換するとは？

Word を Markdown に変換するとは、Microsoft Word 文書のリッチな書式情報をプレーンテキストの Markdown 構文に変換することを意味します。このプロセスは見出し、リスト、テーブル、画像参照を保持しつつ、バイナリ書式情報を除去し、コンテンツをポータブルでバージョン管理に適した形にします。

## Aspose.Words for Java でドキュメントを Markdown として保存するメリットは？

* **フルフィデリティ** – テーブル、画像、複雑なレイアウトがそのまま保持されます。  
* **細かな制御** – テーブル配置、画像パスなどを自由にカスタマイズ可能です。  
* **外部依存なし** – Office のインストールは不要で、すぐに利用できます。  
* **クロスプラットフォーム** – Windows、Linux、macOS いずれでも任意の Java ランタイムで動作します。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

- システムに Java Development Kit（JDK）がインストールされていること。  
- Aspose.Words for Java ライブラリ。ダウンロードは [here](https://releases.aspose.com/words/java/) から取得できます。

## ステップバイステップ ガイド

### 手順 1: 変換対象となる Word 文書を作成する

まず、2 列のテーブルを含むシンプルな Word 文書を作成します。この例では、テーブルセル内の段落配置が **Markdown としてドキュメントを保存** した際に正しく反映されることを示します。

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

### 手順 2: テーブル内容の配置をカスタマイズする

Aspose.Words for Java では、生成される Markdown のテーブルセル配置を制御できます。`TableContentAlignment` プロパティを使用して、左寄せ、右寄せ、中央寄せ、または各列の最初の段落に基づいて自動判定させることができます。

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

この設定を切り替えることで、**Word テーブルを Markdown にエクスポート** する際に、下流のレンダリングエンジンが期待する正確な配置を実現できます。

### 手順 3: 変換時の画像処理

ソースの Word 文書に画像が含まれている場合、Aspose.Words にエクスポート先の画像ファイルの保存場所を指示する必要があります。`MarkdownSaveOptions` の `setImagesFolder` メソッドで画像フォルダーを指定すると、Markdown にはそのフォルダーへの相対リンクが自動的に生成されます。

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

`"document_with_images.docx"` を実際のソースファイルパスに、`"images_folder/"` を画像出力先フォルダーに置き換えてください。

### すべてのシナリオの統合サンプルコード

以下は、**テーブル自動配置**、**配置のカスタマイズ**、**画像フォルダーの設定** を 1 つのメソッドで実演する統合例です。元のチュートリアルコードと同一で、変更なしで動作します。

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

## よくある問題と対策

| 問題 | 原因 | 対策 |
|------|------|------|
| 画像がリンク切れになる | `setImagesFolder` が未設定、またはフォルダー パスが誤っている | フォルダー パスが正しいか、書き込み可能か確認する |
| テーブル配置がずれる | `TableContentAlignment` の値が誤っている | `TableContentAlignment.AUTO` を使用して最初の段落に任せるか、LEFT/RIGHT/CENTER を明示的に指定する |
| 出力ファイルが空になる | `doc.save()` に保存オプションが渡されていない | `MarkdownSaveOptions` インスタンスを `save` メソッドに渡すことを確認する |
| Word の一部機能（例: SmartArt）がサポート外 | Markdown では表現できない複雑オブジェクトがある | それらの要素を画像に変換してから保存するか、ソース文書を簡素化する |

## FAQ（よくある質問）

**Q: Aspose.Words for Java のインストール方法は？**  
A: Aspose.Words for Java はプロジェクトにライブラリを追加することでインストールできます。ライブラリは [here](https://releases.aspose.com/words/java/) からダウンロードし、ドキュメントに記載された手順に従って設定してください。

**Q: 複雑なテーブルや画像を含む Word 文書を Markdown に変換できますか？**  
A: はい、Aspose.Words for Java はテーブル、画像、さまざまな書式要素を含む複雑な Word 文書の Markdown 変換をサポートしています。ドキュメントの複雑さに応じて Markdown 出力をカスタマイズできます。

**Q: Markdown ファイル内の画像はどのように扱えばよいですか？**  
A: `MarkdownSaveOptions` の `setImagesFolder` メソッドで画像フォルダーのパスを設定します。指定したフォルダーに画像が保存され、Aspose.Words for Java が Markdown 内の画像参照を自動的に生成します。

**Q: Aspose.Words for Java のトライアル版はありますか？**  
A: はい、Aspose のウェブサイトから Aspose.Words for Java のトライアル版を入手できます。トライアル版で機能を評価した後、ライセンスを購入してください。

**Q: さらに多くのサンプルやドキュメントはどこで入手できますか？**  
A: 追加のサンプル、ドキュメント、詳細情報は [documentation](https://reference.aspose.com/words/java/) をご覧ください。

## 結論

本ガイドでは、Aspose.Words for Java を使用して **Word を Markdown に変換** するために必要な手順をすべて網羅しました。ソース文書の作成、**テーブル配置のカスタマイズ**、画像フォルダーの適切な設定方法を学び、ブログやドキュメントサイト、その他 Markdown 対応プラットフォーム向けに Word コンテンツを確実にエクスポートできるようになります。

---

**最終更新日:** 2026-02-24  
**テスト環境:** Aspose.Words for Java 24.12（執筆時点での最新バージョン）  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}