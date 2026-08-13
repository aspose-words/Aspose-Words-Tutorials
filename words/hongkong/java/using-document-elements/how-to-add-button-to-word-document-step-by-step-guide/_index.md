---
category: general
date: 2026-07-20
description: 如何使用 Aspose.Words 為 Word 文件添加按鈕。學習只需幾分鐘即可使用 DocumentBuilder 插入 Forms2OleControl
  按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: zh-hant
lastmod: 2026-07-20
og_description: 如何使用 Aspose.Words 在 Word 文件中添加按鈕。請參考本實用指南，使用 Java 嵌入 Forms2OleControl
  CommandButton。
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: 如何在 Word 文件中添加按鈕 – 完整 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: 如何在 Word 文件中加入按鈕 – 逐步指南
url: /zh-hant/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中添加按鈕 – 完整 Aspose.Words 教程

你是否曾經想過 **如何在 Word 文件中添加按鈕** 而不必開啟介面手動點擊？你並非唯一有此需求的人。許多開發人員需要以程式方式嵌入互動控制項——例如在模板中放置一個「Submit」按鈕，之後由最終使用者填寫。好消息是？使用 Aspose.Words for Java，只需幾行程式碼即可完成。

在本教學中，我們將逐步說明如何使用 `DocumentBuilder` 插入類型為 **CommandButton** 的 `Forms2OleControl`。完成後，你將擁有一個可直接使用的 `.docx` 檔案，裡面顯示一個標示為「Click Me」的可點擊按鈕。沒有神祕感，只有清晰的程式碼與每行程式背後的說明。

## 你將學到什麼

- 如何從頭開始建立新的 Word 文件。
- 如何使用 **DocumentBuilder** 放置 **Forms2OleControl**。
- 為何要以我們的方式設定按鈕的標題與尺寸。
- 如何儲存並驗證結果。
- 常見的陷阱（例如缺少函式庫、不支援的控制項類型）以及如何避免。

**先決條件** – 需要 Java 8 以上（或更新版本）以及 Aspose.Words for Java 函式庫（版本 23.12 或更新）。使用 IntelliJ IDEA 或 Eclipse 等 IDE 會更順暢，但任何文字編輯器皆可。

---

## 第一步：設定專案並匯入相依性

在執行任何程式碼之前，Maven（或 Gradle）必須知道從哪裡取得 Aspose.Words。將以下片段加入你的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

如果你偏好使用 Gradle，等價的設定如下：

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **專業提示：** 使用最新版本；較舊的版本可能沒有 `Forms2OleControl` API。

相依性解決後，即可開始撰寫 Java 程式碼。

---

## 第二步：建立新文件並取得 DocumentBuilder

`Document` 類別代表整個 `.docx` 套件，而 `DocumentBuilder` 則是用來在其上繪製內容的畫筆。可將 `DocumentBuilder` 想像成知道下一個元素應放置位置的「游標」。

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**為何這很重要：** 初始化一個全新的 `Document` 為你提供乾淨的畫布。建構器會自動指向第一個段落，讓你不必手動管理節或頁面。

---

## 第三步：插入類型為 CommandButton 的 Forms2OleControl

現在重頭戲登場：`insertForms2OleControl`。此方法會建立一個 OLE（Object Linking and Embedding）控制項，Word 會將其視為表單元素。我們將傳入三個參數：

1. `Forms2OleControlType.COMMANDBUTTON` – 告訴 Word 我們需要一個按鈕。  
2. `100` – 寬度（單位為點，約 1.39 英吋）。  
3. `30` – 高度（單位為點，約 0.42 英吋）。

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**運作原理：** 在底層，Aspose.Words 會在 `word/document.xml` 部分產生相應的 XML，並參照 OLE 物件。你提供的尺寸會被 Word 的版面配置引擎遵守，因此按鈕會正確顯示在建構器游標所在的位置。

---

## 第四步：設定按鈕的標題（文字）

沒有標籤的按鈕會讓人困惑——想像一個沒有顯示文字的電梯按鈕。`setCaption` 方法用來設定可見文字：

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

你可以將標題改成任何文字，例如「Submit」、「Approve」或本地化的字串。標題會儲存在 OLE 物件的屬性中，Word 會原生呈現。

---

## 第五步：儲存文件並驗證結果

最後，將檔案寫入磁碟。選擇一個你有寫入權限的資料夾，否則會拋出 `IOException`。

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

在 Microsoft Word 中開啟 `button-demo.docx`。你應該會在文件頂部看到一個標示為 **Click Me** 的按鈕。點擊該按鈕會觸發預設的 OLE 行為（通常是顯示佔位訊息，除非你綁定了巨集）。

---

## 常見邊緣情況與處理方式

| 情況 | 為何發生 | 解決方法 |
|-----------|----------------|-----|
| **缺少 `Forms2OleControl` 類型** | 較舊的 Aspose.Words 版本未公開此列舉。 | 升級至 23.12 以上版本。 |
| **按鈕顯示為圖片** | Word 的安全設定阻止 OLE 控制項。 | 在信任中心啟用「允許對 VBA 專案物件模型的存取」，或使用支援巨集的 `.docm`。 |
| **尺寸不正確** | 點與像素的混淆。 | 記住 1 點 = 1/72 英吋。相應調整數值。 |
| **儲存時拋出 `FileNotFoundException`** | 路徑不存在。 | 確保在 `doc.save` 前已建立目錄 (`output/`)。使用 `new File("output").mkdirs();`。 |

---

## 延伸範例：新增多個按鈕或其他控制項

如果需要多於一個按鈕，只需在再次呼叫 `insertForms2OleControl` 前，使用 `builder.moveTo` 或 `builder.writeln()` 移動建構器的游標。

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

你也可以透過將 `Forms2OleControlType.COMMANDBUTTON` 換成相應的列舉值（`CHECKBOX`、`COMBOBOX` 等）來插入 **CheckBox**、**ComboBox** 或 **ListBox**。寬度與高度參數仍然適用。

---

## 此方式在更大型 Word 自動化工作流程中的應用

- **模板產生：** 建立包含「Approve」按鈕的合約模板，以供後續簽核使用。  
- **報表產生：** 產生每日報表，內含「Refresh Data」按鈕，可觸發巨集。  
- **表單發佈：** 發送已預先填入互動控制項的問卷。

所有這些情境皆可受益於我們示範的 **Word 自動化** 方法。透過程式化嵌入控制項，可省去手動編輯，降低人為錯誤。

---

## 完整原始碼（可直接複製貼上）

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**預期輸出：** 在 Microsoft Word 中開啟 `output/button-demo.docx` 時，會在檔案頂部垂直排列看到兩個按鈕——「Click Me」與「Submit」。

---

## 結論

我們已逐步說明如何使用 Aspose.Words for Java **在 Word 文件中添加按鈕**。從空白的 `Document` 開始，我們利用 **DocumentBuilder** 插入類型為 **CommandButton** 的 `Forms2OleControl`，設定友善的標題，並儲存結果。此方法可擴展至多個控制項，且能順利整合到更廣泛的 **Word 自動化** 流程中。

準備好迎接下一個挑戰了嗎？試著將按鈕換成 **CheckBox**，或在 `.docm` 檔案中綁定巨集以回應使用者點擊。模式相同——只要更換列舉並調整標題即可。

如果遇到任何問題，請再次確認函式庫版本與輸出資料夾的權限。歡迎在下方留言提問或分享你的使用案例。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在專案中探索其他實作方式。

- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [使用 Aspose.Words 在 Word 文件中插入行內圖片](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}