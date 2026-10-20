---
category: general
date: 2026-03-28
description: 如何在使用 Aspose.Words 加载 DOCX 时捕获警告并获取缺失字体的警告信息。学习高效处理缺失字体的方法。
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: zh
og_description: 如何在使用 Aspose.Words 加载 DOCX 时捕获警告、获取警告信息，并通过实用代码示例处理缺失字体。
og_title: 如何捕获 Aspose.Words 警告 – 完整 C# 指南
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何捕获 Aspose.Words 警告 – 完整 C# 指南
url: /zh/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕获 Aspose.Words 警告 – 完整 C# 指南

有没有想过 **如何捕获** 在使用 Aspose.Words 加载 Word 文档时弹出的警告？也许你看到奇怪的字体变化，想确切了解原因。简而言之，你可以接入库的警告系统，**获取警告信息**，甚至在它们破坏布局之前 **处理缺失的字体**。  

在本教程中，我们将演示一个真实场景：加载 DOCX，收集引擎产生的所有警告，并打印出任何字体替换的详细信息。完成后，你将拥有可直接运行的代码示例，理解每一步背后的 “为什么”，并知道如何在自己的项目中扩展此方法。

## 你将学到

- 如何配置 `LoadOptions` 以自动捕获警告。  
- 从 `WarningInfoCollection` 中 **获取警告信息** 的确切方法。  
- 如何通过 `WarningType.FontSubstitution` 标志识别并响应 **缺失的字体**。  
- 处理边缘情况的技巧，例如包含嵌入字体或自定义字体文件夹的文档。  

无需外部参考——所有内容都在这里。

---

## 前提条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）。  
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）。  
- 一个示例 DOCX（`input.docx`），其中缺少某些字体或使用了机器上未安装的字体。  

就这些。如果你已经熟悉 C# 和 Visual Studio，可以直接复制粘贴代码并立即运行。

---

## 步骤 1：准备 Load Options 和警告回调

当你调用 `new Document(path, loadOptions)` 时，Aspose.Words 首先会解析文件。解析过程中可能会遇到缺失字体、不受支持的特性或已弃用的标记。要捕获这些事件，需要一个 **警告回调** 对象。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**为什么这很重要：** 没有回调时，Aspose.Words 会悄悄将警告记录到控制台（或直接丢弃），导致你看不到可能影响布局的字体替换。通过提供专用的 `WarningInfoCollection`，你可以完整地看到所有信息。

> **小贴士：** 如果你只关心与字体相关的警告，后续可以进行过滤——但收集 *所有* 警告可以为将来的问题提供安全网。

---

## 步骤 2：使用配置好的选项加载文档

回调准备好后，加载文件。`Document` 构造函数会自动在发现任何问题时调用回调。

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**底层发生了什么？** Aspose.Words 解析 Open XML，解析样式，并尝试将每个字体引用映射到系统已安装的字体。如果找不到匹配项，它会创建类型为 `FontSubstitution` 的 `WarningInfo` 条目。

---

## 步骤 3：检索并检查收集到的警告

加载完成后，`warningCollector` 已包含所有产生的警告。我们把它们取出来，重点关注字体替换的消息。

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**示例输出**（你的控制台可能会显示类似内容）：

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

如果想获取 *所有* 警告，只需删除 `if` 检查或对每个条目记录 `warning.Type`。

---

## 步骤 4：处理缺失字体 – 不止记录日志

捕获警告固然有用，但通常你需要以编程方式 **处理缺失的字体**。下面提供两种常见策略：

### 4.1 使用特定回退字体替换缺失字体

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

现在，任何缺失的字体都会被替换为 *Calibri*，而不是库的默认回退字体。

### 4.2 动态嵌入替代字体

如果你有自定义字体文件（例如 `MyFallback.ttf`），可以在运行时注册它：

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

当你随应用程序分发特定企业字体时，这种方式非常方便。

> **边缘情况：** 已经嵌入所需字体的文档会忽略系统替换规则。在这种情况下，针对该字体的警告集合将为空，这正是你想要的结果。

---

## 步骤 5：完整可运行示例（复制‑粘贴即用）

下面是一个自包含的程序，演示从头到尾的所有操作。只需将 `YOUR_DIRECTORY/input.docx` 替换为你的测试文件路径即可。

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**预期结果**

- 控制台会打印每条字体替换警告，前面带有警告表情以提高可见性。  
- 输出的 DOCX（`output.docx`）在检测到缺失字体的地方使用 *Calibri*。  
- 不会出现未处理的异常——警告系统会优雅地处理任何未知字体。

---

## 常见问题与解答

**Q: 这能用于从 Word 生成的 PDF 吗？**  
A: 能。Aspose.Words 将 PDF 视为另一种输出格式。警告捕获发生在 *加载* 阶段，独立于最终导出。

**Q: 如果我要捕获 **所有** 文档操作（保存、转换等）的警告怎么办？**  
A: 可以在实例化文档后将同一个 `WarningInfoCollection` 赋给 `Document.WarningCallback`。随后每一次操作都会向同一集合中添加新条目。

**Q: 警告回调会影响性能吗？**  
A: 影响可以忽略不计。集合仅存储对象；除非在紧密循环中处理成千上万条警告，否则不会感受到明显的慢速。

**Q: 如何抑制我不关心的警告？**  
A: 实现一个继承自 `IWarningCallback` 的自定义类，并在 `Warning` 方法内部进行过滤。内置的 `WarningInfoCollection` 只负责存储，不会过滤。

---

## 小贴士与陷阱

- **小贴士：** 始终检查 `Warning.Description` ——它包含缺失字体的精确名称，可帮助你决定是否随应用程序一起分发该字体。  
- **注意嵌入字体：** 如果源 DOCX 已经嵌入所需字体，Aspose.Words 不会发出替换警告，即使本地未安装该字体。  
- **线程安全：** `WarningInfoCollection` 不是线程安全的。如果并发加载多个文档，请为每个线程提供独立的集合。  
- **版本检查：** 警告 API 自 Aspose.Words 20.8 起已稳定。确保使用较新版本，以免错过后续新增的警告类型。

---

## 结论

我们已经介绍了 **如何捕获 Aspose.Words 警告**，演示了 **获取警告信息** 的方法，并展示了通过回退字体或自定义字体文件夹 **处理缺失字体** 的实用方案。完整示例可直接放入任何 .NET 项目，且这些概念可以扩展到更大的自动化流水线。

接下来，你可以进一步探索：

- 使用 `Document.WarningCallback` 在 **保存** 操作期间捕获警告。  
- 将警告记录到文件或遥测系统，以便生产环境监控。  
- 扩展回调，自动将缺失字体替换为品牌专用字体。

尽情实验吧——更换回退字体、批量添加文档，或将警告收集器集成到 CI 流程中，以标记字体相关的回归。祝编码愉快，愿你的文档始终如你所期望的那样渲染！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}