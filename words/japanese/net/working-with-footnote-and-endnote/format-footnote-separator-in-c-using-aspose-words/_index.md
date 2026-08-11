---
category: general
date: 2026-08-10
description: Aspose.Words を使用して C# で脚注区切り線をフォーマットし、脚注と文末脚注の線をカスタマイズします。数分で C# の脚注フォーマットを学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: ja
lastmod: 2026-08-10
og_description: C#でAspose.Wordsを使用して脚注区切り線をフォーマットします。このチュートリアルに従って、脚注と文末脚注の区切り線を迅速かつ確実にスタイル設定しましょう。
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: C#で脚注区切り文字をフォーマットする – 完全なAspose.Wordsガイド
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: C# と Aspose.Words を使用して脚注区切り線をフォーマットする
url: /ja/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用した C# での脚注区切り線の書式設定

Word 文書で **脚注区切り線をフォーマット** したい場合は、このガイドで Aspose.Words for .NET を使った手順をご紹介します。区切り段落の配置と色を変更する完全な実行可能サンプルを確認でき、エンドノートの区切り線にも同様の手法を適用する方法が学べます。

このチュートリアルは、ソース ファイルの読み込みから変更後の文書の保存までのすべての手順を網羅しているため、コードをそのまま自分のプロジェクトにコピーペーストして追加の調査なしで利用できます。

## 必要なもの

開始する前に、以下を用意してください。

* .NET 6.0 以降（.NET Framework 4.6 以上でも動作します）
* 有効な Aspose.Words for .NET ライセンス（評価用の無料トライアルでも可）
* 少なくとも 1 つの脚注またはエンドノートを含む Word ファイル（例: `Footnotes.docx`）
* Visual Studio 2022 またはお好みの C# IDE

これらが揃っていれば、環境構築に時間を取られることなく **C# の脚注書式設定** ロジックに集中できます。

## 手順 1: 脚注とエンドノートを含む文書を読み込む

最初の操作は、ソース ファイルを指す `Document` オブジェクトを作成することです。Aspose.Words は DOCX パッケージ全体をメモリに読み込み、脚注やエンドノート ノードへのフルアクセスを提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*重要ポイント*: 文書の読み込みはすべての操作の前提条件です。ファイル パスが間違っていると Aspose.Words は `FileNotFoundException` をスローするため、先にパスを確認してください。

## 手順 2: 区切り線および継続区切り線ノードを取得する

脚注とエンドノートの区切り線は、`Footnotes` と `Endnotes` コレクション内の特別なノードとして格納されています。各コレクションは `Separator` と `ContinuationSeparator` プロパティを公開しており、`Node` 参照を返します。

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*重要ポイント*: `Separator` ノードは、本文と脚注ブロックを視覚的に分離する線を表します。この参照を取得すれば、段落書式やフォント、さらにはノード全体の置き換えも可能です。

## 手順 3: 脚注区切り線のビジュアル スタイルを変更する

多くの Word 文書では、区切り線はダッシュやアスタリスクを含む単一の段落です。以下のコードは、区切り線が `Paragraph` であるかを確認し、該当すれば中央揃えにし、文字色をグレーに変更します。

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### 継続区切り線のスタイリング（オプション）

脚注が複数ページにまたがる場合に表示される継続区切り線も、同様にスタイルを設定できます。

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*重要ポイント*: 区切り線を揃えることで可読性が向上し、色を変えることで通常の段落テキストと区別できます。`ParagraphAlignment.Center` は、ドキュメントのデザイン指針に合わせて `Left` や `Right` に変更可能です。

## 手順 4: 変更後の文書を保存する

希望のスタイルを適用したら、文書をディスクに書き戻します。元のファイルを上書きすることも、新しいバージョンとして保存することもできます。

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

`Footnotes_Styled.docx` を Microsoft Word で開くと、脚注区切り線が中央揃えかつグレーで表示され、コードで指定した通りになっていることが確認できます。

## 応用バリエーション

### エンドノート区切り線の書式設定

文書にエンドノートも含まれる場合は、同じロジックを `Endnotes` コレクションに対して適用できます。

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### 区切り線にカスタム文字列を使用する

区切り線をアスタリスクの連続（`***`）にしたい場合は、既存の Run を新しい Run に置き換えます。

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### 区切り線ノードが存在しない文書の処理

まれに、作者が区切り線ノードを削除した文書があります。その場合 `document.Footnotes.Separator` は `null` を返すので、以下のようにガードします。

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## よくある落とし穴と回避策

| 落とし穴 | 発生理由 | 対策 |
|---------|----------|------|
| **区切り線が `Paragraph` でない** | 一部のテンプレートは `Table` や `Shape` を区切り線として使用している | キャスト前に `is Paragraph` でノード型を確認 |
| **`Runs` コレクションが空** | 区切り線が空の段落であることがある | `Runs.Count > 0` を確認してから `Runs[0]` にアクセス |
| **ライセンスが適用されていない** | ライセンス未設定だと Aspose.Words が透かしを挿入し、API 使用が制限される | プログラム開始時に `License license = new License(); license.SetLicense("Aspose.Words.lic");` を呼び出す |
| **書き込み先フォルダーが読み取り専用** | `Save` メソッドが `UnauthorizedAccessException` をスロー | 保存先ディレクトリに書き込み権限があることを確認 |

これらのポイントを事前に対処すれば、実行時例外を防ぎ、**脚注区切り線の変更** 作業をスムーズに進められます。

## 完全な実行可能サンプル

以下は、上記で説明したすべての手順を網羅した単体コンソール アプリケーションです。新規 .NET コンソール プロジェクトにコードを貼り付け、ファイル パスを置き換えて実行してください。

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**期待される結果**  

`Footnotes_Styled.docx` を開くと:

* 脚注区切り線が本文下部で中央揃えになる
* 文字色が薄いグレーになり、通常の段落テキストと視覚的に区別できる
* 文書にエンドノートが含まれている場合、エンドノートの区切り線も同様に中央揃えかつグレーになる

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれているので、API の追加機能を習得したり、独自の実装アプローチを探求したりする際に役立ちます。

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}