---
category: general
date: 2026-10-16
description: 學習如何使用 Java 在 Word 中對圖形進行群組。此教學示範如何新增矩形圖形、設定圖形的大小與尺寸，並儲存文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: zh-hant
lastmod: 2026-10-16
og_description: 使用 Java 在 Word 中對形狀進行分組。新增矩形形狀，設定形狀大小與尺寸，並以程式方式建立專業文件。
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: 使用 Java 在 Word 中分組圖形 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 使用 Java 在 Word 中將形狀分組 – 完整指南
url: /zh-hant/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Java 群組形狀 – 完整指南

如果您需要以程式方式 **在 Word 中群組形狀**，本教學提供一個即用的解決方案。您將會看到如何 **新增矩形形狀**、調整其大小、設定形狀尺寸，最後儲存一個包含已群組矩形與橢圓的 DOCX 檔案。

在 Word 中群組形狀可用於建立複雜圖表、製作可重複使用的圖形元件，或僅僅在文件之後編輯時保持相關物件一起。程式碼使用 Aspose.Words for Java 函式庫，該函式庫相容於任何近期的 JDK，且不需要安裝 Microsoft Word。

## 前置條件

| 需求 | 原因 |
|-------------|--------|
| Java 17（或更高） | 此函式庫針對現代 Java 執行環境。 |
| Aspose.Words for Java（最新版本） | 提供範例中使用的 `Document`、`DocumentBuilder`、`GroupShape` 與 `Shape` 類別。 |
| IDE 或建置工具（Maven/Gradle） | 用於編譯與執行範例。 |
| 基本的 Java 語法知識 | 需要以了解程式流程。 |

將 Aspose.Words 相依性加入您的專案。對於 Maven：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

或對於 Gradle：

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## 解決方案概觀

本教學遵循清晰的 **問題 → 解決方案 → 說明** 模式：

1. **建立新的 Word 文件** 並取得 `DocumentBuilder`。  
2. **插入 `GroupShape` 容器**，用於容納多個形狀。  
3. **新增矩形**，設定其寬度/高度（即 **set shape size** 步驟），並將其附加至群組。  
4. **新增橢圓**，將其定位於同一群組內，並同樣設定其尺寸。  
5. **儲存** 文件至磁碟。  

每個步驟皆說明了程式碼背後的 **原因**，讓您了解 API 的功能以及如何將其套用至其他情境。

## 步驟 1：建立文件與 DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**為什麼重要：** `Document` 代表整個 DOCX 檔案，而 `DocumentBuilder` 是協助您插入內容而不必處理低階節點管理的工具。先建立它們可為後續所有形狀操作提供乾淨的畫布。

## 步驟 2：插入 GroupShape 容器

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape` 的運作方式類似繪圖物件的 **資料夾**。當您移動、旋轉或刪除群組時，所有子形狀會自動跟隨。這就是 **group shapes in word** 的核心。

## 步驟 3：新增矩形形狀 – 矩形形狀程式碼

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – `Shape` 建構子接受 `ShapeType.RECTANGLE`，告訴 Aspose.Words 繪製矩形輪廓。  
- **set shape size** – `setWidth` 與 `setHeight` 以點 (pt) 定義 **shape dimensions**（1 pt = 1/72 in）。這是控制視覺大小最常見的方式。  
- **Why we use `appendChild`** – 它將矩形附加至 `GroupShape`，使其與群組一起移動。  

## 步驟 4：新增橢圓並將其定位於群組內

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

此橢圓示範了 **set shape dimensions** 超出簡單矩形的應用。透過呼叫 `setLeft`，我們可以控制在群組內的水平偏移，這在排列多個物件時相當有用。

## 步驟 5：儲存文件

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

當您在 Microsoft Word 中開啟 *GroupShapeDemo.docx* 時，會看到一個矩形與一個橢圓被鎖定在同一個群組內。選取任一形狀即會選取整個群組——正是您在 **group shapes in word** 時所期待的行為。

## 完整、可執行的範例

將所有部件組合起來，以下是您可以直接複製到 IDE 中的完整原始檔案：

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### 預期輸出

- 在專案資料夾中會產生名為 **GroupShapeDemo.docx** 的檔案。  
- 在 Word 中開啟該檔案會顯示兩個形狀（矩形與橢圓）已被群組在一起。  
- 拖曳任一形狀會移動整個群組，證實 **group shapes in word** 正常運作。  

## 常見變化與邊緣案例

| 情境 | 要變更的項目 | 原因 |
|----------|----------------|-----|
| **不同的形狀類型**（例如三角形） | 在建構 `Shape` 時使用 `ShapeType.TRIANGLE` 或其他列舉值。 | 允許您建立更複雜的圖表。 |
| **設定填充顏色** | 在建立形狀後呼叫 `shape.getFillColor().setColor(Color.BLUE);`。 | 提升視覺外觀且不影響群組。 |
| **旋轉群組** | `groupShape.setRotationAngle(45);` | 一起旋轉所有子形狀，對圖示很有用。 |
| **在形狀內加入文字** | `shape.appendChild(new Paragraph(document));` 然後加入帶文字的 `Run`。 | 使形狀充當標籤或說明框。 |
| **儲存至串流** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | 對直接回傳文件的 Web 服務很有用。 |

### 專業提示

當您需要根據動態資料（例如條碼長度）**設定形狀尺寸**時，請先以點為單位計算寬度/高度：

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## 結論

您現在已了解如何使用 Java **在 Word 中群組形狀**、如何 **新增矩形形狀**，以及如何以簡潔、可投入生產的程式碼 **設定形狀大小** 與 **設定形狀尺寸**。依循上述步驟，您可以建立可重複使用的圖形群組、將其嵌入自動化報告，或打造自訂的圖表工具，而無需手動開啟 Word。

### 接下來該做什麼？

- 探索 **add rectangle shape** 的變化，例如圓角（使用 `ShapeType.RECTANGLE` 搭配 `setCornerRadius`）。  
- 將 **group shapes in word** 與表格或圖表結合，以製作更豐富的文件。  
- 研究 Aspose.Words API 中的 **text wrapping**（`shape.setWrapType(WrapType.SQUARE)`），以控制周圍文字與群組圖形的互動方式。

歡迎自行實驗、調整 **rectangle shape code**，並分享您的成果

## 接下來應該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [建立 Word 文件 Java – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 中使用 Java 建立矩形形狀 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}