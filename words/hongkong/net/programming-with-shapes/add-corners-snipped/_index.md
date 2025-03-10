---
title: 添加剪掉的角
linktitle: 添加剪掉的角
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將剪角形狀新增至 Word 文件。本逐步指南可確保您輕鬆增強文件。
weight: 10
url: /zh-hant/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 添加剪掉的角

## 介紹

在 Word 文件中新增自訂形狀可以是一種有趣且視覺吸引力的方式，可以突出顯示重要資訊或為內容添加一點風格。在本教學中，我們將深入探討如何使用 Aspose.Words for .NET 將「剪角」形狀插入到 Word 文件中。本指南將引導您完成每一步，確保您可以像專業人士一樣輕鬆添加這些形狀並自訂您的文件。

## 先決條件

在我們開始編寫程式碼之前，讓我們確保您擁有開始使用所需的一切：

1.  Aspose.Words for .NET：如果您還沒有下載最新版本，請從[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
2. 開發環境：設定您的開發環境。 Visual Studio 是一個受歡迎的選擇，但您可以使用任何支援 .NET 的 IDE。
3. 許可證：如果您只是嘗試，可以使用[免費試用](https://releases.aspose.com/)或得到一個[臨時執照](https://purchase.aspose.com/temporary-license/)解鎖全部功能。
4. 對 C# 的基本了解：熟悉 C# 程式設計將有助於您理解範例。

## 導入命名空間

在開始使用 Aspose.Words for .NET 之前，我們需要匯入必要的命名空間。將這些添加到 C# 檔案的頂部：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

現在，讓我們將新增「剪角」形狀的過程分解為多個步驟。嚴格遵循這些步驟以確保一切順利進行。

## 第 1 步：初始化 Document 和 DocumentBuilder

我們需要做的第一件事是建立一個新文件並初始化`DocumentBuilder`目的。這個建構器將幫助我們為文件添加內容。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在此步驟中，我們已經設定了文件和建構器。想想`DocumentBuilder`作為您的數位筆，隨時可以在 Word 文件中書寫和繪圖。

## 步驟2：插入角落剪斷的形狀

接下來，我們將使用`DocumentBuilder`插入“剪角”形狀。這種形狀類型是在 Aspose.Words 中預先定義的，並且可以透過一行程式碼輕鬆插入。

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

在這裡，我們指定形狀類型及其尺寸 (50x50)。想像一下，您正在文件上貼上一張剪得完美的小角貼紙。 

## 第 3 步：定義符合要求的保存選項

在儲存文件之前，我們需要定義儲存選項以確保我們的文件符合特定標準。我們將使用`OoxmlSaveOptions`為此類。

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

這些儲存選項可確保我們的文件符合 ISO/IEC 29500:2008 標準，這對於相容性和文件壽命至關重要。

## 步驟 4：儲存文檔

最後，我們使用先前定義的儲存選項將文件儲存到指定目錄。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

就像這樣，您的文件現在包含一個自訂的「剪角」形狀，並使用必要的合規性選項進行儲存。

## 結論

給你了！使用 Aspose.Words for .NET 將自訂形狀新增至 Word 文件非常簡單，並且可以大幅增強文件的視覺吸引力。透過執行以下步驟，您可以輕鬆插入「剪角」形狀並確保您的文件符合所需的標準。快樂編碼！

## 常見問題解答

### 我可以自訂“剪角”形狀的尺寸嗎？
是的，您可以透過更改尺寸來調整尺寸`InsertShape`方法。

### 是否可以新增其他類型的形狀？
絕對地！ Aspose.Words 支援各種形狀。只需更改`ShapeType`到你想要的形狀。

### 我需要許可證才能使用 Aspose.Words 嗎？
雖然您可以使用免費試用版或臨時許可證，但需要完整許可證才能不受限制地使用。

### 如何進一步設計形狀？
您可以使用 Aspose.Words 提供的其他屬性和方法來自訂形狀的外觀和行為。

### Aspose.Words 與其他格式相容嗎？
是的，Aspose.Words 支援多種文件格式，包括 DOCX、PDF、HTML 等。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
