---
title: 使用 Aspose.Words for .NET 在 Word 文件中插入水平線形狀。
weight: 110
limit:
description: 學習使用 DocumentBuilder 及 Aspose.Words for .NET 為 Word 文件新增水平線形狀。
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中插入水平線形狀。
在本教學中，您將學習如何使用 Aspose.Words for .NET 以程式方式在 Word 文件中插入水平線形狀。透過 Document 與 DocumentBuilder 類別，我們建立新文件、加入文字段落，然後在指定位置放置水平線形狀。水平線作為視覺分隔線，可用於章節分割或強調重點。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: `builder.InsertHorizontalRule()` 會在文件中的哪個位置插入線條？**  
A: `InsertHorizontalRule` 會在 `DocumentBuilder` 目前的游標位置插入水平線形狀；若希望它單獨佔一行，請在插入前先呼叫 `builder.Writeln()`。

**Q: 我可以更改插入的水平線的粗細、顏色或寬度嗎？**  
A: `InsertHorizontalRule` 會加入預設樣式的水平線，且不提供格式設定選項；若要自訂這些屬性，必須手動插入 `Shape`（例如 `builder.InsertShape(ShapeType.HorizontalLine)`），然後設定其 `LineFormat` 屬性。

**Q: 是否可以在同一文件中加入多條水平線？**  
A: 可以——只要在需要新水平線時呼叫 `builder.InsertHorizontalRule()`；每次呼叫都會在 builder 目前位置建立一個獨立的形狀。

**Q: 儲存的 .docx 在 Microsoft Word 中開啟時，水平線會顯示嗎？**  
A: 當然會；水平線會以形狀的形式儲存在 .docx 檔案中，Word 會如同在產生的文件中一樣顯示它。

**Q: 如果在呼叫 `doc.Save(...)` 之前 `dataDir` 資料夾不存在，會發生什麼情況？**  
A: `doc.Save` 會拋出 `DirectoryNotFoundException`；請確保目標目錄已存在，或在儲存前以程式方式建立它。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}