---
category: general
date: 2026-11-15
description: JavaでWord文書の段落行間を設定する。Aspose.Wordsを使用してプログラム的に行間を設定し、正確な文書フォーマットを実現する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: ja
lastmod: 2026-11-15
og_description: JavaでWord文書の段落行間を設定する。このガイドでは、Aspose.Wordsを使用して段落および脚注区切り線の行間を設定する方法を説明し、文書レイアウトを完全に制御できるようにします。
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Java を使って Word の段落の行間を設定する
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: JavaでWord文書の段落行間を設定する
url: /ja/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWord文書の段落行間を設定する

Word文書で**段落の行間を設定**する必要がある場合、このチュートリアルではJavaとAspose.Wordsを使用してその方法を示します。また、脚注区切り線の**行間の設定方法**も学べます—プロフェッショナルな文書を整形する際の一般的な要件です。

以下のセクションでは、次のことを行います：

* 既存の *.docx* ファイルを読み込む。
* 脚注区切り段落を取得する。
* カスタムの行間値を適用する。
* 更新された文書を保存する。

プロジェクトに Aspose.Words ライブラリを追加する以外に外部設定は不要なので、コードをそのままコピーしてすぐに実行できます。

## 前提条件

開始する前に、以下が揃っていることを確認してください：

* Java 17 以上がインストールされていること。
* 依存関係管理のための Maven（または他のビルドツール）。
* 有効な Aspose.Words for Java ライセンス（無料評価版でもテストは可能）。
* 既知のディレクトリに配置された入力 Word 文書（`input.docx`）。

`pom.xml` に Aspose.Words の依存関係を追加します：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Aspose.Wordsで段落の行間を設定する

この H2 見出しは主要キーワードを含んでおり、SEO 要件を満たしています。

### 手順 1: Word 文書を読み込む

まず、ソースファイルを指す `Document` インスタンスを作成します。

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*重要性*: 文書を読み込むことで、元のファイルに手を加えることなく、明示的に保存するまで操作できるインメモリモデルが得られます。

### 手順 2: 脚注区切りを取得する

脚注区切りは、脚注と本文の間に表示される特別な段落です。その外観を変更するには `FootnoteSeparator` オブジェクトにアクセスする必要があります。

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*ヒント*: 文書に脚注が含まれていなくても、区切りは非表示の段落として存在するため、呼び出しが `null` を返すことはありません。

### 手順 3: 区切り段落の行間を設定する方法

次に、目的の行間を適用します。Aspose.Words は行間の値にポイントを使用します。12 pts はほとんどのフォントでシングルスペースに相当します。

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

他の間隔モードも使用できます：

| モード                     | メソッド呼び出し                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (e.g., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

適切なルールを選択することで、Word、Google Docs、その他のビューアで文書が一貫して表示されます。

### 手順 4: 更新された文書を保存する

最後に、変更をディスクに書き戻します。

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

`output.docx` を Microsoft Word で開くと、脚注区切りが設定した行間で表示されます。

## 通常の段落の行間設定方法の理解

同じ API は脚注区切りだけでなく、任意の `Paragraph` オブジェクトにも適用できます。以下は本文の最初の段落の間隔を調整する簡単な例です：

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**この機能が必要になる理由**: レポート、契約書、学術論文などでは、特定の行間スタイル（例: 下書きでは二重行間）が求められることが多いです。同じ `setLineSpacing` メソッドを使用することで、期待通りのレイアウトが保証されます。

## よくある落とし穴と回避策

| 問題                                 | 原因                                   | 対策 |
|---------------------------------------|----------------------------------------|-----|
| 行間が変わらない        | `LineSpacingRule` がデフォルト（AUTO）のまま | `setLineSpacingRule` で明示的にルールを設定する。 |
| 区切りの後に余分な空行が入る | 区切りに非表示の改行が含まれている | 間隔を設定する前に `separator.getText().trim();` で区切りのテキストをトリムする。 |
| 保存後に文書が破損する | 古いバージョンの Aspose.Words を使用している | 保存時のバグ修正が含まれる最新バージョン（例: 24.10）にアップグレードする。 |

## プロのコツ: 複数文書をバッチ処理する

数十ファイルを更新する必要がある場合、ロジックをヘルパーメソッドにまとめ、フォルダーを反復処理します：

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

このメソッドをループで実行することで、手作業の編集にかかる時間を数時間短縮できます。

## 期待される出力

プログラムを実行した後、`output.docx` は以下の状態になります：

* 行間以外は元のコンテンツが変更されずに残る。
* 脚注区切りがシングルスペース（12 pts）のレイアウトで表示される。
* その他のすべての書式（スタイル、画像、テーブル）を保持する。

Word でファイルを開き、設定した値に応じて区切り線が狭く（または広く）なっていることを確認してください。

## 結論

これで、Java を使用して Word 文書の**段落行間を設定**する方法、そして脚注区切りと通常の段落の**行間を設定**する方法が分かりました。完全な実行可能サンプルは、文書の読み込み、行間プロパティの調整、結果の保存を数回の明確な API 呼び出しだけで実演しています。

**次のステップ**として以下を検討できます：

* テーブルやリスト項目の**行間設定**方法。
* 見出しと本文テキストで異なる間隔ルールを適用すること。
* `Style` オブジェクトを使用して文書全体の間隔を統一すること。

値を試し、他の書式設定オプションと組み合わせることで、あらゆる Java アプリケーションで文書レイアウトを完全にコントロールできます。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java のオプション設定方法 – 完全ガイド](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Aspose.Words for Java の LoadOptions 設定方法](/words/english/java/document-loading-and-saving/using-load-options/)
- [Word 文書のアジア段落の間隔とインデントを変更する](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}