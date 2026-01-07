---
category: general
date: 2026-01-06
description: 学习如何在加载文档时获取警告以及使用 Aspose.Words 监控字体。本指南涵盖警告回调和字体替换跟踪。
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: zh
og_description: 如何在 Aspose.Words 中获取警告？请按照本分步教程，在加载文档时监控字体并捕获替换信息。
og_title: 如何在 Aspose.Words 中获取警告 – 监视字体
tags:
- Aspose.Words
- C#
- Font Monitoring
title: 如何在 Aspose.Words 中获取警告 – 在 C# 中监控字体
url: /zh/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中获取警告 – 在 C# 中监控字体

是否曾好奇当 Word 文档包含您未安装的字体时，**如何获取警告**？这是一种常见的困扰——您的应用会悄悄替换缺失的字体，而您却不知道发生了什么变化。好消息是，您可以接入 Aspose.Words 的警告系统，实时**监控字体**。

在本教程中，我们将向您展示如何捕获这些字体替换警告、其重要性以及获取信息后该如何处理。无需外部文档，只需一个完整、可运行的示例，您可以立即粘贴到 Visual Studio 中。

> **专业提示：** 如果您正在构建文档转换流水线，提前记录缺失的字体可以避免后续出现糟糕的布局意外。

## 您需要的条件

- **Aspose.Words for .NET**（最新版本；自 v23.10 起 API 未变）
- 一个 .NET 开发环境（Visual Studio、Rider 或带 C# 扩展的 VS Code）
- 一个引用了您未安装字体的示例 `.docx`（例如 **“NonExistentFont”**）

就这些——除了 Aspose.Words 外无需额外的 NuGet 包。

## 步骤1 – 设置警告收集器（标题中的主要关键词）

您首先需要一个在警告发生时存储它们的地方。Aspose.Words 在 `LoadOptions` 上提供了 `WarningCallback` 属性，正是为此而设。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**为何重要：**  
当库遇到缺失的字体时，它不会抛出异常，而是发出一个 `WarningInfo` 对象。通过连接收集器，您可以完整地看到每一次替换事件，从而在不让控制台被无关信息污染的情况下**监控字体**。

## 步骤 2 – 使用启用警告的选项加载文档

现在我们实际读取文件。前一步准备的 `LoadOptions` 确保捕获所有与字体相关的警告。

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**内部发生了什么？**Aspose.Words 解析 Word 文件，解析字体；每当找不到请求的字体时，它会回退到替代字体（通常是 Arial）。此回退会触发 `WarningType.FontSubstitution` 警告，并进入 `warningCollector`。

## 步骤 3 – 检查收集的警告（再次出现主要关键词）

文档加载完成后，我们只需遍历 `warningCollector` 并打印出所有字体替换信息。

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**预期输出**（假设缺失的字体是 *“FancyScript”*）：

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

如果文档包含多个未知字体，您将看到每个替换对应一行——非常适合日志记录或警报。

## 步骤 4 – 可选：记录或持久化警告信息

在生产环境中，您可能比Console.WriteLine` 更强大的功能。下面是一个快速示例，将警告写入 JSON 文件以供后续分析。

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

现在您拥有了永久记录，可将其导入监控仪表盘，甚至触发对缺失字体文件的自动请求。

## 步骤 5 –证结果并清理

运行程序。如果看到替换信息，说明您已成功**获取警告**并正在主动**监控字体**。如果没有任何输出，请再次确认测试文档确实引用了机器上未安装的字体。

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

计数为零通常意味着以下两种情况之一：

1. 所有字体都已解析（可能该字体已在本地安装），或
2. 文档未包含需要替换的字体引用。

## 常见陷阱及规避方法

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **未出现警告** | 字体实际上已在系统中存在，或文档仅使用内置字体。 | 将源文件中的字体重命名为不可能的名称（例如 `XYZ123`），然后重新尝试。 |
| **警告过多（噪声）** | 在循环中加载许多文档而未清空收集器。 | 为每个文档重新实例化 `WarningInfoCollection`，或在处理后调用 `warningCollector.Clear()`。 |
| **性能影响** | 过度写入磁盘日志会减慢批处理速度。 | 在内存中缓冲警告并批量写入，或使用异步文件 I/O。 |
| **缺少 `using Aspose.Words.Loading;`** | `LoadOptions` 类位于该命名空间。 | 添加缺失的 `using` 指令，如步骤 1 所示。 |

## 扩展方案 – 监控其他警告类型

虽然字体替换是最直观的，Aspose.Words 还能针对以下情况发出警告：

- **已弃用的功能** (`WarningType.Deprecated`),
- **可能的数据丢失** (`WarningType.DataLoss`),
- **不受支持的文件格式** (`WarningType.UnsupportedFileFormat`).

您可以在步骤 3 中扩大过滤范围，以捕获这些警告：

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

这样，您不仅能够**监控字体**，还能**获取警告**，以应对应用程序可能遇到的任何场景。

## 完整可运行示例（复制粘贴即可）

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**运行它：** 构建项目并执行，您将看到警告被打印并保存。这就是使用 Aspose.Words **获取警告**和**监控字体**的完整答案。

## 结论

您现在了解了如何从 Aspose.Words **获取警告**，尤其是针对字体替换场景，并且已经学会了在文档加载过程中 **监控字体**。通过附加 `WarningCallback`、遍历收集的 `WarningInfo` 对象，并可选地持久化数据，您可以对缺失字体事件拥有完整的透明度——这是任何文档处理流水线的关键能力。

下一步？尝试将警告过滤器扩展到覆盖数据丢失或已弃用功能的警告，或将 JSON 日志集成到如 Grafana 的监控仪表盘中。同样的模式适用于所有警告类型，让您能够随时关注 Aspose.Words 抛出的任何问题。

祝编码愉快，愿您的文档始终如您所期望的那样渲染！

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}