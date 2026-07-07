---
category: general
date: 2026-07-06
description: 使用 Aspose.Words 在 Java 中建立矩形形狀 ─ 學習如何為形狀添加陰影、設定形狀透明度，並將文件另存為 PDF。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: zh-hant
og_description: 在 Java 中使用 Aspose.Words 建立矩形形狀。本指南說明如何為形狀添加陰影、設定形狀透明度，並將文件另存為 PDF。
og_title: 在 Java 中建立矩形形狀 – Aspose.Words 教學
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: 使用 Aspose.Words 在 Java 中建立矩形形狀 – 完整指南
url: /zh-hant/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中使用 Aspose.Words 建立矩形形狀 – 完整指南

有沒有想過如何在 Java 中 **建立矩形形狀**，卻不必與低階繪圖 API 纏鬥？你並不孤單。許多開發者需要一個快速、可靠的方式，將矩形插入 Word 文件、加上細緻的陰影、調整透明度，然後將結果輸出為 PDF。  

在本教學中，我們將一步一步說明完整可執行的程式碼。完成後，你將會知道 **如何為形狀加入陰影**、**如何設定形狀透明度**，以及 **如何使用 Aspose.Words for Java 將文件儲存為 PDF**。沒有多餘的說明，只有實用的指引，直接複製貼上到你的專案即可。

## 你將學到什麼

- 在 Java 專案中使用 Aspose.Words 所需的最小設定。  
- 如何以程式方式 **建立矩形形狀**。  
- 為 **形狀加入陰影** 並調整模糊、偏移與不透明度的精確呼叫方式。  
- **設定形狀透明度** 的方法，讓矩形能與周圍內容自然融合。  
- 最簡單的 **將文件儲存為 PDF** 方法，無需額外的轉換步驟。  

只要你對基本的 Java 有一定了解，且使用 Maven 或 Gradle 建置，即可立即上手。

## 前置條件

- Java 8 或更新版本。  
- Aspose.Words for Java 23.x（或閱讀時的最新版本）。  
- 任一 IDE 或指令列建置工具（IntelliJ、Eclipse、Maven、Gradle——隨你喜好）。  

> **專業小技巧：** Aspose 提供免費的暫時授權供評估使用。從你的帳號入口取得 `license.xml`，並放入 classpath；否則在 PDF 中會看到浮水印。

---

## 步驟 1：使用 Aspose.Words **建立矩形形狀**

首先，我們需要一個空的 `Document` 與 `DocumentBuilder`。`DocumentBuilder` 是核心工具，可直接在文件流程中插入形狀。

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**為什麼這很重要：** `ShapeType.RECTANGLE` 告訴 Aspose 我們想要一個完美的矩形。寬度與高度以點 (pt) 為單位（1 pt ≈ 1/72 in），讓你能精細控制最終尺寸。

---

## 步驟 2：**為形狀加入陰影**

現在已有矩形，讓我們為它加上一個細緻的投影。`ShadowFormat` 物件提供所有需要的屬性——模糊半徑、X/Y 偏移，甚至透明度。

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**為什麼這很重要：** 沒有模糊的陰影看起來像硬線，這通常不是設計師想要的效果。`setBlur` 讓邊緣變得平滑，而 `setTransparency` 則讓陰影逐漸淡入背景。依照你的 UI 規範調整這些數值即可。

---

## 步驟 3：**設定形狀透明度**

有時候你需要讓矩形本身半透明——例如要覆蓋商標或浮水印。Aspose 只需要一行程式碼即可完成。

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**為什麼這很重要：** 透明度在疊加多個形狀時非常實用。請注意，陰影的透明度是獨立的，你可以讓形狀本身較淡，而陰影較深，以符合設計需求。

---

## 步驟 4：**將文件儲存為 PDF**

所有視覺設定已完成，最後一步是將文件寫入磁碟。Aspose.Words 能直接輸出 PDF，省去額外的轉換函式庫。

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**為什麼這很重要：** 指定 `SaveFormat.PDF` 後，函式庫會在背後自動處理字型嵌入、影像壓縮與 PDF/A 相容性。產出的檔案即可直接用於發佈、列印或保存。

---

## 完整可執行範例

以下是完整、可直接執行的類別。複製貼上、調整輸出資料夾，即可得到帶有真實陰影的矩形 PDF。

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**預期結果：** 開啟 `RectangleWithShadow.pdf` 後，你會看到一個淡灰色的矩形置於第一頁正中央，透過柔和、半透明的陰影稍微浮起。矩形本身透明度為 20%，因此若底下有文字（你自行加入的話），文字會若隱若現。

---

## 常見問題與邊緣情況

### 1️⃣ 如果需要更大的矩形該怎麼辦？

只要在 `insertShape` 的寬度與高度參數調整即可。記得 72 pt = 1 in，例如 `400.0, 200.0` 會產生約 5.5 × 2.8 英吋的矩形。

### 2️⃣ 可以為陰影使用不同顏色嗎？

當然可以。`ShadowFormat` 也提供 `setColor(java.awt.Color)` 方法。若想要細緻的灰色陰影，可使用 `shadow.setColor(java.awt.Color.DARK_GRAY);`。

### 3️⃣ `save document as pdf` 在所有平台都能運作嗎？

可以。Aspose.Words for Java 與平台無關，只要有相容的 JRE，程式碼在 Windows、macOS 與 Linux 上皆可執行。

### 4️⃣ 之後要移除陰影要怎麼做？

呼叫 `rect.getShadowFormat().clear();` 或將 `Visible` 屬性設為 `false`（`shadow.setVisible(false);`）。

### 5️⃣ DPI 與影像品質如何處理？

輸出為 PDF 時，Aspose 會自動以 300 DPI 處理向量圖形（例如形狀），因此在任何放大倍率下都能保持清晰。

---

## 專業技巧與最佳實踐

- **批次處理：** 若需產生大量 PDF，請重複使用同一個 `Document` 實例，僅在每次迭代間清除其 sections，以減少 GC 壓力。  
- **授權設定：** 在 `main` 方法開頭加入 `License license = new License(); license.setLicense("license.xml");`，即可避免評估浮水印。  
- **效能考量：** 陰影渲染對簡單形狀成本低，但複雜路徑會拖慢 PDF 產生速度。若處理大量文件，請進行效能分析。  
- **測試流程：** 先使用 `Document.save(..., SaveFormat.DOCX)` 檢查形狀在 Word 中是否正確顯示，再轉成 PDF。

---

## 結論

現在你已掌握如何在 Java 中使用 Aspose.Words **建立矩形形狀**、**為形狀加入陰影**、**設定形狀透明度**，以及最後 **將文件儲存為 PDF**。程式碼獨立、相容最新的 Aspose 函式庫，示範了大多數文件自動化情境下必備的 API 呼叫。

想挑戰下一個目標嗎？試著把矩形換成橢圓、玩弄漸層填色，或探索如何 **為文字框加入陰影**。原理相同，Aspose API 讓一切變得輕而易舉。

祝開發順利，若遇到任何問題，歡迎在下方留言討論！

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步擴展你的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，助你掌握更多 API 功能，或在專案中探索不同的實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}