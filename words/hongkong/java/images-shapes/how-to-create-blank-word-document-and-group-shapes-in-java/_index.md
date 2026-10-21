---
category: general
date: 2026-09-27
description: 在 Java 中建立空白 Word 文件，並使用 Aspose.Words 將圖形分組。學習設定圖形大小、設定圖形填色，並將子圖形加入分組。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: zh-hant
lastmod: 2026-09-27
og_description: 使用 Aspose.Words 在 Java 中建立空白 Word 文件。本教學示範如何在 Word 中將形狀分組、設定形狀大小、設定形狀填色，以及將子形狀加入群組。
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: 在 Java 中建立空白 Word 文件並將形狀分組 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何在 Java 中建立空白 Word 文件並群組圖形
url: /zh-hant/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中建立空白 Word 文件並將形狀分組

如果您需要以程式方式 **建立空白 Word 文件**，本指南將示範如何使用 Aspose.Words for Java 完成此操作。您還會學會 **在 Word 中分組形狀**、設定每個形狀的大小、套用填色，並 **將子項目加入群組**，使物件以單一單位運作。

透過程式碼操作 Word 檔案，可免除手動排版，並自動產生報告、合約或行銷手冊。完成本教學後，您將擁有一個可執行的 Java 程式，產生包含藍色矩形與圖片且已分組的 `.docx` 檔案。

## 前置條件

開始之前，請確保您已具備：

- 已安裝 Java 17（或任何較新版的 JDK）。
- Maven 或 Gradle 以管理相依性。
- Aspose.Words for Java 授權（免費評估版可用於測試）。
- 一個範例圖片檔（例如 `sample.jpg`），放在程式碼可參考的資料夾中。

> **小技巧：** 將圖片放在 `resources` 目錄，並使用 `ClassLoader.getResourceAsStream` 讀取，可避免硬編碼絕對路徑。

## 步驟 1：建立空白 Word 文件並加入 GroupShape

第一步是實例化一個新的 `Document` 物件，代表空的 Word 檔，接著插入 `GroupShape`。此群組將作為之後加入的所有形狀的容器。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*為什麼重要：* `GroupShape` 讓您一次移動、旋轉或格式化多個形狀，這對於圖表或浮水印等複雜版面配置相當關鍵。

## 步驟 2：插入矩形並 **設定形狀大小**

接著建立矩形、定義其尺寸，並將其加入群組。此範例示範 **設定形狀大小** 的操作。

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*說明：* `setWidth` 與 `setHeight` 控制形狀的精確大小，單位為點（1 point = 1/72 英吋）。依需求調整這些數值即可符合版面需求。

## 步驟 3：為矩形 **設定填色**

使用 `setFillColor` 將矩形背景設為藍色。您可以使用任何 `java.awt.Color` 常數，或自行建立 RGB 顏色。

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*為什麼好用：* 填色可在視覺上區分物件，特別是當您之後將文件匯出為 PDF 或列印時。

## 步驟 4：插入圖片並 **將子項目加入群組**

現在將圖片加入同一個 `GroupShape`。圖片透過 `DocumentBuilder.insertImage` 插入，之後使用 `group.appendChild(picture)` 加入群組，使其與矩形一起移動。

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*邊緣情況：* 若圖片路徑錯誤，Aspose.Words 會拋出 `FileNotFoundException`。請使用相對路徑或從 resources 載入圖片以避免此問題。

## 步驟 5：**儲存含有分組形狀的文件**

最後，將文件寫入磁碟。產生的檔案將包含已分組的矩形與圖片。

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### 預期輸出

- 在指定目錄中會出現名為 `GroupShape.docx` 的檔案。
- 使用 Microsoft Word 開啟時，會看到空白頁面上有藍色矩形與所選圖片，兩者被視為單一物件（可一起移動或調整大小）。

![建立空白 Word 文件並分組形狀](/images/grouped-shapes.png "建立空白 Word 文件並分組形狀")

*上圖示範了新建 Word 文件內最終的分組形狀效果。*

## 常見變化與額外技巧

| 情境 | 處理方式 |
|-----------|-----------------|
| **多張圖片** | 使用 `builder.insertImage` 插入每張圖片，然後對每張呼叫 `group.appendChild(picture)`。 |
| **不同形狀類型** | 建構 `Shape` 物件時使用 `ShapeType.OVAL`、`ShapeType.LINE` 等。 |
| **變更群組位置** | 在加入所有子項目後，使用 `group.setLeft(x)` 與 `group.setTop(y)` 移動整個群組。 |
| **匯出為 PDF** | 在分組後呼叫 `doc.save("output.pdf")`；PDF 會保留分組關係。 |
| **授權限制** | 使用評估版時會出現浮水印。安裝有效授權即可移除。 |

## 結論

您現在已掌握如何 **建立空白 Word 文件**、插入 **GroupShape**、**設定形狀大小**、**設定形狀填色**，以及 **將子項目加入群組**，全部透過 Aspose.Words for Java 完成。此模式讓您能建立可在 Word 中後續編輯或匯出至其他格式的複雜程式化版面。

接下來，您可以探索如何 **在 Word 中分組形狀** 並加入文字方塊、為形狀添加超連結，或自動產生多頁報告。原理相同——只要建立更多形狀、設定屬性，並將它們加入同一個群組即可。

祝編程愉快！


## 接下來該學什麼？

以下教學與本指南的技巧密切相關，提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，或在專案中探索其他實作方式。

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}