---
category: general
date: 2026-08-07
description: Aspose.Words を使用して C# で長方形の図形を挿入し、図形の非表示方法、塗りつぶし色の設定方法、そして長方形の図形を Word
  文書に効率的に追加する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: ja
lastmod: 2026-08-07
og_description: C#でWord文書に長方形の図形を挿入します。図形の非表示、塗りつぶし色の設定、Aspose.Wordsを使用した長方形図形の追加方法を学びましょう。
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: C#で長方形シェイプを挿入 – 完全な Aspose.Words チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: C# と Aspose.Words で長方形シェイプを挿入する – ステップバイステップガイド
url: /ja/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# と Aspose.Words で矩形シェイプを挿入する – ステップバイステップガイド

C# から Word ドキュメントに **矩形シェイプを挿入** する必要がある場合、このガイドで具体的な手順を示します。塗りつぶしの色の設定方法、シェイプを非表示にして最終レイアウトに表示させない方法、そしてファイルの保存方法を、数行のコードだけで実現できます。

以下のセクションでは、必要な前提条件、完全なコード一覧、各ステップの解説、シェイプを再び表示させる方法や別の色を使用するなどの一般的なバリエーションに関するヒントなど、知っておくべきことをすべて網羅します。最後まで読むと、任意の .docx ファイルにプログラムで **矩形シェイプを追加** できるようになります。

## 前提条件

* **Aspose.Words for .NET**（バージョン 23.10 以降）。NuGet でインストールできます：

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK 以降がマシンにインストールされていること。
* C# と Visual Studio（またはお好みの IDE）に関する基本的な理解。

追加のライブラリは不要です。シェイプ関連の API はコアの Aspose.Words パッケージに含まれています。

## Aspose.Words を使用した矩形シェイプの挿入

このソリューションの核心は、空白のドキュメントを作成し、矩形を挿入し、色を付け、非表示にしてからファイルを保存する、短く自己完結したプログラムです。以下に、各行の *理由* を説明するインラインコメント付きの完全なソースコードを示します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### 各ステップの内容

| Step | Reason |
|------|--------|
| **新しいドキュメントを作成** | クリーンなキャンバスを提供します。`new Document(path)` にファイルパスを渡すことで、既存の .docx をロードすることも可能です。 |
| **DocumentBuilder を初期化** | `DocumentBuilder` は高レベルのヘルパーで、低レベルのノードツリーを操作せずにテキスト、テーブル、シェイプを挿入できます。 |
| **矩形シェイプを挿入** | `InsertShape` メソッドは `Shape` オブジェクトを返し、サイズ、位置、枠線などをさらにカスタマイズできます。 |
| **塗りつぶし色を設定** | `FillColor` プロパティは内部の色を制御します。任意の `Color` 値（`Color.Red`、`Color.FromArgb(255, 0, 255, 0)` など）を使用できます。 |
| **シェイプを非表示にする** | `Hidden = true` を設定すると、Word はレイアウト時にシェイプを無視しますが、ドキュメントの XML には残ります。これは不可視オブジェクトを保存する標準的な方法です。 |
| **ドキュメントを保存** | 変更を .docx ファイルに永続化します。保存されたファイルには非表示の矩形シェイプが含まれます。 |

## シェイプの塗りつぶし色の設定方法

塗りつぶし色の変更は、`FillColor` プロパティに `System.Drawing.Color` を代入するだけで簡単です。カスタムの色が必要な場合は `Color.FromArgb` を使用します：

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*重要な理由*: 塗りつぶし色はシェイプの XML（`<w:fill>` 属性）に保存されます。シェイプが非表示でも色は保持されており、下流の処理（例: 色コードに基づくメタデータ抽出）に役立ちます。

## 最終ドキュメントでシェイプを非表示にする方法

`Hidden` フラグは `Shape` クラスのブールプロパティです。`true` に設定すると、Word のレイアウトエンジンはシェイプを無視します。

```csharp
rectangleShape.Hidden = true;
```

**よくある落とし穴**

* **Hidden と Visible** – 後でシェイプを表示させる必要がある場合は、単に `Hidden = false` に設定します。
* **互換性** – Word の古いバージョン（2007 年以前）は非表示の描画オブジェクトを異なる方法で扱うことがあります。Aspose.Words は適切な OOXML 要素にフラグを保存することで互換性を保ちます。

## プログラムからシェイプを挿入する方法

例では矩形を使用していますが、同じ `InsertShape` メソッドは他の多くのシェイプ（楕円、三角形、線など）でも使用できます。最初の引数は `ShapeType` 列挙型の値です：

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**ヒント**: ページ上の特定の位置にシェイプを配置したい場合は、`InsertShape` を呼び出す前に `builder.MoveTo` で挿入位置を設定します。

## 既存のドキュメントに矩形シェイプを追加する

多くの場合、最初から作成するのではなくテンプレートを拡張します。ステップ 1 を次のように置き換えてください。

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

以降のステップはすべて同じで、矩形はビルダーのカーソルが位置する場所（デフォルトでは通常ドキュメントの末尾）に追加されます。

## エッジケースとバリエーションの取り扱い

### 1. シェイプを再び表示させる

ワークフローの後半で非表示の矩形を表示させる必要がある場合、フラグを切り替えることができます。

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. 境界線（ストローク）を追加

非表示のシェイプでも、表示させる際に可視の境界線を持たせることができます。`LineColor` と `LineWidth` プロパティを設定してください。

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. 矩形を絶対位置に配置

正確なレイアウト制御のために、シェイプの `WrapType` を `WrapType.Inline`（デフォルト）または `WrapType.TopBottom` に切り替え、`Left`/`Top` プロパティで位置を調整します。

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. 別の測定単位を使用

Aspose.Words はポイント単位で動作します（1 pt = 1/72 インチ）。センチメートル単位が好みの場合は、事前に変換してください。

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## 完全な実行可能サンプル

以下はコピー＆ペーストして実行できる *完全* なプログラムです。必要な `using` ディレクティブがすべて含まれており、環境に合わせて調整すべき絶対パスが使用されています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**期待される結果**: ファイル `HiddenRectangleShape.docx` を Microsoft Word で開くと *シェイプは表示されません* が、ドキュメント XML には非表示の矩形が存在します。`.docx` を zip アーカイブとして展開し、`word/document.xml` 内に `w:fill="yellow"` および `w:hidden="true"` 属性を持つ `<w:shape>` 要素があるか確認すると存在が分かります。

## 結論

これで C# と Aspose.Words を使用して Word ドキュメントに **矩形シェイプを挿入** する方法、**塗りつぶし色を設定** する方法、そして最終レイアウトで見えないように **シェイプを非表示** にする方法が分かりました。同じパターンは他のシェイプタイプ、カスタムカラー、既存のテンプレートでも機能します。境界線や絶対位置、異なる測定単位を試して、要件に合わせてシェイプを調整してください。

### 次のステップ

* **シェイプの挿入** をテーブルやヘッダー/フッター内で行い、透かしとして利用する方法を調査する。
* **矩形シェイプの追加** とコンテンツコントロールを組み合わせて、動的なプレースホルダーを作成する。
* Aspose.Words の **シェイプ操作** API を確認し、回転、グラデーション塗りつぶし、SVG インポートなどの高度な機能を学ぶ。

コードを自分のプロジェクトに合わせて自由に適用し、コメントで次に解決したシェイプ関連の課題を教えてください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説付きの完全なコード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}