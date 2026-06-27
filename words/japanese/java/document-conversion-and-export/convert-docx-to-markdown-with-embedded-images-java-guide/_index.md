---
category: general
date: 2026-06-27
description: Aspose.Words for Java を使用して docx を markdown に変換します。画像を base64 で埋め込む方法と、Word
  文書を手軽に markdown にエクスポートする方法を学びましょう。
draft: false
keywords:
- convert docx to markdown
- embed images as base64
- how to embed images markdown
- export word document to markdown
- convert docx to markdown with images
language: ja
og_description: Aspose.Words for Java を使用して docx を markdown に変換します。このチュートリアルでは、画像を
  base64 として埋め込み、Word 文書を単一のフローで markdown にエクスポートする方法を示します。
og_title: 埋め込み画像付きでdocxをMarkdownに変換 – Javaガイド
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  headline: convert docx to markdown with embedded images – Java guide
  type: TechArticle
- description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  name: convert docx to markdown with embedded images – Java guide
  steps:
  - name: Read the image file into a byte array (`Files.readAllBytes`).
    text: Read the image file into a byte array (`Files.readAllBytes`).
  - name: Encode with `Base64.getEncoder().encodeToString`.
    text: Encode with `Base64.getEncoder().encodeToString`.
  - name: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
    text: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: 埋め込み画像付きでdocxをMarkdownに変換 – Javaガイド
url: /ja/java/document-conversion-and-export/convert-docx-to-markdown-with-embedded-images-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx を markdown に変換し、画像埋め込み – Java ガイド

画像が消えてしまったりリンク切れになったりして、**docx を markdown に変換**したいと思ったことはありませんか？ あなただけではありません。多くのプロジェクト—静的サイトジェネレータ、ドキュメントパイプライン、またはクイックプレビュー—では画像を保持することが必須で、一般的なコンバータはそれらを落としてしまうことが多いです。

幸い、Aspose.Words for Java を使えば、**画像を base64 として埋め込む**というシンプルな方法で Markdown 内に直接画像を埋め込めるため、出力ファイルは真にポータブルになります。このガイドでは、Word ファイルの読み込み、Markdown 保存オプションの設定、画像リソースの処理、そして最終的な保存までの全工程を解説します。最後まで読むと、**markdown に画像を埋め込む方法**が正確に分かり、Maven や Gradle プロジェクトにすぐ貼り付けて実行できるコードスニペットが手に入ります。

## 必要なもの

- Java 17 以上（API は古いバージョンでも動作しますが、17 が推奨です）。
- Aspose.Words for Java ライブラリ（最新の JAR は Maven Central から取得できます：`com.aspose:aspose-words:23.12`）。
- 変換したい `.docx` ファイル（ここでは `Report.docx` と呼びます）。
- 使いやすい IDE（IntelliJ IDEA、Eclipse、または Java 拡張機能付きの VS Code など）。

追加の画像処理ツールは不要です—ライブラリが内部で全て処理します。

## Step 1: Word ドキュメントの読み込み – **docx を markdown に変換** の基礎

最初に行うのは、ソースファイルを指す `Document` インスタンスを作成することです。このオブジェクトは、段落や表、そしてもちろん画像も含んだ Word ファイルのメモリ上の表現と考えてください。

```java
import com.aspose.words.*;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");
        // … we’ll configure options next
    }
}
```

> **プロのコツ:** docx をストリーム（例：アップロードされたファイル）から読み込む場合は、`Document` コンストラクタに `InputStream` を渡すことができます—Web アプリに最適です。

## Step 2: MarkdownSaveOptions の設定 – **画像を base64 として埋め込む** マジック

Aspose.Words には `MarkdownSaveOptions` クラスが用意されており、変換の挙動を細かく調整できます。画像を保持する鍵は `IResourceSavingCallback` です。コールバック内で各画像ストリームを捕捉し、Base64 文字列に変換し、リソース名をデータ URI に書き換えます。

```java
import java.io.ByteArrayOutputStream;
import java.util.Base64;
import com.aspose.words.*;

MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();

// Embed images directly as Base64 data URIs
markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) throws Exception {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Copy the image stream to a byte array
            ByteArrayOutputStream baos = new ByteArrayOutputStream();
            args.getStream().copyTo(baos);
            // Encode the bytes as Base64
            String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
            // Build a data URI (png assumed, adjust if needed)
            args.setResourceFileName("data:image/png;base64," + base64);
            // Close the original stream – we no longer need it
            args.setKeepResourceStreamOpen(false);
        }
    }
});
```

なぜこの追加手順が必要かというと、**Word ドキュメントを markdown にエクスポート**する際にコールバックを使用しないと、画像が別フォルダーに出力され相対パスで参照されます。そのパスは Markdown ファイルを移動した時に壊れやすく、特に CI パイプラインで問題になります。画像を Base64 文字列として埋め込むことで、Markdown は単一の自己完結型アーティファクトとなり、GitHub の README や外部アセットをサポートしない静的サイトジェネレータに最適です。

### 異なる画像フォーマットの取り扱い

上記のスニペットは PNG（`image/png`）を想定しています。ソースの Word に JPEG が含まれている場合は、元のコンテンツタイプを確認できます：

```java
String mime = args.getContentType(); // e.g., "image/jpeg"
args.setResourceFileName("data:" + mime + ";base64," + base64);
```

この小さな調整により、元のフォーマットに関係なく、生成された Markdown が正しく表示されます。

