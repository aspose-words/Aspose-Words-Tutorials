---
category: general
date: 2026-10-20
description: 空白のWord文書の作成方法、Wordでの図形のグループ化、図形の塗りつぶし色の設定、インラインの折り返しタイプの使用方法を、完全なC#サンプルとともに学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: ja
lastmod: 2026-10-20
og_description: Aspose.Words と C# を使用して、空白の Word 文書を作成し、Word で図形をグループ化し、ラップタイプをインラインに設定して図形の塗りつぶし色を設定します。完全なチュートリアルをご覧ください。
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: 空白のWord文書を作成し、Wordで図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words を使って空白の Word 文書を作成し、Word で図形をグループ化する方法
url: /ja/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word で空白の Word 文書を作成し、図形をグループ化する方法

If you need to **create a blank Word document** that contains multiple shapes acting as a single unit, this guide shows you exactly how. You’ll see how to **group shapes in Word**, set a shape’s fill color, and apply **wrap type inline**—all with a concise, runnable C# program.

このガイドでは、単一のユニットとして機能する複数の図形を含む **空白の Word 文書を作成** する必要がある場合に、正確な手順を示します。**Word で図形をグループ化** する方法、図形の塗りつぶし色の設定、**wrap type inline** の適用方法を、簡潔で実行可能な C# プログラムとともに確認できます。

The tutorial walks you through every line of code, explains why each step matters, and highlights common pitfalls. By the end you’ll have a .docx file that displays a rectangle and a text box grouped together, ready for further automation.

このチュートリアルではコードの各行を順に解説し、各ステップの重要性と一般的な落とし穴を示します。最後まで読むと、矩形とテキストボックスがグループ化された .docx ファイルが作成され、さらに自動化に利用できるようになります。

## 学習できること

* Aspose.Words を使用して空の Word ファイルを初期化する方法。
* **GroupShape** を正しく作成し、子図形を追加する方法。
* **set shape fill color** のテクニックと位置制御。
* **wrap type inline** を使用して、グループが単一のインラインオブジェクトとして動作するようにする方法。
* 結果を保存し、検証する方法。

No prior experience with Aspose.Words is required, but you should be comfortable with basic C# syntax and have Visual Studio (or another IDE) installed.

Aspose.Words の事前経験は不要ですが、基本的な C# 構文に慣れており、Visual Studio（または他の IDE）がインストールされていることが望ましいです。

## 前提条件

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 以降 | C# プロジェクトのランタイムを提供します。 |
| Aspose.Words for .NET（最新バージョン） | 例で使用される `Document`、`DocumentBuilder`、および shape クラスを提供します。 |
| 書き込み可能なフォルダー パス | `doc.Save` 呼び出しが出力ファイルを書き込むために有効なディレクトリを必要とします。 |
| 基本的な C# の知識 | コードを理解し、自分のシナリオに合わせて修正できるようにします。 |

Install Aspose.Words via NuGet:

NuGet を使用して Aspose.Words をインストールします:
```bash
dotnet add package Aspose.Words
```

---

## 手順 1: 空白の Word 文書を作成する

The first operation is to **create a blank Word document**. Aspose.Words’ `Document` class represents an in‑memory Word file, and `DocumentBuilder` provides a convenient API for editing it.

最初の操作は **空白の Word 文書を作成** することです。Aspose.Words の `Document` クラスはメモリ内の Word ファイルを表し、`DocumentBuilder` は編集用の便利な API を提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*この重要性*: クリーンな文書から開始することで、追加するグループ形状が唯一のコンテンツになることが保証され、検証が簡単になります。

## 手順 2: wrap type inline を使用したグループ形状を定義する

A **GroupShape** acts as a container for other shapes. Setting its `WrapType` to `Inline` ensures the group behaves like a single inline object in the paragraph flow.

**GroupShape** は他の図形のコンテナとして機能します。`WrapType` を `Inline` に設定すると、段落の流れの中でグループが単一のインラインオブジェクトとして動作することが保証されます。

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*この重要性*: **wrap type inline** を使用すると、グループが周囲のテキストから浮き上がるのを防ぎ、グループをユニットとして移動させたい場合に不可欠です。

## 手順 3: 矩形を追加し、図形の塗りつぶし色を設定する

A rectangle is a common visual element. The `Shape` constructor takes a `ShapeType`; we then specify dimensions and fill color.

矩形は一般的なビジュアル要素です。`Shape` コンストラクタは `ShapeType` を受け取り、続いてサイズと塗りつぶし色を指定します。

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*この重要性*: `FillColor` プロパティは実際に **set shape fill color** を示し、矩形に淡い青色の背景を付けて最終文書で目立たせます。

## 手順 4: テキストボックスを追加 – 図形を効果的にグループ化する方法

A text box provides editable text inside the group. Position it relative to the group's coordinate system by adjusting the `Top` property.

テキストボックスはグループ内に編集可能なテキストを提供します。`Top` プロパティを調整して、グループの座標系に対して位置を設定します。

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*この重要性*: このステップは **how to group shapes** に答えます — 各子図形を同じ `GroupShape` インスタンスに追加することで実現します。`Top` オフセットによりテキストボックスが矩形の下に表示され、正確なレイアウト制御が示されます。

