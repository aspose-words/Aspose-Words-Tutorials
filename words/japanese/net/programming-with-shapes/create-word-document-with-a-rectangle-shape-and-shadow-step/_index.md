---
category: general
date: 2026-03-01
description: Aspose.Words を使用して Word 文書を作成し、四角形のシェイプの追加方法、影の追加方法、透明度の設定方法、そしてシェイプの作成方法をすべて
  C# で学びます。
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: ja
og_description: C#でAspose.Wordsを使用してWord文書を作成します。矩形シェイプの追加、外側の影の適用、透明度の設定を数ステップで学びましょう。
og_title: 矩形シェイプと影付きのWord文書作成ガイド
tags:
- Aspose.Words
- C#
- Document Generation
title: 矩形シェイプと影付きのWord文書を作成する – ステップバイステップガイド
url: /ja/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 矩形シェイプと影付きの Word ドキュメントを作成する – ステップバイステップガイド

カスタムスタイルの矩形を含む **create word document** が必要になったことはありませんか？レポートテンプレートを作成していて、レイアウトを際立たせるためにさりげないドロップシャドウを加えたいかもしれません。あなただけではありません—開発者は常に「プログラムで矩形シェイプと影を追加するにはどうすればいいですか？」と質問しています。良いニュースは、Aspose.Words を使えば数行のコードで実現できることです。

このチュートリアルでは、空の Word ファイルの作成から矩形シェイプの追加、透明度付きの外側影の設定まで、全プロセスを順に解説します。最後までで、Word で開いてすぐに効果を確認できる、すぐに使える `Shadow.docx` が手に入ります。外部ツールや煩雑な XML は不要で、クリーンな C# コードと明快な説明だけです。

## 学べること

- **How to create shape** オブジェクトを Aspose.Words を使用して Word ドキュメントに作成する方法。
- **How to add rectangle shape** を段落に追加し、既存のコンテンツを乱さない方法。
- **How to add shadow**（外側影）を追加し、色、オフセット、ぼかし、透明度を制御する方法。
- **How to set transparency** を影に設定して、プロフェッショナルに見せる方法。
- 実務プロジェクトで必要になるかもしれないヒント、落とし穴、バリエーション。

### 前提条件

- .NET 6.0 以降（API は .NET Framework 4.6+ でも動作します）。
- NuGet でインストールした Aspose.Words for .NET（`Install-Package Aspose.Words`）。
- C# 構文の基本的な理解—特別なことはなく、通常の `using` 文とオブジェクト作成だけです。

> **Pro tip:** Visual Studio を使用している場合は、潜在的な null 参照バグを早期に検出できるように「nullable reference types」を有効にしてください。

## ステップ 1 – 空の Word ドキュメントを作成する

**create word document** を行うには、まず `Document` クラスから始めます。これは空のキャンバスと考えてください。後からセクション、段落、テーブル、シェイプなどを追加できます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

なぜ新しい `Document` インスタンスが必要なのでしょうか？すべてのシェイプ、段落、スタイルはドキュメントオブジェクトモデル（DOM）内に存在するためです。クリーンなドキュメントから開始することで、追加する矩形が既存のコンテンツと干渉しないことが保証されます。

## ステップ 2 – 矩形シェイプを定義する

ここで矩形を **how to create shape** します。`Shape` コンストラクタは所有するドキュメントとシェイプタイプを受け取ります。また、幅と高さはポイント単位で設定します（1 pt ≈ 1/72 in）。

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

「ポイントの代わりにセンチメートルを使えるか？」と思うかもしれません。API はポイントのみ受け付けますが、変換は可能です：`points = centimeters * 28.35`。この小さな変換は、シェイプをページ余白に合わせる際に便利です。

## ステップ 3 – 外側影を追加し透明度を設定する

ここがマジックがかかる部分です：**how to add shadow** と **how to set transparency** をその影に対して行います。`ShadowFormat` プロパティで完全に制御できます。

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Why these settings?**  
- **Transparency** は下のページテクスチャを透過させ、影が重く見えすぎるのを防ぎます。  
- **OffsetX/Y** はシェイプがページから浮き上がっているような錯覚を作ります。  
- **BlurRadius** はエッジを柔らかくします—これがないと影は硬い矩形になり、不自然に見えます。  

よりドラマチックな効果が必要な場合は、`OffsetX/Y` を 10 に上げ、`BlurRadius` を 8 に増やします。逆に控えめなヒントが欲しい場合は、両方とも 2 に保ちます。

## ステップ 4 – シェイプをドキュメントに挿入する

ここでドキュメントの最初の段落に **add rectangle shape** を行います。ドキュメントにコンテンツがない場合、`FirstParagraph` が自動的に作成されます。

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

