---
date: 2025-12-27
description: Aspose.Words for Java を使用して、方向を設定し、txt ファイルを読み込み、スペースをトリムし、txt を docx
  に変換する方法を学びましょう。
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Javaで方向を設定し、テキストファイルを読み込む方法
url: /ja/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用した方向設定とテキストファイルの読み込み方法

## Aspose.Words for Java でテキストファイルを読み込む概要

このガイドでは、プレーンテキストドキュメントを読み込む際の **方向設定方法** を学び、**txt の読み込み**、**スペースのトリム**、**txt から docx への変換** を Aspose.Words for Java で実装する実用的な方法をご紹介します。ドキュメント変換サービスを構築する場合や、リスト検出を細かく制御したい場合に、本チュートリアルは明確な説明と実行可能なコードでステップバイステップで案内します。

## クイック回答
- **ロードした TXT ファイルのテキスト方向はどう設定しますか？** `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` を使用するか、`LEFT_TO_RIGHT` / `RIGHT_TO_LEFT` を指定します。  
- **Aspose.Words はプレーンテキストの番号付きリストを検出できますか？** はい – `TxtLoadOptions` の `DetectNumberingWithWhitespaces` を有効にします。  
- **先頭と末尾のスペースはどうトリムしますか？** `TxtLeadingSpacesOptions.TRIM` と `TxtTrailingSpacesOptions.TRIM` を設定します。  
- **1 行で TXT ファイルを DOCX に変換できますか？** `TxtLoadOptions` で TXT をロードし、`Document.save("output.docx")` を呼び出すだけです。  
- **必要な Java バージョンは？** Aspose.Words 24.x では Java 8 以上で十分です。

## Aspose.Words における「方向設定」とは何ですか？
テキストファイルに右から左へのスクリプト（例: ヘブライ語やアラビア語）が含まれる場合、ライブラリは読み取り順序を把握する必要があります。`DocumentDirection` 列挙型を使用すると、**方向を手動で設定** したり、Aspose に自動検出させたりでき、正しいレイアウトと双方向（bidi）フォーマットが保証されます。

## TXT ファイルの読み込みに Aspose.Words を使用する理由
- **正確なリスト検出** – 番号付き、箇条書き、空白区切りリストを処理。  
- **細かなスペース制御** – 先頭・末尾スペースのトリムまたは保持が可能。  
- **自動テキスト方向検出** – 多言語ドキュメントに最適。  
- **ワンステップ変換** – `.txt` をロードして `.docx`、`.pdf`、その他サポート形式に保存。

## 前提条件
- Java 8 以上。  
- Aspose.Words for Java ライブラリ（Maven/Gradle の依存関係を追加するか、JAR をプロジェクトに追加）。  
- 基本的な Java I/O ストリームの知識。

## 手順ガイド

### 手順 1: リストの検出 (テキストの読み込み方法)
テキストドキュメントをロードし、リストを自動検出するには `TxtLoadOptions` インスタンスを作成し、リスト検出を有効にします。以下のコードは複数のリストスタイルを示し、空白対応の番号付けを有効にします。

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **プロのコツ:** 基本的なリスト検出だけが必要な場合は、空白オプションを省略しても構いません – Aspose は標準の `1.` や `1)` パターンを認識します。

### 手順 2: スペースオプションの処理 (スペースのトリム方法)
先頭と末尾のスペースはフォーマットの乱れの原因になります。`TxtLeadingSpacesOptions` と `TxtTrailingSpacesOptions` を使用して動作を制御します。

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

> **重要性:** スペースをトリムすると、生成された DOCX に不要なインデントが入らず、手動での後処理なしで文書がすっきりします。

### 手順 3: テキスト方向の制御 (方向設定方法)
右から左の言語の場合、ロード前に文書方向を設定します。以下の例はヘブライ語テキストファイルをロードし、bidi フラグを出力して方向を確認します。

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

> **よくある落とし穴:** `DocumentDirection` を設定し忘れると、アラビア語/ヘブライ語の文字が逆順に表示され、文字化けが発生します。

