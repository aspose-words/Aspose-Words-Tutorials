---
category: general
date: 2026-08-23
description: 使用 Aspose.Words AI Translator 和 Google 提供程序在 C# 中将字符串翻译成西班牙语。按照分步指南快速在
  C# 中翻译字符串。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: zh
lastmod: 2026-08-23
og_description: 使用 Aspose.Words AI 在 C# 中将字符串翻译成西班牙语。本教程展示如何设置 Google 提供程序、翻译字符串并显示结果。
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: 在 C# 中将字符串翻译成西班牙语 – 完整代码示例
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: 在 C# 中使用 Aspose.Words AI 将字符串翻译成西班牙语
url: /zh/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words AI 将字符串翻译成西班牙语

如果您需要在 .NET 应用程序中**将字符串翻译成西班牙语**，本指南将准确展示如何操作。您将看到一个完整、可运行的示例，它创建了一个翻译器，调用 Google 服务，并打印西班牙语文本。

本教程还涵盖了使用 Aspose.Words AI 库在 C# 中**翻译字符串**，因此您可以将本地化直接集成到代码库中，而无需外部脚本。

## 您需要的条件

- .NET 6.0 SDK 或更高版本（代码可在 .NET Core 和 .NET Framework 上编译）
- 有效的 Google Cloud Translation API 密钥
- NuGet 包 `Aspose.Words.AI`（使用 `dotnet add package Aspose.Words.AI` 安装）
- 如 Visual Studio 2022 等代码编辑器或 IDE

这些前置条件可确保示例开箱即用。

## 使用 Aspose.Words AI 将字符串翻译成西班牙语

本节创建了为 Google 提供程序配置的 `Translator` 对象。该提供程序负责向 Google 翻译端点发送 HTTP 请求。

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**为什么这样可行：**  
- `Translator` 抽象了 HTTP 调用，使用您提供的 API 密钥进行身份验证。  
- `TranslationProvider.Google` 告诉 SDK 将请求路由到 Google Cloud Translation。  
- `Language.Spanish` 选择目标语言代码（`es`）。  
- `Translate` 方法返回翻译后的字符串，您可以在应用程序的任何位置使用它。

## 设置 Google 翻译提供程序

1. **获取 API 密钥**，在 Google Cloud Console → APIs & Services → Credentials 中获取。  
2. **为您的项目启用 Cloud Translation API**。  
3. 将密钥安全存储（环境变量、密钥管理器等）。示例为清晰起见使用了字面量，但生产代码应避免硬编码密钥。

## 在 C# 中翻译字符串 – 步骤详解

| 步骤 | 操作 | 原因 |
|------|--------|--------|
| 1 | 实例化 `Translator`，使用 `TranslationProvider.Google` | 将 SDK 连接到 Google 服务 |
| 2 | 调用 `Translate(source, Language.Spanish)` | 发送源文本并接收西班牙语结果 |
| 3 | 使用 `Console.WriteLine` 输出结果 | 验证翻译并演示用法 |

运行程序将输出：

```
¡Hola mundo!
```

> **注意：** 具体输出可能会因 Google 的翻译模型略有差异（例如 “Hola mundo” 与 “¡Hola mundo!”）。两者都是有效的西班牙语等价表达。

## 运行并验证输出

1. 在项目文件夹中打开终端。  
2. 执行 `dotnet run`。  
3. 确认控制台显示西班牙语短语。

如果控制台显示类似 *“401 Unauthorized”* 的错误，请再次确认 API 密钥是否正确且已为项目启用 Cloud Translation API。

## 常见陷阱与最佳实践

- **API 配额限制** – Google 对每个计费账户实施请求限制。请在 Cloud Console 中监控使用情况，以避免意外的限流。  
- **网络延迟** – 翻译调用是远程 HTTP 请求。考虑缓存经常翻译的字符串以降低延迟。  
- **编码问题** – SDK 使用 UTF‑8 字符串；确保源文件以 UTF‑8 编码保存，以保留特殊字符。  
- **错误处理** – 将 `Translate` 调用包装在 try‑catch 块中，以处理 `ApiException` 并提供回退文本。

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## 扩展示例

- **翻译成其他语言** – 将 `Language.Spanish` 替换为 `Language.French`、`Language.German` 等。  
- **批量翻译** – 在循环中调用 `Translate` 以处理字符串列表。  
- **与 UI 集成** – 在 ASP.NET Core Razor 页面、Windows Forms 或 WPF 应用程序中使用翻译后的字符串。

## 结论

您现在已经了解如何在 C# 中使用 Aspose.Words AI 和 Google 翻译服务**将字符串翻译成西班牙语**。完整的解决方案涵盖了提供程序设置、翻译调用、错误处理以及输出验证。

接下来，您可以尝试更多语言、缓存结果以提升性能，并将翻译器集成到更大的本地化流水线中。

--- 

*准备本地化更多内容吗？查看下一篇关于 **在 C# 中使用 Azure Cognitive Services 翻译字符串** 的教程，了解另一种云提供商。*

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [使用字符串替换](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [使用字符串替换](/words/english/net/find-and-replace-text/replace-with-string/)
- [使用 Aspose.Words 创建 Word 文档 – 步骤指南](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}