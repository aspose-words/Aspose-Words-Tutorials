---
category: general
date: 2026-08-04
description: C# を使用してプログラムで Word 文書を作成します。Word にコンテンツコントロールを追加し、動的テンプレート用のプレースホルダー
  テキストを設定する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: ja
lastmod: 2026-08-04
og_description: C#でプログラム的にWord文書を作成する。このガイドでは、Wordにコンテンツコントロールを追加し、再利用可能なテンプレート用のプレースホルダー
  テキストを設定する方法を示します。
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: プログラムでWord文書を作成 – コンテンツコントロールとプレースホルダーを追加
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Word文書をプログラムで作成 – コンテンツコントロールとプレースホルダーを追加
url: /ja/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プログラムで Word 文書を作成 – コンテンツコントロールとプレースホルダーの追加

Word 文書を **プログラムで作成** したい場合、このチュートリアルでは完全に実行可能なソリューションを示します。**Word にコンテンツコントロールを追加**し、意味のあるタイトルを付け、**プレースホルダー テキスト** を設定して、エンドユーザーが後でデータを入力できるようにする方法が分かります。

このガイドではコードの各行を順に解説し、なぜその手順が重要かを説明するとともに、よくある落とし穴にも触れます。最後まで読めば、請求書、契約書、または任意のフォームベース文書のテンプレートとして再利用できる .docx ファイルが手に入ります。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0（またはそれ以降） – コードは最新の C# 言語機能を使用しています。
* Aspose.Words for .NET のライセンス（開発用には無料トライアルで可）。
* Visual Studio 2022 もしくは .NET プロジェクトをビルドできる任意の IDE。
* C# の基本的な知識と Structured Document Tags（SDT）の概念に関する理解。

> **プロのコツ:** ライセンスなしでサンプルを実行すると、Aspose.Words が保存ファイルに小さな透かしを追加します。プログラム開始時にライセンスを適用しておくと透かしを回避できます。

## 手順 1: プロジェクトの作成と名前空間のインポート

新しいコンソールプロジェクトを作成し、Aspose.Words の NuGet パッケージを追加します。

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

次に `Program.cs` で必要な名前空間をインポートします。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

これらの名前空間により、**プログラムで Word 文書を作成** する際に必須となる `Document`、`DocumentBuilder`、`StructuredDocumentTag` クラスにアクセスできます。

## 手順 2: 空のドキュメントとビルダーの初期化

`Document` クラスは .docx 全体を表し、`DocumentBuilder` は特定のカーソル位置にコンテンツを配置するために使用します。

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*重要性*: 空の `Document` から始めることで、挿入するすべての要素を完全にコントロールできます。`DocumentBuilder` は内部カーソルを保持しているため、必要な場所に正確にノードを挿入できます。

## 手順 3: プレーンテキストの Structured Document Tag (SDT) を作成

Structured Document Tag は Word における **コンテンツコントロール** の技術的名称です。ここではインラインのプレーンテキストタグを作成し、プレースホルダー フィールドとして機能させます。

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*重要性*: `StructuredDocumentTagType.PlainText` を使用すると、コントロールがプレーンテキストのみを受け付けることを Word に指示できます。`MarkupLevel.Inline` により、コントロールは段落内の通常の単語と同様に振る舞い、フォームフィールドに最適です。

## 手順 4: タイトルとプレースホルダー テキストの設定

**タイトル** はアプリケーションが後でクエリできる内部識別子です。**プレースホルダー** はユーザーが何も入力していないときに表示される薄灰色のヒントです。

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

ここでは **プレースホルダー テキスト** を “Enter name here” に設定しています。Microsoft Word で文書を開くと、ユーザーが入力を始めるまで薄い灰色で表示されます。

## 手順 5: 現在のカーソル位置にコンテンツコントロールを挿入

`DocumentBuilder.InsertNode` はビルダーのカーソルがある正確な位置に SDT を配置します。デフォルトではカーソルは最初の段落の先頭にあります。

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

特定の段落内にコントロールを入れたい場合は、先にカーソルを移動させます。

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

この例は、周囲のテキストを保持しながら **Word にコンテンツコントロールを追加** する方法を示しています。

## 手順 6: 文書の保存

最後にファイルをディスクに永続化します。保存先フォルダーは任意ですが、アプリケーションに書き込み権限があることを確認してください。

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`SDT.docx` を Microsoft Word で開くと、薄灰色のボックス内に “Enter name here” というプレースホルダーが表示されます。ユーザーはボックスをクリックして、ヒントを実際の顧客名に置き換えることができます。

## 完全な実行可能サンプル

以下は、出力パスを除いてそのままコピー＆ペーストで実行できる完全プログラムです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**期待される出力** – プログラム実行時にコンソールにファイルパスが表示され、生成された Word ファイルには 1 行のテキストと “Enter name here” と表示された灰色のプレースホルダーが含まれます。

## よくあるバリエーションとエッジケース

| シナリオ | コードの適用方法 |
|----------|-----------------------|
| **複数行プレースホルダー** | `StructuredDocumentTagType.RichText` を使用し、`plainTextTag.MultipleLines = true;` を設定します。 |
| **同じコントロールを繰り返し使用** | `plainTextTag.Clone(true)` でタグをクローンし、必要な場所に挿入します。 |
| **データソースへのバインディング** | ユーザーが文書を入力した後、`document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();` で値を取得します。 |
| **コントロールのロック** | `plainTextTag.LockContentControl = true;` を設定して、ユーザーがコントロールを削除できないようにします。 |
| **プレースホルダーの色変更** | SDK ではプレースホルダーのスタイルは公開されていないため、テンプレートを手動で編集するか Word マクロを使用してください。 |

これらのバリエーションにより、**Word にコンテンツコントロールを追加** する操作を、繰り返しテーブルやロックされたセクションなど、より複雑なシナリオでも実現できます。

## ベストプラクティスとトラブルシューティング

* **必ずタイトルを設定** – タイトルがないと、後でコントロールを検索するのが面倒になります。
* **空のプレースホルダーは避ける** – `ShowPlaceholderText` プロパティが `false` の場合、Word は空のプレースホルダーを非表示にします。UX 向上のため `true` に保ちましょう。
* **出力パスを検証** – `document.Save` が `UnauthorizedAccessException` を投げたら、フォルダーが存在するか、プロセスに書き込み権限があるか確認してください。
* **早期にライセンスを適用** – Aspose.Words オブジェクトをインスタンス化する前にライセンスコードを配置し、トライアル透かしを防ぎます。

## 結論

これで **プログラムで Word 文書を作成** し、**Word にコンテンツコントロールを追加**、さらに **プレースホルダー テキスト** を設定する方法が分かりました。Aspose.Words for .NET を使用した完全なサンプルは、ドキュメントの初期化からテンプレートの永続化までのすべての必須手順を示しています。

次に取り組むべきこと:

* テーブル用の **繰り返しコンテンツコントロール** を追加（二次キーワード: add content control to word）。
* データベースから取得したデータでプレースホルダーを埋める（二次キーワード: set placeholder text word）。
* 生成した .docx を PDF や HTML に変換して下流処理に利用。

さまざまなタグタイプ、スタイリング、データバインディング手法を試してみてください。コーディングを楽しんでください！


## 次に学ぶべきこと


以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}