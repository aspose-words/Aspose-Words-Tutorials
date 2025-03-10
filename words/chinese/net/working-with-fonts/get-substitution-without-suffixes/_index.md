---
title: 获取无后缀的替换
linktitle: 获取无后缀的替换
second_title: Aspose.Words 文档处理 API
description: 了解如何在 Aspose.Words for .NET 中管理无后缀的字体替换。按照我们的分步指南，确保您的文档每次都看起来完美无缺。
weight: 10
url: /zh/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 获取无后缀的替换

## 介绍

欢迎阅读本指南，了解如何使用 Aspose.Words for .NET 管理字体替换。如果您曾为文档中字体无法正确显示而苦恼，那么您来对地方了。本教程将逐步指导您如何高效处理无后缀的字体替换。

## 先决条件

在深入学习本教程之前，请确保您已准备好以下内容：

- C# 基础知识：了解 C# 编程将使遵循和执行步骤变得更容易。
-  Aspose.Words for .NET Library：从以下网址下载并安装该库[下载链接](https://releases.aspose.com/words/net/).
- 开发环境：设置一个像 Visual Studio 这样的开发环境来编写和运行您的代码。
- 样本文档：样本文档（例如，`Rendering.docx`) 在本教程中使用。

## 导入命名空间

首先，我们需要导入必要的命名空间来访问 Aspose.Words 提供的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## 步骤 1：定义文档目录

首先，指定文档所在的目录。这有助于找到您要处理的文档。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤 2：设置替换警告处理程序

接下来，我们需要设置一个警告处理程序，该处理程序会在文档处理过程中发生字体替换时通知我们。这对于捕获和处理任何字体问题至关重要。

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## 步骤 3：添加自定义字体源

在此步骤中，我们将添加自定义字体源，以确保 Aspose.Words 可以找到并使用正确的字体。如果您在自定义目录中存储了特定字体，这将特别有用。

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

在此代码中：
- 我们检索当前字体源并添加新的`FolderFontSource`指向我们的自定义字体目录（`C:\\MyFonts\\`）。
- 然后我们使用这个新列表更新字体源。

## 步骤 4：保存文档

最后，应用字体替换设置后保存文档。在本教程中，我们将其保存为 PDF。

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## 步骤 5：创建警告处理程序类

为了有效地处理警告，请创建一个自定义类来实现`IWarningCallback`接口。此类将捕获并记录任何字体替换警告。

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

在本课程中：
- 这`Warning`方法捕获与字体替换相关的警告。
- 这`FontWarnings`集合存储这些警告以供进一步检查或记录。

## 结论

您现在已经掌握了使用 Aspose.Words for .NET 处理无后缀字体替换的过程。这些知识将确保您的文档保持其预期的外观，无论系统上有哪些字体。继续尝试不同的设置和来源，以充分利用 Aspose.Words 的强大功能。

## 常见问题解答

### 如何使用来自多个自定义目录的字体？

您可以添加多个`FolderFontSource`实例`fontSources`列出并相应地更新字体源。

### 在哪里可以下载 Aspose.Words for .NET 的免费试用版？

您可以从[Aspose 免费试用页面](https://releases.aspose.com/).

### 我可以使用以下方法处理多种类型的警告吗`IWarningCallback`?

是的，`IWarningCallback`界面允许您处理各种类型的警告，而不仅仅是字体替换。

### 我可以在哪里获得 Aspose.Words 的支持？

如需支持，请访问[Aspose.Words 支持论坛](https://forum.aspose.com/c/words/8).

### 可以购买临时许可证吗？

是的，你可以从[临时执照页面](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
