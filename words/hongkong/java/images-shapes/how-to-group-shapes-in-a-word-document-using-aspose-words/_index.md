---
category: general
date: 2026-08-20
description: 了解如何在 Java 中使用 Aspose.Words 將形狀分組、設定形狀大小、將圖片插入文件、將圖片加入群組，以及建立矩形形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: zh-hant
lastmod: 2026-08-20
og_description: 如何使用 Aspose.Words 在 Word 文件中對形狀進行分組。請按照此一步一步的 Java 教程設定形狀大小、將圖片插入文件、將圖片加入分組，並建立矩形形狀。
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: 使用 Aspose.Words 在 Word 文件中分組圖形 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: 如何使用 Aspose.Words 在 Word 文件中將形狀分組
url: /zh-hant/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Aspose.Words 將形狀分組

如果您需要在 Word 檔案中 **how to group shapes**，本教學展示完整的 Java 解決方案。您將看到如何 **set shape size**、**insert image into document**、**add picture to group**，以及 **create rectangle shape**——全部提供清晰說明與可執行的程式碼範例。

將形狀分組可簡化版面配置管理，讓您能一次移動或旋轉多個物件，並保持文件整潔。以下步驟將建立一個包含矩形與圖片的群組，然後將該群組放置於頁面上。

## 前置條件

* 已安裝 Java 17 或更新版本。
* 已將 Aspose.Words for Java（版本 23.9 或以上）加入專案的 classpath。
* 在 `YOUR_DIRECTORY/sample.jpg` 位置有一個 JPEG 範例圖（將 `YOUR_DIRECTORY` 替換為實際路徑）。

您可以透過 Maven 加入 Aspose.Words：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## 使用 Aspose.Words 分組形狀的方法

以下各節將逐步說明完成 **how to group shapes** 所需的每個操作。主要的 H2 標題包含主要關鍵字，以符合 SEO 規則。

### 步驟 1：建立新文件與 `DocumentBuilder`

`Document` 代表 Word 檔案，而 `DocumentBuilder` 提供方便的插入內容方法。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*為什麼重要*：從全新的 `Document` 開始，可確保您建立的群組不會干擾現有元素。

### 步驟 2：插入可容納多個子形狀的群組形狀

群組形狀類似容器。其尺寸定義所有子形狀的邊界框。

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*提示*：寬度 (`300`) 與高度 (`200`) 的單位為點（1 pt = 1/72 英吋）。請依您欲加入的形狀大小調整此數值。

### 步驟 3：建立矩形形狀、設定其大小，並加入群組

在需要精確版面控制時，設定形狀的確切大小是必要的。

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*為什麼要設定形狀大小*：`setWidth` 與 `setHeight` 方法對應 **set shape size** 次要關鍵字，讓您對矩形外觀擁有像素級的精確控制。

### 步驟 4：插入圖片，然後將圖片形狀加入同一群組

插入圖片是 **insert image into document** 需求的核心。回傳的 `Shape` 為圖片形狀，可像其他形狀一樣被加入群組。

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*專業提示*：若需保留原始長寬比，只設定一個維度（`setWidth` 或 `setHeight`）。Aspose.Words 會自動縮放另一個維度。

### 步驟 5：在頁面上定位整個群組

加入所有子形狀後，您可以移動、旋轉或隱藏整個群組。定位間接使用 **add picture to group** 概念，因為群組已包含圖片。

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*說明*：`setLeft` 與 `setTop` 使群組相對於頁面邊距定位。旋轉群組可示範所有子形狀繼承此變換。

### 步驟 6：儲存文件

最後，將檔案寫入磁碟。您可以在 Word 中開啟產生的 `.docx` 以驗證分組效果。

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

執行程式會產生 **GroupShapesDemo.docx**，其中包含已合併的矩形與圖片。於 Word 中選取任一形狀時，另一個形狀也會被同時選取，證明您已成功學會 **how to group shapes**。

---

## 預期輸出

當您在 Microsoft Word 中開啟 *GroupShapesDemo.docx* 時：

* 群組左側會出現一個（金色填充）的矩形。
* 您提供的圖片會出現在矩形的右側。
* 拖曳群組時，兩個物件會一起移動。
* 群組位置距左邊距 50 pt、上邊距 100 pt，並旋轉 15°。

若圖片未顯示，請再次確認 `insertImage` 中的檔案路徑。當找不到檔案時，Aspose.Words 會拋出 `IOException`。

---

## 常見問題與邊緣案例處理

| 問題 | 答案 |
|------|------|
| **我可以加入超過兩個形狀嗎？** | 可以。對每個額外的形狀呼叫 `groupShape.appendChild(otherShape)`。 |
| **如果我需要矩形的透明背景怎麼辦？** | 使用 `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **舊版 Word 格式（例如 `.doc`）是否支援分組？** | 分組在 `.docx` 與 `.doc` 中皆可使用，但某些舊版檢視器可能會忽略群組的中繼資料。請以 `.docx` 儲存以獲得完整相容性。 |
| **我之後要如何取消分組？** | 透過 `groupShape.getChildNodes(NodeType.ANY, true)` 取得子節點，將它們移至文件主體，然後刪除群組。 |
| **我可以跨不同節分組形狀嗎？** | 不能。`GroupShape` 必須位於單一 `Story`（通常是文件主體）內。 |

## 強化形狀處理的專業技巧

* **盡量少用絕對定位**——相對定位（`builder.moveToDocumentEnd()`）通常能產生更具彈性的版面配置。
* **快取 `DocumentBuilder`**——為每個操作建立新 builder 會在大型文件上降低效能。
* **設定 `PictureFillMode`** 以在形狀內拉伸或平鋪圖片時使用：`pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **在插入前驗證圖片尺寸**，以避免意外的縮放影響群組的邊界框。

## 後續步驟

既然您已了解 **how to group shapes**，接下來可以探索：

* **Insert image into document** 搭配進階選項，如裁剪 (`pictureShape.setCropTop(...)`)。
* **Set shape size** 可根據頁面尺寸動態設定（`doc.getFirstSection().getPageSetup().getPageWidth()`）。
* **Add picture to group** 可與文字方塊結合，製作帶說明的圖形。
* **Create rectangle shape** 可使用圓角（`rectangleShape.setCornerRadius(5);`）。

這些主題基於相同的 API，協助您建立複雜且程式化的 Word 報告。

## 結論

在本教學中，您學會了使用 Aspose.Words for Java 在 Word 文件中 **how to group shapes**。透過六個步驟——建立文件、插入群組、**create rectangle shape**、**set shape size**、**insert image into document**、**add picture to group**，以及定位群組，您現在擁有可重複使用的複雜版面模式。歡迎自行嘗試加入更多子形狀、不同的旋轉角度，或條件式分組邏輯，以符合您的應用需求。

祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，建立在本篇示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [建立 Word 文件（Java） – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Aspose.Words for Java 中使用文件形狀](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}