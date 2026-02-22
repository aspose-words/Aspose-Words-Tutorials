---
date: 2026-02-22
description: 学习如何使用 Aspose.Words 在 Java 中检测文档格式，并自动按格式移动文件。识别 DOC、DOCX 等格式。
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 检测文档格式
url: /zh/java/document-loading-and-saving/determining-document-format/
weight: 25
---

" phrase maybe keep as is? It's a term; but translation rule: translate all text content naturally to Chinese, keep technical terms in English. "detect document format java" is a phrase; maybe keep as is? It's a search phrase. Could translate but maybe keep as is. We'll keep as is in English because it's a specific term. But we can embed Chinese around.

Proceed.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detect document format java using Aspose.Words for Java

当您需要在一批文件中 **detect document format java** 时，能够自动将它们分类到正确的文件夹可以节省大量手动工作时间。在本教程中，我们将展示 Aspose.Words for Java 如何轻松识别 Word、RTF、HTML、ODT 等多种格式，并随后 **move files by format** 到有序的目录中。

## Quick Answers
- **What does “detect document format java” mean?** 它是使用 Java 代码以编程方式识别文件的文字处理格式（DOC、DOCX、RTF 等）的过程。  
- **Which library provides this capability?** Aspose.Words for Java 提供 `FileFormatUtil.detectFileFormat` API。  
- **Can the utility also handle encrypted files?** 可以 —— `FileFormatInfo.isEncrypted()` 标志会告诉您文档是否受密码保护。  
- **Do I need a license for production use?** 非评估部署需要商业版 Aspose.Words 许可证。  
- **Is it possible to move files automatically after detection?** 完全可以 —— 将检测结果与 `FileUtils.copyFile` 结合使用，即可将文件自动分类到自定义文件夹。

## What is detect document format java?
`detect document format java` 指使用 Java 代码检查文件的二进制头部，以确定其所属的文字处理格式（例如 DOC、DOCX、ODT）。Aspose.Words 在不完整加载文档的情况下读取文件，使操作既快速又节省内存。

## Why move files by format?
按原始格式组织文档可以简化后续处理：

- **Batch conversions** 当所有 DOCX 文件集中在同一文件夹时，批量转换变得非常简单。  
- **Legacy support**：您可以将 97 以前的 Word 文件单独隔离，以便进行特殊处理。  
- **Security**：加密文档可以自动隔离，提升安全性。  

## Prerequisites

在开始之前，请确保您已具备：

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)（下载最新版本）  
- 已安装 Java Development Kit (JDK) 8 或更高版本  
- 对 Java I/O 与流有基本了解  

## Step 1: Set up directories for each format

我们首先创建一个干净的文件夹结构，用于存放检测后要移动的文件。这可以保持工作流整洁，并且以后便于添加新的格式类别。

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

> **Pro tip:** 使用绝对路径或通过属性文件配置基础目录，以避免在生产代码中硬编码路径。

## Step 2: Detect the document format and move files

**detect document format java** 的核心逻辑位于下面的循环中。它会遍历每个文件，判断其类型，并将其复制到相应的文件夹。

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

`switch` 代码块可以根据需要扩展，以覆盖您关心的所有格式。每个 case 都会打印友好的信息，然后将文件移动到对应的文件夹。

## Complete source code for detecting document format java

下面是完整的、可直接运行的示例代码，结合了目录创建和检测逻辑。将其复制到 Java 类中，修改基础路径后即可对混合文档文件夹进行检测。

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

## Common issues and troubleshooting

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | 文件已损坏或使用了非 Word 格式。 | 检查文件扩展名，或添加回退逻辑将其移动到 *Unknown* 文件夹（示例中已有）。 |
| **Encrypted files throw an exception** | API 在检查加密状态之前尝试读取内容。 | 在对文档进行任何其他操作前，始终先调用 `info.isEncrypted()`。 |
| **Directory creation fails on Linux** | 权限不足或缺少父文件夹。 | 确保 Java 进程拥有写权限，并且基础路径已存在。 |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: 您可以从 [here](https://releases.aspose.com/words/java/) 下载 Aspose.Words for Java，并按照提供的安装说明进行操作。

**Q: What document formats are supported for detection?**  
A: Aspose.Words 能检测 DOC、DOCX、DOT、DOTX、DOCM、DOTM、RTF、HTML、MHTML、ODT、OTT、FLAT_OPC、WORD_ML 以及更早的 pre‑97 格式等多种类型。

**Q: Can this code handle password‑protected documents?**  
A: 可以。`FileFormatInfo.isEncrypted()` 标志会识别加密文件，您可以在不打开文档的情况下将其移动到安全文件夹。

**Q: Is there a performance impact when scanning large folders?**  
A: 检测仅读取文件头部，即使是成千上万的文件也能快速处理。对于特别大的批次，建议使用并行流（parallel streams）以提升性能。

**Q: How can I extend the script to convert unsupported formats?**  
A: 检测完成后，您可以调用 `Document.save` 并指定目标格式，对任何受支持的源类型进行转换。

## Conclusion

通过使用 Aspose.Words 的 **detect document format java**，您可以可靠地实现自动分类、隔离或转换 Word 相关文件。示例代码展示了如何创建整洁的文件夹层次结构、识别每个文件的格式并相应移动，从而为您节省时间并降低人工错误。

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}