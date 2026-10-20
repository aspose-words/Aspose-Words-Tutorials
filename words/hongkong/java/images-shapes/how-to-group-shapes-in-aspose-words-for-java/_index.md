---
category: general
date: 2026-10-20
description: 如何在 Aspose.Words for Java 中對圖形進行分組 – 學習如何插入矩形圖形、將它們分組，並在單一指南中儲存文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: zh-hant
lastmod: 2026-10-20
og_description: 如何在 Aspose.Words for Java 中對形狀進行群組。此教學示範如何插入矩形形狀、將它們群組，並匯出結果。
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: 如何在 Aspose.Words for Java 中對形狀進行分組 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: 如何在 Aspose.Words for Java 中將形狀分組
url: /zh-hant/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words for Java 中對形狀進行分組

如果您需要在 Word 文件中 **如何對形狀分組**，使用 Aspose.Words for Java，本指南將展示完整的工作流程。您將學會如何 **插入矩形形狀**、新增第二個矩形、將兩個形狀分組，最後儲存檔案——全部以清晰、可執行的程式碼示範。

對形狀進行分組在您想要一次移動、旋轉或樣式化多個繪圖時非常有用。無論是建立報告範本、圖表或自訂傳單，掌握形狀分組都能節省時間並保持版面一致性。

在本教學中您將：

* 建立新的 `Document` 與 `DocumentBuilder`。
* **如何插入矩形** 形狀並設定精確尺寸。
* 將矩形放入 `GroupShape` 中。
* 儲存文件並驗證結果。

> **先決條件** – 必須在專案中加入 Aspose.Words for Java（v23.12 或更新版本）。Maven 使用者可在下方加入相應的相依性。

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## 您需要的項目

| 項目 | 原因 |
|------|------|
| Java 17+ | 現代語言功能與更佳效能 |
| Aspose.Words for Java | 提供 `DocumentBuilder`、`Shape` 與 `GroupShape` API |
| 開發環境 (IntelliJ IDEA、Eclipse、VS Code 等) | 編譯並執行範例 |
| 寫入資料夾的權限 | 文件將儲存至磁碟 |

---

## 如何插入矩形形狀

第一步是建立 `Document` 與 `DocumentBuilder`。`DocumentBuilder` 提供 `insertShape` 等方法，可將繪圖物件放入文件中。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **為什麼這很重要** – 使用 `insertShape` 是在 Aspose.Words 中 **如何插入矩形** 物件的標準方式。它會自動將形狀加入文件當前段落，無需自行處理低階 OpenXML。

---

## 調整矩形位置（可選）

如果第二個矩形需要相對於第一個矩形的自訂位置，您可以修改其 `left` 與 `top` 屬性。此步驟為可選，但在精確圖表排版時常常必須。

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **小技巧：** 所有測量單位皆為點 (1 pt ≈ 1/72 in)。若需 UI 計算的像素值，可使用 `convertPointsToPixels`。

---

## 如何對形狀分組

現在矩形已存在，您可以將它們放入 `GroupShape` 中。分組使兩個矩形如同單一物件般運作——移動、旋轉或格式化整個群組都會同時影響兩個形狀。

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **為什麼分組會生效** – `GroupShape` 繼承自 `Shape`，因此您可以像對待其他繪圖物件一樣對待群組。呼叫 `appendChild` 後，形狀會從原位置移除，成為群組的子項目。

---

## 儲存包含分組形狀的文件

最後，將文件寫入磁碟。檔案將只包含一個內含兩個矩形的 `GroupShape`。

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 預期結果

在 Microsoft Word 中開啟 `GroupShape.docx`：

* 您會看到兩個矩形（藍色與綠色）並排放置。
* 選取任一矩形即會選取整個群組——拖曳時兩者一起移動。
* 群組具有細紅色邊框，證明已套用 `GroupShape` 的屬性。

如果右鍵點擊群組並選擇 **Group → Ungroup**，矩形會恢復為獨立形狀，顯示分組操作是可逆的。

---

## 常見變化與邊緣案例

| 情況 | 處理方式 |
|-----------|------------------|
| **超過兩個形狀** | 插入每個形狀，然後將所有形狀附加到同一個 `GroupShape`。 |
| **不同形狀類型**（例如橢圓、圖片） | 在附加之前使用 `builder.insertShape(ShapeType.ELLIPSE, …)` 或 `builder.insertImage(...)`。 |
| **縮放群組** | 呼叫 `group.setWidth(newWidth)` 或 `group.setHeight(newHeight)`；子形狀會按比例縮放。 |
| **旋轉群組** | `group.setRotationAngle(45);` 會將整個集合繞其中心旋轉。 |
| **保留原始位置** | 在分組前儲存每個形狀的 `left`/`top`，如有需要在解除分組後還原。 |

---

## 完整、可執行的範例

以下是完整的 Java 類別，您可以直接複製貼上至 IDE 中。程式碼包含所有匯入、錯誤處理與說明註解，便於閱讀。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

執行程式後，開啟產生的 `GroupShape.docx`，即可看到如說明中所示的分組矩形。

---

## 結論

您現在已了解 **如何在 Aspose.Words for Java 中對形狀分組**，從建立文件、插入矩形形狀、調整位置，到最終使用 `GroupShape` 進行分組。此技巧讓您能將多個繪圖視為單一實體，簡化版面調整並提升視覺一致性。

**下一步**

* 探索 **如何插入矩形** 形狀的不同填充樣式或邊框。
* 結合 **插入矩形形狀** 與文字方塊，製作帶標籤的圖表。
* 嘗試旋轉或縮放群組，以產生更複雜的圖形。

歡迎依需求調整程式碼，以支援其他形狀類型、更大的群組或動態文件產生情境。祝開發順利！

## 您接下來應該學習什麼？

以下教學與本指南所示技術緊密相關，提供完整的程式碼範例與逐步說明，協助您掌握更多 API 功能並在專案中探索其他實作方式。

- [在 Java 中插入矩形形狀 – 分組與定位](./words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [在 Java 中插入群組形狀 – 完整指南](./words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [在 Aspose.Words 中設定形狀陰影 – 完整指南](./words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}