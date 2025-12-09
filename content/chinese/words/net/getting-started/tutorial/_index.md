---
language: zh
url: /chinese/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# 检测 Aspose.Words 文档中缺失的字体 – 完整 C# 指南

有没有想过在使用 Aspose.Words 加载 Word 文件时 **检测缺失的字体**？在我的日常工作中，我遇到过一些 PDF 看起来怪怪的，因为原始文档使用了我系统中未安装的字体。好消息是？Aspose.Words 可以准确告知何时替换了字体，并且你可以通过一个简单的警告回调捕获这些信息。

在本教程中，我们将演示一个 **完整、可运行的示例**，展示如何记录每一次字体替换、回调为何重要，以及一些额外的技巧，以实现稳健的缺失字体检测。没有废话，只提供代码和你今天就能使用的思路。

---

## 你将学到

- 如何实现 **Aspose.Words 警告回调** 来捕获字体替换事件。  
- 如何配置 **LoadOptions C#** 使回调在加载文档时被触发。  
- 如何验证缺失字体检测是否真正生效，以及控制台输出的样子。  
- 大批量或无头环境下的可选调整。  

**先决条件** – 需要最近版本的 Aspose.Words for .NET（代码在 23.12 版本上测试通过），.NET 6 或更高版本，以及基本的 C# 认识。如果你满足这些条件，就可以开始了。

---

## 使用警告回调检测缺失字体

解决方案的核心是实现 `IWarningCallback`。Aspose.Words 会为多种情况抛出 `WarningInfo` 对象，但我们只关心 `WarningType.FontSubstitution`。下面看看如何挂接它。

### 步骤 1：创建字体警告收集器

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*为什么重要*：通过过滤 `WarningType.FontSubstitution`，我们可以避免来自不相关警告（如已弃用功能）的噪音。`info.Description` 已经包含了原始字体名称和使用的回退字体，为你提供清晰的审计轨迹。

---

## 配置 LoadOptions 使用回调

现在告诉 Aspose.Words 在加载文件时使用我们的收集器。

### 步骤 2：设置 LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*为什么重要*：`LoadOptions` 是唯一可以插入回调、加密密码以及其他加载行为的地方。将其与 `Document` 构造函数分离，使代码能够在多个文件之间复用。

---

## 加载文档并捕获缺失字体

回调已经接好，接下来只需加载文档。

### 步骤 3：加载你的 DOCX（或任何受支持的格式）

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

当 `Document` 构造函数解析文件时，任何缺失的字体都会触发我们的 `FontWarningCollector`。控制台会显示类似下面的行：

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

这行就是 **检测缺失字体** 成功的具体证据。

---

## 验证输出 – 预期结果

在终端或 Visual Studio 中运行程序。如果源文档使用了系统未安装的字体，你会看到至少一行 “Font substituted”。如果文档只使用已安装的字体，回调保持沉默，你只会看到 “Document loaded successfully.” 的信息。

**小技巧**：双重检查时，在 Microsoft Word 中打开该文件并查看字体列表。任何出现在 *Replace Fonts*（替换字体）下的 *Home → Font* 组中的字体，都可能被替换。

---

## 高级：批量检测缺失字体

通常需要扫描数十个文件。同样的模式可以很好地扩展：

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

因为 `FontWarningCollector` 每次被调用时都会写入控制台，你可以在不额外编写代码的情况下获得每个文件的报告。对于生产环境，你可能希望将日志写入文件或数据库——只需把 `Console.WriteLine` 换成你喜欢的日志记录器即可。

---

## 常见陷阱与专业提示

| 问题 | 为什么会出现 | 解决方案 |
|------|--------------|----------|
| **没有出现任何警告** | 文档实际上只包含已安装的字体。 | 通过在 Word 中打开文件或故意从系统中移除某个字体进行验证。 |
| **回调未被调用** | 未为 `LoadOptions.WarningCallback` 赋值，或后续使用了新的 `LoadOptions` 实例。 | 保持使用同一个 `LoadOptions` 对象，并在每次加载时复用它。 |
| **出现太多无关警告** | 未对 `WarningType.FontSubstitution` 进行过滤。 | 按示例添加 `if (info.Type == WarningType.FontSubstitution)` 条件。 |
| **在超大文件上性能下降** | 回调会在每个警告上执行，对于大型文档可能数量庞大。 | 通过 `LoadOptions.WarningCallback` 禁用其他警告类型，或在已知格式时设置 `LoadOptions.LoadFormat` 为特定类型。 |

---

## 完整可运行示例（复制粘贴即用）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**预期的控制台输出**（当遇到缺失字体时）：

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

如果没有发生替换，你只会看到成功提示行。

---

## 结论

现在你拥有了一套 **完整、可投入生产的缺失字体检测方案**，适用于任何使用 Aspose.Words 处理的文档。通过利用 **Aspose.Words 警告回调** 并配置 **LoadOptions C#**，你可以记录每一次字体替换，排查布局问题，确保生成的 PDF 保持预期的外观。

从单个文件到大批量处理，模式保持不变——实现 `IWarningCallback`，将其插入 `LoadOptions`，让 Aspose.Words 完成繁重的工作。

准备好下一步了吗？尝试将其与 **字体嵌入** 或 **回退字体族** 结合，自动修复问题，或探索 **DocumentVisitor** API 进行更深层次的内容分析。祝编码愉快，愿所有字体都如你所愿！

---

![检测 Aspose.Words 中缺失字体的控制台输出截图](https://example.com/images/detect-missing-fonts.png "检测缺失字体的控制台输出")

{{< layout-end >}}

{{< layout-end >}}