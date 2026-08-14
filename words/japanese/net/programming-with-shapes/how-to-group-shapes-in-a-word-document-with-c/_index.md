---
category: general
date: 2026-08-14
description: C# を使用して Word 文書で図形をグループ化する方法。Word 文書の作成、長方形の図形の挿入、Word での図形のグループ化、そして
  docx として文書を保存する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: ja
lastmod: 2026-08-14
og_description: C# を使用して Word 文書で図形をグループ化する方法。Word ファイルを作成し、長方形の図形を挿入し、Word で図形をグループ化し、結果を
  docx として保存する完全なチュートリアルをご覧ください。
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: C#でWord文書の図形をグループ化する方法 – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: C#でWord文書の図形をグループ化する方法
url: /ja/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word ドキュメントで図形をグループ化する方法

Word ドキュメントで **図形をグループ化する方法** が必要な場合、このガイドでは C# と Aspose.Words ライブラリを使用した正確な手順を示します。Word ドキュメントの作成、矩形図形の挿入、Word での図形のグループ化、そして最終的に **ドキュメントを docx として保存** する方法を、単一の実行可能プログラムで確認できます。

レポート、契約書、マーケティングパンフレットなどをプログラムで生成する際、図形の作成と操作は一般的な要件です。このチュートリアルの最後までに、任意の .NET プロジェクトに組み込める再利用可能なコードスニペットが手に入ります。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

- .NET 6.0 以降がインストールされている  
- Visual Studio 2022（または .NET をサポートする任意の IDE）  
- Aspose.Words for .NET のライセンス（または無料トライアル）  
- C# 構文の基本的な知識  

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## Word ドキュメントで図形をグループ化する方法

このソリューションの核となるのは 5 ステップのプロセスです。各ステップを詳しく解説し、記事の最後に完全なソースコードを掲載しています。

### 手順 1: 新しい空白ドキュメントを作成する

プログラムで **Word ドキュメントを作成** したいときに最初に行うことは、`Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の .docx ファイル全体を表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder` は高レベルのヘルパーで、基礎となるノードツリーを手動で操作せずにテキスト、テーブル、図形を挿入できます。

### 手順 2: 矩形図形を挿入する

**矩形図形を挿入** する方法を示すために、`InsertShape` メソッドを使用します。矩形はグループの最初のメンバーとして機能します。

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Why this matters:** 図形は挿入位置に対して相対的に配置されます。塗りつぶし色を設定すると、生成されたドキュメントを開いたときに図形が視認しやすくなります。

### 手順 3: 楕円形図形を挿入する

次に、**楕円形図形を挿入** します（API では `Ellipse` と呼ばれます）。これがグループの 2 番目のメンバーになります。

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Why this matters:** 矩形の直後に楕円形を挿入することで、両方の図形が同じ段落に配置され、後でのグループ化が簡単になります。

### 手順 4: 矩形と楕円形をグループ化する

ここで中心的な質問である **図形をグループ化する方法** に答えます。Aspose.Words は `AppendGroupShape` を提供してグループ コンテナを作成し、そのコンテナに対して `Group()` を呼び出します。

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Why this matters:** グループ化すると、`groupedShape` に対して行うすべての変形（移動、サイズ変更、回転）が矩形と楕円形の両方に自動的に適用されます。これにより、生成されたドキュメントのレイアウト一貫性が保たれます。

### 手順 5: ドキュメントを DOCX ファイルとして保存する

最終ステップは **ドキュメントを docx として保存** することです。任意のパスを指定できます。例ではプレースホルダー `"YOUR_DIRECTORY"` を使用していますので、実際のフォルダーに置き換えてください。

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Why this matters:** DOCX として保存するとグループ化メタデータが保持されるため、Microsoft Word でファイルを開いたときに矩形と楕円形が単一オブジェクトとして表示されます。

## 完全な実行可能サンプル

以下は 5 つのステップをすべて組み合わせた完全なプログラムです。新しいコンソール プロジェクトにコピーし、Aspose.Words NuGet パッケージを復元して実行してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### 期待される出力

`groupedShapes.docx` を Microsoft Word で開くと、ライトブルーの矩形とライトコーラルの楕円形がロックされた状態で表示されます。どちらかの図形をクリックすると両方が選択され、単一ユニットとして移動やサイズ変更が可能です。

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| **2 つ以上の図形をグループ化できますか？** | はい。任意の数の `Shape` オブジェクトを `AppendGroupShape` に渡せます。このメソッドは配列を受け取るので、コレクションを動的に構築できます。 |
| **グループをテーブルセルにアンカーしたい場合は？** | 図形をセルの段落内に挿入し、その段落で `AppendGroupShape` を呼び出します。グループはセルのアンカー設定を継承します。 |
| **グループ化は基になる XML に影響しますか？** | Aspose.Words は子図形を含む `<w:grpSp>` 要素を書き込みます。Word はこれをグループとして認識し、相対位置を保持します。 |
| **後でグループを解除するには？** | `groupedShape.Ungroup()` を呼び出します。このメソッドは個別の図形を返すので、別々に操作できます。 |
| **多数の図形をグループ化するとパフォーマンスに影響しますか？** | グループ化自体はコストが低いですが、数百の図形を含む大規模なグループをレンダリングするとファイルサイズが増加する可能性があります。サイズが問題になる場合は画像をフラット化することを検討してください。 |

## プロのコツ

- **明示的な位置を設定** (`Left`, `Top`) すると、グループ化前に正確な配置が可能です。  
- **`Shape.WrapType = WrapType.Inline`** を使用すると、グループを段落要素のように扱い、浮動オブジェクトではなくなります。  
- **グループに線スタイルを適用**（`groupedShape.LineFormat`）すると、全体に枠線を付けられます。  
- **グループを再利用**: `Group()` 呼び出し後、`groupedShape` をクローンしてドキュメント内の別の場所に挿入できます。

## 次のステップ

**図形をグループ化する方法** が分かったので、以下の関連トピックも探求してみてください。

- **矩形図形を挿入**し、図形内にカスタムテキストや画像を配置します。  
- **グループを入れ子にして**複雑な図を作成します（グループ内にグループ）。  
- **ドキュメントを PDF としてエクスポート**し、図形のグループ化を保持します（`doc.Save("output.pdf", SaveFormat.Pdf)`）。

これらはすべて、本稿で扱った基本を土台にしているため、Word 自動化ツールキットをさらに拡張するのに最適です。

## 結論

このチュートリアルでは C# を使用して Word ドキュメントで **図形をグループ化する方法** を実演しました。**Word ドキュメントを作成**、**矩形図形を挿入**、**Word で図形をグループ化**、そして最終的に **ドキュメントを docx として保存** する手順を学びました。完全な実行可能サンプルと実用的なヒントを活用すれば、任意のドキュメント生成ワークフローに図形のグループ化を組み込むことができます。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックを扱っています。各リソースには、ステップバイステップの説明と完全なコード例が含まれており、API の追加機能を習得したり、独自の実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for .NET を使用した Word ドキュメントでのグループ形状の作成](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET を使用した Word ドキュメントへの図形挿入](/words/english/net/working-with-shapes/insert-shape/)
- [C# で Word に矩形図形を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}