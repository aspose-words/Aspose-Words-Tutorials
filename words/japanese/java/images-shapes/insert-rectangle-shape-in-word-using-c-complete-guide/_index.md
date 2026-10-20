---
category: general
date: 2026-08-04
description: C#でWord文書に長方形の図形を挿入します。Wordで図形をグループ化する方法、文書をdocxとして保存する方法、そして高度なレイアウトのためにDocumentBuilderを使用する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: ja
lastmod: 2026-08-04
og_description: C# を使用して Word ファイルに長方形の図形を挿入し、さらに高度なレイアウトのために図形をグループ化します。このチュートリアルでは、ドキュメントを
  docx として保存し、DocumentBuilder を効率的に使用する方法も解説します。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Wordで長方形の図形を挿入する – C# ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#でWordに長方形の図形を挿入する完全ガイド
url: /ja/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word に長方形シェイプを挿入する – 完全ガイド

C# を使用して Word 文書に **insert rectangle shape** を挿入する必要がある場合、このチュートリアルで正確な方法を示します。また、Word で **how to group shapes**、**save document as docx**、そして **how to use Builder** を学び、クリーンで保守しやすいコードを書く方法も学べます。

プログラムでレポート、証明書、またはカスタムレイアウトを生成する際に、シェイプの操作は一般的な要件です。このガイドの最後までに、長方形を作成し、楕円を追加し、これらをグループ化して DOCX ファイルとして保存する、完全に実行可能なサンプルを手に入れることができます。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* .NET 6.0 以降がインストール済み  
* Visual Studio 2022（または C# をサポートする任意の IDE）  
* **Aspose.Words for .NET** ライブラリ（NuGet 経由で入手可能）  

以下のコマンドでライブラリを追加できます。

```bash
dotnet add package Aspose.Words
```

## DocumentBuilder を使用した長方形シェイプの挿入

最初のステップは新しい `Document` と `DocumentBuilder` を作成することです。ビルダーはシェイプを含むコンテンツを挿入するためのフルエント API を提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` インスタンスは **insert rectangle shape** やその他の要素を挿入するための中心オブジェクトです。ドキュメント内の現在のカーソル位置を追跡するため、挿入は必要な場所で正確に行われます。

## 長方形シェイプの挿入方法

ビルダーの準備ができたら `InsertShape` を呼び出します。`ShapeType`、幅、高さをポイント単位で指定します（1 pt ≈ 1/72 in）。

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

**重要性*:* `FillColor` と `StrokeColor` を設定すると、長方形が視覚的に際立ち、後で他のシェイプとグループ化する際に役立ちます。

## Word でシェイプをグループ化する方法

シェイプをグループ化すると、複数のオブジェクトを単一のエンティティとして移動、回転、または書式設定できます。長方形を挿入した後、別のシェイプ（この例では楕円）を追加し、`GroupShape` を作成します。

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

`InsertGroupShape` 呼び出しは、任意の数の子シェイプを保持できるプレースホルダーを作成します。長方形と楕円を追加することで、実質的に **group shapes in Word** が実現します。グループは単一のシェイプとして振る舞い、位置を変更したり、枠線を適用したり、サイズを変更したりしても、各子シェイプの内部レイアウトには影響しません。

### プロのコツ

グループ化した後、ページに対するグループの位置を変更できます。

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## ドキュメントを docx として保存

シェイプの配置が完了したら、ファイルを永続化する必要があります。`Document.Save` メソッドはファイル拡張子から形式を自動的に判別します。**save document as docx** するには、拡張子が `.docx` で終わるパスを渡します。

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

プログラムを実行すると `output.docx` が作成されます。Microsoft Word でファイルを開くと、淡い青色の長方形と淡いコーラル色の楕円がグループ化されていることが確認できます。グループをクリックすれば、単一オブジェクトとして移動できます。

## DocumentBuilder を効果的に使用する方法

`DocumentBuilder` はシェイプ挿入ツールにとどまらず、テキスト、テーブル、ヘッダー、フッターも扱えます。シェイプ作成とテキストを組み合わせる際は、別の場所にコンテンツを挿入する必要がある場合にカーソルをリセットすることを忘れないでください。

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

ビルダーの状態を明示的に管理することで、意図しない上書きを防ぎ、コードの保守性が向上します。

## エッジケースとバリエーション

| **状況** | **推奨アプローチ** |
|-----------|----------------------|
| **2つ以上のシェイプ** | 各シェイプを挿入し、保存する前にすべてのシェイプに対して `AppendChild` を呼び出します。 |
| **入れ子グループ** | グループを作成しシェイプを追加し、そのグループを別の `GroupShape` に挿入します。 |
| **異なる測定単位** | 寸法がピクセル単位の場合は `builder.ConvertPixelsToPoints` を使用します。 |
| **古い Word バージョンとの互換性** | 拡張子を変更して `.doc` として保存します。ほとんどのシェイプ機能は引き続き動作します。 |

## 完全な動作例

以下は新しいコンソールプロジェクトにコピー＆ペーストできるフルプログラムです。追加のスニペットは不要です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**期待される結果**: `output.docx` を開くと、淡い青色の長方形と淡いコーラル色の楕円がグループ化され、左余白から 150 pt、上端から 100 pt の位置に配置されていることが確認できます。キャプションはグループの下に表示されます。

## 結論

これで C# を使用して Word ファイルに **insert rectangle shape** を挿入し、Word で **how to group shapes** を行い、Aspose.Words の `DocumentBuilder` で **how to save document as docx** できるようになりました。これらの手順を習得すれば、証明書、レポート、カスタムフォームなど、複雑なレイアウトをコードだけで構築できます。

次に、**adding text boxes**、**working with tables**、または **exporting to PDF** といった関連トピックを探求してください。これらはすべて、今回練習した `DocumentBuilder` の基本に基づいています。

Word ドキュメントの自動化を始めませんか？ 例を拡張してシェイプを増やしたり、グラデーションを適用したり、データをループして単一実行で完全なレポートを生成したりしてみてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Aspose.Words for .NET を使用して Word 文書にグループシェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET を使用して Word 文書にシェイプを挿入する](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words で Word に長方形シェイプを作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}