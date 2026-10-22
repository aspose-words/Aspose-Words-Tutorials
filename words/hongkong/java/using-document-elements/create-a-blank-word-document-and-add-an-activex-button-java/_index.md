---
category: general
date: 2026-10-16
description: 使用 Java 建立空白 Word 文件，並學習如何加入 ActiveX 按鈕、設定其標題以及使用 Aspose.Words 調整其尺寸。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: zh-hant
lastmod: 2026-10-16
og_description: 使用 Java 建立空白的 Word 文件，然後加入 ActiveX 按鈕，設定其標題，並使用 Aspose.Words 定義其尺寸。
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: 建立空白 Word 文件並嵌入 ActiveX 按鈕 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: 建立空白 Word 文件並加入 ActiveX 按鈕（Java）
url: /zh-hant/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並加入 ActiveX 按鈕（Java）

如果您需要以程式方式 **建立空白 Word 文件**，本指南將示範如何使用 Java 與 Aspose.Words 完成。您亦會學習如何 **加入 ActiveX 按鈕**、**設定按鈕標題**，以及 **設定按鈕尺寸**，讓控制項呈現如您所預期的樣子。

本教學涵蓋：

* 使用 Aspose.Words for Java 初始化空的 Word 檔案。  
* 插入 ActiveX `CommandButton` 控制項。  
* 設定按鈕的標題與大小。  
* 儲存最終的 `.docx` 檔案。

您應具備基本的 Java 知識，並使用最新版本的 Aspose.Words for Java 函式庫（程式碼相容於 23.9 及以上版本）。不需要其他相依性。

![建立空白 Word 文件並加入 ActiveX 按鈕](/images/activex-button-example.png){: .align-center alt="建立空白 Word 文件並加入 ActiveX 按鈕"}

## 使用 Aspose.Words 建立空白 Word 文件

第一步是實例化一個空的 `Document` 物件。此物件在記憶體中代表整個 Word 檔案，並提供 `DocumentBuilder` 類別供編輯使用。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**為什麼這很重要：**  
建立空白文件可提供乾淨的畫布，避免任何隱藏的樣式或段落干擾後續的版面計算。

## 向文件加入 ActiveX 按鈕

Aspose.Words 允許您透過 `Forms2OleControl` 類別嵌入舊版 ActiveX 控制項。以下程式碼會在目前游標位置插入 `CommandButton` 控制項。

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**提示：** `setOleClassName` 的值 `"Forms.CommandButton.1"` 為標準 Microsoft Forms 按鈕的 ProgID。使用其他 ProgID（例如 `"Forms.CheckBox.1"`）會插入不同類型的控制項。

## 設定按鈕標題

標題是顯示在按鈕表面的文字。您可以在儲存文件前隨時更改它。

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**為什麼需要這樣做：** 使用者只有在控制項目的用途清晰時才會理解。設定有意義的標題可提升可用性，特別是當文件在 Windows 版 Word 中開啟時。

## 設定按鈕尺寸

位置與尺寸以點 (point) 為單位指定 (1 點 = 1/72 英吋)。調整這些數值以符合您的版面配置。

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**常見變化：**

| 情境 | 調整方式 |
|----------|------------|
| 觸控螢幕用較大的按鈕 | 成比例增加 `setWidth` 與 `setHeight` |
| 頁面置中按鈕 | 計算 `left = (pageWidth - width) / 2` |
| 欄位中多個按鈕 | 對每個新按鈕遞增 `setTop` |

## 儲存包含 ActiveX 按鈕的文件

最後，將文件寫入磁碟。`.docx` 格式會保留 Windows 版 Microsoft Word 的 ActiveX 控制項。

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**預期結果：** 在 Windows 版 Word 中開啟 `ActiveXCommandButton.docx`，會看到一個空白頁面，頁面上有一個可點擊的按鈕，標籤為 **Click Me**，其位置距左邊距 100 pt、距上邊距 200 pt。

## 完整、可執行範例

將下方完整的類別複製到您的 IDE 中，將 Aspose.Words for Java JAR 加入專案 classpath，然後執行。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

執行程式後會在工作目錄產生 `ActiveXCommandButton.docx`。使用 Windows 版 Microsoft Word 開啟，以驗證按鈕是否如設定般正確顯示。

## 為何建議使用此方法

* **簡易性：** 僅使用核心 Aspose.Words API；不需要 COM 互操作或其他函式庫。  
* **可移植性：** 程式碼可在任何支援 Java 的平台上執行，儘管 ActiveX 控制項本身僅在 Windows 版 Word 中有效。  
* **可維護性：** 所有屬性（標題、尺寸、位置）皆透過清晰且自說明的方式設定，使未來的調整變得簡單。

## 常見陷阱與避免方法

| 問題 | 解決方案 |
|---------|------------|
| 按鈕在 macOS 或 Linux 的 Word 中不顯示 | ActiveX 控制項僅支援 Windows。請改用其他控制項（例如內容控制項）以製作跨平台文件。 |
| 標題被截斷 | 確保按鈕寬度足以容納文字；可增加 `setWidth` 或使用較短的標題。 |
| 按鈕與其他內容重疊 | 調整 `setTop` 與 `setLeft` 數值，或在控制項前插入新段落以為其留出空間。 |

## 後續步驟

現在您已能 **建立空白 Word 文件**、**加入 ActiveX 按鈕**、**設定按鈕標題**，以及 **設定按鈕尺寸**，接下來可以探索：

* 透過 VBA 巨集加入事件處理程式碼（需要嵌入巨集模組）。  
* 在表格佈局中插入多個控制項，以建立類表單文件。  
* 使用 Aspose.Words 的 **FormField** API 以提供跨平台表單解決方案。

嘗試不同的尺寸、位置與標題，以符合您的文件設計需求。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [建立 Word 文件 Java – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [使用 Aspose.Words for Java 為文件新增浮水印](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}