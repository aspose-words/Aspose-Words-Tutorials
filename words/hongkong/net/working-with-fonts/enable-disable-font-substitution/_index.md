---
title: 啟用禁用字體替換
linktitle: 啟用禁用字體替換
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中啟用或停用字體替換。確保您的文件在所有平台上看起來一致。
weight: 10
url: /zh-hant/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 啟用禁用字體替換

## 介紹

您是否曾經遇到過這樣的情況：您在 Word 文件中精心選擇的字體在另一台電腦上查看時被替換了？很煩吧？發生這種情況是由於字體替換，即係統以可用字體替換丟失字體的過程。但不用擔心！使用 Aspose.Words for .NET，您可以輕鬆管理和控製字體替換。在本教學中，我們將引導您完成在 Word 文件中啟用或停用字體替換的步驟，確保您的文件始終如您所願。

## 先決條件

在深入了解這些步驟之前，讓我們確保您擁有所需的一切：

-  Aspose.Words for .NET：下載最新版本[這裡](https://releases.aspose.com/words/net/).
- Visual Studio：任何支援 .NET 的版本。
- C# 基礎知識：這將幫助您遵循編碼範例。

## 導入命名空間

首先，請確保您已在專案中匯入了必要的命名空間。將這些添加到 C# 檔案的頂部：

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

現在，讓我們將流程分解為簡單、易於管理的步驟。

## 第 1 步：設定您的項目

首先，在 Visual Studio 中設定新專案並新增對 Aspose.Words for .NET 程式庫的參考。如果您還沒有下載，請從[阿斯普斯網站](https://releases.aspose.com/words/net/).

## 第 2 步：載入您的文檔

接下來，載入您要使用的文檔。操作方法如下：

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

代替`"YOUR DOCUMENT DIRECTORY"`與文檔目錄的實際路徑。此程式碼將文件載入到記憶體中，以便您可以對其進行操作。

## 步驟 3：配置字型設定

現在，讓我們建立一個`FontSettings`管理字型替換設定的物件：

```csharp
FontSettings fontSettings = new FontSettings();
```

## 步驟 4：設定預設字型替換

將預設字體替換設定為您選擇的字體。如果原始字體不可用，將使用此字體：

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

在此範例中，我們使用 Arial 作為預設字體。

## 第 5 步：停用字型資訊替換

若要停用字體資訊替換（這會阻止系統以可用字體取代遺失的字體），請使用以下程式碼：

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## 步驟 6：將字型設定套用到文檔

現在，將這些設定套用到您的文件：

```csharp
doc.FontSettings = fontSettings;
```

## 第 7 步：儲存您的文件

最後，儲存修改後的文件。您可以將其儲存為任何您喜歡的格式。對於本教程，我們將其另存為 PDF：

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## 結論

現在你就擁有了！透過執行以下步驟，您可以使用 Aspose.Words for .NET 輕鬆控制 Word 文件中的字型替換。這可以確保您的文件無論在何處查看，都保持其預期的外觀和感覺。

## 常見問題解答

### 我可以使用 Arial 以外的字體進行替換嗎？

絕對地！您可以透過變更字體名稱來指定係統上可用的任何字體`DefaultFontName`財產。

### 如果指定的預設字體不可用，會發生什麼情況？

如果預設字體不可用，Aspose.Words 將使用系統回退機制來尋找合適的替換字體。

### 禁用字體替換後可以再次啟用嗎？

是的，您可以切換`Enabled`的財產`FontInfoSubstitution`回到`true`如果您想再次啟用字體替換。

### 有沒有辦法檢查哪些字型被替換？

是的，Aspose.Words 提供了記錄和追蹤字體替換的方法，使您可以查看哪些字體被替換。

### 除了 DOCX 之外，我可以將此方法用於其他文件格式嗎？

確實！ Aspose.Words 支援各種格式，您可以將這些字體設定套用至任何支援的格式。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
