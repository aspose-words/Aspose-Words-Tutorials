---
category: general
date: 2026-10-04
description: C# を使用して Word で図形をグループ化する方法を学びましょう。このガイドでは、長方形の図形の挿入、複数の図形のグループ化、そしてプログラムで空の
  Word ファイルを作成する手順を示します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: ja
lastmod: 2026-10-04
og_description: C# を使用して Word で図形をグループ化します。矩形の図形を挿入し、複数の図形をグループ化し、DocumentBuilder
  で空白の Word ファイルを作成する手順をご覧ください。
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: C#でWordの図形をグループ化 – 完全なDocumentBuilderチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: C# と DocumentBuilder を使用して Word で図形をグループ化する方法
url: /ja/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と DocumentBuilder を使用した Word での図形のグループ化方法

C# アプリケーションから **Word で図形をグループ化** する必要がある場合、このチュートリアルでその手順を正確に示します。*矩形の図形を挿入* し、複数の描画を 1 つのグループに結合し、最後に **グループ化されたオブジェクトを含む空の Word ファイルを作成** する方法が分かります。

プログラムでレポート、請求書、またはカスタムテンプレートを生成する際、図形の操作は一般的な要件です。このガイドの最後までに、Aspose.Words を参照する任意の .NET プロジェクトに組み込める再利用可能なコードスニペットを手に入れることができます。

## 学べること

- ゼロから空の Word 文書を作成する方法  
- `DocumentBuilder` を使用して矩形と楕円の図形を挿入する方法  
- **複数の図形を `GroupShape` にグループ化** する方法  
- **append child to group** を使って階層を構築する方法  
- ファイルをディスクに保存し、結果を確認する方法  

Aspose.Words の事前知識は不要ですが、C# と .NET 開発の基本的な理解があるとスムーズです。

## 前提条件

| 必要条件 | 理由 |
|----------|------|
| .NET 6.0 以降 | C# コードの実行環境を提供します。 |
| Aspose.Words for .NET（最新バージョン） | `Document`、`DocumentBuilder`、図形クラスを利用できるようにします。 |
| Visual Studio 2022（または VS Code）などの IDE | サンプルのコンパイルと実行を容易にします。 |
| マシン上のフォルダーへの書き込み権限 | `doc.save` 呼び出しに必要です。 |

NuGet で Aspose.Words をインストールします:

```bash
dotnet add package Aspose.Words
```

---

## Word で図形をグループ化 – ステップバイステップガイド

以下は完全に実行可能なプログラムです。各セクションを詳細に説明し、**コードが何をするか** だけでなく **なぜそのように書かれているか** を理解できるようにしています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 各ステップの重要性

1. **空の Word ファイルを作成** – クリーンなドキュメントから始めることで、隠れた書式設定が図形の位置に影響することを防ぎます。  
2. **DocumentBuilder の初期化** – `DocumentBuilder` は低レベルのノード操作を抽象化し、レイアウトに集中できるようにします。  
3. **個別の図形を挿入** – グループ化する前に、まずは別々のオブジェクト（矩形と楕円）を作成します。`Left` と `Top` を調整して横並びに配置します。  
4. **複数の図形をグループ化** – `GroupShape` を作成し **append child to group** を使用することで、2 つの独立した描画を 1 つの論理単位に変換します。グループ全体を移動またはサイズ変更すると、子要素が同時に影響を受けます。  
5. **ドキュメントを保存** – 最終ファイル `GroupedShapes.docx` は Microsoft Word で開き、矩形と楕円が実際にグループ化されていることを確認できます（どちらかを選択すると両方が一緒に動きます）。

### 期待される出力

Microsoft Word で `GroupedShapes.docx` を開くと:

- 矩形と楕円が隣り合って配置されているのが見えます。  
- どちらかの図形を選択すると両方がハイライトされ、同じグループに属していることが確認できます。  
- グループは単一のオブジェクトとしてドラッグ、サイズ変更、書式設定が可能です。

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Word 文書内でグループ化された矩形と楕円の図"}

*スクリーンショットは最終的なグループ化図形を示しています。*

---

## 矩形図形の挿入 – サイズとスタイルのカスタマイズ

特定の塗りつぶし色や枠線が必要な矩形の場合、挿入後に `Shape` オブジェクトを次のように変更します:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

これらのプロパティは `Shape` クラスの一部であり、矩形に限らずすべての図形タイプで機能します。**append child to group** の前にスタイルを調整すると、グループが設定したビジュアルプロパティを継承します。

---

## 複数の図形をグループ化 – 2 つ以上のオブジェクトを扱う

サンプルは矩形と楕円をグループ化していますが、任意の数の図形を追加できます:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**プロのコツ:** 複雑なグループを作成したら、レイアウトをロックして誤操作を防止できます:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – 順序が重要

`AppendChild` を呼び出す順序が Z‑order（どの図形が前面に来るか）を決定します。サンプルでは矩形を先に、次に楕円を追加しているため、交差した場合は楕円が矩形の上に表示されます。順序の変更は `RemoveChild` で削除し、再度追加するだけで簡単に行えます:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## 空の Word ファイル作成 – 再利用可能なヘルパーメソッド

アプリケーションで頻繁に新規文書が必要な場合、作成ロジックをカプセル化します:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

これにより、メインプログラムの `new Document()` 行を `CreateBlankWordFile()` に置き換えるだけで、**空の Word ファイル作成** の概念を再利用可能にできます。

---

## よくある落とし穴と回避策

| 問題 | 発生理由 | 対策 |
|------|----------|------|
| 図形がページ外に表示される | デフォルトの `Left`/`Top` が 0 で、余白に配置されるため | 挿入後に `Left` と `Top` を明示的に設定する |
| グループが書式を失う | 子図形をグループに追加した後にプロパティを変更するとレイアウトが崩れる | **append child to group** の **前** にすべての視覚プロパティを適用する |
| 保存したファイルが空になる | `DocumentBuilder` でノードを追加せず、別の `Document` インスタンスに対して `doc.Save` を呼び出した | ビルドした同じ `Document` インスタンスを保存しているか確認する |
| Word で互換性警告が出る | 新しい図形機能を使用していて、古い Word バージョンがサポートしていない | 必要に応じて互換モードまたは古い機能に限定する |

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自の実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書でのグループ形状の作成](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET を使用した Word 文書への図形挿入](/words/english/net/working-with-shapes/insert-shape/)
- [C# で矩形図形を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}