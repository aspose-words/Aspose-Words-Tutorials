---
category: general
date: 2026-04-04
description: 了解如何使用 Aspose.Words 的 LoadOptions 在 C# 中捕获警告、检测缺失字体以及记录替换事件。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: zh
og_description: 如何使用 Aspose.Words LoadOptions 在 C# 中捕获警告、检测缺失字体以及记录替换事件。
og_title: 如何捕获 C# 警告 – 检测缺失字体并记录替换
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: 如何在 C# 中捕获警告——检测缺失字体并记录替换
url: /zh/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中捕获警告 – 检测缺失字体并记录替换

是否曾经好奇在加载缺少字体的 Word 文档时弹出的 **如何捕获警告**？你并不孤单。在许多真实项目中，字体在迁移过程中会丢失，静默的替代会破坏布局。好消息是？Aspose.Words 为你提供了一种简洁的方式来监听这些警告、检测缺失的字体，甚至记录每一次替换，以便后续修复源文件。

在本教程中，我们将逐步演示一个完整、可直接运行的解决方案，展示 **如何捕获警告**、演示 **检测缺失字体**，并解释 **如何记录替换** 事件。完成后，你将拥有可复用的警告处理器、完整配置的 `LoadOptions` 对象，以及可验证的示例控制台输出。

> **先决条件：** 需要通过 NuGet 安装 Aspose.Words for .NET（v24.x 或更高），并具备基本的 C# 开发环境（Visual Studio 2022 或 VS Code 均可）。

---

## 加载文档时如何捕获警告

解决方案的核心是实现 `IWarningCallback` 接口的类。Aspose.Words 会在文档加载期间自动调用此回调，以处理生成的每个警告，包括字体替换警告。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **为什么需要这一步？**  
> 通过对 `WarningType.FontSubstitution` 进行过滤，我们可以避免与问题无关的警告（如已弃用的功能）干扰日志，使日志专注于你关心的核心问题——缺失字体。

---

## 使用 Aspose.Words 检测缺失字体

当文档引用的字体未在机器上安装时，Aspose.Words 会替换为最接近的匹配并抛出警告。上面的处理器会捕获每一次出现，从而有效 **检测缺失字体**。

要看到实际效果，需要配置 `LoadOptions` 并附加处理程序：

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **提示：** 如果你想收集警告以便后续处理（例如写入文件），请将 `Console.WriteLine` 替换为将消息添加到 `List<string>` 的代码。

---

## 如何记录替换事件

日志记录只需将警告输出定向到持久存储即可。下面是一个快速示例，将每条字体替换警告写入名为 `font-warnings.log` 的文本文件。

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **为什么要记录到文件？**  
> 持久化日志可以让你在多次运行中审计字体问题、自动化警报，或将数据输入构建流水线检查。

---

## 完整工作示例

把所有内容组合在一起，这里提供一个可复制、粘贴并直接运行的独立控制台应用程序。它演示了 **如何捕获警告**、**检测缺失字体**，以及 **如何记录替换**，一次完成。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### 预期的控制台输出

如果 `input.docx` 引用了未安装的字体，你会看到类似如下的输出：

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

如果你切换到 `FileLoggingWarningHandler`，相同的行将带时间戳出现在 `font-warnings.log` 中。

![如何捕获警告的控制台输出](image-placeholder.png)

---

## 常见问题与边缘情况

### 如果我需要捕获 *所有* 警告，而不仅仅是字体替换怎么办？

只需删除 `if (info.Type == WarningType.FontSubstitution)` 检查。回调将收到每种警告类型（`WarningType.DegradedDocument`、`WarningType.UnexpectedContent` 等），你可以根据 `info.Type` 对不同情况进行分支处理。

### 这适用于 PDF 还是仅限 Word 文档？

`LoadOptions` 和 `IWarningCallback` 是 Aspose.Words 的一部分，适用于 Word 兼容格式（`.docx`、`.doc`、`.rtf`、`.html`）。对于 PDF，需要使用 Aspose.PDF 自身的警告机制。

### 如何抑制警告而不是记录它们？

将 `LoadOptions.WarningCallback = null`，或实现回调但保持方法体为空。库仍会静默完成字体替换。

### 线程安全性如何？

回调实例在加载文档的同一线程上被调用，因此除非在并行加载中共享处理器，否则无需额外同步。如果确实跨线程共享，请使用锁或并发集合来保护共享资源（例如日志文件）。

---

## 结论

我们已经介绍了如何从 Aspose.Words **捕获警告**，展示了 **检测缺失字体** 的方法，并解释了 **记录替换** 事件以便后续分析。只需将一个简单的 `IWarningCallback` 实现插入 `LoadOptions`，即可在不污染代码库的前提下全面掌握字体相关问题。

下一步？尝试扩展日志记录器以发送邮件、集成 Azure Monitor，或在构建服务器上自动安装缺失的字体。你也可以探索其他警告类型——`WarningType.DegradedDocument` 能提醒你哪些功能在转换过程中未能保留。

对字体处理或 Aspose.Words 有更多疑问？在 Aspose 论坛留下评论或新建议题。祝编码愉快，愿你的文档始终使用正确的字体！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}