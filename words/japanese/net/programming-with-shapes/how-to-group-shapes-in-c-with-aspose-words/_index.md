---
category: general
date: 2026-08-23
description: Aspose.Words を使用して C# で図形をグループ化する方法を学びます。このガイドでは、長方形の図形の挿入方法や、複雑な文書向けに図形を追加する方法も解説しています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: ja
lastmod: 2026-08-23
og_description: Aspose.Words を使用した C# でのシェイプのグループ化方法。矩形シェイプの挿入、Word にシェイプを追加、複数のシェイプを効率的にグループ化する完全チュートリアルをご覧ください。
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: C#で形状をグループ化する方法 – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: C# と Aspose.Words でシェイプをグループ化する方法
url: /ja/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Aspose.Words を使用してシェイプをグループ化する方法

Word 文書をプログラムで **シェイプをグループ化する方法** が必要な場合、本チュートリアルでは Aspose.Words for .NET を使用した正確な手順を示します。レポートジェネレータ、テンプレートエンジン、またはダイアグラム作成ツールを構築する際に、グループの開始、矩形シェイプの挿入、コード内で Word レベルのコンテンツをシェイプに追加する方法を学べます。

また、**複数のシェイプをグループ化** する方法も紹介します。これは、オブジェクトのコレクションを単一のエンティティとして移動、回転、またはスタイル設定したい場合に必須です。以下の例は最新の Aspose.Words 24.x リリースで動作し、.NET 6 以降が必要です。

## 前提条件

- .NET 6 SDK（または Aspose.Words がサポートする任意の .NET バージョン）
- Visual Studio 2022 または VS Code
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- C# と Aspose.Words オブジェクトモデルの基本的な知識

> **プロのコツ:** テスト中に透かし制限を回避するため、Aspose の無料評価ライセンスを使用してください。

## Aspose.Words でシェイプをグループ化する方法

以下は、**グループ開始**、矩形の追加、グループの完了を実演する完全な実行可能プログラムです。コードは提供されたスニペットと同じ論理フローに従いますが、コンテキスト、エラーハンドリング、コメントが追加されています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 各ステップの重要性

| ステップ | 目的 | キーワードとの関係 |
|------|---------|--------------------------------|
| **新しい空白ドキュメントを作成** | シェイプ操作用のクリーンなキャンバスを提供します。 | 後の **add shapes word** の土台を設定します。 |
| **DocumentBuilder の初期化** | ビルダーはオブジェクト挿入の主要 API です。 | **how to start group** を実行する前に必要です。 |
| **StartGroupShape** | 論理的なコンテナを開始し、以降のシェイプがこのグループのメンバーになります。 | 直接 **how to start group** に回答します。 |
| **InsertShape**（矩形、楕円、テキスト） | グループ内に個々のシェイプを配置します。矩形呼び出しは **insert rectangle shape** を、テキストシェイプは **add shapes word** を満たします。 | **group multiple shapes** を実演します。 |
| **EndGroupShape** | グループを確定し、単位として移動やスタイル設定が可能になります。 | **how to group shapes** ワークフローを完了します。 |

## 矩形シェイプの挿入 – 詳細解説

`InsertShape` メソッドは `ShapeType` 列挙体、幅、高さを受け取ります。カスタムスタイリングで **insert rectangle shape** を行うには、以下の例を拡張できます。

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **なぜスタイルを設定するのか？** スタイルを設定すると、グループを後で再配置した際に矩形が目立ちます。また、シェイプのプロパティをグループが閉じられる前に設定できることを示しています。

## Word レベルのシェイプを追加する（add shapes word）

テキストをシェイプ内に直接埋め込みたい場合（一般に “WordArt” や “テキストボックス” と呼ばれます）は、`ShapeType.TextPlainText` を使用します。挿入後、`DocumentBuilder.Writeln` でテキストを書き込むか、シェイプの `TextBox` プロパティにアクセスしてテキストを設定できます。

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

これにより **add shapes word** キーワードが満たされ、テキストがグループと共に移動できることが示されます。

## 複数シェイプのグループ化 – 実用シナリオ

**group multiple shapes** を行うと、位置調整、回転、スケーリングを単一オブジェクトとして扱えます。たとえば、グループを閉じた後に全体を移動するには次のようにします。

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

または、グループ全体を回転させるには次のようにします。

```csharp
group.Rotation = 45; // degrees
```

これらの操作が可能なのは、シェイプが同じ親グループを共有しているためです。

## エッジケースの取り扱い

1. **入れ子グループ** – Aspose.Words はグループ内にさらにグループを作成できます。内部グループの `EndGroupShape` を呼ぶ前に、再度 `StartGroupShape` を呼び出してください。  
2. **空のグループ** – グループを開始したもののシェイプを挿入しなかった場合でも、`EndGroupShape` は空のコンテナを作成します。これは無害ですが、ファイルサイズが若干増加する可能性があります。  
3. **互換性** – 生成された DOCX は Word 2010 以降で動作します。古いバージョンはグループ化メタデータを無視することがあるため、対象の Word バージョンで必ずテストしてください。

## 参考用フルソースファイル

以下を `.NET` コンソールプロジェクトの `Program.cs` として保存してください。コードはそのままコンパイル・実行できます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 期待される出力

Microsoft Word で `GroupedShapes.docx` を開くと次が表示されます。

- ライトコーラルの矩形、楕円、テキストボックスが視覚的に一体化されています。  
- グループの任意の部分を選択すると、全体が選択され（単一のバウンディングボックスが表示され）ます。  
- グループ全体を移動または回転すると、3 つのシェイプが同時に動きます。

## よくある質問

**Q: 既に文書内に存在するシェイプをグループ化できますか？**  
A: はい。既存の `Shape` オブジェクトを取得し、`builder.StartGroupShape()` を呼び出してから `builder.InsertShape(existingShape)` で再挿入し、最後に `EndGroupShape()` を呼びます。

**Q: グループ化は基になる XML に影響しますか？**  
A: Aspose.Words は各シェイプの `<w:sp>` ノードを含む `<w:grpSp>` 要素を追加します。これは Office Open XML 仕様に完全に準拠しています。

**Q: 後でグループを解除したい場合は？**  
A: 直接的な “ungroup” API はありませんが、`group.GroupShape.Children` を列挙して子シェイプをドキュメント本文へコピーすることで実現できます。

## 次のステップ

**how to group shapes** が理解できたら、以下の関連トピックを探求してみてください。

- **グループ化シェイプへの高度な書式設定** – グラデーション塗り、影効果、線スタイルの設定方法を学びます。  
- **グループ化シェイプを画像としてエクスポート** – `Shape.GetShapeRenderer().Save(...)` を使用してグループをラスタライズします。  
- **動的ダイアグラムの作成** – データ駆動型の位置決めとグループ化を組み合わせてフローチャートを自動生成します。

これらは本稿で扱った基礎の上に構築され、よりリッチでインタラクティブな Word 文書の作成に役立ちます。

---

*Happy coding! If you found this guide useful, share it with teammates or star the repository that contains the sample project.*

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、完全に動作するコード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for .NET を使用した Word 文書へのシェイプ挿入](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words for .NET を使用した Word 文書でのグループシェイプ作成](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words で Word に矩形シェイプを作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}