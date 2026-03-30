---
category: general
date: 2026-03-30
description: 如何在加载 DOCX 文件时捕获警告——学习检测缺失字体、配置字体设置以及在 C# 中设置加载选项。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: zh
og_description: 如何在加载 DOCX 文件时捕获警告——一步步指南，检测缺失字体并在 C# 中配置字体设置。
og_title: 如何捕获警告——为缺失字体配置加载选项
tags:
- Aspose.Words
- C#
- Font management
title: 如何捕获警告 – 为缺失字体配置加载选项
url: /zh/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕获警告 – 为缺失字体配置加载选项

是否曾经想过 **如何捕获警告**，当文档尝试使用您未安装的字体时会弹出？这种情况会让许多使用文字处理库的开发者感到困惑，尤其是当您需要在它们破坏 PDF 导出流水线之前 **检测缺失的字体** 时。

在本教程中，我们将向您展示一个实用、可直接运行的解决方案，**配置字体设置**、**设置加载选项**，并将每个替换警告打印到控制台。完成后，您将准确了解如何 **处理缺失字体**，从而保持应用程序的健壮性并让用户满意。

## 您将学习

- 如何 **设置加载选项**，使库报告字体问题而不是静默替换。
- 捕获警告所需的 **配置字体设置** 的完整步骤。
- 以编程方式 **检测缺失字体** 并相应地做出响应的方法。
- 一个完整的、可复制粘贴的 C# 示例，适用于最新的 Aspose.Words for .NET（撰写时为 v24.10）。
- 扩展方案的技巧：记录警告、回退到自定义字体，或在关键字体缺失时中止处理。

> **先决条件：** 您需要安装 Aspose.Words for .NET NuGet 包 (`Install-Package Aspose.Words`)。不需要其他外部依赖。

---

## Step 1: Import Namespaces and Prepare the Project

首先，添加必要的 `using` 指令。这不仅是样板代码；它告诉编译器 `LoadOptions`、`FontSettings` 和 `Document` 所在的位置。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **专业提示：** 如果您使用的是 .NET 6+，可以启用 *global using* 声明，以免在每个文件中重复这些行。

---

## Step 2: Set Load Options and Enable Font‑Substitution Warnings

捕获 **如何捕获警告** 的核心在于 `LoadOptions` 对象。通过创建一个全新的 `FontSettings` 实例并将事件处理程序附加到 `SubstitutionWarning`，您可以让库在找不到请求的字体时发出警报。

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**为何重要：** 如果不订阅此事件，Aspose.Words 会静默回退到默认字体，您永远不知道哪些字形被替换。监听 `SubstitutionWarning` 能让您获得完整的审计轨迹——这在合规性要求严格的环境中至关重要。

---

## Step 3: Load the Document Using the Configured Options

现在警告已经接通，使用刚才准备好的 `loadOptions` 加载您的 DOCX（或任何受支持的格式）。`Document` 构造函数会立即触发字体检查逻辑。

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

如果文件引用了比如 *“Comic Sans MS”*，而机器上只有 *“Arial”*，您会看到类似如下的输出：

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

该行直接打印到控制台，因为我们之前附加的处理程序负责输出。

---

## Step 4: Verify and React to Captured Warnings

捕获警告只是第一步；您通常需要决定接下来该怎么做。下面的示例展示了一个快速模式，将警告存入列表以便后续分析——如果您想将其记录到文件或在关键字体缺失时中止导入，这种方式非常合适。

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**边缘情况处理：**  
- **多个缺失字体：** 列表会为每一次替换生成一条记录，您可以遍历并生成详细报告。  
- **自定义回退字体：** 如果您有自己的字体文件，可在加载前将其加入 `FontSettings`：`fontSettings.SetFontsFolder(@"C:\MyFonts", true);`。此后警告将显示自定义回退字体，而不是系统默认字体。  

---

## Step 5: Full Working Example (Copy‑Paste Ready)

将所有内容整合在一起，下面是一个可直接编译运行的完整控制台应用示例。

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**预期的控制台输出**（当 DOCX 引用了缺失的字体时）：

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

如果缺少像 “Times New Roman” 这样的 *关键* 字体，您将看到中止信息。

---

## Common Questions & Gotchas

| Question | Answer |
|----------|--------|
| **是否需要调用 `SetFontsFolder` 才能捕获警告？** | 不需要。警告事件在默认系统字体下即可工作。仅在需要提供额外回退字体时才使用 `SetFontsFolder`。 |
| **这在 .NET Core / .NET 5+ 上能工作吗？** | 完全可以。Aspose.Words 24.10 支持所有现代 .NET 运行时。只需确保 NuGet 包与目标框架匹配。 |
| **如果想把警告记录到文件而不是控制台，怎么办？** | 将 `Console.WriteLine(msg);` 替换为任意日志框架的调用，例如 `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`。 |
| **能否对特定字体抑制警告？** | 可以。在事件处理程序中进行过滤：`if (e.FontName == "SomeFont") return;`，即可实现细粒度控制。 |
| **有没有办法把缺失字体当作错误处理？** | 可以在处理程序内部根据条件手动抛出异常，或设置标志并在 `Document` 构造后中止，如示例所示。 |

---

## Conclusion

您现在拥有一套稳固、可投入生产的 **如何捕获警告** 模式，用于在加载包含缺失字体的文档时进行检测。通过 **检测缺失字体**、**配置字体设置** 和 **设置加载选项**，您可以完整地看到字体替换事件，并决定是记录、回退还是中止。

接下来，可将此逻辑集成到 PDF 转换流水线中，添加自定义回退字体，或将警告列表输送到监控系统。该方法既适用于小工具，也能扩展到企业级文档处理服务。

### Further Reading & Next Steps

- **深入探索 FontSettings 功能** – 嵌入自定义字体、控制回退顺序以及授权注意事项。  
- **与 PDF 转换结合** – 捕获警告后，调用 `doc.Save("output.pdf");` 并验证 PDF 使用了预期的字体。  
- **自动化测试** – 编写单元测试，加载已知缺失字体的文档，并断言警告列表包含预期信息。  

如果您在使用过程中遇到任何问题或有改进想法，欢迎留言交流。祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}