---
category: general
date: 2026-09-21
description: Aspose.Words を使用して空白の Word 文書を作成し、図形のサイズ、位置、色を設定し、1 回の手順で docx ファイルを保存する。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: ja
lastmod: 2026-09-21
og_description: 空白のWord文書を作成し、図形のサイズ・位置・色を設定し、数分でAspose.Wordsを使用してdocxファイルを保存します。
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: 空白のWord文書を作成し、色付きの図形を追加する – Aspose.Wordsガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Aspose.Words で空白の Word 文書を作成し、色付きの図形を追加する
url: /ja/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して空白の Word ドキュメントを作成し、カラーシェイプを追加する

プログラムで **空白の Word ドキュメントを作成** したい場合は、このガイドで Aspose.Words の使い方をご紹介します。**シェイプのサイズ設定**、**シェイプの位置設定**、**シェイプの色設定**、そして最終的に **docx ファイルを保存** する方法を IDE を離れずに学べます。

C# で Word ファイルを扱う際は、低レベルの OpenXML 呼び出しを駆使する必要がありますが、Aspose.Words がその複雑さを抽象化します。このチュートリアルの最後までに、2 つのカラー長方形からなるグループシェイプを含む完全に機能する `.docx` が作成できるようになります。レポート、証明書、カスタムテンプレートなどに最適です。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET 23.9 以上（NuGet でインストール: `Install-Package Aspose.Words`）
- C# と Visual Studio（または任意の C# エディタ）の基本的な知識

既存の Word ファイルは不要です。チュートリアルは **空白の Word ドキュメントを最初から作成** するところから始まります。

## Aspose.Words で空白の Word ドキュメントを作成する

最初のステップは `Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の空の Word ファイルを表します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` は最初から空で、**空白の Word ドキュメントを作成** したいときにまさに必要な状態です。`builder` は後で現在のカーソル位置にシェイプグループを挿入するために使用します。

## シェイプサイズを設定し GroupShape を作成する

`GroupShape` は複数の個別シェイプを保持できるコンテナとして機能します。まず、コンテナ全体の寸法を定義します。

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

ここで **シェイプサイズ** をグループ自体に対して設定しています（300 × 200）。子シェイプでも同じプロパティ名（`Width`, `Height`）を使用できるため、各要素を細かく制御できます。

## 最初の長方形を追加しシェイプの色を設定する

次に、グループに長方形を追加し、背景色を設定します。

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

`FillColor` プロパティは **シェイプの色を設定** します。`System.Drawing.Color` を使用すれば、事前定義された色やカスタム ARGB 値を自由に選択できます。

## 2 番目の長方形を追加し、サイズ・位置・色を設定する

2 番目の長方形では、**シェイプの位置を設定** する方法と、色を変更する方法を示します。

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

グループの幅が 300 ポイントなので、2 つの 120 ポイント長方形は 30 ポイントの隙間で快適に収まります。レイアウトを変えたい場合は `Left` と `Top` を調整してください。

## GroupShape をドキュメントに挿入する

グループの設定が完了したら、現在のカーソル位置に配置します。

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` はシェイプをドキュメントの本文に直接書き込み、先に **シェイプ位置を設定** した通りの位置を保持します。

## docx ファイルを保存する

最後のステップはドキュメントをディスクに永続化することです。これが **docx ファイルを保存** する操作です。

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

プログラムを実行した後、Microsoft Word で `GroupShape.docx` を開いてください。空白ページに、横に並んだ 2 つのカラー長方形を含むグループシェイプが表示されます。

### 期待される出力

- 1 ページの `.docx` ファイル
- ページ上に左・上余白からそれぞれ 100 pts の位置に配置されたグループシェイプ
- グループ内では、左側にライトブルーの長方形、右側にライトコーラルの長方形がそれぞれ 120 × 80 pts のサイズで配置されている

## 完全な実行可能サンプル

以下はコンソールアプリケーションにコピーペーストできる完全プログラムです。追加ファイルは不要です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

このプログラムを実行すると、前述のドキュメントが正確に作成され、**空白の Word ドキュメントを作成**、**シェイプサイズを設定**、**シェイプ位置を設定**、**シェイプ色を設定**、**docx ファイルを保存** の 4 つの目的がすべて達成されます。

## よくあるバリエーションとエッジケース

| シナリオ | 変更点 | 重要な理由 |
|----------|--------|------------|
| **異なるシェイプタイプ** | `ShapeType.Rectangle` を `ShapeType.Ellipse`、`ShapeType.Triangle` などに置き換える | 外部画像を使用せずに、より複雑なグラフィックを構築できる |
| **動的寸法** | `Width` と `Height` をユーザー入力や設定ファイルから計算する | 複数のドキュメントテンプレートで再利用可能になる |
| **PDF として保存** | `document.Save("output.pdf", SaveFormat.Pdf);` を呼び出す | 受取側が編集不可形式を必要とする場合、PDF が安全な選択肢になる |
| **シェイプ内にテキストを追加** | `TextBox` シェイプを作成し `TextBox.Text` を設定する | ラベル付きバッジやコールアウトの作成に便利 |
| **1 ページに複数のグループ** | 手順 2‑5 を異なる `Left`/`Top` 値で繰り返す | ダッシュボードやマルチセクションレイアウトを構築できる |

### プロのコツ

シェイプを正確に揃える必要がある場合は、グループを挿入する前に `ShapeBase.WrapType = WrapType.Inline` プロパティを設定してください。これにより、グループが段落として扱われ、予期しないテキスト回り込みを防げます。

## 結論

これで Aspose.Words を使って **空白の Word ドキュメントを作成**、**シェイプサイズを設定**、**シェイプ位置を設定**、**シェイプ色を設定**、そして **docx ファイルを保存** する方法が分かりました。完全なサンプルは、任意の Word 自動化プロジェクトにグループ化されたグラフィックを追加するためのクリーンで再利用可能なパターンを示しています。

ここからさらに進められること：

- 同じ `GroupShape` にさらにシェイプや画像を追加する（**シェイプサイズ**、**シェイプ色** のバリエーション）
- `ShapeBase.Rotation` を使用して長方形を回転させ、装飾効果を加える
- 同一ドキュメントを PDF や HTML としてエクスポートし、配布範囲を拡大する（**docx ファイルを保存** の代替手段）

さまざまな色、サイズ、レイアウトロジックを試して、特定のレポートやテンプレート要件に合わせてください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}