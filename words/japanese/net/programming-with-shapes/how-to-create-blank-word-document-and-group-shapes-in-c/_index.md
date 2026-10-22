---
category: general
date: 2026-10-07
description: C#で空白のWord文書を作成し、矩形シェイプの追加、画像シェイプの挿入、複数のシェイプをグループ化して動的レポートを作成する方法を学ぶ。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: ja
lastmod: 2026-10-07
og_description: C# と Aspose.Words で空白の Word 文書を作成します。矩形シェイプの追加、画像シェイプの挿入、複数シェイプのグループ化方法を学び、プロフェッショナルな文書を作成しましょう。
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: C#で空白のWord文書を作成し、図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#で空白のWord文書を作成し、シェイプをグループ化する方法
url: /ja/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で空白の Word 文書を作成し、図形をグループ化する方法

プログラムで **空白の Word 文書を作成** する必要がある場合、このガイドが手順をすべて示します。**矩形図形の追加**、**画像図形の挿入**、そして複数の図形を **グループ化** して、後で **Word に画像を追加** したときに単一のオブジェクトとして扱えるようにする方法が分かります。

コードから Word ファイルを操作するのは敷居が高く感じられるかもしれませんが、Aspose.Words を使えばプロセスはシンプルです。このチュートリアルの最後までに、矩形とロゴをグループ化したクリーンな空の Word ファイルを生成する再利用可能な C# スニペットが手に入ります。請求書、レポート、または任意の自動化ドキュメント ワークフローに組み込むことができます。

## 前提条件

開始する前に、以下を確認してください。

* .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）。  
* 有効な Aspose.Words for .NET ライセンスまたは無料評価キー。  
* コードから参照できるフォルダーに配置した画像ファイル（例：`logo.png`）。  
* Visual Studio 2022 または任意の C# 対応 IDE。

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## Aspose.Words で空白の Word 文書を作成する方法

最初のステップは常に **空白の Word 文書を作成** することです。このオブジェクトが以降のすべての図形をホストします。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` は `.docx` ファイル全体を表します。この時点でファイルは空であり、*空白の Word 文書を作成* という要件を満たしています。

## 複数の図形をグループ化するコンテナの作成

図形をグループ化すると、まとめて移動、回転、サイズ変更が可能になります。Aspose.Words はこの目的のために `GroupShape` クラスを提供しています。

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

`Bounds` 四角形はグループがページ上に表示される位置を決定します。グループを最初の段落に配置することで、**空白の Word 文書を作成** した直後に視覚的なコンテナが確実に含まれます。

## グループ内に矩形図形を追加する方法

一般的な要件として、背景や枠線として **矩形図形を追加** することがあります。以下のコードは矩形を作成し、先に定義したグループに追加します。

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

矩形が `GroupShape` の内部に存在するため、後から追加する他の図形と一緒に移動します。これが **複数の図形をグループ化** 機能の核心です。

## グループ内に画像図形を挿入する方法

次に、**画像図形を挿入**（ロゴ）し、矩形の横に配置します。これにより **Word に画像を追加** のワークフローが実演されます。

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

`SetImage` メソッドはファイルを読み込み、画像を直接 Word 文書に埋め込みます。これにより、元ファイルが移動されても画像が保持されます。これで **画像図形の挿入** 手順が完了し、**Word に画像を追加** の要件が満たされます。

## 文書を保存する

最後に、ファイルをディスクに永続化します。保存されたファイルには空白文書、グループ化された矩形、埋め込まれたロゴが含まれます。

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

`GroupShape.docx` を Microsoft Word で開くと、薄いグレーの矩形とロゴが横並びに配置された単一のグループが表示されます。グループの任意の部分を選択すると、全体を移動またはサイズ変更でき、図形が確実に **複数の図形をグループ化** されていることが確認できます。

## 完全な実行可能サンプル

以下はコピーして貼り付け、実行できるフルプログラムです。`YOUR_DIRECTORY` を実際に存在する絶対パスまたは相対パスに置き換えてください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### 期待される出力

* `YOUR_DIRECTORY` に作成される `GroupShape.docx` という名前のファイル。  
* Word でファイルを開くと、左側にグレーの矩形、右側に `logo.png` が配置された単一の視覚的グループが表示されます。  
* 視覚的グループの任意の部分を選択すると、全体を移動またはサイズ変更でき、図形が正しく **複数の図形をグループ化** されていることが確認できます。

## よくある質問とエッジケースの対処

| 質問 | 回答 |
|---|---|
| **同じグループに 2 つ以上の図形を追加できますか？** | はい。追加の `Shape` ごとに `group.AppendChild(yourShape)` を呼び出します。グループは任意の数の描画オブジェクトを保持できます。 |
| **画像ファイルが見つからない場合はどうなりますか？** | `SetImage` は `FileNotFoundException` をスローします。try‑catch ブロックで呼び出しをラップし、代替（例：プレースホルダー図形）を提供してください。 |
| **図形に `WrapType` を設定する必要がありますか？** | デフォルトでは図形はインラインです。フローティング動作が必要な場合は、グループに追加する前に `picture.WrapType = WrapType.Inline;` などのラップモードを設定してください。 |
| **文書サイズがグループの境界に与える影響は？** | `Bounds` 四角形はポイント単位で定義されます（1 pt ≈ 1/72 in）。ページレイアウト（例：A4 と Letter）を変更する場合はサイズを調整してください。 |
| **同じグループを別の文書で再利用できますか？** | はい。`GroupShape cloned = (GroupShape)group.Clone(true);` でグループをクローンし、別の `Document` に挿入できます。 |

## プロのコツ

* **`DocumentBuilder` を再利用** して、グループの前後にテキストを追加します。現在のカーソル位置を自動的に尊重します。  
* **`Shape.StrokeColor` を設定** すると、矩形の枠線が視覚的に表示されます。  
* **ロゴには高解像度 PNG を使用** して、拡大時のピクセル化を防ぎます。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}