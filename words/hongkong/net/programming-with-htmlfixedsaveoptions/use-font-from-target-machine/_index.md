---
title: 使用目標機中的字體
linktitle: 使用目標機中的字體
second_title: Aspose.Words 文件處理 API
description: 了解如何透過 Aspose.Words for .NET 在 Word 文件中使用來自目標電腦的字體。請遵循我們的無縫字體集成分步指南。
weight: 10
url: /zh-hant/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用目標機中的字體

## 介紹

您準備好進入 Aspose.Words for .NET 的迷人世界了嗎？繫好安全帶，因為我們將帶您踏上字體神奇王國的旅程。今天，我們將重點放在處理 Word 文件時如何使用目標電腦上的字型。這項巧妙的功能可確保您的文件看起來完全符合您的預期，無論在何處查看。讓我們開始吧！

## 先決條件

在我們深入了解具體細節之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET 程式庫。如果您還沒有，您可以下載[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：您應該設定一個.NET開發環境，例如Visual Studio。
3. 使用文件：準備好一個 Word 文件以供測試。我們將使用名為「Bullet point with Alternative font.docx」的文件。

現在我們已經介紹了基礎知識，讓我們深入研究程式碼！

## 導入命名空間

首先，我們需要導入必要的名稱空間。這是我們專案的支柱，連接所有的點。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 第 1 步：載入 Word 文檔

我們教學的第一步是載入 Word 文件。這就是一切的開始。我們將使用`Document`Aspose.Words 程式庫中的類別可實現此目的。

### 步驟1.1：定義文檔路徑

讓我們先定義文檔目錄的路徑。這是您的 Word 文件所在的位置。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

### 步驟1.2：載入文檔

現在，我們使用以下命令來載入文檔`Document`班級。

```csharp
//載入Word文檔
Document doc = new Document(dataDir + "Bullet points with alternative font.docx");
```

## 第 2 步：配置儲存選項

接下來，我們需要配置保存選項。此步驟至關重要，因為它確保文件中使用的字體是來自目標電腦的字體。

我們將建立一個實例`HtmlFixedSaveOptions`並設定`UseTargetMachineFonts`財產給`true`.

```csharp
//使用「使用目標電腦中的字型」功能配置備份選項
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions
{
    UseTargetMachineFonts = true
};
```

## 第 3 步：儲存文檔

最後，我們將文件儲存為固定的 HTML 檔案。這就是魔法發生的地方！

我們將使用`Save`使用配置的儲存選項儲存文件的方法。

```csharp
//將文檔轉換為固定 HTML
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
```

## 第 4 步：驗證輸出

最後但並非最不重要的一點是，驗證輸出始終是個好主意。開啟已儲存的 HTML 檔案並檢查目標電腦是否正確套用了字型。

導航到保存 HTML 文件的目錄並在 Web 瀏覽器中開啟它。

```csharp
//透過開啟 HTML 文件驗證輸出
System.Diagnostics.Process.Start(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html");
```

現在你就擁有了！您已使用 Aspose.Words for .NET 在 Word 文件中成功使用了目標電腦中的字型。

## 結論

使用目標電腦中的字型可確保您的 Word 文件看起來一致且專業，無論在何處查看。 Aspose.Words for .NET 讓這個過程簡單而有效率。透過學習本教學課程，您已了解如何載入文件、配置儲存選項以及使用所需的字型設定儲存文件。快樂編碼！

## 常見問題解答

### 我可以將此方法用於其他文件格式嗎？
是的，Aspose.Words for .NET 支援各種文件格式，您可以為不同的格式配置類似的儲存選項。

### 如果目標機器沒有所需的字體怎麼辦？
如果目標電腦沒有所需的字體，則文件可能無法如預期般呈現。必要時嵌入字體總是一個好主意。

### 如何在文件中嵌入字體？
嵌入字體可以使用`FontSettings`Aspose.Words for .NET 中的類別。請參閱[文件](https://reference.aspose.com/words/net/)了解更多詳情。

### 有沒有辦法在儲存之前預覽文件？
是的，您可以使用`DocumentRenderer`類別在儲存之前預覽文件。查看 Aspose.Words for .NET[文件](https://reference.aspose.com/words/net/)了解更多。

### 我可以進一步自訂 HTML 輸出嗎？
絕對地！這`HtmlFixedSaveOptions`類別提供了各種屬性來自訂 HTML 輸出。探索[文件](https://reference.aspose.com/words/net/)對於所有可用的選項。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
