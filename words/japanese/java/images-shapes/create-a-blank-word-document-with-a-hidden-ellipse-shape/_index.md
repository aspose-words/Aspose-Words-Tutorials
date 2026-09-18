---
category: general
date: 2026-09-18
description: Aspose.Words を使用して空白の Word 文書を作成し、楕円形の図形を非表示にします。Word で図形を非表示にする方法、楕円形を挿入する方法、そして非表示の図形をすばやく作成する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: ja
lastmod: 2026-09-18
og_description: 空白のWord文書を作成し、Wordで楕円形の図形を非表示にします。このガイドでは、楕円形の挿入方法、Wordで図形を非表示にする手順、そしてAspose.Wordsを使用して非表示の図形を作成する方法をステップバイステップで示します。
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: 隠し楕円形がある空白のWord文書を作成する
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 隠し楕円形を含む空白のWord文書を作成する
url: /ja/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 隠し楕円形がある空白のWord文書を作成する

空白の Word 文書に、レイアウトに表示したくない形状を含める必要がある場合、このガイドではその手順を正確に示します。Aspose.Words for .NET を使用すれば、プログラムから楕円形を挿入し、形状を非表示にして文書は視覚的に空のままにしつつ、形状データは保持できます。

このチュートリアルで学べること:

* **空白の Word 文書** オブジェクトの作成方法
* `DocumentBuilder` を使用した **楕円形の挿入** 方法
* **Word で形状を非表示** にしてページに影響させない方法
* 後で処理できる **隠し形状オブジェクト** の作成方法

この手順は .NET 6+ と最新の Aspose.Words バージョン（執筆時点 23.9）で動作します。追加の Office インストールは不要です。

## 前提条件

* Visual Studio 2022（または任意の C# IDE）
* .NET 6 SDK 以降
* Aspose.Words for .NET NuGet パッケージ  
  ```bash
  dotnet add package Aspose.Words
  ```
* C# と Word 文書の基本概念に関する知識

## ステップ 1: 空白の Word 文書を作成する

最初に行うべきことは `Document` オブジェクトをインスタンス化することです。このオブジェクトは空の `.docx` ファイルを表し、以降のすべての操作の基盤となります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

**空白の Word 文書** を作成すると、段落もセクションもないクリーンなキャンバスが得られます。これは、隠し形状だけが必要で他に何も不要な場合に最適な出発点です。

## ステップ 2: DocumentBuilder を初期化する

`DocumentBuilder` は `Document` にコンテンツを追加するための便利な API を提供します。文書内を移動するカーソルのように機能します。

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

ビルダーは自動的にデフォルトの最初のセクションと段落を作成するため、手動でセクションを追加する必要はありません。

## ステップ 3: 楕円形を挿入する

ここで `InsertShape` メソッドを使用して **楕円形を挿入** します。このメソッドは `ShapeType` 列挙体、幅、そして高さ（ポイント単位）を受け取ります。

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

なぜ楕円形かというと、楕円形はベクター形状であり、周囲のテキストフローに影響を与えずに非表示にできるからです。幅 100 pt、高さ 50 pt は任意の値で、後の処理要件に合わせて調整できます。

## ステップ 4: 形状を非表示にしてレイアウトに表示されないようにする

**Word で形状を非表示** にするには、`Shape` オブジェクトの `Hidden` プロパティを `true` に設定します。Microsoft Word で文書を開くと、形状は見えず、レイアウト上でもスペースを占有しません。

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

`Hidden` フラグは形状の XML（`<w:hidden/>`）に保存されます。Word はレンダリング時にこの属性を尊重するため、形状が存在していても文書は完全に空白に見えます。

### プロのコツ

後で形状を再び表示したい場合は、単に `ellipse.Hidden = false;` と設定して文書を保存すれば OK です。

## ステップ 5: 隠し形状付きの文書を保存する

最後に文書をディスクに永続化します。ファイルは任意の Word 処理ソフトで開ける通常の `.docx` になります。

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

保存されたファイル `HiddenEllipse.docx` は **空白の Word 文書** でありながら隠し楕円形を含んでいます。Microsoft Word で開くと空白ページが表示されますが、形状は Open XML 構造内に確実に存在しています。

## 完全な動作例

以下はコピーして貼り付け、実行できる完全な自己完結型プログラムです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**期待される出力**

* `C:\Temp` に `HiddenEllipse.docx` という名前のファイルが作成されます。
* Microsoft Word でファイルを開くと、完全に空白のページが表示されます。
* Open XML SDK や ZIP ビューアで文書を確認すると、ドキュメント パート内に `<w:shape>` 要素とその中の `<w:hidden/>` が存在することが分かります。

## よくある質問とエッジケース

### 形状がまだ表示される場合は？

* Aspose.Words 23.9 以降を使用していることを確認してください。古いバージョンでは一部の形状タイプで `Hidden` が無視されるバグがありました。
* 余計な書式設定（例: `WrapType`）が適用されていないか確認し、レイアウトスペースを占有しないようにしてください。

### 他の形状タイプも非表示にできる？

はい。`Hidden` プロパティは `ShapeType.Rectangle`、`ShapeType.Picture` などでも同様に機能します。`ShapeType.Ellipse` を目的のタイプに置き換えるだけです。

### 後で隠し形状を一覧表示するには？

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

このスニペットはすべての形状を走査し、非表示のものを出力します。**隠し形状の作成** ワークフローで、後から処理や再表示が必要な場合に便利です。

## 結論

これで **空白の Word 文書** を作成し、**楕円形を挿入**、そして **Word で形状を非表示** にして、読者には見えない **隠し形状** を保持する方法が分かりました。このテクニックは、メタデータ、ブックマーク、カスタム XML などを文書の視覚的外観を変えずに埋め込む際に便利です。

### 次のステップ

* 文書内容に基づいて **条件付きで形状を非表示** にする方法を探求する
* 最終版文書を生成するときに **形状を再表示** する方法を学ぶ
* 隠し形状と **カスタム文書プロパティ** を組み合わせて機械可読データを埋め込む

さまざまな形状タイプ、サイズ、非表示ロジックを試して、あなたの自動化シナリオに最適な実装を見つけてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、代替実装アプローチを探求したりするのに役立ちます。

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}