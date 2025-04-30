---
"description": "了解如何在 Aspose.Words for .NET 中设置字体回退设置。本指南内容详尽，可确保您文档中的所有字符均能正确显示。"
"linktitle": "设置字体回退设置"
"second_title": "Aspose.Words文档处理API"
"title": "设置字体回退设置"
"url": "/zh/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 设置字体回退设置

## 介绍

处理包含多种文本元素（例如不同语言或特殊字符）的文档时，确保这些元素正确显示至关重要。Aspose.Words for .NET 提供了一项名为“字体回退设置”的强大功能，当原始字体不支持某些字符时，该功能可帮助您定义替换字体的规则。在本指南中，我们将通过分步教程探索如何使用 Aspose.Words for .NET 设置“字体回退设置”。

## 先决条件

在深入学习本教程之前，请确保您已满足以下先决条件：

- C#基础知识：熟悉C#编程语言和.NET框架。
- Aspose.Words for .NET：从下载并安装 [下载链接](https://releases。aspose.com/words/net/).
- 开发环境：像 Visual Studio 这样的设置，用于编写和运行代码。
- 示例文档：提供示例文档（例如， `Rendering.docx`）准备进行测试。
- 字体后备规则 XML：准备一个定义字体后备规则的 XML 文件。

## 导入命名空间

要使用 Aspose.Words，您需要导入必要的命名空间。这样才能访问文档处理所需的各种类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## 步骤1：定义文档目录

首先，定义文档的存储目录。这对于定位和处理文档至关重要。

```csharp
// 文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤 2：加载文档

将您的文档加载到 Aspose.Words `Document` 对象。此步骤允许您以编程方式处理文档。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步骤3：配置字体设置

创建新的 `FontSettings` 对象并从 XML 文件加载字体回退设置。此 XML 文件包含字体回退规则。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## 步骤 4：将字体设置应用于文档

分配已配置的 `FontSettings` 到文档。这确保在渲染文档时应用字体回退规则。

```csharp
doc.FontSettings = fontSettings;
```

## 步骤5：保存文档

最后，保存文档。保存操作期间将使用字体回退设置来确保字体替换正确。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML 文件：字体后备规则

以下是定义字体后备规则的 XML 文件的示例：

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## 结论

通过遵循以下步骤，您可以有效地设置和使用 Aspose.Words for .NET 中的字体回退设置。这可确保您的文档正确显示所有字符，即使原始字体不支持某些字符。实施这些设置将极大地提高文档的质量和可读性。

## 常见问题解答

### Q1：什么是字体回退？

字体回退功能允许在原始字体不支持某些字符时替换字体，以确保所有文本元素的正确显示。

### 问题2：我可以指定多个后备字体吗？

是的，您可以在 XML 规则中指定多个备用字体。Aspose.Words 将按照指定的顺序检查每个字体，直到找到支持该字符的字体。

### 问题3：在哪里可以下载 Aspose.Words for .NET？

您可以从 [Aspose下载页面](https://releases。aspose.com/words/net/).

### Q4：如何创建字体后备规则的 XML 文件？

XML 文件可以使用任何文本编辑器创建。它应遵循本教程中示例所示的结构。

### 问题5：是否支持Aspose.Words？

是的，您可以在 [Aspose.Words 支持论坛](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}