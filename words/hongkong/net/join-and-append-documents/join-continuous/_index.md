---
title: 加入持續
linktitle: 加入持續
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 無縫連接兩個 Word 文件。請依照我們的逐步指南進行順利、有效率的文件合併。
weight: 10
url: /zh-hant/net/join-and-append-documents/join-continuous/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 加入持續

## 介紹

您是否希望將兩個 Word 文件無縫地合併為一個而不出現任何中斷？ Aspose.Words for .NET 提供了一種透過使用連續分節符功能來實現此目的的絕佳方法。本教學將逐步引導您完成整個過程，確保您可以輕鬆加入文檔，沒有任何麻煩。讓我們深入了解吧！

## 先決條件

在開始之前，讓我們確保您擁有所需的一切：

-  Aspose.Words for .NET：如果您還沒有安裝，請下載並安裝[Aspose.Words for .NET](https://releases.aspose.com/words/net/).
- 開發環境：您可以使用 Visual Studio 或任何其他 .NET 開發環境。
- 範例文件：準備好兩個要合併的 Word 文件。

## 導入命名空間

若要使用 Aspose.Words for .NET，您需要在專案中匯入必要的命名空間。操作方法如下：

```csharp
using Aspose.Words;
```

現在，為了清楚起見，讓我們將該範例分解為多個步驟。

## 第 1 步：設定您的文件目錄

首先，我們需要設定儲存文檔的目錄。這將允許我們的程式碼找到我們想要合併的檔案。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與儲存文檔的實際路徑。

## 第 2 步：載入來源文檔和目標文檔

接下來，我們將來源文檔和目標文檔載入到我們的程式中。這些是您要合併的兩個文件。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

確保檔案名稱和路徑與您要使用的實際檔案相符。

## 步驟 3：將“部分開始”設定為“連續”

為了使來源文件的內容立即出現在目標文件之後，我們需要設定`SectionStart`來源文檔中第一部分的屬性`Continuous`.

```csharp
//使文件直接出現在目標文件內容之後。
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

這可確保合併文件時文件之間不會出現中斷。

## 第 4 步：附加來源文檔

現在，我們將來源文件附加到目標文件。此步驟可確保將來源文件中的內容新增至目標文件的末端。

```csharp
//使用來源文件中找到的原始樣式附加來源文件。
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用`ImportFormatMode.KeepSourceFormatting`確保來源文檔的格式保留在最終合併的文檔中。

## 步驟5：儲存合併的文檔

最後，我們將合併後的文檔儲存到指定的目錄中。這樣就完成了加入文件的過程。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.JoinContinuous.docx");
```

確保路徑和檔案名稱符合您的需求。

## 結論

現在你就擁有了！只需幾行程式碼，您就可以使用 Aspose.Words for .NET 成功將兩個 Word 文件合併為一個連續文件。這個過程不僅簡單而且高效，確保您的文件保留其原始格式。

## 常見問題解答

### 我可以合併兩個以上的文檔嗎？
是的，您可以透過載入其他文件並按順序附加它們來重複合併多個文件的過程。

### 原始格式會保留嗎？
是的，使用`ImportFormatMode.KeepSourceFormatting`確保保留來源文件的格式。

### Aspose.Words for .NET 與 .NET Core 相容嗎？
是的，Aspose.Words for .NET 與 .NET Framework 和 .NET Core 也相容。

### 我可以合併具有不同頁面設定的文件嗎？
是的，但您可能需要調整頁面設定屬性以確保無縫合併。

### 如果遇到問題，我可以在哪裡獲得支援？
您可以從 Aspose 社群論壇獲得支持[這裡](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
