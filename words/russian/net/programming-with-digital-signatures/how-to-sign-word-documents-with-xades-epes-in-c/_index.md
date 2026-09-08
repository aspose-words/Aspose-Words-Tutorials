---
category: general
date: 2026-09-08
description: Как подписывать документы Word с помощью рабочего процесса цифровой подписи
  docx, загрузить сертификат pfx и создать подпись XAdES в C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: ru
lastmod: 2026-09-08
og_description: Как подписать документы Word с помощью цифровой подписи в формате
  docx, загрузить сертификат pfx и создать подпись XAdES в C#. Следуйте полному примеру.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Как подписать документы Word с помощью XAdES EPES в C# – пошаговое руководство
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: Как подписать документы Word с XAdES EPES в C#
url: /ru/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как подписать документы Word с помощью XAdES EPES в C#

Если вам нужно **how to sign word** файлы программно, это руководство покажет полное, готовое к продакшну решение. Вы узнаете, как загрузить сертификат PFX, настроить **digital signature docx**, и создать подпись XAdES‑EPES, которую могут проверить Microsoft Word и сторонние валидаторы.

Пример использует библиотеку GroupDocs.Signature для .NET, но концепции применимы к любому API, поддерживающему XAdES. К концу урока у вас будет подписанный `Signed_XAdES_EPES.docx`, готовый к распространению.

## Что вам понадобится

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- Действительный файл сертификата PFX (`.pfx`), содержащий закрытый ключ
- Пароль к файлу PFX
- Документ Word (`.docx`), который вы хотите подписать
- Пакет NuGet **GroupDocs.Signature** (установить с помощью `dotnet add package GroupDocs.Signature`)

## Шаг 1: Установите требуемый пакет NuGet

```bash
dotnet add package GroupDocs.Signature
```

Пакет предоставляет класс `Document`, `XadesSignatureOptions` и вспомогательные типы для создания **digitally sign word** файла.

## Шаг 2: Загрузите неподписанный документ Word

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Загрузка документа даёт объектную модель, которой можно управлять перед применением подписи.

## Шаг 3: Загрузите сертификат PFX (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Pro tip:** Если сертификат хранится в хранилище сертификатов Windows, его можно получить с помощью `X509Store` вместо загрузки файла. Подход `load pfx certificate` работает на любой платформе, включая Linux‑контейнеры.

## Шаг 4: (Опционально) Добавьте визуальную строку подписи

Визуальный индикатор помогает получателям увидеть, где подпись будет отображаться в Word.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Если вы предпочитаете невидимую подпись, можете пропустить этот шаг. **digital signature docx** всё равно будет криптографически валидной.

## Шаг 5: Настройте параметры XAdES‑EPES (create xades signature)

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

Флаг `XadesSignatureType.XAdES_EPES` указывает библиотеке внедрить подпись согласно профилю EPES (Explicit Policy‑based Electronic Signature), который широко принят в рамках регуляций EU e‑IDAS.

## Шаг 6: Примените цифровую подпись

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

Метод `Sign` выполняет всю криптографическую работу: хеширует части документа, создаёт структуру XML‑DSig и вставляет оболочку XAdES в файл Word.

## Шаг 7: Сохраните подписанный документ

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

После сохранения откройте `Signed_XAdES_EPES.docx` в Microsoft Word. Вы должны увидеть строку подписи (если её добавляли) и статус‑полосу **digitally sign word**, указывающую, что файл подписан и подпись действительна.

## Полный, исполняемый пример

Ниже приведена полная программа, которую можно скопировать и вставить в консольное приложение.

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### Ожидаемый вывод

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Открытие файла в Word показывает зелёный баннер «Signed», а если вы добавили визуальную строку, она появляется в указанном месте.

## Обработка распространённых проблем

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Неправильный пароль сертификата** | Конструктор `X509Certificate2` бросает `CryptographicException`. | Проверьте пароль или используйте безопасный менеджер секретов (Azure Key Vault, AWS Secrets Manager). |
| **Word показывает “Signature is invalid”** | Документ был изменён после подписи, или отсутствует политика подписи. | Убедитесь, что файл сохранён **после** подписи и не редактируется повторно. Внедрите правильную политику XAdES, если это требуется вашим регулятором. |
| **Строка подписи не видна** | Документ использует иной макет раздела. | Добавьте `SignatureLine` в правильный абзац или создайте новый абзац перед добавлением. |
| **Снижение производительности на больших документах** | XAdES подписи хешируют каждую часть пакета. | Используйте потоковые API (`SignAsync`) или увеличьте ресурсы машины для очень больших файлов (>50 MB). |

## Расширение решения

- **Multiple signers** – вызывайте `Sign` многократно с разными сертификатами и задавайте `SignatureId` для различения каждого подписанта.
- **Timestamping** – добавьте объект `TimestampOptions` в `XadesSignatureOptions`, чтобы внедрить доверенную метку времени.
- **Custom policies** – укажите XML‑файл политики через `XadesSignatureOptions.PolicyFilePath` для соответствия конкретным стандартам.

## Заключение

Теперь вы знаете **how to sign word** документы программно, как **load pfx certificate**, и как **create xades signature** с помощью GroupDocs.Signature. Руководство охватило каждый шаг от загрузки документа до сохранения подписанного результата, включая практические советы по распространённым краевым случаям.  

Далее изучайте связанные темы, такие как **digitally sign word** PDF, интегрируйте проверку **digital signature docx**, или добавьте поддержку **timestamp** для соответствия продвинутым требованиям комплаенса. Удачной подписи!

## Что стоит изучить дальше?

Следующие уроки охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}