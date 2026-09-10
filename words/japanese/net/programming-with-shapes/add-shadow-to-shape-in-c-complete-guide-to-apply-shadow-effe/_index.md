---
category: general
date: 2026-02-13
description: C#で形状に素早く影を追加する。影効果の適用方法、影の色の変更方法、そして簡単なコード例で45度の影を作成する方法を学びましょう。
draft: false
keywords:
- add shadow to shape
- apply shadow effect
- change shadow color
- 45 degree shadow
- how to add shadow
language: ja
og_description: C# ですぐに形に影を追加します。このチュートリアルでは、影効果の適用方法、影の色の変更方法、そして 45 度の影の設定方法を示します。
og_title: C#で図形に影を追加 – ステップバイステップの影効果ガイド
tags:
- Aspose.Words
- C#
- Document Automation
title: C#でシェイプに影を追加する – 影効果を適用する完全ガイド
url: /ja/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でシェイプに影を追加する – 完全ガイド

Word 文書で C# を使って **add shadow to shape**（シェイプに影を追加）したいと思ったことはありませんか？ あなただけではありません。多くの開発者が、図を際立たせる微妙なドロップシャドウが必要になったときに壁にぶつかりますが、簡潔で実行可能なサンプルが見つからないことが多いです。  

良いニュースです: 本チュートリアルでは **add shadow to shape** に必要な正確なコードを提供し、各行がなぜ重要かを解説し、効果の調整方法（薄いグレーの霞や太字の 45 ° 影など）を示します。さらに **apply shadow effect**、**change shadow color**、そしてクラシックな **45 degree shadow** シナリオについても触れます。

## 学べること

- DOCX を読み込み、シェイプを特定し、影を有効にする方法  
- 各影プロパティ（可視性、色、透明度、サイズ、距離、角度）の意味  
- すべてのシェイプに対して動的に **apply shadow effect** する方法（ループやグループ化オブジェクトの処理など）  
- **changing shadow color** を安全に行うコツと、シェイプが存在しない文書への対処法  
- 正確な **45 degree shadow** を角度を推測せずに実現する方法  

外部ドキュメントは不要です—コピーして貼り付け、実行するだけです。最後には、任意のシェイプにプロフェッショナルな影を追加するプログラムが完成します。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）  
- Aspose.Words for .NET（無料トライアルまたはライセンス版）。NuGet でインストール: `dotnet add package Aspose.Words`  
- 少なくとも 1 つのシェイプ（例: 長方形や画像）が含まれる基本的な Word ファイル（`input.docx`）  

> **プロのコツ:** シェイプが無い場合は、まず Word で手動で挿入してください。本チュートリアルは最初のシェイプを対象としています。

---

## Step 1: Set Up the Project and Load the Document

まず、コンソール アプリ（または任意の C# プロジェクト）を作成し、Aspose.Words への参照を追加します。その後、影を付けたいシェイプが含まれる DOCX をロードします。

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;          // For Shape and ShadowFormat

