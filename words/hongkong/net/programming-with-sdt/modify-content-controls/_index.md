---
"description": "了解如何使用 Aspose.Words for .NET 修改 Word 中的結構化文件標籤。逐步更新文字、下拉式選單和圖像。"
"linktitle": "修改內容控件"
"second_title": "Aspose.Words文件處理API"
"title": "修改內容控件"
"url": "/zh-hant/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 修改內容控件

## 介紹

如果您曾經使用過 Word 文件並需要使用 Aspose.Words for .NET 修改結構化內容控制項（如純文字、下拉清單或圖片），那麼您來對地方了！結構化文件標籤 (SDT) 是強大的工具，可以使文件自動化更容易、更靈活。在本教程中，我們將深入探討如何修改這些 SDT 以滿足您的需求。無論您是更新文字、更改下拉選項還是交換圖像，本指南都會逐步引導您完成整個過程。

## 先決條件

在我們深入討論修改內容控制項的細節之前，請確保您具備以下條件：

1. 已安裝 Aspose.Words for .NET：請確定您已安裝 Aspose.Words 程式庫。如果沒有，你可以 [點此下載](https://releases。aspose.com/words/net/).

2. C# 基礎知識：本教學假設您熟悉基本的 C# 程式設計概念。

3. .NET 開發環境：您應該有一個像 Visual Studio 這樣的 IDE 來執行 .NET 應用程式。

4. 範例文件：我們將使用包含各種類型的 SDT 的範例 Word 文件。您可以使用範例中的那個或創建自己的。

5. 訪問 Aspose 文件：有關更多詳細信息，請查看 [Aspose.Words 文檔](https://reference。aspose.com/words/net/).

## 導入命名空間

要開始使用 Aspose.Words，您需要將相關的命名空間匯入到您的 C# 專案中。以下是操作方法：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

這些命名空間將使您能夠存取操作 Word 文件中的結構化文件標籤所需的類別和方法。

## 步驟 1：設定文檔路徑

在進行任何變更之前，您需要指定文件的路徑。代替 `"YOUR DOCUMENT DIRECTORY"` 使用您的文件儲存的實際路徑。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## 步驟 2：循環遍歷結構化文件標籤

要修改 SDT，首先需要循環遍歷文件中的所有 SDT。這是使用 `GetChildNodes` 取得所有類型的節點的方法 `StructuredDocumentTag`。

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // 根據類型修改 SDT
}
```

## 步驟3：修改純文字SDT

如果SDT是純文字類型，則可以取代其內容。首先，清除現有內容，然後新增文字。

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

解釋：這裡， `RemoveAllChildren()` 清除 SDT 的現有內容。然後我們創建一個新的 `Paragraph` 和 `Run` 物件來插入新文字。

## 步驟 4：修改下拉式清單 SDT

對於下拉清單 SDT，您可以透過存取 `ListItems` 收藏。在這裡，我們選擇清單中的第三項。

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

說明：此程式碼片段從下拉清單中選擇索引 2 處的項目（第三項）。根據您的需求調整索引。

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

說明：此程式碼檢查形狀是否包含圖像，然後用位於的新圖像取代它 `ImagesDir`。

## 步驟6：儲存修改後的文檔

完成所有必要的變更後，請使用新名稱儲存修改後的文檔，以保持原始文檔的完整性。

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

說明：這將使用新文件名保存文檔，以便您可以輕鬆地將其與原始文檔區分開來。

## 結論

一旦您了解所涉及的步驟，使用 Aspose.Words for .NET 修改 Word 文件中的內容控制項就很簡單。無論您是更新文字、更改下拉選擇還是交換圖像，Aspose.Words 都為這些任務提供了強大的 API。透過遵循本教學課程，您可以有效地管理和自訂文件的結構化內容控件，使您的文件更加動態並更適合您的需求。

## 常見問題解答

1. 什麼是結構化文件標籤 (SDT)？

SDT 是 Word 文件中的元素，有助於管理和格式化文件內容，如文字方塊、下拉清單或圖片。

2. 如何為 SDT 新增新的下拉項目？

若要新增項目，請使用 `ListItems` 屬性並附加新的 `SdtListItem` 到收藏夾。

3. 我可以使用 Aspose.Words 從文件中刪除 SDT 嗎？

是的，您可以透過存取文件的節點並刪除所需的 SDT 來刪除 SDT。

4. 如何處理嵌套在其他元素中的 SDT？

使用 `GetChildNodes` 具有適當參數的方法來存取嵌套的 SDT。

5. 如果我需要修改的SDT在文件中不可見，我該怎麼辦？

確保 SDT 未被隱藏或保護。檢查文件設定並確保您的程式碼正確針對 SDT 類型。


### 使用 Aspose.Words for .NET 修改內容控制項的範例原始程式碼 

```csharp
// 文檔目錄的路徑 
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

就是這樣！您已成功使用 Aspose.Words for .NET 修改了 Word 文件中的不同類型的內容控制項。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}