---
date: 2025-12-20
description: 了解如何在 Java 中使用 Aspose.Words 按类型组织文件并检测文档格式。支持 DOC、DOCX、RTF 等。
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 按类型组织文件
url: /zh/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 按类型组织文件

当您需要在 Java 应用程序中**按类型组织文件**时，第一步是可靠地确定每个文档的格式。Aspose.Words for Java 使这变得简单，能够检测 DOC、DOCX、RTF、HTML、ODT 以及许多其他格式——甚至是加密或未知的文件。在本指南中，我们将演示如何设置文件夹、检测文件格式并自动对文件进行分类。

## 快速回答
- **“按类型组织文件”是什么意思？** 它指的是根据检测到的格式（例如 DOCX、PDF、RTF）自动将文档移动到相应的文件夹中。  
- **哪个库可以在 Java 中检测文件格式？** Aspose.Words for Java 提供 `FileFormatUtil.detectFileFormat()`。  
- **API 能识别未知文件类型吗？** 能——对于不受支持或无法识别的文件，它会返回 `LoadFormat.UNKNOWN`。  
- **是否支持加密文档的检测？** 完全支持；`FileFormatInfo.isEncrypted()` 标志会告诉您文件是否受密码保护。  
- **生产环境是否需要许可证？** 商业部署需要有效的 Aspose.Words 许可证。

## 介绍：使用 Aspose.Words for Java 按类型组织文件

在 Java 中进行文档处理时，确定所处理文件的格式至关重要。Aspose.Words for Java 提供强大的**detect file format java** 功能，本文将带您高效地组织文件。

## 前置条件

在开始之前，请确保您具备以下前置条件：

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- 已在系统上安装 Java Development Kit (JDK)
- 基本的 Java 编程知识

## 第一步：目录设置

首先，需要创建必要的目录以有效组织文件。我们将为不同的文档类型创建目录。

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

我们已经为受支持、未知、加密以及 pre‑97 文档类型创建了相应的文件夹。

## 第二步：检测文档格式

接下来，检测目录中文档的格式。我们将使用 Aspose.Words for Java 来实现。

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
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

在此代码片段中，我们遍历文件，**detect file format java**，并将它们组织到相应的文件夹中。

## 完整源码：在 Aspose.Words for Java 中确定文档格式

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
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
            // Display the document type
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

## 如何检测文件格式（Java）

`FileFormatUtil.detectFileFormat()` 方法检查文件头并返回一个 `FileFormatInfo` 对象。该对象告诉您 **load format**、文件是否加密以及其他有用的元数据。利用这些信息，您可以以编程方式**identify unknown file types** 并决定如何处理每个文件。

## 识别未知文件类型

当 API 返回 `LoadFormat.UNKNOWN` 时，文件要么已损坏，要么使用了 Aspose.Words 不支持的格式。在我们的示例代码中，我们会将这些文件移动到 **Unknown** 文件夹，以便您稍后进行检查。

## 常见问题及解决方案

| 问题 | 原因 | 解决方案 |
|------|------|----------|
| 文件总是被放入 *Supported* 文件夹 | `FileFormatUtil` 无法读取文件头（例如，文件为空） | 确保传入的文件路径正确且文件不是零字节。 |
| 加密文件抛出异常 | 未处理加密就尝试读取 | 如代码所示，在进一步处理前使用 `info.isEncrypted()` 检查。 |
| 未检测到 pre‑97 Word 文档 | 需要处理 `DOC_PRE_WORD_60` 情况 | 保留 `case LoadFormat.DOC_PRE_WORD_60` 块，将其路由到 *Pre97* 文件夹。 |

## 常见问答

### 如何安装 Aspose.Words for Java？

您可以从[此处](https://releases.aspose.com/words/java/)下载 Aspose.Words for Java，并按照提供的安装说明进行操作。

### 支持哪些文档格式？

Aspose.Words for Java 支持多种文档格式，包括 DOC、DOCX、RTF、HTML、ODT 等。完整列表请参阅官方文档。

### 如何使用 Aspose.Words for Java 检测加密文档？

使用 `FileFormatUtil.detectFileFormat()` 方法；返回的 `FileFormatInfo.isEncrypted()` 标志指示文件是否加密，详见本指南示例。

### 处理旧版文档格式时有哪些限制？

如 MS Word 6 或 Word 95 等旧版格式可能缺少现代功能，且可能存在兼容性问题。建议在可能的情况下将其转换为新格式。

### 能否在我的 Java 应用程序中自动化文档格式检测？

可以，将提供的代码嵌入到应用程序的处理流水线中，即可实现基于检测到的格式自动排序和处理。

---

**最后更新：** 2025-12-20  
**测试环境：** Aspose.Words for Java 24.12（最新）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}