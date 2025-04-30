---
"description": "このステップバイステップガイドでは、Aspose.Words for .NET を使用してDOCXをMHTMLに変換し、メールを送信する方法を学習します。簡単な自動化で生産性を向上しましょう。"
"linktitle": "DocxをMHTMLに変換してメールを送信する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "DocxをMHTMLに変換してメールを送信する"
"url": "/ja/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# DocxをMHTMLに変換してメールを送信する

## 導入

今日のデジタル時代では、ドキュメントをある形式から別の形式に変換し、メールで送信することは日常的な作業です。この記事では、Aspose.Words for .NET を使用して、DOCX ファイルを MHTML 形式に変換し、メールで送信する手順を詳しく説明します。各ステップを詳細かつ分かりやすいガイドで解説し、プロセスを最初から最後まで理解できるようにします。さあ、始めましょう！

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

1. Aspose.Words for .NET: Aspose.Words for .NETライブラリを以下のサイトからダウンロードしてインストールします。 [Aspose リリースページ](https://releases。aspose.com/words/net/).
2. Aspose.Email for .NET: Aspose.Email for .NETライブラリを以下のサイトからダウンロードしてインストールします。 [Aspose リリースページ](https://releases。aspose.com/email/net/).
3. .NET Framework: マシンに .NET Framework がインストールされていることを確認します。
4. SMTP サーバー: 電子メールを送信するには、SMTP サーバーにアクセスする必要があります。

## 名前空間のインポート

プロジェクトでAspose.WordsとAspose.Emailを使用するには、必要な名前空間をインポートする必要があります。C#ファイルの先頭に以下のusingディレクティブを追加してください。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

各部分を明確に理解できるように、プロセスを複数のステップに分解してみましょう。

## ステップ1: DOCXドキュメントを読み込む

まず、変換したいDOCX文書を読み込む必要があります。 `Document` DOCX ファイルを読み込むための Aspose.Words のクラス。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## ステップ2: ドキュメントをMHTMLとして保存する

次に、読み込んだドキュメントをMHTMLファイルとして保存します。これは、 `Save` の方法 `Document` クラス。

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Aspose.Email が読み取れるように、ストリームを先頭まで巻き戻します。
stream.Position = 0;
```

## ステップ3: メールメッセージを作成する

次に、Aspose.Emailを使用してMHTMLストリームから電子メールメッセージを作成します。 `MailMessage` この目的のためのクラスです。

```csharp
// ストリームから Aspose.Email MIME 電子メール メッセージを作成します。
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## ステップ4: メールを送信する

最後に、SMTPクライアントを使用してメールを送信します。SMTPクライアントにSMTPサーバーの詳細を設定し、 `Send` メッセージを送信する方法。

```csharp
// Aspose.Email を使用してメッセージを送信します。
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## 結論

おめでとうございます！Aspose.Words for .NET を使用して、DOCX ドキュメントを MHTML に変換し、メールで送信することができました。このプロセスには、ドキュメントの読み込み、MHTML への変換、メールメッセージの作成、そして SMTP クライアントを使用した送信が含まれます。これらの手順により、アプリケーション内でのドキュメントの変換とメール送信を簡単に自動化できます。

## よくある質問

### この方法を使用して他のドキュメント形式を変換できますか?
はい、Aspose.Words はさまざまな形式をサポートしており、DOC、DOCX、RTF などのドキュメントを MHTML に変換できます。

### メールに添付ファイルを追加するにはどうすればいいですか?
使用することができます `Attachments` の財産 `MailMessage` 電子メールに添付ファイルを追加するクラス。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Wordsは.NET Coreと互換性があります。.NET Coreアプリケーションでもご利用いただけます。

### Aspose.Words と Aspose.Email のライセンスは必要ですか?
はい、どちらのライブラリもライセンスが必要です。一時ライセンスは [Aspose 購入ページ](https://purchase.aspose.com/temporary-license/) 評価目的のため。

### さらに詳しいドキュメントはどこで見つかりますか?
Aspose.Wordsの詳細なドキュメントは以下をご覧ください。 [ここ](https://reference.aspose.com/words/net/) Aspose.Emailの場合 [ここ](https://reference。aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}