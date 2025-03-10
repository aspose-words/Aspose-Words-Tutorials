---
title: 在 Aspose.Words for Java 中确定文档格式
linktitle: 确定文档格式
second_title: Aspose.Words Java 文档处理 API
description: 了解如何使用 Aspose.Words 检测 Java 中的文档格式。识别 DOC、DOCX 等。高效组织文件。
weight: 25
url: /zh/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中确定文档格式


## Aspose.Words for Java 中确定文档格式的简介

使用 Java 进行文档处理时，确定所处理文件的格式至关重要。Aspose.Words for Java 提供了强大的文档格式识别功能，我们将引导您完成整个过程。

## 先决条件

在开始之前，请确保您满足以下先决条件：

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- 系统上安装了 Java 开发工具包 (JDK)
- Java 编程基础知识

## 步骤 1：目录设置

首先，我们需要设置必要的目录来有效地组织我们的文件。我们将为不同的文档类型创建目录。

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

//如果目录不存在，则创建目录。
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

我们为受支持的、未知的、加密的和 97 年之前的文档类型创建了目录。

## 第 2 步：检测文档格式

现在，让我们检测目录中文档的格式。我们将使用 Aspose.Words for Java 来实现这一点。

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    //显示文档类型
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        //根据需要添加其他文档格式的案例
    }

    //处理加密文档
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        //处理其他文档类型
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

在此代码片段中，我们遍历文件，检测它们的格式，并将它们组织到相应的目录中。

## 用于在 Aspose.Words for Java 中确定文档格式的完整源代码

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        //如果目录不存在，则创建目录。
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            //显示文档类型
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## 结论

在 Aspose.Words for Java 中确定文档格式对于高效处理文档至关重要。通过本指南中概述的步骤，您可以识别文档类型并在 Java 应用程序中进行相应处理。

## 常见问题解答

### 如何安装 Aspose.Words for Java？

您可以从[这里](https://releases.aspose.com/words/java/)并按照提供的安装说明进行操作。

### 支持哪些文档格式？

Aspose.Words for Java 支持多种文档格式，包括 DOC、DOCX、RTF、HTML 等。您可以参考文档获取完整列表。

### 如何使用 Aspose.Words for Java 检测加密文档？

您可以使用`FileFormatUtil.detectFileFormat()`方法来检测加密文档，如本指南所示。

### 使用旧文档格式时有什么限制吗？

较旧的文档格式（例如 MS Word 6 或 Word 95）在功能和与现代应用程序的兼容性方面可能存在限制。必要时请考虑升级或转换这些文档。

### 我可以在我的 Java 应用程序中自动检测文档格式吗？

是的，您可以通过将提供的代码集成到 Java 应用程序中来自动检测文档格式。这样您就可以根据检测到的格式来处理文档。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