class Program
{
    static void Main()
    {
        // Load the Word document that contains the shape.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**Why this matters:** `Document` はすべての Word 処理タスクのエントリーポイントです。ファイルを早期にロードすることで、以降の操作が正しいインメモリ表現に対して行われることが保証されます。

---

## Step 2: Retrieve the Target Shape

次に、変更したいシェイプを特定します。例では最初のシェイプを取得しますが、インデックスを変更したりシェイプタイプでフィルタリングしたりできます。

```csharp
        // Retrieve the first shape in the document (adjust the index if needed).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found. Add a shape to input.docx and try again.");
            return;
        }
```

**Explanation:**  
- `GetChild(NodeType.Shape, 0, true)` は文書ツリーを深さ優先で走査し、最初に見つかったシェイプを返します。  
- `null` チェックは、文書にシェイプが無い場合に `NullReferenceException` が発生するのを防ぐ、初心者が陥りやすいエッジケースです。

---

## Step 3: Turn On the Shadow

シェイプの影はデフォルトで無効化されています。Boolean フラグを切り替えるだけで有効化できます。

```csharp
        // Turn on the shadow effect for the shape.
        targetShape.ShadowFormat.Visible = true;
```

**What’s happening:** `Visible` を `true` に設定すると、Word は影を描画します。この行が無いと、他の影設定を変更しても無視されます。

---

## Step 4: Configure the Shadow’s Appearance

ここで影の外観を定義します。以下のコードは「黒、30 % 透明、5 pt ぼかし、3 pt オフセット、45° 角度」という典型的なスタイルに合わせています。

```csharp
        // Configure the shadow's appearance.
        // • Black color
        // • 30 % transparent
        // • 5 pt blur radius (size)
        // • 3 pt offset distance
        // • 45° direction (angle)
        targetShape.ShadowFormat.Color = Color.Black;          // change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
        targetShape.ShadowFormat.Size = 5;                     // blur radius
        targetShape.ShadowFormat.Distance = 3;                 // offset distance
        targetShape.ShadowFormat.Angle = 45;                   // 45 degree shadow
```

**Why each property matters:**

| Property | Effect | Typical use |
|----------|--------|-------------|
| `Visible` | Turns the shadow on/off | Core to **apply shadow effect** |
| `Color` | Determines the hue of the shadow | Change to gray for subtlety, red for emphasis |
| `Transparency` | 0 = opaque, 1 = fully transparent | 0.3 gives a soft, realistic look |
| `Size` | Controls blur radius (in points) | Larger values create a “feathered” look |
| `Distance` | How far the shadow is offset from the shape | Small distances keep the shape grounded |
| `Angle` | Direction in degrees (0 = right, 90 = up) | 45 gives a classic diagonal drop shadow |

自由に試してみてください。たとえば `Color = Color.Gray` にすれば **change shadow color** がより明るいトーンになり、`Angle = 135` にすれば左下方向の影になります。

---

## Step 5: Save the Modified Document

最後に、変更をディスクに書き戻します。元のファイルを上書きしても、新しいファイルを作成しても構いません。

```csharp
        // Save the document with the new shadow.
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        Console.WriteLine("Shadow added successfully! Check output_with_shadow.docx");
    }
}
```

**Result:** `output_with_shadow.docx` を Word で開き、シェイプを選択すると、45 ° 角度・30 % 透明・ソフトなぼかしが適用された鮮明な黒い影が表示されます。これは UI で手動で影を付けた場合と同じ見た目です。

---

## Bonus: Apply Shadow to All Shapes in a Document

すべてのシェイプに **apply shadow effect** したい場合は、単一ノードを対象にする代わりにコレクションをループします。

```csharp
        // Loop through every shape and add the same shadow.
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Visible = true;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.3;
            shp.ShadowFormat.Size = 5;
            shp.ShadowFormat.Distance = 3;
            shp.ShadowFormat.Angle = 45;
        }
```

**Edge case handling:** WordArt など一部のシェイプは特定のプロパティを無視することがあります。代表的なサンプルで必ずテストしてください。

---

## Visual Confirmation

以下は影が適用されたシェイプのスクリーンショットです。45 ° のオフセットと微妙な透明度に注目してください。

![シェイプに影を追加した例](add-shadow-to-shape.png){: .img alt="シェイプに影を追加した例"}

---

## Frequently Asked Questions

**Q: Can I use a custom color gradient for the shadow?**  
A: Aspose.Words only supports solid colors for `ShadowFormat.Color`. For gradients, you’d need to export the shape as an image and apply a graphic‑level effect.

**Q: What if the document contains grouped shapes?**  
A: Each member of a group is a separate `Shape` node. The loop shown in the “Bonus” section will handle them automatically.

**Q: Does this work with Word 2007‑2019 files?**  
A: Yes. Aspose.Words abstracts the file format, so the same code works for `.doc`, `.docx`, and even `.rtf`.

**Q: How do I make the shadow invisible again?**  
A: Set `targetShape.ShadowFormat.Visible = false;` and re‑save the document.

---

## Conclusion

You now know exactly how to **add shadow to shape** in C#. By toggling `ShadowFormat.Visible` and tweaking color, transparency, size, distance, and angle, you can **apply shadow effect** that matches any design spec—including a precise **45 degree shadow**.  

Whether you’re automating report generation, building a template engine, or just polishing a single diagram, this approach gives you full programmatic control over a shape’s visual depth. Next, try **changing shadow color** based on a theme, or combine this with shape‑fill logic to create dynamic, data‑driven visuals.

Happy coding, and don’t hesitate to experiment—shadows are cheap to add but can dramatically improve readability. If you found this guide useful, share it with teammates or drop a comment with your own tweaks!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}