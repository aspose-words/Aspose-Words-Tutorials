---
title: Конвертировать Docx в Mhtml и отправлять электронную почту
linktitle: Конвертировать Docx в Mhtml и отправлять электронную почту
second_title: API обработки документов Aspose.Words
description: Узнайте, как преобразовать DOCX в MHTML и отправлять электронные письма с помощью Aspose.Words для .NET в этом пошаговом руководстве. Повысьте свою производительность с помощью простой автоматизации.
weight: 10
url: /ru/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Конвертировать Docx в Mhtml и отправлять электронную почту

## Введение

В сегодняшнюю цифровую эпоху преобразование документов из одного формата в другой и отправка их по электронной почте является обычной задачей. Эта статья проведет вас через процесс преобразования файла DOCX в формат MHTML и последующей отправки его по электронной почте с помощью Aspose.Words for .NET. Мы разберем каждый шаг в подробном, простом руководстве, гарантируя, что вы поймете процесс от начала до конца. Давайте погрузимся!

## Предпосылки

Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:

1.  Aspose.Words для .NET: Загрузите и установите библиотеку Aspose.Words для .NET с сайта[Страница релизов Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email для .NET: Загрузите и установите библиотеку Aspose.Email для .NET с сайта[Страница релизов Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Убедитесь, что на вашем компьютере установлен .NET Framework.
4. SMTP-сервер: для отправки электронных писем вам необходим доступ к SMTP-серверу.

## Импорт пространств имен

Чтобы использовать Aspose.Words и Aspose.Email в вашем проекте, вам нужно импортировать необходимые пространства имен. Добавьте следующие директивы using в начало вашего файла C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Давайте разобьем этот процесс на несколько этапов, чтобы вы четко понимали каждую часть.

## Шаг 1: Загрузите документ DOCX

 Сначала вам нужно загрузить документ DOCX, который вы хотите преобразовать. Используйте`Document` класс из Aspose.Words для загрузки вашего файла DOCX.

```csharp
// Путь к каталогу документов.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Шаг 2: Сохраните документ как MHTML

 Далее сохраните загруженный документ как файл MHTML. Это делается с помощью`Save` Метод`Document` сорт.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Перемотайте поток к началу, чтобы Aspose.Email мог его прочитать.
stream.Position = 0;
```

## Шаг 3: Создайте электронное письмо

 Теперь создайте сообщение электронной почты из потока MHTML с помощью Aspose.Email. Вы будете использовать`MailMessage` класс для этой цели.

```csharp
// Создайте из потока сообщение электронной почты Aspose.Email MIME.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Шаг 4: Отправьте электронное письмо

 Наконец, отправьте письмо с помощью SMTP-клиента. Настройте SMTP-клиент с данными вашего SMTP-сервера и используйте`Send` способ отправки сообщения.

```csharp
// Отправьте сообщение с помощью Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Заключение

Поздравляем! Вы успешно преобразовали документ DOCX в MHTML и отправили его по электронной почте с помощью Aspose.Words for .NET. Этот процесс включает загрузку документа, преобразование его в MHTML, создание сообщения электронной почты и отправку его с помощью SMTP-клиента. С помощью этих шагов вы можете легко автоматизировать преобразование и отправку документов по электронной почте в своих приложениях.

## Часто задаваемые вопросы

### Могу ли я использовать этот метод для конвертации других форматов документов?
Да, Aspose.Words поддерживает различные форматы, и вы можете конвертировать такие документы, как DOC, DOCX, RTF и другие, в MHTML.

### Как добавить вложения к письму?
 Вы можете использовать`Attachments` собственность`MailMessage` класс для добавления вложений в ваше электронное письмо.

### Совместим ли Aspose.Words с .NET Core?
Да, Aspose.Words совместим с .NET Core. Вы также можете использовать его в приложениях .NET Core.

### Нужна ли мне лицензия для Aspose.Words и Aspose.Email?
 Да, обе библиотеки требуют лицензии. Вы можете получить временную лицензию у[Страница покупки Aspose](https://purchase.aspose.com/temporary-license/) для целей оценки.

### Где я могу найти дополнительную документацию?
 Подробную документацию по Aspose.Words вы можете найти[здесь](https://reference.aspose.com/words/net/) и для Aspose.Email[здесь](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
