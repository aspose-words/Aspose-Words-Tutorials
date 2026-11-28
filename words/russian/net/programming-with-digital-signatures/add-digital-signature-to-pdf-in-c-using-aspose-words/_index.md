---
category: general
date: 2026-08-10
description: Добавьте цифровую подпись в PDF с помощью Aspose.Words на C#. Узнайте,
  как преобразовать DOCX в подписанный PDF и сохранить документ как подписанный PDF
  за несколько шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add digital signature to pdf
- convert docx to signed pdf
- save document as signed pdf
- Aspose.Words digital signature
- C# PDF signing
language: ru
lastmod: 2026-08-10
og_description: Добавьте цифровую подпись в PDF на C# с использованием Aspose.Words.
  Это руководство покажет, как преобразовать DOCX в подписанный PDF и сохранить документ
  как подписанный PDF с полным кодом.
og_image_alt: Screenshot of C# code that adds a digital signature to a PDF using Aspose.Words
og_title: Добавление цифровой подписи в PDF на C# – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Add digital signature to PDF with Aspose.Words in C#. Learn how to
    convert docx to signed PDF and save document as signed PDF in a few steps.
  headline: Add digital signature to PDF in C# using Aspose.Words
  type: TechArticle
- description: Add digital signature to PDF with Aspose.Words in C#. Learn how to
    convert docx to signed PDF and save document as signed PDF in a few steps.
  name: Add digital signature to PDF in C# using Aspose.Words
  steps:
  - name: Expected result
    text: 'Open the generated PDF in Adobe Acrobat Reader:'
  - name: Using a certificate from the Windows store
    text: 'Instead of a `.pfx` file, you can retrieve a certificate from the local
      machine store:'
  - name: Switching to XAdES‑BES profile
    text: 'If your regulator requires a Basic Electronic Signature (BES) instead of
      EPES, change the policy identifier:'
  - name: Signing multiple PDFs in a loop
    text: When processing a batch of contracts, wrap the logic in a `foreach` loop
      and reuse the same `PdfSignatureOptions` instance to avoid redundant certificate
      loading.
  - name: Next steps
    text: '- Explore timestamping the signature with an RFC 3161 server for long‑term
      validation. - Combine this workflow with Aspose.PDF to add visible signature
      appearances or custom metadata. - Integrate certificate retrieval from Azure
      Key Vault for cloud‑native security.'
  type: HowTo
tags:
- digital signature
- Aspose.Words
- C#
- PDF
- docx
title: Добавить цифровую подпись в PDF на C# с использованием Aspose.Words
url: /ru/net/programming-with-digital-signatures/add-digital-signature-to-pdf-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавить цифровую подпись в PDF с помощью C# и Aspose.Words

Если вам нужно **добавить цифровую подпись в PDF** в .NET‑приложении, это руководство проведёт вас через все шаги. Вы увидите, как преобразовать файл Word .docx в подписанный PDF и как **сохранить документ как подписанный PDF** не выходя из вашего кода.

Во многих проектах с жёсткими требованиями к соответствию требуется PDF с защитой от подделки, подтверждающий личность автора. К концу этого руководства у вас будет готовый пример на C#, который подписывает PDF с профилем XAdES‑EPES, форматом, признанным большинством государственных и корпоративных систем.

## Требования

- .NET 6.0 SDK или новее (код также работает с .NET Framework 4.7+)
- Лицензия Aspose.Words for .NET (бесплатная оценочная версия подходит для тестирования)
- Сертификат PKCS#12 (`.pfx`), содержащий закрытый ключ
- Visual Studio 2022 или любая IDE, поддерживающая C#

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Шаг 1: Загрузить исходный документ Word

Первая операция загружает файл Word, который вы хотите подписать. Класс `Document` представляет весь пакет .docx в памяти.

```csharp
using Aspose.Words;

// Load the Word document that will be signed
Document document = new Document("YOUR_DIRECTORY/Contract.docx");
```

