---
title: 更新上次儲存時間屬性
linktitle: 更新上次儲存時間屬性
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 更新 Word 文件中的上次儲存時間屬性。請遵循我們詳細的逐步指南。
weight: 10
url: /zh-hant/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 更新上次儲存時間屬性

## 介紹

有沒有想過如何以程式設計方式追蹤 Word 文件中上次儲存的時間屬性？如果您正在處理多個文件並需要維護其元數據，則更新上次儲存時間屬性會非常方便。今天，我將使用 Aspose.Words for .NET 引導您完成此過程。所以，繫好安全帶，讓我們開始吧！

## 先決條件

在我們開始逐步指南之前，您需要準備一些東西：

1.  Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET。如果你還沒有，你可以[在這裡下載](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio等開發環境。
3. C# 基礎知識：了解 C# 程式設計的基礎知識將會有所幫助。

## 導入命名空間

首先，請確保將必要的命名空間匯入到您的專案中。這將允許您存取操作 Word 文件所需的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

現在，讓我們將該過程分解為簡單的步驟。每個步驟將引導您完成更新 Word 文件中上次儲存的時間屬性的過程。

## 第 1 步：設定您的文件目錄

首先，您需要指定文檔目錄的路徑。這是現有文件的儲存位置以及更新的文件的保存位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與目錄的實際路徑。

## 第 2 步：載入 Word 文檔

接下來，載入要更新的 Word 文件。您可以透過建立一個實例來做到這一點`Document`類並傳遞文檔的路徑。

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

確保該文件名為`Document.docx`存在於指定目錄中。

## 步驟 3：配置儲存選項

現在，建立一個實例`OoxmlSaveOptions`班級。此類別可讓您指定以 Office Open XML (OOXML) 格式儲存文件的選項。在這裡，您將設定`UpdateLastSavedTimeProperty`到`true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

這告訴 Aspose.Words 更新文件的上次儲存時間屬性。

## 步驟 4：儲存更新後的文檔

最後，使用以下命令儲存文檔`Save`的方法`Document`類，傳入要保存更新文件的路徑和儲存選項。

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

這將使用更新的上次儲存時間屬性來儲存文件。

## 結論

現在你就擁有了！透過執行下列步驟，您可以使用 Aspose.Words for .NET 輕鬆更新 Word 文件的上次儲存時間屬性。這對於維護文件中準確的元資料特別有用，這對於文件管理系統和各種其他應用至關重要。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，用於在 .NET 應用程式中建立、編輯和轉換 Word 文件。

### 為什麼要更新上次儲存的時間屬性？
更新上次保存的時間屬性有助於維護準確的元數據，這對於文件追蹤和管理至關重要。

### 我可以使用 Aspose.Words for .NET 更新其他屬性嗎？
是的，Aspose.Words for .NET 可讓您更新各種文件屬性，例如標題、作者和主題。

### Aspose.Words for .NET 是免費的嗎？
 Aspose.Words for .NET 提供免費試用版，但要獲得完整功能，需要授權。您可以獲得許可證[這裡](https://purchase.aspose.com/buy).

### 在哪裡可以找到更多關於 Aspose.Words for .NET 的教學？
您可以找到更多教學和文檔[這裡](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
