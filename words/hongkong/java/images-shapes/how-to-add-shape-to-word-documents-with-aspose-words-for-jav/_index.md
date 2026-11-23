---
category: general
date: 2026-11-22
description: 學習如何使用 Aspose.Words for Java 為 Word 新增圖形——程式化插入矩形並將其隱藏。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: zh-hant
lastmod: 2026-11-22
og_description: 使用 Aspose.Words for Java 為 Word 添加形狀。本教學示範如何插入矩形、隱藏形狀以及儲存文件。
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: 使用 Aspose.Words 在 Word 中添加形狀 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: 如何使用 Aspose.Words for Java 為 Word 文件添加形狀
url: /zh-hant/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Aspose.Words for Java 新增 shape

如果您需要以程式方式 **add shape to Word** 文件，Aspose.Words for Java 讓這個過程變得簡單。於本指南中，您將學習 **how to insert shape**、控制其可見性，以及 **how to hide shape**，使最終檔案呈現如您所預期的樣子。

您將逐步執行一個完整且可執行的範例，該範例會載入現有的 `.docx`、插入一個矩形、將其隱藏，並儲存結果。無需外部腳本或手動步驟，且本教學涵蓋常見變化，例如從頭建立新文件或僅在列印時隱藏 shape。

## 前置條件

* 已安裝 Java 17（或更新版本）— 早期版本亦可使用，但最新的 LTS 版提供更佳效能。  
* 用於相依管理的 Maven 3.8+。  
* 有效的 Aspose.Words for Java 授權（免費評估版可用於學習）。  
* 您偏好的 IDE 或文字編輯器（例如 IntelliJ IDEA、VS Code）。

## 步驟 1：將 Aspose.Words 加入您的 Maven 專案

在您的 `pom.xml` 中加入以下相依性。此設定會取得最新的穩定版（截至 2026 年 11 月）。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **專業提示：** 若您打算自行攜帶授權邏輯一起發佈 JAR，請使用 `<scope>provided</scope>` 標記。

## 為 Word 新增 shape – 初始化文件

第一個功能步驟是取得 `Document` 物件。您可以載入既有檔案或建立全新文件。

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*為何重要*：`Document` 類別是所有 Word 操作的入口。載入既有檔案可保留樣式、頁首與頁尾，而新文件則提供乾淨的起點。

## 如何在 Word 文件中插入 shape

接著，建立 `DocumentBuilder` 以修改文件內容。此建構器提供插入文字、表格與 **shapes** 的方法。

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

`insertShape` 呼叫會回傳一個 `Shape` 物件，您可進一步設定（顏色、邊框、文字等）。尺寸以點 (point) 為單位表示（1 pt = 1/72 in）。

*為何使用矩形*：矩形是最常見的註解、浮水印或佔位元容器。您可將 `ShapeType.RECTANGLE` 替換為 `ShapeType.ELLIPSE`、`ShapeType.LINE` 等，以符合不同的視覺需求。

## 如何在 Word 中隱藏 shape

有時您需要 shape 仍存在於版面配置計算中，但不在最終呈現時顯示。Aspose.Words 提供 `setHidden(true)` 方法來達成此目的。

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

隱藏旗標的運作方式類似 Microsoft Word 中的 **Hidden** 格式選項：shape 會從視覺版面中省略，但仍參與文件的物件模型。此功能可用於：

* 儲存供應用程式稍後讀取的中繼資料或標記。  
* 建立於發佈前會被移除的佔位元。  
* 為不同輸出格式控制可見性（例如在 HTML 中隱藏但在 PDF 中保留）。

> **注意：** 預設情況下，隱藏的 shape 仍會匯出至 PDF。若您也希望在 PDF 中省略，請將 `rectangle.getWrapType( ) = WrapType.NONE`，並相應調整 `Hidden` 屬性。

## 步驟 4：儲存已修改的文件

最後，將變更寫入新檔案。

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

當您在 Microsoft Word 中開啟 `output.docx` 時，矩形不會顯示，但仍是文件樹的一部份。您可透過重新載入檔案並檢查 `Shape.isHidden()` 以程式方式驗證其存在。

### 預期輸出

* `output.docx` 檔案開啟時不會顯示任何 shape。  
* 若使用 Aspose.Words 檢查文件（例如 `doc.getChildNodes(NodeType.SHAPE, true).size()`），shape 數量將為 **1**，證實 shape 雖被隱藏仍存在。

## 進階變化與邊緣案例

### 1. 在全新文件中建立 shape

若從頭開始，請將載入行替換為：

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. 精確定位 shape

預設情況下，`insertShape` 會將 shape 放置於目前游標位置。若要絕對定位，請這樣做：

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. 依輸出格式控制可見性

若您希望 shape 在 Word 介面中可見，但匯出為 PDF 時隱藏，請同時使用 `Shape.setWrapType(WrapType.NONE)` 以及 `Hidden`：

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. 在 shape 內加入文字

矩形可包含文字框：

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

之後您可使用相同的 `setHidden(true)` 呼叫來隱藏文字框。

## 常見陷阱與避免方法

| 症狀 | 原因 | 解決方法 |
|---------|-------|-----|
| 即使已呼叫 `setHidden(true)`，shape 仍顯示 | 文件在設定隱藏旗標之前已被儲存。 | 確保在 `doc.save()` 之前呼叫 `setHidden(true)`。 |
| shape 大小失真 | 在高 DPI 螢幕上混淆了 points 與 pixels。 | 使用 points（72 pt = 1 in）以在各平台保持一致的尺寸。 |
| 隱藏的 shape 仍會列印 | 部分印表機會忽略隱藏旗標。 | 設定 `Shape.setWrapType(WrapType.NONE)`，並同時將 `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)` 清除。 |

## 結論

現在您已了解如何使用 Aspose.Words for Java **add shape to Word** 文件、**how to insert shape**，以及 **how to hide shape**，使其對最終使用者保持隱形，同時仍屬於文件結構的一部份。上述完整範例會載入檔案、插入矩形、將其隱藏，並儲存結果，涵蓋一般使用情境與多種邊緣案例。

接下來您可以探索相關主題，例如使用自訂填色的 **how to insert shape**、針對條件列印的 **how to hide shape in Word**，或使用 Aspose.Words 自動化大量文件處理。試驗不同的 `ShapeType` 值、定位選項與可見性旗標，以符合您的工作流程。

祝程式開發順利，盡情體驗程式化 Word 操作為您的 Java 應用帶來的彈性！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，建立在所示技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [以程式方式建立 Word 文件，於 Java 中使用 Aspose.Words 新增與隱藏 shape](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [如何在 Word 文件中使用 Java 隱藏 shape](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [建立空白 .docx Word 文件，並使用 Aspose.Words 新增隱藏的矩形 shape](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}