## 手順 5: 完成したグループ形状を文書に挿入する

Now that the group contains both child shapes, insert it at the current builder position.

グループに両方の子図形が含まれたので、現在のビルダー位置に挿入します。

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*この重要性*: グループを単一ノードとして挿入することで、Word が矩形とテキストボックスを一つの論理オブジェクトとして扱い、編集時に相対位置を保持します。

## 手順 6: 文書を保存し、出力を検証する

Finally, write the document to disk. Replace `YOUR_DIRECTORY` with a real path on your machine.

最後に、文書をディスクに書き込みます。`YOUR_DIRECTORY` を実際のパスに置き換えてください。

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

When you open `GroupShape.docx` in Microsoft Word, you should see a light‑blue rectangle with a text box labeled “Grouped text” positioned directly beneath it. Selecting either shape will select the entire group, confirming that **group shapes in Word** works as intended.

Microsoft Word で `GroupShape.docx` を開くと、淡い青色の矩形と、その直下に「Grouped text」とラベル付けされたテキストボックスが表示されます。いずれかの図形を選択するとグループ全体が選択され、**group shapes in Word** が意図通りに機能していることが確認できます。

### 期待される結果

* 単一の段落を含む .docx ファイル。
* 段落内に、単一の複合オブジェクトのように見えるインライングループが配置されます。
* 矩形は淡い青色で塗りつぶされ、テキストボックスには “Grouped text” が表示されます。

![生成された Word 文書のスクリーンショット](grouped_shapes.png){.center width=600 alt="Aspose.Words を使用して作成された空白の Word 文書で、グループ化された矩形とテキストボックスのスクリーンショット"}

## よくある質問とエッジケースの対処法

### グループをインラインではなくフロートさせたい場合はどうすればよいですか？

Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType` enum value). Floating groups can be positioned independently of paragraph flow, but they lose the automatic inline alignment.

`WrapType.Inline` を `WrapType.TopBottom`（または他の任意の `WrapType` 列挙値）に置き換えます。フロートするグループは段落の流れに依存せずに配置できますが、自動インライン整列は失われます。

### 円や画像など、さらに図形を追加できますか？

Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`, configure their properties, and call `group.AppendChild(newShape)`. The group will automatically expand to accommodate the new bounds if you update `group.Bounds` accordingly.

はい。`ShapeType.Ellipse` や `ShapeType.Image` を使用して追加の `Shape` オブジェクトを作成し、プロパティを設定して `group.AppendChild(newShape)` を呼び出します。`group.Bounds` を適切に更新すれば、グループは新しい境界に合わせて自動的に拡張されます。

### 子図形を追加した後にグループ全体のサイズを変更するには？

Adjust `group.Bounds` after all children are appended, or compute the union of child bounds programmatically. This ensures the group’s hit‑test area matches the visual content.

すべての子図形を追加した後に `group.Bounds` を調整するか、子図形の境界の合成をプログラムで計算します。これにより、グループのヒットテスト領域がビジュアルコンテンツと一致します。

### 出力フォルダーが存在しない場合は？

Aspose.Words は `DirectoryNotFoundException` をスローします。まずディレクトリを作成してください:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### .NET Core ではなく .NET Framework でも動作しますか？

All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are available in the .NET Framework version of Aspose.Words, so the same code works unchanged.

使用しているすべての API（`Document`、`DocumentBuilder`、`GroupShape`、`Shape`）は Aspose.Words の .NET Framework バージョンでも利用可能なため、同じコードがそのまま動作します。

## プロのコツ

* **Performance tip** – 多数のグループを挿入する際は単一の `DocumentBuilder` インスタンスを再利用します。グループごとに新しいビルダーを作成するとオーバーヘッドが増加します。
* **Visual consistency** – `rectangle.StrokeColor` を `FillColor` と同じに設定してシームレスな外観にするか、`rectangle.LineWidth = 0` を設定して枠線を非表示にします。
* **Debugging** – 多くの図形を変更した場合は保存前に `doc.UpdatePageLayout()` を呼び出します。これにより Word がレイアウトを再計算し、予期しないクリッピングを防げます。

## 結論

You now know how to **create a blank Word document**, **group shapes in Word**, **set shape fill color**, and apply **wrap type inline** using Aspose.Words for .NET. The complete example demonstrates the standard approach for building composite graphics that behave as a single object in Word.

これで **空白の Word 文書を作成**、**Word で図形をグループ化**、**図形の塗りつぶし色を設定**、そして **wrap type inline** を適用する方法が Aspose.Words for .NET を使って理解できました。完全なサンプルは、Word で単一オブジェクトとして動作する複合グラフィックを構築する標準的な手法を示しています。

From here you can explore:

* 画像やチャートなど、追加の図形を追加する。
* フロートグループ用にさまざまな `WrapType` 値を試す。
* 複数の文書にわたってグループ化された図のバッチ生成を自動化する。

Feel free to adapt the code to your own automation scenarios, and share your results in the comments!

コードを自分の自動化シナリオに合わせて自由に適用し、結果をコメントで共有してください！

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用して Word 文書にグループ形状を作成する](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words で空白の Word 文書を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [インライン図形付き Word から PDF を保存する方法 – 完全ガイド](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}