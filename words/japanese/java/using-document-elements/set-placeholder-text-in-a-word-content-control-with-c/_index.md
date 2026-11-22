---
category: general
date: 2026-11-22
description: C#でWordコンテンツコントロールにプレースホルダー テキストを設定します。カスタムタグの作成方法、プレーンテキスト コントロールの挿入方法、そして
  Aspose.Words を使用してタグにプレースホルダーを追加する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: ja
lastmod: 2026-11-22
og_description: C# を使用して Word のコンテンツコントロールにプレースホルダー テキストを設定します。このチュートリアルでは、カスタム タグの作成、プレーンテキスト
  コントロールの挿入、タグへのプレースホルダーの追加方法を示し、ドキュメントのインタラクティブ性を向上させます。
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Word コンテンツコントロールにプレースホルダー テキストを設定する – C# ガイド
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: C#でWordコンテンツコントロールのプレースホルダー文字列を設定する
url: /ja/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Word コンテンツ コントロールにプレースホルダー テキストを設定する

Word ドキュメントに **プレースホルダー テキスト** をプログラムで設定したい場合は、このガイドに従ってください。Aspose.Words for .NET を使用すると、カスタム タグを作成し、プレーンテキスト コントロールを挿入し、タグにプレースホルダーを追加して、ユーザー入力の準備ができたドキュメントを作成できます。

このチュートリアルでは、**カスタム タグの作成**、**コンテンツ コントロールの挿入**、**タグへのプレースホルダーの追加** を学びます。コードは簡潔で本番環境でも使用できる形にしています。外部ツールは不要で、.NET プロジェクトと Aspose.Words ライブラリさえあれば始められます。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0 SDK 以降  
* 有効な Aspose.Words for .NET ライセンス（または無料評価キー）  
* C# と Visual Studio（またはお好みの IDE）に関する基本的な知識  

以下のセクションでは、`WordPlaceholderDemo` という名前のコンソール プロジェクトを作成したことを前提としています。

## 手順 1: Aspose.Words をインストール

プロジェクトに NuGet パッケージを追加します。

```bash
dotnet add package Aspose.Words
```

> **プロのコツ:** `--version` フラグを使用して、最新の安定版（例: `Aspose.Words.NET 24.9`）にパッケージを固定しましょう。

## 手順 2: ソース ドキュメントを読み込み、`DocumentBuilder` を作成

最初に既存の `.docx` ファイルを読み込む（または空のドキュメントを新規作成する）と同時に、`DocumentBuilder` をインスタンス化します。ビルダーはコントロールやテキストを挿入するためのフルエント API を提供します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

このコードは、コンテンツ コントロールを挿入する **土台** を作ります。`DocumentBuilder` は `doc` オブジェクトに直接作用するため、行った変更は自動的に反映されます。

## 手順 3: カスタム タグ（StructuredDocumentTag）を作成

Word での *カスタム タグ* は **StructuredDocumentTag (SDT)** と呼ばれます。これは一意の識別子を持つコンテンツ コントロールと考えてください。**カスタム タグの作成** がこのステップの中心です。

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

`InsertStructuredDocumentTag` メソッドは 2 つの引数を受け取ります。

1. コントロールの種類（この例では `PlainText`）。  
2. タグを一意に識別する文字列（例: `"MyTag"`）。

**カスタム タグ** を使用すると、後でプログラムからコントロールを検索・操作しやすくなります。

## 手順 4: アクセシビリティ用にタイトルを設定

タイトルを設定するとアクセシビリティが向上し、Word の UI でもコントロールが見つけやすくなります。

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

`Title` プロパティは任意ですが、**タグへのプレースホルダーの追加** 時にユーザー体験を向上させるベストプラクティスです。

## 手順 5: タグにプレースホルダー テキストを追加

ここがメインの目的、**プレースホルダー テキストの設定** です。コントロールが空の場合に表示され、ユーザーに入力内容を案内します。

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

`PlaceholderText` プロパティが **タグへのプレースホルダーの追加** に必要なものです。モダンなフォーム フィールドで見られるグレーのヒントと同様に機能します。

## 手順 6: 変更したドキュメントを保存

コントロールの設定が完了したら、ドキュメントをディスクに書き出します。

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

`output.docx` を Microsoft Word で開くと、プレーンテキスト コンテンツ コントロール「CustomerName」にプレースホルダー「Enter name…」が表示されます。コントロール内をクリックするとプレースホルダーが消え、ユーザーが入力できるようになります。

### 期待される出力

* `output.docx` という Word ファイルが生成され、1 つのプレーンテキスト コンテンツ コントロールが含まれます。  
* ユーザーが何も入力していない間はプレースホルダー「Enter name…」が表示されます。  
* コントロールのタグ識別子は `MyTag` で、後から `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` で取得可能です。

## 手順 7: 別の場所にコンテンツ コントロールを挿入する方法（上級編）

特定の位置（例: 特定の段落の後）に **コンテンツ コントロールを挿入する方法** が必要な場合は、タグを挿入する前に `MoveTo` メソッドを使用します。

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

このスニペットは、同一ドキュメント内で **プレーンテキスト コントロールを複数回挿入** する例を示しています。

## よくある落とし穴と回避策

| 問題 | 発生理由 | 対策 |
|------|----------|------|
| プレースホルダーが表示されない | コントロールに既にテキスト（空白など）が入っている | `PlaceholderText` を設定する前に `sdt.Text` が空であることを確認する |
| タグ識別子が衝突する | 同一ドキュメント内で同じタグ名（`MyTag`）を再利用している | 各 `StructuredDocumentTag` に一意の識別子を使用する |
| ライセンス例外が発生する | 有効な Aspose.Words ライセンスなしで実行している | `Main` の冒頭で `license.SetLicense("Aspose.Words.lic")` を呼び出す |
| ドキュメントが保存されない | `doc.Save` を呼び忘れた、または読み取り専用パスを使用している | 出力パスが書き込み可能か確認し、必ず `doc.Save` を呼ぶ |

## 完全動作サンプル

以下は `Program.cs` にコピペできる完全プログラムです。**カスタム タグの作成**、**コンテンツ コントロールの挿入方法**、**タグへのプレースホルダーの追加**、**プレーンテキスト コントロールの挿入** を一連の流れで実装しています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

`dotnet run` でプログラムを実行してください。実行後に `output.docx` を開くと、両方のコントロールにそれぞれのプレースホルダーが表示されていることが確認できます。

## 次のステップ

* **外観のカスタマイズ** – `sdt.Font` を使用して、コントロール内のフォントサイズ、色、スタイルを変更できます。  
* **XML データへのバインド** – コントロールをデータにマッピングしたい場合は `sdt.XmlMapping` を調査してください。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりする際に役立ちます。

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}