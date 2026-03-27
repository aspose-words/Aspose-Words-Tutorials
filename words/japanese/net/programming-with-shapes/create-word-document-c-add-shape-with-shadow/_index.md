---
category: general
date: 2026-03-27
description: C#でWord文書を作成し、図形の追加、図形への影の適用、影の距離設定方法を学びます。Aspose.Wordsのステップバイステップガイド。
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: ja
og_description: C#で矩形シェイプとカスタムシャドウを使用したWord文書を作成します。シャドウの距離とスタイルを設定する完全なチュートリアルをご覧ください。
og_title: C#でWord文書を作成 – 影付きの図形を追加
tags:
- Aspose.Words
- C#
- Document Automation
title: C#でWord文書を作成 – 影付きシェイプを追加
url: /ja/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ドキュメント C# の作成 – 影付きシェイプの追加

きれいにスタイルされた長方形を含む **create word document c#** が必要になったことはありませんか？レポートテンプレートを作成していて、レイアウトを引き立てるためにさりげないドロップシャドウを加えたいかもしれません。このチュートリアルでは、シェイプの追加、シェイプへの影の適用、そして Aspose.Words を使用して影の距離を微調整する方法を順を追って説明します。

空のドキュメントから始め、長方形を配置し、プリセットの影を設定し、最後にファイルを保存します。最後までに、Word で開いてすぐに効果を確認できる、すぐに使える .docx が手に入ります。外部ツールは不要で、純粋な C# コードだけです。

## 前提条件

- .NET 6（または任意の最新 .NET Framework）がインストールされていること。
- Visual Studio 2022 または C# 拡張機能がインストールされた VS Code。
- Aspose.Words for .NET の NuGet パッケージ（`Aspose.Words` バージョン 23.12 以降）。  
  Package Manager Console から追加できます：

  ```powershell
  Install-Package Aspose.Words
  ```

以上です – 追加の DLL や COM インタープロは不要です。

## ステップ 1: 新しい Document と Builder の初期化 – *create word document c#* の基本

まず、Word ファイルを表す `Document` オブジェクトと、編集用の `DocumentBuilder` が必要です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **このステップが重要な理由:** `Document` クラスはすべての Word パーツ（ページ、スタイル、画像）を格納するコンテナです。Builder は低レベルのノード操作を抽象化したハイレベル API で、XML を直接扱うことなく **create word document c#** を簡単に行えます。

## ステップ 2: 長方形シェイプの挿入 – *how to create rectangle*  

ページ上に長方形を配置します。サイズはポイントで表されます（1 pt ≈ 1/72 インチ）。

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **プロのコツ:** 別のシェイプが必要な場合は、`ShapeType.Rectangle` を `ShapeType.Ellipse`、`ShapeType.Triangle` などに置き換えるだけです。同じコードは任意のタイプの **how to add shape** にも機能します。

## ステップ 3: プリセット影の適用と微調整 – *apply shadow to shape*  

Aspose.Words にはいくつかのプリセット影フォーマットが用意されています。ここでは `Preset1` を使用し、距離、ぼかし、透明度、色をカスタマイズします。

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **なぜ影をカスタマイズするのか？** `Distance` プロパティは影が長方形からどれだけ離れるかを制御します – 3D レンダリングでの「リフト」のようなイメージです。`BlurRadius` を変更するとエッジが柔らかくなり、`Transparency` でさりげなくプロフェッショナルな外観を作れます。これにより **set shadow distance** の要件を満たし、**apply shadow to shape** を柔軟に行う方法が示されます。

## ステップ 4: ドキュメントの保存 – *create word document c#* 完了

最後に、ドキュメントをディスクに書き込みます。書き込み権限のあるフォルダーにパスを調整してください。

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Microsoft Word で生成されたファイルを開くと、淡い青色の長方形に 5 pt のオフセットで柔らかいグレーの影が付いているのが確認できます。これが、スタイル付きシェイプで **create word document c#** に成功したことの視覚的証拠です。

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# example showing rectangle with shadow"}

## オプションのバリエーションとエッジケース

| シナリオ | 変更点 | 重要な理由 |
|----------|----------------|----------------|
| **異なる影スタイル** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | 余分なコードなしで、よりドラマチックな外観を提供します。 |
| **プリセットなし – カスタム影** | `Format` を省略し、`OffsetX`、`OffsetY` を手動で設定します。 | 方向と深さを完全にコントロールできます。 |
| **複数のシェイプ** | 保存前に `builder.InsertShape` を再度呼び出します。 | アイコンやロゴなどを含む複雑なテンプレートに便利です。 |
| **古い Aspose バージョンとの互換性** | `ShadowEffect` クラスを使用します（v20.x で利用可能）。 | レガシープロジェクトでもコードが動作することを保証します。 |
| **PDF として保存** | `document.Save("ShadowShape.pdf");` | PDF 出力でも同じ影のレンダリングが表示されます。 |

> **よくある質問:** *Word で影が表示されない場合は？*  
> Aspose.Words の最新バージョン（≥ 22.9）を使用していることを確認してください。古いリリースでは影のサポートが制限されていました。また、ドキュメントが最新の Word バージョン（2016 以降）で開かれているかも確認してください。

## 完全な動作例

以下は完全なコピー＆ペースト可能なプログラムです。`using` ディレクティブ、コメント、エラーハンドリングがすべて含まれており、スムーズに実行できます。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

プログラムを実行し、`C:\Temp\ShadowShape.docx` に移動すると、設定した通りの影が付いた長方形が表示されます。

## まとめと次のステップ

- これで **create word document c#** の方法、長方形の挿入、そしてカスタム **set shadow distance** を使用した **apply shadow to shape** の方法が分かります。  
- この例は Aspose.Words を使用しており、OpenXML の複雑さを抽象化し、Word バージョン間で一貫したレンダリングを保証します。  
- さらに踏み込むには？複数のシェイプを組み合わせたり、長方形内にテキストを追加したり、同じドキュメントを PDF としてエクスポートして影の変換を確認してみてください。

### 関連トピック

- ブランディングのためにヘッダー/フッターに **How to add shape** を追加する。  
- プログラムでチャートやテーブルを挿入するために **Aspose.Words** を使用する。  
- ベクターシェイプではなく画像に **shadow effects** をカスタマイズする。  
- 請求書や証明書の大量ドキュメント生成を自動化する。

自由に実験し、コードを壊してから再構築してください – これが概念を最速で身につける方法です。問題が発生したら、下にコメントを残すか、公式の Aspose.Words ドキュメントでより深い API の洞察を確認してください。

コーディングを楽しんで、Word ファイルを少しだけ洗練された見た目にしてください！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}