---
category: general
date: 2026-03-19
description: 使用 Aspose.Words 和可变字体创建 Word 文档。学习如何在 C# 中更改字体粗细、设置字体宽度以及定义字体变体。
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: zh
og_description: 使用 Aspose.Words 创建带可变字体的 Word 文档。本教程展示如何加载字体、修改字体粗细、设置字体宽度以及定义字体变体。
og_title: 使用可变字体创建 Word 文档——完整指南
tags:
- Aspose.Words
- C#
- Variable Font
title: 使用可变字体创建 Word 文档 – 指南
url: /zh/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建带可变字体的 Word 文档 – 指南

是否曾经需要 **创建 word 文档** 使用现代可变字体，但不确定从何入手？你并不孤单。在许多项目中——比如动态报告或品牌一致的宣传册——能够实时 **更改字体粗细** 是一个真正的游戏改变者。  

在本教程中，我们将完整演示整个过程：从将可变字体加载到 Aspose.Words、设置其粗细和宽度，最后保存一个外观完全符合设计的 DOCX。没有模糊的引用，只有可以直接放入 C# 项目中的具体代码。

## 您将学习的内容

- 如何使用 `FontSettings` **加载可变字体** 文件到 Aspose.Words。  
- 用于 **定义字体变体** 轴的语法，例如 `wght`（粗细）和 `wdth`（宽度）。  
- 在单个 `Run` 上 **设置字体宽度** 和 **更改字体粗细** 的方法。  
- 排查常见问题的技巧（缺失字形、文件夹路径错误等）。  
- 一个完整的、可运行的示例，您可以直接复制粘贴并立即测试。

> **先决条件**：.NET 6+（或 .NET Framework 4.6+），通过 NuGet 安装 Aspose.Words for .NET，并将类似 *RobotoFlex.ttf* 的可变字体文件放置在本地 *Fonts* 文件夹中。

---

## 步骤 1 – 将可变字体加载到 Aspose.Words

首先，我们必须告诉 Aspose.Words 去哪里寻找自定义字体。`FontSettings` 类负责完成这项工作。  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**为什么这很重要**：如果不注册文件夹，Aspose.Words 会回退到系统字体，并且会忽略后续尝试应用的任何 OpenType 变体数据。通过指向特定目录，您可以确保每次运行代码时都能找到 *RobotoFlex*（或其他任何可变字体）。

> **专业提示**：如果希望 Aspose 也搜索子文件夹，请将 `SetFontsFolder` 的第二个参数设为 `true`。这在您按样式或粗细组织字体时非常有用。

---

## 步骤 2 – 创建新文档并添加示例文本

现在字体引擎已经知道去哪里查找，我们创建一个空的 `Document`，并插入一个包含 `Run` 的段落。  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**正在发生的事情**：`Run` 表示一段具有统一格式的连续文本。先创建它可以将格式逻辑隔离——如果以后需要对不同的 `Run` 应用不同的变体轴，这种做法非常方便。

---

## 步骤 3 – 定义所需的变体轴（粗细 & 宽度）

可变字体公开了可以在运行时调整的 *轴*。最常用的两个轴是 `wght`（字体粗细）和 `wdth`（字体宽度）。Aspose.Words 使用 `OpenTypeFontVariation` 集合来建模这些轴。

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**为什么是这些数值**：在 OpenType 规范中，`wght` 的取值范围是字体的最小到最大粗细（通常是 100–900）。数值 **700** 对应粗体外观。`wdth` 的工作方式类似；**100** 表示默认（正常）宽度，低于 100 的值会使字形更紧凑。

> **边缘情况**：某些可变字体不支持特定轴。如果提供了不受支持的标签，Aspose 会静默忽略。请务必检查字体的规格（通常在 `.ttf` 或 `.otf` 文件的元数据中可找到）。

---

## 步骤 4 – 使用字体名称将变体应用到 Run

