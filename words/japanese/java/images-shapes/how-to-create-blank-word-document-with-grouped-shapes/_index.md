---
category: general
date: 2026-09-08
description: C# を使用して空白の Word 文書を作成し、長方形の図形を挿入し、複数の図形をグループ化する方法を学びましょう。このステップバイステップガイドに従ってください。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: ja
lastmod: 2026-09-08
og_description: 空白のWord文書を作成し、長方形の図形を挿入し、C#で複数の図形をグループ化します。このチュートリアルでは、全工程を順を追って解説します。
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: C#でグループ化された図形を含む空白のWord文書を作成する
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: グループ化された図形を含む空白のWord文書の作成方法
url: /ja/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白の Word ドキュメントをグループ化されたシェイプで作成する方法

カスタムグラフィックを含む **blank Word document** を作成する必要がある場合、このガイドではその手順を正確に示します。Aspose.Words for .NET を使用して **insert rectangle shape**、**group multiple shapes**、および **add shapes to group** を学びます。

空白のドキュメントはクリーンなキャンバスを提供し、シェイプをグループ化するとそれらを単一のユニットとして移動、サイズ変更、回転させることができます。このチュートリアルでは、ドキュメントの初期化から最終ファイルの保存までのすべての手順をカバーしているので、コードを自分のプロジェクトにコピーしてすぐに結果を確認できます。

## 必要なもの

開始する前に、以下が揃っていることを確認してください。

* .NET 6.0 以降（コードは .NET Framework 4.6+ でも動作します）
* 有効な Aspose.Words for .NET ライセンス（無料評価版でもテストは可能です）
* Visual Studio 2022 や Visual Studio Code などの IDE
* C# 構文に関する基本的な知識

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## 空白の Word ドキュメントの作成方法

最初のステップは `Document` オブジェクトをインスタンス化することです。このオブジェクトは、`DocumentBuilder` で編集できる空の `.docx` ファイルを表します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` コンストラクタはメモリ上に **blank Word document** を作成します。`DocumentBuilder` はテキスト、画像、描画オブジェクトを挿入するためのフルエント API を提供します。

## ドキュメントに矩形シェイプを挿入する

次に矩形シェイプを追加します。この矩形は後で作成するグループの最初の子要素になります。

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

`InsertShape` に `ShapeType.Rectangle` を指定して呼び出すと、現在のカーソル位置に **矩形シェイプが挿入** されます。幅と高さはポイント単位で表されます（1 pt ≈ 1/72 in）。

## 複数のシェイプをグループ化する

`GroupShape` はコンテナのように機能します。グループ内のすべての子シェイプは一緒に移動・変形します。まずグループを作成し、先ほど作った矩形を追加します。

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

`InsertGroupShape` メソッドはビルダーのカーソル位置に空のグループを配置します。矩形を追加することで **複数のシェイプをグループ化** し、矩形はグループの内部ノードコレクションの一部になります。

## グループにシェイプを追加してファイルを保存する

次に、2 番目のシェイプ（楕円）を追加し、複数のオブジェクトが同じコンテナを共有できることを示します。その後、ドキュメントを保存します。

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`InsertShape` 呼び出しは、返された `Shape` を `GroupShape` に追加することで **シェイプをグループに追加** します。`Document` を保存すると、Microsoft Word、LibreOffice、または任意の互換ビューアで開ける `.docx` ファイルが書き出されます。

### 期待される結果

*GroupShapeDemo.docx* を開くと、空白ページにライトブルーの矩形とピンクの楕円を含むグループ化オブジェクトが表示されます。グループを選択すると両方のシェイプが一緒に移動でき、**複数のシェイプをグループ化** が正しく機能したことが確認できます。

## GroupShape を使用する理由

* **Atomic transformations** – グループのスケーリング、回転、移動はすべての子要素に均等に適用されます。
* **Logical organization** – 関連するグラフィックをまとめて保持でき、ドキュメント構造の保守が容易になります。
* **Performance** – 多数の独立シェイプを扱うよりも、単一のコンテナをレンダリングする方が高速になることが多いです。

後で単一の子シェイプを変更する必要がある場合は、`group.ChildNodes` からインデックスまたは `Name` プロパティで取得できます。

## よくあるバリエーションとエッジケース

| シナリオ                                 | コードの適応方法                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **異なるシェイプタイプ**                | `ShapeType.Rectangle` または `ShapeType.Ellipse` を他の任意の `ShapeType` に置き換えます |
| **シェイプ内にテキストを追加**           | シェイプを挿入した後で `Shape.TextPath.Text = "Hello"` を使用します                    |
| **回転角度の設定**                       | `group.Rotation = 45;` （度）                                                 |
| **DOCX の代わりに PDF として保存**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **グループに枠線を適用**                 | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## プロのコツ

* **シェイプに名前を付ける** – `rectangle.Name = "MyRect";` は後で検索しやすくします。
* **相対位置指定を使用する** – グループをページ余白に固定したい場合は `group.RelativeHorizontalPosition` を `RelativeHorizontalPosition.Page` に設定します。
* **リソースを解放する** – 大規模アプリケーションで作業する際は、`Document` を `using` ブロックでラップしてアンマネージド メモリを速やかに解放します。

## クイックコピー＆ペースト用の完全ソースコード

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

コードを新しいコンソール プロジェクトにコピーし、`Aspose.Words` NuGet パッケージを復元して実行してください。出力ファイルはプロジェクトの `bin/Debug/net6.0`（または同等）フォルダーに作成されます。

## 次のステップ

これで **blank Word document** を **create** し、**矩形シェイプを挿入**、**複数のシェイプをグループ化** できるようになったので、以下を検討してみてください。

* グループ内に **テキスト ボックス** を追加してラベル付きダイアグラムを作成する。
* `doc.Save("image.png", SaveFormat.Png)` を使用してグループ化されたグラフィックを画像としてエクスポートする。
* グループとテーブルを組み合わせて、リッチなレポートを作成する。

さまざまなシェイプ プロパティ、グループ階層、エクスポート形式を試して、Aspose.Words の描画機能を最大限に活用してください。

--- 

*Remember*: グループ化されたシェイプは、Word ドキュメントを整理し、コードの保守性を高める強力な手段です。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [C# を使用して Word に矩形シェイプを作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words for .NET を使用した Word ドキュメントへのシェイプ挿入](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words for .NET を使用した Word ドキュメントでのグループシェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}