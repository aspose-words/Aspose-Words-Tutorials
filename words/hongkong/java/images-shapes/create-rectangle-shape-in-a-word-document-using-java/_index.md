---
category: general
date: 2026-11-15
description: 使用 Java 在 Word 中建立矩形形狀，學習如何向 Word 新增形狀、設定形狀尺寸，以及有效率地儲存 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: zh-hant
lastmod: 2026-11-15
og_description: 使用 Java 在 Word 文件中建立矩形形狀。學習如何向 Word 添加形狀、設定形狀尺寸，並在數分鐘內儲存 Word 文件。
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: 使用 Java 在 Word 中建立矩形形狀 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 使用 Java 在 Word 文件中建立矩形形狀
url: /zh-hant/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中使用 Java 建立矩形形狀

如果您需要在 Word 檔案中 **建立矩形形狀**，本指南將向您展示如何使用 Java 完成。您將看到如何 **向 Word 添加形狀**、控制 **設定形狀尺寸**，以及最後 **儲存 Word 文件**，且全程不離開您的 IDE。

在接下來的章節中，您將獲得完整可執行的範例、每一行程式碼的說明，以及針對常見問題（如尺寸問題與文件相容性）的實用技巧。無需額外參考資料——只需要 Aspose.Words for Java 函式庫。

## 您將學習到

* 如何初始化 `Document` 與 `DocumentBuilder`。
* 如何插入 **群組形狀**（GroupShape）並在其中放置矩形。
* 如何使用 `setWidth` 與 `setHeight` **定義形狀大小**。
* 如何以 `.docx` 格式 **儲存 Word 文件**。
* 針對不同頁面尺寸與 DPI 設定的邊緣案例處理。

### 前置條件

* Java 17 或更新版本（程式碼亦可在 Java 8 上編譯）。
* Aspose.Words for Java 23.10 或更新版本——可從 Maven Central 取得。
* 具備基本的 Java 語法與物件導向概念。

> **專業提示：** 若您之後計畫加入更多形狀（例如圓形或文字方塊），請將它們放在同一個 `GroupShape` 內。這樣在移動、旋轉或格式化整個集合時會更方便。

## 步驟 1：初始化文件與建構器

第一步是建立一個空白的 Word 檔案，並取得可寫入內容的 `DocumentBuilder`。

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*為什麼這很重要：* `Document` 代表整個檔案，而 `DocumentBuilder` 提供高階方法來插入文字、表格以及 **形狀**。若沒有建構器，您必須手動操作低階節點，十分繁瑣。

## 步驟 2：插入群組形狀以容納多個形狀

**群組形狀**就像一個容器；您可以在裡面加入多個形狀，之後將它們視為單一物件（例如一起移動或旋轉）。

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*為什麼使用群組形狀？* 若您之後想在矩形周圍加入箭頭、圓形或標籤，群組可以確保所有項目保持對齊。它也簡化了 **向 Word 添加形狀** 的流程，因為每新增一個形狀只需一次 `appendChild` 呼叫。

## 步驟 3：建立矩形形狀

現在建立實際會放入群組的矩形。`Shape` 建構子需要傳入所屬的 `Document` 與形狀類型。

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*為什麼是矩形？* `ShapeType.RECTANGLE` 是最常用的基礎形狀，可用於突顯區段、建立佔位符，或直接在 Word 中繪製簡易 UI 原型。

## 步驟 4：定義矩形的大小

設定尺寸時 **設定形狀尺寸** 變得相當重要。您可以使用 Aspose.Words 支援的任何測量單位，預設為點（1 pt = 1/72 英吋）。

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **注意：** 若您偏好使用公釐，可呼叫 `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));`，其中 `1.39 in ≈ 35 mm`。此範例展示了 **定義形狀大小** 的彈性。

## 步驟 5：將矩形加入群組形狀

將矩形附加到先前建立的群組，即可在文件中顯示。

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

