---
date: 2026-02-19
description: 學習如何使用 Aspose.Words for Java 建立帶有浮水印的文件，並加入影像浮水印，以製作專業外觀的文件。
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 建立帶有浮水印的文件
url: /zh-hant/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 建立帶浮水印的文件

在本教學中，您將 **create document with watermark**，使用 Aspose.Words for Java API。浮水印（文字或圖片）可協助您將檔案標示為機密、草稿或已核准，且可以程式方式套用至任何 Word 文件。我們將逐步說明如何設定函式庫、加入文字與圖片浮水印、客製化外觀，甚至在不需要時將其移除。

## 快速解答
- **浮水印的作用是什麼？** 它會在每一頁覆蓋文字或圖片，以傳達狀態或品牌資訊。  
- **哪個函式庫在 Java 中加入浮水印？** Aspose.Words for Java 提供內建的浮水印支援。  
- **我可以加入圖片浮水印嗎？** 可以——使用 `Shape` 類別以及 `add image watermark java` 方法。  
- **浮水印可以半透明嗎？** 您可以透過 `setSemitransparent` 來控制文字浮水印的透明度。  
- **需要授權嗎？** 免費試用可用於測試；正式上線需購買商業授權。

## 什麼是浮水印以及為什麼要使用它？

浮水印是一種淡淡的覆蓋層（文字或圖形），會加在文件的每一頁上。它常用於表示 **機密**、**草稿狀態** 或 **品牌**，而不會改變原始內容。以程式方式加入浮水印可確保大量檔案的一致性，並節省手動編輯的時間。

## 設定 Aspose.Words for Java

在開始加入浮水印之前，請先確保您的專案已正確設定函式庫：

1. 從 [here](https://releases.aspose.com/words/java/) 下載 Aspose.Words for Java。  
2. 將下載的 JAR（或 Maven/Gradle 相依性）加入專案的 classpath。  
3. 在 Java 原始檔中匯入所需的類別：

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

現在函式庫已設定完成，讓我們深入實作浮水印程式碼。

## 如何加入文字浮水印

文字浮水印非常適合為文件標示「CONFIDENTIAL」或「DRAFT」。以下程式碼示範如何使用 `TextWatermarkOptions` **create document with watermark**。

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### 自訂文字浮水印
- **字型與大小** – 變更 `setFontFamily` 與 `setFontSize`。  
- **顏色** – 使用任意 `java.awt.Color`。  
- **版面配置** – 選擇 `HORIZONTAL`、`DIAGONAL` 等。  
- **透明度** – 透過 `setSemitransparent(true)` 取得較淡的效果。

## 如何加入圖片浮水印（add image watermark java）

圖片浮水印非常適合放置商標或自訂圖形。以下是 **add image watermark java** 範例，會在每一頁的中央插入 PNG 圖片。

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### 圖片浮水印的提示
- **調整大小** 使用 `setWidth` / `setHeight` 以符合頁面。  
- **位置** 可置中或依任意邊距對齊，使用 `RelativeHorizontalPosition` / `RelativeVerticalPosition`。  
- **透明度** 可在載入前調整圖片的 alpha 通道來實現。

## 如何移除浮水印

當文件不再需要浮水印時，您可以以程式方式將其刪除。以下程式碼會遍歷所有 Shape，移除名稱中含有 “Watermark” 的項目。

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## 常見問題與除錯

- **儲存後浮水印遺失** – 確認在設定浮水印後呼叫 `doc.save()`。  
- **圖片未顯示** – 檢查圖片路徑是否正確，且檔案格式支援（PNG、JPEG、BMP）。  
- **透明度未套用** – `setSemitransparent(true)` 只對文字浮水印有效；圖片則需先編輯 PNG 的 alpha 通道。  
- **多節點文件** – 若文件包含多個節點，請將浮水印加入每個節點的 body，或使用 `doc.getWatermark().setText(...)` 以全域方式套用。

## 常見問答

**Q: 如何變更文字浮水印的字型？**  
A: 在 `TextWatermarkOptions` 中修改 `setFontFamily` 屬性，例如 `options.setFontFamily("Times New Roman");`。

**Q: 可以在同一文件加入多個浮水印嗎？**  
A: 可以。建立多個 `Shape` 物件（圖片）或對每個浮水印呼叫 `doc.getWatermark().setText(...)`，並使用不同的選項。

**Q: 浮水印可以旋轉嗎？**  
A: 圖片浮水印可在 `Shape` 物件上使用 `watermark.setRotation(angle)` 來設定旋轉角度。文字浮水印則可透過 `setLayout` 屬性（例如 `WatermarkLayout.DIAGONAL`）達成。

**Q: 如何讓浮水印半透明？**  
A: 在 `TextWatermarkOptions` 中設定 `options.setSemitransparent(true)`。圖片則需在載入前調整其不透明度。

**Q: 能只在文件的特定節點加入浮水印嗎？**  
A: 能。遍歷 `doc.getSections()`，僅在需要的節點加入浮水印。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**最後更新：** 2026-02-19  
**測試環境：** Aspose.Words for Java 24.12 (latest)  
**作者：** Aspose