---
category: general
date: 2026-09-08
description: Aspose.Words for .NET を使用して Word 文書をロードする際に、エンドノートの区切り文字を取得し、フットノートの区切り文字を表示します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: ja
lastmod: 2026-09-08
og_description: Aspose.Words for .NET を使用して Word 文書をロードする際に、文末脚注の区切り文字を取得し、脚注の区切り文字を表示します。
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: C#でWord文書を読み込むときに文末脚注区切りを取得する
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: C#でWord文書を読み込むときに文末脚注の区切りを取得する
url: /ja/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でWord文書を読み込む際のエンドノート区切り文字の取得

Wordファイルから**エンドノート区切り文字**を取得する必要がある場合、このガイドではその手順を正確に示します。また、Aspose.Wordsを使用して**Word文書をロード**し、コンソールに**フットノート区切り文字**テキストを**表示**する方法も学べます。すべてが単一の実行可能なサンプルで示されています。

フットノートとエンドノートの操作は、法務、学術、出版アプリケーションで一般的な要件です。このチュートリアルでは、ファイルのオープンから区切り文字が存在しない場合の処理まで、必要なすべてをカバーしています。これにより、推測せずに任意の.NETプロジェクトにソリューションを統合できます。

## 本チュートリアルでカバーする内容

* Aspose.Words API を使用して **Word文書をロード**する方法。  
* **エンドノート区切り文字**を取得する方法と、区切り文字が重要な理由。  
* デバッグやロギングのためにコンソールに **フットノート区切り文字** を **表示**する方法。  
* 文書にフットノートまたはエンドノートが含まれない場合のエッジケース処理。  
* .NET 6 以降で動作する、完全なコピー＆ペースト可能なコードサンプル。

### 前提条件

| Requirement | Reason |
|-------------|--------|
| .NET 6 SDK or newer | C#サンプルのランタイムを提供します。 |
| Aspose.Words for .NET (NuGet package `Aspose.Words`) | `Document.Footnotes` と `Document.Endnotes` を公開するライブラリです。 |
| A Word file (`Footnotes.docx`) that contains at least one footnote or endnote | 区切り文字のデモンストレーションに使用します。 |
| Any IDE (Visual Studio, Rider, VS Code) | プログラムのコンパイルと実行のため。 |

> **プロのコツ:** フットノート付きの文書がない場合は、Microsoft Wordで手早く作成してください: Insert → Footnote → テキストを入力し、`Footnotes.docx` として保存します。

## Aspose.WordsでWord文書をロードする

最初のステップは **Word文書をロード**してメモリに読み込むことです。Aspose.Words はファイル形式を読み取り、クエリ可能なオブジェクトモデルを構築します。

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Why this matters*: ドキュメントのロードは、以降のすべての操作の前提条件です。ファイルパスが間違っていると `Document` は `FileNotFoundException` をスローするため、実行前にパスを確認してください。

## フットノート区切り段落の取得

フットノート区切りは、本文とフットノート一覧を視覚的に分離する段落です。これを取得することで、書式を検査または変更できます。

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Why this matters*: **フットノート区切り文字の表示**は、正しい段落が取得されているかを確認するのに役立ちます。特にカスタムスタイル（例: 線や特定のフォント）を適用する必要がある場合に有用です。

## エンドノート区切り段落の取得

ここで **エンドノート区切り文字** を取得します。手順はフットノートの処理と同様ですが、`Endnotes` コレクションを使用します。

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Why this matters*: **エンドノート区切り文字の取得**は、本文とエンドノート一覧の視覚的な区切りを調整する際に不可欠です。章の最後にエンドノートが表示される学術出版でよく使用されます。

### 区切り文字がない場合の処理

`Footnotes.Separator` と `Endnotes.Separator` は、文書で区切り文字が定義されていない場合 `null` を返します。`GetText()` を呼び出す前に必ず `null` をチェックし、`NullReferenceException` を回避してください。デフォルトの区切り文字が必要な場合は、以下のように作成できます:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

このコードは最小限の区切り文字を挿入し、以降の処理がその存在に依存できるようにします。

## 期待されるコンソール出力

サンプルがフットノートとエンドノートをそれぞれ1つ含む文書に対して実行されると、以下のような出力が得られるはずです:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

文書にフットノートまたはエンドノートがない場合、プログラムは対応する「見つかりません」メッセージを出力し、エラーハンドリングが適切に行われていることを示します。

## 完全な実行可能サンプル

以下は、新しい C# コンソールプロジェクトにコピーできる完全なプログラムです。追加のコードは不要です。

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

`Program.cs` として保存し、Aspose.Words NuGet パッケージ（`dotnet add package Aspose.Words`）を追加して、`dotnet run` を実行してください。プログラムは区切り文字のテキストを出力するか、存在しない場合はその旨を通知します。

## 一般的なバリエーションと想定シナリオ

| Scenario | How to adapt the code |
|----------|-----------------------|
| **複数のカスタム区切り文字** | デフォルトを置き換えるには `doc.Footnotes.Separator` を使用し、追加の区切り段落は `doc.Footnotes.Add(separatorParagraph)` で手動で追加します。 |
| **区切り文字のスタイル変更** | 区切り文字を取得した後、`ParagraphFormat` を変更します（例: `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`）。 |
| **.doc ファイルの取り扱い** | 同じ API が使用できます。ファイルパスが `.doc` で終わっていることを確認してください。 |
| **多数の文書を処理する** | `foreach` ループでロードと区切り文字取得をラップします。`Document` インスタンスを再利用する場合は、`doc = new Document(path)` でリセットしてください。 |

## ベストプラクティスチェックリスト

- ✅ **`null` を常にチェック**してから区切り文字テキストにアクセスしてください。  
- ✅ **`GetText()` の結果を `Trim`** して、隠れた改行文字を除去してください。  
- ✅ バッチ処理で多数のファイルを扱う場合は、大きな `Document` オブジェクトを **Dispose** してください（`using` を使用するか `doc.Dispose()` を呼び出す）。  
- ✅ 区切り文字テキストは開発時のみ **ログ** に記録し、本番ログでの露出は必要な場合を除き避けてください。  

## 結論

これで、.NET コンソールアプリケーションで **Word文書をロード**しながら **エンドノート区切り文字を取得**し、**フットノート区切り文字を表示**する方法が分かりました。完全なサンプルは、ロード、クエリ、そして区切り文字が欠如している場合の安全な処理を示しており、フットノートやエンドノートの操作タスクの確固たる基盤となります。

次に、以下のことを検討してみてください：

* **フットノート/エンドノートの書式カスタマイズ** – フォント、枠線、番号付けスタイルを調整します。  
* **フットノート/エンドノートの内容抽出** – `doc.Footnotes` または `doc.Endnotes` コレクションを反復処理します。  
* **変更後の文書の保存** – `doc.Save("output.docx")` を使用して変更を永続化します。  

さまざまな Word ファイル、区切り文字スタイル、Aspose.Words の機能を自由に試してみてください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Aspose.Words LoadOptions を使用した Word 文書のロード方法](/words/english/net/programming-with-loadoptions/)
- [Word 文書で段落スタイル区切り文字を取得する](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Aspose.Words for .NET で Word 文書を作成およびスタイル設定する](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}