---
category: general
date: 2026-02-21
description: 学习如何在 C# 中使用 Aspose.Words 启用警告、检测缺失字体以及安全加载 docx。请遵循分步指南。
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: zh
og_description: 如何在 Aspose.Words 中启用警告、检测缺失字体并正确加载 docx 文件。附带完整代码示例。
og_title: 如何在加载 DOCX 时启用警告并检测缺失的字体
tags:
- C#
- Aspose.Words
- Document processing
title: 如何在加载 DOCX 文件时启用警告并检测缺失的字体
url: /zh/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

检测缺失字体". Keep same heading level.

Proceed.

Translate paragraphs.

Be careful with bold text **...** keep bold but translate inside.

Also keep code block placeholders.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在加载 DOCX 文件时启用警告并检测缺失字体

是否曾想过 **如何在缺失字体时启用警告**，以免它们悄悄破坏文档渲染？你并不孤单——大多数开发者默认库会“自行处理”，结果后来才发现字体被替换，却毫无线索。

在本教程中，我们将展示 **如何启用警告**、**如何检测缺失字体**，以及使用 Aspose.Words for .NET 正确 **如何加载 docx** 的方法。完成后，你将拥有一个可直接运行的示例，能够将所有字体替换警告打印到控制台，从此不再猜测文件内部发生了什么。

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）  
- Visual Studio 2022 或任意你喜欢的 C# IDE  
- **Aspose.Words** NuGet 包（`Install-Package Aspose.Words`）  
- 一个可能包含未在机器上安装的字体的 DOCX 文件（我们称之为 `input.docx`）

> **专业提示：** 如果没有测试文件，只需打开一个使用自定义企业字体的 Word 文档并另存为 `input.docx`。这就会触发我们想捕获的警告。

## 解决方案概览

1. **创建** 一个 `LoadOptions` 对象并打开 `FontSubstitutionWarnings`。  
2. **加载** DOCX 文件时使用该选项。  
3. **检查** `WarningCallback` 集合中是否有 `FontSubstitution` 条目。  
4. **响应**——你可以记录、显示，甚至在代码中替换缺失的字体。

下面我们将逐步拆解每一步，说明 *为什么* 重要，并提供完整、可运行的代码片段。

---

## 步骤 1：安装 Aspose.Words 并创建项目

在我们能够 **如何启用警告** 之前，需要先获取实际支持该功能的库。

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

或者，在 Visual Studio 包管理器控制台中：

```powershell
Install-Package Aspose.Words
```

> **为什么要执行此步骤？**  
> 没有该包，`LoadOptions`、`Document` 以及警告基础设施根本不存在。添加 NuGet 引用可确保你获取最新的稳定版本（截至本文撰写时为 24.5）。

---

## 步骤 2：创建启用字体替换警告的加载选项

**如何启用警告** 的核心就在 `LoadOptions` 类。将 `FontSubstitutionWarnings` 设置为 `true`，即可让引擎记录每一次缺失字体的替换。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **为什么要打开此标志？**  
> 默认情况下，Aspose.Words 会悄悄将缺失字体替换为回退字体（通常是 Arial），这可能导致布局错位、字符不可见或品牌违规。打开该标志后，你将获得完整可见性。

---

## 步骤 3：使用配置好的选项加载 DOCX 文件

现在我们已经掌握 **如何加载 docx** 并打开警告，接下来实际执行加载操作。

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **内部发生了什么？**  
> 在解析 DOCX 时，Aspose.Words 会检查每个 `<w:rFonts>` 元素。如果指定的字体未安装，它会记录一个 `FontSubstitution` 警告并回退到默认字体。由于我们已启用警告，这些条目会出现在 `document.WarningCallback.Warnings` 中。

---

## 步骤 4：获取并显示字体替换警告

`WarningCallback` 属性保存一个 `WarningInfoCollection`。遍历该集合，筛选出 `WarningType.FontSubstitution`，并输出相应信息。

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**预期输出**（示例）：

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **这些信息该如何处理？**  
> 你可以将它们写入日志文件、在 UI 中展示，甚至触发自定义的字体回退逻辑。关键是现在你能够 *检测缺失字体*，而不必事后猜测。

---

## 步骤 5：（可选）使用特定回退字体替换缺失字体

如果你有企业统一的字体需要强制使用，可以在处理警告时即时替换。

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **为什么要考虑这个方案？**  
> 它能确保所有生成的文档在视觉上保持一致，这对品牌合规性至关重要。

---

## 完整可运行示例

下面是一段可以直接复制到控制台应用的单文件 C# 代码，涵盖从安装包到打印警告的全部过程。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**运行方式**：在项目文件夹中执行 `dotnet run`。如果有缺失的字体，你将看到相应的警告被打印，且可选的替换将在保存文件前生效。

---

## 常见问题

### 这在 PDF 转换时也有效吗？

是的。处理完警告后，你可以调用 `doc.Save("output.pdf")`，PDF 中的字体替换将与 DOCX 中保持一致。

### 如何对特定字体抑制警告？

在遍历循环时过滤掉 `Message` 中包含该字体名称的 `WarningInfo` 即可。

### `FontSubstitutionWarnings` 在旧版 Aspose.Words 中可用吗？

该属性自 20.5 版本起引入。如果你仍在使用更旧的版本，请通过 NuGet 升级；API 变更向后兼容。

---

## 结论

我们已经完整演示了 **如何启用警告**、**检测缺失字体**，并展示了使用 Aspose.Words 正确 **如何加载 docx**、保持对字体替换的全程可视化。通过检查 `document.WarningCallback.Warnings`，你可以获得可靠的审计轨迹——不再有静默的回退。

下一步可以尝试将警告逻辑接入 Serilog 等日志框架，或构建一个 UI 在文档交付前高亮缺失字体。你也可以进一步探索 `FontSettings` 类，以实现更细粒度的字体替换策略。

祝编码愉快，愿你的文档始终如你所愿地渲染！ 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}