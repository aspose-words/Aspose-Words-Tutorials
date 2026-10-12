---
category: general
date: 2026-01-11
description: 启用字体替换警告，以检测 .NET 文档中缺失的字体。了解如何使用 Aspose.Words 获取缺失的字体名称并列出缺失的字体。
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: zh
og_description: 在 Aspose.Words 中启用字体替换警告，以检测缺失的字体、获取缺失字体名称，并列出文档中缺失的字体。
og_title: 启用字体替换警告 – 步骤详解 C# 教程
tags:
- Aspose.Words
- C#
- Document Processing
title: 在 Aspose.Words 中启用字体替换警告 – 完整指南
url: /zh/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 启用字体替换警告 – 完整指南

有没有想过为什么在服务器上加载 Word 文档后，它看起来有点不对劲？很可能是原作者使用的字体在你的机器上不可用，Aspose.Words 会悄悄地将其替换为最接近的字体。**启用字体替换警告**，你就能立即知道缺少哪些字体、它们被替换成什么，以及如何根据这些信息采取行动。

在本教程中，我们将演示一个实用的端到端示例，展示如何**检测缺失字体**、获取**缺失字体名称**，甚至**列出缺失字体**以便报告。没有冗余，只提供一个可以直接在任何 .NET 项目中使用的清晰解决方案。

---

## 您将学习到

- 如何配置 `LoadOptions` 以使 Aspose.Words 发出详细的警告。
- 加载文档并枚举与字体相关的警告所需的完整代码。
- 提取缺失字体名称及其替代字体的方法，然后输出整洁的报告。
- 处理边缘情况的技巧，例如包含数十种缺失字体的文档或自定义字体文件夹。

### 前提条件

- .NET 6+（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET 23.10 或更高版本（可从 NuGet 获取）
- 一个引用了你未安装字体的示例 DOCX（我们称之为 `MissingFont.docx`）

如果你已经具备这些基础，让我们开始吧。

---

## 步骤 1：设置 LoadOptions 以启用字体替换警告  

首先需要告诉 Aspose.Words 你关心缺失的字体。默认情况下，库只在内部记录警告。将 `SubstitutionWarningLevel` 设置为 `Typical`（或 `All` 以获得最详细的输出）即可打开此功能。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**为什么这很重要：**  
当设置了 `SubstitutionWarningLevel` 时，每当 Aspose.Words 找不到引用的字体时，它会向文档的 `Warnings` 集合中添加一个 `FontSubstitutionWarning`。该集合是无需手动解析文档即可**检测缺失字体**的唯一可靠方式。

> **专业提示：** 如果你一次处理一批文档，并且想确保捕获所有替换，请使用 `FontSubstitutionWarningLevel.All`。虽然会产生更多噪音，但能保证没有警告被遗漏。

---

## 步骤 2：使用配置好的选项加载文档  

现在警告系统已经准备就绪，使用我们刚才配置的 `LoadOptions` 加载你的 DOCX。路径可以是绝对路径或相对路径；只需确保文件存在即可。

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**内部发生了什么？**  
Aspose.Words 解析文档的 XML，解析每个 `<w:font>` 元素，并检查系统的字体目录（以及你可能已添加到 `FontSettings` 的任何自定义文件夹）。当它找不到字体时，会记录一个警告——这正是我们稍后**列出缺失字体**所需要的。

---

## 步骤 3：遍历警告并提取缺失字体详情  

文档加载到内存后，`Warnings` 集合中包含所有 `FontSubstitutionWarning`。我们将遍历它，筛选出相应类型，并打印友好的报告。

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**预期输出**（假设源文档引用了未安装的 `MyCustomFont`）：

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

请注意，每条记录同时提供了**缺失字体名称**（`MyCustomFont`）和替代字体（`Arial`）。这正是决定是嵌入原始字体、向作者请求替换，还是直接接受替换所需的信息。

---

## 步骤 4（可选）：将数据收集到列表中以便后续处理  

如果需要将报告导出为 CSV、通过 API 发送，或仅在内存中保存以供后续使用，可以将警告存入强类型列表中。

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

现在你已经以任何下游系统都能使用的格式**列出缺失字体**。无论是为仪表盘提供数据还是生成审计日志，数据都已准备就绪。

---

## 步骤 5：处理边缘情况和常见陷阱  

### 单次运行中出现多个缺失字体  

大型企业模板通常引用数十种自定义字体。警告集合可能会变得相当庞大，但上述遍历模式是线性扩展的，性能不会成为问题。只需记得保持输出可读——如果需要更深入的分析，可按页面或样式分组。

### 自定义字体文件夹  

如果将字体存放在非标准目录（例如共享网络磁盘），需要告诉 Aspose.Words 去哪里查找：

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

在加载文档*之前*设置此项，让库有机会找到字体，这可能会完全消除部分警告。

### 抑制特定警告  

有时你知道某些特定的替换是可以接受的（例如装饰性字体，你并不介意替换）。可以在事后过滤掉这些警告：

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### 版本兼容性  

`FontSubstitutionWarningLevel` 枚举自 Aspose.Words 20.12 起保持稳定。如果使用的是更旧的版本，可能需要升级才能使用警告级别功能。

---

## 完整工作示例  

下面是完整的、可直接运行的程序，包含上述所有步骤。将其粘贴到新的控制台项目中，添加 Aspose.Words NuGet 包，并将 `docPath` 指向引用缺失字体的文档。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

运行此程序将**启用字体替换警告**、**检测缺失字体**、**获取缺失字体名称**，并在控制台和 CSV 文件中**列出缺失字体**。

---

## 结论  

我们已经完整介绍了在 Aspose.Words 中**启用字体替换警告**的全部内容，从最初的配置到提取干净的缺失字体列表。按照上述步骤操作，你就能审计文档、确保视觉一致性，并避免在服务器渲染时出现意外问题。

接下来，你可能想要探索：

- **将缺失字体嵌入**到输出的 PDF 或 DOCX 中（使用 `FontSettings.EmbeddedFonts`）。
- 根据生成的报告**自动在构建代理上安装字体**。
- **将 CI 流水线集成**，在关键字体缺失时使构建失败。

尝试这些，你就能把简单的警告系统转变为完整的字体管理工作流。

祝编码愉快，愿所有字体都能被找到！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}