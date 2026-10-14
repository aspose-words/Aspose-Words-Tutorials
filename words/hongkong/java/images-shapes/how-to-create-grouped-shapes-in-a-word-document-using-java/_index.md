---
category: general
date: 2026-10-13
description: 學習如何在 Word 中使用 Java 建立群組形狀。本指南將示範如何插入群組形狀、向群組加入線條，以及在整個 Word 文件中群組多個形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: zh-hant
lastmod: 2026-10-13
og_description: 使用 Java 在 Word 中建立群組形狀。跟隨本完整教學，學習插入群組形狀、向群組加入線條，以及在 Word 文件中對多個形狀進行群組。
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: 使用 Java 在 Word 中建立群組形狀 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何使用 Java 在 Word 文件中建立群組形狀
url: /zh-hant/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Java 建立群組形狀

如果您需要在 Java 中 **create grouped shapes**（建立群組形狀）於 Microsoft Word 檔案，本教學將逐步說明整個流程。您將會看到如何 **insert group shape**（插入群組形狀），在同一個容器內放置矩形與直線，最後將文件儲存為包含群組圖形的檔案。

將形狀群組化可讓您輕鬆地一次移動、調整大小或設定樣式於多個繪圖物件，彷彿是一個單位——非常適合用於圖表、流程圖或自訂頁面裝飾。完成本指南後，您將能夠 **add line to group**、**group multiple shapes word** 文件，並將相同技巧重複使用於任意數量的形狀。

## 前置條件

- 在開發機器上已安裝 Java 17 或更新版本。  
- Aspose.Words for Java 授權（或免費評估版）。  
- 一個 Maven 或 Gradle 專案，可於其中加入 Aspose.Words 相依性：

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

不需要其他額外的函式庫。

## 步驟 1：插入群組形狀容器

第一步是 **insert group shape** 到文件中。此容器將容納之後的所有形狀。

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` 會建立一個類型為 `GROUPSHAPE` 的空 `Shape` 物件。可將其視為可容納其他繪圖物件的透明畫布。

## 步驟 2：將矩形加入群組

矩形通常作為一組形狀的視覺背景。

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

將 `Left` 與 `Top` 設為 `0` 可將矩形置於群組的左上角。您可以調整這些數值，以在群組內偏移形狀的位置。

## 步驟 3：**Add line to group** – 建立直線形狀

現在我們 **add line to group**。此直線會顯示在矩形之下。

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

`Top` 屬性會將直線向下移動 60 點，位於矩形下方，形成簡單的堆疊布局。如需水平偏移，也可以設定 `Left`。

## 步驟 4：儲存含有群組形狀的文件

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

當您在 Microsoft Word 中開啟 `GroupShapeDemo.docx` 時，會看到一個包含矩形與直線的單一群組。選取該群組即可同時移動兩個形狀，證明您已成功 **group multiple shapes word**。

## 完整、可執行範例

以下為完整程式碼，包含所有匯入與錯誤處理。將其複製到您的 IDE 中，將 `YOUR_DIRECTORY` 替換為實際的資料夾路徑，然後執行。

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### 預期輸出

- 目標資料夾中會產生名為 `GroupShapeDemo.docx` 的檔案。  
- 在 Word 中開啟該檔案會顯示一個單一的群組物件，內含上方的矩形與下方的直線。  
- 拖曳該群組會同時移動兩個形狀，證實您已成功 **created grouped shapes**。

## 提示與常見陷阱

- **Pro tip:** 若需在群組內旋轉或設定個別形狀的樣式，請在將其加入群組前呼叫相應的 setter（`setRotation`、`getFill().setForeColor` 等）。群組會保留這些視覺屬性。  
- **Watch out for:** 若忘記為直線設定 `Top` 屬性，可能會與矩形重疊，使群組看起來雜亂。  
- **Edge case:** 當加入超過兩個形狀時，請記得每個子形狀的座標皆相對於群組的原點 (0,0)。請依此規劃布局。  
- **Performance note:** 將大量形狀（數百個）群組化可能會稍微增加檔案大小，但可簡化之後在 Word 中的編輯。

## 如何以程式方式 **group multiple shapes word** 文件

上述模式——建立群組容器、設定每個子形狀，然後加入——適用於任意數量的形狀：圓形、圖片、文字方塊等。只要在呼叫 `doc.save()` 前重複「建立形狀 → 設定屬性 → 加入」的步驟即可。

若您需要在群組已包含其他形狀後 **add line to group**，可以透過以下方式取得現有的群組：

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

此示例說明您可在文件生命週期的任何階段修改群組。

## 結論

現在您已了解如何使用 Java 與 Aspose.Words 在 Word 文件中 **create grouped shapes**。透過 **inserting group shape**、**adding line to group** 與 **group multiple shapes word**，您可以建立作為單一物件運作的複雜圖形——非常適合用於圖表、範本與自動化報告產生。

接下來，探索以下相關主題：

- **Applying styles to grouped shapes** – 了解如何一次為所有子形狀設定填色、邊框與效果。  
- **Exporting grouped shapes to PDF** – 了解在將文件轉換為 PDF 時，群組如何保持。  
- **Animating shapes with VBA** – 結合 Java 產生的群組與 Word 巨集，製作互動式文件。

歡迎嘗試不同類型、尺寸與位置的形狀。群組化讓您能將多個物件視為一體，簡化程式碼與使用者互動。祝開發愉快！

## 接下來您應該學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}