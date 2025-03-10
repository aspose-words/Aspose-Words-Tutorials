---
title: 在 Aspose.Words for Java 中使用文件浮水印
linktitle: 使用文件浮水印
second_title: Aspose.Words Java 文件處理 API
description: 了解如何在 Aspose.Words for Java 中新增浮水印。為具有專業外觀的文件自訂文字和圖像浮水印。
weight: 15
url: /zh-hant/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文件浮水印


## 在 Aspose.Words for Java 中向文件添加浮水印簡介

在本教學中，我們將探討如何使用 Aspose.Words for Java API 為文件新增浮水印。水印是用文字或圖形標記文件的有用方法，以指示其狀態、機密性或其他相關資訊。我們將在本指南中介紹文字和圖像浮水印。

## 設定 Aspose.Words for Java

在開始向文件添加浮水印之前，我們需要設定 Aspose.Words for Java。請依照以下步驟開始：

1. 下載 Aspose.Words for Java 從[這裡](https://releases.aspose.com/words/java/).
2. 將 Aspose.Words for Java 程式庫新增到您的 Java 專案中。
3. 在 Java 程式碼中匯入必要的類別。

現在我們已經設定了庫，讓我們繼續添加浮水印。

## 新增文字浮水印

當您想要為文件新增文字資訊時，文字浮水印是常見的選擇。以下是使用 Aspose.Words for Java 新增文字浮水印的方法：

```java
//建立文件實例
Document doc = new Document("Document.docx");

//定義文字浮水印選項
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//設定浮水印文字和選項
doc.getWatermark().setText("Test", options);

//儲存帶有浮水印的文檔
doc.save("DocumentWithWatermark.docx");
```

## 新增影像浮水印

除了文字浮水印之外，您還可以將圖像浮水印新增至文件。添加圖片浮水印的方法如下：

```java
//建立文件實例
Document doc = new Document("Document.docx");

//載入浮水印圖像
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

//設定浮水印大小和位置
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

//將浮水印加入文件中
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

//儲存帶有浮水印的文檔
doc.save("DocumentWithImageWatermark.docx");
```

## 自訂浮水印

您可以透過調整浮水印的外觀和位置來自訂浮水印。對於文字浮水印，您可以變更字體、大小、顏色和版面配置。對於影像浮水印，您可以修改其大小和位置，如前面的範例所示。

## 去除浮水印

若要從文件中刪除浮水印，可以使用以下程式碼：

```java
//建立文件實例
Document doc = new Document("DocumentWithWatermark.docx");

//去除浮水印
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

//儲存無浮水印的文檔
doc.save("DocumentWithoutWatermark.docx");
```


## 結論

在本教程中，我們學習如何使用 Aspose.Words for Java 為文件添加浮水印。無論您需要添加文字還是圖像浮水印，Aspose.Words 都提供了有效自訂和管理它們的工具。您也可以在不再需要浮水印時將其刪除，確保您的文件乾淨且專業。

## 常見問題解答

### 如何更改文字浮水印的字體？

若要變更文字浮水印的字體，請修改`setFontFamily`財產在`TextWatermarkOptions`。例如：

```java
options.setFontFamily("Times New Roman");
```

### 我可以在單一文件中添加多個浮水印嗎？

是的，您可以透過建立多個浮水印來為文件添加多個浮水印`Shape`具有不同設定的物件並將它們新增至文件中。

### 可以旋轉浮水印嗎？

是的，您可以透過設定旋轉浮水印`setRotation`財產在`Shape`目的。正值順時針旋轉浮水印，負值逆時針旋轉浮水印。

### 如何讓水印半透明？

要使水印半透明，請設置`setSemitransparent`財產給`true`在`TextWatermarkOptions`.

### 我可以將浮水印新增至文件的特定部分嗎？

是的，您可以透過迭代各個部分並將浮水印新增至所需部分來將浮水印新增至文件的特定部分。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
