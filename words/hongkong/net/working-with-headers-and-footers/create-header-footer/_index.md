---
title: 建立頁眉頁腳
linktitle: 建立頁眉頁腳
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中新增和自訂頁首和頁尾。本逐步指南可確保專業的文件格式設定。
weight: 10
url: /zh-hant/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立頁眉頁腳

## 介紹

在文件中新增頁首和頁尾可以增強文件的專業性和可讀性。使用 Aspose.Words for .NET，您可以輕鬆地為 Word 文件建立和自訂頁首和頁尾。在本教程中，我們將逐步引導您完成該過程，確保您可以無縫地實現這些功能。

## 先決條件

在開始之前，請確保您具備以下條件：

-  Aspose.Words for .NET：從以下位置下載並安裝[下載連結](https://releases.aspose.com/words/net/).
- 開發環境：例如 Visual Studio，用於編寫和執行程式碼。
- C#基礎：了解C#和.NET架構。
- 範例文檔：用於套用頁首和頁尾或建立新文檔的範例文檔，如教學課程所示。

## 導入命名空間

首先，您需要匯入必要的命名空間來存取 Aspose.Words 類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## 第 1 步：定義文檔目錄

定義儲存文檔的目錄。這有助於有效管理路徑。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## 第 2 步：建立新文檔

建立一個新文件和`DocumentBuilder`以方便添加內容。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步驟 3：設定頁面設定

設定頁面設定，包括首頁是否有不同的頁首/頁尾。

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## 步驟 4：為首頁新增頁眉

移至第一頁的標題部分並配置標題文字。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## 第 5 步：新增主標頭

移至主標題部分並插入圖像和文字。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

//將圖像插入標題中
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## 第 6 步：新增主頁腳

移至主頁腳部分並建立一個表格來格式化頁腳內容。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

//新增頁碼
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

## 第 7 步：新增內容和分頁符

移至文件末尾，新增分頁符，然後使用不同的頁面設定建立新部分。

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

如果您想重複使用上一節中的頁首和頁腳，請複製它們並套用必要的修改。

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

透過執行這些步驟，您可以使用 Aspose.Words for .NET 在 Word 文件中有效地新增和自訂頁首和頁尾。這增強了文件的外觀和專業性，使其更具可讀性和吸引力。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？

Aspose.Words for .NET 是一個函式庫，可讓開發人員在 .NET 應用程式中以程式設計方式建立、編輯和轉換 Word 文件。

### 我可以將圖像新增至頁首或頁尾嗎？

是的，您可以使用以下命令輕鬆地將圖像新增至頁首或頁尾`DocumentBuilder.InsertImage`方法。

### 如何為首頁設定不同的頁首和頁尾？

您可以使用以下指令為第一頁設定不同的頁首和頁尾`DifferentFirstPageHeaderFooter`的財產`PageSetup`班級。

### 在哪裡可以找到有關 Aspose.Words 的更多文件？

您可以在以下位置找到全面的文檔[Aspose.Words API 文件頁面](https://reference.aspose.com/words/net/).

### 是否支援 Aspose.Words？

是的，Aspose 透過他們的[支援論壇](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
