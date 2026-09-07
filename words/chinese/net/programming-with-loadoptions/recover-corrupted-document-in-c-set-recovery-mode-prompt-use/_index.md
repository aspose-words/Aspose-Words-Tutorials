---
category: general
date: 2026-01-11
description: 使用 Aspose.Words 在 C# 中恢复损坏的文档。了解如何设置恢复模式、使用恢复加载 docx，以及在出现错误时提示用户，只需几个简单步骤。
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: zh
og_description: 在 C# 中通过设置恢复模式、加载带恢复的 DOCX 并在出错时提示用户来恢复损坏的文档。完整的逐步教程。
og_title: 在 C# 中恢复损坏的文档 – 快速指南
tags:
- Aspose.Words
- C#
- Document Recovery
title: 在 C# 中恢复损坏的文档 – 设置恢复模式并提示用户
url: /zh/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中恢复损坏的文档 – 完整指南

是否曾尝试打开一个在 Word 中看起来正常但在代码中抛出异常的 DOCX？你可能正面对 **recover corrupted document** 场景。好消息是 Aspose.Words 为你提供了细粒度的控制，帮助你决定是静默修复、抛出异常，还是询问用户该怎么做。

在本教程中，我们将逐步演示如何 **recover corrupted document** 文件，从安装库到选择合适的 **set recovery mode** 选项、**load docx with recovery**，以及在出现问题时 **prompt user on error**。没有废话，只有完整、可直接运行的示例，随时可以放入任何 .NET 项目。

> **快速预览：** 完成后，你将拥有一个控制台应用，能够加载可能损坏的 `corrupt.docx`，记录所有警告，并在恢复失败时询问用户是否继续。

---

## 你需要准备的环境

- **.NET 6.0** 或更高版本（代码同样适用于 .NET Framework 4.6+）。  
- **Aspose.Words for .NET** – 通过 NuGet 安装 (`Install-Package Aspose.Words`)。  
- 一个用于测试的 **corrupt DOCX** 文件（可以通过十六进制编辑器损坏文件或更改扩展名来制造）。  
- 任意你喜欢的 IDE——Visual Studio、Rider，甚至 VS Code 都可以。

> *专业提示：* 保留原始文件的备份。恢复过程可能会重写文档的部分内容，避免丢失有效数据。

---

## 第一步 – 安装 Aspose.Words 并添加命名空间

首先，从 NuGet 获取库并引入所需的命名空间。

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

这就是本指南后续所有代码所需的全部内容。`Aspose.Words.Loading` 命名空间包含 `LoadOptions` 类，它是 **set recovery mode** 的关键。

---

## 第二步 – 选择恢复模式（含关键字的主标题）

### Recover Corrupted Document – 设置正确的恢复模式

Aspose.Words 提供三种恢复行为：

| 模式 | 会发生什么 | 何时使用 |
|------|------------|----------|
| **PromptUser** | 显示对话框（或自行实现提示），并尝试修复文件。 | 适用于交互式工具，用户可以自行决定。 |
| **Silent** | 自动尝试修复，不显示 UI。 | 适用于批处理作业或服务。 |
| **ThrowException** | 停止处理并抛出异常。 | 需要严格校验时使用。 |

下面演示如何 **set recovery mode** 为 `PromptUser`。如果你更倾向于静默处理，只需将枚举值替换为相应的模式。

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **为什么重要：** 通过显式 **set recovery mode**，你告诉 Aspose.Words 该采用何种修复力度。默认也是 `PromptUser`，但明确写出可以让后续维护者以及搜索引擎更清晰地了解你的意图。

---

## 第三步 – 使用恢复模式加载 DOCX

现在我们使用刚才配置好的 `LoadOptions` **load docx with recovery**。如果文件受损，Aspose.Words 将根据模式修复或给出警告。

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

`Document` 构造函数负责大部分工作。在 **PromptUser** 模式下，你会看到控制台提示（或通过 `LoadOptions` 事件挂钩的自定义 UI），询问是否继续。 在 **Silent** 模式下，方法会尽力修复并继续执行。

---

## 第四步 – 检查警告并提示用户

Aspose.Words 会把遇到的所有问题记录在 `Warnings` 集合中。我们遍历这些警告，并给用户一个决定后续操作的机会。

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

上面的代码片段在控制台环境下实现了 **prompt user on error**。如果你在构建 Windows Forms 或 WPF 应用，只需将 `Console.ReadLine` 替换为 `MessageBox` 或自定义对话框。

---

## 第五步 – 使用恢复后的文档

此时文档已在内存中，已尽可能被 Aspose.Words 修复。你可以读取内容、保存为干净的副本，或进行任何需要的操作。

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

对损坏文件运行完整程序后，控制台输出类似如下：

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

如果文件本身没有问题，你会看到 “Document loaded without any warnings.”，且保存的干净副本将与源文件完全相同。

---

## 完整可运行示例

下面是一整段程序代码。复制粘贴到新的控制台项目中，按 **F5** 运行。

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

运行它，破坏一个测试文件，观察恢复过程的实际表现。 🎉

---

## 边缘情况与变体

| 场景 | 需要更改的内容 | 原因 |
|------|----------------|------|
| **批量处理**（无用户交互） | 将 `RecoveryMode = RecoveryMode.Silent` 并移除控制台提示。 | 自动化流水线，保持连续运行。 |
| **严格校验**（快速失败） | 使用 `RecoveryMode.ThrowException`。将加载调用包装在 try/catch 中并记录异常。 | 确保永不使用部分修复的文件。 |
| **自定义 UI**（WinForms/WPF） | 订阅 `LoadOptions.LoadingProgress` 或使用 `Document.LoadOptions` 事件显示对话框。 | 为用户提供比控制台更丰富的交互体验。 |
| **大型文档**（内存受限） | 使用 `LoadOptions.LoadFormat = LoadFormat.Docx` 并考虑 `Document.SaveOptions` 进行流式输出。 | 防止 OutOfMemory 异常。 |

---

## 实用技巧（E‑E‑A‑T 信号）

- **始终在恢复前备份**，因为过程可能会覆盖文件的部分内容。  
- **将警告记录到文件**，以便后续分析；警告常常指向根本原因（如缺失部件、XML 损坏）。  
- **使用多种损坏类型进行测试**——截断文件、破坏 XML 标签或修改 zip 结构，观察每种模式的表现。  
- **定期升级 Aspose.Words**；新版本会改进恢复算法并增加新的警告类型。  
- **结合验证**——恢复后执行 `document.UpdateFields()` 与 `document.Save()`，确保文档功能完整。

---

## 结论

现在，你已经掌握了在 C# 中通过 **set recovery mode**、**load docx with recovery**，以及在出现错误时 **prompt user on error** 来 **recover corrupted document** 的完整流程。完整示例展示了一个干净的端到端流程，适用于控制台应用、服务或 UI 项目。

接下来可以尝试在 WinForms 应用中将控制台提示替换为模态对话框，或在后台作业中使用 **Silent** 模式，甚至将恢复逻辑集成到 ASP.NET 文件上传接口，让用户上传损坏的 DOCX 并即时获得修复后的版本。

祝编码愉快，愿你的文档永远完整！  

---

![恢复损坏文档示例](/images/recover-corrupted-document.png "恢复损坏文档")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}