## Aspose.Words for Java でテキストファイルを読み込む完全ソースコード
以下はリスト検出、スペース処理、方向制御を組み合わせた、単一クラスに貼り付けてすぐに実行できるフルソースです。3 つのテストメソッドを個別に実行できます。

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## 共通の問題と解決策
| 問題 | 原因 | 解決策 |
|------|------|--------|
| リストが検出されない | 空白区切りリスト用に `DetectNumberingWithWhitespaces` が `false` のまま | `loadOptions.setDetectNumberingWithWhitespaces(true)` を有効化 |
| 読み込み後に余分なインデントが付く | 先頭スペースが保持されている | `TxtLeadingSpacesOptions.TRIM` を設定 |
| ヘブライ語テキストが逆になる | 文書方向が設定されていない、または `LEFT_TO_RIGHT` に設定されている | `DocumentDirection.AUTO` または `RIGHT_TO_LEFT` を使用 |
| 出力 DOCX が空 | 2 回目のロード前に入力ストリームがリセットされていない | 各ロード呼び出しごとに `ByteArrayInputStream` を再作成 |

## よくある質問

### Q: Aspose.Words for Java とは何ですか？
A: Aspose.Words for Java は、開発者が Java アプリケーション内で Word ドキュメントをプログラム的に作成、操作、変換できる強力なドキュメント処理ライブラリです。シンプルなテキスト読み込みから複雑な書式設定・変換まで幅広い機能をサポートします。

### Q: Aspose.Words for Java の使い方を始めるには？
A: 1. Aspose.Words for Java ライブラリをダウンロードしてインストール。 2. 詳細情報とサンプルは [Aspose.Words for Java API リファレンス](https://reference.aspose.com/words/java/) を参照。 3. サンプルコードやチュートリアルを試してライブラリの使い方を習得してください。

### Q: Aspose.Words for Java でテキストドキュメントを読み込むには？
A: `TxtLoadOptions` クラスと `Document` コンストラクタを組み合わせます。リスト検出、スペース処理、テキスト方向などのオプションは、上記の手順セクションで示した通りに設定します。

### Q: 読み込んだテキストドキュメントを他の形式に変換できますか？
A: はい。TXT を `Document` オブジェクトにロードした後、`doc.save("output.pdf")`、`doc.save("output.docx")` など、サポートされている任意の形式で保存できます。

### Q: 読み込んだテキストドキュメントのスペースはどう扱いますか？
A: `TxtLeadingSpacesOptions` と `TxtTrailingSpacesOptions` で先頭・末尾スペースを制御します。不要な空白を除去したい場合は `TRIM` を、元の間隔を保持したい場合は `PRESERVE` を設定してください。

### Q: Aspose.Words for Java におけるテキスト方向の重要性は？
A: テキスト方向はヘブライ語やアラビア語など右から左へのスクリプトの正しい表示に不可欠です。`DocumentDirection` を設定することで、双方向テキストが期待通りにレンダリングされます。

### Q: Aspose.Words for Java の追加リソースやサポートはどこで得られますか？
A: 詳細な API リファレンス、コードサンプル、ガイドは [Aspose.Words for Java ドキュメンテーション](https://reference.aspose.com/words/java/) をご覧ください。Aspose コミュニティフォーラムやサポートチームにもお問い合わせいただけます。

### Q: 商用プロジェクトで Aspose.Words for Java を使用できますか？
A: はい。個人利用・商用利用の両方に対応したライセンスオプションがあります。プロジェクトに最適なプランは Aspose のウェブサイトでライセンス条件をご確認ください。

## 結論
これで **txt ファイルの読み込み**、**リスト検出**、**スペースのトリム**、**方向設定** を Aspose.Words for Java で実装するための完全なツールキットが手に入りました。これらのパターンを活用してドキュメントワークフローを自動化し、多言語サポートを強化し、常にクリーンでプロフェッショナルな出力を実現してください。

---

**最終更新日:** 2025-12-27  
**テスト環境:** Aspose.Words for Java 24.12  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}