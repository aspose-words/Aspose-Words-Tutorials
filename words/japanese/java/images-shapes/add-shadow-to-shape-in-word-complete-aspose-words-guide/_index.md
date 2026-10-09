---
category: general
date: 2026-02-18
description: Aspose.Words を使用して Word の図形に影を追加します。数行のコードで、Word の影の色を変更し、オフセット、ぼかし、透明度を設定する方法を学びましょう。
draft: false
keywords:
- add shadow to shape
- how to change shadow color in word
language: ja
og_description: Aspose.Words を使用して Word の図形に影を追加します。このチュートリアルでは、Word で影の色を変更し、ぼかし、オフセット、透明度を調整する方法を示します。
og_title: Word の図形に影を付ける – 完全な Aspose.Words ガイド
tags:
- Aspose.Words
- C#
- Word Automation
title: Wordで図形に影を追加する – 完全なAspose.Wordsガイド
url: /ja/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word で図形に影を付ける – 完全 Aspose.Words ガイド

Word 文書で **図形に影を付ける** 必要があっても、どこから始めればいいか分からないことはありませんか？開発者はしばしば *Word で影の色を変更する方法* を尋ねます。  

このチュートリアルでは、Aspose.Words for .NET ライブラリを使った実践的な例を順を追って解説します。最後まで読めば、DOCX を読み込み、最初の図形を取得し、カスタムブラーとオフセットを持つ青い半透明の影を適用する、すぐに実行できるプログラムが手に入ります。曖昧な「ドキュメントを参照」ではなく、完全なコピーペーストソリューションです。

## 学べること

- Word 文書を読み込み、図形ノードを取得する方法。  
- **図形に影を付ける** 正確な API 呼び出し。  
- **Word で影の色を変更する** 方法、ブラー半径、X/Y オフセット、透明度の設定。  
- 複数の図形、既存の影、Word のバージョンに対する対処法のヒント。  

### 前提条件

- .NET 6.0 以降（コードは以前のバージョンでもコンパイルできますが、.NET 6 が推奨です）。  
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）。  
- C# と Word オブジェクトモデルの基本的な理解。  

これらが揃っていれば、さっそく始めましょう。

---

## 手順 1 – 図形を含む Word 文書を読み込む

まず、ソースファイルを指す `Document` インスタンスを作成します。パスは絶対でも実行ファイルからの相対でも構いません。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **ポイント:** `Document` クラスは Aspose.Words のすべての操作のエントリーポイントです。ファイルを一度だけロードすればメモリ使用量を抑え、ノードツリーを効率的にクエリできます。

## 手順 2 – 最初の図形ノードを取得する

図形は文書のノード階層内に存在します。`NodeType.SHAPE` の最初のノードを取得します。`true` フラグは「深く検索」することを意味します。

```csharp
// Grab the first Shape object in the document (depth‑first search).
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    System.Console.WriteLine("No shape found in the document.");
    return;
}
```

> **プロのコツ:** 特定の図形を対象にしたい場合は、常に最初のノードを取得するのではなく、`firstShape.Name` や `firstShape.AlternativeText` でフィルタリングしてください。

## 手順 3 – 図形に関連付けられた影オブジェクトを取得する

すべての `Shape` には `Shadow` プロパティがあり、影がまだ存在しない場合は `null` になることがあります。これにアクセスすると、変更可能な `Shadow` インスタンスが得られます。

```csharp
// The Shadow object is automatically created if it doesn't exist.
Shadow shapeShadow = firstShape.Shadow;
```

> **エッジケース:** 古い Word ファイル（2007 年以前）では影の保存方法が異なることがあります。Aspose.Words はこれを正規化するため、同じ API が DOC、DOCX、さらには RTF でも動作します。

## 手順 4 – ブラー半径（ポイント単位）を定義する

`5.0` ポイントのブラー半径は、ぼやけすぎずに柔らかなエッジを提供します。

```csharp
shapeShadow.BlurRadius = 5.0;   // points
```

## 手順 5 – 水平・垂直オフセットを設定する

オフセットは影を図形に対して相対的に移動させます。正の値は右／下へ、負の値は左／上へシフトします。

```csharp
shapeShadow.OffsetX = 3.0;      // move right 3 points
shapeShadow.OffsetY = 3.0;      // move down 3 points
```

## 手順 6 – 影の色に青を選択する  

ここでは `System.Drawing.Color` を使って **Word で影の色を変更する方法** を示します。

```csharp
shapeShadow.Color = Color.Blue;   // any System.Drawing.Color works
```

> **色が重要な理由:** 青い影はクールでコーポレートな印象を与え、ダークグレーはより中立的です。ブランドに合わせて選んでください。

## 手順 7 – 影の不透明度を調整する

