---
category: general
date: 2026-09-08
description: DocumentBuilder を使用して Word で図形をグループ化し、空白の Word 文書を作成し、数行の C# コードで矩形の図形を挿入する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: ja
lastmod: 2026-09-08
og_description: DocumentBuilder を使用して Word で図形をグループ化します。このチュートリアルでは、空白の Word 文書を作成し、長方形の図形を挿入し、図形を
  GroupShape に結合する方法を示します。
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: DocumentBuilder を使って Word で図形をグループ化 – 完全な C# サンプル
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: DocumentBuilder を使用して Word で図形をグループ化する方法 – ステップバイステップガイド
url: /ja/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# WordでDocumentBuilderを使用して図形をグループ化する方法 – ステップバイステップガイド

If you need to **group shapes in Word** programmatically, this tutorial shows a complete solution in C#. You’ll see how to **create a blank Word doc**, use **DocumentBuilder**, and **insert a rectangle shape** before grouping it with an ellipse. The result is a single `GroupShape` that you can move, resize, or style as one object.

このチュートリアルでは、Wordで図形をプログラムで**グループ化**する必要がある場合、C#での完全なソリューションを示します。**空のWord文書を作成**し、**DocumentBuilder**を使用し、**長方形の図形を挿入**してから楕円とグループ化する方法が分かります。結果は、1つの `GroupShape` で、これをオブジェクトとして移動、サイズ変更、またはスタイル設定できます。

This guide covers everything you need to know to generate a Word document with grouped graphics using the Aspose.Words for .NET library. By the end of the article you’ll have a runnable project that produces `GroupedShapes.docx` containing a rectangle and an ellipse combined into a single shape.

このガイドでは、Aspose.Words for .NET ライブラリを使用してグループ化されたグラフィックを含むWord文書を生成するために必要なすべてをカバーします。記事の最後までに、長方形と楕円が単一の形状に結合された `GroupedShapes.docx` を生成する実行可能なプロジェクトが手に入ります。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7.2+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Aspose.Words`）– バージョン 23.12 以上
- Visual Studio 2022 や Visual Studio Code などの C# IDE
- C# の構文とオブジェクト指向プログラミングの基本的な知識

> **プロのコツ:** コマンドラインから NuGet パッケージをインストールしてプロジェクトを整理しましょう:  
> `dotnet add package Aspose.Words --version 23.12.0`

## 手順 1: 空の Word 文書を作成

The first operation is to instantiate a `Document` object, which represents an empty Word file, and a `DocumentBuilder` that lets you add content.

最初の操作は、空の Word ファイルを表す `Document` オブジェクトをインスタンス化し、コンテンツの追加を可能にする `DocumentBuilder` を作成することです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` はファイルコンテナを提供し、`DocumentBuilder` はテキスト、画像、図形の挿入のためのフルエント API を提供します。`DocumentBuilder` がなければ、ドキュメントのノードツリーを手動で操作する必要があり、エラーが起きやすくなります。

## 手順 2: 長方形の図形を挿入

A rectangle is a common building block for diagrams. Use `InsertShape` with `ShapeType.Rectangle` and specify width and height in points (1 pt ≈ 1/72 in).

長方形は図表の一般的な構成要素です。`InsertShape` を `ShapeType.Rectangle` と共に使用し、幅と高さをポイントで指定します（1 pt ≈ 1/72 in）。

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Why this matters:** `Left` と `Top` を設定することで、長方形をページ上の正確な位置に配置できます。これは後で他の図形とグループ化する際に重要です。`InsertShape` メソッドは自動的に現在の段落に図形を追加します。

## 手順 3: 楕円形の図形を挿入

Next, add an ellipse that will sit beside the rectangle.

次に、長方形の横に配置する楕円を追加します。

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Why this matters:** 異なる `ShapeType` を使用することで、同じ `DocumentBuilder` API がさまざまなグラフィックを作成できることを示します。楕円を長方形と重なるように配置することで、グループ化効果が明確になります。

