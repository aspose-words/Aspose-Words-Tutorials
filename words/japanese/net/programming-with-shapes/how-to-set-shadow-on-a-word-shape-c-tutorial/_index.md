---
category: general
date: 2026-03-30
description: C# を使用して Word のシェイプに影を設定する方法を学びます。このガイドでは、シェイプに影を追加する方法、シェイプの透明度を調整する方法、そして矩形の影を追加する方法も示しています。
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: ja
og_description: C#でWordの図形に影を設定する方法は？このステップバイステップガイドに従って、図形に影を追加し、透明度を調整し、長方形の影を追加しましょう。
og_title: Wordの図形に影を設定する方法 – C#チュートリアル
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Wordシェイプに影を設定する方法 – C#チュートリアル
url: /ja/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word の図形に影を設定する方法 – C# チュートリアル

Word 文書内の図形に **影を設定** する方法を UI をいじらずに知りたくありませんか？ あなただけではありません。多くのレポートやマーケティング資料では、さりげないドロップシャドウが矩形を際立たせ、プログラムで行うことで何時間も節約できます。

このガイドでは、**影の設定方法** を示すだけでなく、**図形に影を追加**、**図形の透明度を調整**、さらには **矩形に影を追加** する方法まで網羅した、実行可能な完全サンプルをステップバイステップで解説します。最後には、洗練された外観の Word ファイル（`output.docx`）が生成され、各プロパティの意味も理解できるようになります。

## 前提条件

- .NET 6 以上（または .NET Framework 4.7.2）と C# コンパイラ  
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）  
- C# と Word のオブジェクトモデルに関する基本的な知識  

追加のライブラリは不要です。すべて Aspose.Words 内に収まります。

---

## C# で Word の図形に影を設定する方法

以下が完全なソースファイルです。`Program.cs` として保存し、IDE もしくは `dotnet run` で実行してください。コードは既存の `.docx` を読み込み、最初の図形（デフォルトでは矩形）に影を有効にし、いくつかの視覚パラメータを調整して結果を保存します。

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **表示される内容** – 矩形に黒いドロップシャドウが付与され、30 % の透明度で右下に 5 pt 移動し、柔らかいぼかしがかかります。`output.docx` を Word で開いて確認してください。

## 図形の透明度を調整する – 重要性

透明度は単なる見た目の調整ではなく、可読性にも影響します。`0.0` は影を完全に不透明にし、`1.0` は完全に非表示にします。上記のサンプルでは `0.3` を使用し、明暗両方の背景で自然に見える効果を実現しています。自由に数値を変えてみてください。

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

**図形の透明度を調整** は、図形自体の塗りつぶし色に対しても適用でき、半透明の矩形を作りたい場合に便利です。

## 異なるオブジェクトに影を追加する

今回のコードは `Shape` オブジェクトを対象にしていますが、同じ `ShadowFormat` プロパティは **Image**、**Chart**、さらには **TextBox** オブジェクトでも利用可能です。以下はコピペで使えるパターンです。

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

したがって、ロゴや装飾アイコンに **図形に影を追加** したい場合でも、手順は全く同じです。

## 任意の図形に影を追加する – エッジケース

1. **バウンディングボックスがない図形** – 手書き風のフリーハンド図形などは影をサポートしません。`ShadowFormat.Visible` を設定しても黙って失敗します。安全に行うには `shape.IsShadowSupported` を確認してください。  
2. **古い Word バージョン** – 影のプロパティは Word 2007 以降の機能にマッピングされています。Word 2003 で開くと影は無視されます。  
3. **複数の影** – 現在 Aspose.Words は図形につき 1 つの影しかサポートしていません。二重レイヤー効果が必要な場合は、図形を複製してオフセットし、別々の影設定を適用してください。

## 矩形に影を追加する – 実務的なユースケース

四半期レポートを自動生成し、各セクションヘッダーをカラー矩形で表示するとします。**矩形に影を追加** すると、ページ全体が「カード」風の外観になります。手順は基本例と同じですが、対象が矩形であること（`shape.ShapeType == ShapeType.Rectangle`）を確認してください。矩形を最初から作成したい場合は、以下のスニペットをご参照ください。

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

この追加を組み込んでプログラムを実行すれば、希望通りの **矩形に影を追加** した図形が生成されます。

---

![Word shape with shadow](placeholder-image.png){alt="Word の図形に影を設定する方法"}

*図: 影設定を適用した後の矩形。*

## クイックリキャップ（箇条書きチートシート）

- **ドキュメントを読み込む**：`new Document(path)`  
- **図形を取得**：`doc.GetChild(NodeType.Shape, index, true)`  
- **影を有効化**：`shape.ShadowFormat.Visible = true;`  
- **色を設定**：任意の `System.Drawing.Color` を使用  
- **透明度を調整**（`0.0–1.0`）で不透明度をコントロール  
- **OffsetX / OffsetY** で影を水平・垂直に移動（ポイント）  
- **BlurRadius** でエッジをぼかす – 値が大きいほど柔らかい影になる  
- **保存** して Word で開き、結果を確認  

## 次に挑戦することは？

- **動的カラー** – テーマやユーザー入力から影の色を取得  
- **条件付き影** – 図形の幅が一定以上の場合のみ影を適用  
- **バッチ処理** – 文書内のすべての図形をループし、**図形に影を追加** を自動化  

このチュートリアルを通じて **影の設定方法**、**図形の透明度調整**、そして **矩形に影を追加** する手順を習得できたはずです。ぜひ実験し、失敗し、修正してみてください。コーディングは最高の教師です。

---

*コーディングを楽しんでください！ 本チュートリアルが役立ったら、コメントや自分の影テクニックを共有してください。互いに学び合うことで、Word 文書はますます美しくなります。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}