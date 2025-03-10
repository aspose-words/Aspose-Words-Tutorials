---
title: 簽署加密的 Word 文件
linktitle: 簽署加密的 Word 文件
second_title: Aspose.Words 文件處理 API
description: 透過這份詳細的逐步指南，了解如何使用 Aspose.Words for .NET 對加密的 Word 文件進行簽署。非常適合開發人員。
weight: 10
url: /zh-hant/net/programming-with-digital-signatures/signing-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 簽署加密的 Word 文件

## 介紹

有沒有想過如何簽署加密的 Word 文件？今天，我們將使用 Aspose.Words for .NET 逐步完成此過程。繫好安全帶，準備好接受詳細、引人入勝且有趣的教學！

## 先決條件

在深入研究程式碼之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：從以下位址下載並安裝[這裡](https://releases.aspose.com/words/net/).
2. Visual Studio：確保已安裝它。
3. 有效證書：您需要一個 .pfx 證書檔案。
4. 基本 C# 知識：了解基礎知識將使本教學更加順利。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這些對於存取 Aspose.Words 功能至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

現在，讓我們將流程分解為簡單、易於管理的步驟。

## 第 1 步：設定您的項目

首先，設定您的 Visual Studio 專案。開啟 Visual Studio 並建立一個新的 C# 控制台應用程式。將其命名為具有描述性的名稱，例如“SignEncryptedWordDoc”。

## 第 2 步：將 Aspose.Words 加入您的專案中

接下來，我們需要將 Aspose.Words 新增到您的專案中。有幾種方法可以做到這一點，但使用 NuGet 是最簡單的。 

1. 從「工具」>「NuGet 套件管理器」>「套件管理器控制台」開啟 NuGet 套件管理器控制台。
2. 運行以下命令：

```powershell
Install-Package Aspose.Words
```

## 第三步：準備文件目錄

您需要一個目錄來儲存 Word 文件和憑證。讓我們創建一個。

1. 在您的電腦上建立一個目錄。為了簡單起見，我們稱之為「DocumentDirectory」。
2. 將您的 Word 文件（例如，「Document.docx」）和 .pfx 憑證（例如，「morzal.pfx」）放入此目錄中。

## 第四步：編寫程式碼

現在，讓我們深入研究程式碼。打開你的`Program.cs`文件並首先設定文檔目錄的路徑並初始化`SignOptions`與解密密碼。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## 第5步：載入證書

接下來，使用以下命令載入您的證書`CertificateHolder`班級。這將需要 .pfx 檔案的路徑和憑證的密碼。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 第 6 步：簽署文件

最後，使用`DigitalSignatureUtil.Sign`方法來簽署加密的 Word 文件。此方法需要輸入檔案、輸出檔案、憑證持有者和簽名選項。

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## 第 7 步：運行程式碼

儲存檔案並運行專案。如果一切設定正確，您應該在指定的目錄中看到您簽署的文件。

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功簽署了加密的 Word 文件。有了這個強大的庫，即使對於加密文件，數位簽名也變得輕而易舉。快樂編碼！

## 常見問題解答

### 我可以使用不同類型的憑證嗎？
是的，Aspose.Words 支援各種憑證類型，只要它們的格式正確即可。

### 是否可以同時簽署多個文件？
絕對地！您可以循環瀏覽文件集合並以程式設計方式簽署每個文件。

### 如果忘記解密密碼怎麼辦？
不幸的是，如果沒有解密密碼，您將無法簽署文件。

### 我可以在文件中添加可見的簽名嗎？
是的，Aspose.Words 還允許您添加可見的數位簽名。

### 有沒有辦法驗證簽名？
是的，您可以使用`DigitalSignatureUtil.Verify`驗證簽名的方法。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
