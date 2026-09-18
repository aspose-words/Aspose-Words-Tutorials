---
category: general
date: 2026-09-18
description: 在 Java 中建立空白文件並加入 ActiveX 按鈕。學習如何插入指令按鈕、建立互動式表單，並儲存 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: zh-hant
lastmod: 2026-09-18
og_description: 在 Java 中建立空白文件並嵌入 ActiveX 命令按鈕。按照此步驟指南建立互動式表單並儲存 Word 檔案。
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: 在 Word 中建立帶有互動指令按鈕的空白文件
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: 使用 Java 在 Word 中建立空白文件並加入互動指令按鈕
url: /zh-hant/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 在 Word 中建立帶有互動指令按鈕的空白文件

如果您需要 **create blank document** 且其中包含可點擊的按鈕，本指南將向您展示如何使用 Aspose.Words for Java 完成此操作。您將學會建立互動表單、加入 ActiveX 按鈕，最後儲存 Word 檔案——只需幾個簡潔步驟。

嵌入指令按鈕可將靜態 .docx 轉變為使用者可直接在 Microsoft Word 內互動的功能性表單。本教學亦涵蓋 **how to insert command button**、處理常見陷阱，以及將解決方案擴充至更複雜的表單。

## 前置條件

* Java 17 或更新版本（程式碼可在 JDK 17+ 編譯）
* Aspose.Words for Java 23.9 或更新版本 – 此函式庫提供 `Document`、`DocumentBuilder` 與 `Forms2OleControl`。
* 可加入 Aspose.Words 相依性的 IDE 或建置工具（Maven/Gradle）。
* 具備 Java 語法與 Word 文件概念的基本知識。

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## 步驟 1：建立空白文件

第一個操作是實例化一個新的 `Document` 物件。此物件代表一個尚未有內容的空白 Word 檔案。

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

建立空白文件可為您提供乾淨的畫布，這在您想要以程式方式 **create word document** 而不使用任何既有範本時尤為重要。

## 步驟 2：初始化 DocumentBuilder

`DocumentBuilder` 是用於加入文字、表格與表單控制項的主要類別。它會作用於您剛剛建立的 `Document`。

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

建構器會維持目前的插入點，因此後續指令會影響檔案中的正確位置。

## 步驟 3：插入 Forms2Ole 指令按鈕控制項

Aspose.Words 釋出 `Forms2OleControl` 類別以支援 ActiveX 控制項。若要 **add activex button**，您需要向建構器請求 `COMMANDBUTTON` 類型。

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

`insertForms2OleControl` 方法會將控制項插入建構器目前游標所在的位置。由於該控制項是 ActiveX 物件，僅能在 Microsoft Word 桌面版使用，Word Online 無法支援。

## 步驟 4：設定按鈕的外觀與位置

您可以使用控制項的 setter 方法設定按鈕的標題、大小與位置。位置數值以點 (point) 為單位 (1 點 = 1/72 吋)。

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*為何要設定這些屬性？* 設定 `Top` 與 `Left` 可確保按鈕出現在頁面上您預期的位置，而 `Caption` 定義使用者可見的標籤。若未設定寬度/高度，Word 會使用預設尺寸，可能與您的設計不符。

### 小技巧
如果您打算加入多個控制項，請在每次插入前呼叫 `builder.moveToDocumentEnd()`，以避免物件重疊。

## 步驟 5：儲存含嵌入指令按鈕的文件

最後，將文件寫入磁碟。檔案副檔名必須為 `.docx`（或舊版 Word 使用的 `.doc`），才能保留 ActiveX 控制項。

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

當您在 Microsoft Word 中開啟 `CommandButton.docx` 時，會看到一個標示為 **Click Me** 的按鈕。點擊它會觸發預設的 ActiveX 動作（預設情況下不會執行任何操作）。您之後可以附加巨集或 VBA 腳本以自訂行為。

## 如何在現有表單中插入指令按鈕（可選）

如果您已經有包含文字欄位的表單，且想要 **create interactive form** 並加入按鈕，請依照以下額外步驟：

1. 載入現有文件：`Document doc = new Document("ExistingForm.docx");`
2. 將建構器移動至目標位置：`builder.moveToParagraph(5, 0); // 第 6 段落，第一個節點`
3. 如同步驟 3 所示插入按鈕。
4. 根據段落的版面配置調整按鈕的 `Top`/`Left`。

此方法讓您無需重新建立整個檔案，即可在任何預先製作的 Word 範本中加入 ActiveX 按鈕。

## 邊緣情況與疑難排解

| Situation | What to check | Recommended fix |
|-----------|---------------|-----------------|
| 按鈕未在 Word 中顯示 | 確保您在桌面版 Word 中開啟檔案（Word Online 會剝除 ActiveX）。 | 在 Word 2016 以上的桌面版開啟檔案。 |
| Caption is truncated | 驗證按鈕寬度足以容納文字。 | 增加 `setWidth` 直至標題完整顯示。 |
| Save throws `IOException` | 確認輸出目錄存在且您具有寫入權限。 | 建立目錄或以提升權限執行程式。 |
| Multiple buttons overlap | 建構器的游標在前一次插入後可能未移動。 | 在插入每個新控制項前呼叫 `builder.moveToDocumentEnd()`。 |

## 完整可執行範例

以下是一個完整、獨立的 Java 程式，您可以複製、編譯並執行。它示範了 **create blank document**、**add activex button** 與 **save word document** 的完整流程。

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**預期輸出**

```
Document created: CommandButton.docx
```

開啟 `CommandButton.docx` 後會看到單頁，頁面上有一個標示為 **Click Me** 的按鈕，距離上緣與左緣各 100 pt。

## 結論

您現在已了解如何 **create blank document**、嵌入 **ActiveX button**，以及將普通的 Word 檔案轉變為 **interactive form**。掌握 **how to insert command button** 後，您可以將此模式擴充至加入核取方塊、下拉式清單，甚至自訂的 VBA 驅動邏輯。

接下來，您可以探索以下相關主題：

* **Create interactive form** 搭配文字欄位 (`builder.insertField`)  
* **Add activex button** 可執行 VBA 巨集 (`builder.insertOleObject`)  
* **Create word document** 從範本建立，使用 `Document(docTemplatePath)`  
* 將產生的 .docx 轉換為 PDF 同時保留按鈕（註：PDF 會將按鈕呈現為靜態影像）。

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎延伸。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [在 Word 文件中建立 VBA 專案](/words/english/net/working-with-vba-macros/create-vba-project/)
- [建立新 Word 文件](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}