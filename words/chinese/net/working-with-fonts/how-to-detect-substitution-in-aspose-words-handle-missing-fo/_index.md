---
category: general
date: 2026-04-24
description: 如何使用 C# 检测 Aspose.Words 中缺失字体的替换。本指南展示了如何通过 FontSettings 警告可靠地处理缺失字体。
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: zh
og_description: 如何在 Aspose.Words 中使用 C# 检测缺失字体的替换。学习使用 FontSettings 警告来处理缺失字体。
og_title: 如何在 Aspose.Words 中检测替换 – 完整指南
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: 如何检测 Aspose.Words 中的字体替换 – 处理缺失字体
url: /zh/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何检测 Aspose.Words 中的字体替换 – 处理缺失字体

是否曾经想过 **如何检测替换**，当文档尝试使用服务器上未安装的字体时？这在自动化流水线中生成 PDF 或 Word 文件时是一个常见的痛点。好消息是 Aspose.Words 提供了内置的钩子来准确捕获这种情况，并且您还可以 **优雅地处理缺失字体**。

在本教程中，我们将通过一个真实案例演示如何通过 `FontSettings.Warning` 事件 **检测替换**，并解释如何 **处理缺失字体** 而不会中断处理流程。完成后，您将拥有可直接运行的代码片段、对每行代码意义的清晰理解，以及避免常见陷阱的若干技巧。

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework）
- Aspose.Words for .NET（NuGet 包 `Aspose.Words`）– 版本 23.11 或更新
- 一个引用了您未安装字体的示例文档（例如 `MissingFont.docx`）
- Visual Studio、VS Code 或任何您喜欢的 C# IDE  

无需除添加 NuGet 包之外的额外配置。

---

## 使用 FontSettings 检测替换

**如何检测替换** 的核心在于 `FontSettings.Warning` 事件。当 Aspose.Words 找不到请求的字体时，它会触发 `WarningType.FontSubstitution` 警告。通过订阅此事件，您可以实时收到通知，包含原始字体名称以及被用作回退的字体。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**为什么这样有效：**  
- `LoadOptions.FontSettings` 告诉 Aspose.Words 使用您刚创建的 `FontSettings` 对象。  
- 订阅 `Warning` 让您在一个位置监控 *所有* 与字体相关的问题，而不仅仅是缺失的字体。  
- `WarningType.FontSubstitution` 过滤器确保您只对感兴趣的特定场景作出响应——这正是 **如何检测替换** 的本质。

### 预期输出

使用引用不存在字体的文档运行上述代码，将会打印类似以下内容：

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

如果文档仅使用已安装的字体，控制台将保持安静——这清晰表明 **如何检测替换** 已成功且没有误报。

---

## 优雅地处理缺失字体

检测到替换只是解决问题的一半；您还需要一种 **处理缺失字体** 的策略，以确保最终输出符合预期。下面提供三种实用方法，您可以自由组合使用。

### 1. 提供回退字体文件夹

Aspose.Words 可以搜索额外的目录来寻找字体。将其指向包含您常用字体的文件夹，可彻底降低出现替换的概率。

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**为什么：** 当原始字体缺失时，Aspose.Words 现在拥有一组已知的备选字体，通常能得到更可预测的视觉效果。

### 2. 以编程方式替换缺失字体

如果需要完全控制，您可以在检测到缺失后将其替换为指定的字体。

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**为什么：** 这明确告诉引擎使用哪些字体，让您能够强制执行企业品牌或可访问性标准。

### 3. 记录并中止（当替换不可接受时）

有时缺失字体意味着文档对您的业务场景无效（例如法律表单）。在这种情况下，您可以在检测到替换后立即抛出异常。

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**为什么：** 立即失败可防止下游错误，例如表格错位或签名破损。

---

## 完整工作示例 – 所有步骤组合

下面是一段可直接复制粘贴的完整程序，演示 **如何检测替换** *以及* 多种 **处理缺失字体** 的方式。根据需要自行注释掉不需要的部分。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**预期行为：**  
- 如果 `MissingFont.docx` 引用了机器上不存在的字体，控制台会打印替换警告。  
- 保存的 `Processed.docx` 将使用您配置的回退字体（或库的默认字体）。  
- 除非您主动在替换时中止，否则不会出现未处理的异常。

---

## 常见问题与边缘情况

| 问题 | 回答 |
|----------|--------|
| *如果文档包含大量缺失字体怎么办？* | 警告事件会为 **每一次** 替换触发一次，因此您会看到多行输出。可以将它们聚合到列表中，以生成汇总报告。 |
| *这在 PDF 转换时也有效吗？* | 完全有效。调用 `doc.Save("out.pdf")` 时，同样会遵循 `FontSettings`，并触发替换警告，帮助您验证 PDF 的视觉一致性。 |
| *文档已经加载后还能检测替换吗？* | 不能直接。警告仅在加载或保存期间触发。如果需要加载后分析，请在加载阶段捕获警告并存入集合。 |
| *如果 DOCX 中嵌入了自定义字体怎么办？* | 嵌入的字体被视为已存在，不会产生替换。如果嵌入的字体损坏，Aspose.Words 仍会抛出警告，捕获方式相同。 |
| *会不会影响性能？* | 影响极小。警告检查本身开销轻微，主要耗时在文档加载上。添加字体文件夹可能会略微增加首次加载时的搜索时间。 |

---

## 专业技巧与需避免的陷阱

- **专业技巧：** 指向包含大量字体的文件夹时，务必将 `recursive: true` 设为 true，否则子文件夹会被忽略。  
- **注意事项：** Linux 上的大小写敏感。Windows 对字体名称不区分大小写，但 Linux 则区分，请使用准确的名称或同时提供两种变体。  
- **记住：** 若在容器化环境中运行，确保字体文件夹已包含在镜像中或在运行时挂载。  
- **小贴士：** 如需向最终用户展示汇总或将其记录到监控系统，可将警告存入 `List<string>` 中。  

---

## 结论

我们已经介绍了在 Aspose.Words 中 **检测缺失字体的替换** 的方法，展示了多种 **处理缺失字体** 的方案，并提供了一个完整、可直接运行的示例，您可以将其放入任何 .NET 项目中。通过使用 `FontSettings.Warning` 事件，您能够实时获知字体问题；结合回退文件夹或显式的替换规则，确保输出始终符合预期。

准备好下一步了吗？尝试将解决方案扩展为自动将回退字体嵌入生成的 PDF，或将警告处理程序接入集中式日志服务，以支撑大规模文档流水线。今天讨论的模式——事件驱动检测、优雅回退以及显式错误处理——同样适用于许多其他 Aspose API，帮助您全面应对字体相关的挑战。

还有关于字体处理、PDF 转换或 Aspose.Words 使用技巧的更多问题吗？在下方留言吧，祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}