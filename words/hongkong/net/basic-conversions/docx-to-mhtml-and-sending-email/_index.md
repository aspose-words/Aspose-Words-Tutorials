---
title: 將 Docx 轉換為 Mhtml 並發送電子郵件
linktitle: 將 Docx 轉換為 Mhtml 並發送電子郵件
second_title: Aspose.Words 文件處理 API
description: 在此逐步指南中了解如何將 DOCX 轉換為 MHTML 並使用 Aspose.Words for .NET 發送電子郵件。透過簡單的自動化提高您的生產力。
weight: 10
url: /zh-hant/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Docx 轉換為 Mhtml 並發送電子郵件

## 介紹

在當今的數位時代，將文件從一種格式轉換為另一種格式並透過電子郵件發送是一項常見任務。本文將引導您完成將 DOCX 檔案轉換為 MHTML 格式，然後使用 Aspose.Words for .NET 將其作為電子郵件發送的過程。我們將在詳細、易於遵循的指南中分解每個步驟，確保您從頭到尾都了解整個過程。讓我們深入了解吧！

## 先決條件

在我們開始之前，請確保您具備以下先決條件：

1.  Aspose.Words for .NET：從下列位置下載並安裝 Aspose.Words for .NET 函式庫：[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET：從下列位置下載並安裝 Aspose.Email for .NET 程式庫：[Aspose 發佈頁面](https://releases.aspose.com/email/net/).
3. .NET Framework：請確定您的電腦上安裝了 .NET Framework。
4. SMTP 伺服器：您需要存取 SMTP 伺服器才能傳送電子郵件。

## 導入命名空間

要在專案中使用 Aspose.Words 和 Aspose.Email，您需要匯入必要的命名空間。在 C# 檔案頂部新增以下 using 指令：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

讓我們將這個過程分解為多個步驟，以確保您清楚地理解每個部分。

## 第 1 步：載入 DOCX 文檔

首先，您需要載入要轉換的 DOCX 文件。使用`Document`Aspose.Words 中的類別來載入 DOCX 檔案。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## 步驟 2：將文件儲存為 MHTML

接下來，將已載入的文件儲存為 MHTML 文件。這是使用以下方法完成的`Save`的方法`Document`班級。

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

//將流倒回到開頭，以便 Aspose.Email 可以讀取它。
stream.Position = 0;
```

## 第 3 步：建立電子郵件訊息

現在，使用 Aspose.Email 從 MHTML 串流建立電子郵件。您將使用`MailMessage`為此目的的類別。

```csharp
//從串流建立 Aspose.Email MIME 電子郵件。
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## 第 4 步：發送電子郵件

最後，使用 SMTP 用戶端發送電子郵件。使用您的 SMTP 伺服器詳細資訊設定 SMTP 用戶端並使用`Send`發送訊息的方法。

```csharp
//使用 Aspose.Email 發送訊息。
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## 結論

恭喜！您已成功將 DOCX 文件轉換為 MHTML 並使用 Aspose.Words for .NET 透過電子郵件傳送。此過程包括載入文件、將其轉換為 MHTML、建立電子郵件以及使用 SMTP 用戶端發送。透過這些步驟，您可以輕鬆地自動轉換應用程式中的文件並透過電子郵件發送。

## 常見問題解答

### 我可以使用此方法轉換其他文件格式嗎？
是的，Aspose.Words 支援各種格式，您可以將 DOC、DOCX、RTF 等文件轉換為 MHTML。

### 如何為電子郵件新增附件？
您可以使用`Attachments`的財產`MailMessage`類別將附件新增至您的電子郵件。

### Aspose.Words 與 .NET Core 相容嗎？
是的，Aspose.Words 與 .NET Core 相容。您也可以在 .NET Core 應用程式中使用它。

### 我需要 Aspose.Words 和 Aspose.Email 授權嗎？
是的，兩個庫都需要許可證。您可以從以下機構獲得臨時許可證[Aspose購買頁面](https://purchase.aspose.com/temporary-license/)出於評估目的。

### 在哪裡可以找到更多文件？
您可以找到 Aspose.Words 的詳細文檔[這裡](https://reference.aspose.com/words/net/)對於 Aspose.Email[這裡](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
