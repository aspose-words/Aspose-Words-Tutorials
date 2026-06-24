---
category: general
date: 2026-06-20
description: 在 C# 中使用 Aspose.Words 启用字体替换警告。了解如何配置 LoadOptions、捕获警告以及高效处理缺失字体。
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: zh
og_description: 在 C# 中使用 Aspose.Words 启用字体替换警告。本指南展示如何设置 LoadOptions、读取 WarningInfo
  并显示缺失字体的消息。
og_title: 在 C# 中启用字体替换警告 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: 在 C# 中使用 Aspose.Words 启用字体替换警告
url: /zh/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 启用字体替换警告

是否曾想过在 Word 文档引用了服务器上未安装的字体时**启用字体替换警告**？你并不是唯一遇到这种情况的人。缺失的字体会悄悄破坏生成的 PDF 或图像的布局，而捕获这些问题的唯一方法就是监听 Aspose.Words 发出的警告。

在本教程中，我们将通过一个动手示例，向你展示如何打开这些警告、从 `WarningInfo` 集合中提取它们，并将有意义的消息打印到控制台。完成后，你将了解如何配置 **Aspose.Words LoadOptions**、处理 **C# 字体替换警告**，以及如何让文档处理流水线保持万无一失。

我们还会涉及一些边缘情况——例如抑制警告会怎样，或者需要将警告记录而不是打印时该怎么做——并提供一段完整的、可直接复制粘贴的代码示例，适用于最新的 Aspose.Words for .NET（截至 24.10 版本）。

## 你需要准备的环境

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）
- 对 `Aspose.Words` 的 NuGet 引用（通过 `dotnet add package Aspose.Words` 安装）
- 一个引用了**未安装**字体的 Word 文件（例如 `DocumentWithMissingFont.docx`）
- 一个不错的 IDE（Visual Studio、Rider 或 VS Code）

就这些——无需额外服务，也不需要专有工具。准备好了吗？让我们开始吧。

## 第一步：启用字体替换警告

首先，需要告诉 Aspose.Words 在替换缺失字体时向你发送通知。这通过 `LoadOptions` 对象的 `FontSettings` 属性实现。默认情况下，警告是**已禁用**的，以保持 API 静默，所以我们必须手动打开开关。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **为什么这样有效：** 当 `FontSettings` 不为 `null` 时，库会自动在加载文档时将所有 `WarningType.FontSubstitution` 条目填充到 `Document.WarningInfo` 中。可以把它看作是为字体打开了一个“调试模式”。

## 第二步：使用已配置的选项加载文档

现在警告集合已经激活，使用我们刚准备好的 `LoadOptions` 加载文档。如果文档中包含缺失的字体，Aspose.Words 会使用回退字体并将警告推入 `WarningInfo` 列表。

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **小技巧：** 如果在循环中处理大量文件，复用同一个 `LoadOptions` 实例——只创建一次可以为每次迭代节省几毫秒。

## 第三步：遍历 WarningInfo 并显示字体替换消息

文档加载完成后，`WarningInfo` 集合保存了加载期间出现的所有警告。我们只关心 `WarningType.FontSubstitution`，因此需要进行过滤。

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

对包含缺失 “Papyrus” 字体的文档运行上述代码片段，可能会得到如下输出：

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

这就是你一直在寻找的**字体替换消息**——清晰、可操作，并且可以直接记录或发送到告警系统。

## 完整工作示例

下面是一个自包含的控制台程序，演示了所有步骤。复制粘贴到新的 `.csproj` 中并点击 **Run** 即可运行。

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### 预期输出

如果文档引用了未安装的字体，你会看到类似以下内容：

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

如果机器上已安装所有字体，程序只会打印：

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## 常见陷阱与高级技巧

| 问题 | 产生原因 | 解决方案 / 避免方式 |
|------|----------|-------------------|
| **警告消失** | 清除了 `FontSettings` 或使用了不包含它的 `LoadOptions`。 | 即使不修改属性，也要实例化 `FontSettings`。 |
| **警告过多** | 文档使用了大量异域字体。 | 通过 `SetFontsFolder` 为 `FontSettings` 添加自定义字体文件夹，以减少替换。 |
| **循环中性能下降** | 每次迭代重新创建 `LoadOptions` 带来开销。 | 在所有文档之间复用同一个 `LoadOptions` 实例。 |
| **控制台没有输出** | 在 GUI 应用中 `Console.WriteLine` 被忽略。 | 将警告重定向到日志记录器（`ILogger`）或写入文件。 |

### 在真实服务中处理警告

在 Web API 中，你可能不想把信息写到控制台。相反，可以将警告写入结构化日志：

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

这样既保留了**文档警告处理**，又保持了服务的整洁。

## 扩展示例

- 通过移除 `if` 过滤，**捕获其他警告类型**（例如 `WarningType.UnknownFileFormat`）。
- 将所有警告导出为 JSON，以供下游分析使用。
- 通过设置 `FontSettings.SubstitutionSettings.DefaultFontName` **强制使用特定回退字体**。

掌握了**启用字体替换警告**后，这些都是自然的扩展。

## 结论

我们已经演示了如何在 C# 中使用 Aspose.Words **启用字体替换警告**，从配置 `LoadOptions` 到遍历 `WarningInfo` 并打印友好消息。按照上述步骤，你可以防止因缺失字体导致的布局悄然变化，从而保障文档处理流水线的可靠性。

接下来，尝试添加自定义字体文件夹、将警告记录到文件，或将其发送到监控仪表盘。相同的模式同样适用于任何**文档警告处理**场景，无论是转换为 PDF、渲染图像，还是执行邮件合并。

对 **C# 字体替换警告** 有疑问或想分享巧妙的解决方案？在下方留言——祝编码愉快！


## 接下来你可以学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助你在实际项目中进一步掌握 API 功能并探索替代实现方案，每篇都提供完整可运行的代码示例和逐步解释。

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}