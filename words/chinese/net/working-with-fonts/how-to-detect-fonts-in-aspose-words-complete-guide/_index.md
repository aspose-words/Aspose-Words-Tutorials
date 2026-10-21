---
category: general
date: 2026-04-21
description: 学习如何检测字体、捕获警告、配置回调以及枚举警告，使用 Aspose.Words 在 C# 中实现可靠的字体处理。一步步指南。
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: zh
og_description: 如何在 Aspose.Words 中检测字体？本教程展示了如何捕获警告、配置回调以及在 C# 中枚举警告。
og_title: 如何在 Aspose.Words 中检测字体 – 完整指南
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何在 Aspose.Words 中检测字体 – 完整指南
url: /zh/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中检测字体 – 完整指南

是否曾好奇在加载 Word 文档时 **如何检测字体** 缺失？这种情况比你想象的更常出现，尤其是在处理旧文件或跨平台部署时。在本教程中，我们将演示一个完整、可运行的示例，**捕获警告**、**配置回调** 并 **枚举警告**，让你随时了解哪些字体被替换。

我们将使用 Aspose.Words for .NET（撰写时版本 v24.9）和纯 C#。无需外部服务，也不需要魔法——只需 API 和几行代码。完成后，你将能够发现每一次字体替换、记录下来，甚至在关键字体缺失时决定是否中止加载。

### 您需要的条件
- **Aspose.Words for .NET**（通过 NuGet 安装：`Install-Package Aspose.Words`）
- .NET 6.0 或更高版本（代码同样适用于 .NET Framework）
- 一个引用了机器上不存在的字体的示例 DOCX（例如 “MyCustomFont.ttf”）
- Visual Studio、Rider 或任意你喜欢的 C# 编辑器

> **Pro tip:** 如果没有缺少字体的文档，只需在系统上重命名一个字体文件，或编辑 DOCX XML 以引用一个不存在的字体族。

---

## 如何使用 Aspose.Words 检测字体

核心思路是挂接到 Aspose.Words 的警告系统。当库找不到请求的字体时，会发出 `WarningType.FontSubstitution` 警告。通过提供自定义的 `IWarningCallback` 实现，你可以 **检测字体** 在加载过程中被替换的情况。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Why this works:** Aspose.Words 会对每个非关键问题调用 `Warning` 方法。通过存储 `WarningInfo` 对象，你可以完整访问类型、消息和上下文，这正是 **检测字体** 被替换所需的全部信息。

---

## 加载文档时如何捕获警告

既然我们已有收集器，就需要在 `LoadOptions` 中指定它。这就是 **如何捕获警告** 的关键步骤。

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Edge case:** 如果你从流加载文档（`new Document(stream, loadOptions)`），同样的回调也会生效——只需传入流而不是文件路径。

此时文档已完整加载，但所有字体替换警告已安全存储在 `warningCollector.Warnings` 中。

---

## 如何枚举警告并报告字体替换

最后，我们遍历收集到的警告，**枚举警告** 中专门关于字体替换的条目。此步骤将原始数据转化为可读报告。

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**预期输出**（示例）：

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

如果文档中没有缺失的字体，循环将不会产生任何输出——无需担心。

---

## 完整工作示例（所有步骤合并在一个文件）

下面是可以直接复制到控制台项目中的完整程序。它将 **如何检测字体**、**如何捕获警告**、**如何配置回调** 与 **如何枚举警告** 融合在一起，形成一个连贯的流程。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**运行此程序** 将打印 Aspose.Words 必须替换的每一种字体。你可以将输出重定向到日志文件、触发警报，甚至在关键字体缺失时中止加载。

---

## 常见问题与注意事项

### 如果需要在缺少必需字体时停止加载该怎么办？
你可以在回调内部检查 `WarningInfo` 对象，当出现特定字体名称时抛出异常。异常会中止加载，给予你完全的控制权。

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### 这在 PDF 或其他格式下也有效吗？
是的。Aspose.Words 对 PDF、RTF、HTML 等格式使用相同的警告基础设施。只需更换文件扩展名，代码其余部分保持不变。

### 如何将警告记录到文件而不是控制台？
将 `Console.WriteLine` 替换为你喜欢的日志框架（如 `Serilog`、`NLog` 等）。`WarningInfo` 类提供 `Message`、`Source` 和 `Exception`，便于详细日志记录。

### 这会影响性能吗？
开销可以忽略不计——Aspose.Words 本身已经在内部生成警告。添加回调仅是将它们存入列表，时间复杂度为 O(n)，其中 n 为警告数量。对普通文档而言，影响远低于总加载时间的 1 %。

---

## 可视化概览

![如何在 Aspose.Words 中检测字体 – 警告流程图](https://example.com/images/font-detection-diagram.png "如何检测字体")

*Alt text:* **如何检测字体** – 图示警告回调、收集和枚举步骤。

---

## 总结

我们已经通过 **捕获警告**、**配置回调** 与 **枚举警告**，完整演示了在 Aspose.Words 中 **如何检测字体** 的方法。完整代码示例展示了可直接投入生产的模式，适用于任何 .NET 应用。

接下来，你可能想进一步探索：

- **如何捕获警告** 以处理其他问题（如图像转换错误）
- **如何配置回调** 以集成自定义日志框架
- **如何枚举警告** 在批量处理多个文档时
- 使用 **Aspose.Words.Fonts.FontSettings** 提供后备字体文件夹，从根本上减少替换次数

动手试一试，依据你的日志风格调整收集器，今后再也不会被意外的字体替换所惊讶。如有任何疑问，欢迎在下方留言——祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}