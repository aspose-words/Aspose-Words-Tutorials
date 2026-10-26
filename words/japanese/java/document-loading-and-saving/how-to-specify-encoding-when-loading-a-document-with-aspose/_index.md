---
category: general
date: 2026-10-26
description: LoadOptions を使用して Java でエンコーディングを指定する方法を学びましょう。このガイドでは文字エンコーディング、setEncoding
  メソッド、そしてドキュメントの読み込みオプションについて解説します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: ja
lastmod: 2026-10-26
og_description: Aspose.Words を使用して Java でエンコーディングを指定する方法。正しい文字セットでドキュメントを読み込むための完全なチュートリアルをご覧ください。
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Aspose.Words を使用した Java のエンコーディング指定方法 – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Aspose.Words for Javaでドキュメントを読み込む際にエンコーディングを指定する方法
url: /ja/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Javaでドキュメントを読み込む際のエンコーディング指定方法

Javaでソースファイルの**エンコーディング指定方法**が必要な場合、本チュートリアルでは具体的な手順を示します。ドキュメントがBig5、UTF‑8、または他の文字セットを使用しているかにかかわらず、`LoadOptions` を使って読み込みプロセスを制御できます。ガイドの最後までに、文字エンコーディングが重要な理由、`setEncoding` メソッドの適用方法、そしてドキュメントが正しく読み込まれたかを確認する方法が理解できるようになります。

正しい文字エンコーディングでドキュメントを読み込むことで、文字化けを防ぎ、多言語コンテンツが意図した通りに表示されます。本チュートリアルでは以下を取り上げます：

* **Javaでの文字エンコーディング** の役割（ファイル読み取り時）。
* Aspose.Words の **LoadOptions エンコーディング** の設定方法。
* プロジェクトにコピーできる実用的なコード。
* エンコーディング不一致などの一般的な落とし穴とそのトラブルシューティング方法。

## 前提条件

開始する前に、以下が揃っていることを確認してください：

* Java Development Kit (JDK) 8 以上。
* 依存関係管理のための Maven または Gradle。
* Aspose.Words for Java 23.10 以降（本ガイドで使用しているバージョン）。
* 任意のエンコーディングで保存されたサンプルテキストドキュメント（`input.doc`、例: Big5）。

追加のライブラリは不要です。例ではコアの Aspose.Words API のみを使用しています。

## 手順 1: Aspose.Words をプロジェクトに追加

Maven を使用している場合、`pom.xml` に以下の依存関係を追加してください：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Gradle を使用している場合、`build.gradle` に以下の行を追加してください：

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

ライブラリを追加することで、`LoadOptions`、`Document`、`Encoding` クラスが使用可能になります。

## 手順 2: `LoadOptions` インスタンスの作成

