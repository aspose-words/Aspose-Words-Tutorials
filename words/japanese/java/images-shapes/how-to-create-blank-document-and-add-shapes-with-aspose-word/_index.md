---
category: general
date: 2026-09-30
description: Aspose.Words を使用して C# で空白のドキュメントを作成し、長方形、楕円形を挿入し、複数の図形をグループ化します。図形の挿入方法とグループの作成方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: ja
lastmod: 2026-09-30
og_description: C#で空白のドキュメントを作成し、Aspose.Wordsを使用して図形の挿入方法と複数の図形のグループ化方法を学びましょう。ステップバイステップのチュートリアルをご覧ください。
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: C#で空白の文書を作成し、図形をグループ化する – Aspose.Words ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Aspose.Words を使用して C# で空白の文書を作成し、シェイプを追加する方法
url: /ja/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET (C#) で空白ドキュメントを作成しシェイプを追加する方法

グラフィックを含む **空白ドキュメントを作成** したい場合、本ガイドが手順をすべて示します。**矩形シェイプの挿入** 方法や他の描画オブジェクトの追加、さらに **複数のシェイプをグループ化** して単一のユニットとして扱う方法が分かります。

シェイプの操作は、契約書や証明書、カスタムレポートを生成する際に頻繁に求められます。このチュートリアルでは、ドキュメントの初期化から最終ファイルの保存まで、Aspose.Words API for .NET を使用した完全なワークフローを学びます。

## Prerequisites

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0（またはそれ以降）SDK がインストール済み  
* 有効な Aspose.Words for .NET ライセンス（無料トライアルでも本例は動作します）  
* Visual Studio 2022 または Visual Studio Code などの IDE  

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## How to create blank document and work with shapes

最初のステップは `Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の Word ファイルを表し、コンテンツ挿入の主要ツールである `DocumentBuilder` へのアクセスを提供します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** 空白のドキュメントはクリーンなキャンバスを提供します。`DocumentBuilder` は現在の挿入位置を保持するため、追加するシェイプは自動的に適切なページに配置されます。

## Insert rectangle shape and other shapes

次に矩形と楕円を追加します。どちらも同じ `InsertShape` メソッドを使用します。これは Aspose.Words で **シェイプを挿入する方法** として推奨される手法です。

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*`InsertShape` メソッドは、現在のカーソル位置にシェイプを自動的に配置します。* 正確な配置が必要な場合は、挿入後に `Shape.Left` と `Shape.Top` を調整できます。

## Group multiple shapes into a single object

ここでは矩形と楕円を 1 つの論理エンティティに結合します。グループ化は、複数のシェイプを同時に移動またはサイズ変更したいときに便利です。

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**How this works:** `InsertGroupShape` は他の `Shape` と同様に振る舞うコンテナを作成します。`AppendChild` を呼び出すことで既存のシェイプをコンテナに移動し、相対座標が自動的に更新されます。

### Practical tip

後で **グループを作成する方法** を 2 つ以上のシェイプに対してプログラム的に実装したい場合は、追加の `Shape` インスタンスごとに `AppendChild` を繰り返すだけです。グループは画像、テキストボックス、あるいは他のグループを含む任意の数の描画オブジェクトを保持できます。

## Full example – how to insert shapes and save the document

以下は、これまで説明したすべての手順を実演する完全な実行可能プログラムです。コードを実行すると、矩形、楕円、そしてグループ化されたシェイプを含む `ShapesDemo.docx` が生成されます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output:** Microsoft Word で `ShapesDemo.docx` を開くと、青い矩形、緑の楕円、そしてそれらを囲む灰色の境界線（グループを表す）が 1 ページに表示されます。グループを移動すると両方のシェイプが同時に動き、**複数のシェイプをグループ化** する操作が正常に機能したことが確認できます。

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| *特定のページにシェイプを配置したい場合はどうすればよいですか？* | シェイプを挿入する前に `builder.MoveToDocumentEnd();` を呼び出すか、`builder.MoveToSection(sectionIndex);` を使用して対象のセクションに移動します。 |
| *グループ化されたシェイプ内にテキストを追加できますか？* | できます。`ShapeType.TextBox` のタイプで `Shape` を作成し、テキストを設定した後、`AppendChild` で `GroupShape` に追加します。 |
| *シェイプのサイズ単位はポイントですか、ピクセルですか？* | Aspose.Words は **ポイント**（1 pt = 1/72 インチ）を使用します。これにより、プリンターやディスプレイ間でサイズが一貫します。 |
| *グループの回転角度を変更するには？* | `groupShape.RotationAngle = 45;`（度）と設定します。すべての子シェイプはグループの原点を中心に回転します。 |

## Conclusion

これで **空白ドキュメントの作成**、**矩形シェイプの挿入**、**楕円などシェイプを挿入する方法**、そして **複数のシェイプをグループ化** して単一オブジェクトとして扱う方法が Aspose.Words for .NET を使って習得できました。完全なコード例は推奨アプローチを示しており、上記のヒントはテキストボックスの追加やグループの回転といった、より複雑なシナリオへの適用を助けます。

さらに探求したいですか？グループに画像シェイプを追加したり、異なる塗りつぶし色で実験したり、各ページに独自のグループ化図を持つマルチページレポートを生成してみてください。同じ原則が適用できるので、このパターンをあらゆるドキュメント自動化プロジェクトにスケールさせることができます。

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、代替実装アプローチを自分のプロジェクトに取り入れたりするのに役立ちます。

- [Aspose.Words for .NET を使用して Word 文書にグループシェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET を使用して Word 文書にシェイプを挿入する](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words で空白の Word 文書を作成する – ステップバイステップ ガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}