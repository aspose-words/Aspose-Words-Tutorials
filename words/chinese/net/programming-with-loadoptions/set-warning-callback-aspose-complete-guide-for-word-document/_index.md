---
category: general
date: 2026-05-23
description: 设置 Aspose 警告回调以捕获 Aspose.Words 中的字体替换警告。了解 LoadOptions、FontSettings 和
  IWarningCallback 的实现。
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: zh
og_description: 设置 Aspose 警告回调以监控 Aspose.Words 中的字体替换。本教程展示 LoadOptions、FontSettings
  和警告处理程序的实现。
og_title: 设置警告回调 aspose – 分步指南
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: 设置警告回调 Aspose – Word 文档加载完整指南
url: /zh/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 设置警告回调 aspose – Word 文档加载完整指南

有没有想过如何 **set warning callback aspose**，从而永远不会错过字体替换警报？你并不孤单。当 DOCX 引用的字体未安装时，Aspose.Words 会悄悄替换它，如果没有合适的回调，你可能根本不知道发生了变化。

在本教程中，我们将逐步演示一个完整、可运行的示例，准确展示如何捕获这些警告。结束时，你将了解 **Aspose.Words LoadOptions**、如何配置 **FontSettings**，以及为何实现 **IWarningCallback** 是保持信息同步的最佳方式。没有废话——只提供可以直接放入 .NET 项目中的代码。

## 您将学习

- 如何在 `LoadOptions` 实例上 **set warning callback aspose**。  
- 在打开文档时 **Aspose.Words LoadOptions** 的作用。  
- 使用 `FontSettings` 配置 **Aspose fonts substitution** 处理。  
- 编写自定义 **IWarningCallback** 实现以记录字体问题。  
- 使用 **Aspose document loading** 的最佳实践安全加载文档。

### 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.5+）。  
- 有效的 Aspose.Words for .NET 许可证或试用密钥。  
- Visual Studio、Rider 或任意你喜欢的 C# 编辑器。  
- 一个引用缺失字体的示例 DOCX（`fontTest.docx`）（可选但有帮助）。

> **技巧提示：** 如果没有缺失字体的 DOCX，只需在文档样式中重命名字体，即可触发警告。

---

## 如何为文档加载设置警告回调 aspose

下面是完整的、独立的程序。将其保存为 `Program.cs`，恢复 NuGet 包并运行。控制台将打印 Aspose.Words 在加载文件时产生的每一个字体替换警告。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### 预期的控制台输出

如果 `fontTest.docx` 引用的字体未安装，你会看到类似如下内容：

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

如果所有字体都已安装，唯一打印的行将是 *Document loaded successfully*——没有警告，没有噪音。

![设置警告回调 aspose 示例](image.png "设置警告回调 aspose 示例")

---

## 理解 Aspose.Words 中的 LoadOptions

`LoadOptions` 是对 **aspose document loading** 进行各种微调的入口。它让你可以：

1. **指定自定义 `FontSettings`** – 当你的应用自带字体时非常有用。  
2. **附加警告回调** – 正是我们用来捕获字体替换的方式。  
3. 控制文档格式检测、密码处理等更多功能。

因为 `LoadOptions` 是传递给 `Document` 构造函数的，设置会在文件解析的那一刻 **一次性** 生效。这就是我们能够保证警告处理器在文档甚至还未在内存中构建之前，就捕获到每一次替换的原因。

### 何时使用自定义 LoadOptions

- **批量处理** 多个文件时，需要统一的日志策略。  
- **云服务** 需要向调用方报告缺失字体。  
- **测试流水线** 用于验证文档是否符合公司字体政策。

---

## 为 Aspose 字体替换配置 FontSettings

`FontSettings` 对象控制 Aspose.Words 如何解析字体。默认情况下，它会搜索系统字体文件夹，然后回退到内置替代字体。你可以对该行为进行细致调优：

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

这些代码行对基本的 “set warning callback aspose” 场景是可选的，但它们展示了通过提前提供正确的字体，如何 **减少** 替换警告的数量。

---

## 实现 IWarningCallback 以处理字体替换警告

`IWarningCallback` 接口非常小——只有一个 `Warning` 方法。然而它让你 **完全控制** 警告的处理方式：

- **记录到文件** 而不是控制台。  
- **收集警告** 到列表中以供后续分析。  
- **抛出异常** 以处理关键警告（例如缺少必需字体）。

下面是一个快速示例，将警告存入 `List<string>`：

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

随后，你可以在加载文档后检查 `handler.Messages`，决定是否中止处理。

---

## 使用自定义警告处理加载文档（完整工作流）

把所有内容组合在一起，最终的模式可能会这样使用：

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

此代码片段演示了生产环境中使用的 **aspose document loading** 流程：配置 → 加载 → 响应。无论是处理单个文件还是遍历成千上万的文件，这种模式都能良好扩展。

---

## 常见问题与边缘情况

**如果文档受密码保护怎么办？**  
在 `LoadOptions` 初始化器中添加 `Password = "secret"`。文件解密后，警告回调仍然有效。

**回调会对其他类型的警告触发吗？**  
会——`WarningInfo.Type` 可以是 `DocumentStructure`、`UnsupportedFileFormat` 等。在示例中我们只过滤 `FontSubstitution`，但移除 `if` 检查即可记录所有警告。

**这会影响性能吗？**  
影响可以忽略不计。回调仅在出现警告时才被调用，远少于正常解析步骤的频率。

**能完全禁用字体替换吗？**  
可以设置 `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;`，但随后 Aspose.Words 会在缺少字体时抛出异常，而不是进行替换。

---

## 结论

现在你已经清楚如何 **set warning callback aspose**，在 **Aspose.Words LoadOptions** 处理期间监控字体替换事件。通过配置 `FontSettings`、实现轻量级 `IWarningCallback`，并使用这些选项加载文档，你可以完整地看到 Aspose 在后台对字体所做的任何更改。

接下来你可以：

- 将警告处理器扩展为写入集中日志服务。  
- 将回调与自定义字体回退策略结合。  
- 在构建验证客户端上传文档的云 API 时使用此模式。

尝试使用自己的 DOCX 文件，调节 `FontSettings`，观察控制台精准报告哪些字体被替换。祝编码愉快，愿你的文档始终如预期渲染！

## 相关教程

- [在 Java 中捕获字体替换警告 – 完整指南](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [在 Aspose.Words 中启用字体替换警告 – 完整指南](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [如何在 Aspose.Words for Java 中设置 LoadOptions](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}