`LoadOptions` は Aspose.Words がファイルを開く方法をカスタマイズできます。オブジェクトの作成は **エンコーディング指定方法** の最初のステップです。

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions` オブジェクトはデフォルト設定で開始します。次のステップでプロパティを調整します。

## 手順 3: 目的の文字エンコーディングを設定

`setEncoding` メソッドはローダーが使用すべき **Java の文字エンコーディング** を定義します。この例では、繁体字中国語のテキストファイルで一般的な Big5 コードページを選択します。

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Why this matters*: ファイルのバイトが誤ったコードページで解釈されると、文字が「?」や意味不明な文字列として表示されます。`setEncoding` を明示的に呼び出すことで、Aspose.Words に対しバイトストリームを Big5 のマッピングテーブルでデコードするよう指示します。

`"Big5"` を Java が認識する任意の文字セット名（例: `"UTF-8"`、`"ISO-8859-1"`、`"Windows-1252"`）に置き換えることができます。名前が無効な場合、メソッドは `UnsupportedEncodingException` をスローするため、本番コードでは例外を捕捉することを検討してください。

## 手順 4: 設定したオプションでドキュメントを読み込む

これで **LoadOptions のエンコーディング** が設定されたので、`Document` コンストラクタにオプションを渡します。このステップで **エンコーディング指定方法** の基本的なフローが完了します。

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

`YOUR_DIRECTORY` をファイルへの絶対パスまたは相対パスに置き換えてください。`Document` インスタンスは、指定したエンコーディングを考慮した完全に解析されたコンテンツを保持します。

## 手順 5: テキストが正しく読み込まれたか検証

簡単な検証により、エンコーディングが期待通りに適用されたことを確認できます。ドキュメントのテキストを抽出し、コンソールに出力してみましょう：

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

コンソールに読みやすい中国語文字（または期待する言語）が表示されれば、エンコーディングは成功しています。文字化けが続く場合は、元ファイルのエンコーディングを再確認し、charset 名が正確に一致しているか確認してください。

## 一般的なエッジケースの処理

### 5.1 `InputStream` からの読み込み

ドキュメントをストリーム（例: Web サービスから）として受け取ることがあります。その場合でも、`LoadOptions` と共にストリームを渡すことでエンコーディングを制御できます：

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

同じ **ドキュメント読み込みオプション** が適用され、`setEncoding` の呼び出しは変わりません。

### 5.2 エンコーディングが不明な場合のフォールバック

ソースファイルの charset が判別できない場合、エンコーディングを設定する前に検出ライブラリ（例: ICU4J）を試すことができます。推測した charset を取得したら、その値で `setEncoding` を呼び出します。この手法により、誤デコードのリスクが低減します。

### 5.3 サポートされていないエンコーディングへの対処

Java は多数のコードページをサポートしていますが、いくつかのレガシーエンコーディングは存在しない場合があります。その場合は、Aspose.Words で読み込む前に外部ツール（例: `iconv`）でファイルを UTF‑8 に変換することを検討してください。変換後は `setEncoding` 呼び出しを省略できます。UTF-8 はほとんどの最新 API のデフォルトです。

## プロのコツ: バッチ処理で `LoadOptions` を再利用

同じ charset を共有する多数のドキュメントを読み込む必要がある場合、単一の `LoadOptions` インスタンスを作成し、再利用してください：

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

オブジェクトを再利用することで、インスタンス生成のオーバーヘッドが削減され、バッチ全体でエンコーディングの一貫性が保証されます。

## 完全に実行可能なサンプル

以下は、すべての手順を組み込み、必要なインポートを含み、例外処理を行う完全なプログラムです。

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**期待される出力**（ソースファイルが Big5 でエンコードされた中国語テキストを含む場合）：

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

出力に読めない記号が表示された場合は、charset 名を見直すか、ファイルの元のエンコーディングを確認してください。

## よくある質問

**他のドキュメント形式（DOCX、RTF、HTML）でも動作しますか？**  
はい。`LoadOptions` オブジェクトは Aspose.Words がサポートするすべての形式に適用できます。唯一の要件は、対象ファイルが実際に指定した charset を使用していることです。

**ドキュメント読み込み後にエンコーディングを変更したい場合は？**  
エンコーディングは読み取り段階にのみ影響します。`Document` オブジェクトが生成されると、内部の Unicode 表現は元の charset とは無関係になります。出力エンコーディングを変更するには、ファイルを書き出す際に `SaveOptions` を調整してください。

**この手法を他のライブラリ（例: Apache POI）で使用できますか？**  
Apache POI は古いバイナリ形式に対して独自の charset 検出を行いますが、ローダーに charset を指定する概念は類似しています。Aspose.Words では、`LoadOptions` が **エンコーディング指定方法** を制御する公式手段です。

## 結論

これで、Aspose.Words for Java でドキュメントを読み込む際の **エンコーディング指定方法** が分かりました。`LoadOptions` オブジェクトを作成し、`setEncoding` メソッドを呼び出し、オプションを `Document` コンストラクタに渡すことで、ファイルのバイトが正しく解釈されます。この手法により文字化けが防止され、多言語コンテンツがサポートされ、バッチ処理やストリームベースのワークフローにもスムーズに統合できます。

**ドキュメント読み込みオプション**、**特定エンコーディングでの保存**、**Java における Unicode の取り扱い** などの関連トピックを探求し、テキスト処理のスキルを深めてください。さまざまな charset 名で実験したり、PDF 変換と組み合わせたり、複数のエンコーディングでのアップロードを受け付ける Web サービスに統合したりしてみましょう。

コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words を使用した Java での UTF-8 エンコーディングによる RTF テキスト変換方法](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Aspose.Words for Java のオプション設定方法 – 完全ガイド](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Aspose.Words LoadOptions を使用した破損した DOCX Word ドキュメントの復元 – Java ガイド](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}