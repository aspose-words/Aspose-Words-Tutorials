---
category: general
date: 2026-08-23
description: 學習如何使用 Java 與 Aspose.Words 在 Word 文件中插入指令按鈕。本指南說明如何新增表單控制項、設定按鈕名稱以及嵌入
  ActiveX 按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: zh-hant
lastmod: 2026-08-23
og_description: 使用 Java 在 Word 文件中插入指令按鈕。請參考本指南，新增表單控制項、設定按鈕名稱，並使用 Aspose.Words 嵌入
  ActiveX 按鈕。
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: 使用 Java 在 Word 中插入命令按鈕 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 如何使用 Java 在 Word 文件中插入指令按鈕
url: /zh-hant/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Java 插入指令按鈕

如果您需要在 Word 檔案中 **插入指令按鈕**，本教學將示範使用 Aspose.Words for Java 的完整解決方案。您將會看到如何新增表單控制項、設定其說明文字，並在不離開 IDE 的情況下設定按鈕名稱。  
本指南涵蓋了建立包含可於 Microsoft Word 中使用的 ActiveX 按鈕的 `.docx` 所需的一切。無需額外工具，範例可在 Java 8+ 上執行。

## 您將學會

* 如何在 Word 文件中新增類型為 **CommandButton** 的表單控制項。  
* 設定 **按鈕名稱** 以及 **新增 ActiveX 按鈕** 屬性的完整步驟。  
* 如何儲存文件，使按鈕在 Word 中開啟時正確顯示。  

您應具備基本的 Java 開發環境，以及能匯入 Aspose.Words 函式庫的 Maven 或 Gradle 專案。

## Prerequisites

| 需求 | 原因 |
|-------------|--------|
| Java 8 or newer | Aspose.Words for Java 可在 Java 8+ 上執行。 |
| Maven or Gradle build tool | 簡化 Aspose.Words 相依性的加入。 |
| Aspose.Words for Java license (or free trial) | 需要授權才能使用完整功能；API 在評估模式下亦可運作。 |
| An IDE such as IntelliJ IDEA or Eclipse | 讓編輯與執行範例更為方便。 |

## 步驟 1：將 Aspose.Words 加入您的專案

如果您使用 Maven，請將以下相依性加入 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

對於 Gradle，請將此行放入 `build.gradle`：

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

相依性解析完成後，您即可在 Java 原始檔中匯入函式庫類別。

## 步驟 2：插入指令按鈕 – 核心程式碼

建立一個名為 `InsertCommandButtonDemo` 的新 Java 類別。以下程式碼執行插入 **指令按鈕** 所需的全部四個動作：

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### 為何每一行都很重要

* **Document & DocumentBuilder** – 它們提供 Word 檔案的記憶體表示，以及修改內容的 API。  
* **insertForms2OleControl** – 此方法 **新增類型為 `COMMAND_BUTTON` 的表單控制項**。回傳的 `Forms2OleControl` 物件代表 ActiveX 控制項。  
* **setName** – 指定程式識別碼 (`btnSubmit`)。Word 巨集或 VBA 可在之後參考此名稱。  
* **setCaption** – 定義使用者在按鈕上看到的文字，回應「如何新增按鈕」的問題。  
* **save** – 將 `.docx` 寫入磁碟，保留內嵌的 ActiveX 按鈕。  

執行程式後會在工作目錄產生 `CommandButtonDemo.docx`。在 Microsoft Word 中開啟該檔案時，會看到標示為 **Submit** 的按鈕，點擊後會在評估模式下顯示預設的 ActiveX 對話框。

## 步驟 3：在 Word 中驗證插入的按鈕

1. 使用 Microsoft Word（2016 或更新版本）開啟 `CommandButtonDemo.docx`。  
2. **Submit** 按鈕會出現在插入時游標所在的位置。  
3. 右鍵點擊該按鈕，選取 **Properties**，即可看到 **Name** 欄位為 `btnSubmit`。  

若按鈕未出現，請確認在 Word 的 Trust Center 設定中已啟用 **ActiveX 控制項**。

## 步驟 4：自訂按鈕（可選）

您可以透過調整大小、位置或加入 VBA 巨集進一步自訂按鈕。`Forms2OleControl` 類別提供額外屬性，如 `setWidth`、`setHeight` 與 `setLeft`。以下範例示範將按鈕放大：

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

這些程式碼可放在 `setCaption` 呼叫之後，示範 **新增 ActiveX 按鈕** 的進階自訂，超出基本插入的範圍。

## 常見陷阱與避免方法

| 症狀 | 原因 | 解決方式 |
|---------|-------|-----|
| 按鈕未在 Word 中顯示 | 文件在加入控制項之前已儲存 | 確保在呼叫 `doc.save` 前已執行 `insertForms2OleControl`。 |
| 按鈕說明文字為空 | `setCaption` 未被呼叫或傳入空字串 | 提供非空字串，例如 `"Submit"`。 |
| VBA 找不到按鈕 | VBA 程式碼與 `setName` 設定的名稱不符 | 保持名稱一致；使用 `setName("btnSubmit")`，並在 VBA 中參考 `btnSubmit`。 |
| 開啟檔案時出現安全性警告 | Word 的巨集安全性阻擋 ActiveX 控制項 | 調整 Trust Center > Macro Settings，或使用受信任的憑證簽署文件。 |

## 完整、可執行的範例

以下為完整的來源檔，可直接複製貼上至您的 IDE。內含匯入語句、例外處理，以及說明每個主要步驟的註解區塊。

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**預期結果：** 執行程式後，`CommandButtonDemo.docx` 內含一個 **Submit** 按鈕。於 Word 開啟檔案時，按鈕正好位於 `DocumentBuilder` 游標所在的位置。

## 後續步驟

* **新增更多表單控制項** – 使用 `Forms2OleControlType.CHECK_BOX`、`RADIO_BUTTON` 或 `TEXT_BOX` 來建立完整的 Word 表單。  
* **結合合併列印** – 在合併列印的文件中插入按鈕，以建立個人化的互動表單。  
* **附加 VBA 巨集** – 以程式方式嵌入會回應按鈕 `Click` 事件的 VBA，實現進階自動化。  

這些主題自然延伸了您剛剛掌握的 **新增表單控制項** 技巧。

---

### 重點回顧

您現在已了解如何使用 Java **插入指令按鈕** 至 Word 文件、如何 **新增表單控制項**、如何 **設定按鈕名稱**，以及如何進行 **新增 ActiveX 按鈕** 的自訂。完整範例即開即用，您亦可依需求套用於任何文件產生工作流程。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中建立表單欄位並新增內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [在 Word 文件中插入下拉式方塊表單欄位](/words/english/net/working-with-form-fields/insert-form-fields/)
- [在 Word 文件中插入核取方塊表單欄位](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}