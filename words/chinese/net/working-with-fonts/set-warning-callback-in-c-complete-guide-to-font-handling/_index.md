---
category: general
date: 2026-02-10
description: 在 Aspose.Words 中设置警告回调，以监控字体更改，同时配置默认字体并设置默认导入字体。了解完整的分步解决方案。
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: zh
og_description: 在配置默认字体和设置默认导入字体时，设置警告回调以监控字体更改。请参阅 Aspose.Words 的完整教程。
og_title: 在 C# 中设置警告回调 – 完整指南
tags:
- Aspose.Words
- C#
- Document Import
title: 在 C# 中设置警告回调 – 字体处理完整指南
url: /zh/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中设置警告回调 – 完整字体处理指南

是否曾在加载 Word 文档时**设置警告回调**，并且想同时*配置默认字体*？你并不孤单。在许多真实项目中——比如自动化报表生成器或文档转换流水线——缺失的字体会悄悄破坏布局，而捕获这些问题的唯一办法是通过警告回调**监控字体更改**。

在本教程中，我们将通过一个动手示例，展示如何**设置警告回调**、**配置默认字体**，甚至**设置默认导入字体**，使用 Aspose.Words for .NET。完成后，你将拥有可直接运行的代码片段，了解每一步的意义，并知道如何针对自定义字体文件夹或静默替换等边缘情况进行调整。

---

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）  
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）  
- 包含备用字体的文件夹（例如 `fonts/Arial.ttf`）  
- 对 C# 控制台应用有基本了解  

无需其他库。

---

## 第一步：创建 LoadOptions 并**配置默认字体**

当你想控制字体处理时，首先需要构建一个 `LoadOptions` 实例。该对象告诉 Aspose.Words 在导入期间如何处理缺失的字体。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**为什么重要：**  
如果源文档引用了服务器上未安装的字体，Aspose.Words 会查找你提供的文件夹。这正是**设置默认导入字体**的核心——你显式告诉库在任何警告触发之前去哪里寻找替代字体。

---

## 第二步：**设置警告回调**以**监控字体更改**

Aspose.Words 在需要替换字体等情况下会触发 `WarningInfoCollection`。通过附加处理程序，你可以记录或响应每一次替换。

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**为什么重要：**  
仅**配置默认字体**不足以审计实际被替换的字体。回调提供实时日志，满足**监控字体更改**的需求，并帮助你在 CI 流水线中提前捕获意外的替代。

---

## 第三步：使用准备好的选项加载文档

现在 `LoadOptions` 已完全准备好，你可以安全地加载任意 `.docx` 文件。若发生替换，回调会自动触发。

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**你将看到的结果：**  
如果源文档使用了不存在的字体，控制台会打印类似以下内容：

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

该输出确认你已成功**设置警告回调**，且**默认导入字体**已生效。

---

## 第四步：（可选）微调字体替换行为

有时你可能希望将*所有*缺失字体统一替换为同一字体族，而不考虑原始请求。Aspose.Words 允许全局设置*回退字体*。

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**何时使用：**  
如果你为品牌生成 PDF，仅允许使用有限的几种字体，这可以确保每个文档保持一致，即使源文档尝试使用奇特字体。

---

## 第五步：保存或进一步处理文档

加载完成后，你可以继续进行任何需要的处理——编辑、转换为 PDF、提取文本等。下面是一个将文档保存为 PDF 并保留已替换字体的快速示例。

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

生成的 PDF 将在每次替换发生的地方显示回退字体，直观地确认**设置警告回调**已按预期工作。

---

## 常见陷阱与专业技巧

| 陷阱 | 产生原因 | 解决方案 |
|------|----------|----------|
| **回调从未触发** | 在加载文档**之前**未为 `LoadOptions.WarningCallback` 赋值。 | 始终在调用 `new Document(...)` **之前**附加回调。 |
| **字体文件夹错误** | 路径拼写错误或缺少读取权限。 | 确认文件夹存在且应用拥有 `Read` 权限。为可靠起见使用绝对路径。 |
| **多次替换，输出噪声大** | 大文档缺失字体较多。 | 按 `WarningType.FontSubstitution` 过滤警告（如示例所示），或将其写入日志文件而非控制台。 |
| **回退字体未生效** | 回退字体未放置在机器上。 | 将 `.ttf`/`.otf` 文件放入传给 `SetFontsFolder` 的文件夹中。Aspose.Words 会直接加载，无需系统安装。 |

**专业技巧：** 在 CI/CD 流水线中运行时，将控制台输出重定向为构建产物。这样即可保留每次构建期间所有字体替换的审计记录。

---

## 完整可运行示例（复制‑粘贴即用）

下面是可以直接放入新 Console App 项目的完整程序。它包含所有步骤、using 语句以及必要的注释。

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**预期的控制台输出**（假设缺少 `Times New Roman`）：

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

运行程序，打开 `output.pdf`，即可看到文档在所有需要的地方使用了回退字体进行渲染。

---

## 结论

现在你已经掌握了一套稳健、可投入生产的模式，能够在 C# 中**设置警告回调**、**配置默认字体**、**监控字体更改**，以及在使用 Aspose.Words 时**设置默认导入字体**。通过在加载前附加警告收集器、将 `FontSettings` 指向可靠的字体文件夹，并可选地强制全局回退，你获得了对字体替换的完整可视化与控制——这正是任何强大文档处理流水线所必需的。

想更进一步？尝试将此方法与以下方案结合：

- **从数据库动态加载字体**（在运行时使用 `FontSettings.SetFontsFolder`）。  
- **自定义警告处理器**，将信息写入结构化日志（JSON 或 CSV）以供分析。  
- **并行文档处理**，为每个线程创建独立的 `LoadOptions`，避免相互干扰。

欢迎实验、根据自身架构进行改造，并在评论区分享你的发现。祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}