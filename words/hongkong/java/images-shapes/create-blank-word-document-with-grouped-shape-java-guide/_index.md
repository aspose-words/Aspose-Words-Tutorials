---
category: general
date: 2026-07-20
description: 使用 Aspose.Words 在 Java 中建立空白 Word 文件。了解如何建立群組、插入矩形形狀，並在形狀中嵌入圖片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: zh-hant
lastmod: 2026-07-20
og_description: 使用 Aspose.Words 在 Java 中建立空白 Word 文件。本指南示範如何建立群組、插入矩形圖形，並在圖形中嵌入圖片，以製作動態
  Word 檔案。
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: 建立帶有群組圖形的空白 Word 文件 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: 建立帶有群組圖形的空白 Word 文件 – Java 指南
url: /zh-hant/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並加入群組圖形 – Java 指南

有沒有想過如何 **建立空白 Word 文件**，同時已經包含一個精美的群組圖形？也許你正在製作報告範本，或是需要一個放置商標與說明文字的佔位區。無論哪種情況，這都是常見的需求：先從空檔開始，接著加入群組、在裡面放入矩形，最後嵌入圖片——全部以程式方式完成。

在本教學中，我們將逐步說明一個完整、可直接執行的 Java 範例，正好完成上述工作。你將學會 **how to create group**、**insert rectangle shape**，以及 **add image word document**，全部放在同一個群組內。完成後，你將得到一個看起來如同精緻範本的 Word 檔案，隨時可進一步自訂。

> **你將獲得：** 完整可執行的 Java 類別、逐步說明、檔案路徑處理技巧，以及預期輸出結果的預覽。無需外部文件——所有資訊皆在此處。

---

## 建立空白 Word 文件 – 步驟概覽

我們首先需要的是一個徹底空白的 Word 檔案。Aspose.Words 讓這件事變得非常簡單：只要以預設建構子建立 `Document` 類別的實例，即可得到一張乾淨的畫布，等同於在 Word 中點選 **New → Blank document**。

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **為什麼要從空白文件開始？**  
> 空白文件可確保沒有隱藏的樣式或章節會干擾之後加入的圖形，同時也能保持檔案大小最小，對於批次產生大量文件時相當方便。

---

## 如何建立群組並加入圖形

**群組圖形** 本質上是一個容器，可容納多個子圖形——可視為繪圖物件的資料夾。透過群組化，你可以一次指令就移動、調整大小或旋轉整個集合。

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

`insertGroupShape` 方法會回傳一個 `GroupShape` 物件，我們將以它作為矩形與圖片的父層。尺寸以點 (point) 為單位 (1 point = 1/72 吋)，因此 200 點大約等於 2.78 × 2.78 吋的方框。

> **小技巧：** 若需要群組為透明，請在建立後設定 `group.setFillColor(Color.getWhite());`。

現在群組已建立，我們必須告訴 DocumentBuilder 下一個圖形要放在哪裡。Builder 的游標必須定位在群組的第一個段落內。

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## 在群組內插入矩形圖形

矩形常被用作文字佔位或視覺提示。將它作為群組的 **第一個子圖形** 插入，可確保它位於之後所有圖片的後方。

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

矩形會繼承群組的座標系統，因此其 100 × 50 點的大小預設會置中。你可以進一步設定樣式——加入邊框、變更填色，或套用陰影——只要操作回傳的 `Shape` 物件即可。

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## 加入圖片至 Word 文件 – 在圖形中嵌入圖片

現在進入有趣的部分：**在圖形中嵌入圖片**。我們會將 JPEG 圖片作為同一個群組的第二個子圖形插入。由於游標仍在群組內，圖片會自動成為子節點。

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

若找不到圖片檔案，Aspose.Words 會拋出 `FileNotFoundException`。為避免此情況，請將 `sample.jpg` 放在專案的工作目錄，或使用絕對路徑。

> **如果需要其他圖片格式該怎麼辦？**  
> Aspose.Words 支援 PNG、BMP、GIF、TIFF，甚至 SVG。只要更改檔案副檔名，程式庫會自動處理轉換。

---

## 儲存文件並檢視結果

最後，我們將記憶體中的文件寫入磁碟。產生的 `.docx` 會包含一頁，內有一個群組圖形，裡面同時包含矩形與圖片。

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

當你在 Microsoft Word 中開啟 `output.docx` 時，應該會在左上角看到一個 200 × 200 點的群組。群組內，淡灰色的矩形位於上方，緊接著下方則是你指定的圖片，兩者完美對齊。

![Grouped shape example](grouped-shape.png){:alt="空白 Word 文件的螢幕截圖，內含一個包含矩形與嵌入圖片的群組圖形"}

## 常見變化與邊緣情況處理

| 情境 | 需要變更的項目 | 為何重要 |
|----------|----------------|----------------|
| **不同的群組大小** | 調整 `insertGroupShape(width, height)` 的參數 | 較大的群組可容納更複雜的版面配置。 |
| **多張圖片** | 每次先移至群組的段落，再重複呼叫 `builder.insertImage()` | 每次呼叫會新增一個子圖形；也可以使用 `Shape.setLeft()` / `setTop()` 來定位。 |
| **動態圖片路徑** | 使用 `String.format("images/%s.jpg", imageName)` | 讓程式碼在批次處理時更具可重用性。 |
| **另存為 PDF** | 改為 `doc.save("output.pdf")` | Aspose.Words 可即時轉換，直接產生 PDF。 |
| **旋轉群組** | `group.setRotation(45);` | 可用於裝飾性浮水印或風格化的標題。 |

## 預期輸出與驗證

執行類別後：

1. `output.docx` 會出現在專案資料夾中。  
2. 開啟檔案會看到一個包含群組圖形的單頁文件。  
3. 群組內，矩形位於左上角，圖片緊接其下。  
4. 在 Word 中選取該群組時，兩個子物件皆會被高亮，證明它們真的被群組化。

若上述任一步驟失敗，請再次確認圖片路徑，並確保 Aspose.Words 的 JAR 已加入 classpath。

## 結論

現在你已了解 **how to create blank word document**，並能以包含矩形與嵌入圖片的群組圖形來豐富它。掌握 **how to create group**、**insert rectangle shape** 與 **add image word document** 後，你即可全程以程式碼建立複雜的 Word 範本，無需手動調整。

準備好接受下一個挑戰了嗎？試著在同一個群組內加入文字方塊，或是測試不同的圖形樣式以符合企業品牌。甚至可以產生一整套報告庫，讓每份文件都以此版面開始。

祝程式開發順利，歡迎在下方留言分享你的變化版本！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，建立在此處示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [建立 Word 文件 Java – 加入帶陰影效果的矩形圖形](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words for Java 建立 PDF 文件 | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}