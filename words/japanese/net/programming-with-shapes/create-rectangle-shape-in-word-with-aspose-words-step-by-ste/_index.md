---
category: general
date: 2026-02-18
description: Aspose.Words を使用して長方形の図形を作成し、影の追加、図形サイズの設定、Word 文書の保存方法を数分で学びましょう。
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: ja
og_description: Word ファイルに長方形の図形を作成し、影の追加方法、図形サイズの設定方法を学び、Aspose.Words を使用して C# でドキュメントを保存します。
og_title: Wordで長方形シェイプを作成 – 完全な Aspose.Words チュートリアル
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.WordsでWordに矩形シェイプを作成する – ステップバイステップガイド
url: /ja/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使って Word に矩形シェイプを作成する – ステップバイステップガイド

Word ファイルに **矩形シェイプを作成** したいけど、どこから始めればいいか分からないことはありませんか？ 開発者はよく「シェイプに影を付けて、なおかつ文書を編集可能にしたい」と質問します。このチュートリアルではその疑問に答えると同時に、**影の付け方**、**シェイプサイズの設定**、**Word 文書の保存** を一連の流れで紹介します。

新しいドキュメントの初期化（**ドキュメントの作成方法** の最初のステップ）から最終的な *.docx* をディスクに保存するまで、外部参照は一切不要です。Visual Studio にコピペしてすぐに実行できる、自己完結型のサンプルです。

---

## 前提条件

- .NET 6+（または .NET Framework 4.7+）。Aspose.Words は最新の .NET ランタイムで動作します。
- 有効な Aspose.Words ライセンス（または無料評価キー） – これがないと透かしが表示されます。
- Visual Studio、Rider、またはお好みの C# エディタ。
- 基本的な C# の知識 – コンソールアプリを実行できれば問題ありません。

> **プロのコツ:** Mac を使用している場合でも、.NET 6 と VS Code で同じコードが動作します。その際は `Aspose.Words` NuGet パッケージを参照してください。

---

## 手順 1: ドキュメントの初期化 – **ドキュメントの作成方法** の基礎

何かを描く前に、空のキャンバスが必要です。Aspose.Words ではこれを `Document` と呼びます。  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **重要ポイント:** `Document` オブジェクトは *.docx* ファイル全体を表します。追加するすべてのシェイプ、段落、セクションはこのオブジェクトの子になります。クリーンなドキュメントから始めることで、隠れたスタイルが矩形に影響することを防げます。

---

## 手順 2: 矩形の定義と **シェイプサイズの設定**

矩形は `ShapeType.Rectangle` を持つ `Shape` にすぎません。意図した通りの見た目になるよう、明示的な寸法を設定します。

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **数値の意味:** Aspose.Words はポイント単位（1 pt = 1/72 in）を使用します。レイアウトに合わせて値を調整してください。A4 用紙の典型的な幅は 200 pt が快適です。

---

## 手順 3: **影の付け方** – シェイプを際立たせる

影はシェイプがページから「浮き上がって」いるように見せる視覚効果です。`Shadow` プロパティで色、距離、透明度、ぼかしを調整できます。

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **透明度を使う理由:** 完全に不透明な影は硬く見えることがあります。0.4 に設定すると、効果が控えめでプロフェッショナルになります。

---

## 手順 4: 矩形の位置決め – 周囲のテキストとインラインフロー

シェイプを段落内の文字のように扱いたい場合は、`WrapType` を `Inline` に設定します。これにより、後で文書を編集したときのレイアウトが予測可能になります。

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **例外ケース:** 矩形をテキストの上に浮かせたい（例: 透かし）場合は、`WrapType` を `Square` または `BehindText` に変更してください。

---

## 手順 5: シェイプをドキュメント本文に挿入

ここで実際に矩形を最初の段落に配置します。ドキュメントにまだコンテンツが無い場合、`FirstParagraph` が自動的に作成されます。

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **ヒント:** まず新しい段落を作成してからシェイプを追加することも可能です。テキストが前後に必要なシナリオで便利です。

---

## 手順 6: **Word 文書の保存** – 最終ステップ

すべてが揃ったら、ファイルの永続化はワンライナーで完了します。好きなパスを指定してください。サンプルではプレースホルダーを使用しているので、実際のディレクトリに置き換えてください。

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **結果:** 生成された *.docx* を Microsoft Word で開くと、幅 200 pt・高さ 100 pt の黒い影付き矩形が、最初の段落とインラインで表示されます。

---

## 期待される出力

**ShadowShape.docx** を開くと、文書は次のようになります：

- 矩形シェイプを含む単一の段落。
- 矩形には 5 pt オフセットの控えめな黒影が付いている。
- シェイプサイズは手順 2 で設定した寸法と一致する。
- 手動でテキストを追加しない限り、余分な文字は表示されません。

シェイプが表示されない場合は、正しい Aspose.Words バージョンを参照しているか、ライセンス（または評価版）が有効かを再確認してください。

---

## よくある質問とバリエーション

| 質問 | 回答 |
|------|------|
| *影の色を黒以外に変更できますか？* | もちろんです。`rectangleShape.Shadow.Color = Color.Blue;` のように `System.Drawing.Color` で任意の色を指定できます。 |
| *もっと大きな矩形が必要な場合は？* | `Width` と `Height` の値を調整してください。単位はポイントです。72 pt = 1 in です。 |
| *シェイプを絶対位置に配置できますか？* | はい。`WrapType = WrapType.Absolute` にし、`Top`／`Left` プロパティを設定します。 |
| *.NET Core でも動作しますか？* | 動作します。Aspose.Words はクロスプラットフォーム対応で、.NET Standard 用の NuGet パッケージをインストールすれば OK です。 |
| *矩形の中にテキストを入れられますか？* | 直接はできません。代わりに `TextBox` シェイプを使用してください。 |

---

## 完全動作サンプル（コピー＆ペースト可能）

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

プログラムを実行し、`C:\Temp\ShadowShape.docx` を開くと、説明通りの影付き矩形が確認できます。

---

## まとめ

Aspose.Words を使って Word ファイルに **矩形シェイプを作成** し、**シェイプサイズの設定**、**影の追加**、そして最終的に **Word 文書を保存** する方法を習得しました。**ドキュメントの作成方法** から結果の永続化まで、数行の C# コードで実現でき、より複雑なレイアウトにも拡張可能です。

次の課題に挑戦してみませんか？矩形を角丸シェイプに置き換えたり、異なる影の色を試したり、テーブルセル内にシェイプを埋め込んでみたり。各変更は本ガイドで学んだコア概念を強化します。

本ガイドが役立ったらシェアしたり、コメントで独自のバリエーションを共有したり、画像挿入やテーブル生成など他の Aspose.Words チュートリアルもぜひご覧ください。Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}