---
"description": "透過本詳細的逐步指南了解如何使用 Aspose.Words for .NET 簽署加密的 Word 文件。非常適合開發人員。"
"linktitle": "簽署加密的 Word 文件"
"second_title": "Aspose.Words文件處理API"
"title": "簽署加密的 Word 文件"
"url": "/zh-hant/net/programming-with-digital-signatures/signing-encrypted-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 簽署加密的 Word 文件

## 介紹

有沒有想過如何簽署加密的 Word 文件？今天，我們將使用 Aspose.Words for .NET 來完成這個過程。繫好安全帶，準備好接受詳細、引人入勝且有趣的教學！

## 先決條件

在深入研究程式碼之前，請確保您已準備好所需的一切：

1. Aspose.Words for .NET：從以下位置下載並安裝 [這裡](https://releases。aspose.com/words/net/).
2. Visual Studio：確保您已安裝它。
3. 有效證書：您需要一個 .pfx 證書檔案。
4. 基本 C# 知識：了解基礎知識將使本教學更加順暢。

## 導入命名空間

首先，讓我們導入必要的命名空間。這些對於存取 Aspose.Words 功能至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

現在，讓我們將這個過程分解為簡單、易於管理的步驟。

## 步驟 1：設定項目

首先，設定您的 Visual Studio 專案。開啟 Visual Studio 並建立一個新的 C# 控制台應用程式。將其命名為“SignEncryptedWordDoc”等描述性名稱。

## 第 2 步：將 Aspose.Words 新增至您的項目

接下來，我們需要將 Aspose.Words 新增到您的專案中。有幾種方法可以做到這一點，但使用 NuGet 是最簡單的。 

1. 從「工具」>「NuGet 套件管理器」>「套件管理器控制台」開啟 NuGet 套件管理器控制台。
2. 運行以下命令：

```powershell
Install-Package Aspose.Words
```

## 步驟3：準備文件目錄

您需要一個目錄來儲存您的 Word 文件和憑證。讓我們創建一個。

1. 在您的電腦上建立一個目錄。為了簡單起見，我們稱之為「DocumentDirectory」。
2. 將您的 Word 文件（例如「Document.docx」）和 .pfx 憑證（例如「morzal.pfx」）放在此目錄中。

## 步驟4：編寫程式碼

現在，讓我們深入研究程式碼。打開你的 `Program.cs` 文件並首先設定文檔目錄的路徑並初始化 `SignOptions` 以及解密密碼。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## 步驟5：載入證書

接下來，使用 `CertificateHolder` 班級。這將需要您的 .pfx 檔案的路徑和憑證的密碼。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 第六步：簽署文件

最後，使用 `DigitalSignatureUtil.Sign` 方法將加密的 Word 文件進行簽署。此方法需要輸入檔案、輸出檔案、憑證持有者和簽名選項。

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## 步驟 7：運行程式碼

儲存檔案並運行專案。如果一切設定正確，您應該會在指定的目錄中看到您簽署的文件。

## 結論

就是這樣！您已成功使用 Aspose.Words for .NET 簽署加密的 Word 文件。有了這個強大的函式庫，數位簽章就變得輕而易舉，即使對於加密檔案也是如此。編碼愉快！

## 常見問題解答

### 我可以使用不同類型的憑證嗎？
是的，Aspose.Words 支援各種憑證類型，只要它們的格式正確。

### 可以一次簽署多份文件嗎？
絕對地！您可以循環遍歷文件集合併以程式設計方式對每個文件進行簽名。

### 如果我忘了解密密碼怎麼辦？
不幸的是，如果沒有解密密碼，您將無法簽署該文件。

### 我可以在文件上添加可見的簽名嗎？
是的，Aspose.Words 也允許您添加可見的數位簽名。

### 有沒有辦法驗證簽名？
是的，您可以使用 `DigitalSignatureUtil.Verify` 方法來驗證簽名。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}