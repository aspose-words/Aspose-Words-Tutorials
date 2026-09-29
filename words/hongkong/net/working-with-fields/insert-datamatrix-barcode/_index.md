---
title: 使用 Aspose.Words for .NET 在 Word 文件中插入 DataMatrix 條碼
weight: 210
limit:
description: 以 Aspose.Words for .NET 程式化地將 DataMatrix 條碼加入 Word 文件。
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: 以 Aspose.Words for .NET 程式化地將 DataMatrix 條碼加入 Word 文件。
  headline: 使用 Aspose.Words for .NET 在 Word 文件中插入 DataMatrix 條碼
  type: TechArticle
- description: 以 Aspose.Words for .NET 程式化地將 DataMatrix 條碼加入 Word 文件。
  name: 使用 Aspose.Words for .NET 在 Word 文件中插入 DataMatrix 條碼
  steps:
  - name: 建立一個全新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
    text: 建立一個全新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
  - name: 在目前游標位置插入 DISPLAYBARCODE 欄位，這會在文件中加入欄位佔位符。
    text: 在目前游標位置插入 DISPLAYBARCODE 欄位，這會在文件中加入欄位佔位符。
  - name: 將欄位的 BarcodeType 設為 DataMatrix，並提供要編碼的資料字串。
    text: 將欄位的 BarcodeType 設為 DataMatrix，並提供要編碼的資料字串。
  - name: 亦可選擇性定義條碼的背景色與前景色。
    text: 亦可選擇性定義條碼的背景色與前景色。
  - name: 對文件呼叫 UpdateFields，以在欄位內呈現條碼影像。
    text: 對文件呼叫 UpdateFields，以在欄位內呈現條碼影像。
  - name: 將文件儲存為 .docx 檔案。
    text: 將文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: 欄位仍會被插入，但 `document.UpdateFields()` 會使條碼顯示為空白，且 Aspose.Words 會拋出 `FieldException`，指出條碼類型無效。
    question: 如果將不支援的值指派給 `displayBarcodeField.BarcodeType`，會發生什麼情況？
  - answer: '`UpdateFields()` 會渲染條碼影像，因此您可以插入多個 `FieldDisplayBarcode` 物件，最後只需呼叫一次
      `document.UpdateFields()` 即可一次渲染全部。'
    question: 我需要在每次插入條碼後都呼叫 `document.UpdateFields()`，還是可以在加入所有欄位後一次性更新？
  - answer: 兩個屬性皆接受以 `0x` 為前綴的十六進位 RGB 字串（例如紅色為 `"0xFF0000"`）；其他格式將被忽略，並使用預設顏色。
    question: '`BackgroundColor` 與 `ForegroundColor` 的顏色字串應使用何種格式？'
  - answer: 可以——只需將 `displayBarcodeField.BarcodeValue` 設為新的字串，然後再次呼叫 `document.UpdateFields()`
      即可重新渲染影像。
    question: 插入欄位後，我可以變更條碼的內容嗎？
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: 使用 Aspose.Words 插入 DataMatrix 條碼
og_description: 了解如何僅用幾行 .NET 程式碼將 DataMatrix 條碼加入 Word 檔案。
og_image_alt: 指南示範如何使用 Aspose.Words for .NET 在 Word 文件中插入與呈現 DataMatrix 條碼
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中插入 DataMatrix 條碼
使用 Aspose.Words for .NET，您可以以程式方式將 DataMatrix 條碼加入 Word 文件。本教學說明如何建立新文件、插入 DISPLAYBARCODE 欄位、將其類型設為 DataMatrix，並使用 Document 與 DocumentBuilder 類別呈現條碼影像。依照步驟操作，即可在 .docx 檔案中直接產生可列印的條碼。

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 如果將不支援的值指派給 `displayBarcodeField.BarcodeType`，會發生什麼情況？**  
A: 欄位仍會被插入，但 `document.UpdateFields()` 會使條碼顯示為空白，且 Aspose.Words 會拋出 `FieldException`，指出條碼類型無效。

**Q: 我需要在每次插入條碼後都呼叫 `document.UpdateFields()`，還是可以在加入所有欄位後一次性更新？**  
A: `UpdateFields()` 會渲染條碼影像，因此您可以插入多個 `FieldDisplayBarcode` 物件，最後只需呼叫一次 `document.UpdateFields()` 即可一次渲染全部。

**Q: `BackgroundColor` 與 `ForegroundColor` 的顏色字串應使用何種格式？**  
A: 兩個屬性皆接受以 `0x` 為前綴的十六進位 RGB 字串（例如紅色為 `"0xFF0000"`）；其他格式將被忽略，並使用預設顏色。

**Q: 插入欄位後，我可以變更條碼的內容嗎？**  
A: 可以——只需將 `displayBarcodeField.BarcodeValue` 設為新的字串，然後再次呼叫 `document.UpdateFields()` 即可重新渲染影像。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}