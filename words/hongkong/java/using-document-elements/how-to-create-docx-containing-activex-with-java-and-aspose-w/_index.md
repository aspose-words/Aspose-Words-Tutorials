---
category: general
date: 2026-09-27
description: 建立使用 Aspose.Words 的 Java 程式，於 docx 中加入 ActiveX。一步一步學習插入 ActiveX 指令按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: zh-hant
lastmod: 2026-09-27
og_description: 使用 Aspose.Words 在 Java 中建立包含 ActiveX 的 docx 檔案。請依照本指南插入 ActiveX 指令按鈕並儲存檔案。
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: 在 Java 中建立包含 ActiveX 的 docx 檔案 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: 如何使用 Java 與 Aspose.Words 建立包含 ActiveX 的 docx
url: /zh-hant/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 與 Aspose.Words 建立含 ActiveX 的 docx

如果您需要 **建立含 ActiveX 的 docx**，本指南將提供完整解決方案。您將學會如何使用 Aspose.Words for Java **插入 ActiveX 命令按鈕** 到 Word 檔案，然後將結果儲存為可在 Microsoft Word 開啟的 .docx。

以程式方式產生 Word 文件可避免手動編輯，並確保報告、合約或表單範本的一致性。以下步驟涵蓋從專案設定到處理常見問題的全部內容，讓您能將此技術整合至任何 Java 應用程式。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Java Development Kit (JDK) 8 或更新版本。
* Maven 3.6+（或您偏好的其他建置工具）。
* Aspose.Words for Java 授權檔（免費評估版可用於測試）。
* 若要視覺驗證 ActiveX 控制項，請在目標機器上安裝 Microsoft Word。

需要這些項目是因為 Aspose.Words 提供建立文件的 API，而 Word 則負責呈現 ActiveX 控制項。

## 步驟 1：設定 Maven 專案

建立新的 Maven 專案或將 Aspose.Words 相依性加入現有的 `pom.xml`：

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **小技巧：** 請將 Aspose.Words 版本與官方發行說明保持同步，以獲得錯誤修正與最新的 ActiveX 功能。

## 步驟 2：撰寫建立文件的 Java 程式碼

建立名為 `ActiveXDocxCreator` 的類別。以下程式碼包含所有必要的匯入、`main` 方法，以及說明每個操作的詳細註解。

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### 為何每一行都很重要

* `Document` 是所有 Word 內容的容器。建立全新實例即可得到乾淨的畫布。
* `DocumentBuilder` 提供流暢的 API 來插入元素；它會自動追蹤插入點。
* `insertForms2OleControl()` 會建立一個通用的 OLE 控制項佔位符。Aspose.Words 會將其視為 ActiveX 容器。
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` 告訴 Word 此佔位符必須以 CommandButton 呈現。
* `setCaption("Click Me")` 定義按鈕上顯示的文字。
* `setLeft` 與 `setTop` 依頁面邊界設定按鈕位置。請依版面需求調整這些值。
* `setWidth` 與 `setHeight` 為可選項目，但可改善按鈕外觀，尤其在預設尺寸過小時。
* `doc.save` 將記憶體中的結構寫入實體 .docx 檔，供 Word 開啟。

## 步驟 3：驗證產生的文件

在 Microsoft Word 中開啟 `output/ActiveXCommandButton.docx`：

1. 文件應顯示單一頁面，左上角附近有一個標示 **Click Me** 的按鈕。
2. 若按鈕未出現，請確認 Word 的信任中心已啟用 **ActiveX 控制項**（檔案 → 選項 → 信任中心 → 信任中心設定 → ActiveX 設定）。
3. 按鈕僅在支援 ActiveX 的 Windows 版 Word 上可運作；在 macOS 或網頁版 Word 中，控制項會以靜態圖像顯示。

## 步驟 4：處理常見邊緣情況

| 情況 | 原因 | 建議的處理方式 |
|-----------|--------|--------------------|
| 開啟檔案後按鈕遺失 | Word 的安全性設定阻擋 ActiveX | 為受信任位置啟用「對所有控制項不加限制地執行」 |
| 產生的 .docx 無法開啟 | Aspose.Words 版本不相容 | 升級至最新的 Aspose.Words 版本；舊版可能無法正確嵌入所需的 OLE 部分 |
| 需要按鈕執行巨集 | 單純的 ActiveX 不包含巨集程式碼 | 將 ActiveX 控制項與處理 `Click` 事件的 VBA 巨集結合。使用 `DocumentBuilder.insertOleObject` 方法嵌入可執行巨集的範本 |
| 不同頁面尺寸下版面錯位 | 座標為絕對點數 | 在定位控制項前，使用 `builder.getPageSetup().setPageWidth` 與 `setPageHeight` 統一頁面尺寸 |

## 步驟 5：擴充解決方案

只要更改 `ControlType` 列舉，即可插入其他 ActiveX 控制項：

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words 亦支援插入 **ActiveX 文字方塊**、**清單方塊** 與 **下拉式方塊**。相同的定位方法（`setLeft`、`setTop`、`setWidth`、`setHeight`）皆適用。

若需放置多個控制項，只要重複呼叫 `builder.insertForms2OleControl()`，並分別調整每個控制項的座標即可。

## 完整原始檔案

以下為完整的 `ActiveXDocxCreator.java` 檔案，您可直接複製貼上使用：

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

執行此程式後，即會產生 **含 ActiveX 的 docx**，可供需要互動式表單的最終使用者分發。

## 結論

現在您已掌握如何使用 Java 與 Aspose.Words **建立含 ActiveX 的 docx**，以及如何以程式方式 **插入 ActiveX 命令按鈕**。本教學涵蓋了專案設定、完整原始碼、驗證步驟，以及處理常見問題的策略。

接下來您可以探索：

* 為按鈕點擊加入 VBA 巨集以回應事件。
* 嵌入其他 ActiveX 控制項，如核取方塊或下拉式方塊。
* 使用動態資料自動產生多頁表單。

嘗試不同的座標、尺寸與控制項類型，以符合您的文件版面需求。祝開發順利！

## 接下來您可以學習什麼？

以下教學與本指南緊密相關，能進一步擴充您的技巧。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您在專案中掌握更多 API 功能與替代實作方式。

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}