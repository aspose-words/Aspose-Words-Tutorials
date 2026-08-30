---
category: general
date: 2026-08-07
description: 使用 Aspose.Words 在 Java 中建立空白 Word 文件，並加入群組形狀。了解如何將形狀群組、設定形狀大小，以及將形狀加入
  Word。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: zh-hant
lastmod: 2026-08-07
og_description: 在 Java 中建立帶有群組形狀的空白 Word 文件。請依照本指南設定形狀大小、將形狀加入 Word，並掌握如何群組形狀。
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: 使用群組形狀建立空白 Word 文件 – Java 教學
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: 在 Java 中建立含有群組圖形的空白 Word 文件
url: /zh-hant/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中建立空白 Word 文件並使用群組形狀

如果您需要 **create blank Word document**（建立空白 Word 文件），且該文件包含多個形狀作為單一單位排列，本教學將完整說明如何操作。您將看到一個完整且可執行的範例，示範 **how to group shape**（如何群組形狀）物件、調整其尺寸，並使用 Aspose.Words for Java **add shapes to Word**（將形狀加入 Word）。

本指南會逐步說明每個步驟——從專案設定到儲存最終的 .docx 檔案——讓您可以直接將程式碼複製到自己的應用程式中。無需任何外部參考，且此解決方案適用於 Aspose.Words 23.9 或更新版本。

## 前置條件

* Java 17（或任何受支援的 JDK）
* Maven 或 Gradle 用於相依性管理
* Aspose.Words for Java 授權（或暫時的評估金鑰）
* 放置於已知目錄的範例圖片檔案（例如 `sample.jpg`）

如果缺少上述任何項目，請先安裝；本教學的其餘部分假設環境已就緒。

## 步驟 1：將 Aspose.Words 加入您的專案

將 Aspose.Words 相依性加入您的 `pom.xml`（Maven）或 `build.gradle`（Gradle）。此函式庫提供稍後會使用的 `Document`、`DocumentBuilder`、`GroupShape` 與 `Shape` 類別。

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**為何重要：** 若未加入此函式庫，Word 處理相關的 API 將無法使用，您也無法以程式方式 **create blank Word document**。

## 步驟 2：建立空白 Word 文件

第一個具體動作是實例化 `Document` 物件，它在記憶體中代表一個 **blank Word document**（空白 Word 文件）。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* 會以預設設定（A4 頁面、預設邊距）建立一個 **blank Word document**。隨附的 `DocumentBuilder` 允許您在目前游標位置插入內容。

## 步驟 3：插入群組形狀（how to group shape）

*群組形狀*（group shape）充當其他形狀的容器。在此步驟中，您將學習 **how to group shape** 物件，使它們一起移動。

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

`insertGroupShape` 方法會將容器放置於 builder 的游標位置。當您想將多個圖形視為單一實體時，群組是必須的——這正是 **group shapes word** 功能的核心。

## 步驟 4：建立矩形並設定其尺寸

現在將矩形加入群組。此範例示範 **set shape size**，這對精確佈局是必要的。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*為何要設定尺寸？* 明確呼叫 `setWidth` 與 `setHeight` 可確保矩形依預期顯示，無論文件的預設形狀樣式如何。

## 步驟 5：插入圖片並加入群組

加入圖片展示了另一個常見的 **add shapes to word** 用例。圖片會成為同一群組的一部分，與矩形一起移動。

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

若圖片檔案遺失，Aspose.Words 會拋出例外。實用技巧是事先驗證路徑：

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## 步驟 6：儲存包含群組形狀的文件

最後，將 **blank Word document**（現在已包含群組形狀）寫入磁碟。

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

當您在 Microsoft Word 中開啟 `GroupShapeDemo.docx` 時，會看到一個包含矩形與圖片的單一群組物件。選取群組的任何部分都會移動整個容器，證實形狀已正確 **grouped**。

### 預期輸出

* 在指定目錄下產生名為 `GroupShapeDemo.docx` 的檔案。
* 開啟檔案會顯示一個 300 × 200 點的容器，內含：
  * 一個位於 (20, 20) 的 100 × 50 點矩形。
  * 一張位於 (150, 30) 的圖片，亦在同一容器內。

## 邊緣情況與變體

| Situation | How to handle it |
|-----------|-----------------|
| **不同的頁面大小** | 在插入群組之前，呼叫 `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);`。 |
| **多個群組** | 使用新的 `GroupShape` 實例重複步驟 3‑5；每個群組皆可獨立定位。 |
| **旋轉形狀** | 使用 `shape.setRotationAngle(45.0);` 於將矩形或圖片加入群組前旋轉它們。 |
| **非圖片形狀** | 建立 `Shape` 物件，類型為 `ShapeType.ELLIPSE`、`ShapeType.LINE` 等，並像矩形一樣加入群組。 |
| **大型圖片** | 使用 `picture.setWidth(80.0); picture.setHeight(60.0);` 縮放圖片，以保持群組在原始範圍內。 |

## 實務技巧分享

* **Pro tip（專業提示）：** 若希望群組固定於頁面而非游標，請將群組的 `RelativeHorizontalPosition` 與 `RelativeVerticalPosition` 設為 `RelativeHorizontalPosition.PAGE` 與 `RelativeVerticalPosition.PAGE`。
* **Watch out for（注意）：** 若加入的形狀超出群組尺寸，該形狀在 Word 中會被裁切。請使用 `group.setWidth()` 與 `group.setHeight()` 來相應調整群組大小。
* **Performance note（效能說明）：** 若在迴圈中產生大量文件，請重複使用同一個 `DocumentBuilder` 實例，並呼叫 `doc.clone()` 以減少物件建立的開銷。

## 結論

現在您已了解如何使用 Aspose.Words for Java **create blank Word document**，其中包含一組群組形狀。本教學涵蓋完整工作流程：設定函式庫、建立文件、插入群組、**set shape size**、**add shapes to word**，以及儲存結果。

接下來，您可以探索更進階的功能，例如群組圖表、為單一形狀套用樣式，或將文件匯出為 PDF。這些主題皆建立在本指南所示的相同原則之上。

---

## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [建立 Word 文件 Java – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Aspose.Words for .NET 在 Word 文件中插入形狀](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}