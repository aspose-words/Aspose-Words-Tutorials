---
category: general
date: 2026-07-19
description: Aspose.Words を使用して Word で図形をグループ化します。矩形の図形の追加方法、楕円形の定義方法、そして図形を Word
  文書に挿入する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: ja
lastmod: 2026-07-19
og_description: Aspose.Words を使用して Word で図形をグループ化します。矩形図形の追加、楕円形の定義、そして図形を Word 文書に挿入します。
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Wordで図形をグループ化 – ステップバイステップ C# チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words を使用した Word のグループ シェイプ – 完全 C# ガイド
url: /ja/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word でシェイプをグループ化する – 完全な C# ガイド

UI をいじらずに **Word でシェイプをグループ化** したいと思ったことはありませんか？ あなただけではありません。契約書、チラシ、図表をプログラムで生成する場合でも、**矩形シェイプを追加**し、**楕円シェイプを定義**し、そして **Word でシェイプをグループ化** できれば、手作業の時間を何時間も節約できます。

このチュートリアルでは **Aspose.Words for .NET** を使用した実践的な例を順に解説します。最後まで読むと、**Word にシェイプを挿入**し、それらを組み合わせて、クライアントやチームメイトに提供できる洗練されたドキュメントを作成する方法が正確に分かります。

---

## 必要なもの

- **Aspose.Words for .NET**（最新バージョン、例: 24.9）。NuGet から `Install-Package Aspose.Words` で取得できます。
- .NET 開発環境（Visual Studio 2022 または C# 拡張機能が入った VS Code で問題ありません）。
- C# 構文の基本的な知識—特別なことは不要で、通常の `using` 文やオブジェクト作成ができれば十分です。

以上です。余計なライブラリや COM 相互運用は不要で、純粋なマネージドコードだけです。

---

## Aspose.Words を使用して Word でシェイプをグループ化する方法

以下は、既存のコードに対応したステップバイステップの解説です。各ステップでは **なぜ** それを行うのかを説明し、単に **何を** 行っているかだけでなく、好きなシェイプにパターンを適用できるようにしています。

### 手順 1: Document と Builder の設定

`Document` と `DocumentBuilder` の空オブジェクトを作成することから始めます。Builder は「ペン」のようなもので、必要な場所にコンテンツを挿入できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **なぜ？** `Document` オブジェクトは .docx ファイル全体を表し、`DocumentBuilder` は基礎となるノードツリーを意識せずにノード（シェイプなど）を挿入するための便利な API を提供します。

### 手順 2: 矩形シェイプの追加 (add rectangle shape)

ここでドキュメントに **矩形シェイプを追加** します。サイズ、位置、塗りつぶし色を設定して目立たせます。

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **ヒント:** `FillColor` は任意の `System.Drawing.Color` に変更できます。レポートで色分けされたセクションが必要なときに便利です。

### 手順 3: 楕円シェイプの定義 (define ellipse shape)

次に **楕円シェイプを定義** します。`ShapeType` が異なることと、オフセット（`Left = 120`）に注目してください。これにより楕円が矩形の横に配置されます。

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **重要な理由:** シェイプを明示的に配置することで、グループ化する前の見た目を制御できます。自動レイアウトに任せると、グループ化後に中心からずれる可能性があります。

### 手順 4: （オプション）個別シェイプを挿入してプレビュー

グループ化前に各シェイプを確認したい場合は、個別に **Word にシェイプを挿入** できます。このステップはオプションですが、デバッグに便利です。

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **プロのコツ:** シェイプの見た目が正しいと確信したらこの2行をコメントアウトしてください。そうしないと、グループ化後に重複したビジュアルが表示されます。

### 手順 5: シェイプをグループ化する方法 – GroupShape の作成

これがチュートリアルの核心です： **シェイプをグループ化する方法**。`GroupShape` を作成し、矩形と楕円を添付し、グループが周囲のテキストとどのように動作するかを決定します。

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **説明:** `GroupShape` は実質的に他のシェイプを保持するミニキャンバスです。`WrapType` を `Inline` に設定すると、テキストの追加や削除時にグループ全体が一つの単位として移動します。

### 手順 6: グループ化されたシェイプをドキュメントに挿入 (insert shape into word)

ここで **Word にシェイプを挿入** します—ただし今回は個々のパーツではなく、グループ化されたコンテナです。

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **内部で何が起きているか？** `InsertNode` 呼び出しは `GroupShape` をドキュメントのノードコレクションに追加します。グループにはすでに矩形と楕円が含まれているため、1つのオブジェクトとして一緒に表示されます。

### 手順 7: ドキュメントを保存

最後に、ファイルをディスクに書き込みます。プロジェクトの構成に合わせてパスを変更できます。

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **結果:** Microsoft Word で `GroupShape.docx` を開くと、淡い青色の矩形とコーラル色の楕円が一緒にロックされているのが見えます。どちらかをドラッグするともう一方も動きます—まさに “Word でシェイプをグループ化” が約束する動作です。

---

## ビジュアルでの確認

以下は、グループ化されたシェイプが Word ファイル内でどのように見えるかのモックアップです。  

![Screenshot of grouped shapes in a Word document created with Aspose.Words](grouped_shapes_placeholder.png "group shapes in word")

*画像の alt テキストにはアクセシビリティと SEO のための主要キーワードが含まれています。*

---

## よくある質問とエッジケース

### 2 つ以上のシェイプが必要な場合は？

`groupShape.AppendChild(yourNewShape);` をグループに挿入する前に呼び出し続けるだけです。API には子シェイプの数に制限はありません。

### グループ全体を回転またはサイズ変更できますか？

もちろんです。`GroupShape` は `Shape` を継承しているため、グループ自体に `RotationAngle`、`Width`、`Height` などのプロパティを設定すれば、すべての子シェイプがそれに従います。

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### グループの背景色を変更するには？

`groupShape.FillColor` を使用します。これにより見えないバウンディングボックスが塗りつぶされ、ハイライトに便利です。

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### 古い Word フォーマット（.doc）でも動作しますか？

`Aspose.Words` は `.doc` 形式でも保存可能です—`Save` のファイル拡張子を変更すればよいだけです。ただし、グループ化のような高度なシェイプ機能は OOXML の `.docx` 形式でのみ完全にサポートされています。

---

## 完全な動作例

以下のブロックを新しいコンソールアプリにコピー＆ペーストすると、全工程を実際に確認できます。欠けている部分はなく、これは **完全な実行可能サンプル** です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**期待される出力:** `GroupShape.docx` を開くと、淡い青色の矩形と淡いコーラル色の楕円からなる単一のグループオブジェクトが並んで表示されます。

---

## まとめ

ここまでで、Aspose.Words を使用して **Word でシェイプをグループ化** するために必要なすべてを網羅しました：

1. ドキュメントとビルダーを作成する。  
2. 明示的なサイズで **矩形シェイプを追加**し、**楕円シェイプを定義**する。  
3. （オプション）**Word にシェイプを挿入**して簡単にプレビューする。  
4. `GroupShape` を使用して **シェイプをグループ化**—各子を追加し、ラップ設定を行い、挿入する。  
5. ファイルを保存し、結果を確認する。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を応用した密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装方法を検討するのに役立ちます。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}