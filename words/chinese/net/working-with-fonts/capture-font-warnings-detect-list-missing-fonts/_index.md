---
category: general
date: 2025-12-31
description: 在 Aspose.Words 中捕获字体警告，以检测缺失的字体并在 .NET 应用程序中列出缺失的字体。学习一步一步的 C# 解决方案。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: zh
og_description: 在 Aspose.Words 中捕获字体警告，以检测缺失的字体并列出缺失的字体。完整的 C# 指南，包含代码和技巧。
og_title: 捕获字体警告 – 检测并列出缺失的字体
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: 捕获字体警告 – 检测并列出缺失的字体
url: /zh/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 捕获字体警告 – 检测并列出缺失的字体

是否曾在加载 Word 文档时需要 **捕获字体警告**，但不确定如何显示缺失字体的详细信息？您并不孤单。在许多实际项目中，缺失的字体会导致布局错误，如果没有适当的警告，您就会追逐难以定位的 bug。

在本教程中，我们将展示如何使用 Aspose.Words for .NET **检测缺失的字体** 并 **列出缺失的字体**。结束时，您将拥有一个可直接运行的 C# 代码片段，它会打印每个替换警告，方便您记录、提醒，甚至自动替换字体。

---

## 为什么捕获字体警告很重要

当 Aspose.Words 打开一个引用了服务器上未安装字体的 DOCX 时，它会悄悄地使用后备字体进行替换。文档表面上看起来正常，但视觉忠实度受到影响——比如企业品牌标志以错误的字体呈现。

捕获这些警告可以让您：

* **保持品牌一致性** – 您可以准确知道缺失了哪些字体。
* **自动化修复** – 通过代码程序化地替换缺失的字体。
* **审计合规** – 生成法律或设计审查所需的报告。

简而言之，**捕获字体警告** 是防止静默字体替换的第一道防线。

---

## 设置 LoadOptions 以检测缺失的字体

显示警告的关键是 `LoadOptions.FontSubstitutionWarning` 属性。默认情况下它被设置为 `None`，这意味着 Aspose.Words 会吞掉这些信息。将其切换为 `All` 则会让库记录每一次替换事件。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **技巧提示：** 如果您已经有自定义字体文件夹，请在加载文档之前将其分配给 `FontSettings.SetFontsFolder("path")`。这样您就可以 **检测缺失的字体**，即系统目录中不存在的字体。

---

## 加载文档并列出缺失的字体

现在 `LoadOptions` 已经准备就绪，下一步是加载 Word 文件。构造函数接受该选项对象，任何替换都会记录在文档的 `WarningInfoCollection` 中。

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

如果文件引用了不可用的字体，每个缺失的字体都会生成一个 `WarningInfo` 条目。您可以通过遍历该集合来 **列出缺失的字体**。

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

典型的输出如下：

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

每行都准确指示缺失的字体，满足 **列出缺失的字体** 的需求。

---

## 读取并解释 WarningInfoCollection

`WarningInfoCollection` 可能包含不同类型的警告（例如 `DocumentStructure`、`ImageLoading`）。若只关注字体问题，可通过 `WarningType.FontSubstitution` 进行过滤。

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

为什么要过滤？因为大型文档可能还会产生关于损坏图像或不受支持功能的警告。通过缩小集合范围，您可以避免噪音，使 **捕获字体警告** 的输出保持整洁。

---

## 完整示例 – 实际捕获字体警告

下面是完整的、独立的程序，您可以将其放入任何 .NET 控制台项目中。它演示了从配置 `LoadOptions` 到打印整洁的缺失字体列表的每一步。

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**预期的控制台输出**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

如果文档中没有缺失的字体，您将看到：

```
All referenced fonts are available – no warnings captured.
```

---

## 常见边缘情况及处理方法

| 情况 | 产生原因 | 推荐解决方案 |
|---|---|---|
| **文档使用嵌入的 OpenType 字体** | Aspose.Words 能读取嵌入的字体，但前提是文件未损坏。 | 首先在 Word 中检查 DOCX；如有必要，重新嵌入字体。 |
| **大量警告**（例如 200+ 缺失字体） | 旧系统的大批量导入通常引用了大量字体。 | 批量处理警告：将其存入数据库，然后运行字体安装脚本。 |
| **WarningInfoCollection 为空** | 要么文档已包含所有字体，要么 `FontSubstitutionWarning` 仍为 `None`。 | 再次检查 `LoadOptions` 配置，并确保加载了正确的文件路径。 |
| **自定义字体位于网络共享** | 网络延迟可能导致字体查找超时。 | 使用 `SetFontsFolder` 将字体预加载到 `FontSettings`，并设置 `CacheFontData = true`。 |

这些技巧帮助您在复杂环境中可靠地 **检测缺失的字体**。

---

## 图片示例

![捕获字体警告示例](https://example.com/images/capture-font-warnings.png "捕获字体警告示例")

*该截图显示了控制台运行时报告了两个缺失的字体。*

---

## 下一步 – 超越简单报告

既然您已经可以 **捕获字体警告**，可以考虑自动化修复：

1. **自动字体替换** – 通过修改 `FontSettings.SubstitutionSettings` 将缺失的字体替换为公司批准的后备字体。
2. **记录到监控系统** – 将警告信息导入 Serilog、ELK 或 Azure Application Insights。
3. **面向用户的报告** – 生成 HTML 或 PDF 摘要，供设计师审查需要安装的字体。

所有这些扩展都基于我们所介绍的相同基础：配置 `LoadOptions`、加载文档以及读取 `WarningInfoCollection`。

---

## 结论

您刚刚学习了如何在 Aspose.Words 中 **捕获字体警告**、**检测缺失的字体**，以及使用简洁的控制台友好输出 **列出缺失的字体**。该方法直观，只需几行 C# 代码，且适用于任何支持 Aspose.Words 23.x 或更高版本的 .NET。

在一个引用了您故意卸载的字体的示例 DOCX 上尝试一下——您会立即看到警告出现。随后，您可以决定是安装缺失的字体、通过代码进行替换，还是仅记录该问题以供后续审查。

祝编码愉快，愿您的文档始终使用正确的字体呈现！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}