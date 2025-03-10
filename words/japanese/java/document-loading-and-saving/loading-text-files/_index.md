---
title: Aspose.Words for Java でテキスト ファイルを読み込む
linktitle: テキストファイルの読み込み
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java のパワーを解き放ちます。テキスト ドキュメントの読み込み、リストの管理、スペースの処理、テキストの方向の制御を学習します。
weight: 13
url: /ja/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でテキスト ファイルを読み込む


## Aspose.Words for Java を使用したテキスト ファイルの読み込みの概要

このガイドでは、Aspose.Words for Java を使用してテキスト ファイルを読み込み、Word 文書として操作する方法について説明します。リストの検出、スペースの処理、テキストの方向の制御など、さまざまな側面について説明します。

## ステップ1: リストの検出

テキスト ドキュメントを読み込んでリストを検出するには、次の手順に従います。

```java
//リストとして解釈できる部分を含む文字列形式のプレーンテキスト ドキュメントを作成します。
//ロード時に、最初の3つのリストは常にAspose.Wordsによって検出されます。
//ロード後にそれらのリスト オブジェクトが作成されます。
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
//4番目のリストでは、リスト番号とリスト項目の内容の間に空白が入っています。
// LoadOptionsオブジェクトの「DetectNumberingWithWhitespaces」がtrueに設定されている場合にのみリストとして検出されます。
//数字で始まる段落が誤ってリストとして検出されるのを避けるためです。
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// LoadOptions をパラメータとして適用しながらドキュメントをロードし、結果を確認します。
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

このコードは、さまざまなリスト形式のテキスト文書を読み込み、`DetectNumberingWithWhitespaces`リストを正しく検出するオプション。

## ステップ2: スペースオプションの処理

テキスト ドキュメントを読み込むときに先頭と末尾のスペースを制御するには、次のコードを使用できます。

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

この例では、テキスト文書を読み込み、先頭と末尾のスペースを削除します。`TxtLeadingSpacesOptions.TRIM`そして`TxtTrailingSpacesOptions.TRIM`.

## ステップ3: テキストの方向を制御する

テキスト ドキュメントを読み込むときにテキストの方向を指定するには、次のコードを使用できます。

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

このコードは、ドキュメントの方向を自動検出に設定します（`DocumentDirection.AUTO`をクリックして、ヘブライ語のテキストを含むテキスト ドキュメントを読み込みます。必要に応じてドキュメントの方向を調整できます。

## Aspose.Words for Java でテキスト ファイルを読み込むための完全なソース コード

```java
public void detectNumberingWithWhitespaces() throws Exception {
	//リストとして解釈できる部分を含む文字列形式のプレーンテキスト ドキュメントを作成します。
	//ロード時に、最初の3つのリストは常にAspose.Wordsによって検出されます。
	//ロード後にそれらのリスト オブジェクトが作成されます。
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	//4番目のリストでは、リスト番号とリスト項目の内容の間に空白が入っています。
	// LoadOptionsオブジェクトの「DetectNumberingWithWhitespaces」がtrueに設定されている場合にのみリストとして検出されます。
	//数字で始まる段落が誤ってリストとして検出されるのを避けるためです。
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// LoadOptions をパラメータとして適用しながらドキュメントをロードし、結果を確認します。
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## 結論

このガイドでは、Aspose.Words for Java を使用してテキスト ファイルを読み込み、リストを検出し、スペースを処理し、テキストの方向を制御する方法について説明しました。これらのテクニックを使用すると、Java アプリケーションでテキスト ドキュメントを効果的に操作できます。

## よくある質問

### Aspose.Words for Java とは何ですか?

Aspose.Words for Java は、開発者が Java アプリケーションで Word 文書をプログラム的に作成、操作、変換できるようにする強力なドキュメント処理ライブラリです。テキスト、表、画像、その他のドキュメント要素を操作するための幅広い機能を提供します。

### Aspose.Words for Java を使い始めるにはどうすればよいですか?

Aspose.Words for Java を使い始めるには、次の手順に従います。
1. Aspose.Words for Java ライブラリをダウンロードしてインストールします。
2. 以下のドキュメントを参照してください。[Aspose.Words for Java API リファレンス](https://reference.aspose.com/words/java/)詳細な情報と例については、こちらをご覧ください。
3. サンプル コードとチュートリアルを参照して、ライブラリを効果的に使用する方法を学習します。

### Aspose.Words for Java を使用してテキスト ドキュメントを読み込むにはどうすればよいでしょうか?

 Aspose.Words for Javaを使用してテキストドキュメントを読み込むには、`TxtLoadOptions`クラスと`Document`クラス。必要に応じて、スペースとテキストの方向を処理するための適切なオプションを指定してください。詳細な例については、この記事のステップバイステップ ガイドを参照してください。

### 読み込まれたテキスト ドキュメントを他の形式に変換できますか?

はい、Aspose.Words for Javaでは、読み込んだテキスト文書をDOCX、PDFなどのさまざまな形式に変換できます。`Document`変換を実行するクラス。具体的な変換例についてはドキュメントを確認してください。

### 読み込まれたテキスト ドキュメント内のスペースをどのように処理すればよいですか?

読み込まれたテキスト文書の先頭と末尾のスペースの処理方法を制御するには、`TxtLoadOptions` . オプション`TxtLeadingSpacesOptions`そして`TxtTrailingSpacesOptions`必要に応じてスペースをトリミングまたは保持できます。例については、このガイドの「スペース処理オプション」セクションを参照してください。

### Aspose.Words for Java におけるテキスト方向の重要性は何ですか?

ヘブライ語やアラビア語など、複数のスクリプトや言語が混在するドキュメントでは、テキストの方向が重要です。Aspose.Words for Java には、テキストの方向を指定するオプションが用意されており、これらの言語でテキストが適切にレンダリングされ、書式設定されます。このガイドの「テキストの方向の制御」セクションでは、テキストの方向を設定する方法を説明します。

### Aspose.Words for Java のその他のリソースやサポートはどこで見つかりますか?

追加のリソース、ドキュメント、サポートについては、[Aspose.Words for Java ドキュメント](https://reference.aspose.com/words/java/)また、Aspose.Words コミュニティ フォーラムに参加したり、特定の問題や質問について Aspose サポートに問い合わせることもできます。

### Aspose.Words for Java は商用プロジェクトに適していますか?

はい、Aspose.Words for Java は個人プロジェクトと商用プロジェクトの両方に適しています。さまざまな使用シナリオに対応するライセンス オプションが用意されています。Aspose Web サイトでライセンス条件と価格を確認し、プロジェクトに適したライセンスを選択してください。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
