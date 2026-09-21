---
category: general
date: 2026-01-14
description: 在使用 Aspose.Words 加载 Word 文档时记录字体替换警告。学习如何检测缺失的字体以及在 C# 中捕获缺失字体的方法。
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: zh
og_description: 在使用 Aspose.Words 加载 Word 文档时记录字体替换警告。了解如何检测缺失的字体并在 C# 中捕获缺失的字体。
og_title: 记录字体替换警告 – 完整的 Aspose.Words 指南
tags:
- Aspose.Words
- C#
- Document Processing
title: 记录字体替换警告 – 完整的 Aspose.Words 指南
url: /zh/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 日志字体替换警告 – 完整的 Aspose.Words 指南

在需要确保 Word 文档在 Aspose.Words 加载后外观完全一致时，记录字体替换警告至关重要。如果你曾想了解如何 **detect missing fonts** 或想知道 **how to capture missing fonts**，那么你来对地方了。  

在本教程中，我们将通过一个真实场景，展示完整的 C# 代码，并解释每行代码的意义。完成后，你将能够记录每一次字体替换事件并采取相应措施——不再有神秘的警告。

![日志字体替换警告示例](/images/font-warnings.png "显示日志字体替换警告控制台输出的截图")

## 您将学习

- 如何配置 `LoadOptions` 使 Aspose.Words 为字体替换抛出类型化警告。  
- 在文档加载期间执行 **detect missing fonts** 的确切步骤。  
- 一种简洁的方法 **capture missing fonts** 并将其写入您自己的日志或监控系统。  
- 边缘情况处理（例如，文档包含服务器上未安装的字体）。  

### 前提条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6 及以上）。  
- 有效的 Aspose.Words for .NET 许可证（或免费试用版）。  
- 对 C# 和控制台应用程序有基本了解。

如果你已经具备这些条件，让我们开始吧。

## 步骤 1 – 设置 LoadOptions 以抛出类型化警告

解决方案的核心在于 `LoadOptions.FontSubstitutionWarning`。将其切换为 `RaiseTypedWarnings`，即可告诉 Aspose.Words 在每次找不到所请求的精确字体时触发事件 **every time**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **为什么这很重要：**  
> 默认行为是悄悄将缺失的字体替换为最接近的匹配，这可能导致你未预料到的布局错误。抛出类型化警告可以让你全面可见。

## 步骤 2 – 订阅警告事件

现在我们挂钩到 `loadOptions.FontSubstitutionWarning`。lambda 接收一个 `e` 对象，告诉我们缺失的字体以及使用的替代字体。

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **专业提示：** 如果在 Web 服务器上运行，请将 `Console.WriteLine` 替换为结构化日志记录器（Serilog、NLog 等），以便以后查询数据。

## 步骤 3 – 使用配置好的选项加载文档

在启用警告机制后，像往常一样加载文档即可。每当缺失字体时，事件会自动触发。

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### 预期的控制台输出

如果 `input.docx` 引用了一个未安装的字体 *MyFancyFont*，你会看到：

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

每行对应一次 **detect missing fonts** 事件，为你提供完整的审计轨迹。

## 步骤 4 – 处理边缘情况和高级场景

### 4.1 当没有发生替换时

有时文档仅使用已存在的系统字体。在这种情况下，警告事件不会触发，控制台将保持空白。这是个好迹象——你的环境已经拥有所有必需的字体。

### 4.2 捕获警告以供后续分析

如果需要将警告存储用于每夜报告，可将它们收集到列表中：

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

加载完成后，你可以将 `missingFonts` 序列化为 JSON，写入数据库，或通过电子邮件发送摘要。

### 4.3 处理 PDF 或其他格式

相同的 `LoadOptions` 方法同样适用于对 PDF、RTF 甚至 HTML 文件的 `Load` 调用。只需传入相同的选项实例，Aspose.Words 将对任何无法匹配的字体抛出警告。

## 步骤 5 – 以编程方式验证结果

如果你更倾向于使用自动化测试而不是肉眼观察控制台，可断言列表包含预期条目：

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

此代码片段演示了在代码中 **how to capture missing fonts**，而不仅仅是记录日志。

## 常见陷阱及规避方法

| 陷阱 | 产生原因 | 解决方案 |
|------|----------|----------|
| 忘记设置 `RaiseTypedWarnings` | 默认是 `DoNotRaise`，因此不会触发事件。 | 如步骤 1 所示，显式设置 `FontSubstitutionWarning`。 |
| 在 Web 应用中使用 `Console.WriteLine` | 在 IIS/ASP.NET Core 中控制台输出会消失。 | 切换到持久化日志记录器（例如 Serilog）。 |
| 使用相对路径加载文档 | 运行时工作目录可能不同。 | 使用绝对路径或 `Path.Combine(AppContext.BaseDirectory, "input.docx")`。 |
| 忽略 `SubstitutedFontName` | 失去对所选替代字体的了解。 | 始终记录 `FontName` 和 `SubstitutedFontName`。 |

## 额外内容：自动化字体安装

如果你可以控制部署环境，可以使用 PowerShell 脚本预先安装缺失的字体：

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

在应用程序启动前运行此脚本，可彻底消除大多数 **detect missing fonts** 警告。

## 结论

我们已经介绍了在使用 Aspose.Words 加载 Word 文档时 **log font substitution warnings** 所需的全部内容。通过配置 `LoadOptions`、订阅警告事件并可选地持久化结果，你可以可靠地 **detect missing fonts** 并了解 **how to capture missing fonts**，适用于任何 .NET 项目。

拿到代码后，根据你的技术栈调整日志记录器，你将不再被静默的字体替换所惊讶。接下来的步骤可能包括：

- 将警告列表集成到 CI/CD 流水线中，以在关键字体缺失时使构建失败。  
- 将此方法扩展到监控整批文档的字体使用情况。  
- 探索 Aspose.Words 的 `FontSettings` API，以提供自定义的回退字体。

有问题或遇到棘手的情况？留下评论，让我们一起排查。祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}