**Почему это важно** – Загрузка документа создаёт объектную модель, которую Aspose.Words позже может преобразовать в PDF. Если путь к файлу неверен, `Document` генерирует `FileNotFoundException`, поэтому проверьте путь перед продолжением.

## Шаг 2: Подготовить параметры сохранения PDF с подписью XAdES‑EPES

Aspose.Words позволяет внедрять цифровую подпись во время конвертации в PDF. Контейнер `PdfSaveOptions` содержит объект `PdfSignatureOptions`, который, в свою очередь, использует `XAdESSigner`, настроенный под политику EPES.

```csharp
using Aspose.Words.Saving;
using Aspose.Words.Signing;
using System.Security.Cryptography.X509Certificates;

// Create PDF save options and configure XAdES‑EPES signature
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    SignatureOptions = new PdfSignatureOptions
    {
        Signer = new XAdESSigner
        {
            // Use the XAdES‑EPES profile for the digital signature
            SignaturePolicyIdentifier = XAdESSignaturePolicyIdentifier.Epes,

            // Load the signing certificate (replace with your own certificate file and password)
            SigningCertificate = new X509Certificate2(
                "YOUR_DIRECTORY/mycert.pfx",
                "yourPassword")
        }
    }
};
```

**Почему мы выбираем XAdES‑EPES** – EPES (Explicit Policy-based Electronic Signature) встраивает идентификатор политики в подпись, удовлетворяя многие нормативные рамки, такие как eIDAS. `XAdESSigner` выполняет низкоуровневую криптографическую работу, поэтому вам не нужно вручную управлять хешированием или структурами ASN.1.

**Распространённые подводные камни** –  
- Файл `.pfx` должен содержать закрытый ключ; иначе `SigningCertificate` генерирует `CryptographicException`.  
- Храните пароли безопасно; в продакшене используйте Azure Key Vault или хранилище сертификатов Windows вместо их жёсткого кодирования.

## Шаг 3: Преобразовать документ и **сохранить документ как подписанный PDF**

Теперь вы объединяете загруженный документ Word с настроенными `PdfSaveOptions`. Метод `Save` создаёт PDF‑файл и внедряет цифровую подпись в одной операции.

```csharp
// Save the document as a signed PDF
document.Save("YOUR_DIRECTORY/Contract_Signed.pdf", pdfOptions);
```

После завершения вызова файл `Contract_Signed.pdf` содержит видимое поле подписи (если исходный файл Word имел строку подписи) и скрытую подпись XAdES‑EPES, которую можно проверить в Adobe Acrobat, Foxit Reader или любом PDF‑просмотрщике, поддерживающем цифровые подписи.

### Ожидаемый результат

Откройте сгенерированный PDF в Adobe Acrobat Reader:

1. Панель **Signature** отображает действительную цифровую подпись с именем подписанта из сертификата.  
2. Статус подписи показывает **Signed and all signatures are valid**, если цепочка сертификатов доверена.  
3. Содержимое документа нельзя изменить без аннулирования подписи.

## Шаг 4: Необязательно – Проверить подпись программно

Если вашему приложению необходимо подтвердить, что PDF был подписан корректно, используйте Aspose.PDF (или стороннюю библиотеку) для чтения полей подписи.

```csharp
using Aspose.Pdf;
using Aspose.Pdf.Forms;

// Load the signed PDF
Document pdfDoc = new Document("YOUR_DIRECTORY/Contract_Signed.pdf");

// Access the first signature field
SignatureField sigField = (SignatureField)pdfDoc.Form["Signature1"];

// Verify the signature
bool isValid = sigField.ValidateSignature();
Console.WriteLine(isValid ? "Signature is valid." : "Signature validation failed.");
```

**Почему проверять** – Автоматизированные рабочие процессы (например, обработка счетов) часто требуют отклонять документы с отсутствующими или повреждёнными подписями до их попадания в последующие системы.

