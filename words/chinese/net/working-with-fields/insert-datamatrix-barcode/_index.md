---
title: 使用 Aspose.Words for .NET 在 Word 文档中插入 DataMatrix 条码
weight: 210
limit:
description: 使用 Aspose.Words for .NET 以编程方式向 Word 文档添加 DataMatrix 条码。
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: 使用 Aspose.Words for .NET 以编程方式向 Word 文档添加 DataMatrix 条码。
  headline: 使用 Aspose.Words for .NET 在 Word 文档中插入 DataMatrix 条码
  type: TechArticle
- description: 使用 Aspose.Words for .NET 以编程方式向 Word 文档添加 DataMatrix 条码。
  name: 使用 Aspose.Words for .NET 在 Word 文档中插入 DataMatrix 条码
  steps:
  - name: 创建一个新的空 Word 文档以及用于编辑它的 DocumentBuilder。
    text: 创建一个新的空 Word 文档以及用于编辑它的 DocumentBuilder。
  - name: 在当前光标位置插入 DISPLAYBARCODE 字段，这会在文档中添加一个字段占位符。
    text: 在当前光标位置插入 DISPLAYBARCODE 字段，这会在文档中添加一个字段占位符。
  - name: 将字段的 BarcodeType 设置为 DataMatrix，并提供要编码的数据字符串。
    text: 将字段的 BarcodeType 设置为 DataMatrix，并提供要编码的数据字符串。
  - name: 可选地定义条码的背景色和前景色。
    text: 可选地定义条码的背景色和前景色。
  - name: 在文档上调用 UpdateFields，以在字段内部渲染条码图像。
    text: 在文档上调用 UpdateFields，以在字段内部渲染条码图像。
  - name: 将文档保存为 .docx 文件。
    text: 将文档保存为 .docx 文件。
  type: HowTo
- questions:
  - answer: 字段会被插入，但 `document.UpdateFields()` 会导致条码为空，且 Aspose.Words 会抛出 `FieldException`，提示条码类型无效。
    question: 如果我为 `displayBarcodeField.BarcodeType` 赋予不受支持的值，会发生什么？
  - answer: '`UpdateFields()` 会渲染条码图像，因此您可以插入多个 `FieldDisplayBarcode` 对象，并在最后一次性调用
      `document.UpdateFields()` 来渲染全部。'
    question: 我是否需要在每次插入条码后调用 `document.UpdateFields()`，还是可以在添加完所有字段后一次性更新？
  - answer: 这两个属性都期望以 `0x` 为前缀的十六进制 RGB 字符串（例如红色的 `"0xFF0000"`）；其他格式将被忽略，使用默认颜色。
    question: '`BackgroundColor` 和 `ForegroundColor` 的颜色字符串应使用什么格式？'
  - answer: 可以——只需将 `displayBarcodeField.BarcodeValue` 设置为新的字符串，然后再次调用 `document.UpdateFields()`
      即可刷新渲染的图像。
    question: 字段插入后，我可以更改条码的内容吗？
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: 使用 Aspose.Words 插入 DataMatrix 条码
og_description: 了解如何仅用几行 .NET 代码向 Word 文件添加 DataMatrix 条码。
og_image_alt: 指南展示了如何使用 Aspose.Words for .NET 在 Word 文档中插入并渲染 DataMatrix 条码
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文档中插入 DataMatrix 条码
使用 Aspose.Words for .NET，您可以以编程方式向 Word 文档添加 DataMatrix 条码。本教程展示了如何创建新文档，插入 DISPLAYBARCODE 字段，将其类型设置为 DataMatrix，并使用 Document 和 DocumentBuilder 类渲染条码图像。按照步骤操作，即可在 .docx 文件中直接生成可打印的条码。

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

**Q: 如果我为 `displayBarcodeField.BarcodeType` 赋予不受支持的值，会发生什么？**  
A: 字段会被插入，但 `document.UpdateFields()` 会导致条码为空，且 Aspose.Words 会抛出 `FieldException`，提示条码类型无效。

**Q: 我是否需要在每次插入条码后调用 `document.UpdateFields()`，还是可以在添加完所有字段后一次性更新？**  
A: `UpdateFields()` 会渲染条码图像，因此您可以插入多个 `FieldDisplayBarcode` 对象，并在最后一次性调用 `document.UpdateFields()` 来渲染全部。

**Q: `BackgroundColor` 和 `ForegroundColor` 的颜色字符串应使用什么格式？**  
A: 这两个属性都期望以 `0x` 为前缀的十六进制 RGB 字符串（例如红色的 `"0xFF0000"`）；其他格式将被忽略，使用默认颜色。

**Q: 字段插入后，我可以更改条码的内容吗？**  
A: 可以——只需将 `displayBarcodeField.BarcodeValue` 设置为新的字符串，然后再次调用 `document.UpdateFields()` 即可刷新渲染的图像。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}