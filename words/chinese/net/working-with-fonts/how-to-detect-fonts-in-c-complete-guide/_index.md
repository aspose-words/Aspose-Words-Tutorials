---
category: general
date: 2026-04-02
description: 如何使用 Aspose.Words 在 C# 文档中检测字体。学习配置字体设置并高效处理缺失的字体。
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: zh
og_description: 如何使用 Aspose.Words 检测 C# 文档中的字体。本指南展示了如何配置字体设置以及处理缺失的字体。
og_title: 如何在 C# 中检测字体 – 完整指南
tags:
- C#
- Aspose.Words
- Document Processing
title: 如何在 C# 中检测字体 – 完整指南
url: /zh/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中检测字体 – 完整指南

有没有想过在 .NET 中加载 Word 文档时，如何检测缺失或被替代的 **字体**？你并不是唯一遇到这个问题的人——开发者经常在文档引用服务器上未安装的字体时卡住。好消息是 Aspose.Words 为你提供了一种简洁、可编程的方式来发现这些缺口。

在本教程中，我们将通过一个实战示例，展示 **如何检测字体**，并演示如何 **配置字体设置** 与 **优雅地处理缺失字体**。完成后，你将拥有一个可直接运行的代码片段，能够打印所有字体替换警告，以便记录、提醒或替换字体。

---

## 您需要的条件

- **Aspose.Words for .NET**（最新版本效果最佳；下面的代码针对 .NET 6+）
- .NET 开发环境（Visual Studio、Rider 或 VS Code）
- 一个引用了你未安装字体的示例 `.docx`（非常适合测试）

无需除 Aspose.Words 之外的额外 NuGet 包，且该方案在 Windows、Linux 和 macOS 上均可运行。

---

## 步骤 1：安装并引用 Aspose.Words

首先，将库添加到项目中。NuGet 命令非常直接：

```bash
dotnet add package Aspose.Words
```

> **专业提示：** 如果你在 CI 服务器上，固定包的版本以避免意外的破坏性更改。

---

## 步骤 2：配置字体设置（并准备加载选项）

在打开文档之前，你可以告诉 Aspose.Words 去哪里查找回退字体。这就是 **配置字体设置** 的环节，能够防止引擎在不希望的情况下悄悄替换字体。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

为什么要这么做？如果文档引用了 *Comic Sans*，但服务器上只有 *Calibri*，Aspose.Words 会替换为 *Calibri* 并抛出警告。通过配置搜索路径，你可以减少不必要的惊喜。

---

## 步骤 3：使用准备好的选项加载文档

现在我们真正打开文件。前一步构建的 `LoadOptions` 直接传递给 `Document` 构造函数。

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

如果文件找不到或已损坏，会抛出异常——因此在生产代码中建议使用 try/catch 包裹。

---

## 步骤 4：扫描文档警告以检测字体替换

Aspose.Words 在解析时会收集一系列警告。其中，`FontSubstitutionWarning` 能准确告诉你哪个字体被替换了。

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

`Warnings` 集合中可能还包含其他项目（例如 `DocumentStructureWarning`）。过滤 `FontSubstitutionWarning` 能确保我们只报告关注的 **处理缺失字体** 场景。

---

## 步骤 5：整合所有代码 – 完整、可运行的示例

下面是完整程序。复制粘贴到新的控制台应用并运行；你将看到每个缺失字体在控制台中打印出来。

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**预期输出**（示例）：

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

如果文档只使用了机器上已存在的字体，你会看到 “No font substitutions detected” 那一行。

---

## 边缘情况与常见问题

### 如果文档根本没有 **警告** 呢？

这仅表示所有引用的字体都在你配置的搜索文件夹中找到了。示例中的 `anySubstitutions` 标志已经处理了这种情况。

### 我可以把警告 **记录** 到文件而不是控制台吗？

完全可以。将 `Console.WriteLine` 调用替换为你选择的日志框架（Serilog、NLog 等）。如果需要更详细的信息，`WarningInfo` 对象还提供 `WarningType` 和 `WarningMessage`。

### 我如何 **忽略** 某些字体，例如不应被替换的公司品牌字体？

你可以添加自定义替换规则：

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

此后 Aspose.Words 只会将 *MyBrandFont* 替换为列出的备选项，同时仍会抛出可供处理的警告。

### 这在 **Linux** 容器上可用吗？

可以——只需确保挂载包含所需 `.ttf`/`.otf` 文件的文件夹，并将 `SetFontsFolder` 指向该路径。Aspose.Words 并不依赖操作系统预装的字体。

---

## 可视化概览

![如何检测字体 流程图](detect-fonts.png "展示文档中检测字体步骤的图示")

*图片替代文字:* **如何检测字体** 流程图，展示配置、加载和警告检查。

---

## 回顾 – 我们学到了什么

- **如何检测字体**，通过 Aspose.Words 警告发现缺失或被替代的字体。  
- 如何 **配置字体设置**，指向自定义字体文件夹并设置默认回退。  
- 处理 **缺失字体** 的策略，包括记录日志和自定义替换规则。

所有这些都封装在一个紧凑的、独立的控制台应用中，随时可以放入任何 .NET 解决方案。

---

## 下一步与相关主题

- **嵌入字体** 直接到输出文档，以避免后续替换（`SaveOptions` 配合 `EmbedFullFonts`）。  
- **编程式字体替换** —— 在保存前将缺失字体替换为特定的备选字体。  
- **性能调优** —— 在批量处理大量文档时缓存 `FontSettings`。

如果你对这些主题感兴趣，搜索 *configure font settings* 和 *handle missing fonts* 即可找到更深入的 Aspose.Words 字体管理指南。

祝编码愉快！遇到奇怪的字体边缘情况？留下评论，我们一起排查。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}