## Step 3: ファイルの保存 – **Word ドキュメントを markdown にエクスポート** 最終ステップ

オプションの設定が完了したら、`document.save` を呼び出し、保存先パスと設定した `MarkdownSaveOptions` を渡すだけです。ライブラリが重い処理を行い、ドキュメントツリーを走査し、段落を Markdown 構文に変換し、適切な場所に Base64 画像を挿入します。

```java
// Save the document as Markdown with embedded Base64 images
document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
System.out.println("Conversion complete! Check Report.md");
```

任意の Markdown ビューア（VS Code、GitHub、Typora など）で `Report.md` を開くと、画像がインラインで表示され、余分なファイルは不要です。

## Step 4: 完全な実行可能サンプル – **画像付きで docx を markdown に変換** を一括で

すべてをまとめると、以下がコピー＆ペースト、コンパイル、実行できる完全なプログラムです：

```java
import com.aspose.words.*;
import java.io.*;
import java.util.Base64;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");

        // 2️⃣ Set up Markdown save options with Base64 image embedding
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    ByteArrayOutputStream baos = new ByteArrayOutputStream();
                    args.getStream().copyTo(baos);
                    String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
                    String mime = args.getContentType(); // Preserve original MIME type
                    args.setResourceFileName("data:" + mime + ";base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                }
            }
        });

        // 3️⃣ Save as Markdown – this is where we **export word document to markdown**
        document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
        System.out.println("✅ convert docx to markdown with embedded images finished.");
    }
}
```

### 期待される出力

`Report.md` を開くと、以下のような内容が表示されます：

```markdown
# Sample Report

Here is an introductory paragraph.

![Image](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...==)

Another paragraph follows.
```

長い Base64 文字列は画像データを表しています。多くのエディタは UI 上で文字列を省略表示しますが、プレビュー時には画像が正しく表示されます。

## よくある落とし穴と回避策

| 問題 | 発生原因 | 対策 |
|------|----------------|-----|
| 画像がリンク切れになる | `ResourceType` のチェックが欠けていたためコールバックが呼び出されなかった。 | `if (args.getResourceType() == ResourceType.IMAGE)` でロジックを囲むようにしてください。 |
| 出力ファイルが巨大になる | Base64 にエンコードするとデータが約 33% 増加するため。 | 可搬性のためのトレードオフとして受け入れるか、サイズが問題なら外部画像に切り替えてください。 |
| 画像フォーマットが間違っている | JPEG に対してハードコードされた `image/png` を使用している。 | 元の MIME タイプを保持するために `args.getContentType()` を使用してください。 |
| 大きなドキュメントでメモリ不足になる | 巨大な DOCX をメモリに読み込んでいるため。 | ドキュメントを分割して処理するか、JVM ヒープを増やしてください（例：`-Xmx2g`）。 |

## 他のコンテキストで **markdown に画像を埋め込む方法** が必要なとき

Aspose.Words を使用しない場合でも Base64 画像を埋め込みたい場合、原理は同じです：

1. 画像ファイルをバイト配列に読み込む（`Files.readAllBytes`）。
2. `Base64.getEncoder().encodeToString` でエンコードする。
3. Markdown 文字列にデータ URI を挿入する：`![alt](data:image/png;base64,${base64})`。

ライブラリはこれを自動化してくれるので、ループを書かずに済みます。

## 次のステップ – 変換の拡張

これで **画像付きで docx を markdown に変換** をマスターしたので、以下の拡張を検討してください：

- **スタイル保持**：まず `HtmlSaveOptions` を使用し、次に flexmark‑java などのツールで HTML を Markdown に変換してリッチな書式を実現します。
- **表の取り扱い**：Aspose は既に表を変換しますが、`markdownOptions.setTableAlignment` で列の配置を微調整できます。
- **バッチ処理**：上記コードをディレクトリスキャナでラップし、数十件のレポートを自動的に変換します。
- **CI との統合**：JAR をビルドパイプラインに追加し、コミットごとにドキュメントを生成します。

これらのアイデアはすべて、ここで扱ったコア概念に基づいているため、コードの適応が容易に感じられるでしょう。

## 結論

ここでは、**docx を markdown に変換**し、すべての画像を Base64 文字列として埋め込む完全なエンドツーエンドのソリューションを紹介しました。重要な手順—ドキュメントの読み込み、カスタム `IResourceSavingCallback` を使用した `MarkdownSaveOptions` の設定、ファイルの保存—はシンプルで、Aspose.Words for Java ですぐに動作します。

この知識を活用すれば、ドキュメントパイプラインの自動化、ポータブルな Markdown レポートの生成、あるいは Word コンテンツの単一ファイル版の保持が可能です。SVG の取り扱いや見出しレベルのカスタマイズなど、さらなる調整に興味がある場合は、Aspose.Words API ドキュメントを参照してください。豊富なサンプルが本ガイドを補完しています。

コーディングを楽しんで、あなたの Markdown が常に画像豊富でありますように！

![docx を markdown に変換する図](convert-docx-to-markdown.png "docx を markdown に変換")

---


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを検討したりするのに役立ちます。

- [DOCX を変換するときに Markdown に画像を埋め込む方法](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Aspose.Words for Java で Markdown をエクスポートする方法](/words/english/java/document-loading-and-saving/saving-documents-as-markdown/)
- [docx を markdown に変換 – Aspose.Words で数式を LaTeX にエクスポート](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}