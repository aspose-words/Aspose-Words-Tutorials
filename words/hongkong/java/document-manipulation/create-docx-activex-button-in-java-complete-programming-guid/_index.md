---
category: general
date: 2026-08-14
description: 在 Java 中使用 Aspose.Words 建立 docx ActiveX 按鈕。了解如何以程式方式在 Word 中加入表單按鈕並儲存文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: zh-hant
lastmod: 2026-08-14
og_description: 使用 Aspose.Words 在 Java 中建立 docx ActiveX 按鈕。本指南將示範如何在 Word 中加入表單按鈕、設定它，並儲存檔案。
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: 在 Java 中建立 docx ActiveX 按鈕 – 逐步教學
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: 在 Java 中建立 docx ActiveX 按鈕 – 完整程式設計指南
url: /zh-hant/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中建立 docx ActiveX 按鈕 – 完整程式指南

如果您需要 **在 Java 中建立 docx ActiveX 按鈕**，本指南將一步步帶您完成整個流程。您將學會如何在 Word 中加入表單按鈕、設定屬性，並產出可直接使用的 .docx 檔案。

在自動化舊版 Word 表單時，使用 ActiveX 控制項是常見需求。在本教學中，您將學會使用 Aspose.Words for Java 套件 **在 word 文件中加入表單按鈕**，讓您不必手動編輯即可嵌入互動控制項。

## 您需要的環境

在開始之前，請確保您已具備以下條件：

* Java 17 或更新版本（程式碼亦可在較早版本編譯，但建議使用 Java 17）。
* Aspose.Words for Java 23.10 或更新版本 – 從 Aspose 官方網站下載 JAR，或加入 Maven 依賴。
* IDE（如 IntelliJ IDEA、Eclipse、VS Code）或簡易文字編輯器加上命令列建置工具。
* 基本的 Java 語法與物件導向程式設計知識。

## 使用 Aspose.Words 建立 docx ActiveX 按鈕的步驟

以下步驟說明了 **建立 docx ActiveX 按鈕** 物件並將其嵌入 Word 文件的完整流程。

### 步驟 1：設定專案並匯入 Aspose.Words

如果使用 Maven，請在 `pom.xml` 中加入 Aspose.Words 依賴：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

如果您偏好 Gradle，則使用：

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

依賴解決後，於 Java 原始檔中匯入必要的類別：

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

這些匯入讓您可以使用 `Document`、`DocumentBuilder` 以及用於插入 ActiveX 控制項的 `Forms2OleControl` API。

### 步驟 2：建立新的空白文件

建立一個 `Document` 物件，代表一個尚未有內容的 Word 檔案，準備接受後續的寫入。

```java
// Step 2: Create a new blank document
Document document = new Document();
```

先建立文件可確保後續的 builder 在乾淨的畫布上操作。

### 步驟 3：初始化 DocumentBuilder

`DocumentBuilder` 提供流暢的介面來插入文字、圖片與控制項。將它與剛才建立的文件關聯。

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

builder 會追蹤文件內目前的游標位置，讓下一個插入動作正確出現在您指定的位置。

### 步驟 4：插入 ActiveX CommandButton 控制項

使用 `insertForms2OleControl` 方法嵌入 ActiveX `CommandButton`。此方法會回傳一個 `Forms2OleControl` 實例，您可以進一步設定。

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

此時 .docx 檔案已包含按鈕的佔位元，但尚未設定視覺標題或尺寸。

### 步驟 5：設定按鈕屬性

為控制項設定名稱、標題與版面屬性。這些值決定按鈕在 Word 中的外觀，以及日後透過 VBA 或自動化腳本如何引用。

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **專業提示：** Word 以點 (pt) 為單位測量位置 (1 pt ≈ 1/72 in)。調整 `setTop` 與 `setLeft` 以使按鈕與周圍內容對齊。

### 步驟 6：儲存文件

最後，將文件寫入磁碟。使用 `.docx` 副檔名以保留現代的 Office Open XML 格式。

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

當您在 Microsoft Word 中開啟產生的檔案時，會看到一個 **Submit** 按鈕出現在您指定的座標位置。除非另行附加 VBA 程式碼，點擊該按鈕不會觸發任何動作，但控制項已完整可用於表單工作流程。

## 常見問題與特殊情況

| 問題 | 解答 |
|----------|--------|
| **需要特定的 Word 版本嗎？** | ActiveX 控制項僅在 Windows 桌面版 Microsoft Word 中受支援，Mac 版或 Word Online 無法使用。 |
| **可以套用於 `.doc` 檔案嗎？** | 可以。將文件以 `.doc` 副檔名儲存 (`document.save("ActiveXButton.doc")`) 即可，相同 API 亦支援舊版二進位格式。 |
| **如果按鈕沒有顯示該怎麼辦？** | 確認 **檔案 → 選項 → 信任中心 → 信任中心設定 → ActiveX 設定** 已允許 ActiveX 控制項，同時確保文件未在「受保護檢視」中開啟。 |
| **可以加入其他 ActiveX 控制項嗎？** | 當然可以。將 `Forms2OleControlType.COMMAND_BUTTON` 替換為 `Forms2OleControlType.CHECK_BOX`、`RADIO_BUTTON` 等類型。 |
| **尺寸有限制嗎？** | 控制項尺寸僅受頁面版面限制。過大的尺寸可能導致版面溢位。 |

## 完整可執行範例

以下是一個完整的 Java 類別，您可以直接複製、編譯並執行。程式碼包含所有匯入、`main` 方法以及說明性註解。

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**預期結果：** 執行程式後，工作目錄會產生 `ActiveXButton.docx`。在 Microsoft Word 中開啟時，會看到位於第一頁左上角的可點擊 **Submit** 按鈕。

## 結論

您現在已掌握如何使用 Aspose.Words 在 Java 中 **建立 docx ActiveX 按鈕**，以及如何程式化 **在 word 文件中加入表單按鈕**。從設定專案、建立文件、插入控制項、設定屬性到儲存檔案的完整步驟，已涵蓋從頭到尾的工作流程。

接下來，您可以探索：

* 加入回應按鈕點擊的 VBA 巨集。
* 嵌入其他 ActiveX 控制項，如核取方塊或清單方塊。
* 自動產生包含多個互動元素的多頁表單。

歡迎自行實驗尺寸、位置與標題，以符合您的表單設計需求。祝開發順利！

## 接下來您可以學習什麼？

以下教學與本指南緊密相關，能進一步擴充您在本章節中學到的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索其他實作方式。

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}