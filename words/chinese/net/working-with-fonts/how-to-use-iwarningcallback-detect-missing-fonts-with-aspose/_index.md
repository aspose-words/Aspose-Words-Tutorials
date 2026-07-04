---
category: general
date: 2026-06-24
description: 如何使用 IWarningCallback 检测 Aspose.Words 文档中缺失的字体。了解完整的可运行示例和最佳实践。
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: zh
og_description: 如何使用 IWarningCallback 检测 Aspose.Words 中缺失的字体。请遵循逐步指南，获取完整的生产就绪解决方案。
og_title: 如何使用 IWarningCallback – 检测缺失字体
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何使用 IWarningCallback – 使用 Aspose.Words 检测缺失字体
url: /zh/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 IWarningCallback – 检测 Aspose.Words 中缺失的字体

在使用 Aspose.Words 并需要 **detect missing fonts**（检测缺失字体）时，使用 **IWarningCallback** 至关重要。本指南将逐步演示一个完整的可复制粘贴示例，向您展示如何使用 IWarningCallback 捕获字体替换警告、其重要性以及捕获后该如何处理。

如果您曾经打开文档时看到乱码，因为自定义字体未安装，您一定深有体会。完成本教程后，您将拥有一种可靠的方式，以编程方式发现这些问题、记录日志，甚至自动应用回退字体。

## 您将学到

- **IWarningCallback** 的作用以及何时使用它。  
- 如何实现自定义警告收集器，以隔离 **detect missing fonts** 事件。  
- 将收集器绑定到 **LoadOptions**，实现对每次文档加载的监控。  
- 验证输出并处理边缘情况（多个缺失字体、静默警告等）。  

### 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）。  
- 通过 NuGet 安装 Aspose.Words for .NET (`Install-Package Aspose.Words`)。  
- 一个引用了机器上不存在的字体的 DOCX 文件（例如 `DocumentWithMissingFont.docx`）。  

无需额外库——所有功能均内置于 Aspose.Words。

---

## 如何使用 IWarningCallback 检测 Aspose.Words 中缺失的字体

下面是 **完整、可运行的程序**。将其复制到新的控制台项目中，调整文件路径后运行。您将在控制台看到每个缺失字体的警告。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### 预期输出

如果 `DocumentWithMissingFont.docx` 引用了名为 *“MyFancyFont”* 的字体且未安装，您会看到类似如下内容：

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

每行以 **[Missing Font]** 为前缀的输出都是由我们的 **IWarningCallback** 实现生成的，表明我们成功 **detect missing fonts**。

---

## 步骤 1：实现 IWarningCallback 接口

为什么需要自定义类？Aspose.Words 会因多种原因抛出 **warnings**——文件格式问题、已弃用特性，以及对我们最重要的字体替换。实现 `IWarningCallback` 后，我们可以在警告产生的瞬间获取到它们。通过过滤 `WarningType.FontSubstitution`，即可只保留字体缺失的情形。

**小技巧：** 如果想捕获 *所有* 警告用于诊断，只需移除 `if` 检查，记录每个 `info.Type` 即可。

---

## 步骤 2：将回调绑定到 LoadOptions

`LoadOptions` 是告诉 Aspose.Words 如何处理输入文档的入口。将 `WarningCallback` 设置为我们收集器的实例，即可在整个加载过程中激活回调。相同的 `LoadOptions` 对象可以复用于多个文档，这在批处理流水线中非常方便。

**常见问题：** *如果在加载文档时不指定 LoadOptions 会怎样？*  
答：Aspose.Words 仍会在内部抛出警告，但没有回调时这些警告会被静默丢弃，您也就失去了 **detect missing fonts** 的机会。

---

## 步骤 3：加载文档并捕获缺失字体警告

接受文件路径和 `LoadOptions` 的 `Document` 构造函数负责完成大部分工作。文档解析时，任何缺失的字体都会触发我们的 `FontWarningCollector.Warning` 方法。控制台输出验证了机制的有效性。

**边缘情况：** 单个文档可能引用多个缺失字体。回调会为每个缺失字体触发一次，因此会出现多行输出——这非常适合生成完整的报告。

---

## 为什么使用 IWarningCallback 而不是手动检查字体？

您可以在加载后遍历文档的 `Run.Font` 属性手动检查，但这要求文档必须成功加载——如果字体完全不可用，加载本身就会失败。警告系统在任何替换发生之前就会触发，能够提供真实的缺失字体信息。

此外，回调作为加载管道的一部分运行，您可以提前中止、即时替换字体，或记录详细诊断信息，而无需再次遍历文档树。

---

## 优雅地处理多个缺失字体

如果预计会有大量缺失字体，建议将它们聚合到集合中：

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

加载完成后，您可以遍历 `MissingFonts`，例如将其写入 CSV 文件供设计团队使用。

---

## 进阶：将警告记录到文件

控制台输出适合演示，但生产代码通常会写入持久存储。将 `Console.WriteLine` 替换为类似如下代码：

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

这样即可留下审计日志，便于日后审查，满足合规要求。

---

## 结论

我们已经完整演示了 **如何使用 IWarningCallback** 来 **detect missing fonts**，包括实现回调、将其绑定到 `LoadOptions`，以及处理产生的警告。该方法为您提供了实时的字体问题洞察，能够在文档渲染前记录、替换或提醒用户。

后续可进一步探索：

- **回退字体：** 在发生替换时以编程方式指定默认字体。  
- **批量处理：** 循环处理文件夹中的文档，复用同一个 `AggregatingFontCollector`。  
- **用户反馈：** 将缺失字体警告展示在 UI 而非控制台。

在自己的项目中尝试一下吧——不再有神秘的乱码，只有清晰可操作的诊断信息。祝编码愉快！


## 接下来该学习什么？

以下教程与本指南的技术紧密相关，帮助您进一步掌握 API 功能并探索替代实现方式：

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}