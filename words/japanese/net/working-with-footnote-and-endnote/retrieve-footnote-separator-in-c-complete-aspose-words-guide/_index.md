---
category: general
date: 2026-08-07
description: Aspose.Words for .NET を使用して脚注区切り文字を取得する。脚注と文末脚注の区切り文字の抽出方法、ノードタイプの確認、C#
  での変更方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: ja
lastmod: 2026-08-07
og_description: Aspose.Words for .NET を使用して脚注区切り文字を取得します。このガイドでは、脚注と文末脚注の区切り文字を抽出し、ノードの種類を確認し、変更を保存する方法を示します。
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: C#で脚注区切り文字を取得する – ステップバイステップ Aspose.Words チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: C#で脚注区切りを取得する – 完全な Aspose.Words ガイド
url: /ja/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で脚注区切り文字を取得する – 完全な Aspose.Words ガイド

Word 文書から **retrieve footnote separator** を取得する必要がある場合、このチュートリアルでは Aspose.Words for .NET を使用してその手順を正確に示します。ドキュメント処理サービスを構築している場合でも、脚注の書式を整理している場合でも、脚注と文末脚注の両方の区切り文字を抽出する完全な実行可能サンプルが確認できます。

このガイドでは、`.docx` ファイルの読み込み方法、`FootnoteSeparator` と `EndnoteSeparator` プロパティの呼び出し方、返される `Node` オブジェクトの検査方法、そしてオプションで区切り線を置き換える方法を学びます。外部ドキュメントは不要です—必要な情報はすべて以下に含まれています。

## 前提条件

* .NET 6.0 以降（コードは .NET Framework 4.7.2 でも動作します）
* Aspose.Words for .NET NuGet パッケージ（バージョン 24.9 以降）
* 脚注や文末脚注を含む Word 文書（例: `Footnotes.docx`）

以下の CLI コマンドで Aspose.Words パッケージを追加できます。

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## 手順 1: プロジェクトの設定と名前空間のインポート

新しいコンソールプロジェクトを作成するか、既存のプロジェクトにコードを追加してください。必要な `using` ディレクティブは以下に示します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

これらの名前空間により、`Document` クラス、`Node` 階層、そして **retrieve footnote separator** 操作に必要な `NodeType` 列挙型にアクセスできます。

## 手順 2: 脚注と文末脚注を含む文書をロードする

Aspose.Words のワークフローで最初に行う操作はソースファイルのロードです。プレースホルダーのパスを実際の `.docx` の場所に置き換えてください。

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

ファイルをロードすると内部のノードツリーが構築されます。**retrieve footnote separator** にとっては、このツリー内に区切りノードが存在するため重要です。

## 手順 3: 脚注区切りノードを取得する

これで、`Document` オブジェクトの `FootnoteSeparator` プロパティにアクセスすることで **retrieve footnote separator** が可能になります。このノードは脚注と本文テキストを分ける線を表します。

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

標準的な区切り線の場合、`NodeType` は `Paragraph` になります。ノードタイプを把握することで、区切り線を変更するか完全に置き換えるかを判断できます。

## 手順 4: 文末脚注区切りノードを取得する

同様に、`EndnoteSeparator` プロパティを使用して **retrieve endnote separator** が可能です。このノードは文末脚注と本文を分けます。

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

ほとんどの文書では、両方の区切りノードは同じ `NodeType`（`Paragraph`）を共有しますが、個別にカスタマイズすることも可能です。

## 手順 5: 区切りコンテンツの検査または変更（オプション）

区切り線の見た目を変更したい場合（例: ダッシュの線を細い罫線に置き換える）には、`Paragraph` ノードを直接編集できます。以下は、デフォルトの区切りテキストをカスタム文字列に置き換える例です。

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

ノードを変更した後、文書を保存すれば Word で変更が反映されたことを確認できます。

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## 期待されるコンソール出力

元の `Footnotes.docx` でプログラムを実行すると、以下のような出力が得られるはずです。

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

`Footnotes_Updated.docx` を Microsoft Word で開くと、脚注と文末脚注の区切りが挿入したカスタムテキストで表示されます。

## よくある質問とエッジケース

**文書に脚注がない場合はどうなりますか？**  
`FootnoteSeparator` プロパティは、Word が常に区切りプレースホルダーを含むため、`Paragraph` ノードを返します。そのノードは空なので、コンテンツを安全に追加するか、そのままにしておくことができます。

**特定のセクションの区切りを取得できますか？**  
脚注と文末脚注の区切りは文書全体に対して適用され、セクション単位ではありません。セクションレベルで制御したい場合は、グローバルな区切りノードではなく `Section.FootnoteOptions` と `Section.EndnoteOptions` を使用する必要があります。

**.NET Core でも動作しますか？**  
はい。Aspose.Words for .NET はクロスプラットフォームで、同じコードが .NET 6+ の Windows、Linux、macOS で動作します。

**期待されるノードタイプは何ですか？**  
`FootnoteSeparator` と `EndnoteSeparator` はどちらも `Paragraph` ノード（`NodeType.Paragraph`）を返します。別のタイプが返された場合、文書が破損している可能性があるので、再度ロードするかソースファイルを検証してください。

## 簡単にコピー＆ペーストできる完全なソースコード

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

コードを `Program.cs` にコピーし、ファイルパスを調整して `dotnet run` を実行してください。このプログラムは、文書のロードから変更の永続化まで、**retrieve footnote separator** の全工程を示します。

## 結論

これで、Aspose.Words for .NET を使用して **retrieve footnote separator** と **endnote separator retrieval** を行い、`document node type` を検査し、必要に応じてコンテンツを置き換える方法が分かりました。この手法により、脚注の書式設定を自動化したり、カスタム区切り線を生成したり、任意の C# アプリケーションで文書構造を検証したりできます。

次に、個々の脚注テキストを取得する **C# footnote extraction** や、`FootnoteOptions` を使用して **modify footnote reference marks** を学ぶなど、関連トピックを探求してみてください。これらの概念はすべて、本稿で取り上げたノードツリーの基礎に直接基づいています。

コーディングを楽しんでください。また、プロジェクトのブランディングに合わせてさまざまな区切りスタイルを試してみてください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [脚注と文末脚注を使用したワード処理](/words/english/net/working-with-footnote-and-endnote/)
- [Aspose.Words for .NET の Document Builder を使用したコンテンツ追加](/words/english/net/add-content-using-document-builder/)
- [脚注と文末脚注の操作](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}