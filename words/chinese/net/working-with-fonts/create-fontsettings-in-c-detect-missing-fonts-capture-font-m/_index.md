---
category: general
date: 2026-03-01
description: 在 C# 中创建 FontSettings，以检测缺失的字体、捕获字体消息，并使用 Aspose.Words 处理缺失的字体。面向开发者的逐步指南。
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: zh
og_description: 在 C# 中创建 FontSettings，以检测缺失的字体、捕获字体消息，并使用 Aspose.Words 处理缺失的字体。完整教程附代码。
og_title: 在 C# 中创建 FontSettings – 检测缺失字体并捕获字体信息
tags:
- Aspose.Words
- C#
- Font Management
title: 在 C# 中创建 FontSettings – 检测缺失字体并捕获字体信息
url: /zh/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中创建 FontSettings – 检测缺失字体并捕获字体消息

是否曾经在 .NET 项目中**创建 FontSettings**，却不确定如何发现目标机器上未安装的字体？你并不孤单。在许多真实场景的应用中——比如自动化报表生成器或文档转换器——缺失的字体会悄悄破坏布局，而你直到 PDF 看起来怪怪的才发现问题。

如果可以**检测缺失字体**、**捕获字体消息**，并在它们破坏输出之前**处理缺失字体**，该多好？好消息是 Aspose.Words 能让这变得轻而易举。在本教程中，我们将完整演示从设置 `FontSettings` 对象到接入警告回调，精准告知哪些字形被替换的全过程。

> **TL;DR：** 完成后，你将拥有一个可直接运行的 C# 控制台应用，记录每一次字体替换，让你决定是嵌入替代字体还是提示用户。

---

## 前置条件

- .NET 6 SDK（或任意近期的 .NET 版本）  
- Visual Studio 2022 或带 C# 扩展的 VS Code  
- Aspose.Words for .NET 许可证（免费试用即可演示）  
- 一个引用了你系统中未安装字体的示例 DOCX（例如在 Linux 上没有的 *Comic Sans MS*）  

除 `Aspose.Words` 之外，无需其他特殊 NuGet 包。

---

## 第一步 – 安装 Aspose.Words 并创建项目

首先，创建一个新的控制台项目并引入 Aspose.Words 库。

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **小技巧：** 如果已有解决方案，只需通过 NuGet 包管理器 UI 添加包——这样更便于版本管理。

---

## 第二步 – 创建 FontSettings（此处出现主要关键词）

**创建 FontSettings** 是任何与字体相关工作流的基石。`FontSettings` 告诉 Aspose.Words 去哪里寻找字体、是否使用系统文件夹，以及在缺失时如何回退。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

为什么这很重要？如果 `FontSettings` 配置不当，渲染引擎会悄悄用系统默认字体替代缺失字形，而你永远收不到警告。

---

## 第三步 – 使用 FontSettings 配置 LoadOptions

`LoadOptions` 让你在文档加载时传入 `FontSettings`。这是一座桥梁，使引擎在 `Document` 构造阶段**检测缺失字体**。

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

现在，每次使用 `loadOptions` 加载 DOCX 时，Aspose.Words 都会参考我们之前设置的 `FontSettings`。

---

## 第四步 – 绑定警告回调以**捕获字体消息**

Aspose.Words 会在多种情况下发出警告——字体替换是最常见的之一。实现 `IWarningCallback` 并提供回调后，你可以**实时捕获字体消息**。

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### 警告处理类

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

`info.Description` 字段包含可读的提示信息，例如 *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* 这正是你在**处理缺失字体**时需要的输出。

---

## 第五步 – 加载文档并让回调发挥作用

所有配置就绪后，加载文档变得非常简单。如果源文件引用了系统中不存在的字体，我们的警告处理器会被触发。

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

运行程序时，你会在控制台看到类似以下的输出：

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

这就是工作流中**捕获字体消息**的部分。你可以进一步扩展处理器，将信息写入文件、发送遥测，甚至在关键字体缺失时中止转换。

---

## 第六步 – 完整示例（全部代码合在一起）

下面是一段可直接复制粘贴的完整程序。将其粘入 `Program.cs`，修改文件路径后执行 `dotnet run`。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### 预期输出

在缺少 *Comic Sans MS* 的机器上运行程序，控制台会打印类似：

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

同时会生成 `Result.pdf`，其中使用了替代字体，确保转换过程不会崩溃。

---

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| **如果我希望在缺少字体时直接失败而不是替换，该怎么办？** | 在 `FontSubstitutionWarningHandler` 中，当 `info.Description` 包含关键字体名称时抛出异常。 |
| **能否自动嵌入替代字体？** | 可以。检测到缺失字体后，加载已知路径下的备用 `FontInfo` 并通过 `fontSettings.SetFontsFolder` 添加。 |
| **这在 Linux/macOS 上可用吗？** | 完全可以。`FontSettings` 跨平台工作，只需确保回退文件夹中包含相应的 `.ttf` 或 `.otf` 文件。 |
| **警告回调是线程安全的吗？** | 回调在加载文档的同一线程上执行，控制台日志无需额外同步。若在多线程场景下使用，请自行保护共享资源。 |
| **如何将警告写入文件？** | 将 `Console.WriteLine` 替换为 `File.AppendAllText("font_warnings.log", ...)`，或使用任意日志框架（Serilog、NLog）。 |

---

## 生产环境字体处理的专业技巧

1. **缓存字体查找** – 在多个文档加载之间复用同一个 `FontSettings` 实例，可避免重复的文件系统扫描。  
2. **白名单关键字体** – 若品牌要求特定字体，提前验证其存在并在缺失时给出明确错误。  
3. **递归设置字体文件夹** – 将 `recursive: true` 传给 `SetFontFolder`，可扫描子文件夹，适合一次性部署整套字体库。  
4. **结合 `FontSubstitutionSettings`** – 细化替换规则，例如优先使用同一字体族的字体。  

---

## 结论

我们已经**创建了 FontSettings**，配置 `LoadOptions` 以**检测缺失字体**，并绑定回调**捕获字体消息**，展示了在生产环境中**处理缺失字体**的完整方案。整个流程只需几十行 C# 代码，却能让你全面掌握任何 DOCX 文档的字体情况。

接下来，你可以进一步探索：

- **将回退字体直接嵌入输出 PDF**（`PdfSaveOptions.FontEmbeddingMode`）。  
- **根据企业品牌规则进行程序化字体替换**。  
- **在 CI 流水线中集成**，自动标记使用了未授权字体的文档。

动手试一试，依据需求调整警告处理器，让你的文档流水线更加可靠——再也不会因为看不见的字体替换而出现神秘的布局错误。

祝编码愉快！ 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}