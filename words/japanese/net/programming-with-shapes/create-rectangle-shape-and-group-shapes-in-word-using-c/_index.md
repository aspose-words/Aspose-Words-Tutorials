---
category: general
date: 2026-09-08
description: C#でWord文書に長方形の図形を作成します。図形のサイズ設定、複数の図形のグループ化、そしてプログラムで空白のWord文書を作成する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: ja
lastmod: 2026-09-08
og_description: C#でWord文書に長方形の図形を作成する。このガイドでは、図形のサイズ設定、複数の図形のグループ化、そしてプログラムで空白のWord文書を作成する方法を示します。
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: C# を使用して Word で長方形の図形を作成し、図形をグループ化する
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# を使用して Word で長方形のシェイプを作成し、シェイプをグループ化する
url: /ja/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word で矩形シェイプを作成し、シェイプをグループ化する方法

Word ファイル内に **矩形シェイプを作成** したい場合、このチュートリアルは完全に実行可能なソリューションを提供します。シェイプのサイズ設定、複数シェイプのグループ化、そして最初から空の Word 文書を作成する方法を、Aspose.Words for .NET ライブラリを使って解説します。

プログラムで Word 文書を操作するのは、細かい点が多くて大変に感じることがあります。このガイドを最後まで読むと、矩形と楕円がグループ化された `.docx` ファイルを生成する単一メソッドが手に入り、さらに編集や印刷にすぐに利用できます。

## 前提条件

開始する前に以下を用意してください。

* .NET 6.0 以降（コードは .NET Framework 4.6 以上でも動作します）
* **Aspose.Words for .NET** のライセンス版（無料評価キーでも可）
* Visual Studio 2022 や Visual Studio Code などの IDE
* C# の基本的な構文に関する知識

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## 手順 1: 空の Word 文書を作成する

最初のステップは、シェイプを配置するための空の文書を作成することです。これで *空の Word 文書を作成* する要件が満たされます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

空の文書を作成すると、クリーンなキャンバスが得られます。`Document` オブジェクトは `.docx` 全体を表し、`FirstSection.Body.FirstParagraph` が新しいノードのデフォルト挿入ポイントになります。

## 手順 2: 矩形シェイプを作成する

次に矩形を追加します。ここで **矩形シェイプを作成** する操作が行われます。

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

サイズを直接設定することで **シェイプのサイズを設定** というキーワードに対応します。サイズはすべてポイント単位で指定され、最終文書でのシェイプの見た目を正確にコントロールできます。

## 手順 3: 追加のシェイプ（楕円）を作成する

典型的なユースケースは複数シェイプを組み合わせることです。ここでは後で同じコンテナに入れる楕円を追加します。

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

この時点では両シェイプはまだ独立しています。次の手順で **複数シェイプをグループ化** する方法を示します。

## 手順 4: Word でシェイプをグループ化する

シェイプをグループ化すると、1 つのユニットとして移動、サイズ変更、書式設定が可能になります。これで **Word でシェイプをグループ化** および **複数シェイプをグループ化** の要件が満たされます。

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

`GroupShape.Bounds` プロパティは子シェイプの座標系を決定します。矩形と楕円を同じ `GroupShape` に入れることで、後から 1 回の呼び出しで一緒に移動や回転ができるようになります。

## 手順 5: 文書を保存する

最後に文書をディスクに書き出します。ファイルには先ほど作成したグループ化されたシェイプが含まれます。

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

プログラムを実行したら、`GroupedShapes.docx` を Microsoft Word で開いてください。矩形と楕円がグループ化されていることが確認でき、1 つのシェイプを選択するともう 1 つも同時に選択されます。

## 完全なソースコード

以下の完全なプログラムを新しいコンソールアプリ プロジェクトにコピーし、実行してください。追加のコードは不要です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### 期待される出力

プログラムを実行すると `GroupedShapes.docx` が生成されます。Word でファイルを開くと次のように表示されます。

* 青い枠線と薄いグレーの塗りつぶしを持つ **矩形**（100 pt × 50 pt）
* ダークグリーンの枠線と薄いイエローの塗りつぶしを持つ **楕円**（80 pt × 80 pt）
* 両シェイプは単一のグループに入っているため、1 つを移動するともう 1 つも同時に移動します。

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| **グループに 2 つ以上のシェイプを追加できますか？** | はい。追加の `Shape` オブジェクトを作成し、`group.AppendChild(yourShape)` をそれぞれ呼び出します。 |
| **グループを回転させるにはどうすればよいですか？** | `group.RotationAngle = 45;`（単位は度）を設定します。子シェイプはすべて一緒に回転します。 |
| **文書を保存した後でもシェイプをグループ化できますか？** | 保存前に文書構造を変更する必要があります。保存後にグループ化したい場合は、ファイルを再度読み込み、シェイプを検索して新たにグループを作成する必要があります。 |
| **オブジェクトの破棄は必要ですか？** | Aspose.Words はリソースを自動管理しますが、手動でストリームを開く場合は `FileStream` などを適切に `Dispose` してください。 |
| **.doc（バイナリ）形式でも動作しますか？** | はい、`doc.Save("output.doc")` に変更すれば同じグループ化動作が得られます。 |

## 結論

これで C# を使って Word ファイル内に **矩形シェイプを作成**、**シェイプのサイズを設定**、そして **複数シェイプをグループ化** する方法が分かりました。この手法を利用すれば、プログラムで複雑な図や透かし、テンプレートベースのレポートを手動編集なしで構築できます。

### 次のステップ

* **Word でシェイプをグループ化** をさらに深掘りし、テキストボックスや画像も同じグループに追加してみましょう。  
* `SetShapeSize` パターンを使って、ページレイアウトに基づくサイズを動的に計算します。  
* このテクニックとメールマージ フィールドを組み合わせ、スケールでパーソナライズされた文書を大量に生成します。

さまざまなシェイプタイプ、色、グループ変換を試してみてください。コーディングを楽しんでください！


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装を検討したりするのに役立ちます。

- [Aspose.Words for .NET を使用して Word 文書にグループ シェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [影付き矩形シェイプで空の Word 文書を作成する – ステップバイステップ ガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [影付き矩形を含む Word 文書を作成する – ステップバイステップ ガイド](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}