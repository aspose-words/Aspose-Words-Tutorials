---
category: general
date: 2026-04-07
description: 学习如何检测字体以及在使用 Aspose.Words 处理缺失字体时捕获警告。附带一步步的代码示例。
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: zh
og_description: 如何在 Aspose.Words 中检测字体？请按照本教程轻松捕获警告并处理缺失的字体。
og_title: 如何在 Aspose.Words 中检测字体 – 完整指南
tags:
- Aspose.Words
- C#
- Font handling
title: 如何在 Aspose.Words 中检测字体 – 完整指南
url: /zh/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何检测 Aspose.Words 中的字体 – 完整指南

是否曾经想过 **如何检测字体** 在 Word 文档中缺失，在将其投入生产之前？你并不孤单。在许多企业场景中，偶然的字体缺失会导致 PDF 转换管道中断或出现看起来不专业的布局故障。好消息是，Aspose.Words 为你提供了内置的方式来嗅探这些缺失的字体并显示明确的警告。

在本教程中，我们将逐步演示 **如何检测字体**、**如何捕获警告**，以及处理缺失字体的最佳实践，以确保你的应用保持稳健。无需外部工具，无需猜测——只需将纯 C# 代码直接放入你的项目中即可。

> **快速预览：** 完成后，你将拥有一个可重用的 `FontSubstitutionWarningCollector`，它会在文档加载期间收集每个字体替换消息，并且你将知道在找不到字体时该如何响应。

---

## 你将学到的内容

- 如何配置 `LoadOptions` 以监听字体替换警告。  
- 如何在自定义收集器类中捕获这些警告。  
- 如何处理收集到的警告并决定是中止、记录还是替换字体。  
- 对引用远程或嵌入式字体的文档进行边缘情况处理。  

**先决条件：** .NET 6+（或 .NET Framework 4.6+），Aspose.Words for .NET（最新版本），以及对 C# 的基本了解。如果你从未使用过 Aspose.Words，也无需担心——本指南只假设几分钟的设置时间。

## 使用 Aspose.Words LoadOptions 检测字体

检测缺失字体的第一步是让 Aspose.Words 报告它们。这通过 `LoadOptions.WarningCallback` 属性实现，该属性接受实现 `IWarningCallback` 的任意类。下面我们创建一个小型收集器，用于存储每个警告以供后续检查。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**为什么这很重要：** 如果没有警告回调，Aspose.Words 会悄悄地用默认字体替换缺失的字体，而你永远不会知道问题的存在。通过捕获 `WarningType.FontSubstitution`，我们获得了完整的可见性——正是你需要的用于 **检测字体** 的数据，这些字体在主机上不可用。

现在我们将收集器挂接到 `LoadOptions` 并加载文档：

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **专业提示：** 如果你批量处理许多文档，请复用同一个 `FontSubstitutionWarningCollector` 实例，但记得在每次加载之间调用 `Clear()`，以避免混合不同文件的警告。

## 在文档加载期间捕获警告

文档加载后，收集器已经保存了每个与字体相关的警告。接下来的合乎逻辑的问题是：*如何捕获警告* 以便轻松记录或显示？

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

典型的输出如下：

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**这告诉你什么：** 每行显示原始字体名称以及 Aspose.Words 选择的替代字体。凭借这些信息，你可以决定替代字体是否可接受，或是否需要手动嵌入缺失的字体。

## 优雅地处理缺失字体

检测并捕获警告只是成功的一半。当你在生产环境中 **处理缺失字体** 时，真正的价值才显现。下面是三种常见策略：

1. **记录并继续** – 适用于只需要审计跟踪的批处理。  
2. **关键字体时中止** – 如果缺少特定字体（例如品牌专用字体），则抛出异常。  
3. **即时嵌入字体** – 从已知文件夹加载缺失的字体，并在重新加载文档之前将其注册到 Aspose.Words。  

### 示例：在关键字体缺失时中止

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### 示例：自动嵌入缺失字体

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**为什么这些模式有帮助：** 通过明确决定在字体缺失时的处理方式，你可以消除可能损害品牌或可读性的静默替代。这就是以受控方式 **处理缺失字体** 的本质。

## 完整可运行示例

将所有内容整合在一起，下面是一个可直接运行的程序示例，演示 **如何检测字体**、**如何捕获警告**，以及通过记录日志的简单策略来 **处理缺失字体**。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**预期结果：** 当你对引用了机器上不存在的字体的文档运行程序时，控制台会列出每个替换警告。如果任何警告涉及 `critical` 集合中的字体，程序将提前退出，防止生成有缺陷的 PDF。

## 常见问题解答 (FAQs)

| Question | Answer |
|----------|--------|
| *我需要 Aspose.Words 的许可证才能使用这段代码吗？* | 是的，有效的 Aspose.Words 许可证会去除评估水印并解锁全部功能。 |
| *此方法能检测嵌入的字体吗？* | 嵌入的字体已经是文件的一部分，因此 Aspose.Words 不会触发替代警告。如有需要，你可以检查 `Document.FontInfos` 来枚举嵌入的字体。 |
| *如果缺失的字体在 Windows 上是系统字体，但在 Linux 上不存在怎么办？* | 在 Linux 上同样会触发警告，因为该字体未安装。请使用 “处理缺失字体” 策略，将所需的 `.ttf` 文件随应用一起分发。 |
| *警告收集器是线程* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}