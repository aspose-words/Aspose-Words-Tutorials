---
category: general
date: 2026-09-11
description: C# を使用して Word で図形を非表示にする方法を学びます。このガイドでは、長方形の図形を挿入する方法と、Aspose.Words を使って図形を
  Word 文書に挿入する方法も紹介しています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: ja
lastmod: 2026-09-11
og_description: C# と Aspose.Words を使用して Word で図形を非表示にする方法。ステップバイステップのチュートリアルに従って、長方形の図形を挿入し、Word
  文書内の図形を管理しましょう。
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Wordで図形を非表示にする方法 – 完全なC#ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: C# と Aspose.Words を使用して Word で図形を非表示にする方法
url: /ja/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words で Word の図形を非表示にする方法

Word の図形を文書構造内に残したまま非表示にしたい場合、本チュートリアルでその手順を詳しく解説します。Aspose.Words for .NET を使用すれば、矩形の図形を挿入し、非表示にし、後から処理できるように位置情報を保持したままにできます。

Word の自動化では、テンプレート生成やレポート作成、文書編集サービスの構築などで図形を細かく制御する必要があります。このガイドを読み終えると、以下ができるようになります。

* Word 文書に矩形の図形を挿入する（`insert rectangle shape`）。
* 図形を削除せずに非表示にする（`how to hide shape in word`）。
* 結果を保存し、非表示の図形がレンダリングビューに表示されないことを確認する（`insert shape into word document`）。

本例は Aspose.Words 24.10 以降で動作し、.NET 6.0+ を対象としていますが、概念は以前のバージョンでも適用できます。

## 前提条件

* **Aspose.Words for .NET** ≥ 24.10。Aspose のウェブサイトから無料の一時ライセンスを取得できます。
* **.NET SDK** 6.0 以上がマシンにインストールされていること。
* Visual Studio 2022、VS Code、または Rider などの開発環境。
* C# と Word Open XML の基本的な知識（任意だがあると便利）。

## Aspose.Words で Word の図形を非表示にする方法

以下は、ドキュメント作成から矩形図形の挿入、最終的に非表示にするまでの一連の流れを示す、完全に実行可能なサンプルプログラムです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### 各ステップの説明

1. **新しいドキュメントを作成** – `Document` はメモリ上の Word ファイルを表します。`DocumentBuilder` はコンテンツ挿入用のフルエント API を提供します。  
2. **矩形図形を挿入** – `InsertShape` が `Rectangle` タイプの描画オブジェクトを作成します。サイズはポイント単位（1 pt ≈ 1/72 in）で指定します。これが `insert rectangle shape` の要件を満たします。  
3. **図形を非表示に設定** – `Shape.Hidden = true` と設定すると、Word のマークアップに `<w:hidden/>` が付加され、図形は非表示になります。文書ツリー上には残るため、後から `Hidden = false` にして再表示したり、プログラムから参照したりできます。これが `how to hide shape in word` の核心です。  
4. **ファイルを保存** – ドキュメントは `output.docx` に書き出されます。Microsoft Word で開くと矩形は表示されませんが、XML 内に存在し、ZIP ビューアや Open XML SDK で確認できます。

### 期待される結果

`output.docx` を Microsoft Word で開くと:

* 文書は空白に見え、目に見える図形はありません。  
* 基礎 XML（`word/document.xml`）を確認すると、`<w:pict>` 要素内に `<w:hidden/>` 属性が付いた図形が存在することが分かります。

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

`Hidden = false` に設定して再保存すれば、非表示の図形を再び表示できます。

## Word 文書に矩形図形を挿入する

図形を非表示にすることが主目的でも、多くのシナリオでは最初に図形を挿入します。`InsertShape` メソッドは `Rectangle` のほか、`Ellipse`、`Line`、カスタム画像など多数の `ShapeType` をサポートしています。

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**なぜ矩形を使うのか？**  
矩形は軸に平行なシンプルなコンテナで、テキスト、画像、他の入れ子図形を保持できます。テーブルやチャートといった動的コンテンツのプレースホルダーとして頻繁に利用されます。先に矩形を挿入しておくことで、後で非表示にした際もレイアウトの一貫性が保たれます。

## Word 文書に図形を挿入する際のベストプラクティス

`insert shape into word document` を行う際は次の点に留意してください。

* **明示的なサイズ指定** – 自動サイズに依存せず、ポイント単位で幅と高さを指定してプラットフォーム間でレイアウトを統一します。  
* **位置指定** – デフォルトでは現在の段落にアンカーされます。`builder.MoveTo` や `builder.StartBookmark` を使って正確に配置しましょう。  
* **早期のスタイリング** – 塗りつぶし色、線スタイル、テキストの折り返しは最終的な外観に影響します。非表示の図形でもマークアップは変わらないため、適切に設定しておくと後からの操作が楽になります。  
* **バージョン互換性** – `Hidden` プロパティは Aspose.Words 24.10 以降で利用可能です。古いバージョンを対象とする場合は、`Node` API を使って手動で `<w:hidden/>` 属性を追加してください。

### 手動で hidden 属性を追加する（フォールバック）

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## 完全なエンドツーエンド例

すべてをまとめた単一プログラムは以下の通りです。

1. 矩形図形を挿入。  
2. その図形を非表示に設定。  
3. コントラスト用に可視の楕円を挿入。  
4. ドキュメントを保存。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

プログラムを実行すると `demo_output.docx` が生成されます。開くとコーラル色の楕円だけが表示され、緑の矩形は XML に残っているものの非表示状態です。

## よくある質問とエッジケース

**Q: 図形を非表示にするとページ割り付けに影響しますか？**  
A: 影響しません。非表示の図形はレイアウトエンジンに無視されるため、スペースを消費せず、ページブレークにも影響しません。

**Q: ヘッダーやフッター内の図形も非表示にできますか？**  
A: できます。`Hidden` プロパティは文書ツリー内の任意の場所にある図形（ヘッダー、フッター、テーブル内部など）に対して機能します。

**Q: 複数の図形を一括で非表示にしたい場合は？**  
A: `Document.GetChildNodes(NodeType.Shape, true)` コレクションを走査し、対象となる各図形に対して `Hidden = true` を設定します。

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: PDF 変換時に hidden 属性は保持されますか？**  
A: PDF 変換時はデフォルトで非表示の図形は除外され、Word の描画と同様の結果になります。PDF に含めたい場合は、変換前に図形を再表示（`Hidden = false`）してください。

## コツと落とし穴

* **プロのコツ:** 非表示にする前に `shape.WrapType = WrapType.None` を設定すると、後で再表示した際に周囲のテキストが乱れません。  
* **古い Aspose.Words バージョンに注意:** 24.10 未満では `Hidden` プロパティが `NotSupportedException` を投げます。その場合は手動で XML に属性を追加してください。  
* **テスト:** 生成した `.docx` は必ず Word で開き、開発タブの「XML マークアップの表示」で `<w:hidden/>` が存在することを確認しましょう。

## 結論

これで C# と Aspose.Words を使って Word の図形を非表示にする方法、矩形図形の挿入方法、そして図形の可視性をフルコントロールする手順がマスターできました。`Hidden` プロパティを活用すれば、図形を文書モデルに残したままエンドユーザーにはクリーンなビューを提供できます。

次は **実行時に図形プロパティを更新する**、**非表示図形を画像に変換する**、または **Open XML SDK で hidden 要素を直接操作する** といったトピックに挑戦してみてください。これらの拡張により、さらに高度なシナリオに対応できるようになります。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれているので、API の追加機能を習得したり、独自の実装アプローチを探求したりするのに役立ちます。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}