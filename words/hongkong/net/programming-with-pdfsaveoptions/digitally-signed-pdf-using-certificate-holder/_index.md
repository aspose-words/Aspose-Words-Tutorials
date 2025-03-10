---
title: 使用憑證持有者將數位簽章新增至 PDF
linktitle: 使用憑證持有者將數位簽章新增至 PDF
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 透過數位簽章保護您的 PDF 檔案。請按照此逐步指南輕鬆將數位簽章新增至您的 PDF。
weight: 10
url: /zh-hant/net/programming-with-pdfsaveoptions/digitally-signed-pdf-using-certificate-holder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用憑證持有者將數位簽章新增至 PDF

## 介紹

您是否想知道如何使用數位簽章來保護您的 PDF 文件？嗯，您來對地方了！數位簽章是手寫簽名的現代版本，提供了一種驗證數位文件的真實性和完整性的方法。在本教學中，我們將向您展示如何使用 Aspose.Words for .NET 將數位簽章新增至 PDF。我們將介紹從設定環境到逐步執行程式碼的所有內容。閱讀本指南後，您將擁有安全可靠的數位簽章 PDF。

## 先決條件

在我們開始之前，您需要準備一些東西：

1.  Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET。您可以從[阿斯普斯網站](https://releases.aspose.com/words/net/).
2. 證書文件：您需要 .pfx 證書文件來簽署 PDF。如果您沒有，您可以建立自簽名憑證用於測試目的。
3. Visual Studio：本教學假設您使用 Visual Studio 作為開發環境。
4. C# 基礎知識：熟悉 C# 和 .NET 程式設計至關重要。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這些對於存取文件操作和數位簽章所需的類別和方法至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
```

讓我們將這個過程分解為簡單、易於管理的步驟。

## 第 1 步：設定您的項目

在 Visual Studio 中建立一個新的 C# 專案。新增對 Aspose.Words for .NET 的參考。您可以透過 NuGet 套件管理器搜尋“Aspose.Words”並安裝它來執行此操作。

## 第 2 步：載入或建立文檔

您需要簽署一份文件。您可以載入現有文件或建立新文件。在本教程中，我們將建立一個新文件並添加一些範例文字。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//在文件中添加一些文字。
builder.Writeln("Test Signed PDF.");
```

## 步驟 3：指定數位簽名詳細信息

現在，是時候設定數位簽名詳細資料了。您需要指定 .pfx 憑證檔案的路徑、簽章原因、位置和簽章日期。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DigitalSignatureDetails = new PdfDigitalSignatureDetails(
        CertificateHolder.Create(dataDir + "morzal.pfx", "your_password"), "reason", "location",
        DateTime.Now)
};
```

代替`"your_password"`使用 .pfx 檔案的密碼。

## 步驟 4：將文件儲存為經過數位簽署的 PDF

最後，將文件儲存為具有數位簽章的 PDF。

```csharp
doc.Save(dataDir + "DigitallySignedPdfUsingCertificateHolder.pdf", saveOptions);
```

就是這樣！您的文件現已簽名並儲存為 PDF。

## 結論

數位簽章是確保文件完整性和真實性的強大工具。透過 Aspose.Words for .NET，為 PDF 檔案添加數位簽章既簡單又有效率。透過遵循此逐步指南，您可以保護您的 PDF 文件並讓收件人放心地了解其真實性。快樂編碼！

## 常見問題解答

### 什麼是數位簽章？
數位簽名是一種電子形式的簽名，用於驗證數位文件的真實性和完整性。

### 我需要證書來添加數位簽名嗎？
是的，您需要 .pfx 憑證檔案才能將數位簽章新增至 PDF。

### 我可以建立自簽名憑證用於測試嗎？
是的，您可以建立自簽名憑證用於測試目的。但是，對於生產用途，建議從受信任的憑證授權單位取得憑證。

### Aspose.Words for .NET 是免費的嗎？
 Aspose.Words for .NET 是一個商業產品，但您可以從[阿斯普斯網站](https://releases.aspose.com/).

### 我可以使用 Aspose.Words for .NET 簽署其他類型的文件嗎？
是的，Aspose.Words for .NET 可用於簽署各種類型的文檔，而不僅僅是 PDF。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
