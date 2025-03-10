---
title: 将 Docx 转换为 Mhtml 并发送电子邮件
linktitle: 将 Docx 转换为 Mhtml 并发送电子邮件
second_title: Aspose.Words 文档处理 API
description: 在本分步指南中了解如何使用 Aspose.Words for .NET 将 DOCX 转换为 MHTML 并发送电子邮件。通过轻松的自动化提高您的工作效率。
weight: 10
url: /zh/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 Docx 转换为 Mhtml 并发送电子邮件

## 介绍

在当今的数字时代，将文档从一种格式转换为另一种格式并通过电子邮件发送是一项常见任务。本文将引导您完成将 DOCX 文件转换为 MHTML 格式然后使用 Aspose.Words for .NET 将其作为电子邮件发送的过程。我们将在详细、易于遵循的指南中分解每个步骤，确保您从头到尾了解该过程。让我们开始吧！

## 先决条件

在开始之前，请确保您已满足以下先决条件：

1.  Aspose.Words for .NET：从以下位置下载并安装 Aspose.Words for .NET 库：[Aspose 发布页面](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET：从以下位置下载并安装 Aspose.Email for .NET 库[Aspose 发布页面](https://releases.aspose.com/email/net/).
3. .NET Framework：确保您的机器上安装了 .NET Framework。
4. SMTP 服务器：您需要访问 SMTP 服务器才能发送电子邮件。

## 导入命名空间

要在项目中使用 Aspose.Words 和 Aspose.Email，您需要导入必要的命名空间。在 C# 文件顶部添加以下使用指令：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

我们将该过程分解为多个步骤，以确保您清楚地理解每个部分。

## 步骤 1：加载 DOCX 文档

首先，您需要加载要转换的 DOCX 文档。使用`Document`来自 Aspose.Words 的类来加载您的 DOCX 文件。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## 步骤 2：将文档另存为 MHTML

接下来，将加载的文档保存为 MHTML 文件。使用`Save`方法`Document`班级。

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

//将流倒回到开头，以便 Aspose.Email 可以读取它。
stream.Position = 0;
```

## 步骤 3：创建电子邮件

现在，使用 Aspose.Email 从 MHTML 流创建电子邮件消息。您将使用`MailMessage`为此目的而设的班级。

```csharp
//从流中创建 Aspose.Email MIME 电子邮件消息。
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## 步骤 4：发送电子邮件

最后，使用 SMTP 客户端发送电子邮件。使用 SMTP 服务器详细信息配置 SMTP 客户端，然后使用`Send`方法发送消息。

```csharp
//使用 Aspose.Email 发送消息。
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## 结论

恭喜！您已成功将 DOCX 文档转换为 MHTML，并使用 Aspose.Words for .NET 通过电子邮件发送。此过程包括加载文档、将其转换为 MHTML、创建电子邮件消息以及使用 SMTP 客户端发送。通过这些步骤，您可以轻松地在应用程序中自动转换和发送电子邮件。

## 常见问题解答

### 我可以使用此方法来转换其他文档格式吗？
是的，Aspose.Words 支持各种格式，您可以将 DOC、DOCX、RTF 等文档转换为 MHTML。

### 如何在电子邮件中添加附件？
您可以使用`Attachments`的财产`MailMessage`类将附件添加到您的电子邮件中。

### Aspose.Words 与 .NET Core 兼容吗？
是的，Aspose.Words 与 .NET Core 兼容。您也可以在 .NET Core 应用程序中使用它。

### 我需要 Aspose.Words 和 Aspose.Email 的许可证吗？
是的，这两个库都需要许可证。你可以从[Aspose 购买页面](https://purchase.aspose.com/temporary-license/)用于评估目的。

### 在哪里可以找到更多文档？
您可以找到 Aspose.Words 的详细文档[这里](https://reference.aspose.com/words/net/)以及 Aspose.Email[这里](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
