---
category: general
date: 2026-09-18
description: C# を使用して Word 文書に矩形シェイプを作成します。複数のシェイプの追加方法、シェイプをグループに追加する方法、そして Aspose.Words
  でグループシェイプを挿入する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: ja
lastmod: 2026-09-18
og_description: C#でWordファイルに長方形の図形を作成する。このガイドでは、複数の図形の追加、図形をグループに追加する方法、そして Aspose.Words
  を使用してグループ図形を挿入する方法を示します。
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: C#で矩形シェイプを作成し、シェイプをグループ化する
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: C#で矩形シェイプを作成し、複数のシェイプをグループ化する
url: /ja/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で長方形シェイプを作成し、複数のシェイプをグループ化する方法

Word 文書に **長方形シェイプを作成** したい場合、このチュートリアルで完全なソリューションを示します。**複数のシェイプを追加**、**シェイプをグループに追加**、そして **グループシェイプを挿入** する方法を Aspose.Words for .NET API を使って学びます。

シェイプの操作は、レポート、契約書、マーケティング資料などをプログラムで生成する際に頻繁に必要となります。このガイドを終える頃には、長方形、楕円、そして両方のシェイプを保持するグループを含む `.docx` ファイルを生成する C# コンソール アプリケーションが実行できるようになります。

必要な前提条件は、.NET SDK（6.0 以降）と Aspose.Words for .NET のライセンス版だけです。追加ツールは不要です。

## 前提条件

- .NET 6.0 SDK 以上  
- Aspose.Words for .NET（NuGet パッケージ `Aspose.Words`）  
- C# の基本的な構文に関する知識  

以下のコマンドでパッケージをインストールできます:

```bash
dotnet add package Aspose.Words
```

## 手順 1: Aspose.Words で長方形シェイプを作成

最初のステップは、`Rectangle` タイプの `Shape` オブジェクトを作成することです。このオブジェクトが文書内に表示される長方形を表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**重要ポイント:** `ShapeType.Rectangle` は Aspose.Words に幾何学的な長方形を描画させます。`Width` と `Height` を設定することでサイズ（ポイント単位、1 ポイント = 1/72 インチ）を決めます。塗りつぶし色と枠線色を設定すれば、追加のスタイリングなしでシェイプが可視化されます。

## 手順 2: 文書に複数のシェイプを追加

長方形に続いて、任意の数だけシェイプを作成できます。この例では、**複数のシェイプを追加** する方法を示すために楕円を追加します。

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**重要ポイント:** `new Shape` の呼び出しごとに独立した描画オブジェクトが生成されます。シーケンシャルに挿入することで、後でグループ化したり個別に配置したりできるシェイプのコレクションが構築されます。

## 手順 3: シェイプをグループに追加

シェイプをグループ化すると、レイアウト管理が簡素化されます。グループは単一のノードとして振る舞うためです。このステップでは `GroupShape` を使って **シェイプをグループに追加** する方法を示します。

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**重要ポイント:** `GroupShape` はコンテナのように機能します。グループ全体を移動、回転、サイズ変更すると、子シェイプは自動的に追従します。バウンディング ボックス（200 × 200 ポイント）が子シェイプの座標空間を定義します。

## 手順 4: グループシェイプを文書に挿入

グループに長方形と楕円が入ったら、**グループシェイプを挿入** して目的の位置に配置します。ビルダーはすでに空のグループを配置していますが、必要に応じて別の場所に挿入することも可能です。

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**重要ポイント:** `Left` と `Top` を調整すると、ページ内でグループ全体の位置が変更されます。文書を保存すると、シェイプ階層が `.docx` ファイルに書き込まれ、Microsoft Word、LibreOffice、または互換ビューアで開くことができます。

## 完全に実行可能なサンプル

以下はすべての手順を組み合わせたフルプログラムです。コードを新しいコンソール プロジェクトに貼り付けて実行すると `GroupShapeExample.docx` が生成されます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**期待される出力:**  
`GroupShapeExample.docx` を開くと、200 × 200 ポイントのコンテナ内に淡い青色の長方形と淡いコーラル色の楕円が含まれる単一のグループが表示されます。Word ではグループ全体が 1 つのオブジェクトとして選択でき、**シェイプをグループに追加** が成功したことが確認できます。

## よくあるバリエーションとエッジケース

| 状況 | 推奨される調整 |
|-----------|------------------------|
| 異なるシェイプタイプ（例: `ShapeType.Line`） | 希望する `ShapeType` でシェイプを作成し、ジオメトリを適切に設定します。 |
| シェイプを回転させる必要がある | グループに追加する前に `shape.Rotation = 45;`（度）を設定します。 |
| 多数のグループを含む大規模文書 | `DocumentBuilder` インスタンスを再利用し、各グループごとに新しいビルダーを作成しないようにしてメモリ使用量を抑えます。 |
| DOCX ではなく PDF に保存したい | グループ挿入後に `doc.Save("output.pdf", SaveFormat.Pdf);` を呼び出します。 |

**プロのコツ:** 正確な配置が必要な場合は、必ずグループの `Left` と `Top` を明示的に設定してください。省略するとビルダーの現在のカーソル位置を継承し、予期しないレイアウト結果になることがあります。

## 結論

C# を使って Word 文書に **長方形シェイプを作成**、**複数のシェイプを追加**、**シェイプをグループに追加**、そして **グループシェイプを挿入** する方法が分かりました。完全なサンプルは、文書作成から最終ファイルの保存までの全ワークフローを示しています。

次は、**テキストに対するシェイプの位置指定**、**テキストラッピングの適用**、**グループ化されたシェイプの PDF へのエクスポート** といったトピックを探求してください。これらの拡張により、Aspose.Words を使った高度なプログラム的文書レイアウトが構築できます。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、ステップバイステップの説明と完全なコード例が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりするのに役立ちます。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}