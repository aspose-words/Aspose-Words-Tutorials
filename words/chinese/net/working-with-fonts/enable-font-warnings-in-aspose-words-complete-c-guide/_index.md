---
category: general
date: 2026-04-01
description: 在使用 Aspose.Words 加载 Word 文档时启用字体警告。了解如何使用 C# LoadOptions 和字体设置捕获字体替换事件。
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: zh
og_description: 在使用 Aspose.Words 加载 Word 文档时启用字体警告。本教程展示了如何在 C# 中捕获字体替换事件。
og_title: 在 Aspose.Words 中启用字体警告 – 完整 C# 指南
tags:
- Aspose.Words
- C#
- Font Management
title: 在 Aspose.Words 中启用字体警告 – 完整 C# 指南
url: /zh/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words 中启用字体警告 – 完整 C# 指南

有没有想过为什么在程序化加载 Word 文档后，它会突然显示不同？**启用字体警告**，您将立即知道 Aspose.Words 在缺失字体时何时替换为回退字体。在本教程中，我们将通过一个实战示例，既捕获这些替换，又解释它们发生的*原因*。

我们将覆盖您快速上手所需的一切：必需的 NuGet 包、精确的 `LoadOptions` 配置，以及一个整洁的控制台输出，告诉您哪些字体被替换。完成后，您将拥有一个稳固、可复用的 **C# 文档处理** 模式，适用于任何版本的 Aspose.Words。

## 您将学习

- 如何创建一个跟踪字体更改的 `LoadOptions` 实例。  
- `SubstitutionWarning` 事件的作用以及如何订阅它。  
- 一个完整、可运行的代码示例，能够在控制台打印清晰的警告。  
- 处理边缘情况的技巧，例如仅包含标准字体的文档。  

无需任何 Aspose.Words 经验——只需对 C# 和 .NET 有基本了解。

---

![启用字体警告示意图](placeholder-image.png "启用字体警告示意图")

*Alt text: 启用字体警告示意图，展示缺失字体被替换时的事件流。*

## 步骤 1：设置 LoadOptions 并启用字体警告

您首先需要一个 `LoadOptions` 对象。该容器告诉 Aspose.Words 如何处理即将加载的文件。通过分配一个全新的 `FontSettings` 实例，您即可开启与字体相关的事件。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**为什么这很重要：**  
如果跳过 `FontSettings` 的分配，Aspose.Words 仍会替换缺失的字体，但您不会收到任何通知。警告机制位于 `FontSettings` 中，因此初始化它对我们的目标*至关重要*。

> **专业提示：** 您还可以使用 `SetFontsFolder` 将 `FontSettings` 指向自定义字体文件夹。这会减少您看到的警告数量，因为 Aspose.Words 实际上能够找到缺失的字体。

## 步骤 2：订阅 SubstitutionWarning 事件（字体替换）

现在 `FontSettings` 对象已经存在，我们将其 `SubstitutionWarning` 事件挂钩。该事件在 Aspose.Words 每次将请求的字体替换为其他字体时**触发**。

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**为什么这很重要：**  
如果没有此监听器，您将无法看到替换过程。控制台输出为您提供快速的审计轨迹，这在自动化构建或为合规性要求高的行业生成 PDF 时尤为方便。

> **常见问题：** *如果我想抑制警告怎么办？*  
> 您可以简单地解除处理程序的绑定，或设置 `FontSettings.SubstitutionWarning += null;`。然而，保留警告通常是最安全的做法，因为静默的替换可能导致布局错误。

## 步骤 3：使用配置好的选项加载文档（C# 文档处理）

警告系统准备就绪后，加载文档变得简单。将 `LoadOptions` 实例传递给 `Document` 构造函数，Aspose.Words 将完成其余工作。

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**为什么这很重要：**  
`LoadOptions` 对象是原始文件与警告基础设施之间的桥梁。如果省略它，文档将静默加载，任何缺失的字体都会在没有痕迹的情况下被替换。

> **边缘情况：** 某些文档嵌入了所需的完整字体文件。在这种情况下不会出现警告，因为 Aspose.Words 能找到嵌入的字体。上述代码仍然有效，只是您会看到空的控制台输出。

## 步骤 4：验证输出及常见陷阱

在命令提示符或 IDE 的调试器中运行程序。如果源文档包含机器上未安装（或自定义字体文件夹中不可用）的字体，您将看到类似以下的行：

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

如果没有任何输出，可能是因为：

1. 所有字体都已找到，**或**  
2. `SubstitutionWarning` 处理程序未正确附加（请再次检查步骤 2）。

### 为什么会发生字体替换？

- **缺失系统字体：** 操作系统没有请求的字体。  
- **不受支持的字体格式：** Aspose.Words 能读取 TrueType 和 OpenType，但并非所有专有格式都支持。  
- **许可证限制：** 某些商业字体阻止嵌入，导致使用回退字体。

了解*原因*有助于您决定是随应用一起分发缺失的字体，还是调整文档的样式。

## 额外内容：控制回退字体

如果您希望所有缺失的字体都回退到特定的字体族（例如 “Calibri”），可以设置全局替换规则：

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

现在控制台仍会发出警告，但视觉效果将在所有缺失字体之间保持一致。

---

## 回顾

- **通过创建带有全新 `FontSettings` 的 `LoadOptions` 来启用字体警告。**  
- 挂钩 `SubstitutionWarning` 事件，以在每次字体被替换时获得实时警报。  
- 使用配置好的选项加载文档，并可选择保存为 PDF 以查看视觉效果。  
- 诊断替换发生的原因，如有必要，强制使用特定的回退字体。

您刚刚为 **Aspose.Words** 工作流添加了一个安全网，防止静默的布局更改。接下来，您可以探索诸如 `DefaultFontName` 的 **字体设置**，或深入 **文档渲染** 选项，以微调 PDF 输出。

---

### 接下来可以尝试什么？

- **探索其他 FontSettings 功能**：`SetFontsFolder`、`LoadFontSources` 和 `DefaultFontName`。  
- **将警告与日志框架结合**（Serilog、NLog），以实现生产级诊断。  
- **尝试不同的文档格式**（`.doc`、`.rtf`、`.html`），观察每种格式如何处理缺失字体。

有问题或奇怪的场景？在下方留言吧，祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}