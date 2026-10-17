---
category: general
date: 2026-04-10
description: C#で図形に影を設定する方法 – ドロップシャドウの適用、透明度の変更、ぼかしの調整、そして Aspose.Words を使用した図形の影の追加方法を学びましょう。
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: ja
og_description: C#でシェイプに影を設定する方法 – このチュートリアルでは、ドロップシャドウの適用、透明度の変更、ぼかしの調整、そしてシェイプの影を追加する方法を、分かりやすいコード例とともに紹介します。
og_title: C#でシェイプに影を設定する方法 – 完全ガイド
tags:
- Aspose.Words
- C#
- Document Automation
title: C#でシェイプに影を設定する方法 – ステップバイステップガイド
url: /ja/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でシェイプに影を設定する方法 – 完全ガイド

Word 文書をプログラムで作成するときに、シェイプに**影を設定する方法**を疑問に思ったことはありませんか？ あなたは一人ではありません。テキストボックスやロゴ、コールアウトボックスに微妙なドロップシャドウが必要になると、多くの開発者が壁にぶつかりますし、API ドキュメントはやや不足していると感じることが多いです。

このチュートリアルでは、`.docx` の読み込みから最初の `Shape` の取得、ドロップシャドウの適用、透明度の調整、ぼかし半径の設定、そして最適な位置決めまで、全プロセスを順に解説します。最後まで読めば、Aspose.Words .NET 2023 以降で動作する再利用可能なスニペットが手に入り、各プロパティが *なぜ* 重要なのかが理解できるようになります。

## 必要なもの

- **Aspose.Words for .NET** (NuGet パッケージ `Aspose.Words`) – `Document`、`Shape`、`ShadowFormat` クラスを提供します。  
- **.NET 6+**（または .NET Framework 4.7.2） – 最近のランタイムであればどれでも可。  
- シンプルな Word ファイル（`input.docx`）で、少なくとも 1 つのシェイプ（例：テキストボックス）が含まれているもの。  
- Visual Studio、VS Code、またはお好みの IDE。

以上です。余計なサードパーティーツールや COM インターロップは不要で、純粋な C# だけで完結します。

![how to set shadow example](image-placeholder.png){:alt="Word 文書のシェイプに影を設定する方法"}

## 影の設定 – 概要

**影を設定する**というコアアイデアは、`Shape` が持つ `ShadowFormat` オブジェクトを操作することです。`ShadowFormat` は影そのもののミニチュア「スタイルシート」のようなもので、影が表示されるか、色は何か、透明度はどれくらいか、ぼかし具合はどうか、シェイプに対してどの位置にあるかをレンダラに指示します。

以下は *完全* な実行可能プログラムです。コンソールアプリにコピーペーストして **F5** を押すだけで、保存された `output.docx` に影が現れます。

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### これらの設定が重要な理由

- **Visible** – このフラグをオンにしないと、他のすべてのプロパティは無視されます。  
- **Color** – ダークグレーは一般的な UI のドロップシャドウを模倣します。任意の `Color` に差し替え可能です。  
- **Transparency** – 0.3 にすると、形状が読みやすいまま *柔らかい* 見た目になります。  
- **Size** – ぼかしを制御します。値 6 はプロフェッショナルな印象に十分です。  
- **Distance & Angle** – これらが合わせて *オフセット* を定義します。2 pt の 45° で微妙な斜め影が得られます。

これが **影を設定する** 本質です。次に、各要素を分解して **ドロップシャドウを適用**、**透明度を変更**、**ぼかしを調整**、そして **シェイプの影を追加** できるように解説します。

---

## シェイプにドロップシャドウを適用する

「C# で**ドロップシャドウを適用**する方法は？」と質問されると、多くの場合は可視化フラグと色だけが必要です。以下のスニペットはその 2 行だけを抽出しています。

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** 古い Word バージョン（2003‑2007）を対象にする場合は標準色に留めてください。レガシーレンダラでは一部の特殊な ARGB 値が無視されることがあります。

---

## 影の透明度を変更する方法

透明度は **0 から 1 の間の float** で表現します。**0** は完全に不透明な影、**1** は見えなくなります。自然な見た目のために多くのデザイナーは **0.2‑0.4** の範囲で設定します。

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### エッジケース

- **Negative values** – Aspose.Words は 0 にクランプしますが、入力は事前に検証した方が良いです。  
- **Values > 1** – 1 にクランプされ、実質的に影が非表示になります。  

ユーザーにパーセンテージで選択させる場合は、まず変換してください：

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## 影のぼかし（サイズ）を調整する方法

**Size** プロパティはぼかし半径を制御します。数値が大きいほど、柔らかく拡散した影になります。単位はポイント（pt）で、ピクセルではありません。

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### 小さなぼかしと大きなぼかしの使い分け

- **Small blur (2‑4 pt)** – 鮮明なエッジが欲しい UI スタイルのコールアウトに最適です。  
- **Large blur (8‑12 pt)** – 印刷レポートやシェイプが背景から離れている場合に効果的です。

---

## シェイプの影を追加 – 位置と方向

**シェイプの影を追加**する最終要素はオフセットです。2 つのプロパティが連携します：

| プロパティ | 意味 |
|----------|---------|
| **Distance** | 影がシェイプからどれだけ離れているか（ポイント単位）。 |
| **Angle** | オフセットの方向（0° = 右、90° = 下、180° = 左、270° = 上）。 |

右下に微妙な影を作る例：

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

角度を変えて光源の方向をシミュレートできます。一般的なテクニックとして、ユーザーにドロップダウンで「光源」を選ばせ、その値を角度にマッピングする方法があります。

---

## 完全動作サンプル（全ステップ統合）

以下は先ほどと同じプログラムですが、**追加コメント**でロジックを分かりやすくしています。`Program.cs` に貼り付けて実行してください。出力ファイルには完璧に調整された影付きテキストボックスが含まれます。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Expected result:** `output.docx` を開きます。最初のテキストボックスはダークグレーで 30 % 透明な影が表示され、若干ぼかし（size = 6）され、2 pt の 45° オフセットが適用されています。この効果は控えめながらも目立ち、ほとんどの UI デザイナーが目指すものと一致します。

---

## よくある質問と落とし穴

- **“画像でも同様に機能しますか？”**  
  はい。`Shape` であればテキストボックス、画像、オートシェイプのいずれでも `ShadowFormat` が利用可能です。シェイプ取得ロジックを適切なインデックスまたは名前に置き換えるだけで OK です。

- **“文書に複数のシェイプがある場合は？”**  
  `doc.GetChildNodes(NodeType.Shape, true)` をループして同じ設定を各シェイプに適用します。`shape.Name` や `shape` でフィルタリングすることも可能です。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}