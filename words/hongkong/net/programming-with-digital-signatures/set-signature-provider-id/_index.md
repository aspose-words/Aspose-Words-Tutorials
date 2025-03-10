---
title: 在 Word 文件中設定簽名提供者 ID
linktitle: 在 Word 文件中設定簽名提供者 ID
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 在 Word 文件中安全地設定簽名提供者 ID。請依照我們詳細的 2000 字指南對您的文件進行數位簽章。
weight: 10
url: /zh-hant/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中設定簽名提供者 ID

## 介紹

嘿！那麼，您已經有了需要數位簽名的令人驚嘆的 Word 文檔，對嗎？但不僅僅是任何簽名 - 您需要設定特定的簽名提供者 ID。無論您是處理法律文件、合約還是任何文書工作，添加安全的數位簽名都至關重要。在本教學中，我將引導您完成使用 Aspose.Words for .NET 在 Word 文件中設定簽名提供者 ID 的整個過程。準備好？讓我們深入了解吧！

## 先決條件

在我們開始之前，請確保您具備以下條件：

1. Aspose.Words for .NET Library：如果您還沒有，[在這裡下載](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何 C# 相容 IDE。
3. Word 文件：帶有簽名行的文件 (`Signature line.docx`）。
4. 數位憑證：A`.pfx`證書文件（例如，`morzal.pfx`）。
5. C# 基礎知識：只是基礎知識 - 不用擔心，我們隨時為您提供幫助！

現在，讓我們開始行動吧！

## 導入命名空間

首先，請確保您的專案中包含必要的命名空間。這對於存取 Aspose.Words 庫和相關類別至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

好吧，讓我們將其分解為簡單易懂的步驟。

## 第 1 步：載入 Word 文檔

第一步是載入包含簽名行的 Word 文件。該文件將被修改以包含具有指定簽章提供者 ID 的數位簽章。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

在這裡，我們指定您的文件所在的目錄。代替`"YOUR DOCUMENT DIRECTORY"`與文檔的實際路徑。

## 第 2 步：訪問簽名行

接下來，我們需要存取文件中的簽名行。簽名行作為形狀物件嵌入到 Word 文件中。

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

這行程式碼會取得文件第一部分正文中的第一個形狀，並將其轉換為`SignatureLine`目的。

## 第 3 步：設定簽名選項

現在，我們建立簽名選項，其中包括提供者 ID 和存取的簽名行中的簽名行 ID。

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

簽署文件時將使用這些選項，以確保設定正確的簽章提供者 ID。

## 第4步：載入證書

要對文件進行數位簽名，您需要證書。這是您加載的方式`.pfx`文件：

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

代替`"aw"`以及您的證書文件的密碼（如果有的話）。

## 第 5 步：簽署文件

最後，是時候使用以下命令簽署文件了`DigitalSignatureUtil.Sign`方法。

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

這將簽署您的文件並將其另存為新文件，`Digitally signed.docx`.

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 在 Word 文件中成功設定簽名提供者 ID。此過程不僅可以保護您的文檔，還可以確保它們符合數位簽章標準。現在，繼續使用您的文件進行嘗試。有任何疑問嗎？請參閱下面的常見問題或點擊[Aspose 支援論壇](https://forum.aspose.com/c/words/8).

## 常見問題解答

### 什麼是簽名提供者 ID？

簽名提供者ID唯一標識數位簽章的供應商，確保真實性和安全性。

### 我可以使用任何 .pfx 檔案進行簽署嗎？

是的，只要它是有效的數位憑證。如果密碼受到保護，請確保您擁有正確的密碼。

### 如何取得 .pfx 檔案？

您可以從憑證授權單位 (CA) 取得 .pfx 文件，或使用 OpenSSL 等工具產生文件。

### 我可以一次簽署多份文件嗎？

是的，您可以循環瀏覽多個文件並對每個文件套用相同的簽名流程。

### 如果我的文件中沒有簽名行怎麼辦？

您需要先插入簽名行。 Aspose.Words 提供了以程式設計方式新增簽名行的方法。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