## 手順 4: 2つの図形をグループ化

A `GroupShape` acts like a container. By appending the rectangle and ellipse as children, they behave as a single object.

`GroupShape` はコンテナのように機能します。長方形と楕円を子として追加することで、1つのオブジェクトとして扱われます。

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Why this matters:** `Bounds` プロパティは、グループがページ上のどこに配置されるかを Word に指示します。子図形を追加することで、個々の書式設定を保持しつつ、集合的な変換（移動、回転、サイズ変更）を可能にします。

## 手順 5: 文書を保存

Finally, write the document to disk. You can change the path to any folder you prefer.

最後に、文書をディスクに書き込みます。パスは好きなフォルダーに変更できます。

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

When you open `GroupedShapes.docx` in Microsoft Word, you’ll see a rectangle and an ellipse grouped together. Selecting the group will highlight both shapes, allowing you to drag or resize them as a single unit.

Microsoft Word で `GroupedShapes.docx` を開くと、長方形と楕円が一緒にグループ化されているのが確認できます。グループを選択すると両方の図形がハイライトされ、1つのユニットとしてドラッグやサイズ変更が可能です。

### 期待される出力

- **GroupedShapes.docx** という名前の Word ファイル
- 1 ページ目に位置 (50, 50) に **長方形** (100 pt × 50 pt) が含まれる
- 位置 (200, 70) に **楕円** (80 pt × 80 pt) がある
- 両方の図形は、バウンディングボックスが 300 pt × 200 pt の **GroupShape** の一部

## 一般的なバリエーションとエッジケース

| シナリオ | 調整 |
|----------|------------|
| **ページサイズが異なる場合** | Set `document.Sections[0].PageSetup.PageWidth` and `PageHeight` before inserting shapes. |
| **2つ以上の図形の場合** | Create additional `Shape` objects and call `groupShape.AppendChild(newShape)` for each. |
| **塗りつぶし色を適用** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **グループを回転** | `groupShape.Rotation = 45;` (degrees) |
| **PDF にエクスポート** | After saving the DOCX, call `document.Save("GroupedShapes.pdf");` |

## 完全なソースコード（実行可能）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Copy the code into a new console project, restore the Aspose.Words NuGet package, and run. The console will confirm the file location, and opening the file will show the grouped graphics.

コードを新しいコンソールプロジェクトにコピーし、Aspose.Words NuGet パッケージを復元して実行してください。コンソールにファイルの場所が表示され、ファイルを開くとグループ化されたグラフィックが確認できます。

## 結論

You now know **how to group shapes in Word** with the Aspose.Words `DocumentBuilder`. The tutorial walked through creating a **blank Word doc**, **inserting a rectangle shape**, adding an ellipse, and combining them into a `GroupShape`. With this foundation you can build richer diagrams, flowcharts, or custom graphics directly from C#.

これで、Aspose.Words の `DocumentBuilder` を使用して **Word で図形をグループ化する方法** が分かりました。このチュートリアルでは、**空の Word 文書** の作成、**長方形の図形の挿入**、楕円の追加、そしてそれらを `GroupShape` に結合する手順を解説しました。この基礎をもとに、C# から直接、よりリッチな図表、フローチャート、カスタムグラフィックを作成できます。

### 次は何をすべきか？

- **DocumentBuilder** を使用してテーブル、ヘッダー、フッターを操作する方法を探求する。
- **insert rectangle shape Word** のテクニックとテキストボックスを組み合わせて注釈付き図を作成する。
- **create blank word doc** をテンプレートとして自動レポート生成に利用する。

色やグラデーション、追加の図形を自由に試してみてください。コーディングを楽しんで！

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書へのグループシェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET を使用した Word 文書への図形挿入](/words/english/net/working-with-shapes/insert-shape/)
- [C# で Word に長方形の図形を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}