---
category: general
date: 2026-03-06
description: Wordで長方形の図形を作成し、Aspose.Wordsで図形に影を追加します。Wordに長方形を挿入する方法と、C#で図形に影を付ける方法を学びましょう。
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: ja
og_description: Aspose.Words を使用して Word に長方形の図形を作成し、図形に影を追加します。Word に長方形を挿入する方法と、図形に影を付ける方法をステップバイステップで解説します。
og_title: Aspose.Words を使用して Word で影付きの長方形シェイプを作成する
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words を使用して Word で影付きの長方形シェイプを作成する
url: /ja/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して Word で影付きの長方形シェイプを作成する

Word 文書で **create rectangle shape** が必要だったことはありませんか？しかし、洗練された外観を与える方法が分からずに悩んだことはありませんか？同じ壁にぶつかる開発者は多いです。朗報です！Aspose.Words for .NET を使えば、数行の C# で **create rectangle shape** と **add shape shadow** の両方を実現できます。

このチュートリアルでは、**Word に長方形を挿入する方法** を詳しく解説し、**シェイプに影を追加する方法** を示します。最後には、`Shadow.docx` という保存可能なファイルができ、Word で開くとグレーがかった長方形に柔らかいドロップシャドウが表示されます。余計な画像ファイルや手動調整は不要、コードだけです。

## 学べること

- Aspose.Words で **create rectangle shape** を行う正確な C# 文  
- `Shadow` オブジェクトを使用して影を有効化・設定する方法  
- 各プロパティの重要性（例: `Transparency`, `Blur`, `Angle`）  
- よくある落とし穴（単位、バージョン互換性）と即時解決策  
- 今日すぐに実行できる、コピー＆ペースト可能な完全プログラム  

### 前提条件

- .NET 6+（または .NET Framework 4.7+）  
- Aspose.Words for .NET 23.10 以降（NuGet パッケージは `Aspose.Words`）  
- C# と Visual Studio（またはお好みの IDE）の基本的な理解  

これらが揃っていれば、すぐに始められます。

---

## ステップ 1: プロジェクトの設定と名前空間のインポート

まず、新しいコンソール アプリを作成（または既存のものを再利用）し、Aspose.Words NuGet パッケージを追加します。

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

次に、必要な名前空間を `Program.cs` にインポートします。

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** .NET 6+ を対象にしている場合、グローバル `using` ディレクティブを有効にすれば、各ファイルで同じ行を繰り返す必要がなくなります。

---

## ステップ 2: 空白の Word ドキュメントで **Create rectangle shape** を作成する

まず、`Document` オブジェクトと `DocumentBuilder` を作成して操作できるようにします。マジックは `InsertShape` メソッドで起こります。

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

なぜ 200 × 100 ポイントなのか？Word では 1 ポイントは 1/72 インチに相当するため、長方形は約 2.8 × 1.4 インチになります。目立ちすぎず、かつ十分に見えるサイズです。レイアウトに合わせて数値は自由に変更できますが、単位は **points**（ピクセルではなく）であることを忘れないでください。

---

## ステップ 3: **Add shape shadow** – 外観の設定

長方形ができたので、控えめなグレーの影を付けましょう。`Shadow` オブジェクトは `Shape` に属し、便利なプロパティを多数提供します。

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### 各プロパティの役割

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | 影のオン/オフを切り替える | `true` or `false` |
| **Color** | 影の基本色 | Any `System.Drawing.Color` |
| **Transparency** | 不透明度 (0 = 不透明、1 = 透明) | 0.0 – 1.0 |
| **Blur** | エッジの柔らかさ | 0 – 10 (数値が大きいほど柔らかい) |
| **Distance** | シェイプと影の間隔 | 0 – 20 points |
| **Angle** | 光源の方向 | 0 – 360 degrees |
| **Size** | シェイプに対する影のスケール | 0 – 200 % |

> **Why bother with these settings?**  
> 影を微調整することで、企業のブランディングガイドライン（例: プロフェッショナルな外観のために 20 % の透明度）に合わせられ、外部の画像エディタを使う必要がなくなります。

---

## ステップ 4: ドキュメントを保存して結果を確認する

最後に、ファイルをディスクに書き出します。好きなフォルダーを指定できるので、`YOUR_DIRECTORY` を実際のパスに置き換えてください。

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

`Shadow.docx` を Microsoft Word で開くと、グレーの長方形に 45° の角度でオフセットされた柔らかいドロップシャドウが表示されます。この視覚効果により、シェイプがページから「持ち上げられた」ように見え、洗練されたレポートや請求書に最適です。

---

## 完全な動作例

以下は `Program.cs` にコピー＆ペーストできる完全プログラムです。欠けている部分はなく、そのままコンパイル・実行できます。

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### 期待される出力

- **File:** プロジェクトの実行フォルダーに配置された `Shadow.docx`  
- **Visual:** ページ中央に配置された単一の長方形（デフォルトの白で塗りつぶし）に、右下へ 4 ポイントオフセットされたグレーの影が付いており、自然な見た目になるように少しぼかされています。

---

## よくある質問とエッジケース

### 1. 別の単位（例: センチメートル）が必要な場合は？

Aspose.Words はポイント単位で動作しますが、センチメートルをポイントに変換する簡単な式があります：  
`points = centimeters * 28.3465`。

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. 古い Aspose.Words バージョンでも動作しますか？

`Shadow` API はバージョン 14.0 で導入されました。古いバージョンを使用している場合は、NuGet でアップグレードが必要です。シェイプ作成に関するコードは長年安定しているため、破壊的変更に遭遇することはありません。

### 3. 他のシェイプ（例: 円）にも影を追加できますか？

もちろんです。任意の `Shape` オブジェクトは `Shadow` プロパティを持ちます。`ShapeType.Rectangle` を `ShapeType.Ellipse` や `ShapeType.Cloud` に置き換えて、同じ影設定を適用してください。

### 4. カラフルな影（例: ブランドの青）が必要な場合は？

`Color.Gray` を任意の `Color` に置き換えるだけです：

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

`Transparency` を調整して、色が強すぎないようにしてください。

---

## 🎨 ビジュアルサマリー

![Word で影付きの長方形シェイプを作成する (Aspose.Words 使用)](image-placeholder.png "Word で影付きの長方形シェイプを作成する (Aspose.Words 使用)")

*Alt text: Word で影付きの長方形シェイプを作成する (Aspose.Words 使用)*

スクリーンショット（プレースホルダー）は最終的なドキュメントを示しています—長方形とその柔らかいグレーの影だけが表示されています。

---

## 結論

これで **create rectangle shape** を Word ファイルに作成し、**add shape shadow** を適用し、Aspose.Words for .NET を使ってすべての視覚要素を微調整する方法が分かりました。今回構築した短いプログラムは、以下のようにワークフロー全体をカバーしています—

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}