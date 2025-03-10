---
title: 確定 Aspose.Words for Java 中的文件格式
linktitle: 確定文件格式
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words 偵測 Java 中的文件格式。識別 DOC、DOCX 等。有效地組織文件。
weight: 25
url: /zh-hant/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 確定 Aspose.Words for Java 中的文件格式


## 在 Aspose.Words for Java 中確定文件格式簡介

在 Java 中進行文件處理時，確定正在處理的文件的格式至關重要。 Aspose.Words for Java 提供了用於識別文件格式的強大功能，我們將引導您完成整個過程。

## 先決條件

在我們開始之前，請確保您符合以下先決條件：

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- 系統上安裝的 Java 開發工具包 (JDK)
- Java程式設計基礎知識

## 第 1 步：目錄設定

首先，我們需要設定必要的目錄來有效地組織我們的文件。我們將為不同的文件類型建立目錄。

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

//如果目錄尚不存在，則建立它們。
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

我們為受支援的、未知的、加密的和 97 之前的文件類型建立了目錄。

## 步驟2：檢測文檔格式

現在，讓我們檢測目錄中文件的格式。我們將使用 Aspose.Words for Java 來實現這一點。

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    //顯示文檔類型
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        //根據需要新增其他文件格式的案例
    }

    //處理加密文檔
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        //處理其他文件類型
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

在此程式碼片段中，我們迭代文件，偵測它們的格式，並將它們組織到各自的目錄中。

## 在 Aspose.Words for Java 中確定文件格式的完整原始碼

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        //如果目錄尚不存在，則建立它們。
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
            //顯示文檔類型
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

## 結論

確定 Aspose.Words for Java 中的文件格式對於高效文件處理至關重要。透過本指南中概述的步驟，您可以識別文件類型並在 Java 應用程式中相應地處理它們。

## 常見問題解答

### 如何安裝 Aspose.Words for Java？

您可以從以下位置下載 Aspose.Words for Java：[這裡](https://releases.aspose.com/words/java/)並按照提供的安裝說明進行操作。

### 支援哪些文件格式？

Aspose.Words for Java 支援各種文件格式，包括 DOC、DOCX、RTF、HTML 等。您可以參閱文件以取得完整清單。

### 如何使用 Aspose.Words for Java 偵測加密文件？

您可以使用`FileFormatUtil.detectFileFormat()`偵測加密文件的方法，如本指南所示。

### 使用較舊的文件格式時是否有任何限制？

較舊的文件格式（例如 MS Word 6 或 Word 95）可能在功能和與現代應用程式的相容性方面有限制。必要時考慮升級或轉換這些文件。

### 我可以在 Java 應用程式中自動偵測文件格式嗎？

是的，您可以透過將提供的程式碼整合到您的 Java 應用程式中來自動偵測文件格式。這允許您根據檢測到的格式處理文件。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
