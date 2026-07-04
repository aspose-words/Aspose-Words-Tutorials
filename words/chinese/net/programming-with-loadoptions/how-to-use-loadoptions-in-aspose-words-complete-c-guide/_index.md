---
category: general
date: 2026-04-10
description: 如何在 Aspose.Words 中使用 LoadOptions 捕获加载文档时的字体替换警告。学习一步一步的 C# 解决方案以及完整代码示例。
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: zh
og_description: 如何在 Aspose.Words 中使用 LoadOptions 在加载文档时捕获字体替换警告。本指南将带您完整实现 C# 示例。
og_title: 如何在 Aspose.Words 中使用 LoadOptions – 完整 C# 指南
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: 如何在 Aspose.Words 中使用 LoadOptions – 完整 C# 指南
url: /zh/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中使用 LoadOptions – 完整 C# 指南

在需要对文档加载进行精细控制时，如何使用 LoadOptions 是一个常见的难点。在本教程中，我们将向您展示**如何使用 LoadOptions**来捕获字体替换警告并在 C# 中作出响应。

如果您曾打开过引用了缺失字体的 DOCX 并疑惑为何输出看起来怪怪的，那么您来对地方了。我们将完整演示从创建 `LoadOptions` 实例到在控制台打印警告详情的整个过程。结束后，您将拥有一段可直接放入任何 .NET 项目的可运行代码片段。

## 您将学到

- 为什么 `LoadOptions` 对可靠的文档导入至关重要。  
- 如何插入一个专门监视**字体替换警告**的 **WarningCallback**。  
- 加载 Word 文件并启用这些选项所需的完整代码。  
- 处理边缘情况的技巧，例如文档中包含多个缺失字体的情况。  

无需查阅外部文档——所有内容都在这里。

## 前置条件

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 或更高版本 | 为示例中使用的 C# 10 语法提供运行时支持。 |
| Aspose.Words for .NET（最新版本） | 提供 `LoadOptions` 和警告基础设施的库。 |
| 可能引用了未安装字体的 DOCX 文件 | 用于观察警告回调的实际效果。 |
| Visual Studio 2022（或您喜欢的任何 IDE） | 便于调试和测试。 |

如果您已经具备上述条件，太好了——让我们开始吧。

## 第一步 – 创建 LoadOptions 对象并绑定 WarningCallback

在**如何使用 LoadOptions**时，第一件事就是实例化它。关键在于为 `WarningCallback` 分配一个委托。每当 Aspose.Words 遇到想要告知您的情况时（尤其是缺失字体），该委托就会被触发。

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**为何这很重要：**如果没有回调，Aspose.Words 会悄悄将缺失字体替换为默认字体，您可能永远不会注意到视觉上的变化。通过注册 `WarningCallback`，您可以实时记录每一次替换，这对质量保证的文档流水线至关重要。

## 第二步 – 只对字体替换警告作出响应

您可能会担心回调会被无关的警告（如已弃用的特性）淹没。答案是*会*——但我们可以对其进行过滤。在上面的代码片段中，我们已经检查 `args.WarningType == WarningType.FontSubstitution`。这行代码就是**字体替换警告**的守卫，帮助输出保持聚焦。

如果您需要处理其他警告类型，只需扩展 `if` 块：

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

该模式展示了 **warningcallback** 机制的灵活性，让您能够针对真正关心的场景定制响应。

## 第三步 – 使用配置好的 LoadOptions 加载文档

监听器准备就绪后，最后一步是将 `LoadOptions` 实例传递给 `Document` 构造函数。这正是 **Aspose.Words LoadOptions 示例** 发光发热的时刻。

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**您将看到的结果：**如果 DOCX 引用了机器上未安装的字体，控制台会输出类似以下内容的一行：

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

该输出确认您已经成功**如何使用 LoadOptions**来监控字体问题。

## 完整可运行示例（复制‑粘贴即用）

下面是可以立即编译运行的完整程序。它将前三个步骤整合在一起，加入了一些小细节（如友好的横幅），并演示了错误处理。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### 预期输出

在缺少 `input.docx` 中引用的字体的机器上运行程序，输出大致如下：

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

如果所有字体都已安装，您只会看到成功信息——不会出现警告行。

## 常见陷阱与专业提示

- **陷阱：**忘记设置 `WarningCallback`。代码仍然可以加载，但您会错过替换细节。  
  **专业提示：**创建 `LoadOptions` 后立即分配回调；成本低，后期收益大。

- **陷阱：**使用了指向错误文件夹的相对路径。  
  **专业提示：**使用 `Path.Combine(Environment.CurrentDirectory, "input.docx")` 进行更稳健的文件查找。

- **陷阱：**误以为警告会阻止加载。  
  **专业提示：**字体替换警告是*信息性*的；它们不会中止加载。如果需要更严格的验证，可在回调中抛出异常。

- **陷阱：**在没有任何字体的服务器上运行（例如极简的 Docker 镜像）。  
  **专业提示：**预先安装所需字体或将其随应用程序打包，然后通过回调验证生产环境中没有发生替换。

## 何时使用 LoadOptions 与加载后检查

您可能会问：“为什么不在文档加载后再检查？”答案在于性能和正确性。通过在**加载期间**处理警告，您可以在任何布局计算或 PDF 转换之前及早捕获问题。这在批处理流水线中尤为重要，因为每一步都会增加耗时。

## 扩展示例：保存所有被替换字体的报告

如果需要永久记录（例如合规需求），可以修改回调，将消息收集到列表中，并在加载完成后写入文件：

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

这样您既拥有控制台反馈，又拥有持久化日志。

## 您可能感兴趣的相关主题

- **如何在 Aspose.Words 中嵌入自定义字体** – 完全消除替换。  
- **使用 LoadOptions 限制文档大小** – 防止恶意的大文件。  
- **将 Word 转换为 PDF 并保留排版** – 与警告回调方法相得益彰。  

上述每个主题都建立在您刚刚使用 `LoadOptions` 打下的基础之上。

## 结论

我们已经从头到尾完整演示了**如何在 Aspose.Words 中使用 LoadOptions**：创建选项、绑定专注于**字体替换警告**的 `WarningCallback`，并自信地加载文档。完整示例可直接运行，附加的技巧帮助您规避常见陷阱。

欢迎自行实验——将回调换成其他警告类型、记录到数据库，或将逻辑集成到验证上传 Word 文件的 Web 服务中。该模式灵活可靠，最重要的是，它让您看见原本隐藏的字体替换过程，避免文档渲染出现意外。

祝编码愉快，愿您的文档始终如您所愿完美呈现！

![Diagram showing the flow of using LoadOptions with a warning callback in Aspose.Words](https://example.com/images/loadoptions-flow.png "How to use LoadOptions diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}