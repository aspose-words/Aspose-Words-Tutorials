---
category: general
date: 2026-10-07
description: 在 Java 中建立 ActiveX 指令按鈕，並以程式方式將指令按鈕加入 Word 文件。學習如何設定按鈕的左上位置。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: zh-hant
lastmod: 2026-10-07
og_description: 在 Java 中建立 ActiveX 指令按鈕，以在 Word 文件中嵌入互動控制元件。學習如何以程式方式新增指令按鈕、設定其位置，並自訂外觀。
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: 在 Java 中建立 ActiveX 命令按鈕 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: 如何在 Java 中建立 ActiveX 指令按鈕
url: /zh-hant/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中建立 ActiveX command button

如果您需要在 Word 文件中使用 Java **建立 ActiveX command button**，本指南將會精確說明步驟。您將看到一個完整、可執行的範例，示範如何 **以程式方式加入 command button**，並使用 `setLeft` 與 `setTop` 來定位，最後將結果儲存為 `.docx` 檔案。

嵌入互動式按鈕可讓您建立表單、 自動化工作流程，或直接在 Word 檔案中收集使用者輸入。以下步驟涵蓋從專案設定到最終驗證的全部內容，讓您可以毫無遺漏地將程式碼複製到自己的專案中。

## 前置條件

- 已安裝 JDK 17 或更新版本  
- Maven 3.8+（或您偏好的建置工具）  
- Aspose.Words for Java 23.9 或更新版本 – 提供 `DocumentBuilder` 與 OLE 控制支援的函式庫  
- 具備 Java 語法與物件導向概念的基本熟悉度  

如果您使用 Maven，請將相依性加入 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **小技巧：** 使用最新的 Aspose.Words 版本，以獲得錯誤修正與新 OLE 功能的好處。

## 步驟 1：建立新的空白文件與 DocumentBuilder

**建立 ActiveX command button** 的第一步是實例化一個空白的 `Document` 與 `DocumentBuilder`。Builder 為您提供流暢的 API，以插入內容，包括 OLE 控制項。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表記憶體中的 Word 檔案，而 `DocumentBuilder` 則充當游標，讓您能精確地將元素放置在需要的位置。

## 步驟 2：插入 OLE command button 控制項

ActiveX 控制項以 OLE 物件的形式插入。Aspose.Words 提供 `Forms2OleControl` 類別以完成此操作。

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

當您呼叫 `insertForms2OleControl()` 時，Aspose 會自動建立一個佔位形狀，用以容納 ActiveX 按鈕。

## 步驟 3：設定按鈕屬性

現在您可以 **以程式方式加入 command button** 的細節，如 ProgID、標題與大小。最常見的 command button ProgID 為 `"Forms.CommandButton.1"`。

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### 如何設定按鈕的左上座標

按鈕的定位即是次要關鍵字 **how to set button left top** 發揮作用的地方。`setLeft` 與 `setTop` 方法接受以點 (point) 為單位的數值 (1 point = 1/72 英吋)。

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

調整這些數值以符合您的版面配置。例如，若要將按鈕與表格儲存格對齊，請計算儲存格的座標，並將其傳入 `setLeft`/`setTop`。

## 步驟 4：儲存文件

最後，將文件寫入磁碟。該檔案將包含可於 Microsoft Word 開啟時互動的 ActiveX 按鈕。

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

執行 `main` 方法會產生 `CommandButton.docx`。在 Word 中開啟該檔案，若出現提示請啟用內容，您將看到一個標示為 **Click Me** 的可點擊按鈕，位於您指定的座標位置。

![Create ActiveX command button in Java](/images/activex-button-screenshot.png){.center width=600 alt="在 Java 中建立 ActiveX command button 的螢幕截圖，顯示按鈕位於 Word 文件內"}

## 常見變化與邊緣情況

### 新增多個按鈕

如果需要多個按鈕，請對每個控制項重複 **步驟 2** 與 **步驟 3**。記得調整 `setLeft` 與 `setTop`，以免按鈕重疊。

### 變更按鈕行為

ActiveX 按鈕在點擊時可以執行 VBA 巨集。若要附加巨集，請使用巨集名稱設定 `setOnAction` 屬性：

```java
commandButton.setOnAction("MyMacro");
```

請確保目標文件包含相應的 VBA 模組；否則 Word 會顯示錯誤。

### 相容性說明

- 此按鈕僅在支援 ActiveX 的桌面版 Word（例如 Windows 版 Word）中可用。於 Mac 版 Word 或線上編輯器中會顯示為靜態圖片。  
- 若您的環境為混合平台，建議改用 **content control**（`RichTextContentControl`）取代 ActiveX 控制項。

## 完整來源程式碼參考

以下為完整、獨立的範例，您可直接複製到新的 Maven 專案中並立即執行。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**預期輸出：** 執行後，您會在專案的工作目錄中找到 `CommandButton.docx`。在 Microsoft Word 中開啟該檔案，即可看到位於指定位置、標題為 “Click Me” 的按鈕。

## 結論

您現在已了解如何在 Java 中 **建立 ActiveX command button**、**以程式方式加入 command button** 到 Word 文件，並使用 **how to set button left top** 方法精確控制其版面配置。此技術為您開啟了建立豐富、互動式 Word 表單的大門，這些表單可觸發巨集、啟動外部應用程式，或直接在文件內收集使用者輸入。

### 後續步驟

- 探索其他 ActiveX 控制項，例如 `Forms.TextBox.1` 或 `Forms.CheckBox.1`。  
- 結合多個控制項與 VBA 模組，以實作完整功能的表單。  
- 若需跨平台相容性，請將 ActiveX 改為使用 content control。  

歡迎自行嘗試調整大小、標題與定位，以符合您的 UI 設計。若遇到問題，請再次確認您使用的 Aspose.Words 版本支援 OLE 控制項，並檢查 Word 的安全性設定是否允許執行 ActiveX。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 文件中嵌入 OLE 物件與 ActiveX 控制項](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位與加入內容的方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [使用 Java 在 Word 中建立矩形形狀 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}