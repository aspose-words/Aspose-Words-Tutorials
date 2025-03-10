---
title: 在 Aspose.Words for Java 中將文件儲存為 PDF
linktitle: 將文件另存為 PDF
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 將 Word 文件儲存為 PDF。自訂字體、屬性和圖像品質。 PDF 轉換的綜合指南。
weight: 22
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中將文件儲存為 PDF


## 在 Aspose.Words for Java 中將文件儲存為 PDF 的簡介

在本逐步指南中，我們將探討如何使用 Aspose.Words for Java 將文件儲存為 PDF。我們將介紹 PDF 轉換的各個方面，並提供程式碼範例以使流程更容易。

## 先決條件

在我們開始之前，請確保您具備以下先決條件：

- 您的系統上安裝了 Java 開發工具包 (JDK)。
-  Aspose.Words for Java 函式庫。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/).

## 將文件轉換為 PDF

若要將Word文件轉換為PDF，您可以使用以下程式碼片段：

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

代替`"input.docx"`以及 Word 文件的路徑和`"output.pdf"`與所需的輸出 PDF 文件路徑。

## 控制 PDF 保存選項

您可以使用以下命令控制各種 PDF 儲存選項`PdfSaveOptions`班級。例如，您可以如下設定 PDF 文件的顯示標題：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## 在 PDF 中嵌入字體

若要在產生的 PDF 中嵌入字體，請使用下列程式碼：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## 自訂文件屬性

您可以在產生的 PDF 中自訂文件屬性。例如：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## 匯出文檔結構

若要匯出文件結構，請設定`exportDocumentStructure`選項`true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## 影像壓縮

您可以使用以下程式碼控制影像壓縮：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## 更新最後列印的屬性

若要更新 PDF 中的「上次列印」屬性，請使用：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## 渲染 DML 3D 效果

對於DML 3D效果的進階渲染，設定渲染模式：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## 插值影像

您可以啟用影像插值來提高影像品質：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## 結論

Aspose.Words for Java 提供了將 Word 文件轉換為 PDF 格式的全面功能，並具有靈活性和自訂選項。您可以控制 PDF 輸出的各個方面，包括字體、文件屬性、圖像壓縮等。

## 常見問題解答

### 如何使用 Aspose.Words for Java 將 Word 文件轉換為 PDF？

若要將 Word 文件轉換為 PDF，請使用下列程式碼：

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

代替`"input.docx"`以及 Word 文件的路徑和`"output.pdf"`與所需的輸出 PDF 文件路徑。

### 我可以在 Aspose.Words for Java 產生的 PDF 中嵌入字體嗎？

是的，您可以透過設定在 PDF 中嵌入字體`setEmbedFullFonts`選項`true`在`PdfSaveOptions`。這是一個例子：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### 如何在生成的 PDF 中自訂文件屬性？

您可以使用以下命令自訂 PDF 中的文件屬性`setCustomPropertiesExport`選項中`PdfSaveOptions`。例如：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Aspose.Words for Java 中圖片壓縮的目的為何？

影像壓縮可讓您控制生成的 PDF 中影像的品質和大小。您可以使用設定影像壓縮模式`setImageCompression`在`PdfSaveOptions`.

### 如何更新 PDF 中的「上次列印」屬性？

您可以透過設定更新 PDF 中的「上次列印」屬性`setUpdateLastPrintedProperty`到`true`在`PdfSaveOptions`。這將反映 PDF 元資料中的最後列印日期。

### 轉換為 PDF 時如何提升影像品質？

若要提高影像質量，請透過設定啟用影像插值`setInterpolateImages`到`true`在`PdfSaveOptions`。這將使 PDF 中的影像更平滑、更高品質。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
