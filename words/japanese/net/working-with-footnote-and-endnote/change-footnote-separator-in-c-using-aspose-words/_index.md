---
category: general
date: 2026-08-04
description: Aspose.Words を使用した C# で脚注区切り文字を変更 – Word 文書における脚注区切り文字の編集方法と文末脚注区切り文字の変更方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: ja
lastmod: 2026-08-04
og_description: C# と Aspose.Words で脚注の区切り文字を変更します。このガイドでは、脚注の区切り文字の編集、文末脚注の区切り文字のカスタマイズ、そして更新された文書の保存方法を示します。
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: C#で脚注区切り文字を変更する – 完全なAspose.Wordsガイド
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Aspose.Words を使用して C# で脚注セパレータを変更する
url: /ja/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Aspose.Words を使用して脚注の区切り記号を変更する

Word 文書で **脚注の区切り記号を変更** したい場合、このチュートリアルでは Aspose.Words for .NET を使った手順を詳しく解説します。デフォルトの線を記号に置き換えたい場合や、エンドノートの区切りに別のスタイルを適用したい場合でも、以下のコードでフルワークフローを実現できます。

また、**脚注の区切り記号を編集** する方法と、関連する **エンドノートの区切り記号を変更** する操作も学べるので、同一文書内で脚注とエンドノートのスタイリングを統一できます。外部ツールは不要で、C# の数行で完了します。

## 本ガイドで達成できること

このガイドを読み終えると、次のことができるようになります。

* 脚注とエンドノートを含む既存の *.docx* ファイルを読み込む  
* 脚注、脚注の継続、エンドノートの区切りノードにアクセスする  
* 区切り文字を置換する（例: デフォルトの線をアスタリスクに変更）  
* 他のコンテンツを失うことなく、変更後の文書を保存する  

本チュートリアルは、C# の基本的な知識があり、**Aspose.Words** NuGet パッケージ（バージョン 24.9 以降）をインストール済みであることを前提としています。  

---

## 前提条件

| 要件 | 理由 |
|------|------|
| .NET 6.0+ または .NET Framework 4.7.2+ | Aspose.Words の実行に必要なランタイム |
| Aspose.Words for .NET ライブラリ | `Document` と `FootnoteOptions` API を提供 |
| 少なくとも 1 つの脚注またはエンドノートを含む Word ファイル (`input.docx`) | 区切り記号の変更をデモンストレーション |

次の CLI コマンドで Aspose.Words をプロジェクトに追加できます。

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## 手順 1: 脚注を含む文書を読み込む

最初の操作は、ソースファイルを `Document` オブジェクトに読み込むことです。このオブジェクトはメモリ上の Word ファイル全体を表し、すべてのノードにアクセスできます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**なぜこれが重要か:** 文書の読み込みは、あらゆる操作のエントリーポイントです。ファイルが見つからない場合、Aspose.Words は `FileNotFoundException` をスローするため、パスが正しいことを確認してから進めてください。

---

## 手順 2: 脚注とエンドノートの区切りノードにアクセスする

`Document.FootnoteOptions` では、次の 3 つの区切りノードが公開されています。

* `Separator` – 最初のページの脚注コレクションの後に表示される線  
* `ContinuationSeparator` – 脚注が次のページに続くときに使用される線  
* `EndnoteSeparator` – 本文とエンドノート一覧を分ける線  

これらのノードは汎用の `Node` オブジェクトとして取得し、`Run` にキャストしてテキストを変更します。

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**なぜこれが重要か:** これらのノードが、視覚的な区切り文字が格納されている唯一の場所です。別のノード（例: 通常の段落）を変更しても脚注の書式には影響しません。

---

## 手順 3: 脚注の区切り文字を変更する

最も一般的な要件は、デフォルトの線をアスタリスク (`*`) などの記号に置き換えることです。区切りは `Run` として保存されているため、`Text` プロパティを安全に変更できます。

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**なぜこれが重要か:** `Run.Text` を直接編集すると、他の脚注コンテンツに影響を与えることなく、最終文書の視覚表現が更新されます。同様の手法で任意の文字列（Unicode 記号を含む）を適用できます。

---

## 手順 4: エンドノートの区切りを変更する（任意）

**エンドノートの区切りを変更** したい場合も、手順は脚注と同様です。`endnoteSeparator` のテキストを希望の文字に置き換えてください。

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**なぜこれが重要か:** エンドノートは脚注とスタイルが異なることが多いため、別個の区切りを設定することで文書デザインガイドラインに合わせた視覚的一貫性を保てます。

---

## 手順 5: 変更後の文書を保存する

すべての変更が完了したら、`Document.Save` で変更を永続化します。元のファイルを上書きすることも、新しい場所に保存することも可能です。

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**なぜこれが重要か:** `Save` はメモリ上の表現をディスクに書き出し、スタイル・画像・テーブルなど他の要素をそのまま保持します。

---

## 完全な実行可能サンプル

以下に、すべての手順をまとめた単一のコンソール アプリケーション例を示します。

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**期待される結果:** Microsoft Word で *ModifiedSeparators.docx* を開くと、最初の脚注ページ下部の区切り線がアスタリスク (`*`) に置き換わっているはずです。文書にエンドノートが含まれている場合、本文とエンドノート一覧を分ける線はハイフン (`-`) になります。テキスト・画像・テーブルなど他のコンテンツはそのままです。

---

## よくある質問とエッジケースの対処

| 質問 | 回答 |
|------|------|
| **文書に脚注が全くない場合はどうなる？** | `FootnoteOptions.Separator` は依然として `Run` ノードを返しますが、テキストは空になることがあります。コードはノードの型を安全に確認してから変更します。 |
| **複数文字列（例: "***"）を使用できるか？** | はい。`Run.Text` プロパティは任意の文字列、Unicode 文字を含めて受け取れます。 |
| **区切りを変更しても脚注番号は変わらないか？** | 変わりません。区切りは番号付けスキームとは独立しています。 |
| **`Document` オブジェクトは破棄する必要があるか？** | `Document` は内部的に `Node` を通じて `IDisposable` を実装しています。短命なコンソール アプリでは必須ではありませんが、長時間稼働するサービスでは `using` ブロックで囲むことを推奨します。 |
| **.NET Core と .NET Framework の違いは？** | API はランタイム間で同一です。必要なのは対象フレームワークが Aspose.Words パッケージでサポートされていることだけです。 |

**プロのコツ:** セクションごとに異なる区切りを設定したい場合は、`doc.GetChildNodes(NodeType.Footnote, true)` を列挙し、各脚注の `Separator` プロパティを個別に調整できます。高度な操作ですが、複雑な文書で有用です。

---

## まとめ

これで、C# と Aspose.Words を使って Word ファイルの **脚注の区切り記号** と **エンドノートの区切り記号** を変更する方法がマスターできました。ガイドでは、文書の読み込み、対象ノードの取得、テキストの変更、保存までを一つの自己完結型プログラムで解説しました。

ここからは、**脚注の区切り記号のスタイル編集**、脚注番号のカスタマイズ、ページレイアウトに基づく条件付き書式設定など、関連トピックを探求できます。ノードを取得し、`Run` にキャストして `Text` を変更するパターンは、他の多くの Word 処理シナリオでも応用可能です。

コーディングを楽しみながら、記号を変えてみたり、画像を区切りとして埋め込んでみたり、ユニークな文書レイアウトに挑戦してみてください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれているので、API の追加機能を習得したり、代替実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}