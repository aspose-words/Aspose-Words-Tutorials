---
category: general
date: 2026-07-29
description: 使用 Aspose.Words 於 Java 建立 Word 文件，學習在 Word 中插入矩形形狀、群組形狀，並快速儲存為 docx 檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: zh-hant
lastmod: 2026-07-29
og_description: 使用 Aspose.Words 在 Java 中建立 Word 文件。插入矩形形狀，在 Word 中將形狀分組，並在幾分鐘內將文件另存為
  docx。
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: 建立含圖形的 Word 文件 – Java Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: 使用 Java 建立帶有形狀的 Word 文件 – 完整 Aspose.Words 指南
url: /zh-hant/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 建立含圖形的 Word 文件 – 完整 Aspose.Words 指南

有沒有想過如何以程式方式 **create word document** 並加入自訂圖形？你並不是唯一有此需求的人。無論是要產生帶有重點標示的報告，或是即時設計傳單，精通 Word 中的圖形處理都能為你節省大量手動工作時間。

在本教學中，我們將逐步說明如何使用 Aspose.Words for Java **create word document**、**insert rectangle shape**、**group shapes in Word**，以及最後的 **save document as docx**。完成後，你將擁有一個可直接在任何專案中執行的完整範例。

## 你將學到的內容

- 完全由 Java 程式碼產生的全新 Word 檔案。  
- 於頁面上加入兩個不同的圖形（矩形與橢圓）。  
- 透過 **group shapes in word** API 將這些圖形打包，使其行為如同單一物件。  
- 檔案以標準 `.docx` 格式儲存於磁碟，可在 Microsoft Word 中順利開啟。  

不需要外部工具或繁雜的 XML 操作——只要乾淨、型別安全的 Java 程式碼與 Aspose.Words 即可。

---

## 前置條件

在開始之前，請確保你已具備以下條件：

1. **Java Development Kit (JDK) 8 或更新版本** – 程式碼以 Java 8+ 為目標。  
2. **Aspose.Words for Java** JAR（可從 Maven Central 取得最新版本）。  
3. 一個基本的 IDE（IntelliJ IDEA、Eclipse，或甚至是簡易文字編輯器）。  

如果你已備妥，太好了——讓我們開始吧。

---

## 步驟實作

以下我們將整個流程拆解為多個小步驟。每個步驟都包含程式碼片段、簡短說明，以及官方文件中可能未提及的小技巧。

### ## 使用 Aspose.Words 建立含圖形的 Word 文件

首先，你需要一個空的 Word 檔案作為起點。Aspose.Words 只需一行程式碼即可完成。

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**為什麼重要：**  
`Document` 是所有內容的容器——文字、表格、圖片與圖形。`DocumentBuilder` 是友善的輔助工具，讓你無需與低階物件糾纏即可加入內容。可將其想像成直接在頁面上書寫的筆。

> **專業提示：** 若打算以範本（例如公司信頭）作為起點，請將 `new Document()` 改為 `new Document("template.docx")`。

### ## 插入矩形圖形與其他圖形

現在我們將加入一個藍色矩形與一個綠色橢圓。矩形示範 **insert rectangle shape** 關鍵字，而橢圓則顯示你可以自由混合不同類型的圖形。

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**背後發生了什麼？**  
每次呼叫 `insertShape` 都會建立一個 `Shape` 物件，並自動加入目前段落。`setLeft`/`setTop` 方法以點 (pt) 為單位（1 pt = 1/72 in）相對於頁面邊界定位圖形。調整這些數值即可將圖形放置於任意位置。

> **常見問題：** *我可以改為加入圖片而非純色填充嗎？*  
> 當然可以——只需使用 `shape.getFill().setImage("path/to/image.png")` 取代填色即可。

### ## 在 Word 中群組圖形以便於操作

擁有兩個獨立的物件固然可行，但通常你會希望一次一起移動。這時 **group shapes in word** 就顯得非常有用。

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**為什麼要群組？**  
圖形群組後，任何變換——移動、旋轉、調整大小——都會套用到整個集合。這與在 Word 介面手動選取多個圖形後點選 *Group* 的行為相同。也能簡化後續程式碼，因為只需調整單一物件，而非多個。

> **特殊情況：** 若之後需要取消群組，可呼叫 `group.getParentNode().removeChild(group)`，再將子圖形逐一重新插入。

### ## 以 DOCX 格式儲存文件並驗證輸出

最後，我們將檔案寫入磁碟。此步驟滿足 **save document as docx** 的需求。

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**預期結果：**  
在 Microsoft Word 中開啟產生的 `GroupShapeExample.docx`。你會看到一個藍色矩形與綠色橢圓已被整齊群組。拖曳該群組時，兩個圖形會一起移動，正如 UI 中的行為。

> **小技巧：** 若需要 PDF 版，只需使用 `SaveFormat.PDF`，程式碼不需任何變更。

### ## 完整可執行範例與常見陷阱

以下是完整、可直接執行的 Java 類別。將其複製貼上至你的專案，調整輸出資料夾後點選 *Run* 即可。

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### 常見陷阱與避免方法

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | 忘記在建立 `Document` 後實例化 `DocumentBuilder`。 | 確保在插入任何圖形之前先執行 `new DocumentBuilder(doc)`。 |
| **Shapes appear off‑page** | 使用像素值而非點，或未考慮邊界。 | 記得 Aspose.Words 使用點作為單位；72 pt = 1 in。相應調整 `setLeft`/`setTop`。 |
| **Group disappears after save** | 在已儲存的群組之後才加入圖形。 | 一定要在呼叫 `doc.save()` 之前完成群組。 |
| **File not found on save** | 輸出目錄不存在。 | 以程式方式建立目錄 (`new File("output").mkdirs();`) 或使用已存在的路徑。 |

---

## 結論

我們剛剛從頭 **create word document**、**add shapes to word**、**insert rectangle shape**、**group shapes in word**，最後 **save document as docx**——全部只需幾行 Java 程式碼。Aspose.Words 的強大之處在於其清晰的物件模型；你可以把 Word 檔案當作畫布，用圖形繪製，然後依需求匯出。

想挑戰更高階的功能嗎？試著把矩形換成星形、使用 `Shape.getTextBox()` 在圖形內加入文字，或是嘗試旋轉 (`shape.setRotationAngle(45)`)。API 功能豐富，可能性幾乎無限。

對更進階的情境有疑問——例如將圖形連結至書籤或以嵌入字型的方式匯出 PDF？在下方留言，我們會一起深入探討。祝編程愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並在專案中探索其他實作方式。

- [建立 Word 文件（Java） – 加入帶陰影效果的矩形圖形](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 在 Word 中建立矩形圖形 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}