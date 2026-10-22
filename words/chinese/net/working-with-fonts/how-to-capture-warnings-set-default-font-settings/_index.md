---
category: general
date: 2026-03-19
description: 了解如何在 Aspose.Words 中捕获警告、设置默认字体设置，以及在加载 Word 文档时检测缺失的字体。
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: zh
og_description: 如何在 Aspose.Words 中捕获警告、设置默认字体，并在加载 Word 文档时检测缺失的字体。
og_title: 如何捕获警告 – 设置默认字体设置
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何捕获警告 – 设置默认字体设置
url: /zh/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕获警告 – 设置默认字体

**如何捕获警告** 是在使用 Aspose.Words 时的常见需求，尤其是当你的文档依赖于目标机器上可能不存在的特定字体时。是否曾打开过 DOCX，却发现布局怪怪的？答案往往隐藏在缺失字体的警告中。  

在本指南中，我们将演示在 **加载 word 文档** 时 **如何捕获警告**，配置 **设置默认字体**，并最终 **检测缺失字体**，以便你能够以编程方式作出响应。没有冗余——只提供完整可运行的示例以及每行代码背后的原理。

> *小贴士：* 及早捕获警告可以帮助你避免后期调试神秘的布局问题。

---

## 你需要准备的东西

- **Aspose.Words for .NET**（截至 2026 年的最新版本）。  
- .NET 开发环境（Visual Studio、Rider 或 VS Code）。  
- 一个引用了你 **未** 安装的字体的示例 DOCX（例如在 Linux 上没有安装的 *Comic Sans MS*）。  

就这些。除了 Aspose.Words 外，无需额外的 NuGet 包。

---

## 第一步 – 理解为何需要捕获警告

当 Aspose.Words 解析文档时，可能会遇到主机上不存在的字体。默认情况下，库会悄悄地使用回退字体进行替换，这会导致换行、间距甚至文字消失。  

将 **WarningCallback** 与 **FontSettings** 对象结合使用，可以为你提供两件事：

1. **可见性** – 你会收到每一次替换的 `WarningInfo` 条目。  
2. **可控性** – 你可以预先配置默认字体，以最大程度减少视觉上的意外。

可以把它想象成安装了一个“看门狗”，每当引擎在内部更换部件时就会大声提醒。

---

## 第二步 – 设置默认字体

第一个二级关键词 **set default font settings** 正在这里出现。你需要创建一个 `FontSettings` 实例，并可选地指向包含回退字体的文件夹。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **为什么要这样做？**  
> 如果不指定回退字体，Aspose.Words 会选取系统中第一个匹配样式的字体，而这个字体可能差别巨大。通过设置已知的默认字体，你可以保证在不同机器上的渲染保持一致。

---

## 第三步 – 准备 Warning Callback 以捕获警告

接下来我们通过将 `WarningInfoCollection` 附加到加载选项来 **如何捕获警告**。该集合会存储加载过程中产生的所有警告。

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` 实现了 `IWarningCallback`，因此 Aspose.Words 会自动把每条警告推入 `warningInfos`，无需轮询。

---

## 第四步 – 使用已配置的选项加载 Word 文档

这里正是第二个二级关键词 **load word document** 发光的地方。我们通过 `LoadOptions` 实例同时传入 `FontSettings` 和 `WarningCallback`。

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

如果文档引用了未安装的字体，警告回调将捕获到 `WarningType.FontSubstitution` 条目。

---

## 第五步 – 从收集的警告中检测缺失字体

最后，我们通过遍历收集到的警告来回答第三个二级关键词 **detect missing fonts**。

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

典型的输出如下：

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

该行精确指出了缺失的字体以及使用的回退字体——这些信息可以记录日志、展示给用户，甚至触发自定义的字体安装流程。

---

## 完整可运行示例

下面是可以直接复制到控制台应用程序中的完整代码。它演示了 **如何捕获警告**、**设置默认字体**、**加载 word 文档**，以及 **检测缺失字体** 的完整流程。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**预期结果：** 当指定的 DOCX 引用了未安装的字体时，控制台会为每一次替换打印一条警告。如果所有字体都已安装，循环将不产生任何输出。

---

## 常见陷阱与边缘情况

| 情况 | 为什么会出现 | 处理方法 |
|-----------|----------------|------------------|
| **即使布局异常仍没有警告出现** | 文档可能使用了 *嵌入* 字体，Aspose.Words 会直接渲染而不进行替换。 | 检查 `Document.HasEmbeddedFonts`，如有需要可提取嵌入的字体以在其他机器上使用。 |
| **Multiple warnings for the |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}