---
category: general
date: 2026-08-10
description: Aspose.Words を使用してプログラムで Word 文書を作成し、複数のシェイプをグループ化する方法、Word に長方形を追加する方法、C#
  でグループ シェイプを作成する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: ja
lastmod: 2026-08-10
og_description: Aspose.Words を使用してプログラムで Word 文書を作成します。このガイドでは、複数のシェイプをグループ化する方法、Word
  に矩形を追加する方法、プレーンテキストのコンテンツ コントロールを埋め込む方法をすべて C# で示します。
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: プログラムでWord文書を作成 – C#でシェイプをグループ化
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: C#でプログラム的にWord文書を作成し、シェイプをグループ化する
url: /ja/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でプログラム的に Word 文書を作成し、シェイプをグループ化する

プログラム的に **create word document programmatically** する必要がある場合、このチュートリアルでは Aspose.Words を使用して DOCX ファイルを作成し、**group multiple shapes word** を一緒にグループ化する方法を示します。また、**add rectangle to word** と **how to create group shape** についても取り上げ、矩形と楕円の両方を含むグループシェイプと、ユーザー入力用のプレーンテキスト StructuredDocumentTag を作成します。

最終的に、グループ化された矩形‑楕円シェイプと、ユーザーが名前を入力できるコンテンツコントロールを含む、すぐに使用できる Word ファイルが完成します。コード実行後に Word で手動編集する必要はありません。

## 必要なもの

- .NET 6.0 以降（サンプルは .NET 6 を対象としていますが、最近の .NET バージョンであればどれでも動作します）
- Aspose.Words for .NET のライセンス（無料トライアルでテスト可能）
- Visual Studio 2022 またはお好みの C# IDE
- C# 構文の基本的な知識

## プログラム的に Word 文書を作成する – 全体的なワークフロー

このプロセスは 3 つの論理的フェーズで構成されます：

1. **Initialize** a `Document` と `DocumentBuilder` を初期化します – 生成するすべての Word ファイルの基盤です。
2. **Build a group shape** で矩形と楕円を保持するグループシェイプを作成します – **group multiple shapes word** と **how to create group shape** を示します。
3. **Insert a StructuredDocumentTag (SDT)** – エンドユーザーがデータを入力できるプレーンテキストのコンテンツコントロールで、全体の文書レイアウトの一部として **add rectangle to word** を示します。

以下に、完全な実行可能コードとステップバイステップの解説を示します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### ステップ 1 – ドキュメントとビルダーの初期化
`Document` オブジェクトは DOCX ファイル全体を表し、`DocumentBuilder` はコンテンツ追加のための便利な API を提供します。これらを初期化することは、**create word document programmatically** を行う際の最初の要件です。

> **Pro tip:** 複数の操作で同じドキュメントを再利用する予定がある場合、不要なオブジェクト生成を避けるために `DocumentBuilder` のインスタンスを1つだけ保持してください。

### ステップ 2 – グループシェイプコンテナの作成
`ShapeType.Group` を持つ `Shape` は他のシェイプを保持できるキャンバスとして機能します。`Width` と `Height` を設定することでグループのバウンディングボックスが定義されます。これは Aspose.Words における **how to create group shape** の核心です。

> **Edge case:** グループの幅が子シェイプの合計幅より小さい場合、子シェイプは切り取られます。必ずすべての子シェイプを収められるだけの十分な大きさにしてください。

### ステップ 3 – Word に矩形を追加
`ShapeType.Rectangle` で矩形を作成します。`Left` と `Top` プロパティでグループの原点に対する位置を指定します。このステップは **add rectangle to word** を示し、正確な配置を制御できることを示します。

> **Common mistake:** `Left`/`Top` を設定し忘れると、矩形がグループのデフォルト原点 (0,0) に表示され、他の子シェイプと重なる可能性があります。

### ステップ 4 – グループに楕円（円）を追加
楕円は矩形と同様の方法で追加しますが、`ShapeType.Ellipse` を使用します。`Left = 210` により矩形の右側に移動し、同じグループ内で視覚的に区別された 2 つのシェイプのペアが作られます。

> **Why use a group?** グループ化すると、後で単一の操作で両方のシェイプを一緒に移動、回転、サイズ変更でき、相対的なレイアウトが保たれます。

### ステップ 5 – 完成したグループシェイプをドキュメントに挿入
`builder.InsertNode(groupShape)` は現在のカーソル位置にグループ全体を配置します。グループはすでに子シェイプを含んでいるため、矩形や楕円に対して追加の挿入呼び出しは不要です。

### ステップ 6 – プレーンテキスト StructuredDocumentTag (SDT) を作成
StructuredDocumentTag は、ドキュメントが Word で開かれたときにエンドユーザーが入力できるコンテンツコントロールです。`Title = "CustomerName"` を設定すると、コントロールに意味のある識別子が付与され、後のデータ抽出に役立ちます。

> **Why a plain‑text SDT?** 入力をプレーンテキストに制限することで、誤って書式設定が行われ、下流の処理が壊れるのを防ぎます。

### ステップ 7 – ドキュメントを保存
`doc.Save("GroupAndSDT.docx")` はファイルをディスクに書き込みます。生成された DOCX にはグループ化されたシェイプと SDT が含まれます。Microsoft Word でファイルを開くと、矩形と円が隣り合って表示され、両方が単一オブジェクトとして選択可能で、その下に「Enter name here …」というプレースホルダーが表示されます。

#### 期待される出力
- 実行フォルダーに **GroupAndSDT.docx** という名前のファイルが作成されます。
- Word では、矩形と楕円からなるグループシェイプが単位として移動可能です。
- グループのすぐ下に、ユーザーに名前入力を促す灰色のシェーディングがされたコンテンツコントロールが表示されます。

## 追加のバリエーションとベストプラクティス

### 異なるシェイプタイプの使用
`ShapeType.Rectangle` や `ShapeType.Ellipse` を他の任意の `ShapeType`（例: `ShapeType.Polygon`、`ShapeType.Line`）に置き換えることができます。グループ化ロジックは同じままです。

### 塗りつぶし色と枠線の設定
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
塗りつぶしとストロークを追加すると、特に文書が非技術的なステークホルダーと共有される場合に視覚的な区別が向上します。

### グループ全体の回転
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
グループ全体を回転させる方が、各子シェイプを個別に回転させるよりも効率的です。

### PDF へのエクスポート
PDF バージョンが必要な場合は、次のように呼び出すだけです：

```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
すべてのグループ化されたシェイプと SDT（テキストフィールドとしてレンダリングされます）が PDF に表示されます。

## よくある落とし穴と回避方法

| 症状 | 原因 | 対策 |
|------|------|------|

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for .NET を使用して Word 文書にグループシェイプを作成](/words/english/net/working-with-shapes/add-group-shape/)
- [C# を使用して Word に矩形シェイプを作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [影付き矩形シェイプで空白の Word 文書を作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}