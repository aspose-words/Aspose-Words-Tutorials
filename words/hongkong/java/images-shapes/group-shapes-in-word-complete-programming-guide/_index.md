---
category: general
date: 2026-08-14
description: 使用 Aspose.Words 於 Java 中對 Word 進行圖形群組。了解如何建立矩形圖形、設定圖形尺寸，並在空白的 Word 文件中將多個圖形群組在一起。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: zh-hant
lastmod: 2026-08-14
og_description: 使用 Aspose.Words for Java 在 Word 中對形狀進行分組。建立空白 Word 文件、建立矩形形狀、設定形狀尺寸，並在數分鐘內將多個形狀分組。
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Word 中的形狀分組 – 開發者 Java 範例
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Word 中的群組圖形 – 完整程式設計指南
url: /zh-hant/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中群組形狀 – 完整程式指南

如果您需要在 Word 中**群組形狀**，本教學將帶您一步步完成整個流程，使用 Java 與 Aspose.Words。您將學會如何**建立空白 Word 文件**、**建立矩形形狀**、**設定形狀尺寸**，以及最終**群組多個形狀**，使它們如同單一物件般運作。

在 Word 檔案中操作形狀常常感覺像在沒有畫筆的畫布上繪圖。完成本指南後，您將擁有一段可重複使用的程式碼片段，能直接嵌入任何 Java 專案，無論是產生報告、發票或自訂範本。

## 您需要的環境

- Java 8 或更新版本
- Aspose.Words for Java（最新版本，例如 24.9）
- IntelliJ IDEA 或 Eclipse 等 IDE
- 具備基本的物件導向程式設計概念

上述所有前置條件皆可免費安裝，以下程式碼僅需一個 Maven 依賴即可編譯：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 步驟 1：建立空白 Word 文件並初始化 Builder

您首先必須**建立空白的 Word 文件**。這會提供一個乾淨的畫布，之後您可以在上面插入形狀。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整個 *.docx* 檔案，而 `DocumentBuilder` 是用來插入段落、表格與形狀的輔助工具。初始化這兩個物件是任何 Word 自動化任務的基礎。

## 步驟 2：插入群組形狀容器

**群組形狀**的功能類似資料夾，可容納其他形狀。首先，我們建立一個固定尺寸為 400 pt × 200 pt 的容器。

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

`insertGroupShape` 方法會回傳一個 `GroupShape` 物件。之後所有想要視為單一單元的形狀，都必須附加到此物件上。

## 步驟 3：建立矩形形狀並設定形狀尺寸

現在我們**建立矩形形狀**物件，設定其大小，並將其放置於群組內。此步驟同時示範如何精確**設定形狀尺寸**。

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

兩個矩形共享相同的尺寸，但 `left` 屬性不同，因而呈現並排顯示。您可以調整 `setTop` 與 `setLeft` 以安排任何所需的版面配置。

## 步驟 4：儲存包含已群組矩形的文件

將形狀放入群組後，只需儲存 `Document`。產生的檔案會顯示兩個矩形，選取時會一起移動。

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

執行程式會在工作目錄產生 `GroupShape.docx`。在 Microsoft Word 中開啟，選取任一矩形，即可發現整個群組會一起移動——這正是 **在 Word 中群組形狀** 所應達成的效果。

![Group shapes in Word example](group-shapes.png){alt="Group shapes in Word example"}

*圖示：在 Word 文件中兩個矩形形狀已群組在一起。*

## 小技巧：重複使用相同的群組形狀

如果稍後需要加入更多形狀（例如圓形、文字方塊），請保留對 `groupShape` 的參考，並持續呼叫 `appendChild`。如此可避免重新建立容器，並確保所有成員保持同步。

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## 邊緣情況與常見問題

- **如果形狀重疊會怎樣？** 允許重疊；Word 會依照加入的順序呈現。若需明確的堆疊順序，可使用 `setZOrder`。
- **可以跨頁群組形狀嗎？** 不行。`GroupShape` 受限於單一頁面，因為其座標系統是相對於頁面的。
- **群組形狀會繼承格式嗎？** 每個子形狀保留自己的格式（填色、線條樣式）。若要套用統一樣式，請遍歷 `groupShape.getChildNodes()` 並以程式方式設定屬性。

## 完整原始碼供參考

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

執行程式會產生一個 DOCX 檔案，兩個矩形已被 **群組**。選取任一矩形即會同時移動，證明您已成功 **群組多個形狀**。

## 結論

現在您已了解如何使用 Java **在 Word 中群組形狀**，從 **建立空白 Word 文件**、**建立矩形形狀**、**設定形狀尺寸**，到最終 **將多個形狀群組** 成為單一可移動的物件。此模式可擴展至任意數量的形狀，並能與文字、圖片或圖表結合，打造豐富的程式化文件。

### 接下來可以做什麼？

- 探索使用不同類型（橢圓、箭頭、文字方塊）**群組多個形狀**。
- 透過呼叫 `shape.getFillColor()` 與 `shape.getLine().setColor()` 來套用填色或邊框。
- 將群組形狀插入表格儲存格，以製作結構化報告。
- 結合此方法與郵件合併，產生包含品牌圖形的個人化合約。

歡迎自行實驗、調整尺寸或嵌入其他內容。掌握群組技巧後，您的 Word 自動化腳本將變得更具彈性與可維護性。祝編程愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [在 Aspose.Words for Java 中使用文件形狀](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [建立 Word 文件（Java）— 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 文件中使用 Aspose.Words for .NET 建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}