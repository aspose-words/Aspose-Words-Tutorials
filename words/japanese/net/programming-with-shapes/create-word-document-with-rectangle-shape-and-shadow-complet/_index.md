---
category: general
date: 2026-01-02
description: Aspose.Words を使用して、長方形のシェイプを持つ Word ドキュメントを作成し、シェイプの塗りつぶし色を設定し、docx ファイルとして保存します。数分で影付きの長方形の作成方法を学びましょう。
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: ja
og_description: カスタム矩形でWord文書を作成し、塗りつぶし色を設定、影を追加してDOCXとして保存します。完全なコードと解説付き。
og_title: 矩形シェイプ付きWord文書の作成 – ステップバイステップ
tags:
- Aspose.Words
- C#
- Document Generation
title: 矩形シェイプと影付きのWord文書作成 – 完全ガイド
url: /ja/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Document に長方形シェイプと影を追加する – 完全ガイド

Word 文書にスタイリッシュな長方形を入れたいことはありませんか？ロゴのプレースホルダーやカラーバナー、あるいはレポート内の視覚的なヒントとして使えるかもしれません。このチュートリアルでは **長方形シェイプを追加**し、塗りつぶしカラーを設定し、さりげない影を適用し、最後に **docx ファイルを保存**する方法を Aspose.Words for .NET を使って解説します。

実行可能な C# スニペットと、各行の明確な説明、そしてプロジェクトで再利用できるヒントを提供します。余計な説明は省き、すぐにコピーペーストできる実践的な解決策だけをご紹介します。

## 必要な環境

- .NET 6 以降（.NET Framework でも動作します）  
- Visual Studio 2022（またはお好みのエディタ）  
- **Aspose.Words** NuGet パッケージ (`Install-Package Aspose.Words`)  

上記がすでに揃っていれば、さっそく始めましょう。

## Step 1 – Initialize a New Document (How to create word document)

最初に **Word 文書をメモリ上で作成** します。空白のキャンバスを開き、そこに長方形を描くイメージです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **ポイント:** `Document` は DOCX 全体を表し、`DocumentBuilder` はテキスト、テーブル、画像、シェイプなどを手軽に挿入できるヘルパーです。内部のノードツリーを自分で操作する必要はありません。

## Step 2 – Insert a Rectangle Shape (Add rectangle shape)

次に **長方形シェイプを文書に挿入** します。`InsertShape` メソッドはシェイプの種類とサイズ（ポイント単位、1pt = 1/72 インチ）を受け取ります。

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **プロのコツ:** 別のジオメトリ（楕円、三角形など）が必要な場合は `ShapeType.Rectangle` を目的の列挙値に置き換えるだけです。

## Step 3 – Configure the Shadow (Set shape fill color & shadow)

影を付けると平面的なシェイプが立体的に見えます。ここでは影を有効にし、外観を微調整します。

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **なぜこの値か？** ほどほどのぼかし半径と 5pt の距離にすることで、影がシェイプを圧倒しないようにし、45° の角度は左上から光が当たるという UI の一般的な慣習を模倣しています。

## Step 4 – Save the Document (Save docx file)

最後に **docx ファイルをディスクに保存** します。環境に合わせてパスを調整してください。

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

`ShadowDemo.docx` を Word で開くと、ライトブルーの長方形に柔らかいグレーの影が付いた状態が以下のスクリーンショットと同じように表示されます。

![Word Document に長方形シェイプと影を追加する](https://example.com/images/rectangle-shadow.png "Word Document に長方形シェイプと影を追加する")

*画像の代替テキスト:* **Word Document** に影付きの長方形シェイプが表示されています。

## Full, Ready‑to‑Run Example (How to create rectangle and save)

すべてをまとめた完全なプログラムです。コンソールアプリにコピーして実行できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### 期待される結果

- **ShadowDemo.docx** という名前のファイルが対象フォルダーに作成されます。  
- Microsoft Word で開くと、テキスト「Shadow Demo」の下にライトブルーの長方形が表示されます。  
- 長方形には 45° 方向の柔らかいグレーの影が付いており、わずかな 3D 感覚が得られます。

## Common Questions & Edge Cases

### 別のサイズが必要な場合は？

`InsertShape` の `200, 100` 引数を変更してください。これらは幅と高さ（ポイント）です。正方形にしたい場合は同じ数値を指定します。

### 影をもっと強調したい？

`BlurRadius` を大きくするとエッジが滑らかになり、`Distance` を増やすとオフセットが大きくなります。また `Transparency` を低く（例: `0.1`）すると影が濃くなります。

### 長方形に枠線を付ける方法は？

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### 古いバージョンの Aspose.Words でも動作しますか？

はい。`ShadowFormat` クラスは 2020 年初期リリースから存在します。非常に古いバージョンを使用している場合は、すべてのプロパティにアクセスできるようにアップグレードが必要です。

## Tips & Pitfalls

- **プロのコツ:** 大きな文書は使用後に必ず `doc.Dispose()` してネイティブリソースを解放しましょう（特に Web アプリで重要）。  
- **注意点:** 相対パスだけで書き込み権限が不足していると `UnauthorizedAccessException` が発生します。絶対パスを使用するか、アプリプールに書き込み権限を付与してください。  
- **覚えておくべきこと:** `FillColor` プロパティは任意の `System.Drawing.Color` を受け取ります。カスタムのパステルカラーが欲しい場合は `Color.FromArgb(255, 173, 216, 230)` などを利用できます。

## Next Steps

**Word 文書を作成**し、**長方形シェイプを追加**し、**塗りつぶしカラーを設定**し、**docx ファイルを保存**できるようになったら、さらに以下を試してみてください。

- `RelativeHorizontalPosition` と `RelativeVerticalPosition` を使って複数シェイプを配置。  
- `Shape.TextBox` を利用して長方形にキャプション用テキストを入れる。  
- 同じ文書を PDF にエクスポート（`doc.Save("output.pdf")`）して配布。

もっと高度なグラフィックに興味がある方は、Aspose.Words の **WordArt**、**チャート**、**インライン画像** のサポートをチェックしてください。すべて同じパターンで、ノードを作成し、プロパティを設定し、保存するだけです。

---

### TL;DR

- `Document` と `DocumentBuilder` を使って **Word 文書を作成**。  
- `InsertShape(ShapeType.Rectangle, …)` で **長方形シェイプを追加**。  
- `FillColor` で背景色を設定。  
- `ShadowFormat` を有効にし、各種プロパティで見た目を調整。  
- `document.Save("yourPath.docx")` で **docx ファイルを保存**。

Happy coding, and enjoy making your Word files look a little more stylish!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}