## Шаг 5: Пограничные случаи и варианты

### Использование сертификата из хранилища Windows

Вместо файла `.pfx` вы можете получить сертификат из хранилища локального компьютера:

```csharp
X509Store store = new X509Store(StoreName.My, StoreLocation.CurrentUser);
store.Open(OpenFlags.ReadOnly);
X509Certificate2 cert = store.Certificates
    .Find(X509FindType.FindByThumbprint, "YOUR_CERT_THUMBPRINT", false)[0];
store.Close();

pdfOptions.SignatureOptions.Signer.SigningCertificate = cert;
```

### Переход на профиль XAdES‑BES

Если ваш регулятор требует базовую электронную подпись (BES) вместо EPES, измените идентификатор политики:

```csharp
SignaturePolicyIdentifier = XAdESSignaturePolicyIdentifier.Bes
```

### Подписание нескольких PDF в цикле

При обработке пакета контрактов оберните логику в цикл `foreach` и повторно используйте тот же экземпляр `PdfSignatureOptions`, чтобы избежать повторной загрузки сертификата.

```csharp
foreach (var docPath in Directory.GetFiles("Contracts", "*.docx"))
{
    Document doc = new Document(docPath);
    string outPath = Path.ChangeExtension(docPath, "_Signed.pdf");
    doc.Save(outPath, pdfOptions);
}
```

**Совет по производительности** – Загрузите сертификат один раз вне цикла; повторное использование того же объекта `X509Certificate2` снижает нагрузку на процессор.

## Полный список исходного кода

Ниже представлен полный, исполняемый пример программы, объединяющий все шаги. Замените шаблонные пути и пароль своими значениями.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
using System.Security.Cryptography.X509Certificates;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that will be signed
        Document document = new Document("YOUR_DIRECTORY/Contract.docx");

        // Step 2: Create PDF save options and configure XAdES‑EPES signature
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            SignatureOptions = new PdfSignatureOptions
            {
                Signer = new XAdESSigner
                {
                    SignaturePolicyIdentifier = XAdESSignaturePolicyIdentifier.Epes,
                    SigningCertificate = new X509Certificate2(
                        "YOUR_DIRECTORY/mycert.pfx",
                        "yourPassword")
                }
            }
        };

        // Step 3: Save the document as a signed PDF
        document.Save("YOUR_DIRECTORY/Contract_Signed.pdf", pdfOptions);

        Console.WriteLine("Signed PDF created successfully.");
    }
}
```

Скомпилируйте и запустите программу:

```bash
dotnet run
```

Вы должны увидеть **"Signed PDF created successfully."** и новый файл `Contract_Signed.pdf` в целевой папке.

## Заключение

Теперь вы знаете, как **добавить цифровую подпись в PDF** с помощью Aspose.Words для .NET, как **преобразовать docx в подписанный pdf**, и как **сохранить документ как подписанный pdf** в одной эффективной операции. Этот подход работает как с отдельными файлами, так и с большими партиями, и поддерживает альтернативные политики подписи и источники сертификатов.

### Следующие шаги

- Изучите добавление метки времени к подписи с помощью сервера RFC 3161 для долгосрочной проверки.  
- Объедините этот процесс с Aspose.PDF, чтобы добавить видимые подписи или пользовательские метаданные.  
- Интегрируйте получение сертификатов из Azure Key Vault для облачной безопасности.

Не стесняйтесь экспериментировать с различными профилями XAdES, встраивать несколько подписей или соединять этот процесс с конвейерами автоматической генерации документов. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, основанные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и изучить альтернативные подходы к реализации в ваших проектах.

- [Добавить цифровую подпись в PDF с использованием Certificate Holder](/words/english/net/programming-with-pdfsaveoptions/digitally-signed-pdf-using-certificate-holder/)
- [конвертировать word в pdf в C# с помощью Aspose.Words – Руководство](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [сохранить docx как pdf с Aspose.Words – Полное руководство C#](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}