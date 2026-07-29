---
category: general
date: 2026-07-29
description: 設定按鈕大小 Java 教學：學習如何使用 Java 與 Aspose.Words 在 Word 文件中插入 ActiveX 命令按鈕，並了解尺寸設定與空白文件的建立。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: zh-hant
lastmod: 2026-07-29
og_description: 《設定按鈕大小 Java 指南》示範如何使用 Java 在 Word 檔案中插入 ActiveX 命令按鈕、調整其大小，並以程式方式儲存文件。
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: 設定按鈕大小 Java – 使用 Java 為 Word 添加 ActiveX 命令按鈕
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: 設定按鈕大小 java – 在 Word 中插入 ActiveX 指令按鈕
url: /zh-hant/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – 在 Word 中插入 ActiveX 命令按鈕

你是否曾好奇在自動化 Word 文件時 **how to set button size java** 是怎麼做到的？也許你正在構建一個報告工具，需要在 .docx 檔案內直接放置可點擊的 “Submit” 按鈕。在本教學中，我們將完整示範整個流程——建立空白 Word 文件、插入 ActiveX 命令按鈕，並明確設定其寬度與高度——全部使用 Java 與 Aspose.Words。

我們也會解答許多開發者常見的 “how to insert activex” 問題。完成後，你將擁有一個可執行的程式，產生包含尺寸恰當的命令按鈕的 Word 檔案，方便後續自訂。

---

## 需要的環境

- **Java Development Kit (JDK) 8 或更新版本** – 程式碼可在任何較新的 JDK 上編譯。
- **Aspose.Words for Java**（截至 2026 年 7 月的最新版本）。從 [Aspose website](https://products.aspose.com/words/java) 下載 JAR，或透過 Maven 取得：
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- 任一 IDE 或簡易文字編輯器——IntelliJ IDEA、Eclipse 或 VS Code 都可。
- 一個資料夾，用於存放產生的 **CommandButton.docx**。

就這樣。無需額外的 Office interop 函式庫、COM 技巧，純粹使用 Java。

---

## 步驟說明實作

我們將解決方案分為五個邏輯步驟。每個步驟都有專屬的 H2 標題，其中一個包含我們的 **primary keyword** 以符合 SEO。

### 1. 設定專案並匯入 Aspose.Words

首先，建立一個新的 Maven（或 Gradle）專案，並加入上方顯示的 Aspose.Words 相依性。接著，在 Java 原始檔中匯入所需的類別：

```java
import com.aspose.words.*;
```

> **專業提示：** 若使用 IDE，請讓它自動匯入類別。這樣可省下大量打字時間，且避免拼寫錯誤。

### 2. java create blank word Document

現在我們真的要 **java create blank word** 文件。這是之後 **insert command button word** 的基礎。

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

`Document` 物件在記憶體中代表整個 Word 檔案。此時檔案尚未有頁面、文字——只有一張空白頁。

### 3. 初始化 DocumentBuilder 並插入 ActiveX 控制項

`DocumentBuilder` 是一個輔助工具，讓我們可以新增內容、段落、表格，當然還有 ActiveX 控制項。以下即是回答 **how to insert activex** 的程式碼：

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` 是 Aspose 對 OLE 物件的封裝。透過指定 `COMMANDBUTTON`，我們告訴 Word 嵌入傳統的 ActiveX 命令按鈕。

### 4. How to Set Button Size Java – 調整寬度與高度

現在進入本教學的核心：**how to set button size java**。此控制項提供多個版面屬性——`Left`、`Top`、`Width`、`Height`。直接設定這些屬性即可控制按鈕在頁面上的外觀。

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

為什麼是這些數值？在 Word 中，1 點等於 1/72 英吋。因此 `120` 點的寬度約為 1.67 英吋——足以容納可讀的標籤，同時不會過於佔空間。請依你的版面需求調整這些值；相同的屬性也能回應 **how to set button** 的疑問。

> **注意：** 若需要其他類型的按鈕（例如核取方塊），請將 `Forms2OleControlType.COMMANDBUTTON` 替換為相對應的 enum 值。

### 5. 儲存文件

最後，將文件寫入磁碟：

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

將 `YOUR_DIRECTORY` 替換為你機器上的絕對或相對路徑。執行程式後，用 Microsoft Word 開啟產生的檔案，你會看到一個標示為 “Click Me” 的按鈕，距左側 100 pts、距上方 200 pts，尺寸正好如我們設定的那樣。

---

## 完整範例程式

以下是完整、可直接執行的 Java 類別。將它貼到 `CommandButtonActiveX.java`，調整輸出路徑後點擊 **Run**。

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**預期結果：** 在 Word 中開啟 `CommandButton.docx` 後，會看到單一頁面，中央左右放置一個可點擊的 “Click Me” 按鈕。按鈕尺寸與你設定的數值相符，證明 **set button size java** 正常運作。

---

## 常見問題與邊緣情況

### 若按鈕在 Word 中未顯示，該怎麼辦？

- **檢查 Word 版本。** ActiveX 控制項需要桌面版 Word；Word Online 會移除它們。
- **確保已套用 Aspose.Words 授權**（若使用付費版）。未授權的評估版可能會嵌入浮水印，但仍會顯示控制項。

### 我可以變更按鈕的字型或顏色嗎？

可以。插入控制項後，你可以存取其底層 OLE 物件並操作 VBA 屬性。這屬於較進階的主題——例如可使用 `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` 讓標題變成紅色。

### 如何處理按鈕的點擊事件？

ActiveX 命令按鈕會觸發 VBA `Click` 事件。若要使按鈕具備功能，需要在同一文件中嵌入巨集。Aspose.Words 可透過 `Document.getMacros()` API 新增巨集模組，但巨集程式碼必須以 VBA 撰寫。

### 不同類型的按鈕怎麼辦？

Aspose.Words 支援多種 `Forms2OleControlType` 值：`CHECKBOX`、`OPTIONBUTTON`、`LISTBOX` 等。只要在 `insertForms2OleControl` 呼叫中更換 enum 常數即可試驗。

---

## 生產環境程式碼的專業建議

1. **使用常數儲存版面數值**——未來調整時更方便。
2. **將儲存路徑包裝在 `Path` 物件中**，以避免平台特定的分隔符。
3. **釋放 Document**（或使用 try‑with‑resources），當在迴圈中處理大量檔案時。
4. **在呼叫 `save` 前驗證輸出資料夾**，避免拋出 `FileNotFoundException`。

---

## 結論

你剛剛學會了透過建立空白 Word 檔、插入 ActiveX 命令按鈕，並精確設定其尺寸——全部僅需幾行 Java 程式碼，完成 **set button size java**。此範例同時涵蓋了 **how to insert activex**、**how to set button**、**java create blank word** 與 **insert command button word** 的核心操作，且為單一自足的範例。

接下來的步驟？試著自訂按鈕文字、加入回應點擊的巨集，或在同一頁面嵌入多個控制項。你也可以探索使用 Aspose.Words 將產生的 .docx 轉換為 PDF，將按鈕保留為靜態影像。

歡迎自行嘗試，若遇到問題，請在下方留言。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，建立在此處示範的技巧之上。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在專案中探索其他實作方式。

- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words Java 載入 Word 文件：完整指南](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [如何使用 Aspose.Words for Java 將文件另存為 PDF](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}