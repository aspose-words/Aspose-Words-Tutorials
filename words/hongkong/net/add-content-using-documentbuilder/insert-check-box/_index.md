---
title: 使用 Aspose.Words for .NET 在 Word 文件中加入核取方塊表單欄位
weight: 210
limit:
description: 了解如何使用 Aspose.Words for .NET 以程式方式在新建的 Word 文件中加入核取方塊表單欄位，並儲存檔案。
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中加入核取方塊表單欄位
本教學說明如何建立全新的 Word 文件，並使用 Aspose.Words for .NET 的 DocumentBuilder 插入核取方塊表單欄位。依照步驟操作，即可看到加入互動元件的完整程式碼，然後將文件儲存為檔案。這是以程式方式快速建立簡易表單功能 Word 檔的方式。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: InsertCheckBox 的第四個參數 (0) 代表什麼？**
A: 它指定核取方塊的視覺大小（以點為單位）；值為 0 時表示讓 Aspose.Words 使用預設大小。

**Q: 我可以插入多個名稱相同的核取方塊嗎？**
A: 不行——每個表單欄位名稱必須唯一；若嘗試再插入名稱為 "CheckBox" 的核取方塊，會拋出 ArgumentException。

**Q: 如何在現有文件中加入核取方塊，而不是在新文件中？**
A: 先載入文件（例如 `Document doc = new Document("Existing.docx");`），再為該文件建立 DocumentBuilder，於所需的游標位置呼叫 `InsertCheckBox`。

**Q: 文件儲存後，我該如何讀取已插入核取方塊的狀態？**
A: 透過 `doc.Range.FormFields["CheckBox"]` 取得表單欄位，檢查其 `Checked` 屬性即可得知是否已勾選。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}