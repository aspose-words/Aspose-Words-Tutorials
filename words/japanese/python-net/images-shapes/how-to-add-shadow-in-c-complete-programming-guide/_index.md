---
category: general
date: 2025-12-25
description: C#で影を追加する方法（簡単なコード例付き）。影の距離の設定方法、色のカスタマイズ、そしてグラフィックに奥行きを作り出す方法を学びましょう。
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: ja
og_description: C#で影を追加する方法をステップバイステップで解説しています。ガイドに従って、影の距離、色、ぼかしを設定し、プロフェッショナルな見た目の形状を作成しましょう。
og_title: C#で影を追加する方法 – 完全プログラミングガイド
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: C#で影を追加する方法 – 完全プログラミングガイド
url: /ja/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で影を追加する方法 – 完全プログラミングガイド

C# で影を追加することは、グラフィックに立体感を持たせたいときの一般的なニーズです。このチュートリアルでは、形状の影を設定する正確な手順を解説します。影の距離の設定、ぼかしの調整、適切な色の選択方法を含みます。

平面的な長方形を見て「もう少し奥行きが欲しいな」と感じたことがあるなら、ここがピッタリです。空のドキュメントから始め、形状を配置し、デザイナーが配置したかのような洗練された影で仕上げます。余計な説明は省き、すぐにコピー＆ペーストできる実用的なサンプルを提供します。

## 学べること

- 新しいドキュメントを作成し、プログラムで形状を挿入する方法  
- 形状の影にソフトなぼかしを適用する方法  
- **影の距離を設定する方法**で、自然なオフセットを実現する方法  
- 任意の背景で機能する影の色の選び方  
- 結果を PDF（または必要な形式）で保存する方法  

### 前提条件

- .NET 6.0 以降（コードは .NET Core と .NET Framework でも動作）  
- Aspose.Words for .NET（無料トライアルまたはライセンス版）  
- C# の基本構文に関する基礎知識  

以上だけです。余計なライブラリやマジックは不要です。さっそく始めましょう。

![ソフトな黒い影が付いた形状の例 – 影の追加方法](https://example.com/placeholder-shadow.png "影の追加例")

## 手順 1: プロジェクトのセットアップと名前空間のインポート

まず、新しいコンソール アプリ（または任意の C# プロジェクト）を作成し、Aspose.Words の NuGet パッケージを追加します。

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

次に `Program.cs` を開き、必要な名前空間をスコープに持ち込みます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **プロのコツ:** Visual Studio を使用している場合、`Document` と入力すると IDE が `using` 文を自動提案してくれます。

## 手順 2: 新しいドキュメントを作成し、形状を追加

ライブラリの準備ができたら、`Document` オブジェクトをインスタンス化し、1 ページ目にシンプルな長方形を配置します。

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

なぜ長方形かというと、影の効果を余計な要素に邪魔されずに評価できる中立的なキャンバスになるからです。`ShapeType.Rectangle` を `Ellipse` や `Star` に置き換えても、影のロジックは同じままです。

## 手順 3: 影の追加 – ぼかし、距離、色の設定

ここがチュートリアルの核心です。**影の追加** 方法を解説します。Aspose.Words はすべての形状に `Shadow` オブジェクトを提供し、ぼかし、距離、色を調整できます。

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

コメント `// 3b) Set the shadow's offset distance` に注目してください。この行が **影の距離を設定する方法** に直接答えています。`shadow.Distance` を調整することで、形状と影の視覚的な間隔を制御し、特定の角度から光が当たっているように見せられます。

### なぜこれらの値か？

- **Blur = 5.0** – 柔らかなぼかしはハードなシルエットを防ぎつつ、十分に見えるようにします。  
- **Distance = 3.0** – 影が形状に近すぎず、自然に投影されているように見せます。  
- **Color = Black** – 明暗どちらの背景でもコントラストが保たれます。

数値は自由に調整してください。API は任意の `double` 値を受け付けます。

## 手順 4: ドキュメントを保存し、結果を確認

影の設定が完了したら、ファイルを書き出すだけです。Aspose.Words は多数のフォーマットに出力でき、PDF は共有に最適です。

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

`ShadowedShape.pdf` を開くと、灰色の長方形に右下方向に少しオフセットされたソフトな黒影が表示されます。影が薄すぎる場合は `shadow.Blur` または `shadow.Distance` を増やして再実行してください。

## よくある質問とエッジケース

### 透明な影が必要な場合は？

アルファチャンネルが 255 未満の ARGB カラーを使用します。

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### 複数の形状に同じ影を適用できますか？

もちろんです。ヘルパーメソッドを作成します。

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

各形状に対して `ApplyStandardShadow(rectangle);` を呼び出してください。

### 古い .NET Framework バージョンでも動作しますか？

はい。Aspose.Words 22.9 以降は .NET Framework 4.5 以上をサポートしています。プロジェクト ファイルを適宜調整してください。

## 完全動作サンプル

以下は `Program.cs` にそのまま貼り付けられるフルプログラムです。NuGet パッケージがインストールされていれば、すぐにコンパイル・実行できます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

プログラムを実行：

```bash
dotnet run
```

プロジェクト フォルダーに `ShadowedShape.pdf` が生成されます。任意の PDF ビューアで開き、影が期待通りか確認してください。

## 結論

C# で形状に **影を追加する方法** を、開始から完了まで網羅しました。また **影の距離を設定する方法** も併せて解説し、ぼかしと色の調整方法を示しました。数行のコードで、デザインツール不要のプロフェッショナルな立体感を実現できます。

基本をマスターしたら、以下にも挑戦してみてください：

- 影の色を微妙な青に変えてクールな雰囲気に  
- ぼかしを強めて夢幻的な拡散効果に  
- 同じ手法をチャート、画像、テキスト ボックスにも適用  

各バリエーションは同じコア概念を強化し、どんなシナリオでも影を自在にカスタマイズできるようになります。

質問があればコメントでどうぞ。ハッピーコーディング！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}