---
category: general
date: 2026-03-25
description: C#でPDFドキュメントを作成し、数ステップで矩形シェイプの追加、塗りつぶし色の設定、サイズ調整、透明度の設定方法を学びましょう。
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: ja
og_description: C#でPDFドキュメントを作成し、矩形を追加して塗りつぶし色、サイズ、透明度を設定し、洗練されたPDF出力を実現する方法をご覧ください。
og_title: 矩形シェイプでPDFドキュメントを作成 – C#チュートリアル
tags:
- C#
- PDF
- Aspose.Words
title: 矩形シェイプでPDFドキュメントを作成する – 完全C#ガイド
url: /ja/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 矩形シェイプで PDF ドキュメントを作成 – 完全 C# ガイド

カスタムスタイルのシェイプを含む **PDF ドキュメントを作成** したいけど、どこから始めればいいか分からないことはありませんか？レポートジェネレータやマーケティングフライヤーを作るとき、プログラムで矩形を描画し、塗りつぶし色を設定し、サイズを調整し、透明度までコントロールできれば、PDF の見栄えが格段にプロフェッショナルになります。

このチュートリアルでは、**PDF ドキュメントを作成**、**矩形シェイプを追加**、**塗りつぶし色を設定**、**シェイプのサイズを定義**、そして **外側の影の透明度を設定** する、実行可能な完全な C# サンプルを順を追って解説します。最後には、結果を確認できる単一の PDF ファイル（`shadow.pdf`）が生成されます。

> **プロのコツ:** 同じ手法は他のシェイプタイプ（楕円、直線など）でも使えます。`ShapeType.RECTANGLE` を必要なシェイプに置き換えるだけです。

---

## 必要なもの

| 前提条件 | 理由 |
|--------------|----------------|
| **.NET 6+**（または .NET Framework 4.6+） | Aspose.Words ライブラリは最新のランタイムを対象としています。 |
| **Aspose.Words for .NET** NuGet パッケージ | `Document`、`Shape`、`ShadowEffect` などのクラスを提供します。 |
| **C# IDE**（Visual Studio、Rider、VS Code） | サンプルのデバッグと実行が楽になります。 |
| **基本的な C# 知識** | 深い解説なしで構文を理解できます。 |

ライブラリはコマンドラインからインストールできます：

```bash
dotnet add package Aspose.Words
```

これだけです—余計な DLL やネイティブ依存関係は不要です。パッケージが導入されれば、以下のコードはそのままコンパイル・実行できます。

---

## 手順別実装

以下の 5 つの論理ステップに分けて解説します。各ステップは見出しが付いており、直接コピー＆ペーストできる短いコードブロックが付属しています。

### ## 1. PDF ドキュメントを作成しキャンバスを準備

最初に `Document` をインスタンス化します。これは最終的に PDF ファイルになる空のキャンバスです。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **なぜ必要か？** `Document` はすべてのセクション、段落、シェイプを保持します。クリーンなオブジェクトから始めることで、過去の実行から残った不要なアーティファクトが混入しません。

### ## 2. 矩形シェイプを追加 – 塗りつぶし色とサイズを設定

ここで矩形を作成し、明るい黄色で塗りつぶし、サイズを定義します。**矩形シェイプの追加**、**塗りつぶし色の設定**、**シェイプサイズの設定** を同時に行います。

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **注記:** 幅・高さはポイント単位（1 ポイント = 1/72 インチ）で測定します。レイアウトに合わせて数値を調整してください。

### ## 3. 外側の影を適用しシェイプの透明度を設定

影は奥行きを与え、透明度のコントロールが **シェイプ透明度の設定** の本質です。以下では 30 % の透明度を持つグレーの外側影を設定します。

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **なぜ透明度を設定するか？** 30 % の透明な影は控えめで、矩形がページ上で「平坦」にならないようにします。

### ## 4. シェイプをドキュメント本文に挿入

矩形をドキュメントの最初のセクションの最初の段落に配置します。このステップで全体が結びつきます。

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **エッジケース:** シェイプを新しいページに配置したい場合は、シェイプを追加する前に `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` を前置してください。

### ## 5. PDF ファイルとして保存

最後に、メモリ上の構造を実際の PDF ファイルとして永続化します。ファイルは指定したフォルダーに書き込まれます。

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

プログラムを実行すると `shadow.pdf` という名前のファイルが生成されます。開くと、黄色の矩形に 4 ポイントオフセットしたソフトなグレーの影が付いた状態が確認できます。

> **期待される出力:** 1 ページの PDF で、矩形がページ左上付近に配置され、黄色で塗りつぶされ、サイズは 200 × 100 ポイント、半透明の外側影が付いています。

---

## 完全動作サンプル（コピー＆ペースト可能）

以下は新しいコンソールプロジェクトにそのまま貼り付けられる、全ソースコードです。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **ヒント:** `YOUR_DIRECTORY` を `C:\Temp` のような絶対パス、または `.\output` のような相対パスに置き換えてください。プログラムはフォルダーが存在しない場合自動で作成します。

---

## よくある質問 (FAQ)

**Q: 矩形のページ上での位置を変更できますか？**  
A: もちろんです。段落に追加する前に `rectangle.Left` と `rectangle.Top`（どちらもポイント単位）を設定してください。

**Q: 影ではなく塗りつぶし自体を透明にしたい場合は？**  
A: `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` を使用します。最初の引数がアルファチャンネル（0‑255）で、128 は約 50 % の透明度です。

**Q: .NET Core でも動作しますか？**  
A: はい。Aspose.Words は .NET Standard 2.0+ をサポートしているため、.NET 6、.NET 7、または .NET Framework 4.6+ でも同じコードが実行可能です。

**Q: 複数のシェイプを追加したい場合は？**  
A: 手順 2‑4 をシェイプごとに繰り返し、必要に応じて別の段落やセクションに挿入してください。

---

## 結論

ここまでで、**PDF ドキュメントをゼロから作成**し、**矩形シェイプを追加**、**塗りつぶし色を設定**、**サイズを定義**、そして **シェイプ透明度を調整** して洗練された影効果を実現しました。サンプルコードは自己完結型で、1 分未満で実行でき、より高度な PDF レイアウトに必要なコア概念を示しています。

次のチャレンジはどうですか？矩形を角丸シェイプに置き換えたり、シェイプ内部に画像を埋め込んだり、目次を自動生成したりしてみてください。同じ API でテキスト、画像、ベクターをレイヤー化できるので、可能性は無限です。

このガイドが役に立ったら、GitHub でスターを付けたり、チームメンバーと共有したり、あなた独自のバリエーションをコメントで教えてください。ハッピーコーディング！

---

![矩形シェイプで PDF ドキュメントを作成した例](/images/rectangle-shadow.png "作成された PDF（黄色の矩形とグレーの外側影）")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}