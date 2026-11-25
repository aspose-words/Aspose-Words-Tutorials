---
category: general
date: 2026-11-25
description: Word文書の作成方法、長方形シェイプの追加、AIによる文書の要約、AIを使ったテキストの翻訳、そして Aspose.Words を使用して
  DOCX として保存する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: ja
lastmod: 2026-11-25
og_description: Word文書を作成し、長方形の図形を追加し、AIで文書を要約し、AIでテキストを翻訳し、DOCXとして保存する—すべてを1つのC#チュートリアルで実現。
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: C#でシェイプ、AI要約、翻訳を含むWord文書を作成する
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: C#でシェイプ、AI要約、翻訳を含むWord文書を作成する方法
url: /ja/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でシェイプ、AI 要約、翻訳を含む Word 文書を作成する方法

プログラムで **Word 文書を作成** する必要がある場合、このガイドで具体的な手順を示します。Aspose.Words for .NET を使用して、**矩形シェイプの追加**、AI サービスを呼び出して **AI で文書を要約**、段落を **AI を使ってテキストを翻訳**、そして最終的に **DOCX として文書を保存** する方法を学びます。

多くの開発者は、文書自動化と最新の AI 機能を組み合わせるのに苦労しています。このチュートリアルの最後までに、視覚的シェイプ、AI 生成の要約、マルチ言語コンテンツを備えた完全にフォーマットされた *.docx* ファイルを生成する、単一の自己完結型 C# プロジェクトが手に入ります。

## 前提条件

- .NET 6.0 SDK またはそれ以降がインストールされていること  
- Visual Studio 2022（または任意の C# IDE）  
- Aspose.Words for .NET のライセンス（または無料評価キー）  
- AI 要約および翻訳呼び出しのためのインターネット接続  

`Aspose.Words` と `Aspose.Words.AI` 以外に追加の NuGet パッケージは必要ありません。

## 手順 1: プロジェクトのセットアップと必要なパッケージの追加

新しいコンソール プロジェクトを作成し、Aspose.Words ライブラリを追加します。

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **プロのコツ:** 評価モードを使用する場合は、`Main` の早い段階で `Aspose.Words.License.SetLicense("Aspose.Words.lic");` を呼び出して、透かしを回避してください。

## 手順 2: 文書の初期化 – **create word document** のコア

最初の実行可能なコード行は新しい **Word 文書** オブジェクトを作成します。このオブジェクトは以降のすべての操作のキャンバスとなります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` は、低レベルのノードツリーを手動で扱うことなく、テキスト、シェイプ、コントロールの挿入を簡素化します。

## 手順 3: 文書に **Add rectangle shape** を追加

矩形シェイプは、視覚的なプレースホルダー、ラベルの背景、またはシンプルなグラフィックとして使用できます。まず `GroupShape` を作成し、その中に `Rectangle` を挿入します。

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

この矩形は幅 100 ポイント、高さ 50 ポイントです。`GroupShape` 内にあるため、後でテキスト ボックスなどの要素を追加してもレイアウトの衝突を心配する必要はありません。

## 手順 4: プレーンテキストの StructuredDocumentTag (SDT) を挿入

StructuredDocumentTag オブジェクトは、後でデータ ソースにバインドできるコンテンツ コントロールに便利です。

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

`true` フラグはタグを **repeating** コントロールとしてマークし、テンプレートに便利です。

## 手順 5: ActiveX CommandButton コントロールを追加 (オプション UI)

生成された文書が ActiveX をサポートする環境で使用される場合、ボタンを埋め込むことができます。

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

この手順はオプションです。対象ユーザーが Windows 環境で文書とやり取りしない場合は削除できます。

## 手順 6: **Summarize document with AI**

Aspose.Words.AI は大規模言語モデルサービスの便利なラッパーを提供します。ここでは OpenAI バックエンドを使用して `DocumentSummarizer.Summarize` を呼び出します。

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

このメソッドは現在のノードツリーを分析し、最も関連性の高い文を抽出して簡潔な段落を返します。これが **summarize document with AI** 機能のコアです。

## 手順 7: **Translate text using AI**

次に、サンプル文字列を英語からフランス語に翻訳する方法を示します。`Translator.Translate` メソッドは内部で Google AI モデルを呼び出します。

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

`Language.French` を任意のサポートされている言語列挙値に置き換えることで、リアルタイムにマルチ言語文書を生成できます。

## 手順 8: **Save document as DOCX**

最後に、編集した文書をディスクに保存します。`.docx` 拡張子を指定すると、`Save` メソッドは自動的に *.docx* ファイルを書き出します。

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

ファイル `Result.docx` には現在以下が含まれます：

- グループシェイプ内の矩形シェイプ  
- プレーンテキストのコンテンツ コントロール (SDT)  
- ActiveX CommandButton（手順 5 を残した場合）  
- AI 生成の要約段落  
- “Hello world” のフランス語訳  

Microsoft Word でファイルを開き、各要素を確認できます。

## 完全なソースコード

以下は完全に実行可能なプログラムです。`Program.cs` にコピーし、`dotnet run` を実行してください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### 期待される出力

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

`Result.docx` を開くと、上部付近に矩形シェイプ、SDT プレースホルダー、ボタン、要約段落、そしてプレーンテキストとして挿入されたフランス語訳が表示されます。

## 結論

これで、**Word 文書をゼロから作成**し、**矩形シェイプを追加**、**AI で文書を要約**、**AI を使ってテキストを翻訳**、そして **DOCX として保存** する方法が分かりました—すべて数行の C# コードで実現できます。このパターンはスケーラブルで、ハードコードされた文字列を動的データに置き換えたり、シェイプやチャートを追加したり、`SummarizerOptions` や `Translator` パラメータを調整して AI プロバイダーを切り替えることができます。

### 次にやることは？

- **add rectangle shape** のバリエーションを探求：塗りつぶし色、線のスタイルを変更したり、シェイプ内にテキストを追加したりできます。  
- 大規模な文書で **summarize document with AI** を使用し、エグゼクティブサマリーを自動生成します。  
- **translate text using AI** を拡張して、段落やテーブル全体をバッチ処理し、マルチ言語レポートを作成します。  
- Aspose.Words のチャート API を組み合わせ、AI 生成インサイトと共にデータ可視化を埋め込みます。  

自由に試してみて、結果をコメントや GitHub で共有してください。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれ、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [空白の Word 文書を作成し、矩形シェイプを追加する](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Aspose.Words for .NET を使用して Word 文書にグループシェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET を使用して Word 文書にテキスト透かしを追加する](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}