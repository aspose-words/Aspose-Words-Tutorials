---
title: 修改內容控件
linktitle: 修改內容控件
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 修改 Word 中的結構化文件標籤。逐步更新文字、下拉式選單和圖像。
weight: 10
url: /zh-hant/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 修改內容控件

## 介紹

如果您曾經使用過 Word 文檔，並且需要使用 Aspose.Words for .NET 修改結構化內容控制項（例如純文字、下拉清單或圖片），那麼您來對地方了！結構化文件標籤 (SDT) 是功能強大的工具，可讓文件自動化變得更輕鬆、更靈活。在本教程中，我們將深入探討如何修改這些 SDT 以滿足您的需求。無論您是更新文字、更改下拉選項還是更換圖像，本指南都將引導您逐步完成該過程。

## 先決條件

在我們深入討論修改內容控制項的細節之前，請確保您具備以下條件：

1. 已安裝 Aspose.Words for .NET：確保已安裝 Aspose.Words 程式庫。如果沒有，您可以[在這裡下載](https://releases.aspose.com/words/net/).

2. C# 基礎知識：本教學假設您熟悉基本的 C# 程式設計概念。

3. .NET 開發環境：您應該有一個像 Visual Studio 這樣的 IDE，用於執行 .NET 應用程式。

4. 範例文件：我們將使用包含各種類型的 SDT 的範例 Word 文件。您可以使用範例中的範例或建立自己的範例。

5. 訪問 Aspose 文件：有關更多詳細信息，請查看[Aspose.Words 文檔](https://reference.aspose.com/words/net/).

## 導入命名空間

要開始使用 Aspose.Words，您需要將相關命名空間匯入到您的 C# 專案中。操作方法如下：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

這些命名空間將使您能夠存取操作 Word 文件中的結構化文件標籤所需的類別和方法。

## 第 1 步：設定文檔路徑

在進行任何變更之前，您需要指定文件的路徑。代替`"YOUR DOCUMENT DIRECTORY"`與儲存文檔的實際路徑。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## 第 2 步：循環遍歷結構化文件標籤

要修改SDT，首先需要循環遍歷文件中的所有SDT。這是使用以下方法完成的`GetChildNodes`取得類型的所有節點的方法`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    //根據 SDT 的類型修改 SDT
}
```

## 步驟 3：修改純文字 SDT

如果SDT是純文字類型，可以取代其內容。首先，清除現有內容，然後新增文字。

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

說明： 在這裡，`RemoveAllChildren()`清除 SDT 的現有內容。然後我們創建一個新的`Paragraph`和`Run`物件插入新文字。

## 步驟 4：修改下拉式清單 SDT

對於下拉清單 SDT，您可以透過造訪來變更所選項目`ListItems`收藏。在這裡，我們選擇清單中的第三項。

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

說明：此程式碼片段從下拉清單中選擇索引 2 處的項目（第三個項目）。根據您的需求調整索引。

## 步驟5：修改圖片SDT

若要更新圖片 SDT 中的影像，您可以用新影像取代現有影像。

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

說明：此程式碼檢查形狀是否包含圖像，然後將其替換為位於`ImagesDir`.

## 步驟 6：儲存修改後的文檔

進行所有必要的變更後，使用新名稱儲存修改後的文檔，以保持原始文檔完整。

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

說明：這會使用新文件名保存文檔，以便您可以輕鬆地將其與原始文件區分開來。

## 結論

一旦您了解了所涉及的步驟，使用 Aspose.Words for .NET 修改 Word 文件中的內容控制項就變得非常簡單。無論您是更新文字、更改下拉選項還是交換圖像，Aspose.Words 都為這些任務提供了強大的 API。透過遵循本教程，您可以有效地管理和自訂文件的結構化內容控件，使您的文件更加動態並根據您的需求進行自訂。

## 常見問題解答

1. 什麼是結構化文件標籤 (SDT)？

SDT 是 Word 文件中的元素，可協助管理和格式化文件內容，例如文字方塊、下拉清單或圖片。

2. 如何為 SDT 新增新的下拉項目？

若要新增項目，請使用`ListItems`屬性並附加一個新的`SdtListItem`到收藏。

3. 我可以使用 Aspose.Words 從文件中刪除 SDT 嗎？

是的，您可以透過存取文件的節點並刪除所需的 SDT 來刪除 SDT。

4. 如何處理嵌套在其他元素中的 SDT？

使用`GetChildNodes`具有適當參數的方法來存取嵌套 SDT。

5. 如果我需要修改的SDT在文件中不可見怎麼辦？

確保 SDT 未被隱藏或保護。檢查文件設定並確保您的程式碼正確定位 SDT 類型。


### 使用 Aspose.Words for .NET 修改內容控制項的範例原始程式碼 

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

就是這樣！您已使用 Aspose.Words for .NET 成功修改了 Word 文件中不同類型的內容控制項。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
