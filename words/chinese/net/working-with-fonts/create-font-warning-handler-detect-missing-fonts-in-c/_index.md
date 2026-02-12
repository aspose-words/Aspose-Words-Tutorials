---
category: general
date: 2026-02-12
description: 创建字体警告处理程序，以检测缺失的字体并在 Aspose.Words 中跟踪缺失的字体。了解如何高效记录警告。
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: zh
og_description: 在 C# 中创建字体警告处理程序，以检测缺失的字体，并了解在 Aspose.Words 替换字体时如何记录警告。
og_title: 创建字体警告处理程序 – 检测缺失字体
tags:
- Aspose.Words
- C#
- Document Processing
title: 创建字体警告处理程序 – 在 C# 中检测缺失的字体
url: /zh/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建字体警告处理程序 – 检测 C# 中缺失的字体

是否曾经因为 Word 文档悄悄将你未预料的字体替换而需要 **创建字体警告处理程序**？你并不孤单。当 Aspose.Words 加载引用了服务器上不存在的字体的 DOCX 时，它会默默回退到默认字体——导致布局细微破坏。  

在本教程中，我们将向你展示如何 **检测缺失的字体**、**跟踪缺失的字体**，以及 **如何记录警告**，让你在问题出现前就能发现这些替换。完成后，你将拥有一个可复用的警告处理程序，能够将每一次字体替换事件打印到控制台（或任意你喜欢的日志记录器）。没有神秘，只是清晰、可操作的代码。

## 前提条件

- .NET 6.0 或更高（API 在 .NET Framework 4.6+ 中相同）
- 已安装 Aspose.Words for .NET（`dotnet add package Aspose.Words`）
- 一个引用了本机未安装字体的 Word 文件（例如 `MissingFont.docx`）

如果你已经具备上述条件，太好了——我们直接开始。

## 第一步：使用警告回调设置 LoadOptions  

当你想 **创建字体警告处理程序** 时，第一件事就是告诉 Aspose.Words 在遇到问题时触发回调。`LoadOptions` 是该配置的容器。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**为什么这很重要：**  
`LoadOptions` 是唯一可以插入 `IWarningCallback` 的位置。若不这样做，Aspose.Words 只会在内部记录警告，而你永远看不到。通过分配 `FontWarningHandler`，我们即可完全控制缺失字体被替换时的行为。

## 第二步：实现 FontWarningHandler 类  

现在我们真正 **创建字体警告处理程序** 的代码。该类实现 `IWarningCallback`，并为 Aspose.Words 抛出的每个警告接收一个 `WarningInfo` 对象。

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**说明：**  
- `info.Type` 告诉我们警告的类别。我们关注 `WarningType.FontSubstitution`，因为它表示缺失字体。  
- `info.Description` 包含类似 *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* 的可读信息。  
- 通过 `Console.WriteLine` 我们 **即时记录警告**。在实际项目中，你可能会改用 `ILogger`、文件写入器或遥测服务。

> **小技巧：** 如果需要收集所有缺失字体以便后续报告，可将 `info.Description` 存入 `List<string>`，而不是直接打印。

## 第三步：使用配置好的 LoadOptions 加载文档  

有了回调后，加载文档时会自动在缺失字体时触发我们的处理程序。

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**你将看到的输出：**  
运行程序后会打印类似以下内容：

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

该行确认你已经成功 **检测缺失的字体**，并且正在实时 **跟踪缺失的字体**。

## 第四步：使用不同场景验证处理程序  

很多人会误以为处理程序只对 DOCX 有效，实际上 Aspose.Words 支持多种格式。尝试加载引用了嵌入字体的 PDF，或较旧的 `.doc` 文件。只要进入字体解析管线，回调都会被触发。

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

如果 PDF 引用了未安装的字体，你将得到相同的控制台输出。这表明你的 **创建字体警告处理程序** 方案与格式无关。

## 第五步：扩展处理程序 – 记录到文件  

控制台输出适合演示，但生产代码通常写入日志文件。下面是一个快速改动。

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

现在每当发生字体替换时，信息会追加到 `font-warnings.log`。这满足了 **如何记录警告** 的需求，并提供了持久的审计轨迹。

## 第六步：完整示例 – 可直接运行的代码  

下面是完整程序，可直接复制到控制台应用中。只需将文件路径替换为你自己的文档即可。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**预期结果：**  

- 控制台会打印每一条替换信息。  
- `font-warnings.log` 中会包含带时间戳的每一次缺失字体事件记录。  
- 使用替换后的字体生成的 `output.pdf` 文件会成功创建，即使原始字体不可用。

## 常见问题与边缘情况  

| 问题 | 答案 |
|----------|--------|
| *如果我想忽略某些字体怎么办？* | 在 `Warning` 方法中检查 `info.Description` 中的字体名称，针对可接受的字体直接 `return;`。 |
| *处理程序会对嵌入字体触发吗？* | 不会——嵌入字体始终随文档可用，因此不会产生替换警告。 |
| *我能捕获其他警告类型吗（例如图像分辨率问题）？* | 当然。移除 `if (info.Type == WarningType.FontSubstitution)` 条件，或为 `WarningType.ImageResolution` 添加额外的 `if` 块。 |
| *处理程序线程安全吗？* | 示例实现直接写文件而未做同步。若在多线程环境使用，请在写文件时加锁或使用并发日志记录器。 |

## 后续步骤  

既然你已经掌握了 **如何记录缺失字体的警告**，可以进一步：

- **在批量导入过程中检测缺失字体** 并生成汇总报告。  
- **跨多个文档跟踪缺失字体**，当某个字体频繁出现时发送邮件提醒。  
- **与监控系统集成**（如 Azure Application Insights），实时展示字体替换趋势。  

所有这些扩展都基于我们创建的 `IWarningCallback` 基础。

---

*祝编码愉快！如果遇到奇怪的情况——比如自定义字体文件夹或网络共享——欢迎在下方留言。社区（以及我）随时乐意帮助你微调字体警告策略。* 

![创建字体警告处理程序示例](image-placeholder.png "创建字体警告处理程序示例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}