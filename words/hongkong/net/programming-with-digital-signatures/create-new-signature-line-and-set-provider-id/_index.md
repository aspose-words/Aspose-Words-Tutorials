---
"description": "了解如何使用 Aspose.Words for .NET 在 Word 文件中建立新的簽名行並設定提供者 ID。逐步指南。"
"linktitle": "建立新的簽名行並設定提供者 ID"
"second_title": "Aspose.Words文件處理API"
"title": "建立新的簽名行並設定提供者 ID"
"url": "/zh-hant/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 建立新的簽名行並設定提供者 ID

## 介紹

嘿，技術愛好者們！有沒有想過如何以程式設計方式在 Word 文件中新增簽名行？好吧，今天我們將深入研究如何使用 Aspose.Words for .NET 來實現這一點。本指南將引導您完成每個步驟，讓您可以輕鬆地在 Word 文件中建立新的簽名行並設定提供者 ID。無論您是想自動化文件處理還是只想簡化工作流程，本教學都能滿足您的需求。

## 先決條件

在我們開始動手之前，讓我們先確保我們已經準備好了我們需要的一切：

1. Aspose.Words for .NET：如果您還沒有下載，請下載 [這裡](https://releases。aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他 C# 開發環境。
3. .NET Framework：確保您已安裝 .NET Framework。
4. PFX 憑證：為了簽署文件，您需要一個 PFX 憑證。您可以從受信任的憑證授權單位取得一個。

## 導入命名空間

首先，讓我們在 C# 專案中導入必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

好吧，讓我們開始討論細節。以下是建立新簽名行和設定提供者 ID 的每個步驟的詳細分解。

## 步驟 1：建立新文檔

首先，我們需要建立一個新的 Word 文件。這將成為我們標誌性系列的畫布。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在這個程式碼片段中，我們初始化一個新的 `Document` 和一個 `DocumentBuilder`。這 `DocumentBuilder` 幫助我們為文件添加元素。

## 第 2 步：定義簽章行選項

接下來，我們定義簽名行的選項。其中包括簽名者的姓名、職稱、電子郵件和其他詳細資訊。

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

這些選項可以個性化簽名行，使其清晰、專業。

## 步驟 3：插入簽名行

設定完選項後，我們現在可以將簽名行插入到文件中。

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

在這裡， `InsertSignatureLine` 方法新增簽章行，我們為其指派一個唯一的提供者ID。

## 步驟4：儲存文檔

插入簽名行後，我們儲存文件。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

這將保存您的文件以及新新增的簽名行。

## 步驟 5：設定簽名選項

現在，我們需要設定簽署文件的選項。其中包括簽名行 ID、提供者 ID、註解和簽名時間。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

這些選項確保文件使用正確的詳細資訊進行簽署。

## 步驟 6：建立證書持有者

為了簽署該文件，我們將使用 PFX 憑證。讓我們為其建立一個證書持有者。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

確保更換 `"morzal.pfx"` 與您的實際證書文件和 `"aw"` 使用您的證書密碼。

## 步驟 7：簽署文件

最後，我們使用數位簽章實用程式對文件進行簽署。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

這將對文件進行簽名並將其儲存為新文件。

## 結論

就是這樣！您已成功建立了新的簽名行並使用 Aspose.Words for .NET 在 Word 文件中設定了提供者 ID。這個強大的程式庫使得管理和自動化文件處理任務變得非常容易。嘗試一下，看看它如何簡化您的工作流程。

## 常見問題解答

### 我可以自訂簽名行的外觀嗎？
絕對地！您可以在 `SignatureLineOptions` 以滿足您的需求。

### 如果我沒有 PFX 憑證怎麼辦？
您需要從受信任的憑證授權單位取得一個。它對於數位簽章文件至關重要。

### 我可以在一份文件中新增多個簽名行嗎？
是的，您可以透過使用不同的選項重複插入過程來新增所需數量的簽名行。

### Aspose.Words for .NET 是否與 .NET Core 相容？
是的，Aspose.Words for .NET 支援 .NET Core，使其適用於不同的開發環境。

### 數位簽章有多安全？
只要您使用有效且可信賴的證書，使用 Aspose.Words 建立的數位簽章就非常安全。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}