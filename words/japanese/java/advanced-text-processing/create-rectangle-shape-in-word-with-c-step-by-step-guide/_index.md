---
category: general
date: 2026-03-04
description: Learn how to create rectangle shape, add shadow to shape and apply shadow
  effect in a Word document, then save Word document automatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: ja
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: Wordで長方形の図形を作成 – 完全なC#チュートリアル
tags:
- C#
- Aspose.Words
- Document Automation
title: C#でWordに長方形の図形を作成する – ステップバイステップガイド
url: /ja/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で Word に矩形シェイプを作成 – 完全プログラミングチュートリアル

Word ファイルに **create rectangle shape** を作成したいけれど、どこから始めればいいか分からないことはありませんか？同じ壁にぶつかる開発者は多いです。嬉しいことに、数行の C# で矩形を挿入し、**add shadow to shape** と **apply shadow effect** を Word を開かずに実行できます。このガイドでは、**create blank document** から最終的な **save word document** をディスクに保存するまでの全工程を順を追って解説します。

必要な NuGet パッケージ、正確な API、各プロパティの意味、そしてよくある落とし穴を回避するコツをすべて網羅します。最後まで読めば、任意の .NET プロジェクトにすぐ組み込める実行可能サンプルが手に入ります。

## 前提条件

- .NET 6.0 以降（.NET Framework 4.7+ でも動作します）
- Visual Studio 2022 またはお好みの IDE
- **Aspose.Words for .NET** を NuGet でインストール (`Install-Package Aspose.Words`)
- C# の基本的な構文に慣れていること

追加の Word Interop ライブラリは不要です—Aspose.Words がメモリ上ですべて処理します。

## Step 1 – Create a blank document

最初に **create blank document** を行います。これは後で **create rectangle shape** を配置する空のキャンバスです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Why this matters:** Starting with a clean `Document` object guarantees that no hidden styles or sections interfere with the shape positioning later on.

## Step 2 – Insert a rectangle shape into the document

いよいよ **create rectangle shape** を実行します。サイズ、位置を設定し、テキストの回り込みを無効にします。

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tip:** If you need the rectangle to sit inside a table cell, change `WrapType` to `WrapType.Inline`. For most reports, `None` keeps the shape floating above the text.

## Step 3 – Add shadow to shape and configure its appearance

ここで魔法がかかります。**add shadow to shape** し、**apply shadow effect** を設定します。影を付けることで、印刷時にも矩形が際立ちます。

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Why these values?**  
> - **BlurRadius** controls how fuzzy the edges appear; a value around `5` gives a subtle, professional look.  
> - **Transparency** lets the underlying text remain readable.  
> - **OffsetX/Y** move the shadow away from the shape, creating depth.  
> - Using a **blue** tint is just an example—any `System.Drawing.Color` works.

## Step 4 – Add the configured shape to the document body

矩形のスタイル設定が完了したら、**add rectangle shape** をドキュメントの最初のセクションに追加します。これで実際にファイル内にシェイプが配置されます。

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Edge case:** If your document already contains sections, you may want to target a specific one (`doc.Sections[2]` for example). The code above works for a single‑section document, which is common for quick reports.

## Step 5 – Save the Word document

最後に **save word document** をディスクに保存します。これで影付き矩形が含まれたファイルが完成し、Microsoft Word で開くことができます。

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tip:** Use `doc.Save(outputPath, SaveFormat.Docx)` if you need to be explicit about the format. The `Save` method automatically detects the extension, but being explicit can avoid confusion when the path is generated programmatically.

## Full, Runnable Example

以下はコンソール アプリケーションにそのまま貼り付けて実行できる完全プログラムです。`using` 文と `Main` メソッドを含んでいるので、すぐに動作させられます。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Expected Result

*shadowed_rectangle.docx* を Microsoft Word で開くと、1 ページ目の上部付近に青い枠線の矩形が浮かび上がり、右下に 8 pt シフトした柔らかい青い影が付いているのが確認できます。`WrapType.None` を設定したため、余分なテキストは回り込んでいません。

## Frequently Asked Questions & Variations

| Question | Answer |
|----------|--------|
| **Can I change the shape to an ellipse?** | Yes—replace `ShapeType.Rectangle` with `ShapeType.Ellipse`. All shadow properties remain the same. |
| **What if I need multiple shapes?** | Simply repeat Steps 2‑4 for each new `Shape` instance, adjusting `OffsetX/Y` or `Left/Top` to avoid overlap. |
| **Is there a way to make the shadow color match the shape’s fill?** | Absolutely. Set `rectangle.FillColor` first, then assign `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **How do I insert the shape into a table cell?** | Use `cell.FirstParagraph.AppendChild(rectangle);` after locating the desired `Cell` object. |
| **Will this work on .NET Core?** | Yes—Aspose.Words is cross‑platform. Just ensure you reference the appropriate NuGet package version for .NET Core/5/6. |

## Common Pitfalls & Pro Tips

- **Pitfall:** Forgetting to set `ShadowFormat.Visible = true`. The shadow properties will be ignored silently.  
  **Fix:** Always enable visibility before tweaking other shadow parameters.

- **Pitfall:** Using a very large `BlurRadius` (e.g., 20) can make the shadow look fuzzy and unprofessional.  
  **Fix:** Stick to values between `3` and `8` for most business documents.

- **Pro tip:** If you need the shape to be selectable later (e.g., for end‑user editing), avoid setting `WrapType.Inline`. Floating shapes (`WrapType.None`) are easier to move around programmatically.

- **Pro tip:** When generating many documents in a loop, reuse a single `Document` instance and call `doc.Clone(true)` for each iteration to improve performance.

## Related Topics You Might Explore Next

- **Add text inside a rectangle shape** – learn how to use `Shape.TextPath` for labels.  
- **Create complex diagrams** – combine multiple shapes, connectors, and grouping.  
- **Export to PDF** – convert the same document to PDF with a single `doc.Save("output.pdf")`.  
- **Apply different fill styles** – gradients, textures, or even pictures inside shapes.

## Conclusion

We’ve just **create rectangle shape**, **add shadow to shape**, and **apply shadow effect** in a Word file using C#. By following the five concise steps you now have a reusable pattern for any document‑automation scenario, and you know how to **save word document** reliably. Feel free to tweak dimensions, colors, or even swap the rectangle for another geometry—Aspose.Words makes it all straightforward.

If you found this tutorial helpful, give it a star on GitHub, or share your own variations in the comments. Happy coding, and may your documents always look as polished as this shadowed rectangle!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}