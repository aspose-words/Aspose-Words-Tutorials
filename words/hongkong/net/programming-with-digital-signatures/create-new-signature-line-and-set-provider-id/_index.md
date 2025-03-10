---
title: 建立新簽名行並設定提供者 ID
linktitle: 建立新簽名行並設定提供者 ID
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中建立新的簽名行並設定提供者 ID。逐步指南。
weight: 10
url: /zh-hant/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立新簽名行並設定提供者 ID

## 介紹

嘿，科技愛好者們！有沒有想過如何以程式設計方式在 Word 文件中新增簽名行？好吧，今天我們將深入探討使用 Aspose.Words for .NET。本指南將引導您完成每個步驟，讓您在 Word 文件中建立新的簽名行和設定提供者 ID 變得非常簡單。無論您是要自動化文件處理還是只是想簡化工作流程，本教學都能滿足您的要求。

## 先決條件

在我們動手之前，讓我們確保我們已經擁有我們需要的一切：

1.  Aspose.Words for .NET：如果您還沒有，請下載它[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他 C# 開發環境。
3. .NET Framework：確保您已安裝 .NET Framework。
4. PFX 憑證：要簽署文檔，您需要 PFX 憑證。您可以從受信任的憑證授權單位取得一份。

## 導入命名空間

首先，讓我們在 C# 專案中導入必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

好吧，讓我們進入實質內容。以下是建立新簽名行和設定提供者 ID 的每個步驟的詳細細分。

## 第 1 步：建立一個新文檔

首先，我們需要建立一個新的 Word 文件。這將是我們簽名行的畫布。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在此程式碼片段中，我們正在初始化一個新的`Document`和一個`DocumentBuilder`。這`DocumentBuilder`幫助我們為文件添加元素。

## 第 2 步：定義簽章行選項

接下來，我們定義簽名行的選項。這包括簽名者的姓名、職位、電子郵件和其他詳細資訊。

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

這些選項使簽名行個性化，使其清晰且專業。

## 第 3 步：插入簽名行

設定選項後，我們現在可以將簽名行插入文件中。

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

在這裡，`InsertSignatureLine`方法新增簽名行，並且我們為其分配唯一的提供者 ID。

## 步驟 4：儲存文檔

插入簽名行後，讓我們儲存文件。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

這將使用新新增的簽名行來儲存您的文件。

## 第 5 步：設定簽名選項

現在，我們需要設定用於簽署文件的選項。這包括簽名行 ID、提供者 ID、註解和簽名時間。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

這些選項可確保使用正確的詳細資訊簽署文件。

## 第 6 步：建立證書持有者

為了簽署文檔，我們將使用 PFX 憑證。讓我們為它建立一個證書持有者。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

確保更換`"morzal.pfx"`與您的實際證書文件和`"aw"`與您的證書密碼。

## 第 7 步：簽署文件

最後，我們使用數位簽章實用程式對文件進行簽署。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

這會對文件進行簽名並將其另存為新文件。

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 在 Word 文件中成功建立了新的簽名行並設定了提供者 ID。這個強大的程式庫使管理和自動化文件處理任務變得非常容易。嘗試一下，看看它如何簡化您的工作流程。

## 常見問題解答

### 我可以自訂簽名行的外觀嗎？
絕對地！您可以在其中調整各種選項`SignatureLineOptions`以滿足您的需求。

### 如果我沒有 PFX 憑證怎麼辦？
您需要從受信任的憑證授權單位取得一份憑證。這對於數位簽章文件至關重要。

### 我可以在文件中新增多個簽名行嗎？
是的，您可以透過使用不同的選項重複插入過程來新增所需數量的簽名行。

### Aspose.Words for .NET 與 .NET Core 相容嗎？
是的，Aspose.Words for .NET 支援 .NET Core，使其適用於不同的開發環境。

### 數位簽章的安全性如何？
只要您使用有效且可信賴的證書，使用 Aspose.Words 建立的數位簽章就非常安全。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
