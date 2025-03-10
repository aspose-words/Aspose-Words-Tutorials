---
title: 建立並簽署新的簽名行
linktitle: 建立並簽署新的簽名行
second_title: Aspose.Words 文件處理 API
description: 透過此逐步教學課程，了解如何使用 Aspose.Words for .NET 在 Word 文件中建立簽名行並對其進行數位簽章。非常適合文件自動化。
weight: 10
url: /zh-hant/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立並簽署新的簽名行

## 介紹

嘿！因此，您有一個 Word 文檔，需要新增簽名行，然後進行數位簽章。聽起來很棘手？一點也不！透過 Aspose.Words for .NET，您只需幾行程式碼即可無縫實現此目的。在本教程中，我們將引導您完成從設定環境到使用閃亮的新簽名保存文件的整個過程。準備好？讓我們深入了解吧！

## 先決條件

在我們進入程式碼之前，讓我們確保您擁有所需的一切：
1.  Aspose.Words for .NET - 你可以[在這裡下載](https://releases.aspose.com/words/net/).
2. 強烈推薦 .NET 開發環境 - Visual Studio。
3. 要簽署的文件 - 建立一個簡單的 Word 文件或使用現有文件。
4. 證書文件 - 數位簽名需要該文件。您可以使用`.pfx`文件。
5. 簽名行圖像 - （可選）簽名的圖像檔案。

## 導入命名空間

首先，我們需要導入必要的名稱空間。此步驟至關重要，因為它設定了使用 Aspose.Words 功能的環境。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## 第 1 步：設定文檔目錄

每個專案都需要一個好的開始。讓我們設定文檔目錄的路徑。這是保存和檢索您的文件的地方。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：建立新文檔

現在，讓我們使用 Aspose.Words 建立一個新的 Word 文件。這將是我們添加簽名行的畫布。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 第 3 步：插入簽名行

這就是奇蹟發生的地方。我們使用以下命令在文件中插入簽名行`DocumentBuilder`班級。

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## 步驟 4：儲存帶有簽名行的文檔

簽名行到位後，我們需要儲存文件。這是我們繼續簽署之前的中間步驟。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## 第 5 步：設定簽名選項

現在，讓我們設定用於簽署文件的選項。這包括指定簽名行 ID 和要使用的映像。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## 第6步：載入證書

數位簽章需要憑證。在這裡，我們載入將用於簽署文件的證書文件。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 第 7 步：簽署文件

這是最後一步。我們使用`DigitalSignatureUtil`類來簽署文件。已簽署的文件將以新名稱儲存。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## 結論

現在你就擁有了！透過這些步驟，您已成功建立了一個新的 Word 文檔，新增了簽名行，並使用 Aspose.Words for .NET 對其進行了數位簽章。它是一個強大的工具，使文件自動化變得輕而易舉。無論您處理合約、協議或任何正式文檔，此方法都可確保它們經過安全簽署和驗證。

## 常見問題解答

### 我可以使用其他圖像格式作為簽名行嗎？
是的，您可以使用各種圖像格式，如 PNG、JPG、BMP 等。

### 是否有必要使用一個`.pfx` file for the certificate?
是的，一個`.pfx`文件是儲存加密資訊（包括憑證和私鑰）的通用格式。

### 我可以在單一文件中新增多個簽名行嗎？
絕對地！您可以透過對每個簽名重複插入步驟來插入多個簽名行。

### 如果我沒有數位憑證怎麼辦？
您需要從受信任的憑證授權單位取得數位憑證或使用 OpenSSL 等工具產生數位憑證。

### 如何驗證文件中的數位簽章？
您可以在Word中開啟已簽署的文件並前往簽名詳細資料以驗證簽名的真實性和完整性。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
