---
"description": "了解如何在 Aspose.Words for Java 中新增浮水印。自訂文字和圖像浮水印，使文件看起來更專業。"
"linktitle": "在文件中使用浮水印"
"second_title": "Aspose.Words Java文件處理API"
"title": "在 Aspose.Words for Java 中使用浮水印文檔"
"url": "/zh-hant/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用浮水印文檔


## Aspose.Words for Java 文件浮水印新增簡介

在本教學中，我們將探討如何使用 Aspose.Words for Java API 為文件新增浮水印。水印是一種使用文字或圖形標記文件以指示其狀態、機密性或其他相關資訊的有效方法。在本指南中，我們將介紹文字和圖像浮水印。

## 設定 Aspose.Words for Java

在我們開始在文件中新增浮水印之前，我們需要設定 Aspose.Words for Java。請依照以下步驟開始：

1. 下載 Aspose.Words for Java [這裡](https://releases。aspose.com/words/java/).
2. 將 Aspose.Words for Java 程式庫新增至您的 Java 專案。
3. 在 Java 程式碼中匯入必要的類別。

現在我們已經設定好了庫，讓我們繼續添加水印。

## 新增文字浮水印

當您想要在文件中新增文字資訊時，文字浮水印是常見的選擇。以下是使用 Aspose.Words for Java 新增文字浮水印的方法：

```java
// 建立 Document 實例
Document doc = new Document("Document.docx");

// 定義 TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// 設定浮水印文字和選項
doc.getWatermark().setText("Test", options);

// 儲存帶有浮水印的文檔
doc.save("DocumentWithWatermark.docx");
```

## 新增影像浮水印

除了文字浮水印之外，您還可以在文件中新增圖像浮水印。添加影像浮水印的方法如下：

```java
// 建立 Document 實例
Document doc = new Document("Document.docx");

// 載入浮水印圖像
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// 設定浮水印大小和位置
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// 為文件添加浮水印
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// 儲存帶有浮水印的文檔
doc.save("DocumentWithImageWatermark.docx");
```

## 自訂浮水印

您可以透過調整浮水印的外觀和位置來自訂浮水印。對於文字浮水印，您可以變更字體、大小、顏色和版面配置。對於影像浮水印，您可以按照前面的範例所示修改其大小和位置。

## 去除浮水印

若要從文件中刪除浮水印，可以使用以下程式碼：

```java
// 建立 Document 實例
Document doc = new Document("DocumentWithWatermark.docx");

// 刪除浮水印
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// 儲存文檔，不含浮水印
doc.save("DocumentWithoutWatermark.docx");
```


## 結論

在本教程中，我們學習如何使用 Aspose.Words for Java 為文件添加浮水印。無論您需要添加文字還是圖像浮水印，Aspose.Words 都提供了有效自訂和管理它們的工具。您也可以刪除不再需要的浮水印，確保您的文件乾淨、專業。

## 常見問題解答

### 如何更改文字浮水印的字體？

若要變更文字浮水印的字體，請修改 `setFontFamily` 財產 `TextWatermarkOptions`。例如：

```java
options.setFontFamily("Times New Roman");
```

### 我可以在單一文件中添加多個浮水印嗎？

是的，您可以透過建立多個 `Shape` 具有不同設定的物件並將它們新增至文件中。

### 可以旋轉浮水印嗎？

是的，您可以透過設定 `setRotation` 財產 `Shape` 目的。正值使水印順時針旋轉，負值使水印逆時針旋轉。

### 如何讓水印變成半透明的？

要使水印半透明，請設置 `setSemitransparent` 財產 `true` 在 `TextWatermarkOptions`。

### 我可以在文件的特定部分添加浮水印嗎？

是的，您可以透過遍歷各個部分並將水印新增至所需的部分來將浮水印新增至文件的特定部分。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}