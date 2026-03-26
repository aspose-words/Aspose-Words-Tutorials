---
category: general
date: 2026-03-25
description: 创建警告回调以加载 Word 文档并检测缺失的字体。了解如何在 Aspose.Words for .NET 中配置字体设置。
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: zh
og_description: 创建警告回调以在加载 Word 文档时检测缺失字体。本指南展示了如何在 Aspose.Words 中配置字体设置。
og_title: 创建警告回调 – 加载 Word 文档并检测缺失字体
tags:
- Aspose.Words
- C#
- Font handling
title: 为加载 Word 文档创建警告回调 – 完整指南
url: /zh/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建警告回调 – 加载 Word 文档并检测缺失字体

是否曾在加载 Word 文档时需要 **创建警告回调**，却不明白为什么有些字体会消失？你并非唯一遇到此问题的人。在许多企业应用中，缺失的字体会导致布局灾难，而没有合适的回调，你甚至可能根本注意不到这个问题。

好消息是？使用 Aspose.Words for .NET，你可以 **加载 Word 文档**、**检测缺失字体**，并 **配置字体设置**，只需几行简洁的代码。在本教程中，我们将逐步演示一个完整、可运行的示例，解释每个部分为何重要，并展示如何验证警告回调是否正常工作。

> **你将收获**  
> * 一个完整的 C# 程序，能够加载 DOCX，报告任何字体替换，并让你自定义字体搜索路径。  
> * 对 `FontSettings`、`LoadOptions` 和 `IWarningCallback` 类的理解。  
> * 处理诸如嵌入字体或系统级字体文件夹等边缘情况的技巧。

---

## 前置条件

- .NET 6+（或 .NET Framework 4.7.2+）并配有 C# 编译器。  
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）。  
- 一个示例 Word 文件（`input.docx`），其中至少包含一种未在机器上安装的字体（例如在精简的 Windows 容器中缺少 *Calibri Light*）。  
- 对 C# 控制台应用有基本了解。

无需额外库；所有功能均内置于 Aspose.Words。

---

## 第 1 步：创建警告回调以检测缺失字体

此谜题的 **核心** 是实现 `IWarningCallback` 接口的类。Aspose.Words 在遇到需要发出警告的情况时（最常见的是字体替换）会调用此回调。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**为何重要** – 如果没有回调，你只能事后在日志中筛选信息。实时处理警告可以让你决定是中止加载、使用回退字体替换缺失字体，还是仅将问题记录下来以供后续审查。

---

## 第 2 步：为自定义字体处理配置 FontSettings

在实际加载文档之前，我们可能需要告诉 Aspose.Words 去哪里寻找系统中不存在的字体。这时就需要使用 `FontSettings`。

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**为何重要** – 将 Aspose.Words 指向包含缺失字体的文件夹，往往可以完全避免替换。当无法做到时，使用合理的默认字体（如 *Arial*）可以保持文档可读。

---

## 第 3 步：使用配置好的警告回调加载 Word 文档

现在把所有内容串联起来：创建 `LoadOptions`，注入我们的 `FontSettings` 与 `FontWarningHandler`，最后加载文档。

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**为何重要** – `LoadOptions` 是唯一可以配置文档读取方式的地方。通过同时提供字体配置和警告回调，我们确保任何缺失的字体既会在正确的位置查找，又会立即报告。

---

## 第 4 步：验证输出 – 你会看到什么？

在控制台运行程序。如果 `input.docx` 使用了未安装且也不在 `C:\SharedFonts` 中的字体，你会看到类似如下的输出：

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

如果所有字体均可用，警告行根本不会出现。此即时反馈在自动化文档处理流水线中极其宝贵，因为静默的字体替换可能会破坏品牌规范。

---

## 第 5 步：常见陷阱与最佳实践提示

| 陷阱 | 如何避免 |
|---------|-----------------|
| **忘记引用 `Aspose.Words.Fonts`** | 确保在文件顶部加入 `using Aspose.Words.Fonts;`，否则编译器会提示缺少类型。 |
| **字体文件夹路径错误** | 再次确认路径，并在有子文件夹时设置 `recursive: true`。使用 `Path.GetFullPath` 进行调试。 |
| **多个警告回调** | Aspose.Words 只会使用最后一次赋值的 `WarningCallback`。如需更复杂的逻辑，请保持单一处理器并在内部进行委托。 |
| **在无 UI 的服务器上运行** | 控制台写入在控制台应用中没问题，但在 Web 应用中建议改为写入文件或监控系统，而不是 `Console.WriteLine`。 |
| **大型文档导致性能下降** | 在多次加载之间复用同一个 `FontSettings` 实例；频繁创建会带来额外开销。 |

**专业提示**：如果需要 **收集** 警告以供后续分析，可在处理器内部将信息存入 `List<string>`，而不是直接打印。

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

随后即可在文档加载后检查 `handler.Messages`。

---

## 第 6 步：扩展方案 – 如果需要嵌入回退字体怎么办？

有时你希望将缺失的字体 **嵌入** 到输出的 PDF 中，以便下游查看器能够呈现完全相同的外观。加载文档后，你可以强制进行嵌入：

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

该代码片段展示了相同的 **配置字体设置** 方法如何扩展到加载之外的场景。

---

## 完整可运行示例

下面是完整程序代码，可直接复制粘贴到新的 Console App 项目中。它包含了上述所有要点。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**预期输出**（当存在缺失字体时）：

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

如果没有发生替换，仅会显示成功信息。

---

## 结论

我们已经 **创建了一个警告回调**，能够在使用 Aspose.Words **加载 Word 文档** 时可靠地 **检测缺失字体**，并展示了如何 **配置字体设置** 来控制库的字体搜索路径以及使用的回退字体。通过将 `FontSettings` 与 `LoadOptions` 结合使用，你可以全面掌握字体相关的问题——不再有静默的布局错误。

下一步？尝试将 `FontWarningHandler` 替换为写入数据库的日志器，或实验 **字体替换规则**，将特定缺失字体映射为品牌批准的替代字体。如果你的应用运行在容器化环境中，还可以探索 **从云存储动态加载字体** 的方案。

对特定边缘案例有疑问——比如处理 OpenType 特性或加密的 DOCX 文件？欢迎在下方留言，祝编码愉快！

---

![创建警告回调示意图](https://example.com/images/create-warning-callback.png "创建警告回调示意图")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}