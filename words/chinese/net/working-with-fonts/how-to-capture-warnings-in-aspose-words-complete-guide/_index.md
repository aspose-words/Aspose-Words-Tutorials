---
category: general
date: 2026-03-13
description: 如何在使用 Aspose.Words 加载文档时捕获警告，以及处理缺失字体和设置自定义字体的技巧。学习完整的 C# 解决方案。
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: zh
og_description: 如何在使用 Aspose.Words 加载 Word 文件时捕获警告，并提供处理缺失字体和设置自定义字体的实用方法。
og_title: 如何捕获 Aspose.Words 警告 – 完整指南
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何捕获 Aspose.Words 警告 – 完整指南
url: /zh/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕获 Aspose.Words 警告 – 完整指南

有没有想过 **如何捕获警告**，当 Aspose.Words 加载文档时弹出？在许多真实项目中，你会看到字体替换提醒、已弃用特性提示，甚至安全相关的消息。忽视它们就像开着挡风玻璃裂开的车——你可能到达目的地，但永远不知道何时会出现故障。

好消息是，Aspose.Words 为你提供了一种简洁的基于回调的方式来拦截这些信息。在本教程中，我们将逐步演示一个 **完整的 C# 示例**，不仅捕获警告，还展示如何 **处理缺失字体** 并 **设置自定义字体设置**，让文档渲染如你所期望。

---

## 您将学到

- 配置 `LoadOptions` 以插入自定义 `FontSettings` 对象。  
- 注册一个警告回调，仅过滤 `FontSubstitution` 事件。  
- 将警告详情输出到控制台（或您喜欢的任何日志记录器）。  
- 扩展解决方案，以在不同平台上优雅地处理缺失字体。  

通过本指南的学习，你将拥有一个可直接运行的代码片段，能够放入任何 .NET 项目中，并获得一系列实用技巧，帮助你避免常见陷阱。

---

## 前提条件

| 要求 | 为什么重要 |
|------|------------|
| **Aspose.Words for .NET** (v23.12 或更高) | 我们使用的 API（`LoadOptions`、`IWarningCallback`）位于此处。 |
| **.NET 6+**（或 .NET Framework 4.7.2+） | 现代语言特性让代码更简洁。 |
| **示例 DOCX**（名为 `input.docx`）放置在已知文件夹中 | 我们需要加载它以触发警告。 |
| **控制台或日志框架**（可选） | 用于查看捕获的警告。 |

无需额外的 NuGet 包，除了 Aspose.Words 本身。

---

## 步骤 1：设置自定义字体设置  

在加载文档之前，你可以告诉 Aspose.Words 去哪里查找字体。这就是 **设置自定义字体设置** 的关键环节。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**为什么这很重要：**  
如果 DOCX 引用了机器上未安装的字体，Aspose.Words 将在未配置所需字体文件夹的情况下悄悄使用回退字体。通过设置自定义文件夹，你可以从根本上降低 “字体替换” 警告的概率。

> **专业提示：** 在 Linux 上，您可能需要添加 `fonts-dejavu-core` 包或任何文档依赖的 TrueType 集合。

---

## 步骤 2：注册警告回调  

Aspose.Words 实现了 `IWarningCallback`。我们将创建一个小型处理器，仅打印我们关心的警告：缺失或被替换的字体。

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**为什么这很重要：**  
**处理缺失字体** 的情形现在对你可见。你不再需要猜测哪个字体被替换，而是会得到类似 “Font 'Calibri' was substituted with 'Arial'” 的清晰描述。这在调试生成的 PDF 或打印报告的布局问题时极其宝贵。

---

## 步骤 3：使用配置的选项加载文档  

现在我们终于将文档加载到内存中，使用刚才准备好的 `LoadOptions`。

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

如果源文件使用的字体不在 `C:\MyFonts` 中，你会看到类似以下的输出：

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

那行就是你想要的 **如何捕获警告** 的结果。

---

## 步骤 4：完整工作示例（可复制粘贴）

下面是完整的程序，已准备好编译。将其粘贴到新的控制台项目并运行——只需确保路径指向机器上的真实位置。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**预期输出：**  

- 如果所有字体都可用：  
  `Document processed. Check console for any warning messages.`  

- 如果缺少字体：  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## 步骤 5：常见变体与边缘情况  

| 情况 | 需要调整的内容 |
|------|----------------|
| **多个字体文件夹** | 对每个额外位置调用 `fontSettings.AddFontFolder(@"C:\MoreFonts", true);`。 |
| **抑制所有警告** | 实现 `Warn` 但保持方法体为空，或将 `loadOptions.WarningCallback = null;`。 |
| **捕获其他警告类型** | 将 `info.WarningType` 与 `WarningType.DeprecatedFeature`、`WarningType.UnexpectedContent` 等进行比较。 |
| **在 Linux/macOS 上运行** | 确保字体文件夹包含 Linux 兼容的 `.ttf`/`.otf` 文件；可能需要安装 `libfontconfig`。 |
| **大文档** | 考虑流式加载文档（`LoadOptions.LoadFormat = LoadFormat.Docx;`），以降低内存压力。 |

通过预先考虑这些情形，你可以避免在从开发机迁移到 CI 流水线或云 VM 时出现意外。

---

## 步骤 6：可视化确认（可选）

如果你更喜欢快速的视觉提示，可以将捕获的警告导出为小型 HTML 报告。下面是一段将信息写入 `warnings.html` 的简短代码片段：

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

加载文档后，调用 `handler.WriteReport(@"C:\Docs\warnings.html");` 并在浏览器中打开。下图展示了报告可能的外观：

![How to capture warnings screenshot](/images/capture-warnings.png)

*Alt text:* **如何捕获警告** – 控制台输出和 HTML 报告的截图。

---

## 结论  

我们已经介绍了在 Aspose.Words 中 **如何捕获警告**，演示了可靠的 **处理缺失字体** 方法，并展示了如何 **设置自定义字体设置** 以实现确定性的渲染。完整示例已准备好放入任何 .NET 解决方案，模块化的 `FontWarningHandler` 也可以扩展以适配你的日志或遥测策略。

下一步？尝试将 `Console.WriteLine` 调用替换为结构化日志记录器（如 Serilog），或将警告推送到 Application Insights 进行实时监控。如果需要在加载后检查文档内容，还可以探索 `DocumentVisitor` 模式。

对其他警告类型或字体嵌入策略有疑问？在下方留言——祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}