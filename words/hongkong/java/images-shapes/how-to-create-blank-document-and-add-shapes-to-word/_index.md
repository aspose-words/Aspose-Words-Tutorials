---
category: general
date: 2026-09-18
description: 使用 Aspose.Words 建立空白文件並插入形狀到 Word – 了解如何加入三角形形狀及其他。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: zh-hant
lastmod: 2026-09-18
og_description: 使用 Aspose.Words 在 Word 中建立空白文件，並學習如何插入三角形形狀、群組形狀及其他圖形。跟隨本完整指南。
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: 建立空白文件並在 Word 中加入形狀 – 步驟教學
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: 如何在 Word 中建立空白文件並加入圖形
url: /zh-hant/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何建立空白文件並在 Word 中加入圖形

如果您需要 **建立空白文件**，然後以圖形豐富內容，本教學將一步步示範。 我們會從頭建立 Word 檔案，並 **在 Word 中加入圖形**，包括 **如何插入三角形**，使用 Aspose.Words for Java。

完成本教學後，您將得到一個可直接使用的 *.docx* 檔案，內含一個包含三角形的群組圖形。 步驟涵蓋從專案設定到儲存最終 **create word document** 的全部流程。 除了 Aspose.Words，無需其他外部工具。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Java 17 或更新版本  
* Maven 或 Gradle 以管理相依性  
* Aspose.Words for Java 授權（免費評估版即可執行本示範）  

若您使用其他建置系統，請自行調整相依性語法。 此程式碼可在任何支援 Java 的平台上執行。

## 使用 Aspose.Words 建立空白文件

第一步是 **建立空白文件**（於記憶體中）。 Aspose.Words 提供的 `Document` 類別代表一個尚未有任何內容的 Word 檔案。

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` 建構子會建立一個空的 *.docx* 結構，之後您可以自行加入段落、表格或圖形。 由於文件是空白的，您對每個新增的元素都有完整的控制權。

## 在 Word 中加入圖形 – 插入群組圖形

群組圖形允許您將多個圖形視為單一單元。 當您希望一次移動或調整多個圖形時，這非常有用。

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` 是加入內容的主要 API。 `insertGroupShape` 會建立一個 300 × 300 點（約 4 × 4 吋）的容器。 呼叫此方法後，游標會定位在群組 **內部**，可供後續加入圖形。

### 為什麼要使用群組圖形？

將相關圖形分組可保持對齊，且更容易套用統一的格式。 若日後要移動三角形，只要搬移整個群組即可，版面不會被破壞。

## 如何在群組內插入三角形圖形

接下來說明 **如何插入三角形** 圖形。 三角形是內建的 `ShapeType` 之一。

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

`moveTo` 呼叫確保 builder 的插入點位於群組的第一個段落。 接著 `insertShape` 會加入一個 60 × 60 點的三角形。 由於游標位於群組內，該三角形會成為群組圖形的子項目。

**插入三角形圖形** 小技巧：

* 大小以點為單位；72 點等於一吋。 請依版面需求調整尺寸。  
* 若需不同方向，可使用 `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` 來設定圖形在群組內的對齊方式。  
* 除非您使用 `shape.getFillColor()` 或 `shape.getStrokeColor()` 另行設定，否則三角形會繼承群組的填色與線條樣式。

## 儲存文件 – create word document

完成圖形建構後，即可儲存檔案。 此步驟完成 **create word document** 的操作。

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` 會將記憶體中的表示寫入磁碟，產生標準的 Word 文件。 您可以在 Microsoft Word、LibreOffice 或任何支援 OOXML 格式的檢視器中開啟 `ExtendedGroup.docx`。 該檔案會顯示一個包含三角形的群組圖形，與程式碼所建構的結果完全相同。

## 完整可執行範例

將所有片段整合起來，以下是完整程式碼，您可以直接複製、編譯並執行：

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### 預期結果

開啟 `ExtendedGroup.docx` 後，您會看到頁面中央有一個單一的群組圖形。 在該群組內，預設位置會出現一個小三角形。 您可以將三角形與群組一起選取、移動，證明 **add shapes to word** 已成功執行。

## 常見問題與邊緣情況

| Question | Answer |
|----------|--------|
| *Can I add more than one shape inside the group?* | Yes. After inserting the triangle, keep the cursor inside the group and call `builder.insertShape` again with a different `ShapeType`. |
| *What if I need the triangle to be red?* | Retrieve the `Shape` returned by `insertShape` and call `shape.getFillColor().setColor(Color.RED)`. |
| *Does this work with older .doc files?* | Aspose.Words saves in the format you specify. Use `doc.save("file.doc", SaveFormat.DOC)` to create a legacy Word document. |
| *How do I change the group’s border?* | Use `group.getStrokeColor().setColor(Color.BLUE)` and `group.setLineWeight(2.0)` to customize the outline. |
| *Is there a way to rotate the triangle?* | Call `shape.getRotation()` to set an angle in degrees. |

## 專業提示

* **重複使用 builder** – 為每個圖形都建立新的 `DocumentBuilder` 會增加開銷。 建議在同一文件中只保留一個 builder。  
* **單位換算** – 若您使用公釐，可將其換算成點（`points = mm * 2.83465`）。  
* **效能** – 對於大型文件，請在全部圖形加入完畢後只呼叫一次 `doc.updatePageLayout()`。

## 結論

現在您已掌握 **建立空白文件**、**在 Word 中加入圖形**，以及使用 Aspose.Words for Java **插入三角形** 圖形的完整流程。 完整範例示範了從空白檔案到儲存 **create word document**，且內含一個群組三角形的全程操作。

接下來，您可以探索其他 `ShapeType`、套用自訂樣式，或結合多個群組以建立複雜圖表。 嘗試不同的尺寸、顏色與位置，精通 Java 中的 Word 自動化。

--- 

*準備好自動化您的下一份報告了嗎？立即複製範例、調整尺寸，並將程式碼整合到您自己的應用程式中吧。*


## 接下來該學什麼？

以下教學與本指南的技巧密切相關，能進一步延伸您的應用：

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}