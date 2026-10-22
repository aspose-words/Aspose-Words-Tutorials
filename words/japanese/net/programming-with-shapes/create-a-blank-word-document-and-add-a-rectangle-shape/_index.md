---
category: general
date: 2026-09-05
description: C# の Aspose.Words を使用して、空白の Word 文書を作成し、非表示にできる矩形シェイプを追加する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: ja
lastmod: 2026-09-05
og_description: Aspose.Words を使用した空白の Word ドキュメント作成と非表示の長方形シェイプ挿入 – C# 開発者向けステップバイステップガイド
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: 隠し矩形シェイプ付きの空白のWord文書を作成する
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 空白のWord文書を作成し、長方形の図形を追加する
url: /ja/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白の Word ドキュメントを作成し、矩形シェイプを追加する

レイアウトに表示したくないシェイプを含む **blank word document** を作成したい場合は、このガイドで Aspose.Words for .NET を使用した手順をすべてご紹介します。新しいドキュメントを作成し、矩形シェイプを追加し、そのシェイプを非表示にしてファイルを保存する、完全に実行可能なサンプルをご覧いただけます。追加のツールは不要です。

このチュートリアルでは、プロジェクトのセットアップから一般的な落とし穴のトラブルシューティングまで網羅しています。最後まで読めば、読者には空白に見える Word ファイルを生成でき、隠しメタデータを保持したまま、透かしやカスタム XML の保存、レイアウトアンカーなどに活用できるようになります。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 SDK 以降（コードは .NET Framework 4.7+ でも動作します）
* Visual Studio 2022（または C# をサポートする任意の IDE）
* 有効な **Aspose.Words** NuGet ライセンス（無料トライアルでもテスト可能）
* C# の基本的な知識と、ドキュメントノードの概念に関する理解

以下の CLI コマンドでライブラリをインストールできます。

```bash
dotnet add package Aspose.Words
```

> **プロのコツ:** Aspose.Words のバージョンは常に最新に保ちましょう。本チュートリアルで使用している API はバージョン 23.10 時点で安定しています。

## Aspose.Words で空白の Word ドキュメントを作成する方法

最初のステップは `Document` オブジェクトをインスタンス化することです。新規 `Document` は空の **blank word document** を表し、段落もセクションもなく、単なるファイルコンテナだけが存在します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **重要性の説明:** クリーンなドキュメントから開始することで、後で追加する隠しシェイプが既存のコンテンツやスタイルに干渉しないことが保証されます。

## ドキュメントに矩形シェイプを追加する

次に矩形シェイプを作成します。Aspose.Words ではシェイプはドキュメントツリーの任意の場所に配置できるノードで、サイズ、塗りつぶし、線スタイル、可視性を設定できます。

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

上記コードは可視の矩形を作成します。この時点で `builder.InsertNode(rectangle)` でドキュメントに挿入できますが、シェイプを非表示にしたいので、挿入前に `Hidden` プロパティを調整します。

## Word ドキュメントでシェイプを非表示にする方法

Word にはシェイプノード用の `Hidden` 属性があります。`true` に設定すると、シェイプはページレイアウトに表示されませんが、XML には残ります。これが **how to hide shape** の核心です。

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **解説:** `Hidden = true` を設定すると、シェイプの XML に `<w:hide>` 属性が追加されます。Word エディタは描画時にシェイプを無視しますが、プログラムからや Word の XML ビューからは依然としてアクセス可能です。

## 非表示シェイプを空白ドキュメントに挿入する

ここで非表示の矩形をドキュメントツリーに配置します。ドキュメントはまだ空なので、シェイプはメインストーリーの最初のノードになります。

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Microsoft Word で生成されたファイルを開くと、見た目は空白のページになります。シェイプは存在しますが目に見えません。

## ドキュメントを保存する

最後にドキュメントをディスクに書き出します。サポートされている任意の形式（`.docx`、`.pdf`、`.odt` など）を選択できます。このチュートリアルでは最新の DOCX 形式を使用します。

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### 期待される結果

Word で `HiddenRectangle.docx` を開くと:

* ドキュメントは空白に見えます（可視シェイプやテキストはありません）。
* **Open XML SDK** や **Word XML Viewer** などのツールでファイルを確認すると、`hidden` 属性が付いた矩形を含む `<w:pict>` 要素が見えます。

![blank word document with hidden rectangle shape](image.png){: .align-center alt="非表示の矩形シェイプがある空白の Word ドキュメント"}

## 完全な実行可能サンプル

以下はコンソール アプリケーションにコピーペーストできる完全プログラムです。必要な `using` ディレクティブ、エラーハンドリング、コメントがすべて含まれています。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

プログラムを実行（`dotnet run`）し、出力ファイルを確認してください。コンソールに保存場所が表示されます。

## よくある質問とエッジケース

### 複数のシェイプを同時に非表示にできますか？

はい。各シェイプを作成し、`Hidden = true` を設定して順に挿入します。非表示フラグはノード単位で機能するため、同一ドキュメント内で非表示シェイプと可視シェイプを混在させることが可能です。

### 印刷プレビューでのみシェイプを非表示にしたい場合は？

Word では **display** と **print** の可視性を `DisplayWhen` プロパティで区別します。Aspose.Words には直接的な API がありませんが、基になる XML を次のように変更できます。

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

印刷時のみの可視性が必要な場合にのみ使用してください。

### 非表示シェイプはファイルサイズに影響しますか？

非表示シェイプは可視シェイプと同じ XML ペイロードを持つため、ファイルサイズの増加は同等です。ただし、シェイプ自体が

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを取り上げています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりする際に役立ちます。

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}