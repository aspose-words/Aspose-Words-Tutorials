---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX 教學示範如何使用 Java 在 Word 文件中加入 CommandButton 控制項。了解完整的程式碼、設定與儲存步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: zh-hant
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX 教學說明如何使用 Java 在 Word 文件中嵌入 CommandButton ActiveX
  控制項。請參考完整範例，建立、設定並儲存文件。
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX 教學 – Java 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX 教學 – 使用 Java 插入 CommandButton
url: /zh-hant/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX 教學 – 使用 Java 插入 CommandButton

如果您需要在 Word 檔案中嵌入 ActiveX 控制項，本 **Aspose.Words ActiveX 教學** 會一步步帶您完成整個流程。您將會看到如何建立空白文件、插入 CommandButton、設定屬性，並儲存結果——全部使用純 Java 程式碼。

此範例使用 Aspose.Words for Java API，無需在建置伺服器上安裝 Microsoft Office。完成本指南後，您即可產生包含完整功能 CommandButton 控制項的 .docx 檔案，供 Windows 環境使用。

## 前置條件

開始之前，請確保您已具備：

- 已安裝 Java Development Kit (JDK) 8 或更新版本。
- Maven 或其他建置工具，以管理相依性。
- Aspose.Words for Java 授權（或暫時的評估金鑰），以避免評估浮水印。
- 基本的 Java 語法與物件導向程式設計概念。

> **小技巧：** 在 `pom.xml` 中加入 Aspose.Words Maven 相依性，讓 IDE 能自動解析類別：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## 步驟 1：建立新空白文件與 `DocumentBuilder`

`Document` 類別代表記憶體中的 Word 檔案，而 `DocumentBuilder` 提供流暢的 API 以編輯文件。初始化這兩個物件即可為後續修改做好準備。

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**為什麼重要：**  
`DocumentBuilder` 會追蹤目前的游標位置，因此任何後續的插入操作（例如加入控制項）都會出現在您預期的位置。

## 步驟 2：插入 CommandButton ActiveX 控制項

Aspose.Words 以 `Forms2OleControl` 來表示 ActiveX 物件。`insertForms2OleControl` 方法需要指定控制項類型，您可以透過 `Forms2OleControlType` 列舉來設定。

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**說明：**  
插入的控制項是一個基於 COM 的物件，當文件在 Windows 環境的 Word 中開啟時，會呈現為可點擊的按鈕。

## 步驟 3：設定按鈕屬性

插入後，您可以調整按鈕的名稱、標題、大小與位置。這些屬性會影響控制項在 Word 中的外觀與行為。

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**為什麼這些設定很重要：**  

- **Name** – 讓 VBA 巨集能夠參照此控制項 (`ActiveDocument.Forms("cmdSubmit")`)。
- **Caption** – 決定使用者點擊的可見標籤。
- **Left / Top** – 控制相對於頁面邊界的放置位置。
- **Width / Height** – 確保在不同螢幕解析度下呈現一致的視覺尺寸。

## 步驟 4：儲存文件

呼叫 `save` 會將記憶體中的表示寫入實體檔案。您可以選擇任何支援的格式（`.docx`、`.doc`、`.pdf` 等）。本教學保留原生的 Word 格式。

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**結果：**  
在 Microsoft Word 中開啟 `ActiveXDemo.docx` 後，會看到一個標示為 **Submit** 的 CommandButton，位於指定的座標。點擊該按鈕會觸發預設行為（預設未附加 VBA 程式碼）。

## 完整原始碼

將上述片段組合起來，完整且可執行的程式如下：

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### 預期輸出

- 在 `output` 資料夾中產生名為 **ActiveXDemo.docx** 的檔案。
- 於 Windows 版 Microsoft Word 開啟時，文件會顯示一個可點擊的 **Submit** 按鈕，位於先前定義的位置。
- 使用者可透過 Word UI（開發人員 → 屬性）選取、移動或將按鈕連結至 VBA 程式碼。

## 常見變化處理

| 情境 | 調整方式 |
|----------|------------|
| **另存為 .doc**（舊版格式） | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **加入事件處理程式** | Word 透過 Aspose.Words 不會公開 ActiveX 事件。您必須在產生文件後手動加入 VBA 程式碼。 |
| **多個控制項** | 以不同的 `setName` 與 `setCaption` 值，重複插入/設定區塊。 |
| **不同控制項類型（例如 CheckBox）** | 在 `insertForms2OleControl` 呼叫中使用 `Forms2OleControlType.CHECKBOX`。 |
| **非 Windows 平台** | ActiveX 控制項僅在 Windows 版 Word 中呈現。若需跨平台解決方案，請考慮使用內容控制項（`StructuredDocumentTag`）。 |

## 最佳實踐與常見陷阱

- **提前授權** – 在建立 `Document` 前先註冊 Aspose.Words 授權，以避免出現評估提示。
- **座標系統** – 位置以點 (pt) 為單位 (1 pt = 1/72 in)。若您的 UI 設計使用像素或公分，請先轉換。
- **檔案路徑** – 使用絕對路徑或 Java 的 `Paths` API，避免因輸出目錄不存在而拋出 `FileNotFoundException`。
- **執行緒安全** – `Document` 與 `DocumentBuilder` 並非執行緒安全。若在平行產生文件，請為每個執行緒建立獨立實例。
- **測試** – 在目標 Word 版本（如 Word 2016、Word 365）上驗證產生的文件，因舊版可能會以不同方式呈現 ActiveX 控制項。

## 結論

本 **Aspose.Words ActiveX 教學** 示範了如何使用 Java 程式化地在 Word 文件中加入 CommandButton 控制項。您已學會：

1. 初始化 `Document` 與 `DocumentBuilder`。
2. 插入 `Forms2OleControl`（類型為 `COMMAND_BUTTON`）。
3. 設定按鈕的名稱、標題、大小與位置。
4. 將文件儲存為包含 ActiveX 控制項的 .docx 檔案。

接下來，您可以探索其他控制項類型、自動化 VBA 巨集注入，或將 ActiveX 控制項與 Aspose.Words 其他功能（如合併列印、內容控制項）結合。嘗試不同版面配置，並將產生的文件整合至更大的 Java 報表管線中。

---


## 接下來該學什麼？

以下教學與本指南內容密切相關，能進一步延伸您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索其他實作方式。

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convert Word to RTF with Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}