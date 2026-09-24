---
title: detect document format java using Aspose.Words for Java
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
description: Learn how to detect document format java with Aspose.Words and automatically move files by format. Identify DOC, DOCX, and more.
weight: 25
url: /java/document-loading-and-saving/determining-document-format/
date: 2026-02-22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detect document format java using Aspose.Words for Java

When you need to **detect document format java** in a batch of files, the ability to automatically sort them into the right folders can save hours of manual work. In this tutorial we’ll show you how Aspose.Words for Java makes it easy to identify Word, RTF, HTML, ODT and many other formats, and then **move files by format** into organized directories.

## Quick Answers
- **What does “detect document format java” mean?** It is the process of programmatically identifying a file’s Word processing format (DOC, DOCX, RTF, etc.) using Java code.  
- **Which library provides this capability?** Aspose.Words for Java offers the `FileFormatUtil.detectFileFormat` API.  
- **Can the utility also handle encrypted files?** Yes – the `FileFormatInfo.isEncrypted()` flag tells you if a document is password‑protected.  
- **Do I need a license for production use?** A commercial Aspose.Words license is required for non‑evaluation deployments.  
- **Is it possible to move files automatically after detection?** Absolutely – combine the detection result with `FileUtils.copyFile` to sort files into custom folders.

## What is detect document format java?
`detect document format java` refers to using Java code to inspect a file’s binary header and determine which Word processing format it belongs to (e.g., DOC, DOCX, ODT). Aspose.Words reads the file without fully loading the document, making the operation fast and memory‑efficient.

## Why move files by format?
Organizing documents by their native format simplifies downstream processing:

- **Batch conversions** become straightforward when all DOCX files sit in one folder.  
- **Legacy support**: you can isolate pre‑97 Word files for special handling.  
- **Security**: encrypted documents can be quarantined automatically.  

## Prerequisites

Before we begin, make sure you have:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (download the latest version)  
- Java Development Kit (JDK) 8 or higher installed  
- Basic familiarity with Java I/O and streams  

## Step 1: Set up directories for each format

We first create a clean folder structure where the detected files will be moved. This keeps the workflow tidy and makes it easy to add new format categories later.

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

> **Pro tip:** Use absolute paths or configure the base directory via a properties file to avoid hard‑coding paths in production code.

## Step 2: Detect the document format and move files

The core of **detect document format java** lives in the loop below. It scans every file, determines its type, and copies it to the appropriate folder.

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

The `switch` block can be expanded to cover every format you care about. Each case prints a friendly message and then moves the file to the matching folder.

## Complete source code for detecting document format java

Below is the full, ready‑to‑run example that combines the directory setup and detection logic. Copy it into a Java class, adjust the base path, and run it against a folder of mixed documents.

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
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | The file is corrupted or uses a non‑Word format. | Verify the file extension, or add a fallback to move it to the *Unknown* folder (already in the sample). |
| **Encrypted files throw an exception** | The API tries to read the content before checking encryption. | Always call `info.isEncrypted()` before any other operation on the document. |
| **Directory creation fails on Linux** | Insufficient permissions or missing parent folder. | Ensure the Java process has write access and that the base path exists. |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: You can download Aspose.Words for Java from the [here](https://releases.aspose.com/words/java/) and follow the installation instructions provided.

**Q: What document formats are supported for detection?**  
A: Aspose.Words can detect DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, and older pre‑97 formats, among others.

**Q: Can this code handle password‑protected documents?**  
A: Yes. The `FileFormatInfo.isEncrypted()` flag identifies encrypted files, allowing you to move them to a secure folder without opening them.

**Q: Is there a performance impact when scanning large folders?**  
A: Detection reads only the file header, so even thousands of files are processed quickly. For very large batches, consider parallel streams.

**Q: How can I extend the script to convert unsupported formats?**  
A: After detection, you can call `Document.save` with the desired output format for any supported source type.

## Conclusion

By using **detect document format java** with Aspose.Words, you gain a reliable way to automatically sort, quarantine, or convert Word‑related files. The sample code demonstrates how to create a clean folder hierarchy, identify each file’s format, and move it accordingly—saving you time and reducing manual errors.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}