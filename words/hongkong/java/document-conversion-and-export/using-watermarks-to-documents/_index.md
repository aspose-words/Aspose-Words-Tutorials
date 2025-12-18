---
date: 2025-12-18
description: 學習如何使用 Aspose.Words for Java 為文件加入水印，包括圖片水印範例、更改水印顏色、設定水印透明度，以及移除文件水印。
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 為文件添加水印
url: /zh-hant/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 為文件添加浮水印

## 在 Aspose.Words for Java 中添加浮水印的簡介

在本教學中，您將學習 **如何添加浮水印** 到使用 Aspose.Words for Java 的 Word 文件。浮水印是一種快速標示檔案為機密、草稿或已批准的方式，且可以是文字或圖片形式。我們將逐步說明如何設定程式庫、建立文字與圖片浮水印、客製化外觀（包括變更浮水印顏色與設定浮水印透明度），以及在不再需要時移除浮水印。

## 快速問答
- **什麼是浮水印？** 一種半透明的覆蓋層（文字或圖片），顯示在文件主要內容的後方。  
- **我可以添加多個浮水印嗎？** 可以 – 建立多個 `Shape` 物件，並將它們加入到所需的節中。  
- **如何變更浮水印顏色？** 調整 `TextWatermarkOptions` 中的 `Color` 屬性。  
- **有圖片浮水印範例嗎？** 請參閱下方的「添加圖片浮水印」章節。  
- **移除浮水印需要授權嗎？** 生產環境使用時需要有效的 Aspose.Words 授權。

## 設定 Aspose.Words for Java

在開始為文件添加浮水印之前，我們需要先設定 Aspose.Words for Java。請依照以下步驟進行：

1. 從 [此處](https://releases.aspose.com/words/java/) 下載 Aspose.Words for Java。  
2. 將 Aspose.Words for Java 程式庫加入您的 Java 專案中。  
3. 在您的 Java 程式碼中匯入必要的類別。  

現在程式庫已設定完成，讓我們深入探討實際的浮水印建立方式。

## 添加文字浮水印

當您想在文件中加入文字資訊時，文字浮水印是常見的選擇。以下說明如何使用 Aspose.Words for Java 添加文字浮水印：

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

**為什麼這很重要：** 透過調整 `setFontFamily`、`setFontSize` 與 `setColor`，您可以 **變更浮水印顏色** 以符合品牌形象；而 `setSemitransparent(true)` 則可 **設定浮水印透明度**，營造細緻的效果。

## 添加圖片浮水印

除了文字浮水印外，您也可以在文件中加入圖片浮水印。以下是一個 **圖片浮水印範例**，示範如何嵌入 PNG 標誌或印章：

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

您可以使用不同的圖片或位置重複此程式碼區塊，以 **在單一檔案中添加多個浮水印**。

## 自訂浮水印

您可以透過調整外觀與位置來自訂浮水印。對於文字浮水印，您可以變更字型、大小、顏色與版面配置；對於圖片浮水印，則可如前例所示調整大小、旋轉角度與對齊方式。

## 移除浮水印

若需要 **移除文件中的浮水印**，以下程式碼會遍歷所有圖形，並刪除被辨識為浮水印的項目：

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

## 常見使用情境與技巧
- **機密草稿：** 套用類似「CONFIDENTIAL」的半透明文字浮水印。  
- **品牌形象：** 使用包含公司標誌的圖片浮水印。  
- **特定節的浮水印：** 迭代 `doc.getSections()`，僅在您選擇的節中加入浮水印。  
- **效能技巧：** 在多個文件套用相同浮水印時，重複使用同一個 `TextWatermarkOptions` 實例。  

## 常見問題

### 如何變更文字浮水印的字型？

若要變更文字浮水印的字型，請修改 `TextWatermarkOptions` 中的 `setFontFamily` 屬性。例如：

```java
options.setFontFamily("Times New Roman");
```

### 我可以在單一文件中添加多個浮水印嗎？

可以，您可以透過建立多個具有不同設定的 `Shape` 物件，並將它們加入文件中，以添加多個浮水印。

### 可以旋轉浮水印嗎？

可以，您可以在 `Shape` 物件中設定 `setRotation` 屬性來旋轉浮水印。正值會順時針旋轉，負值則會逆時針旋轉。

### 如何讓浮水印呈半透明？

若要讓浮水印呈半透明，請在 `TextWatermarkOptions` 中將 `setSemitransparent` 屬性設為 `true`。

### 我可以在文件的特定節加入浮水印嗎？

可以，您可以遍歷文件的各節，並將浮水印加入您指定的節中。

---

**最後更新：** 2025-12-18  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}