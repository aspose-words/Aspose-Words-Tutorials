---
title: 保留舊控製字符
linktitle: 保留舊控製字符
second_title: Aspose.Words 文件處理 API
description: 透過此逐步指南，了解如何使用 Aspose.Words for .NET 保留 Word 文件中的舊控製字元。
weight: 10
url: /zh-hant/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 保留舊控製字符

## 介紹

您是否曾經對 Word 文件中那些奇怪的、看不見的控製字元感到困惑？它們就像微小的、隱藏的小妖怪，可能會擾亂格式和功能。幸運的是，Aspose.Words for .NET 提供了一個方便的功能，可以在儲存文件時保持這些舊控製字元的完整性。在本教學中，我們將深入探討如何使用 Aspose.Words for .NET 管理這些控製字元。我們將逐步分解它，確保您掌握整個過程中的每個細節。準備好開始了嗎？讓我們深入了解吧！

## 先決條件

在我們開始之前，請確保您具備以下條件：

1.  Aspose.Words for .NET：從以下位址下載並安裝[這裡](https://releases.aspose.com/words/net/).
2. 有效的 Aspose 許可證：您可以獲得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).
3. 開發環境：Visual Studio 或任何其他支援.NET 的IDE。
4. C# 基礎知識：熟悉 C# 程式語言將會有所幫助。

## 導入命名空間

在編寫程式碼之前，您需要匯入必要的名稱空間。將以下行新增至 C# 檔案的頂部：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 第 1 步：設定您的項目

首先，您需要在 Visual Studio（或您首選的 IDE）中設定專案。 

1. 建立新的 C# 專案：開啟 Visual Studio 並建立新的 C# 控制台應用程式專案。
2. 安裝 Aspose.Words for .NET：使用 NuGet Package Manager 安裝 Aspose.Words for .NET。在解決方案資源管理器中右鍵單擊您的項目，選擇“管理 NuGet 套件”，搜尋“Aspose.Words”並安裝它。

## 第 2 步：載入您的文檔

接下來，您將載入包含舊控製字元的 Word 文件。

1. 指定文檔路徑：設定文檔目錄的路徑。
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. 載入文檔：使用`Document`類別來載入您的文件。

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## 步驟 3：配置儲存選項

現在，讓我們配置儲存選項以保持舊控製字元完整。

1. 建立保存選項：初始化一個實例`OoxmlSaveOptions`並設定`KeepLegacyControlChars`財產給`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## 步驟 4：儲存文檔

最後，使用配置的儲存選項儲存文件。

1. 儲存文件：使用`Save`的方法`Document`類別以使用指定的儲存選項儲存文件。

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## 結論

現在你就擁有了！透過執行這些步驟，您可以確保在 Aspose.Words for .NET 中處理 Word 文件時保留舊控製字元。此功能可以成為救星，尤其是在處理控製字元起著至關重要作用的複雜文件時。 

## 常見問題解答

### 什麼是遺留控製字元？

舊控製字元是舊文件中用於控制格式和佈局的非列印字元。

### 我可以刪除這些控製字元而不是保留它們嗎？

是的，如果需要，您可以使用 Aspose.Words for .NET 刪除或取代這些字元。

### 此功能在 Aspose.Words for .NET 的所有版本中都可用嗎？

此功能在最新版本中可用。確保使用最新版本來存取所有功能。

### 我需要許可證才能使用 Aspose.Words for .NET 嗎？

是的，您需要有效的許可證。您可以獲得用於評估目的的臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件？

你可以找到詳細的文檔[這裡](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
