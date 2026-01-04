---
category: general
date: 2026-01-03
description: C#でWordに長方形の図形を作成し、図形に影を付ける。Wordに図形を挿入し、影を付け、プログラムでWord文書を生成する方法を学びます。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: ja
og_description: C#でWordに長方形の図形を作成し、図形に影を追加します。このガイドに従ってWordに図形を挿入し、影を設定し、プログラムで文書を生成しましょう。
og_title: C#でWordに長方形の図形を作成する – 完全チュートリアル
tags:
- C#
- Word Automation
- Aspose.Words
title: C# を使用して Word に長方形シェイプを作成する – ステップバイステップガイド
url: /ja/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# を使用して Word に長方形シェイプを作成 – 完全チュートリアル

Word 文書に **長方形シェイプを作成** したいけど、どこから始めればいいか分からないことはありませんか？同じ壁にぶつかる開発者は多いです。特に **シェイプに影を付ける** と、より洗練された見た目になります。このチュートリアルでは、**Word にシェイプを挿入** し、微妙な影を適用し、最終的に **c# generate word document** ファイルを作成してユーザーに配布できるまでの手順を詳しく解説します。

プロジェクトのセットアップから影のプロパティ調整までを網羅し、実行可能なコードサンプルで締めくくります。余計な説明は省き、実務ですぐに使えるポイントだけをお届けします。

## What You’ll Learn

- C# で Aspose.Words（または Open XML）を使って **長方形シェイプを作成** する方法  
- 奥行きを出すために **シェイプに影を付ける** 正確なプロパティ  
- `DocumentBuilder` を使ってシェイプを配置する場所  
- Microsoft Word で正しく開くようにファイルを保存する方法  
- 実務で役立つコツ、落とし穴、バリエーション  

### Prerequisites

- .NET 6.0 以上（コードは .NET Core と .NET Framework でも動作）  
- Word ファイルを操作できる NuGet パッケージ – ここでは API がシンプルな **Aspose.Words for .NET** を使用します。Open XML SDK を好む場合は概念は同じですが、クラスが異なります。  
- Visual Studio、VS Code、またはお好みの C# IDE  

> **Pro tip:** 予算が限られている場合は、Aspose の無料トライアルを利用すると学習に最適です。テスト時はライセンス行をコメントアウトに置き換えてください。

## Step 1: Install the Word‑Processing Library

まず、ライブラリをプロジェクトに追加します。ソリューションフォルダーでターミナルを開き、次のコマンドを実行してください。

```bash
dotnet add package Aspose.Words
```

Open XML SDK を使用する場合は `dotnet add package DocumentFormat.OpenXml` がコマンドになります。このガイドは Aspose.Words 前提ですが、API 呼び出しを置き換えるだけで簡単に対応できます。

## Step 2: Create a New Blank Document

