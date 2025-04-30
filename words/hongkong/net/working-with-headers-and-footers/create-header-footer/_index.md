---
"description": "了解如何使用 Aspose.Words for .NET 在 Word 文件中新增和自訂頁首和頁尾。本逐步指南可確保專業的文件格式。"
"linktitle": "建立頁眉頁腳"
"second_title": "Aspose.Words文件處理API"
"title": "建立頁眉頁腳"
"url": "/zh-hant/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 建立頁眉頁腳

## 介紹

在文件中加入頁首和頁尾可以增強其專業性和可讀性。使用 Aspose.Words for .NET，您可以輕鬆地為 Word 文件建立和自訂頁首和頁尾。在本教程中，我們將逐步引導您完成整個過程，確保您可以無縫地實現這些功能。

## 先決條件

在開始之前，請確保您已具備以下條件：

- Aspose.Words for .NET：從下載並安裝 [下載連結](https://releases。aspose.com/words/net/).
- 開發環境：例如 Visual Studio，用於編寫和執行程式碼。
- C# 基礎：了解 C# 和 .NET 架構。
- 範例文檔：套用頁首和頁尾的範例文檔，或依照教學課程所示建立一個新文檔。

## 導入命名空間

首先，您需要匯入必要的命名空間來存取 Aspose.Words 類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## 步驟1：定義文檔目錄

定義儲存文檔的目錄。這有助於有效地管理路徑。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## 第 2 步：建立新文檔

建立新文件和 `DocumentBuilder` 以方便添加內容。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步驟3：設定頁面設定

設定頁面設定，包括第一頁是否有不同的頁首/頁尾。

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## 步驟 4：為第一頁新增頁眉

移動到第一頁的頁首部分並配置頁首文字。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## 步驟 5：新增主標題

移動到主標題部分並插入圖像和文字。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// 在頁首中插入圖片
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## 步驟 6：新增主頁尾

移至主要頁腳部分並建立一個表格來格式化頁腳內容。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// 新增頁碼
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## 步驟 7：新增內容和分頁符

移至文件末尾，新增分頁符，並建立具有不同頁面設定的新部分。

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## 步驟 8：複製上一節的頁首和頁尾

如果您想重複使用上一節的頁首和頁腳，請複製它們並套用必要的修改。

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## 結論

透過遵循這些步驟，您可以使用 Aspose.Words for .NET 在 Word 文件中有效地新增和自訂頁首和頁尾。這增強了文件的外觀和專業性，使其更具可讀性和吸引力。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？

Aspose.Words for .NET 是一個函式庫，可讓開發人員在 .NET 應用程式內以程式設計方式建立、編輯和轉換 Word 文件。

### 我可以在頁首或頁尾添加圖像嗎？

是的，您可以使用 `DocumentBuilder.InsertImage` 方法。

### 如何為第一頁設定不同的頁首和頁尾？

您可以使用 `DifferentFirstPageHeaderFooter` 的財產 `PageSetup` 班級。

### 在哪裡可以找到有關 Aspose.Words 的更多文件？

您可以找到有關 [Aspose.Words API 文件頁面](https://reference。aspose.com/words/net/).

### 是否支援 Aspose.Words？

是的，Aspose 透過其 [支援論壇](https://forum。aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}