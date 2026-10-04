---
category: general
date: 2026-10-04
description: 學習如何在 Java 中使用 Aspose.Words 初始化 DocumentBuilder 以建立新文件，並加入 ActiveX 按鈕。一步一步的完整程式碼指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: zh-hant
lastmod: 2026-10-04
og_description: 初始化 DocumentBuilder 以建立新文件，並使用 Aspose.Words Java API 嵌入 ActiveX 命令按鈕。請跟隨此簡潔教學。
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: 為新文件初始化 DocumentBuilder – 完整 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: 如何使用 Aspose.Words 為新文件初始化 DocumentBuilder
url: /zh-hant/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 為新文件初始化 DocumentBuilder

如果您需要在 Java 專案中 **initialize DocumentBuilder for new document**，本教學將向您展示具體步驟。您將看到如何建立空白 Word 檔案、附加 ActiveX 命令按鈕，並儲存結果——全部只需一段完整的程式碼範例。

以程式方式操作 Word 文件通常需要處理諸如表單控制項等底層細節。完成本指南後，您將能在不離開 IDE 的情況下嵌入 ActiveX 按鈕，這對於產生範本、自動化報表或互動式表單非常有用。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 Java 17 或更新版本  
* Maven 3.8+（如果您偏好也可使用 Gradle）  
* Aspose.Words for Java 授權（免費試用版可用於測試）  
* 基本的 Java 語法熟悉度  

如果您是 Aspose.Words 的新手，該函式庫提供了高階 API 來建立、編輯與儲存 Word 文件。`DocumentBuilder` 類別是建構文件內容的主要入口。

## 步驟 1：設定 Maven 專案

建立一個新的 Maven 專案（或在現有專案中加入），並加入 Aspose.Words 的相依性：

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **專業提示：** 請保持函式庫版本為最新；較新的發行版會加入對更多表單控制項的支援，並提升效能。

## 步驟 2：為新文件初始化 `DocumentBuilder`

本教學的核心是 **initialize DocumentBuilder for new document** 的操作。您先建立一個空的 `Document` 實例，然後將它傳入 `DocumentBuilder` 建構子。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*為什麼這很重要：* 初始化 `DocumentBuilder` 會將建構器綁定到特定的 `Document` 物件，讓您可以直接在該文件中加入段落、表格或表單控制項。若省略此步驟，建構器將沒有目標可供操作。

## 步驟 3：插入 ActiveX 命令按鈕控制項

Aspose.Words 透過 `Forms2OleControl` 類別提供嵌入傳統 ActiveX 控制項的功能。以下程式碼會在目前游標位置加入 **Forms2OleControl 命令按鈕**。

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### 什麼是 ActiveX 命令按鈕？

ActiveX 命令按鈕是一種舊式 UI 元件，使用者在 Word 文件內點擊時可執行巨集或觸發事件。雖然現代 Office 版本較傾向使用內容控制項，但許多企業範本仍因相容性需求而依賴 ActiveX。

## 步驟 4：儲存文件

插入控制項後，只需呼叫 `save` 即可。產生的檔案會包含 ActiveX 按鈕，並可於 Microsoft Word 中開啟。

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

當您在 Word 中開啟 `ActiveXButton.docx` 時，會看到一個標示為 **Click Me** 的按鈕。除非您另外附加巨集，點擊該按鈕不會產生任何動作，但控制項本身已完整運作。

## 完整、可執行範例

以下是可直接貼入 `src/main/java/com/example/ActiveXButtonDemo.java` 的完整程式碼，已包含所有匯入與錯誤處理，方便您快速測試。

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**預期輸出**

```
Document saved to output/ActiveXButton.docx
```

在 Microsoft Word 2016 或更新版本中開啟產生的檔案，您應該會在第一頁頂部看到一個標示為 *Click Me* 的按鈕。

## 常見變體與邊緣情況

| 情境 | 調整方式 |
|----------|------------|
| **將按鈕加入特定段落** | 在呼叫 `insertForms2OleControl` 前，使用 `builder.moveToParagraph(index, NodeType.PARAGRAPH);` 移動建構器的游標。 |
| **設定按鈕大小** | 使用 `commandButton.setWidth(100);` 與 `commandButton.setHeight(30);` 以點為單位定義尺寸。 |
| **為按鈕加入巨集** | 儲存文件後，在 Word 中開啟，啟用「開發人員」索引標籤，手動將 VBA 巨集附加至按鈕（ActiveX 控制項無法直接由 Aspose.Words 程式碼腳本化）。 |
| **目標為 .doc（二進位）格式** | 將 `doc.save(outputPath, SaveFormat.DOC);` 改為產生舊版 Word 97‑2003 檔案。 |
| **在 Android 上執行** | 使用 Aspose.Words for Android 的 Java API；只要將函式庫納入 APK，相同程式碼即可運作。 |

## 疑難排解技巧

* **`java.lang.NoClassDefFoundError`** – 確認 Aspose.Words JAR 已在 classpath 中。Maven 會自動加入；若手動建置，請將 JAR 放於 `libs/` 並加入 IDE 的函式庫。  
* **按鈕在 Word 中未顯示** – 確認 Word 的信任中心已啟用 *Show legacy forms* 選項（`File → Options → Trust Center → Trust Center Settings → Macro Settings`）。  
* **授權例外** – 若未使用有效授權執行程式，Aspose.Words 會在文件中插入浮水印。請註冊免費試用或購買授權以移除浮水印。

## 結論

您現在已掌握如何 **initialize DocumentBuilder for new document**、插入 ActiveX 命令按鈕，並使用 Aspose.Words for Java 儲存結果。此模式讓您能以程式方式產生互動式 Word 範本，特別適用於自動化報表或表單驅動的工作流程。

接下來，您可以探索其他表單控制項（如 `Forms2OleControlType.CHECKBOX`、`COMBOBOX` 等）、將按鈕與自訂 VBA 巨集結合，或產生包含表格、圖片與樣式的完整文件——全部皆透過相同的 `DocumentBuilder` 工作流程。

---

*想要構建更複雜的 Word 自動化嗎？請參考我們的指南：**insert table with DocumentBuilder**、**apply styles programmatically** 與 **export to PDF with Aspose.Words**。*


## 接下來該學什麼？

以下教學與本指南所示技術緊密相關，提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索其他實作方式。

- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words for Java 將文件另存為 PDF](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [使用 Aspose.Words for Java 為文件加入浮水印](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}