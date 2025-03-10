---
title: 设置字体文件夹系统和自定义文件夹
linktitle: 设置字体文件夹系统和自定义文件夹
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文档中设置系统和自定义字体文件夹，确保您的文档在不同环境中正确显示。
weight: 10
url: /zh/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 设置字体文件夹系统和自定义文件夹

## 介绍

想象一下，您正在制作具有独特字体样式的文档，却发现字体在另一台机器上无法正确显示。令人沮丧，对吧？这就是配置字体文件夹发挥作用的地方。使用 Aspose.Words for .NET，您可以定义系统和自定义字体文件夹，以确保您的文档始终按预期显示。让我们深入了解如何实现这一点。

## 先决条件

在开始之前，请确保您已准备好以下内容：

-  Aspose.Words for .NET Library：如果尚未下载，请下载[这里](https://releases.aspose.com/words/net/).
- 开发环境：像 Visual Studio 这样的 IDE。
- C# 基础知识：熟悉 C# 将帮助您理解代码示例。

## 导入命名空间

首先，在您的项目中导入必要的命名空间：

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

现在，让我们将这个过程分解为简单的步骤。

## 步骤 1：加载文档

首先，将你的 Word 文档加载到 Aspose.Words`Document`对象。此文档将是您想要设置字体文件夹的文档。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## 步骤 2：初始化字体设置

创建新的实例`FontSettings`。该对象将允许您管理字体源。

```csharp
FontSettings fontSettings = new FontSettings();
```

## 步骤 3：检索系统字体源

检索默认系统字体源。在 Windows 计算机上，这通常包括“Windows\Fonts\" 目录。

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## 步骤 4：添加自定义字体文件夹

添加包含附加字体的自定义文件夹。如果您有未安装在系统字体目录中的特定字体，这将非常有用。

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## 步骤 5：更新字体源

将字体源列表转换回数组并将其设置为`FontSettings`目的。

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## 步骤 6：将字体设置应用于文档

最后，应用配置`FontSettings`到您的文档并将其保存为您想要的格式，例如 PDF。

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## 结论

就这样！按照以下步骤操作，您可以确保您的 Word 文档使用正确的字体，无论是系统字体还是存储在特定目录中的自定义字体。此设置有助于在不同环境中保持文档外观的完整性。

## 常见问题解答

### 如果系统文件夹和自定义文件夹中都缺少字体会发生什么情况？

Aspose.Words 将使用默认字体来替代缺失的字体，确保文档仍然可读。

### 我可以添加多个自定义字体文件夹吗？

是的，您可以通过重复创建过程来添加多个自定义字体文件夹`FolderFontSource`对象并将它们添加到字体源列表中。

### 是否可以对自定义字体文件夹使用网络路径？

是的，您可以在`FolderFontSource`构造函数。

### Aspose.Words 支持保存哪些文件格式的文档？

Aspose.Words 支持各种格式，包括 DOCX、PDF、HTML 等。

### 如何处理字体替换通知？

您可以使用以下方式处理字体替换通知`FontSettings`班级`FontSubstitutionWarning`事件。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
