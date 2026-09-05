---
category: general
date: 2026-09-05
description: Aspose.Words を使用して Word 文書に矩形の図形を作成し、次に楕円形の図形を挿入して図形をグループ化する方法を学び、よりリッチなレイアウトを実現します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: ja
lastmod: 2026-09-05
og_description: Aspose.Words を使用して Word 文書に矩形シェイプを作成し、次に楕円形を挿入し、複雑なレイアウトのために Word
  でシェイプをグループ化する方法をご覧ください。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Wordで長方形のシェイプを作成し、シェイプをグループ化する – Aspose.Words ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words を使用して Word で矩形シェイプを作成し、シェイプをグループ化する方法
url: /ja/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して Word で長方形シェイプを作成し、シェイプをグループ化する方法

Word 文書で **長方形シェイプを作成** する必要がある場合、このガイドでは Aspose.Words for .NET を使用した正確な手順を示します。また、楕円シェイプの挿入方法、Word でのシェイプのグループ化方法、結果を DOCX ファイルとして保存する方法も確認できます。このソリューションは .NET 6 以降のプロジェクトで動作し、サーバーに Microsoft Office をインストールする必要はありません。

このチュートリアルはプロジェクトのセットアップから一般的なレイアウト上の落とし穴の対処までを網羅しているため、コードをコピーしてすぐに実行できます。

## 前提条件

* .NET 6 SDK 以降がインストールされていること  
* NuGet 対応の IDE（Visual Studio、Rider、または VS Code）  
* Aspose.Words for .NET のライセンス（または一時評価キー）  
* C# と Word 文書構造の基本的な知識  

これらが揃っていれば、コードがコンパイルされ、シェイプが正しく描画されます。

## 手順 1: プロジェクトをセットアップし Aspose.Words を追加する

新しいコンソールプロジェクトを作成し、Aspose.Words パッケージを追加します。

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

このパッケージは、本チュートリアル全体で使用する `Document`、`DocumentBuilder`、`Shape`、`GroupShape` クラスを提供します。

## 手順 2: 空のドキュメントとビルダーを初期化する

`Document` オブジェクトは Word ファイル全体を表し、`DocumentBuilder` はプログラムからコンテンツを挿入できるようにします。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

最初にドキュメントを作成することで、以降のシェイプ操作が有効なコンテナを持つことが保証されます。

## 手順 3: **長方形シェイプを作成** し、サイズを設定する

長方形はテキストや画像の最も一般的なコンテナです。サイズはポイント単位で指定します（1 pt ≈ 1/72 インチ）。

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

この手順が重要な理由: `Shape` クラスはジオメトリ、塗りつぶし、線のプロパティをカプセル化します。挿入前に `Width` と `Height` を設定することで、シェイプが期待通りのサイズで表示されます。

## 手順 4: **楕円シェイプを挿入する方法** – 楕円シェイプを追加する

楕円はアイコン、マーカー、装飾要素として使用できます。コードは長方形作成と同様ですが、`ShapeType` が異なるだけです。

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

`FillColor` と `Line.Color` プロパティは、外部画像を使用せずに外観をカスタマイズする方法を示しています。

## 手順 5: **Word でシェイプをグループ化** – 長方形と楕円を組み合わせる

グループ化すると、複数のシェイプを単一ユニットとして移動、サイズ変更、回転させることができます。これは、合成グラフィック（例: ラベル付きアイコン）が必要な場合に不可欠です。

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

`AppendChild` を呼び出すと、元のシェイプはメインドキュメントのフローから削除され、`GroupShape` の子として配置されます。グループは単一のシェイプとして振る舞うため、後のレイアウト調整が簡素化されます。

## 手順 6: ドキュメントを保存する

最後に、ドキュメントをディスクに書き出します。サポートされている任意の形式（`.docx`、`.pdf`、`.html` など）を選択できます。このチュートリアルではネイティブの Word 形式を使用します。

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

プログラムを実行したら、Microsoft Word で *GroupShape.docx* を開きます。指定した座標に配置された長方形と楕円がグループ化されているのが確認できます。

## 一般的なバリエーションとエッジケース

| 状況 | 変更点 | 理由 |
|-----------|----------------|--------|
| **異なるサイズ単位** | インチの場合は `ConvertUtil.InchToPoint(2.5)`、ミリメートルの場合は `ConvertUtil.MillimeterToPoint(30)` を使用します。 | ポイント以外の単位で作業する際にコードの可読性を保ちます。 |
| **長方形内にテキストを追加** | `Paragraph` ノードを作成し、`Text` プロパティを設定して `AppendChild` で `rectangleShape` に追加します。 | 別個のテキストボックスを使用せずにシェイプにラベルを付けられます。 |
| **グループを回転** | `groupShape.Rotation = 45;`（度）を設定します。 | 斜めのバッジや透かしを作成するのに便利です。 |
| **PDF として保存** | `doc.Save("GroupShape.pdf");` を呼び出します。 | Aspose.Words は PDF 出力時にベクターシェイプを自動的にラスタライズします。 |
| **複数のグループ** | 追加の `GroupShape` インスタンスを作成し、append/insert 手順を繰り返します。 | 複数の独立した合成要素を持つ複雑なページレイアウトが可能になります。 |

### プロのコツ

シェイプは常に **グループ化する前に** 追加してください。すでに別のグループの一部であるシェイプをグループ化しようとすると、Aspose.Words は `ArgumentException` をスローします。1 つのメソッドでグループを構築すれば、この実行時エラーを防げます。

### 注意すべき点

* **座標系** – `Left` と `Top` は文書の端ではなく、ページの左・上余白から測定されます。この違いを誤解するとシェイプがページ外に配置されてしまいます。  
* **ライセンス** – 有効なライセンスがない場合、保存されたドキュメントには “Aspose.Words for .NET Evaluation” という透かしが入ります。コードの早い段階でライセンスを適用してください（`License license = new License(); license.SetLicense("Aspose.Words.lic");`）。

## 完全なソースコード（実行可能）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

このプログラムを実行すると、説明どおりにシェイプがグループ化された *GroupShape.docx* が生成されます。

## 結論

これで、Aspose.Words を使用して **長方形シェイプの作成**、**楕円シェイプの挿入**、そして **Word でシェイプをグループ化**する方法が分かりました。完全なサンプルは、ドキュメントの初期化から最終ファイルの保存までの全工程を示しているので、シェイプ処理をあらゆる自動レポートや文書生成ソリューションに組み込むことができます。

### 次にやることは？

* **aspose.words create shapes** を調べて、`Polygon` や `Freeform` などのより複雑なジオメトリを作成してみましょう。  
* グループ化したシェイプを **content controls** と組み合わせて、動的テンプレートを構築します。  
* DOCX を PDF や HTML に変換し、ベクターシェイプが各フォーマットでどのようにレンダリングされるか確認します。  

さまざまなサイズ、色、回転を試してみてください。シェイプのグループ化をマスターすれば、Word 文書内に高度な図表やバッジ、カスタム UI 要素を直接作成できます。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトでの代替実装方法を検討するのに役立ちます。

- [Aspose.Words for .NET を使用して Word 文書にグループシェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET を使用して Word 文書にシェイプを挿入する](/words/english/net/working-with-shapes/insert-shape/)
- [C# を使用して Word に長方形シェイプを作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}