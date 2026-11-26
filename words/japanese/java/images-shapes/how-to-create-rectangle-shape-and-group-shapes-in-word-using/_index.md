---
category: general
date: 2026-11-18
description: C# を使用して Word 文書に長方形の図形を作成する方法を学びます。このガイドでは、図形のサイズ設定、位置設定、そして Word での図形のグループ化についても解説しています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: ja
lastmod: 2026-11-18
og_description: C# を使用して Word ファイルに長方形の図形を作成し、図形のサイズ設定、位置設定、そして Word での図形のグループ化を学びます。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: C#でWordに矩形シェイプを作成し、シェイプをグループ化する
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# を使用して Word で矩形の図形を作成し、図形をグループ化する方法
url: /ja/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word で長方形シェイプを作成し、シェイプをグループ化する方法

Word 文書で **長方形シェイプを作成** する必要がある場合、このチュートリアルでは完全な実行可能ソリューションを示します。シェイプのサイズ設定、位置設定、そしてシェイプを Word でグループ化して単一のオブジェクトとして動作させる方法が分かります。

プログラムでレポート、請求書、または図表を生成する際にシェイプを扱うことは一般的な要件です。このガイドの最後までに、`.docx` ファイルに長方形、楕円、そしてグループ化されたコンテナを含めることができるようになります—すべて Aspose.Words for .NET で作成されています。

## Prerequisites

- .NET 6.0 SDK 以降（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- コードエディタまたは IDE（Visual Studio、VS Code、Rider など）

追加のライブラリは必要ありません。

## How to create rectangle shape and group shapes in Word

The core steps are:

1. **空のドキュメント** と `DocumentBuilder` を作成します。
2. 個々のシェイプを保持する `GroupShape` を挿入します。
3. `rectangle` シェイプを作成し、サイズを設定してグループに追加します。
4. `ellipse` シェイプを作成し、サイズと位置を設定してグループに追加します。
5. ドキュメントを **保存** します。

Each step is explained below, and the complete source code follows the explanation.

### Step 1: Initialize the document and builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` は Word ファイル全体を表し、`DocumentBuilder` はコンテンツ挿入用のフルエント API を提供します。シェイプを追加する前にこれらを初期化する必要があります。

