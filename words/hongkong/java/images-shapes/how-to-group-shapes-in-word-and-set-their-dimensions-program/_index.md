---
category: general
date: 2026-11-25
description: 如何在 Word 中使用 Java 將形狀分組，以及如何在 DOCX 檔案中使用 Aspose.Words 設定形狀尺寸。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: zh-hant
lastmod: 2026-11-25
og_description: 如何使用 Aspose.Words Java API 在 Word 中將形狀分組並快速設定形狀大小。請跟隨完整的逐步解決方案。
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: 如何在 Word 中將形狀分組並設定其尺寸 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: 如何在 Word 中將圖形分組並以程式方式設定其尺寸
url: /zh-hant/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中將圖形分組並以程式方式設定其尺寸

如果您需要 **how to group shapes in Word** 並控制其精確大小，本指南將提供完整、可執行的解決方案。使用 Aspose.Words for Java，您可以建立矩形、橢圓，將它們加入 `GroupShape`，然後 **how to set shape dimensions** 如寬度與高度，全部寫入同一個 DOCX 檔案。

您將學會：

* 從頭開始建立新的 Word 文件。  
* 插入 `GroupShape`（版本 24.9 中的全新 API）。  
* 將矩形與橢圓加入分組。  
* 使用 `setWidth` 與 `setHeight` **Set shape size Word** 精確設定圖形尺寸。  
* 將文件儲存至磁碟。

不需要任何外部工具——只要 Java 17+、Maven，以及 Aspose.Words for Java 函式庫即可。

## 前置條件

* Java Development Kit 17 或更新版本。  
* Maven（或 Gradle）用於相依性管理。  
* Aspose.Words for Java 24.9 或更新（`GroupShape` API 於 24.9 版加入）。  
* 具備基本的 Java 語法與物件導向概念。

如果您尚未將 Aspose.Words 加入專案，請加入以下 Maven 相依性：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## 步驟 1：建立新文件與 DocumentBuilder

`Document` 類別代表整個 Word 檔案，而 `DocumentBuilder` 提供方便的方式加入內容。

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*為什麼需要這一步？*  
建立全新的 `Document` 能讓您得到乾淨的畫布。`DocumentBuilder` 是高階輔助工具，可讓您插入段落、表格，以及本例中的圖形。

## 步驟 2：插入 GroupShape（版本 24.9 中的全新 API）

`GroupShape` 如同容器；您加入的任何圖形都會成為同一視覺群組的一部份。

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*為什麼使用 `GroupShape`？*  
將圖形分組可簡化一次移動、旋轉或套用格式的操作。此 API 於 24.9 版加入，較舊版本無法編譯此行程式碼。

## 步驟 3：建立矩形、設定尺寸，並加入群組

此處示範 **how to set shape dimensions** 用於矩形的設定方式。

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*為什麼要明確設定寬度與高度？*  
Word 以點 (point) 為單位儲存圖形尺寸。透過呼叫 `setWidth` 與 `setHeight`，您可以掌控精確的視覺佔位，這在需要精確版面配置或匯出為 PDF 時尤為重要。

## 步驟 4：建立橢圓、設定尺寸，並加入同一個群組

相同的 **set shape size word** 技巧適用於任何圖形類型。

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*為什麼要將橢圓加入同一個 `GroupShape`？*  
兩個圖形會一起作為單一單位移動。這對於製作圖示、標誌或必須保持對齊的複雜圖表非常有用。

## 步驟 5：將含有分組圖形的文件儲存

最後，將 DOCX 檔案寫入磁碟。

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

執行此程式後會產生名為 **GroupShape.docx** 的檔案，內含已分組的矩形與橢圓。當您在 Microsoft Word 中開啟此檔案時，會看到兩個圖形如同單一物件般，可一起拖曳、調整大小或旋轉。

### 預期輸出

* 一個 Word 文件（`GroupShape.docx`），僅有一頁。  
* 一個 `GroupShape`，內含 100 × 50 pt 的矩形與 80 × 80 pt 的橢圓。  
* 選取任一圖形即會同時選取整個群組。

## 常見問題與邊緣案例

### 如何變更分組圖形的位置？

在建立 `GroupShape` 後，您可以設定其 `left` 與 `top` 屬性：

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

這些座標同樣以點為單位。

### 若需要加入超過兩個圖形該怎麼辦？

`GroupShape` 的行為如同其他容器節點。對每個額外的圖形呼叫 `groupShape.appendChild(yourShape)` 即可。API 並未限制子節點數量。

### 能否對單一圖形套用樣式（填色、線條粗細）？

可以。每個 `Shape` 物件都提供格式屬性：

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### 此程式碼能在較舊的 Aspose.Words 版本上執行嗎？

`insertGroupShape` 方法於 24.9 版加入。若您使用較早的版本，必須透過節點樹手動建立 `GroupShape`，流程較為繁雜。建議升級至新版。

## 專業提示

* **使用點作為單位以保持一致性** – Word 的內部單位為點 (1/72 英吋)。從像素或公分轉換可能導致尺寸不符。  
* **先分組再定位** – 在加入所有子圖形後再設定 `GroupShape` 的位置，否則可能需要重新計算偏移量。  
* **重複使用 DocumentBuilder** – 透過在每次 `insertGroupShape` 前移動建構器游標 (`builder.moveTo`) ，即可在同一文件中插入多個群組。

## 結論

您現在已掌握使用 Aspose.Words for Java **how to group shapes in Word** 以及 **how to set shape dimensions** 的完整端對端範例。本文示範了建立文件、插入 `GroupShape`、加入矩形與橢圓、設定精確尺寸，並將結果儲存。

接下來您可以探索：

* 將文字方塊或圖片加入同一個群組。  
* 使用 Word 的智慧圖形功能（透過 API）為分組圖形加入動畫。  
* 將分組圖形匯出為 PDF 或 SVG，以供網頁使用。

歡迎自行嘗試不同的圖形類型、尺寸與位置——分組能讓您在 Word 文件中對複雜版面擁有強大的控制力。

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索其他實作方式。

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}