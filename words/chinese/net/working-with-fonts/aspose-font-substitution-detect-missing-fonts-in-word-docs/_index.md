---
category: general
date: 2026-05-04
description: 学习如何使用 Aspose 字体替换在加载 Word 文档时检测缺失的字体并获取缺失字体的详细信息——一步步指南。
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: zh
og_description: 精通 Aspose 字体替换，在加载 Word 文档时检测缺失字体，并使用完整的 C# 代码检索缺失字体信息。
og_title: Aspose 字体替换 – 检测 Word 文档中缺失的字体
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose 字体替换：检测 Word 文档中缺失的字体
url: /zh/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose 字体替换 – 检测 Word 文档中缺失的字体

有没有想过为什么同一份 Word 文档在不同机器上显示异常？通常是因为缺少字体，而 **Aspose 字体替换** 可以帮助你在问题变成视觉灾难之前发现这些缺口。在本教程中，我们将演示如何在 **加载 Word 文档** 的瞬间 **检测缺失的字体**，以及随后 **检索缺失字体** 的详细信息，以便你进行修复或替换。

我们将覆盖从设置警告回调到获取干净的缺失字体列表的全部步骤。完成后，你将拥有一个可直接运行的 C# 代码片段，准确告诉你哪些字体未被找到，并且你会明白这对文档保真度为何如此重要。

---

## 前置条件 – 开始之前需要准备的内容

- **Aspose.Words for .NET**（建议使用 v23.12 或更高版本）。  
- .NET 开发环境（Visual Studio、Rider 或 `dotnet` CLI）。  
- 一个有意使用了你未安装字体的示例 DOCX，命名为 `DocumentWithMissingFont.docx`。  
- 基础的 C# 知识——不需要高级技巧，只要能运行控制台应用即可。

如果上述任意项你不熟悉，请暂停并安装 NuGet 包：

```bash
dotnet add package Aspose.Words
```

就这么简单。无需额外字体，也不需要外部服务。

---

## 步骤 1：加载 Word 文档（并触发字体检查）

首先要 **加载 Word 文档**。Aspose.Words 会解析文件，如果找不到引用的字体，就会排队一个 *FontSubstitution* 警告。下面的代码演示了加载过程：

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **为什么重要：** 及早加载文档让 Aspose 有机会扫描每一段文字、样式和嵌入对象。如果系统或自定义字体文件夹中找不到某个字体，稍后就会收到警告。

---

## 步骤 2：附加警告回调以捕获替换事件

Aspose.Words 使用回调机制通知你诸如缺失字体之类的问题。通过将 `IWarningCallback` 的实现分配给 `doc.WarningCallback`，即可在警告产生时拦截它们。

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **小技巧：** 你可以通过组合模式包装多个回调（例如日志、UI 更新），但在本教程中使用单一回调即可保持思路清晰。

---

## 步骤 3：实现字体替换警告回调

现在我们定义实际执行工作的类。回调会收到一个 `WarningInfo` 对象；我们筛选 `WarningType.FontSubstitution` 并将描述保存以供后续使用。

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **正在发生什么：** 当 Aspose 遇到缺失的字体时，会生成类似 “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” 的警告。我们的回调会打印该行并保存下来。

---

## 步骤 4：处理文档（可选）并收集缺失字体

如果你仅需 **检测缺失的字体**，加载步骤已经足够——警告会自动触发。不过，许多开发者在完成某些操作（如保存、转换）后仍需要 **检索缺失字体** 信息。下面我们强制执行一个小操作——保存为 PDF——以确保所有警告都被发出，然后提取收集到的消息。

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **预期的控制台输出**（示例）：
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

请注意，每一行都清晰地说明了原始字体以及 Aspose 选择的回退字体。这正是 **aspose font substitution** 报告的核心。

---

## 步骤 5：进阶 – 使用自定义字体源以减少替换

有时你 *确实* 拥有缺失的字体，只是它们不在默认系统文件夹中。Aspose.Words 允许你通过 `FontSettings` 指向自定义目录。添加此步骤可以显著降低替换警告的数量。

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **为什么要添加？** 如果你在多台机器间分发文档，将所需字体打包到已知文件夹可以确保在任何地方都有相同的视觉效果。它还能让你的 **detect missing fonts** 过程更准确，因为 Aspose 会先检查该文件夹再回退。

---

## 完整可运行示例

将所有代码组合在一起，下面是一个可直接复制粘贴的控制台程序。将其保存为 `Program.cs` 并使用 `dotnet run` 运行。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**运行结果示例：** 如果源 DOCX 引用了你未安装的字体，控制台会打印每条替换信息并给出简要汇总。若所有字体均已存在，则会显示 “No missing fonts were detected.” 的提示。

---

## 常见问题及解决方案

| 问题 | 产生原因 | 解决办法 |
|------|----------|----------|
| **未出现任何警告** | 文档仅使用系统字体，或已添加包含缺失字体的自定义文件夹。 | 确认 DOCX 确实引用了不可用的字体。可在 Word 中将段落设置为罕见字体（例如 “Papyrus”）。 |
| **重复的警告信息** | 同一字体在多个文本运行中被使用，导致多次警告。 | 如只需唯一列表，可使用 `Distinct()` 去重。 |
| **大文档性能下降** | 每条警告都在 UI 线程上处理。 | 将加载放在后台任务中执行，或在后处理时使用 `Parallel.ForEach`。 |
| **回退字体不符合品牌** | Aspose 的默认回退字体可能不符合你的品牌要求。 | 设置 `FontSettings.SubstitutionSettings.DefaultFontName` 为首选回退字体（例如 “Calibri”）。 |

---

## 扩展方案 – 将缺失字体导出为 JSON

如果你在构建需要向客户端报告缺失字体的 Web 服务，序列化列表非常简单：

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

现在你的 API 可以返回干净的 JSON 负载，供其他系统消费。

---

## 结论

本指南从头到尾演示了 **Aspose 字体替换**：加载 Word 文档、附加警告回调、捕获每个 *detect missing fonts* 事件，最终 **检索缺失字体** 信息用于报告或修复。通过添加可选的自定义字体文件夹，你可以显著减少替换数量；再加几行代码，还能将结果导出为 JSON。

请记住，文档的视觉完整性取决于所使用的字体。使用本教程中的技术，你再也不会因意外的回退字体而感到惊讶。

准备好迈出下一步了吗？尝试将此逻辑集成到更大的文档处理流水线中，或探索 Aspose.Words 的其他功能，如字体嵌入（`doc.FontSettings.EmbeddedFonts`）。可能性无限，你的用户也会因更精致的输出而感激不已。

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}