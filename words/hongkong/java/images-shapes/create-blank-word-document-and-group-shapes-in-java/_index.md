---
category: general
date: 2026-08-23
description: 使用 Aspose.Words for Java 建立空白 Word 文件，學習如何將圖形分組、為矩形圖形上色，並在數分鐘內將文件儲存為
  docx。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: zh-hant
lastmod: 2026-08-23
og_description: 使用 Aspose.Words for Java 建立空白 Word 文件，然後了解如何將形狀分組、為矩形形狀著色，並有效地將文件儲存為
  docx。
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: 在 Java 中建立空白 Word 文件並將圖形分組 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 在 Java 中建立空白 Word 文件並將圖形分組
url: /zh-hant/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並在 Java 中群組圖形

如果您需要以程式方式 **建立空白 Word 文件**，Aspose.Words for Java 讓這件事變得相當簡單。本教學將一步步示範如何 **建立空白 Word 文件**、在 Word 中 **插入群組圖形**、套用 **彩色矩形圖形**，最後 **將文件另存為 docx**。完成後，您將擁有一段可直接放入任何 Java 專案的可重用程式碼片段。

您將學會：

* Aspose.Words 所需的 Maven/Gradle 相依性。
* 如何實例化空白文件與 `DocumentBuilder`。
* 在 `GroupShape` 中 **如何群組圖形** 的完整步驟。
* 如何為矩形圖形設定填色。
* **將文件另存為 docx** 的最佳實踐以及輸出檔案的存放位置。

不需要事先了解 Aspose.Words，但您應該熟悉基本的 Java 開發，且已安裝 JDK 8 或更新版本。

---

## 前置條件

| 前置條件 | 版本 / 詳細資訊 |
|----------|-------------------|
| Java Development Kit | 8 或以上 |
| 建置工具 | Maven 3+ 或 Gradle 6+ |
| Aspose.Words for Java | 23.12 或更新（撰寫本文時的最新版本） |
| IDE（可選） | IntelliJ IDEA、Eclipse、VS Code，或任何支援 Java 的編輯器 |

---

## 第一步：將 Aspose.Words 加入您的專案

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **專業小技巧：** 若您使用公司代理伺服器，請依官方文件說明，將 Maven/Gradle 設定為從 Aspose 套件庫取得套件。

---

## 第二步：使用 Builder **建立空白 Word 文件**

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 建構子會在記憶體中建立一個空的 `.docx` 容器。`DocumentBuilder` 提供流暢的 API 讓您加入內容，包括圖形。

---

## 第三步：插入 **Word 中的群組圖形** 容器

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` 如同一個小型畫布。所有加入其中的圖形會一起移動，這正是 **如何群組圖形** 以確保版面一致性的做法。

---

## 第四步：加入第一個 **彩色矩形圖形**（紅色）

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

`ShapeType.RECTANGLE` 常數會建立簡單的矩形。透過 `getFill().setForeColor(...)` 您即可控制 **彩色矩形圖形**。您可以將 `java.awt.Color.RED` 替換為任何 `java.awt.Color` 常數或自訂的 RGB 值。

---

## 第五步：加入第二個 **彩色矩形圖形**（綠色）並設定位置

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

使用 `setLeft`（或 `setTop`）可將圖形相對於 **Word 中的群組圖形** 容器左上角移動。此步驟示範了 **如何群組圖形** 之精確定位。

---

## 第六步：**將文件另存為 docx** 並驗證結果

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` 方法會自動依檔案副檔名寫入 `.docx` 檔案。如果您需要其他格式（例如 PDF），只要傳入相對應的 `SaveFormat` 列舉即可。

> **小提示：** 確認目標目錄（本例中的 `output/`）已存在，或使用 `new File("output").mkdirs();` 於程式中自行建立。

---

## 完整原始碼，方便直接複製貼上

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**預期輸出：** 在 Microsoft Word 開啟 `GroupShapeDemo.docx` 後，會看到單一頁面上有兩個彩色矩形（左側紅色、右側綠色），選取群組時兩個矩形會一起移動。

---

## 常見問題與特殊情況處理

| 問題 | 解答 |
|------|------|
| *我可以在同一個群組中加入超過兩個圖形嗎？* | 可以。對每個額外的圖形呼叫 `groupShape.appendChild(yourShape)`。群組會自動依最遠的邊界調整大小，或您也可以手動設定寬高。 |
| *如果需要不同的圖形類型（例如橢圓）該怎麼做？* | 將 `ShapeType.RECTANGLE` 改為 `ShapeType.ELLIPSE`。填色邏輯相同。 |
| *是否需要自行釋放 `Document` 物件？* | Aspose.Words 會在內部管理本機資源。JVM 結束時會釋放資源。若是長時間執行的應用程式，使用 **Aspose.Words for Java (Native)** 版時可呼叫 `doc.dispose();`。 |
| *如何變更 Z‑order，使其中一個矩形顯示在上層？* | 使用 `groupShape.insertAfter(shape, referenceShape);` 或 `groupShape.insertBefore(shape, referenceShape);` 於群組內重新排序子項目。 |
| *我可以跨不同段落群組圖形嗎？* | 不行。`GroupShape` 必須位於同一段落或圖形容器內。若需跨段落群組，請在每個段落分別建立群組。 |

---

## 結論

現在您已掌握如何使用 Aspose.Words for Java **建立空白 Word 文件**、在 Word 中 **群組圖形**、套用 **彩色矩形圖形** 的樣式，並 **將文件另存為 docx**。此模式可擴展至更複雜的版面配置——只要加入更多圖形、調整偏移量，甚至在群組內加入文字、圖片或超連結。

**下一步** 您可以探索：

* 使用 **Word 中的群組圖形** 來建立流程圖或 UI 原型。
* 結合 **將文件另存為 docx** 與 PDF 轉換（`doc.save("out.pdf")`）。
* 為 **彩色矩形圖形** 套用漸層或圖案，以提升視覺設計。
* 將群組圖形與表格或圖表結合，製作進階報表文件。

隨意調整尺寸、顏色或圖形類型，以符合您專案的品牌需求。祝開發順利！

## 接下來您可以學習什麼？

以下教學與本指南的技巧密切相關，提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索其他實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}