### Step 2: Insert a group shape

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` はコンテナのように機能し、すべての子シェイプが一緒に移動します。これは、移動、回転、削除などの集合的な変換が必要なときに **Word でシェイプをグループ化** する推奨方法です。

### Step 3: Create the rectangle and set its size

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

ここでは `rectangle` シェイプを作成し、`Width` と `Height` を割り当てて **シェイプのサイズを設定** しています。Aspose.Words ではサイズはポイントで表されます（1 pt ≈ 1/72 in）。寸法を明示的に設定することで、長方形が意図した通りに表示されます。

### Step 4: Create the ellipse, set dimensions, and position it

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

楕円の **シェイプ寸法の設定** は幅と高さが同じで、完全な円が生成されます。`Left` プロパティは **シェイプの位置設定** を示しており、楕円はグループの原点から右へ 120 pt の位置から開始するため、長方形と重なりません。

### Step 5: Save the document

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

保存により Word ファイルがディスクに書き込まれます。`GroupShape.docx` を Microsoft Word で開くと、長方形と楕円が正しくグループ化され、位置が設定されていることを確認できます。

## Setting shape dimensions and size – deeper look

- **Points vs. inches**: 72 pt = 1 in. If you prefer inches, multiply by 72 (e.g., `2.5 * 72` for 2.5 in). → **ポイントとインチ**: 72 pt = 1 in。インチ単位が好みの場合は 72 倍してください（例: `2.5 * 72` は 2.5 in）。
- **Automatic scaling**: If you omit `Width` or `Height`, the shape uses its default size. Explicitly **set shape size** to avoid layout surprises. → **自動スケーリング**: `Width` または `Height` を省略すると、シェイプはデフォルトサイズを使用します。レイアウトの予期せぬ変化を防ぐために、明示的に **シェイプのサイズを設定** してください。
- **Aspect ratio**: For shapes like `Ellipse`, keeping `Width` and `Height` equal maintains a circular appearance. → **アスペクト比**: `Ellipse` のようなシェイプでは、`Width` と `Height` を同じに保つことで円形の外観が維持されます。

## Positioning a shape in Word

`Left` と `Top` プロパティはシェイプのオフセットをコンテナ（グループまたはページ）内で制御します。正の値は右下方向にシェイプを移動させ、負の値は左上方向にシフトさせます。グループ化時には、位置はグループの原点に対して相対的になるため、レイアウト計算が簡素化されます。

## Grouping shapes in Word using Aspose.Words

Grouping is essential when you want multiple shapes to act as a single unit. The `GroupShape` object:

- `AppendChild` をサポートし、任意の `Shape`（長方形、楕円、画像など）を追加できます。
- 1 回の呼び出しでグループ全体を移動、回転、削除できます。
- 子シェイプの位置はグループに対して相対的に保持され、複雑な図を管理しやすくなります。

**Pro tip:** After adding all child shapes, you can adjust the group’s `Width`, `Height`, `Left`, and `Top` to reposition the entire collection in one step. → **プロのコツ:** すべての子シェイプを追加した後、グループの `Width`、`Height`、`Left`、`Top` を調整すれば、コレクション全体を一度に再配置できます。

## Complete runnable example

Below is the full program you can copy, paste, and run. It includes all `using` directives, a `Main` method, and comments that explain each line.  

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Expected output:** After running the program, `GroupShape.docx` appears in the execution folder. Opening it in Word shows a rectangle (100 pt × 50 pt) on the left and an ellipse (80 pt × 80 pt) positioned 120 pt to the right, both inside a single grouped object. → **期待される出力:** プログラム実行後、実行フォルダーに `GroupShape.docx` が生成されます。Word で開くと、左側に 100 pt × 50 pt の長方形、右側に 120 pt ずらした位置に 80 pt × 80 pt の楕円が表示され、両方とも単一のグループ化オブジェクト内にあります。

![グループ化された長方形と楕円形を含む Word ドキュメント](grouped_shapes.png){: .center alt="C# で作成された、グループ化された長方形と楕円形シェイプを示す Word ドキュメントのスクリーンショット"}

*上の画像は最終結果を示しています。長方形と楕円は 1 つのグループとして選択可能です。*

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **2 つ以上のシェイプを追加できますか？** | はい。追加のシェイプごとに `group.AppendChild(yourShape)` を呼び出します。 |
| **グループを回転させる必要がある場合は？** | すべての子シェイプを追加した後、`group.RotationAngle = 45;`（度）を使用します。 |
| **グループの背景色を変更するには？** | `group.FillColor = System.Drawing.Color.LightGray;` を設定します。 |
| **.doc ファイルでも動作しますか？** | Aspose.Words は `.doc` と `.docx` をサポートしています。同じコードが使用できます。`Save` のファイル拡張子を変更するだけです。 |
| **多数のシェイプをグループ化するとメモリに影響がありますか？** | グループ化自体は最小限のオーバーヘッドです。主な懸念はシェイプ総数であり、大規模文書では適切な数に抑えることが推奨されます。 |

## Conclusion

In this tutorial you learned how to **create rectangle shape** in a Word file using C#, how to **set shape size**, **set shape dimensions**, **set shape position**, and finally how to **group shapes in Word** with Aspose.Words. The complete example demonstrates a clean, maintainable approach that you can extend to more complex diagrams, charts, or custom graphics.

Next, you might explore:

- シェイプ内にテキストを追加する (`Shape.TextPath.Text = "Hello"`).
- `GroupShape` に画像を挿入する。
- `doc.Save("output.pdf")` でグループ化されたシェイプを PDF にエクスポートする。

Feel free to experiment with different sizes, positions, and additional shape types to fit your project's needs. Happy coding!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words を使用して Word で長方形シェイプを作成し、シェイプをグループ化する方法](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Aspose.Words for .NET を使用して Word 文書にグループシェイプを作成する](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}