此時矩形位於群組的左上角。如需精確定位，可稍後使用 `rectangle.setLeft(...)` 與 `rectangle.setTop(...)` 調整。

## 步驟 6：（可選）儲存文件以檢視結果

最後，將文件寫入磁碟。這就是 **儲存 Word 文件** 的步驟，會產生一個 `.docx` 檔，您可以在 Microsoft Word、LibreOffice 或 Google Docs 中開啟。

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

執行程式後會產生 `RectangleShapeDemo.docx`，其中包含一個位於群組內的單一矩形。開啟檔案時會看到一個純白的矩形——尺寸正是您先前定義的。

### 預期輸出

* 一個名為 `RectangleShapeDemo.docx` 的 Word 檔案。
* 在第一段落內，有一個包含 100 pt × 50 pt 矩形的群組形狀。
* 未加入任何文字，矩形會出現在空白頁面上。

## 常見變化與邊緣案例

| 情況 | 如何調整程式碼 |
|-----------|-----------------------|
| **不同頁面尺寸**（例如 A4） | 在插入形狀前呼叫 `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` |
| **列印時較高 DPI** | 將寬度/高度乘上所需的 DPI 因子，例如 `rectangle.setWidth(200 * 2);` 以取得雙倍解析度 |
| **在矩形內加入文字標籤** | 建立 `Shape` 類型為 `TEXT_BOX`，將其 `setWidth`/`setHeight` 設為與矩形相同，然後加入同一個 `GroupShape` |
| **旋轉矩形** | 使用 `rectangle.setRotationAngle(45);` 讓矩形順時針旋轉 45 度 |
| **儲存為 PDF 而非 DOCX** | 將 `document.save("output.docx");` 改為 `document.save("output.pdf");`——相同的 API 也支援 PDF，且會保留矩形 |

## 建立穩健實作的專業提示

1. **重複使用建構器**——插入群組形狀後，您可以繼續加入段落或表格，而不必重新建立建構器實例。
2. **釋放資源**——雖然 Java 的垃圾回收會處理大多數物件，但若使用串流寫入，請明確呼叫 `document.close();` 以防止檔案句柄泄漏。
3. **驗證尺寸**——在呼叫 `setWidth`/`setHeight` 前，確保數值為正；負值會拋出 `IllegalArgumentException`。
4. **版本相容性**——此程式碼適用於 Aspose.Words 23.x 及以上版本。較早的版本可能需要使用 `Shape.setSize(width, height)` 取代分別的 setter。

## 完整可執行範例

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **結果驗證：** 在 Microsoft Word 中開啟 `output/RectangleShapeDemo.docx`。您應該會看到第一頁頂部居中的指定尺寸矩形。若矩形顯示過小，請調整傳入 `setWidth` 與 `setHeight` 的數值。

## 結論

您現在已掌握如何使用 Java **建立矩形形狀**於 Word 檔案、如何透過 `GroupShape` **向 Word 添加形狀**、如何 **設定形狀尺寸** 與 **定義形狀大小**，以及最後如何 **儲存 Word 文件** 以供後續分發。同樣的模式亦適用於其他形狀類型，讓您能以程式方式建立複雜圖表。

### 接下來要做什麼？

* 探索 **向 Word 添加形狀**，插入圓形、箭頭或文字方塊。
* 將多個形狀合併為單一 `GroupShape`，並套用轉換（旋轉、翻轉）。
* 產生內嵌圖表的報表，然後 **儲存 Word 文件** 為 PDF 以便分享。

歡迎自行實驗尺寸、顏色與定位，以符合您的具體需求。祝開發順利！

## 您接下來應該學習什麼？

以下教學與本指南緊密相關，能進一步深化您對 API 功能的掌握，並提供其他實作方式的範例。

- [建立 Word 文件 Java – 添加陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Java Word 文件中建立矩形形狀 – 完整步驟指南](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [建立 word document java – 隱藏形狀並設定填色](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}