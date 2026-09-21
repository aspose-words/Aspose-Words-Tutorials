---
category: general
date: 2026-09-21
description: Aspose.Words for C# を使用して Word で図形をグループ化する方法を学びましょう。このステップバイステップガイドでは、グループ化された図形の作成、配置、保存について解説します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: ja
lastmod: 2026-09-21
og_description: C# 用 Aspose.Words を使用して Word で図形をグループ化します。この簡潔なチュートリアルに従い、図形の作成、配置、そしてプログラムでグループ化された図形を保存してください。
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Aspose.WordsでWordの図形をグループ化する – 完全なC#ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# 用 Aspose.Words を使用して Word で図形をグループ化する方法
url: /ja/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for C# を使用した Word での図形のグループ化方法

Word で **図形をプログラムでグループ化** したい場合、Aspose.Words を使えば簡単に実現できます。このチュートリアルでは、2 つの矩形図形を作成し、横に並べて `GroupShape` にまとめ、DOCX ファイルとして保存する手順を紹介します。

完全に実行可能なサンプル、各ステップの重要性の解説、重なり合う図形や動的サイズ調整といった一般的なエッジケースへの対処法も掲載しています。このガイドを終える頃には、任意の Word 自動化プロジェクトに図形のグループ化を組み込めるようになります。

## 前提条件

開始する前に、以下を確認してください。

* .NET 6.0（またはそれ以降） – Aspose.Words は .NET Standard 2.0+、.NET Core、.NET Framework をサポートしています。
* 有効な Aspose.Words for .NET ライセンス（または一時評価キー） – ライセンスなしでも動作しますが、透かしが付加されます。
* Visual Studio 2022（または任意の C# IDE） – サンプルのコンパイルと実行に使用します。

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## Aspose.Words を使用した Word での図形のグループ化手順

解決策の中心となるのは、個々の図形を格納するコンテナとして機能する **`GroupShape`** オブジェクトです。以下の手順で処理を分解して説明します。

### 手順 1: 空のドキュメントと `DocumentBuilder` を作成

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*このステップの目的*  
`Document` は DOCX 全体を表し、`DocumentBuilder` はフルエントなメソッド（例: `InsertShape`）を提供し、現在のカーソル位置に自動的に新しい要素を配置します。

### 手順 2: 最初の矩形図形を挿入

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

`InsertShape` 呼び出しにより図形がドキュメントに追加され、返された `Shape` オブジェクトで色や枠線などをさらに設定できます。サイズはポイント単位（1 pt ≈ 1/72 in）で指定します。

### 手順 3: 2 番目の矩形を挿入し、オフセットを設定

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

`Left` プロパティでページ余白に対する水平位置を指定します。オフセットは最初の図形の幅（100 pt）より大きくし、重なりを防ぐために 120 pt としています。

### 手順 4: 両方の矩形を収めるだけの大きさの `GroupShape` を作成

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` は所有する `Document` とコンテナのサイズを受け取ります。コンテナ幅は最も右側にある図形の右端を超えている必要があり、そうしないと 2 番目の図形が切り取られてしまいます。

### 手順 5: 個々の図形をグループに追加

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

`AppendChild` により図形がグループの内部コレクションに移動します。この呼び出し以降、図形はドキュメントツリー上の独立オブジェクトではなく、グループに属するようになります。

### 手順 6: グループ化した図形をドキュメントに再挿入

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` はカーソル位置に `GroupShape` 全体を配置します。特定の段落にグループを入れたい場合は、事前に `DocumentBuilder` をその段落へ移動させてください。

### 手順 7: ドキュメントを保存

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

生成されたファイルには 2 つの矩形が単一オブジェクトとして扱われ、Microsoft Word で一緒に移動・サイズ変更・削除が可能です。

## 完全なソースコード

すべての手順を統合した、自己完結型プログラムは以下の通りです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**期待される出力:** Microsoft Word で *GroupedShapes.docx* を開くと、横に並んだ 2 つの矩形が単一の選択可能オブジェクトとして表示されます。グループ全体をドラッグすると、両方の矩形が同時に移動します。

## よくあるバリエーションとエッジケース

| 状況 | 推奨の調整 |
|-----------|------------------------|
| **2 つ以上の図形** | 追加の `Shape` オブジェクトを作成し、適切に配置したうえで同じ `GroupShape` にすべて `AppendChild` してください。 |
| **動的サイズ** | 子図形の最大 `Right` と `Bottom` 値からグループの幅・高さを計算します。 |
| **異なる図形タイプ** | `ShapeType.Ellipse`、`ShapeType.Triangle` なども同様に挿入可能です。グループコンテナはタイプを意識しません。 |
| **回転した図形** | `shape.Rotation = 45;` を `AppendChild` 前に設定します。回転情報はグループ内で保持されます。 |
| **PDF として保存** | `doc.Save("GroupedShapes.pdf");` を呼び出すと、PDF でもグループが保持されます。 |

**プロのコツ:** グループ化後でも `group.GetChildNodes(NodeType.Shape, true)` で個々の図形にアクセスできるため、グループを壊さずに特定の矩形の塗りつぶし色だけを変更するといった操作が可能です。

## プログラムでグループ化を検証する方法

ユニットテスト等で図形が正しくグループ化されているか確認したい場合は、ドキュメントのノード階層を調べます。

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

出力は次のようになるはずです。

```
Number of groups: 1
Children in first group: 2
```

これにより **Word の図形グループ化** が期待通りに作成されたことが確認できます。

## 結論

これで Aspose.Words for C# を使った **Word での図形のグループ化** 方法が理解できました。個々の図形を作成・配置し、`GroupShape` でラップし、再度ドキュメントに挿入するという流れです。上記のサンプルを基に、図形の数や種類を増やしたり、テキストボックスや画像と組み合わせたりと、さまざまなシナリオに応用できます。

次は **Aspose.Words の図形グループ化**、**C# の Word 図形操作**、**DocumentBuilder の InsertShape** など、より高度なドキュメント自動化シナリオを探求してみてください。動的サイズ設定や条件付きグループ化、PDF へのエクスポートなどを試し、Aspose.Words のパワーを最大限に活用しましょう。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの検討に役立ちます。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}