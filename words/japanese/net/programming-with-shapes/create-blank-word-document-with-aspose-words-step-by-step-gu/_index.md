---
category: general
date: 2026-02-23
description: C# と Aspose.Words を使用して空白の Word ドキュメントを作成します。矩形シェイプの追加方法、影付きテキストの追加方法、そしてシェイプ付きの
  Word を数分で保存する方法を学びましょう。
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: ja
og_description: 空白のWord文書をすばやく作成します。このガイドでは、矩形シェイプの追加、影付き文字の追加、そしてAspose.Wordsを使用してシェイプ付きのWordを保存する方法を示します。
og_title: 空白のWord文書を作成 – 完全なC#チュートリアル
tags:
- Aspose.Words
- C#
- Document Automation
title: Aspose.Wordsで空白のWord文書を作成する – ステップバイステップガイド
url: /ja/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空の Word 文書を作成 – 完全 C# チュートリアル

Microsoft Word を開かずに **空の Word 文書をプログラムで作成** したいと思ったことはありませんか？ 多くの自動化プロジェクトでは、新しい .docx ファイルが必要で、そこに図形を配置し、影を付けて、後で使えるように **形状付きの Word を保存** したいものです。  

このガイドでは、空の文書から始めて **長方形の図形を追加** し、**影効果を追加** して、最終的にファイルを保存するまでの手順を順を追って説明します。最後には、任意の .NET コンソール アプリに貼り付けられる完全な実行可能スニペットが手に入ります。謎もなく、抜け落ちもありません。

## 必要なもの

- **Aspose.Words for .NET**（任意の最新バージョン、例: 24.10）。  
- .NET 6 以降（コードは .NET Framework 4.7+ でも動作します）。  
- 基本的な C# IDE—Visual Studio、Rider、または C# 拡張機能付き VS Code。  

以上です。Aspose.Words 以外の NuGet パッケージは不要で、Word のインストールも必要ありません。

---

## 手順 1: 空の Word 文書を作成

**空の Word 文書を作成** したいときに最初に行うのは `Document` クラスのインスタンス化です。これは Aspose.Words が提供する「白紙のキャンバス」と考えてください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **重要ポイント:** `Document` オブジェクトはすべてのセクション、段落、図形を保持します。空のインスタンスから始めることで、後から追加する要素をすべて自分で管理できるようになります。

---

## 手順 2: 文書に長方形の図形を追加

クリーンな文書ができたので、次は **長方形の図形を追加** します。長方形は `Shape` に `ShapeType.Rectangle` を指定しただけのシンプルな図形です。もちろん他のタイプも選べますが、デモには長方形が最適です。

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **プロのコツ:** **長方形以外の図形を追加** したい場合は、`ShapeType.Rectangle` を `ShapeType.Ellipse` や `ShapeType.Polygon` などの別の列挙値に変更すれば OK。残りのコードはそのままです。

---

## 手順 3: 図形にカスタム影を設定

普通の長方形だけではやや味気ないので、**影効果を追加** して立体感を出します。Aspose.Words では多数のプロパティを持つ `ShadowFormat` オブジェクトが用意されています。

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **重要ポイント:** 影は画面上で文書を見るときに微妙な奥行きを与えてくれます。`OffsetX`、`OffsetY`、`BlurRadius` などを調整してデザインに合わせましょう。

---

## 手順 4: 図形を文書に挿入

図形の準備ができたら、文書内のどこかに配置します。最も簡単なのは最初のセクションの最初の段落です。文書に段落がまだ無い場合、Aspose が自動的に作成します。

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **エッジケース:** 特定の見出しの後など、決まった位置に図形を入れたい場合は `document.GetChildNodes(NodeType.Paragraph, true)` で対象の `Paragraph` を取得し、`InsertAfter` または `InsertBefore` を使用してください。

---

## 手順 5: 図形付きの Word 文書を保存

最後に **形状付きの Word を保存** します。`Save` メソッドはファイル拡張子から自動的にフォーマットを判別します。

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **期待される結果:** `shadowedRectangle.docx` を Word（または互換ビューア）で開くと、1 ページ目の上部に柔らかい影が付いた灰色の長方形が表示されます。

---

## 完全動作サンプル

以下はコンソール アプリにそのまま貼り付けられる完全プログラムです。using ディレクティブ、コメント、先ほど説明した手順がすべて含まれています。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

プログラムを実行し、`YOUR_DIRECTORY` に移動して生成された `shadow.docx` を開いてください。微かな灰色の影が付いた長方形が表示されるはずです—まさに目指した通りです。

---

## よくある質問 & ヒント

### 図形の色を変えるには？
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
`FillColor` を設定した後に図形を文書に追加してください。

### 同じページに複数の図形を配置したい場合は？
追加の `Shape` オブジェクトを作成し、同じ段落または別の段落にそれぞれ `AppendChild` します。`WrapType` や `RelativeHorizontalPosition` を使ってレイアウトを調整できます。

### 影を保持したまま PDF にエクスポートできるか？
もちろん可能です。`document.Save("output.pdf")` とすれば、Aspose.Words は PDF 変換時に影効果を保持します。

### .NET Core でも動作するか？
はい。Aspose.Words はクロスプラットフォーム対応で、.NET Core、.NET 5+、および .NET Framework でも同じコードが動作します。

### 段落なしで図形だけを追加する方法は？
`Run` または `Story` に直接図形を追加できます。より正確な位置指定が必要な場合は `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` とし、`Left`／`Top` プロパティで調整してください。

---

## ビジュアル結果

![Word 文書内の灰色の影付き長方形 – add shadow word の例](https://example.com/placeholder-image.png "add shadow word の例")

*画像の alt テキストには二次キーワード **add shadow word** が含まれ、SEO 対策になっています。*

---

## 結論

本稿では **空の Word 文書を作成**、**長方形の図形を追加**、**影効果を適用**、そして **形状付きの Word を保存** する手順を Aspose.Words for .NET を使って実演しました。手順はシンプルです：`Document` をインスタンス化し、`Shape` を作成し、`ShadowFormat` を調整し、文書に挿入して `Save` を呼び出すだけです。  

ここからは自由に実験してください—別の図形タイプを試したり、色を変えたり、複数の図形を重ねたり。既存のコンテンツと結合したい場合は `new Document("existing.docx")` で既存ファイルを読み込み、同じ手順を適用すれば完了です。  

質問があればコメントで教えてください。ハッピーコーディング！

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}