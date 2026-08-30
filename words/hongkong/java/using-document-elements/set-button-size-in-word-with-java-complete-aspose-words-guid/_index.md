---
category: general
date: 2026-07-16
description: 使用 Aspose.Words for Java 在 Word 文件中以程式方式設定按鈕大小。了解如何插入 ActiveX 按鈕、設定按鈕位置等更多資訊。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: zh-hant
lastmod: 2026-07-16
og_description: 使用 Java 設定 Word 文件中的按鈕大小。本分步指南說明如何插入 ActiveX 按鈕、設定按鈕位置，以及以程式方式新增按鈕。
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: 使用 Java 在 Word 中設定按鈕大小 – 完整 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: 使用 Java 在 Word 中設定按鈕大小 – 完整 Aspose.Words 使用指南
url: /zh-hant/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 設定按鈕大小 – 完整 Aspose.Words 指南

有沒有想過如何在不開啟 UI 的情況下在 Word 檔案中 **set button size**？你並不是唯一有此需求的人。當你需要即時產生填寫好的表單文件——例如，包含「Submit」按鈕的入職套件——以程式方式完成可節省大量手動工作時間。

在本教學中，我們將逐步說明如何 **insert ActiveX button**、調整其尺寸、正確定位，最後儲存檔案。完成後，你將能夠使用 Aspose.Words for Java **programmatically add button** 控制項至任何 Word 文件。

## 前置條件 – 開始之前你需要的東西

- **Java Development Kit (JDK) 8+** – 程式碼可在任何較新的 JDK 上執行。
- **Aspose.Words for Java** library (download the latest JAR from the official site).  
- 你選擇的 **IDE**——IntelliJ IDEA、Eclipse，或甚至簡單的文字編輯器皆可使用。
- 具備基本的 Java 語法概念；不需要深入的 Word 自動化知識。

> *Pro tip:* 請將 Aspose.Words JAR 放在專案的 classpath 中，否則在嘗試匯入 `com.aspose.words.*` 時會拋出 `ClassNotFoundException`。

## 步驟 1：建立新的 Word 文件

我們首先建立一個空白文件以及 `DocumentBuilder`。把 builder 想像成一支筆，讓我們能在檔案內繪製任何內容。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` 物件代表整個 .docx 檔案，而 `DocumentBuilder` 則是讓我們插入段落、表格，甚至 **ActiveX** 控制項的主要工具。

## 步驟 2：插入 ActiveX 按鈕 – “Insert ActiveX Button” 時刻

現在我們實際在文件中 **insert activex button**。Aspose.Words 提供便利的 `insertForms2OleControl` 方法，會回傳 `Forms2OleControl` 物件。

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *What’s happening under the hood?* `Forms2OleControlType.COMMAND_BUTTON` 告訴 Word 我們需要傳統的 CommandButton，與在 UI 的 Developer 標籤中拖曳的類型相同。

## 步驟 3：設定按鈕大小與位置 – 核心 “Set Button Size” 邏輯

這裡正是主要關鍵字發揮作用的地方。我們將 **set button size** 並且 **set button location**，讓控制項精確出現在頁面上我們想要的位置。

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Why you should care:** 點是 Word 的原生測量單位（1 點 = 1/72 英吋）。透過調整 `setLeft`、`setTop`、`setWidth` 與 `setHeight`，即可取得像素級的精確控制——不再出現「在螢幕上看起來正確，但列印出來卻不對」的情況。

> *Common pitfall:* 若忘記設定寬度或高度，按鈕會保留預設尺寸，可能過小而無法點擊。務必同時指定兩者。

## 步驟 4：儲存文件 – “Create Word Document Button” 完成

最後，我們將檔案寫入磁碟。名稱暗示我們正在 .docx 中 **creating a Word document button**。

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

當你在 Microsoft Word 中開啟 `CommandButtonDemo.docx` 時，會看到一個 **Submit** 按鈕，距左邊緣 100 pt、距上邊緣 150 pt，尺寸為 80 × 30 pt。於 UI 中點擊它會觸發預設的 ActiveX 行為（若需要，可稍後以 VBA 連結）。

### 預期輸出截圖

![顯示已插入按鈕且設定按鈕大小的 Word 文件](https://example.com/images/set-button-size.png "使用 Aspose.Words for Java 設定按鈕大小的 Word 檔案截圖")

*Alt text:* 使用 Java 在 Word 文件中設定按鈕大小

## 步驟 5（可選）：新增更多控制項或樣式化按鈕

如果你需要在單一 Submit 按鈕之外 **programmatically add button** 其他控制項，只需使用新名稱與標題重複插入區塊。亦可調整字型、背景色，甚至稍後綁定 VBA 巨集。

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* 保持所有按鈕尺寸一致以獲得專業外觀。快速方法是將寬度/高度存於常數中。

## 常見問題與邊緣情況

### 「我可以使用公分而非點來設定按鈕大小嗎？」

Word 的 API 只接受點作為單位，但你可以將公分轉換為點 (`points = cm * 28.3465`)。如果偏好公制單位，可撰寫小型輔助方法。

### 「如果我要按鈕出現在特定頁面該怎麼辦？」

插入按鈕後，可使用 `builder.moveToPage(pageNumber)` 將游標移至特定頁面。將控制項插入於移動之後，然後依照上述方式設定其位置。

### 「這能在 .doc（Word 97‑2003）檔案上運作嗎？」

可以——Aspose.Words 會自動處理舊版格式。只需在 `doc.save("Demo.doc")` 中更改檔案副檔名即可。

## 完整、可執行範例

以下是完整程式碼，你可以直接複製貼上到 Java 類別中執行（前提是 Aspose.Words JAR 已在 classpath 中）。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

執行程式後，開啟產生的 `CommandButtonDemo.docx`，即可看到兩個尺寸恰當的按鈕，已可供互動。

## 結論 – 你已掌握在 Word 中設定按鈕大小

我們剛剛完整示範了使用 Aspose.Words for Java 進行 **set button size** 與 **set button location** 的端對端解決方案。依循步驟即可 **insert activex button**、**programmatically add button** 控制項，最終 **create word document button** 元素，讓其行為完全符合需求。

接下來可以嘗試將按鈕嵌入表格儲存格，或附加 VBA 巨集以在提交前驗證表單欄位。同樣的模式亦適用於其他 ActiveX 控制項，如核取方塊或下拉式清單——只需將 `Forms2OleControlType.COMMAND_BUTTON` 替換為相應的列舉值。

如果遇到任何問題，歡迎在下方留言。祝開發愉快，盡情體驗自動化 Word 文件產生的威力！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在本教學示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在專案中探索其他實作方式。

- [如何在 Aspose.Words for Java 中設定 LoadOptions](/words/english/java/document-loading-and-saving/using-load-options/)
- [如何使用 Aspose.Words for Java 移除 Word 文件的頁腳](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Word 文件處理完整指南](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}