ライブラリの準備ができたら、**長方形シェイプを作成** するためにクリーンな `Document` オブジェクトから始めます。これが新しいキャンバスです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` は低レベルのノードツリーに深入りせずにコンテンツを挿入できる高レベル API を提供します。

## Step 3: Insert the Rectangle Shape

`DocumentBuilder` が手元にあれば、**Word にシェイプを挿入** できます。`InsertShape` メソッドはシェイプの種類とサイズ（幅・高さ）をポイント単位で受け取ります。

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

この時点で長方形は文書に表示されますが、やや平坦に見えます。次のステップで影を付けます。

## Step 4: Add Shadow to the Shape

影はシェイプに奥行きを与えます。`Shadow` オブジェクトでぼかし、距離、角度、色、透明度を細かく調整できます。以下は多くのレポートでうまく機能する設定例です。

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**なぜこの値なのか？**  
- `BlurRadius` を `5.0` にするとエッジが滑らかになり、ぼやけすぎません。  
- `Distance` を `4.0` にすると影が目立つ程度にオフセットされます。  
- `Angle` を `45` にすると左上からの自然光を模倣し、一般的な UI の慣例に合います。  
- `Transparency` を `0.3` にすると、影がシェイプの塗りつぶしを圧倒しません。

よりドラマチックにしたい場合は `BlurRadius` を上げ、`Transparency` を下げます。逆にほぼ見えないほど控えめにしたい場合は数値を入れ替えてください。

## Step 5: Save the Document

最後にファイルをディスクに書き出します。`Save` メソッドは拡張子からフォーマットを自動判別するので、`.docx` とすれば最新の Word 形式になります。

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

`ShadowRectangle.docx` を Microsoft Word で開くと、ソフトな影が付いた鮮明な長方形が表示されます。これこそが「**シェイプの追加方法**」をプロフェッショナルに実装した結果です。

![Create rectangle shape with shadow in Word](placeholder-image.png "Create rectangle shape with shadow in Word")

*Image alt text: Wordで影付きの長方形シェイプを作成*

## Full Working Example

すべてをまとめた、すぐに実行できる完全版プログラムです。コンソールアプリにコピペして **F5** を押すだけです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Expected Result

- 生成された `ShadowRectangle.docx` には、カーソル位置に **1 つの長方形シェイプ** が中央に配置されています。  
- 長方形には **30 % 透明な黒色のソフト影** が 45° の角度でオフセットされています。  
- それ以外のコンテンツは追加されず、ファイルは軽量で他のレポートに埋め込みやすい状態です。

## Common Questions & Edge Cases

### What if I need a different shape?

`ShapeType.Rectangle` を任意の `ShapeType` 列挙値（例：`Ellipse`、`Triangle`）に置き換えるだけです。影の API は同じなので、設定を再利用できます。

### How do I change the fill color?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Can I add the shape to a specific paragraph?

はい。`InsertShape` を呼び出す前に `builder.MoveToParagraph(index)` で `DocumentBuilder` を目的の段落に移動させます。これでシェイプが正確に必要な位置に挿入されます。

### What about older Word formats (.doc)?

拡張子を変更するだけです：

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

影機能は Word 2003 以降でサポートされているため、効果は維持されます。

### Using Open XML SDK instead of Aspose?

手順は同じです：`WordprocessingDocument` を作成し、`Drawing` 要素を追加し、`<a:shadow>` プロパティを設定します。XML は冗長になりますが、サイズ、ぼかし、距離、角度といった概念は同一です。

## Tips to Avoid Pitfalls

- **ライセンスを忘れずに**。有料版 Aspose を使用する場合、ライセンスが無いと透かしが入ります。  
- **単位はポイント** です。ピクセルではありません。一般的な画面ピクセルは約 0.75 pt なので、サイズはそれに合わせて調整してください。  
- **`WrapType` が `Inline` の場合、影のプロパティは無視されます**。影を正しく描画させるには `WrapType = WrapType.Square` のようにフローティングシェイプを使用してください。  
- **ネットワーク共有へ保存する場合は権限に注意**。パスが正しくアクセスできるか事前にテストしましょう。

## Conclusion

これで C# を使って Word 文書に **長方形シェイプを作成**し、**シェイプに影を付ける** 方法、そして **c# generate word document** ファイルをすぐに配布できる手順が身につきました。ライブラリのインストール、`Document` のインスタンス化、シェイプの挿入、影の設定、保存というコアステップは覚えやすく、他のシェイプや色、動的データにも簡単に応用できます。

次はどうしますか？複数のシェイプを重ねたり、画像を埋め込んだり、テーブルやチャートを含むフルレポートを生成したりしてみましょう。また、データ値に応じて影の強さを変える条件付き書式に挑戦すれば、機能的だけでなく視覚的にも魅力的な文書が作れます。

ぜひ試してみて、疑問や問題があればコメントで教えてください。ハッピーコーディング！そして、あなたの Word 文書が常に完璧なドロップシャドウを持ちますように。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}