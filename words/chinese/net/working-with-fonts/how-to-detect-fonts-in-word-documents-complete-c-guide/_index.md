---
category: general
date: 2026-02-24
description: 如何使用 Aspose.Words 检测 Word 文档中的字体。了解如何设置回调并加载 Word 文档，完整代码示例。
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: zh
og_description: 如何使用警告回调检测 Word 文档中的字体。本指南展示了如何设置回调并使用 Aspose.Words 加载 Word 文档。
og_title: 如何检测Word文档中的字体 – 步骤详解C#教程
tags:
- C#
- Aspose.Words
- Document Processing
title: 如何在 Word 文档中检测字体 – 完整 C# 指南
url: /zh/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

block placeholders unchanged.

Let's produce final content.

Will start with the shortcodes as given.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何检测 Word 文档中的字体 – 完整 C# 指南

是否曾经想过 **如何检测缺失的字体** 在加载 Word 文件时？也许你遇到过文档在编辑器中显示正常，但生成的 PDF 却在幕后替换了几种字体。这正是字体替换的典型症状，提前捕获它可以避免布局意外。

在本教程中，我们将演示一个实用方案：使用 **Aspose.Words** 加载 `.docx`，附加警告回调，并 **如何设置回调** 以报告每一次字体替换。完成后，你不仅会了解 **如何检测字体** 的编程方法，还会掌握 **如何设置回调** 的正确方式以及 **加载 word 文档** 的安全做法——全部在一个可直接运行的 C# 示例中。

> **你将获得**
> * 完整的、可直接复制粘贴的代码示例  
> * 对每行代码的逐步解释  
> * 处理多缺失字体或自定义字体文件夹等边缘情况的技巧  
> * 预期的控制台输出，帮助你验证一切正常

---

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Core）  
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）  
- 一个故意引用了未安装字体的 Word 文件（例如 `MissingFont.docx`）  
- Visual Studio、Rider 或任意你喜欢的编辑器

不需要其他库；其余全部由标准 .NET 运行时提供。

---

## 如何检测 Word 文档中的字体

### 步骤 1：创建 Load Options 并附加警告回调

首先，我们告诉 Aspose.Words 在加载文件时需要收到任何问题的通知。这正是 **如何设置回调** 发挥作用的地方。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**为什么重要：**  
`LoadOptions` 是自定义加载过程的入口。将 `FontWarningCollector` 实例分配给 `WarningCallback` 后，Aspose.Words 每次用回退字体替换缺失字体时都会调用我们的 `Warning` 方法。这正是 **如何检测字体** 未在机器上存在的核心。

---

### 步骤 2：准备 LoadOptions 实例

现在实例化 `LoadOptions` 并挂载我们的回调。

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**小贴士：** 如果需要控制 Aspose 在何处查找替代字体，可以在这里设置 `loadOptions.FontSettings`。当服务器上有私有字体文件夹时，这非常有用。

---

### 步骤 3：加载 Word 文档

准备好选项后，我们终于 **加载 word 文档**。此时 Aspose 会解析 DOCX，如果有缺失字体，就会触发我们的回调。

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**内部发生了什么？**  
Aspose.Words 读取 DOCX 的 XML 部分，解析每个 `<w:font>` 引用，并检查系统字体集合。每当无法满足引用时，它会使用第一个匹配的回退字体并抛出 `FontSubstitution` 警告。

---

### 步骤 4：验证输出

运行程序并观察控制台。每个缺失的字体都会出现类似以下的行：

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

如果文档中没有缺失字体，控制台将保持沉默——这意味着 **如何检测字体** 没有检测到任何问题。

---

### 步骤 5：完整可运行示例（控制台应用）

下面是一个完整的 `Program.cs`，可以直接放入新建的控制台项目中。它包含了前面讨论的所有代码，并附带了一个小助手，在调试时保持控制台窗口打开。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**预期的控制台输出**（示例）：

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

如果将 `MissingFont.docx` 换成仅使用已安装字体的文件，你只会看到 “Press any key…” 那一行——这表明检测逻辑按预期工作。

---

## 常见问题与边缘情况

### 如果我想捕获 *所有* 警告，而不仅仅是字体替换该怎么办？

只需删除 `if (info.Type == WarningType.FontSubstitution)` 的判断。`WarningInfo` 对象包含一个 `Type` 枚举，你可以根据其他场景（如 `DocumentStructure`、`ImageLoading`）进行切换。

### 能否将警告写入文件而不是控制台？

完全可以。将 `Console.WriteLine` 替换为任意日志框架的调用（`Serilog`、`NLog` 等）。回调在加载文档的同一线程上执行，请确保你的日志记录器是线程安全的。

### 在 Web 应用中如何使用？

在 ASP.NET Core 中，你通常会注入一个单例的 `IWarningCallback` 实现，并通过 `LoadOptions` 传入。记得不要直接写入响应流——应将日志写入数据库或内存集合，随后通过 API 端点暴露。

### 如何使用存放在非系统文件夹中的自定义字体？

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

现在 Aspose.Words 会先在 `C:\MyCustomFonts` 中搜索，然后才回退到操作系统字体，从而减少出现替换警告的次数。

---

## 可视化概览

![检测字体警告回调在 Aspose.Words 中的表现](/images/font-warning-callback.png "使用警告回调检测字体的方式")

*该截图展示了缺失字体被替换时的控制台输出。alt 文本包含了主要的 SEO 关键词。*

---

## 结论

现在，你已经掌握了一套可靠、可投入生产的模式，用于 **如何检测字体** 在任何使用 Aspose.Words 加载的 Word 文件中。通过 **如何设置回调**，你可以实时获取缺失或被替换的字体信息，并学会了在 **加载 word 文档** 时保持代码整洁、易于维护。

接下来可以尝试将回调收集的警告存入列表，然后在 UI 或自动化报告中展示。你也可以探索 `FontSettings.SubstitutionSettings`，进一步控制选择哪些字体作为回退。

尽情实验吧——更换文档、添加更多缺失字体，或将逻辑集成到更大的文档处理流水线中。如果遇到任何问题，欢迎在下方留言或在 GitHub 上私信我。

祝编码愉快，愿你的文档始终使用期望的字体呈现！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}