不透明度は `0.0`（透明）から `1.0`（不透明）までの範囲です。ここでは控えめな効果として `0.6` を使用します。

```csharp
shapeShadow.Opacity = 0.6;   // 60% opacity
```

## 手順 8 – 変更後の文書を保存する

最後に、変更をディスクに書き戻します。元のファイルを上書きするか、新しいファイルを作成するかは自由です。

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
System.Console.WriteLine("Shadow applied and document saved.");
```

### 完全動作サンプル

すべてをまとめた、コピー＆ペーストしてすぐに実行できる完全プログラムは以下です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class AddShadowToShapeDemo
{
    static void Main()
    {
        // 1️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Find the first shape
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (firstShape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Get (or create) the shadow object
        Shadow shapeShadow = firstShape.Shadow;

        // 4️⃣ Set blur radius
        shapeShadow.BlurRadius = 5.0;

        // 5️⃣ Set offsets
        shapeShadow.OffsetX = 3.0;
        shapeShadow.OffsetY = 3.0;

        // 6️⃣ Change shadow color (how to change shadow color in Word)
        shapeShadow.Color = Color.Blue;

        // 7️⃣ Set opacity
        shapeShadow.Opacity = 0.6;

        // 8️⃣ Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        System.Console.WriteLine("Shadow applied and document saved.");
    }
}
```

**期待される結果:** `output_with_shadow.docx` を Microsoft Word で開くと、最初の図形に右下へ 3 pt シフトした柔らかな青い影が表示され、適度なブラーと 60 % の不透明度が適用されています。  

---

## 複数の図形を扱う場合

文書に複数のグラフィックがある場合は、以下のようにループ処理します。

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shp in shapes)
{
    // Apply the same shadow settings to each shape
    shp.Shadow.BlurRadius = 5.0;
    shp.Shadow.OffsetX = 3.0;
    shp.Shadow.OffsetY = 3.0;
    shp.Shadow.Color = Color.Blue;
    shp.Shadow.Opacity = 0.6;
}
```

> **注意:** この方法は既存の影設定を上書きします。元の設定を保持したい場合は、先に `Shadow` オブジェクトをクローンしてください。

## よくある落とし穴と対策

| 落とし穴 | 回避策 |
|---------|--------|
| **`Shape` が `null`** – 文書に画像がない | `GetChild` 後は必ず `null` チェックを行う |
| **影がすでに存在** – カスタムスタイルを意図せず上書き | 変更前に `shapeShadow` のプロパティを読み取る |
| **色空間が不適切** – 古い Word バージョンで `System.Drawing.Color` を使用すると予期せぬ色合いになる | 標準色を使用するか、ARGB を手動で定義する（例: `Color.FromArgb(255, 0, 0, 255)`） |
| **大規模文書でのパフォーマンス低下** – 数千ノードのループは遅くなる | トップレベルの図形だけが必要なら `doc.GetChildNodes(NodeType.Shape, false)` を使用 |

---

## 別の影効果が必要な場合は？

- **ハードエッジ:** `BlurRadius = 0` に設定。  
- **大きなオフセット:** `OffsetX`/`OffsetY` を 10 pt 以上に増やす。  
- **異なる不透明度:** `0.3` で薄い光彩、`0.9` で大胆な外観。  
- **グラデーション影:** Aspose.Words は直接的なグラデーション影をサポートしていません。事前にエフェクトを適用した画像を挿入する必要があります。

---

## プログラムで結果を検証する

Word を開かずに影の設定を確認したいこともあります。

```csharp
Shadow s = firstShape.Shadow;
System.Console.WriteLine($"Blur: {s.BlurRadius}, OffsetX: {s.OffsetX}, OffsetY: {s.OffsetY}, " +
                         $"Color: {s.Color}, Opacity: {s.Opacity}");
```

コンソールに設定した数値が出力されれば、API 呼び出しは成功しています。

---

## 結論

本稿では Aspose.Words を使用して **Word 文書の図形に影を付ける方法** と、**Word で影の色を変更する方法** をブラー、オフセット、透明度と共に実演しました。上記の完全なコードを使えば、数秒で任意の図形に影を付けられ、追加のヒントで一般的なミスを回避できます。  

次のステップに挑戦したいですか？個々の図形に異なる色を適用したり、影と反射を組み合わせてよりリッチなビジュアル効果を作り出したりしてみましょう。また、Aspose.Words の `ShapeStyle` クラスを使って線の太さ、塗りパターン、3‑D 回転なども調整できます。  

このガイドが役立ったら、チームと共有したり、Aspose.Words リポジトリにスターを付けたり、独自の実験結果をコメントで残したりしてください。ハッピーコーディング！

![Word shape with blue shadow – add shadow to shape example](https://example.com/images/shape-shadow.png "add shadow to shape example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}