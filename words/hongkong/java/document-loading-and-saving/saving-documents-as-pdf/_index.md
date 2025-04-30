---
"description": "了解如何使用 Aspose.Words for Java 將 Word 文件儲存為 PDF。自訂字體、屬性和圖像品質。 PDF 轉換的綜合指南。"
"linktitle": "將文件儲存為 PDF"
"second_title": "Aspose.Words Java文件處理API"
"title": "在 Aspose.Words for Java 中將文件儲存為 PDF"
"url": "/zh-hant/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中將文件儲存為 PDF


## Aspose.Words for Java 文件儲存為 PDF 簡介

在本逐步指南中，我們將探討如何使用 Aspose.Words for Java 將文件儲存為 PDF。我們將介紹 PDF 轉換的各個方面，並提供程式碼範例以簡化該過程。

## 先決條件

在開始之前，請確保您已滿足以下先決條件：

- 您的系統上安裝了 Java 開發工具包 (JDK)。
- Java 函式庫的 Aspose.Words。您可以從下載 [這裡](https://releases。aspose.com/words/java/).

## 將文件轉換為 PDF

若要將 Word 文件轉換為 PDF，您可以使用以下程式碼片段：

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

代替 `"input.docx"` 您的 Word 文件的路徑和 `"output.pdf"` 使用所需的輸出 PDF 檔案路徑。

## 控制 PDF 保存選項

您可以使用以下方式控制各種 PDF 儲存選項 `PdfSaveOptions` 班級。例如，您可以如下設定 PDF 文件的顯示標題：

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

若要匯出文件結構，請設定 `exportDocumentStructure` 選擇 `true`：

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

## 更新上次列印的屬性

若要更新 PDF 中的「上次列印」屬性，請使用：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## 渲染 DML 3D 效果

對於 DML 3D 效果的進階渲染，請設定渲染模式：

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

代替 `"input.docx"` 您的 Word 文件的路徑和 `"output.pdf"` 使用所需的輸出 PDF 檔案路徑。

### 我可以在 Aspose.Words for Java 產生的 PDF 中嵌入字體嗎？

是的，您可以透過設定 `setEmbedFullFonts` 選擇 `true` 在 `PdfSaveOptions`。以下是一個例子：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### 如何在生成的 PDF 中自訂文件屬性？

您可以使用 `setCustomPropertiesExport` 選擇 `PdfSaveOptions`。例如：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Aspose.Words for Java 中的圖片壓縮的目的為何？

影像壓縮可讓您控制生成的 PDF 中影像的品質和大小。您可以使用以下方式設定影像壓縮模式 `setImageCompression` 在 `PdfSaveOptions`。

### 如何更新 PDF 中的「上次列印」屬性？

您可以透過設定來更新 PDF 中的「上次列印」屬性 `setUpdateLastPrintedProperty` 到 `true` 在 `PdfSaveOptions`。這將反映 PDF 元資料中的最後列印日期。

### 如何在轉換為 PDF 時提高影像品質？

為了提高影像質量，請透過設定啟用影像插值 `setInterpolateImages` 到 `true` 在 `PdfSaveOptions`。這將使 PDF 中的影像更加流暢且品質更高。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}