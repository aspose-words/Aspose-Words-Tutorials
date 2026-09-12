---
category: general
date: 2026-09-11
description: Aspose.Words を使用して Word 文書を作成し、長方形の図形を追加し、図形のサイズを設定する方法を学びます。正確な図形サイズ設定のためのステップバイステップ
  C# ガイド。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: ja
lastmod: 2026-09-11
og_description: C#でAspose.Wordsを使用してWord文書を作成します。このガイドでは、長方形のシェイプを追加し、シェイプのサイズを設定し、プログラムでシェイプの寸法を管理する方法を示します。
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: シェイプ付きWord文書を作成する – Aspose.Words C# チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: C#でAspose.Wordsを使用してシェイプ付きWord文書を作成する方法
url: /ja/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用した C# でシェイプ付き Word 文書の作成方法

カスタムグラフィックを含む **create word document** が必要な場合、コードだけで完全に作成できます。このチュートリアルでは、Word ファイルの作成、矩形シェイプの追加、シェイプのすべての寸法の制御方法を順を追って説明します。最後まで読むと、任意の .NET プロジェクトに組み込める再利用可能なスニペットが手に入ります。

**add rectangle shape**、**set shape size**、**set shape dimensions** をグループ化コンテナ内で行う方法を学びます。例は Aspose.Words 13.9 を使用していますが、概念は後続バージョンでも適用できます。Aspose の描画 API の事前経験は不要で、基本的な C# の知識があれば十分です。

## 前提条件

- .NET 6.0 以降がインストールされていること  
- Aspose.Words for .NET NuGet パッケージ (`Install-Package Aspose.Words`)  
- Visual Studio 2022 などの IDE（C# をサポートするエディタであれば可）  

これらのツールが揃っていれば、追加設定なしでコードをすぐに実行できます。

## 手順 1: ドキュメントとビルダーの初期化 – create word document の基本

最初の操作は `Document` オブジェクトと `DocumentBuilder` をインスタンス化することです。`Document` はファイル自体を表し、`DocumentBuilder` はコンテンツ挿入用の流暢な API を提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
ドキュメントを最初に作成することで、クリーンなキャンバスが得られます。ビルダーのカーソルは最初の段落に位置しており、ここで後ほど **create shapes in word** を行います。

## 手順 2: 複数のグラフィックを保持する GroupShape の構築

`GroupShape` はコンテナのように機能し、グループ全体を単一ユニットとして移動、回転、サイズ変更できます。ここではコンテナの幅と高さをポイント単位で定義します（1 pt ≈ 1/72 in）。

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Why this matters:**  
シェイプをグループ化することでレイアウト管理が簡素化されます。後でさらにシェイプ（例: 円やテキストボックス）を追加する場合、グループの位置とスケーリングを継承します。

## 手順 3: 矩形シェイプの作成と寸法の設定

ここで実際の矩形を追加します。`Shape` コンストラクタはドキュメント参照とシェイプタイプを必要とします。作成後、明示的に **set shape size** と **set shape dimensions** を設定します。

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Why this matters:**  
幅・高さ・左・上を指定することで、シェイプをピクセル単位で正確に制御できます。これは、ドキュメントがデザイン仕様や印刷フォームと一致する必要がある場合に不可欠です。

## 手順 4: 矩形を追加してグループを組み立てる

矩形を `GroupShape` に追加すると子ノードになります。グループをドキュメントに挿入する前に、必要なだけ子ノードを追加できます。

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:** 2 番目のシェイプを追加する場合は、同様に作成し `group.AppendChild(secondShape)` を呼び出します。すべての子はグループの座標系を共有します。

## 手順 5: グループ化シェイプをドキュメントに挿入して保存

グループが完全に構築されたら、現在の段落に配置します。ビルダーの `CurrentParagraph` プロパティは基礎となるノードツリーへの直接アクセスを提供します。

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Why this matters:**  
グループを段落に追加すると、シェイプがテキストの流れにインラインで表示されます。ドキュメントを保存することで **create word document** 操作が完了します。

## 一般的なバリエーションとエッジケース

| シナリオ | 調整 |
|----------|------------|
| **Different page orientation** | グループ作成前に `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` を設定します。 |
| **Multiple rectangles** | 追加の `Shape` オブジェクトを作成し、各々に対して `group.AppendChild(newRect)` を呼び出します。 |
| **Dynamic size based on content** | 画像の寸法やテキストメトリクスから幅/高さを計算し、`rectangle.Width` / `rectangle.Height` に割り当てます。 |
| **Export to PDF** | `doc.Save` 後に `doc.Save("GroupShape.pdf", SaveFormat.Pdf);` を呼び出します。 |
| **Compatibility with older Word versions** | Word 97‑2003 互換性のために `Docx` の代わりに `SaveFormat.Doc` で保存します。 |

これらのバリエーションは、同じコアロジックをさまざまな実務要件に適用できることを示しています。

## 完全な実行可能サンプル

以下はコピー、貼り付け、実行できる完全なプログラムです。すべての `using` ディレクティブ、`Main` エントリーポイント、および各行を説明するコメントが含まれています。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Expected output:**  
*GroupShape.docx* を開くと、1 ページ目に左/上マージンから 50 pt の位置に灰色の枠線の矩形が表示され、矩形自体はグループ内で 10 pt オフセットされています。寸法はコードで設定した値と一致します。

## 結論

これで Aspose.Words を使用して **create word document**、**add rectangle shape**、そして正確に **set shape size** と **set shape dimensions** を行う方法が分かりました。グループ化シェイプのアプローチにより、レイアウトが柔軟になり、追加のグラフィックやテキストボックスなど将来的な拡張にも対応できます。

次に、円や矢印、カスタム SVG パス用の **create shapes in word** などの関連トピックを調べ、**set shape fill color** や **apply rotation** の方法を学びましょう。さまざまな測定単位で Word がポイントとセンチメートルをどのように描画するかを試し、コードを大規模なドキュメント生成パイプラインに統合してください。

コーディングを楽しんでください。このパターンは、あらゆる自動レポート作成やフォーム入力シナリオに自由に適用してください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [C# を使用して Word に矩形シェイプを作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [影付き矩形シェイプで空白の Word 文書を作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words シェイプシャドウチュートリアル – C# で Word シェイプに影を追加](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}