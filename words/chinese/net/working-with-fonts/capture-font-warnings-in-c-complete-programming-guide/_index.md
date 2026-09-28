---
category: general
date: 2026-02-18
description: 学习如何在 C# 中使用 Aspose.Words 捕获字体警告并检测缺失的字体。请按照本分步指南高效处理缺失字体。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: zh
og_description: 在 C# 中捕获字体警告，并学习检测缺失字体、处理缺失字体以及列出缺失字体，提供完整代码示例。
og_title: 在 C# 中捕获字体警告 – 完整指南
tags:
- Aspose.Words
- C#
- Font Management
title: 在 C# 中捕获字体警告 – 完整编程指南
url: /zh/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

arnings in C# – Complete Programming Guide" translate: "# 在 C# 中捕获字体警告 – 完整编程指南"

Proceed.

Will translate each paragraph.

Let's produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中捕获字体警告 – 完整编程指南

是否曾想过在文档引用了服务器上未安装的字体时**捕获字体警告**？你并不是唯一有此困扰的人。在许多企业应用中，缺失的字体会导致布局错乱，而唯一可靠的发现方式就是监听库抛出的警告。

在本教程中，我们将展示一个可直接运行的方案，不仅能够**捕获字体警告**，还能**检测缺失字体**、**处理缺失字体**，甚至**列出缺失字体**，让你决定是替换、嵌入还是提示用户。无需外部文档——复制、粘贴、运行即可。

## 你将学到

- 如何配置 `LoadOptions` 以打开字体替换警告。  
- 加载 DOCX 并提取所有警告的完整代码。  
- 每一步为何重要，包括性能考量。  
- 边缘情况处理，例如混合脚本字体或自定义字体文件夹的文档。  

**先决条件**：.NET 6+（或 .NET Framework 4.6+），引用 **Aspose.Words** NuGet 包，并具备 C# 基础。如果你从未使用过 Aspose.Words，也无需担心——本指南会逐步带你了解每个细节。

![展示捕获字体警告流程的图示](image.png){alt="捕获字体警告示意图"}

## 捕获字体警告 – 为什么重要

当 Aspose.Words 加载文档时，会悄悄将任何不可用的字体替换为回退字体。该回退可以让加载继续，但视觉效果可能完全偏离预期。通过打开 **SubstitutionWarningLevel.All** 标志，库会为每个缺失的字体添加一条 `WarningInfo` 条目，从而让你在文档渲染或保存之前**检测缺失字体**。

> **专业提示**：如果你在批处理作业中处理数百个文件，将这些警告记录到集中存储可以为后续的手动 QA 节省数小时的时间。

## 步骤 1：设置项目

1. 打开你喜欢的 IDE（Visual Studio、Rider、VS Code）。  
2. 创建一个新的控制台项目：

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. 添加 Aspose.Words 包：

```bash
dotnet add package Aspose.Words
```

就这么简单——无需额外 DLL、无需 COM 互操作。库已经包含了处理**缺失字体**所需的一切。

## 步骤 2：准备 LoadOptions 以捕获所有字体替换警告

要让引擎**捕获字体警告**，必须告诉它记录每一次替换。下面的代码片段创建了 `LoadOptions` 实例，启用警告级别，并（可选）指向包含自定义字体的文件夹。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**这样做的意义**：  
- `SubstitutionWarningLevel.All` 确保**每一次**缺失字体事件都会被记录，而不仅仅是第一次。  
- 若不设置此标志，Aspose.Words 会悄悄替换字体，你永远不知道问题的存在。

## 步骤 3：使用配置好的选项加载文档

现在真正打开文件。将 `DocumentWithMissingFonts.docx` 替换为你的测试文档路径。

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

如果文件中包含任何在机器上（或你添加的可选文件夹中）不存在的字体，`document.WarningInfoCollection` 将被填充。

## 步骤 4：查找并显示所有字体替换警告

下面是本教程的核心：遍历 `WarningInfoCollection` 以**列出缺失字体**。我们会按 `WarningType.FontSubstitution` 过滤，并打印友好的信息。

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### 预期输出

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

如果文档仅使用已安装的字体，你会看到 “✅ 未检测到缺失字体” 这一行。

## 步骤 5：进阶 – 如何**程序化处理缺失字体**

仅打印列表可能对诊断工具足够，但许多生产系统需要**自动处理缺失字体**。下面提供两种常见策略：

### 5.1 使用已知回退字体进行替换

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 动态嵌入自定义字体

如果你有企业字体文件（`MyBrand.ttf`），可以在检测到缺失字体时将其嵌入：

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **注意**：嵌入字体会增加输出文件大小，请在保真度与带宽之间权衡。

## 常见陷阱及规避方法

| 症状 | 可能原因 | 解决方案 |
|------|----------|----------|
| 即使文档显示异常也没有警告 | 未将 `SubstitutionWarningLevel` 设置为 `All` | 确认第 2 步严格按照示例设置标志 |
| 警告中同一字体出现多次 | 文档在多个样式中使用了该字体 | 如只需唯一列表，可使用 `fontWarnings.Select(w => w.Description).Distinct()` 去重 |
| 大型 DOCX 文件导致应用崩溃 | 使用默认内存设置加载 | 使用 `LoadOptions.LoadFormat` 或流式读取文件以降低内存压力 |

## 完整可运行示例（复制‑粘贴即用）

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

使用 `dotnet run` 运行程序。你应该会在控制台看到缺失字体列表，证明已成功**捕获字体警告**。

## 结论

现在，你已经掌握了使用 Aspose.Words 在 C# 中**捕获字体警告**、**检测缺失字体**、**处理缺失字体**以及**列出缺失字体**的完整、可投入生产的模式。该方案轻量、代码行数少，且可直接嵌入任何现有流水线——无论你

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}