---
category: general
date: 2026-09-21
description: 使用 Java 程式化建立 Word 文件。學習如何在 Word 中將圖形分組、插入矩形圖形、設定圖形大小，並將圖形加入 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Java 程式化建立 Word 文件：本指南示範如何在 Word 中將圖形分組、插入矩形圖形、設定圖形大小，以及將圖形加入 Word
  文件。
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: 以程式方式建立 Word 文件，於 Java 中將形狀分組
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: 以程式方式建立 Word 文件，於 Java 中將圖形分組
url: /zh-hant/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中以程式方式建立 Word 文件，將形狀分組

如果您需要 **以程式方式建立 Word 文件**，本指南將一步步帶您完成完整解決方案。您將會看到如何 **在 Word 中分組形狀**、插入矩形、設定尺寸，並加入其他形狀——全部使用 Java 以及 Aspose.Words for Java 函式庫。

本教學涵蓋從專案設定到儲存最終 .docx 檔案的每個步驟。完成後，您將能產生一個包含矩形與圖片且已包在同一個群組中的 Word 文件，方便一起移動或調整大小。無需事先熟悉 Aspose.Words API，但您應具備基本的 Java 開發環境。

## 前置條件

* Java Development Kit (JDK) 8 或更新版本  
* Maven 或 Gradle 用於相依管理  
* Aspose.Words for Java 23.9（或最新版本）— 此函式庫可免費評估使用  
* 一張圖片檔案（例如 `sample.jpg`），放置於已知目錄  

事先準備好上述項目，可確保程式碼在不需額外設定的情況下順利執行。

## 第一步：設定專案並匯入 Aspose.Words

建立一個 Maven 專案（或在現有的 `pom.xml` 中加入相依）：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

如果您偏好使用 Gradle，請在 `build.gradle` 中加入以下內容：

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

相依解決完成後，於 Java 原始檔中匯入所需的類別：

```java
import com.aspose.words.*;
import java.io.File;
```

## 第二步：以程式方式建立 Word 文件

在任何自動化情境中，第一件事就是實例化 `Document` 物件與 `DocumentBuilder`。Builder 可簡化文字、圖片與形狀的插入。

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

此時文件僅存在於記憶體中，接下來即可開始加入形狀。

## 第三步：插入矩形形狀 – 如何插入矩形形狀

矩形是使用 `ShapeType.RECTANGLE` 的基本 `Shape`。您可透過 `setWidth`、`setHeight` 設定尺寸，並以 `setTop`、`setLeft` 調整位置。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**為什麼重要：** 明確設定大小與位置（`set shape size word`）可保證矩形會出現在您預期的地方，而不受文件預設版面的影響。

## 第四步：插入圖片 – 為 Word 文件加入形狀

`DocumentBuilder` 能直接從檔案路徑插入圖片。插入後，您可以像處理其他形狀一樣重新定位圖片。

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

此時矩形與圖片皆為文件內的獨立形狀。

## 第五步：分組形狀 – 如何在 Word 中分組形狀

當您希望一次移動或調整多個形狀時，分組非常有用。Aspose.Words 提供 `GroupShape` 容器來實現此功能。

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

儲存群組後，Word 會將兩個子形狀視為一個邏輯物件。之後您只要選取該群組並拖曳，矩形與圖片會同步移動。

## 第六步：儲存文件

最後，將文件寫入磁碟。路徑必須對 Java 程序具有寫入權限。

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

執行 `main` 方法後會產生名為 **GroupShapeExample.docx** 的檔案。於 Microsoft Word 開啟，即可看到矩形與圖片已鎖定在同一個群組內。選取該群組即可同時移動兩個物件，證明分組成功。

## 預期輸出

* 位於您指定目錄下的 Word 檔案（`GroupShapeExample.docx`）  
* 檔案內，矩形（淡灰色填色）出現在左上角，圖片緊貼其下方  
* 兩個物件屬於同一個群組，拖曳其中一個即會同步移動另一個

## 常見變化與邊緣案例

| 情境 | 建議 |
|-----------|----------------|
| **不同的圖片格式** | Aspose.Words 支援 PNG、BMP、GIF 與 TIFF。請在 `insertImage` 中使用相對應的副檔名。 |
| **負值尺寸** | API 會拋出 `ArgumentException`。在呼叫 `setWidth` / `setHeight` 前務必先驗證寬度與高度。 |
| **大型文件** | 大量形狀分組可能會增加檔案大小。若效能是關鍵，考慮將形狀合併為單一圖片。 |
| **Word 版本相容性** | GroupShape 支援 Word 2007（`.docx`）及之後的版本。對於較舊的 `.doc` 檔，群組會被展平。 |
| **動態定位** | 若需自適應放置，可根據頁面尺寸計算（`doc.getFirstSection().getPageSetup().getPageWidth()`）。 |

**小技巧：** 建立群組後，您可以變更

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您對 API 的運用，並提供其他實作方式的範例。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}