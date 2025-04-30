---
"description": "了解如何使用 Aspose.Words for .NET 鎖定 Word 文件中形狀的縱橫比。按照本逐步指南，保持圖像和形狀的比例。"
"linktitle": "長寬比已鎖定"
"second_title": "Aspose.Words文件處理API"
"title": "長寬比已鎖定"
"url": "/zh-hant/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 長寬比已鎖定

## 介紹

您是否想過如何在 Word 文件中保持圖像和形狀的完美比例？有時，您需要確保影像和形狀在調整大小時不會變形。這時鎖定縱橫比就派上用場了。在本教學中，我們將探討如何使用 Aspose.Words for .NET 設定 Word 文件中形狀的縱橫比。我們將把它分解為易於遵循的步驟，確保您可以自信地將這些技能應用到您的專案中。

## 先決條件

在深入研究程式碼之前，讓我們先了解一下入門所需的內容：

- Aspose.Words for .NET 函式庫：您需要安裝 Aspose.Words for .NET。如果你還沒有，你可以 [點此下載](https://releases。aspose.com/words/net/).
- 開發環境：確保您已設定 .NET 開發環境。 Visual Studio 是個受歡迎的選擇。
- C# 基礎知識：熟悉 C# 程式設計將會有所幫助。

## 導入命名空間

首先，讓我們導入必要的命名空間。這些命名空間將使我們能夠存取處理 Word 文件和形狀所需的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 步驟 1：設定文檔目錄

在開始處理形狀之前，我們需要設定一個儲存文件的目錄。為了簡單起見，我們將使用佔位符 `YOUR DOCUMENT DIRECTORY`。將其替換為文檔目錄的實際路徑。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：建立新文檔

接下來，我們將使用 Aspose.Words 建立一個新的 Word 文件。該文件將作為我們添加形狀和圖像的畫布。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在這裡，我們創建一個 `Document` 類別並使用 `DocumentBuilder` 幫助我們建立文件內容。

## 步驟3：插入圖片

現在，讓我們將圖像插入到我們的文件中。我們將使用 `InsertImage` 方法 `DocumentBuilder` 班級。確保在指定的目錄中有一個圖像。

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

代替 `dataDir + "Transparent background logo.png"` 以及您的圖像檔案的路徑。

## 步驟 4：鎖定長寬比

一旦插入圖像，我們就可以鎖定其縱橫比。鎖定縱橫比可確保影像的比例在調整大小時保持不變。

```csharp
shape.AspectRatioLocked = true;
```

環境 `AspectRatioLocked` 到 `true` 確保影像保持其原始縱橫比。

## 步驟5：儲存文檔

最後，我們將文檔儲存到指定的目錄。此步驟將我們所做的所有變更寫入文件檔案。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 結論

恭喜！您已成功學習如何使用 Aspose.Words for .NET 設定 Word 文件中形狀的縱橫比。透過遵循這些步驟，您可以確保您的圖像和形狀保持其比例，使您的文件看起來專業且精緻。請隨意嘗試不同的圖像和形狀，看看縱橫比鎖定功能在各種場景下如何運作。

## 常見問題解答

### 鎖定寬高比後還能解鎖嗎？
是的，您可以透過設定解鎖寬高比 `shape。AspectRatioLocked = false`.

### 如果我調整鎖定縱橫比的圖像大小會發生什麼？
影像將按比例調整大小，保持其原始的寬高比。

### 除了圖像之外，我可以將其應用於其他形狀嗎？
絕對地！縱橫比鎖定功能可套用於任何形狀，包括矩形、圓形等。

### Aspose.Words for .NET 是否與 .NET Core 相容？
是的，Aspose.Words for .NET 同時支援 .NET Framework 和 .NET Core。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件？
您可以找到全面的文檔 [這裡](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}