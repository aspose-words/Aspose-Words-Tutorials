---
category: general
date: 2026-09-14
description: C# を使用して Word で図形を非表示にする方法を学びます — Word 文書作成コード、矩形図形の挿入、そしてプログラムで図形を非表示にする方法を含む。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: ja
lastmod: 2026-09-14
og_description: C# を使用して Word で図形を非表示にする方法—ステップバイステップのガイドで、Word 文書の作成コードと矩形図形の挿入方法も紹介します。
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: C#コードでWord文書の図形を非表示にする方法
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#コードでWord文書の図形を非表示にする方法
url: /ja/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# コードで Word 文書のシェイプを非表示にする方法

Word ファイルで **how to hide shape** を行う必要がある場合、このチュートリアルでは完全なソリューションを示します。Word 文書の作成方法、矩形シェイプの挿入、楕円の追加、そしてその楕円を非表示にしてファイルを開いたときに矩形だけが表示される方法を確認できます。

このガイドは必要なすべてを網羅しています—外部参照は不要で、コードと解説だけです。最後まで実践すれば、プログラムで生成する任意の Word 文書に隠しグラフィックを埋め込むことができるようになります。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET（無料トライアルまたはライセンス版）  
  NuGet でインストール: `dotnet add package Aspose.Words`
- C# と Visual Studio、またはお好みの IDE に関する基本的な知識

## 手順 1: プロジェクトのセットアップと名前空間のインポート

新しいコンソール アプリケーションを作成し、必要な `using` 文を追加します。これらのインポートにより、シェイプ操作に必要な `Document`、`DocumentBuilder`、および描画クラスにアクセスできます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Why this matters** – 正しい名前空間をインポートすることでコンパイル エラーを防ぎ、シェイプ作成と可視性制御のための API が利用可能になります。

## 手順 2: 新しい Word 文書とビルダーの作成

`Document` はファイルを表し、`DocumentBuilder` はコンテンツ追加用のフルエント API を提供します。ここが **how to hide shape** ロジックを適用する最初の場所です。シェイプを作成する前に文書コンテキストが必要です。

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explanation** – `Document` オブジェクトは空の状態で開始します。`DocumentBuilder` は最初の段落の先頭に配置され、シェイプやテキストの挿入が可能な状態です。

## 手順 3: 可視の矩形シェイプを挿入

矩形は文書を開いたときに表示され続けるシェイプです。サイズ、位置、書式はシェイプ オブジェクトを介して直接制御できます。

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Why this step** – 矩形の追加は **insert rectangle shape word** 要件を示すものです。`FillColor` と `LineColor` を設定することで、最終文書でシェイプが見やすくなります。

## 手順 4: 楕円シェイプを挿入して非表示にする

ここで隠したいシェイプを追加します。`Hidden` プロパティは Word に対して UI にシェイプを描画しないよう指示しますが、文書構造の一部として残ります。

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explanation** – `Hidden = true` の設定が **hide shape in word** の核心です。Word は通常の表示および印刷時にこのフラグを尊重しますが、必要に応じてプログラムからシェイプにアクセスできます。

## 手順 5: 文書の保存

最後に文書をディスクに書き出します。書き込み権限のあるフォルダーを選び、チュートリアルの目的が分かる明確な名前を付けてください。

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Result** – Microsoft Word で `ShapeVisibility.docx` を開くと、ライトブルーの矩形だけが表示されます。隠された楕円は表示されず、**how to hide shape** を Word ファイルで正しく実装できたことが確認できます。

## 完全な動作例

すべてのスニペットを組み合わせると、単一の実行可能プログラムが得られます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 期待される出力

- **Visual**: `ShapeVisibility.docx` を開くと、左余白付近にライトブルーの矩形が配置されているのが見えます。楕円は表示されません。  
- **Programmatic**: 隠された楕円は文書の XML（`<w:drawing>` 要素）内に `w:hidden` 属性が設定された状態で残っており、ZIP として展開し `document.xml` を確認することで検証できます。

## よくある質問とエッジケース

| Question | Answer |
|----------|--------|
| *Can I hide multiple shapes?* | はい。隠したい各シェイプに対して `Hidden = true` を設定してください。 |
| *Will hidden shapes print?* | デフォルトでは Word は隠しオブジェクトを印刷しません。印刷が必要な場合は印刷前に `Hidden` フラグをクリアしてください。 |
| *Is the hidden property supported in older Word versions?* | `Hidden` 属性は Office Open XML 標準の一部であり、Word 2007 以降で動作します。 |
| *What if I need to toggle visibility at runtime?* | `document.GetChildNodes(NodeType.Shape, true)` でシェイプを取得し、ロジックに応じて `Hidden` プロパティを切り替えてください。 |

## プロのコツ

- **Performance**: 多数の文書を生成する場合は、ファイルごとに新しいインスタンスを作成するのではなく、単一の `DocumentBuilder` インスタンスを再利用してください。  
- **Version control**: 生成した `.docx` ファイルはバージョン管理されたフォルダーに保存しましょう。隠しシェイプは下流処理用のメタデータマーカーとして活用できます。  
- **Testing**: Aspose.Words で DOCX を PDF に変換 (`document.Save("out.pdf")`) して、PDF でも楕円が非表示になることを自動化テストで確認すると、隠しフラグがフォーマット変換に伝播することが検証できます。

## 結論

これで C# を使用して Word 文書内の **how to hide shape** 方法が分かりました。チュートリアルでは文書の作成、**insert rectangle shape word**、楕円の追加、そして `Hidden` フラグの適用を通じて **hide shape in word** 動作を実現しました。完全な実行可能コードを使えば、任意の自動レポートやテンプレート ワークフローに隠しグラフィックを組み込むことができます。

### 次のステップ

- 回転、影、テキスト折り返しなど、他のシェイプ プロパティを調査する。  
- 隠しシェイプとカスタム文書プロパティを組み合わせて、機械可読データを埋め込む。  
- **create word document code** パターンを活用し、表、チャート、コンテンツ コントロールの自動化ツールキットを拡張する。

さまざまなシェイプ タイプや可視性設定を試してみてください—次の Word 自動化プロジェクトは数行のコードで実現できます！

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [C# で Word に矩形シェイプを作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [影付き矩形シェイプで空白の Word 文書を作成する – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words シェイプ シャドウ チュートリアル – C# で Word シェイプに影を追加](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}