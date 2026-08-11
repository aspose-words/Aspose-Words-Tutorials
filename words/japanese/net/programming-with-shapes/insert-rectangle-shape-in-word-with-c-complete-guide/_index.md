---
category: general
date: 2026-08-10
description: C# を使用して Word に長方形の図形を挿入します。図形の非表示方法、Word での図形の非表示、そして Aspose.Words で非表示の図形を作成する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: ja
lastmod: 2026-08-10
og_description: C# を使用して Word に長方形の図形を挿入する。このチュートリアルでは、図形の非表示方法、Word での図形の非表示、そして完全なコード例を用いた非表示図形の作成方法を解説します。
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: C#でWordに長方形の図形を挿入する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C#でWordに長方形の図形を挿入する – 完全ガイド
url: /ja/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Word に長方形シェイプを挿入する – 完全ガイド

C# を使用して Word 文書に **insert rectangle shape** を挿入する必要がある場合、本ガイドでは正確な手順を示します。また、**how to hide shape** を学び、最終ファイルに表示されないようにする方法を解説します。これは一般的な質問 **hide shape in Word** に対する回答であり、プログラムで **create hidden shape** を作成する方法も示します。

このチュートリアルでは、Aspose.Words SDK の設定からシェイプが非表示であることの確認まで、すべてをカバーしています。記事の最後までに、任意の .NET プロジェクトに組み込める再利用可能なコードスニペットが手に入ります。

## 前提条件

- .NET 6.0 以降がインストールされていること（コードは .NET Framework 4.6+ でも動作します）
- 有効な Aspose.Words for .NET ライセンスまたは一時評価キー
- Visual Studio 2022（または C# をサポートする任意の IDE）
- C# の構文と Word ファイルの Document Object Model (DOM) に関する基本的な知識

`Aspose.Words` 以外に追加の NuGet パッケージは必要ありません。

## 手順 1: 新しい空白ドキュメントと DocumentBuilder の作成

最初の操作は `Document` オブジェクトをインスタンス化することです。`DocumentBuilder` は、シェイプ、段落、テーブルなどのコンテンツを挿入するための便利な API を提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` は .docx ファイル全体を表し、`DocumentBuilder` は次の要素が配置される位置を追跡するカーソルを保持します。両方のオブジェクトを初期化することは、Word 自動化タスクの基礎となります。

## 手順 2: 長方形シェイプの挿入

ここで長方形を挿入します。`InsertShape` メソッドはシェイプの種類とサイズ（ポイント単位、1 point ≈ 1/72 inch）を指定する必要があります。**200 × 100 points** のサイズは、約 2.78 × 1.39 インチの長方形になります。

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Why this matters:** 取得した `Shape` オブジェクトは完全に構成可能で、色、枠線、テキスト、可視性などをドキュメント保存前にすべて変更できます。

## 手順 3: シェイプの非表示

長方形が表示または印刷されないようにするには、`Hidden` プロパティを `true` に設定します。このプロパティは Word の “Hidden” 属性に直接対応しており、表示モードと印刷モードの両方で Word が尊重します。

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Why this matters:** `Hidden` を設定することは、ドキュメント構造からシェイプを削除せずに **hide shape in Word** を実現する標準的な方法です。シェイプはコードから引き続きアクセス可能で、条件付き書式やデータ駆動の可視性切り替えなどの後続操作が可能になります。

## 手順 4: ドキュメントの保存

最後に、ドキュメントをディスクに保存します。任意のフォルダーを選択してください。例ではプレースホルダーのパスを使用しているので、実際のパスに置き換えてください。

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Why this matters:** 保存によりファイルが確定し、非表示フラグが基盤となる Open XML に書き込まれます。Microsoft Word でドキュメントを開くと、長方形は見えなくなり、**created hidden shape** に成功したことが確認できます。

## 手順 5: 非表示シェイプの確認

生成された `HiddenShape.docx` を Microsoft Word で開きます:

1. **File → Options → Display** に移動し、*“Show hidden text”* が **チェックされていない**ことを確認します。  
2. 長方形はどのページにも表示されないはずです。  
3. 再確認のために *“Show hidden text”* を有効にすると、長方形が薄い点線の輪郭で表示され、シェイプが存在するが非表示であることが証明されます。

長方形がまだ表示される場合は、`Hidden = true` を設定した後にファイルを保存したか、正しいファイルを開いているかを確認してください。

## 完全に実行可能なサンプル

以下に、コピーして貼り付け、直接実行できる完全なプログラムを示します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Expected output:** コンソールにファイルパスと簡単なリマインダーが表示されます。Word でファイルを開くと、非表示テキストが有効でない限り長方形は見えません。

## よくある質問とエッジケース

### アウトラインだけを非表示にし、塗りは表示したままにできますか？

はい。`Hidden = true` を設定する代わりに、`rectangle.LineFormat.Visible = false` と設定すれば、枠線を非表示にしつつ塗りの色は保持できます。これは **how to hide shape** のバリエーションで、視覚的外観の一部を保ちます。

### 古い Word バージョン（2003、2007）でも非表示フラグは機能しますか？

非表示属性は Word 2007 で導入された Open XML 仕様の一部です。古いバイナリ形式の `.doc` で保存されたドキュメントはこのフラグを保持しません。レガシーフォーマットをサポートするには、ドキュメントを `.docx` として保存し、必要に応じて Aspose.Words の `SaveFormat.Doc` を使用して後で変換してください。

### 複数のシェイプを一度に非表示にしたい場合は？

`Document.GetChildNodes(NodeType.Shape, true)` コレクションを反復処理し、条件に合致する各シェイプ（例: 特定の `ShapeType` やカスタム `AlternativeText` の値）に対して `Hidden = true` を設定します。

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### シェイプを非表示にした場合、パフォーマンスへの影響はありますか？

非表示フラグはごく小さな XML 属性を追加するだけで、描画速度には影響しません。ただし、非常に多数の非表示オブジェクトがあると、ファイルサイズがわずかに増加する可能性があります。不要なシェイプは削除して、ドキュメントを軽量に保ちましょう。

## ヒントとベストプラクティス

- `rectangle.Name = "MyHiddenRectangle"` を使用してシェイプに意味のある名前を付けます。これにより、後で DOM 内でシェイプを検索しやすくなります。
- `AlternativeText` にカスタムタグ（例: `"HiddenShape"`）を設定します。これにより、インデックスに依存せずシェイプを特定できます。
- コードを try‑catch ブロックでラップし、ライセンスエラーや I/O 例外を適切に処理します。
- 多数のファイルをループで処理する場合は、保存後に `document.Dispose();` で Document を破棄し、アンマネージドリソースを解放します。

## 結論

これで、C# を使用して Word 文書に **insert rectangle shape** を挿入する方法、**hide shape in Word** の方法、そしてドキュメント構造の一部として残りつつエンドユーザーには見えない **create hidden shape** の作成方法が分かりました。完全な実行可能サンプルは、ドキュメント作成から検証までの全工程を示しています。

次のステップとして、ユーザー入力に基づく **how to hide shape** の探索や、非表示シェイプとコンテンツコントロールを組み合わせた動的ドキュメント生成を検討できます。また、同様の手法を楕円形、矢印、カスタム図形など他のシェイプタイプにも適用可能です。

さまざまなサイズ、色、可視性設定を試してみてください。問題が発生した場合は、上記の手順を再確認するか、Aspose.Words のドキュメントで API の詳細を参照してください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を応用した密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}