现在我们将变体数据绑定到实际文本。`FontInfo` 类保存字体族名称以及轴集合。

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**说明**：通过设置 `FontInfo`，我们绕过了常规的 `Font.Name` 属性，直接向引擎提供完整的字体配置。这是让 Aspose.Words 使用带自定义轴的可变字体的唯一方式。

> **常见错误**：未能精确匹配字体文件内部的族名称（本例中的 `RobotoFlex`）。拼写错误会导致 Aspose 回退到默认字体，从而失去变体效果。

---

## 步骤 5 – 保存文档并验证结果

最后，将文档写入磁盘。生成的 DOCX 将包含可变字体指令，Microsoft Word（2016 及以上）能够正确渲染。

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

在 Word 中打开生成的文件，选中该文本并查看 **字体** 对话框。您应该看到 *Roboto Flex* 已列出，且文本比周围内容更粗——正是我们通过 `wght = 700` 设置实现的效果。

> **验证提示**：如果文本看起来没有变化，请再次确认字体文件确实支持 `wght` 轴。有些所谓的“可变”字体仅公开 `ital`（斜体）或 `opsz`（光学尺寸）轴。

---

## 可选：添加更多变体 – 动态更改宽度

如果想为另一段落 **设置字体宽度**，只需使用新的 `OpenTypeFontVariation` 集合重复步骤 3‑4。

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

现在您拥有两个 Run——一个加粗，一个稍宽——演示了在同一文档中同时 **更改字体粗细** 和 **设置字体宽度** 的方法。

---

## 完整可运行示例

将下面的代码片段复制到新的控制台应用程序（`Program.cs`）并运行。确保 `Fonts` 文件夹中包含 `RobotoFlex.ttf`（或您喜欢的任何可变字体）。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**预期输出**：生成一个 `VariableFont.docx` 文件，其中短语 “Variable‑weight text” 因 `wght = 700` 轴而呈现加粗，同时保持默认宽度。

---

## 常见问题 & 边缘情况

| Question | Answer |
|----------|--------|
| *如果找不到字体怎么办？* | 检查文件夹路径，确保文件名匹配，并且进程拥有读取权限。您也可以调用 `fontSettings.GetFonts()` 列出已检测到的字体。 |
| *我可以将多个 Run 与不同的变体组合使用吗？* | 当然可以。每个 `Run` 都可以携带自己的 `FontInfo`。只需对每个 Run 重复步骤 3‑4 即可。 |
| *旧版本的 Word 支持可变字体吗？* | Word 2016（Build 16.0.8001）引入了基本支持。如果目标是更早的版本，文档会回退到该字体的最近静态实例。 |
| *可以设置多少个轴？是否有限制？* | 您可以设置字体定义的任意数量的轴。常见标签包括 `wght`、`wdth`、`ital`、`opsz`、`GRAD`。提供不受支持的标签仅会无效，不会报错。 |
| *如何调试缺失的字形？* | 使用 `FontSettings.GetFontSources()` 检查已加载的字体，使用 `FontInfo.HasGlyph(char)` 测试单个字符是否存在字形。 |

---

## 结论

通过几个简单的步骤，我们展示了 **如何创建利用可变字体的 word 文档**，实现 **更改字体粗细**、**设置字体宽度**、**加载可变字体文件** 与 **定义字体变体轴**，全部使用 Aspose.Words for .NET。  

核心思路很直接：注册字体文件夹、描述所需轴、将其附加到 `Run`，然后保存。从这里您可以将该技术扩展到整段、表格，甚至以编程方式生成品牌专属报告。

**后续建议**：尝试将 `RobotoFlex` 替换为其他可变字体，实验 `ital`（斜体）轴，或使用 Aspose.PDF 生成同一文档的 PDF 版本。相同的模式依然适用——加载、定义、应用、保存。

祝编码愉快，尽情享受可变字体为 Word 自动化项目带来的灵活性吧！  

<img src="variable-font-demo.png" alt="创建带可变字体的 word 文档示例">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}