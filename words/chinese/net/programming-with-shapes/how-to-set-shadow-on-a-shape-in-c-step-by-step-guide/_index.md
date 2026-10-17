---
category: general
date: 2026-04-10
description: 如何在 C# 中为形状设置阴影——学习如何使用 Aspose.Words 应用投影阴影、更改透明度、调整模糊以及添加形状阴影。
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: zh
og_description: 如何在 C# 中为形状设置阴影——本教程展示了如何应用投影阴影、更改透明度、调整模糊以及添加形状阴影，并提供清晰的代码示例。
og_title: 如何在 C# 中为形状设置阴影 – 完整指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 如何在 C# 中为形状设置阴影 – 步骤指南
url: /zh/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中为形状设置阴影 – 完整指南

是否曾经想过在以编程方式构建 Word 文档时，**如何设置阴影**？你并不孤单。许多开发者在需要为文本框、徽标或标注框添加细腻的投影时会卡住，而 API 文档又显得有些薄弱。  

在本教程中，我们将完整演示整个过程：从加载 `.docx`、获取第一个 `Shape`，到应用投影、调整透明度、修改模糊半径，最后将其精准定位。完成后，你将拥有一个可复用的代码片段，适用于 Aspose.Words .NET 2023 或更高版本，并且能够理解每个属性为何重要。

## 所需条件

- **Aspose.Words for .NET**（NuGet 包 `Aspose.Words`）——提供 `Document`、`Shape` 和 `ShadowFormat` 类的库。  
- **.NET 6+**（或 .NET Framework 4.7.2）——任何近期的运行时都可以。  
- 一个简单的 Word 文件（`input.docx`），其中已经包含至少一个形状，例如文本框。  
- Visual Studio、VS Code 或你喜欢的 IDE。

就是这样。无需额外的第三方工具，无需 COM 互操作，仅使用纯 C#。

![how to set shadow example](image-placeholder.png){:alt="在 Word 文档中为形状设置阴影示例"}

## 设置阴影概述

**如何设置阴影** 的核心思路是操作附属于 `Shape` 的 `ShadowFormat` 对象。可以把 `ShadowFormat` 看作是阴影的微型“样式表”：它告诉渲染器阴影是否可见、颜色是什么、透明度是多少、模糊程度如何，以及相对于形状的定位位置。  

下面是*完整*的可运行程序。可以随意复制粘贴到控制台应用中，按 **F5**，即可在生成的 `output.docx` 中看到阴影效果。

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

### 为什么这些设置很重要

- **Visible** – 如果不打开此标志，其他所有属性都会被忽略。  
- **Color** – 深灰色模拟典型的 UI 投影；你可以替换为任意 `Color`。  
- **Transparency** – 0.3 能产生*柔和*的外观，同时保持形状可辨认。  
- **Size** – 控制模糊程度；数值 6 通常足以获得专业感。  
- **Distance & Angle** – 两者共同定义*偏移*；2 pt、45° 可产生细腻的对角阴影。

这就是 **如何设置阴影** 的要点。接下来，我们将逐一拆解每个环节，以便你能够单独 **应用投影**、**更改透明度**、**调整模糊**，以及 **为形状添加阴影**。

---

## 为形状应用投影

当有人问“如何在 C# 中 **apply drop shadow**？”时，他们通常只需要打开可见性开关并设置颜色。下面的代码片段仅包含这两行：

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **专业提示：** 如果你的目标是较旧的 Word 版本（2003‑2007），请使用标准颜色。某些特殊的 ARGB 值可能会被旧版渲染器忽略。

---

## 如何更改阴影的透明度

透明度以 **0 到 1 之间的浮点数** 表示。**0** 表示完全不透明的阴影；**1** 则使其不可见。大多数设计师会在 **0.2‑0.4** 左右取值，以获得自然的效果。

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### 边缘情况

- **Negative values** – Aspose.Words 会将其限制为 0，但最好先验证输入。  
- **Values > 1** – 会被限制为 1，从而实际上隐藏阴影。  

如果需要让用户选择百分比，请先进行转换：

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## 如何调整阴影的模糊（Size）

`**Size**` 属性控制模糊半径。数值越大，阴影越柔和、越散。它的单位是点（pt），而非像素。

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### 何时使用小模糊 vs. 大模糊

- **Small blur (2‑4 pt)** – 适用于 UI 风格的标注，需要清晰边缘的情况。  
- **Large blur (8‑12 pt)** – 适合打印报告或形状与背景距离较远的场景。

---

## 为形状添加阴影 – 定位与方向

**add shape shadow** 的最后一步是偏移。两个属性协同工作：

| 属性 | 含义 |
|----------|---------|
| **Distance** | 阴影距离形状的距离（单位：点）。 |
| **Angle**    | 偏移的方向（0° = 向右，90° = 向下，180° = 向左，270° = 向上）。 |

下面的示例创建了一个细腻的右下角阴影：

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

你可以尝试不同的角度来模拟光源的方向。常见的技巧是让用户从下拉框中选择“光源”，并将其映射为相应的角度值。

---

## 完整工作示例（所有步骤合并）

下面是与前面相同的程序，但添加了 **额外注释**，使逻辑一目了然。将其复制到 `Program.cs` 并运行；输出文件将包含一个阴影调校完美的文本框。

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

**预期结果：** 打开 `output.docx`。第一个文本框将显示深灰色、30 % 透明度的阴影，略有模糊（size = 6），并在 45° 方向上偏移 2 pt。效果细腻而显著——正是大多数 UI 设计师所追求的。

---

## 常见问题与注意事项

- **“这也适用于图片吗？”**  
  是的。Any `Shape`—whether a textbox, picture, or auto‑shape—exposes `ShadowFormat`. Just replace the shape retrieval logic with the appropriate index or name.

- **“如果文档中有多个形状怎么办？”**  
  Loop through `doc.GetChildNodes(NodeType.Shape, true)` and apply the same settings to each. You can also filter by `shape.Name` or `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}