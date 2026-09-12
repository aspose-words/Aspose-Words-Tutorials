---
category: general
date: 2026-09-11
description: 在 Word 中使用 Aspose.Words for Java 將形狀群組化並新增矩形形狀。了解如何設定形狀大小、群組物件以及儲存檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: zh-hant
lastmod: 2026-09-11
og_description: 在 Word 中將形狀群組，並使用 Aspose.Words for Java 新增矩形形狀。本教學示範如何設定形狀大小、群組形狀以及匯出文件。
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: 在 Word 中分組形狀 – 使用 Aspose.Words 添加矩形
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 在 Word 中將形狀群組，並使用 Aspose.Words 新增矩形
url: /zh-hant/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中分組形狀並使用 Aspose.Words 添加矩形

如果您需要在程式中添加矩形時 **在 Word 中分組形狀**，本指南提供完整、可直接執行的解決方案。您將會看到如何插入群組形狀、添加矩形形狀、設定形狀大小，最後儲存文件以即時檢視結果。

處理 Word 文件時，通常需要將多個物件（圖片、圖表或簡單的幾何形狀）排列成單一的邏輯單元。將這些物件分組可讓您更輕鬆地一起移動、旋轉或設定樣式。在本教學中，我們亦會說明 **如何添加矩形** 形狀以及 **設定形狀大小**，以達到完美的版面控制。

## 您將學習到

* 如何使用 Aspose.Words for Java 建立新的 Word 文件。  
* **如何分組形狀** 使其行為如同單一物件。  
* **將矩形形狀** 加入群組，並在同一群組中插入圖片。  
* **設定形狀大小**，同時適用於矩形與圖片。  
* 儲存文件並在 Microsoft Word 中開啟以驗證結果。

### 前置條件

* 已安裝 Java 17 或更新版本。  
* 使用 Maven 或 Gradle 來管理相依性。  
* 有效的 Aspose.Words for Java 授權（或免費評估金鑰）。  
* 已將圖片檔案（`sample.png`）放置於已知目錄（將 `YOUR_DIRECTORY` 替換為實際路徑）。

---

## 使用 Aspose.Words 在 Word 中分組形狀

第一步是建立 `Document` 與 `DocumentBuilder`。Builder 提供方便的 API 讓您插入形狀、文字及其他元素。

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **為什麼這很重要：**`DocumentBuilder` 直接作用於底層的 `Document` 物件，讓您無需手動處理低階節點集合即可插入形狀。

### 新增群組形狀

群組形狀是一個容器，可容納其他形狀。可將其視為繪圖物件的資料夾。

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

`insertGroupShape()` 方法會建立一個 `GroupShape` 節點並回傳，之後您即可在其上附加子形狀。  

---

## 將矩形形狀加入群組

現在我們將 **添加矩形形狀** 到先前建立的群組。此矩形可作為圖片的背景或邊框。

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

**提示：** 設定 `FillColor` 與 `StrokeColor` 可讓矩形在最終文件中可見。若省略這些屬性，形狀可能會呈現透明。

### 如何添加矩形

上述程式碼示範了 **如何添加矩形**：透過建立 `Shape` 實例並指定 `ShapeType.RECTANGLE`，再將其附加至 `GroupShape`。此模式同樣適用於其他形狀類型（例如 `ELLIPSE`、`POLYLINE`）。

---

## 設定矩形與圖片的形狀大小

適當的尺寸可確保矩形與圖片正確對齊。此處我們亦 **設定形狀大小** 以供之後插入的圖片使用。

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

矩形與圖片現在共享相同的尺寸（100 × 50 點）。由於它們屬於同一群組，移動或旋轉該群組會同時影響兩個形狀。

> **為什麼要匹配尺寸？** 對齊尺寸可確保圖片整齊地放入矩形內，產生乾淨的「相框」效果。

---

## 儲存文件並檢視結果

最後，我們將文件寫入磁碟。使用 Microsoft Word 開啟檔案時，會看到分組的形狀呈現為單一可選取的物件。

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

當您開啟 `output.docx` 時，會看到矩形內含圖片。點選該形狀會同時選取矩形與圖片，因為它們已 **分組**。

![Word 中分組形狀範例](https://example.com/images/group-shapes-word.png "Word 中分組形狀範例")

*圖片替代文字：* *Word 中分組形狀範例* – 一個顯示分組矩形與圖片的 Word 文件。

---

## 常見問題與邊緣情況處理

| 問題 | 答案 |
|----------|--------|
| **如果我需要不同尺寸的圖片該怎麼辦？** | 在插入後調整 `picture.setWidth()` 與 `picture.setHeight()`。矩形可以保持原始尺寸，或您也可以將其重新調整為相同大小。 |
| **我可以在同一群組中加入更多形狀嗎？** | 可以。對任何額外的 `Shape` 物件呼叫 `group.appendChild(newShape)` 即可。 |
| **如何旋轉整個群組？** | 使用 `group.setRotationAngle(double angleInRadians)`。旋轉會套用到每個子形狀。 |
| **如果圖片檔案遺失會怎樣？** | `insertImage` 會拋出 `FileNotFoundException`。請將呼叫包在 try‑catch 區塊中，並提供備用的佔位形狀。 |
| **之後可以解除群組嗎？** | 呼叫 `group.removeAllChildren()` 以分離子項，然後將它們逐一插回文件中。 |

---

## 結論

現在您已擁有一個完整、可執行的範例，展示 **如何在 Word 中分組形狀**、**添加矩形形狀**、**設定形狀大小**，以及使用 Aspose.Words for Java **儲存** 文件。透過將矩形與圖片分組，您可以將它們作為單一單元移動、調整大小或旋轉——正是許多文件自動化情境所需的功能。

從此您可以進一步探索：

* 在同一群組中加入文字方塊（類似 `how to add rectangle` 風格的文字）。  
* 套用不同的填充圖案或漸層（結合 `set shape size` 與樣式設定）。  
* 使用相同技巧分組圖表、表格或 SmartArt（`how to group shapes` 於其他物件類型）。  

歡迎嘗試其他形狀類型、顏色與版面配置。祝開發愉快！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索其他實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}