---
category: general
date: 2026-07-29
description: Aspose.Words を使用して四角形のワードを描画します。四角形シェイプの追加、直線シェイプの追加、そして単一のドキュメント内で複数のシェイプを管理する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: ja
lastmod: 2026-07-29
og_description: Aspose.Wordsで矩形を描く。ステップバイステップのガイドに従って、矩形シェイプを追加し、線シェイプを追加し、複数のシェイプを簡単に操作しましょう。
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Wordで長方形を描く – Wordで図形追加をマスター
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Wordで長方形を描く – AsposeでWordに図形を追加
url: /ja/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Word で図形を追加する完全ガイド

毎回 UI を開かずに **draw rectangle word** ドキュメントを作成したいと思ったことはありませんか？ あなたは一人ではありません。多くの開発者がリアルタイムで Word ファイルを生成する必要があり、最も簡単な方法はライブラリに重い処理を任せることです。このチュートリアルでは Aspose.Words for .NET を使用して **図形の追加方法** を正確に示します—具体的には矩形と直線です—そして、*draw rectangle word* というフレーズに焦点を当てて、迷わないようにします。

コード内にあるミニアートスタジオと考えてください。最後まで読むと **add rectangle shape**、**add line shape** を行い、さらにそれらを **multiple shapes word** グループに結合できるようになります。UI は不要、手作業の調整も不要、クリーンで再利用可能な C# です。

## 学習内容

- Aspose.Words を使用して新しい Word ドキュメントをセットアップする。  
- 複数のオブジェクトを保持できる **GroupShape** を作成する。  
- そのグループ内に **add rectangle shape** と **add line shape** を追加する。  
- グループ化された図形をドキュメント本文に挿入する。  
- ファイルを保存し、結果をすぐに確認する。  

基本的な C# に慣れていて Aspose.Words のコピーを持っていれば、すぐに始められます。コアライブラリ以外に追加の NuGet パッケージは必要ありません。

> **Pro tip:** Aspose.Words は .NET 6、.NET 7、そして .NET Framework 4.6+ に対応しています。プロジェクトに合ったランタイムを選択してください。

![draw rectangle word の例](https://example.com/placeholder-image.png "draw rectangle word – Word ファイル内のグループ化された図形")

## draw rectangle word – ドキュメントの設定

**draw rectangle word** を行う前に、クリーンなキャンバスが必要です。`Document` クラスがそのキャンバスで、`DocumentBuilder` がブラシに相当します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

上記の 2 行でメモリ上の新しい `.docx` が作成されます。まだディスクには書き込まれていないため、ファイルシステムを汚さずに実験できます。

## How to Add Shapes – GroupShape コンテナの作成

**multiple shapes word** を単一ユニットとして扱いたい（一緒に移動、回転）場合は、`GroupShape` でラップします。グループは他の図形を保持するフォルダと考えてください。

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

なぜグループが必要かというと、後で **add rectangle shape** と **add line shape** を追加し、まとめて移動したくなるからです。グループがなければ、各図形を個別に再配置する必要があります。

## add rectangle shape – グループ内に矩形を挿入する

コンテナができたので、**add rectangle shape** を行いましょう。矩形は `ShapeType` が `Rectangle` の `Shape` です。

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

`Left` と `Top` の値はページではなくグループの原点に対して相対的であることに注意してください。これにより図形を正確に配置しやすくなります。矩形はグループの左上隅付近に表示されます。

## add line shape – 同じグループに直線を追加する

直線も別の `Shape` ですが、`ShapeType` は `Line` です。矩形の下に配置します。

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

直線の高さが 0 のため、`Top` プロパティで垂直位置が決まります。`Width` が水平に伸びる長さを制御します。

## multiple shapes word – グループをドキュメント本文に挿入する

現在、**add rectangle shape** と **add line shape** を保持するグループがあります。最後のステップはそれをドキュメントに挿入することです。

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` は `DocumentBuilder` の現在位置にグループを正確に配置します。特定の段落に挿入したい場合は、まず `builder.MoveToParagraph(index)` でビルダーを移動させてください。

## Saving the Result – draw rectangle word の出力を確認する

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

生成されたファイルを Microsoft Word で開くと、矩形と直線を含む単一のグループが表示されます。グループをクリックしてドラッグしたり、サイズ変更したりすると、すべての図形が一緒に動きます。これが **multiple shapes word** の力です。

### 期待される出力

- `GroupShape.docx` という名前の `.docx` ファイル。  
- 1 ページに、左上隅付近に配置されたグループ化された矩形（120 × 80 pt）。  
- 矩形のすぐ下に配置された横線（長さ 150 pt）。  
- 両方の図形が単一オブジェクトとして選択可能。

グループをダブルクリックすると、Word で各図形を個別に編集できるようになります—微調整に最適です。

## よくある質問とエッジケース

**2 つ以上の図形が必要な場合は？**  
追加のオブジェクトごとに `group.AppendChild(yourShape)` を呼び続けます。グループは任意の数の図形を保持でき、複雑な図表に最適です。

**矩形の塗りつぶし色を変更できますか？**  
もちろんです。矩形を作成した後、`rectangle.FillColor = System.Drawing.Color.LightBlue;` と設定します。塗りつぶしをサポートするすべての図形で機能します。

**直線に `Height = 0` を設定しなければなりませんか？**  
はい、水平直線の場合は高さをゼロにする必要があります。垂直直線の場合は `Width = 0` とし、`Height` に正の値を設定します。

**.doc ファイル（Word 97‑2003）でも動作しますか？**  
Aspose.Words は古い `.doc` 形式にも保存できますが、最新の図形機能の一部は制限される可能性があります。完全な機能を利用するには `.docx` を使用してください。

**グループ全体を回転させるには？**  
挿入前に `group.Rotation = 45;`（度）を設定できます。回転はすべての子図形に適用されます。

## まとめ – Word でプログラム的に図形を追加する方法

- **draw rectangle word** は `Document` と `DocumentBuilder` の作成から始まります。  
- **multiple shapes word** を保持する **GroupShape** を構築します。  
- **add rectangle shape** と **add line shape** をグループに追加します。  
- `builder.InsertNode` でグループを本文に挿入します。  
- ファイルを保存し、開いてビジュアル結果を確認します。

以上が全体のワークフローで、シンプルで読みやすいコードリストにまとめられています。

## 次のステップと関連トピック

**図形の追加方法** が分かったので、以下を検討してみてください：

- 角丸矩形の **add rectangle shape**（`ShapeType.Rectangle` + `CornerRadius`）。  
- 異なる破線パターンで線をスタイリング（`line.LineFormat.DashStyle`）。  
- 図形と一緒に画像を埋め込んでリッチなレポートを作成。  
- **multiple shapes word** を使用してフローチャートやシンプルな UML 図を作成。  

これらのトピックはすべて、ここで示した基礎の上に自然に構築され、図形の作成、設定、必要に応じてグループ化するという同じパターンに従います。

---

コーディングを楽しんでください！ 問題に直面したり、面白いユースケースがあれば、下にコメントを残してください。皆さんのフィードバックが **draw rectangle word** そしてそれ以降の技術習得に役立ちます。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックをカバーしています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [C# を使用して Word に矩形を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words で Word に矩形を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words for .NET を使用して Word 文書に図形を挿入する](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}