特定のテーブルセルや後の段落内にシェイプを入れたい場合はどうしますか？そのノードを (`doc.GetChild(NodeType.Paragraph, index, true)`) で取得し、`AppendChild` を呼び出すだけです。同じシェイプオブジェクトは、複数コピーが必要なときにクローンできます。

## ステップ 5 – ドキュメントを保存する

最後に、ディスク上に **create word document** ファイルを作成します。環境に合ったパスを使用してください。例ではプレースホルダーを使用しています。

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Microsoft Word で `Shadow.docx` を開くと、右下にオフセットされた柔らかな外側影を持つ薄いグレーの矩形が表示されます。影の 30 % 透明度により、ページ全体を支配しないようになっています。

---

![影付き矩形シェイプのある Word ドキュメントを作成する](image.png "影付き矩形シェイプのある Word ドキュメントを作成する")

*画像の代替テキスト: 影付き矩形シェイプのある Word ドキュメントを作成する*

## 完全な、すぐに実行できるコード

以下はコンソールアプリにコピー＆ペーストできる完全なプログラムです。欠落部分はなく、「詳細はドキュメントを参照」もありません。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### 期待される結果

- ターゲットフォルダーに **Shadow.docx** という名前のファイルが作成されます。
- Word で開くと、暗いグレーの外側影を持つ矩形（200 × 100 pt）が表示されます。
- 影は水平方向・垂直方向に 5 pt オフセットされ、ぼかされ、30 % 透明です。

## よくある質問とエッジケース

| Question | Answer |
|----------|--------|
| **影の色をブランドに合わせて変更できますか？** | もちろんです。`System.Drawing.Color.DarkGray` を任意の `Color` に置き換えるだけです。例えば、青系のアクセントにしたい場合は `Color.FromArgb(255, 0, 120, 215)` を使用します。 |
| **外側ではなく内側の影が必要な場合はどうすればいいですか？** | `ShadowFormat.Style = ShadowStyle.InnerShadow` を設定します。その他のプロパティは同様に機能します。 |
| **古いバージョンの Word でも透明度はサポートされていますか？** | はい。Aspose.Words は Word 2007 以降が理解できる適切な XML を出力します。古いバージョンでは透明度の値が無視される可能性がありますが、影は表示されます。 |
| **異なる影を持つ複数のシェイプを追加できますか？** | もちろんです。新しい `Shape` インスタンスを作成し、各影を個別に設定して、目的のノードに追加します。 |
| **数百個のシェイプを扱う場合のパフォーマンスはどうですか？** | 多数のシェイプを作成するとメモリ使用量が増加する可能性があります。単一の `Document` インスタンスを再利用し、ループでシェイプを追加してください。メモリが逼迫した場合は一時オブジェクトを破棄しましょう。 |

## 実務プロジェクト向けのヒント

- **Batch generation:** 多数のユーザー向けにレポートを生成する際は、単一の `Document` テンプレートをインスタンス化し、各イテレーションでクローンします。シェイプを追加する前にプレースホルダーを置換してください。
- **Dynamic sizing:** ページ寸法（`document.FirstSection.PageSetup.PageWidth`）を使用して、ページに対するシェイプサイズを計算し、異なる用紙サイズでもレイアウトが一貫するようにします。
- **Testing:** 影のパラメータを変更したら、必ず生成された `.docx` を Word で開いて確認してください。視覚的なフィードバックは数値を推測するよりも早いです。

## 次のステップ

**how to add rectangle shape**、**how to add shadow**、**how to set transparency** が分かったので、次のことを検討してください：

- シェイプに **gradient fills** を追加する（`Shape.FillFormat`）。
- シェイプ内に **pictures** を埋め込み、透かし効果を実現する。
- **tables** を使用して、複数の影付きシェイプをグリッド状に配置する。
- 同じドキュメントを PDF にエクスポートする（`document.Save("output.pdf")`）際に影を保持する。

これらはすべて同じ基本概念に基づいているため、コードの拡張が容易に感じられるでしょう。

---

### まとめ

まず Aspose.Words で **create word document** を行い、次に矩形を **how to create shape** し、**how to add shadow** を適用し、**how to set transparency** を調整して結果を保存しました。この一連のプロセスは、あらゆる自動化シナリオに適用できるコンパクトで再利用可能なパターンです。

自由に試してみてください—色を変えたり、オフセットを調整したり、複数のシェイプを重ねたりできます。問題が発生したら上記のセクションに戻りましょう。すぐに参照できるように作られています。コーディングを楽しんで、あなたのドキュメントが常に洗練されたものになることを願っています！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}