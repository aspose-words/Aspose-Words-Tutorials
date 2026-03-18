---
category: general
date: 2026-03-17
description: 如何在 C# 中使用 Aspose.Words 和警告回调检测字体。了解如何使用回调在加载文档时捕获缺失字体的替换。
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: zh
og_description: 如何在 C# 中使用 Aspose.Words 检测字体。本指南展示了如何使用回调在加载文档时捕获缺失字体警告。
og_title: 如何在 C# 中检测字体 – 使用 Aspose.Words 的回调
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何在 C# 中检测字体 – 使用 Aspose.Words 的回调
url: /zh/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

translate. The title attribute also contains English; translate. But URLs remain unchanged.

We need to translate headings, bullet points, paragraphs, table content, etc.

Let's produce final content.

Be careful with the table: translate column headers and content, but keep code snippets unchanged.

Also preserve the shortcodes at beginning and end.

Let's start.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中检测字体 – 使用 Aspose.Words 的回调

是否曾经需要**检测 Word 文档中的字体**，并且在转换后发现某些字符显示异常？你并不孤单。在许多实际项目中——发票生成器、报表导出器或批处理流水线——缺失的字体会导致静默的布局错误，难以调试。

好消息是？Aspose.Words 提供了一种简洁的方式，通过警告回调来暴露这些问题。在本教程中，你将学习**如何使用回调**捕获 Aspose 在加载文档时执行的每一次字体替换，并获得一个可直接运行的示例，打印出缺失字体的清晰报告。

我们将覆盖：

* 最小前置条件（一个 .NET 项目和 Aspose.Words NuGet 包）。  
* 如何实现 `IWarningCallback` 来监听 `WarningType.FontSubstitution`。  
* 如何将回调插入 `LoadOptions` 并加载文档。  
* 输出示例，以及一些面向生产环境的实用技巧。

完成后，你将能够自动**检测任何 DOCX、DOC 或 RTF 文件中的字体**并对缺失的字体信息采取行动——无论是记录日志、提醒用户，还是使用后备字体进行替换。

---

![使用 Aspose.Words 警告回调检测 Word 文档中的字体](https://example.com/images/detect-fonts.png "使用 Aspose.Words 警告回调检测 Word 文档中的字体")

## 所需环境

* **.NET 6.0** 或更高版本（示例同样可以在 .NET Framework 4.6+ 上编译）。  
* **Aspose.Words for .NET** – 通过 NuGet 安装：`Install-Package Aspose.Words`。  
* 一个特意引用了你未安装的字体的示例 Word 文件（例如 `MissingFont.docx`）。  

无需其他库；所有内容都在 Aspose 命名空间内部。

---

## 使用警告回调检测字体的步骤

### 步骤 1：创建警告回调类

该回调实现 `IWarningCallback`。当 Aspose.Words 遇到找不到的字体时，会抛出带有 `WarningType.FontSubstitution` 的 `WarningInfo`。我们的类仅向控制台写入一行友好的信息。

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**为何重要：** 通过仅过滤 `WarningType.FontSubstitution`，我们可以避免噪声警告（如已弃用的特性），让日志专注于你想要解决的**检测字体**问题。

---

### 步骤 2：将回调绑定到 `LoadOptions`

`LoadOptions` 允许自定义文档的解析方式。将我们的 `FontWarningCollector` 赋给 `WarningCallback` 属性，即可让 Aspose 在遇到缺失字体时调用它。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**提示：** 你也可以在这里设置 `LoadOptions.FontSettings`，以编程方式提供后备字体。稍后我们会提到这种高级场景。

---

### 步骤 3：加载文档并观察输出

现在真正加载文件。Aspose 解析文档的瞬间，任何找不到的字体都会触发我们的回调。

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**预期的控制台输出**（假设文档引用了未安装的 *Comic Sans MS*）：

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

如果文档包含多个缺失字体，你会看到每个字体对应一行——正是你需要的**检测字体**信息。

---

## 在更复杂场景中使用回调

### 将日志写入文件而非控制台

在生产环境中，你可能需要持久化日志。将 `Console.WriteLine` 替换为 `StreamWriter`：

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### 收集警告以供后续分析

有时你需要在文档加载后获取缺失字体列表，以在 UI 对话框中显示。将警告存入 `List<string>` 并提供访问接口：

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### 编程方式提供后备字体

如果公司有统一的字体需要强制使用，可以在加载前向 `FontSettings` 添加它：

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

现在 Aspose 会用 *Arial Unicode MS* 替代缺失的字体，同时仍通过回调报告替换情况。这是一种将**使用回调**用于检测和自动修复的巧妙方式。

---

## 常见陷阱与专业技巧

| 陷阱 | 产生原因 | 规避方法 |
|--------|----------------|--------------|
| **忘记引用 `Aspose.Words.Warnings`** | `IWarningCallback` 接口位于该命名空间。 | 在文件顶部添加 `using Aspose.Words.Warnings;`。 |
| **未使用 `LoadOptions` 加载文档** | 默认加载器会在没有任何通知的情况下静默替换字体。 | 始终创建 `LoadOptions` 实例并分配你的回调。 |
| **服务器权限受限** | 写入日志文件可能抛出 `UnauthorizedAccessException`。 | 使用可写文件夹（例如应用程序数据目录）或改用内存集合。 |
| **多个线程共享同一收集器** | `FontWarningCollector` 默认不是线程安全的。 | 为每个线程创建独立的收集器，或使用锁保护列表。 |
| **误以为回调会对嵌入字体触发** | 嵌入字体已随文档一起存在，不会产生警告。 | 若需验证嵌入字体完整性，请通过 `FontSettings` 检查 `FontInfo`。 |

---

## 完整可运行示例（复制粘贴即用）

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**你应该看到的结果**（假设文件引用了两个缺失的字体）：

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

如果文件仅使用已安装的字体，控制台只会打印：

```
Document loaded successfully.

No missing fonts detected.
```

---

## 小结

我们已经通过将自定义警告回调接入 Aspose.Words，完整演示了**如何检测 Word 文档中的字体**。这种方法轻量、易于实现，只需

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}