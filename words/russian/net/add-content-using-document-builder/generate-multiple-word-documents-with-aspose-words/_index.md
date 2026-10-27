---
category: general
date: 2026-08-10
description: Создавайте несколько документов Word с помощью Aspose.Words в C#. Узнайте,
  как создавать счета из шаблона и эффективно пакетно генерировать файлы Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate multiple word documents
- create invoices from template
- batch generate word files
- Aspose.Words mail merge
- C# document automation
language: ru
lastmod: 2026-08-10
og_description: Создавайте несколько документов Word с помощью Aspose.Words. Этот
  учебник показывает, как создавать счета из шаблона и пакетно генерировать файлы
  Word на C#.
og_image_alt: Screenshot of generate multiple word documents result
og_title: Создание нескольких документов Word – пошаговое руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  headline: Generate multiple word documents with Aspose.Words
  type: TechArticle
- description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  name: Generate multiple word documents with Aspose.Words
  steps:
  - name: Prepare the data that will populate the merge fields
    text: The mail‑merge engine expects a collection of objects whose property names
      match the `MERGEFIELD` names in the template. In this example we use an anonymous
      type array, but you can replace it with a list of strongly‑typed DTOs.
  - name: Load the Word template that contains MERGEFIELD placeholders
    text: '```csharp // Step 2 – load template Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
      ```'
  - name: Merge the data into the template – one‑line call creates a single document
    text: '```csharp // Step 3 – perform the merge Document mergedDocument = MailMerger.Merge(template,
      invoiceData); ```'
  - name: Split the merged document into separate files and save each one
    text: '```csharp // Step 4 – split and save each invoice int invoiceNumber = 1;
      foreach (Document singleInvoice in mergedDocument.Split()) { string outputPath
      = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx"; singleInvoice.Save(outputPath);
      } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- MailMerge
- Document Automation
title: Создание нескольких документов Word с Aspose.Words
url: /ru/net/add-content-using-document-builder/generate-multiple-word-documents-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Генерация нескольких документов Word с помощью Aspose.Words

Если вам нужно **генерировать несколько документов Word** на C#, Aspose.Words предоставляет лаконичное API, которое устраняет шаблонный код работы с файлами. Независимо от того, создаёте ли вы систему выставления счетов или вам необходимо подготовить набор персонализированных писем, это руководство покажет, как **создавать счета из шаблона** и **пакетно генерировать файлы Word** всего за несколько строк кода.

Вы узнаете, как:

* Подготовить данные для операции слияния почты.  
* Загрузить шаблон Word, содержащий заполнители `MERGEFIELD`.  
* Объединить данные в один документ и разбить его на отдельные файлы.  
* Сохранить каждый сгенерированный файл с уникальным именем.

Для выполнения не требуется внешних инструментов, кроме библиотеки Aspose.Words for .NET, а полный пример кода работает на .NET 6 или новее.

## Требования и настройка

Перед началом убедитесь, что у вас есть:

| Требование | Причина |
|-------------|--------|
| .NET 6 SDK (или новее) | Код использует современные возможности C#, такие как типизированный `new`. |
| NuGet‑пакет Aspose.Words for .NET | Предоставляет API `Document`, `MailMerger` и `Split`. |
| Шаблон Word (`InvoiceTemplate.docx`) с тегами `MERGEFIELD` | Служит источником для **создания счетов из шаблона**. |
| IDE (Visual Studio, Rider или VS Code) | Для сборки и отладки проекта. |

Установите NuGet‑пакет с помощью следующей команды:

```bash
dotnet add package Aspose.Words
```

Поместите `InvoiceTemplate.docx` в папку, к которой можно обратиться из кода, например `YOUR_DIRECTORY`.

## Как генерировать несколько документов Word с помощью слияния почты

Основная часть решения состоит из четырёх логических шагов. Каждый шаг обёрнут в понятный вызов метода, что делает код лёгким для чтения и поддержки.

### Шаг 1: Подготовьте данные, которые заполнят поля слияния

Механизм слияния почты ожидает коллекцию объектов, имена свойств которых совпадают с именами `MERGEFIELD` в шаблоне. В этом примере мы используем массив анонимных типов, но вы можете заменить его списком строго типизированных DTO.

```csharp
// Step 1 – data preparation
var invoiceData = new[]
{
    new { Name = "Alice", Amount = 123.45 },
    new { Name = "Bob",   Amount = 678.90 }
};
```

**Почему это важно:**  
Предоставление строго типизированного источника данных гарантирует, что каждый заполнитель получит корректное значение, что особенно важно при **пакетной генерации файлов Word** для большого количества получателей.

### Шаг 2: Загрузите шаблон Word, содержащий заполнители MERGEFIELD

```csharp
// Step 2 – load template
Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
```

**Почему это важно:**  
Класс `Document` представляет весь файл Word в памяти. Однократная загрузка шаблона и его повторное использование избавляют от лишних операций ввода‑вывода, когда позже вы **генерируете несколько документов Word**.

### Шаг 3: Объедините данные в шаблоне — однострочный вызов создаёт один документ

```csharp
// Step 3 – perform the merge
Document mergedDocument = MailMerger.Merge(template, invoiceData);
```

`MailMerger.Merge` проходит по коллекции данных, вставляя копию шаблона для каждой строки и заполняя значения `MERGEFIELD`. В результате получается один `Document`, содержащий все счета подряд.

### Шаг 4: Разделите объединённый документ на отдельные файлы и сохраните каждый

```csharp
// Step 4 – split and save each invoice
int invoiceNumber = 1;
foreach (Document singleInvoice in mergedDocument.Split())
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
    singleInvoice.Save(outputPath);
}
```

Расширение `Split()` проходит по объединённому документу и возвращает новый экземпляр `Document` для каждой строки данных. Сохранение каждого `singleInvoice` создаёт отдельный файл, завершая процесс **пакетной генерации файлов Word**.

#### Полный исполняемый пример

Ниже приведена полная программа, связывающая четыре шага. Скопируйте её в новый консольный проект и запустите после корректировки путей.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

class Program
{
    static void Main()
    {
        // Step 1 – prepare data
        var invoiceData = new[]
        {
            new { Name = "Alice", Amount = 123.45 },
            new { Name = "Bob",   Amount = 678.90 }
        };

        // Step 2 – load the template
        Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");

        // Step 3 – merge data into a single document
        Document mergedDocument = MailMerger.Merge(template, invoiceData);

        // Step 4 – split and save each invoice
        int invoiceNumber = 1;
        foreach (Document singleInvoice in mergedDocument.Split())
        {
            string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
            singleInvoice.Save(outputPath);
        }

        System.Console.WriteLine("Invoices generated successfully.");
    }
}
```

**Ожидаемый вывод:**  
Запуск программы создаёт `Invoice_1.docx`, `Invoice_2.docx`, … в указанной директории. Каждый файл содержит данные счета для одного клиента, а заполнители заменены значениями из `invoiceData`.

## Создание счетов из шаблона — обработка распространённых проблем

При **создании счетов из шаблона** могут возникнуть некоторые проблемы. Ниже приведены практические рекомендации по их избежанию.

| Проблема | Решение |
|----------|---------|
| Имена полей шаблона не совпадают с именами свойств | Убедитесь, что имена свойств (`Name`, `Amount`) точно соответствуют тегам `MERGEFIELD` в файле Word. |
| Большие наборы данных вызывают высокое потребление памяти | Обрабатывайте данные порциями: объединяйте подмножество, разделяйте, сохраняйте, затем удаляйте промежуточный документ перед следующей порцией. |
| Специальные символы (например, “&”, “<”) отображаются некорректно | Aspose.Words автоматически экранирует небезопасные для XML символы, но проверьте кодировку шаблона, если вы загружаете его из источника, не использующего UTF‑8. |
| Необходимы пользовательские имена файлов (например, включить имя клиента) | Замените строку `outputPath` на `$"YOUR_DIRECTORY/Invoice_{singleInvoice.MailMergeData[\"Name\"]}.docx"` после извлечения значения поля из разделённого документа. |

## Пакетная генерация файлов Word — соображения по производительности

Если вы планируете **пакетно генерировать файлы Word** для тысяч записей, учитывайте следующие рекомендации:

1. **Повторное использование объекта шаблона** – загрузка шаблона один раз (как показано в Шаге 2) предотвращает повторные чтения с диска.  
2. **Освобождение промежуточных документов** – цикл `foreach` автоматически освобождает память после каждого `singleInvoice.Save`, но при очень больших партиях можно явно вызвать `singleInvoice.Dispose()`.  
3. **Параллелизация шага сохранения** – операция разделения выдаёт независимые объекты `Document`, поэтому можно использовать `Parallel.ForEach` для одновременной записи файлов, если носитель поддерживает параллельный ввод‑вывод.

```csharp
using System.Threading.Tasks;

// ...

Parallel.ForEach(mergedDocument.Split(), (singleInvoice, state, index) =>
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{index + 1}.docx";
    singleInvoice.Save(outputPath);
});
```

**Почему это работает:**  
`Split()` возвращает `IEnumerable<Document>`, который можно безопасно перечислять параллельно, поскольку каждый экземпляр `Document` владеет собственной памятью.

## Ожидаемые результаты и проверка

После завершения программы откройте любой сгенерированный счёт в Microsoft Word:

* Заполнитель `«Name»` заменяется на «Alice» или «Bob».  
* Заполнитель `«Amount»` отображает соответствующее числовое значение, отформатированное согласно формату чисел по умолчанию в документе.  
* Макет страницы, колонтитулы и нижние колонтитулы из оригинального шаблона сохраняются.

Если какой‑либо заполнитель остаётся незаполненным, дважды проверьте имена `MERGEFIELD` в шаблоне относительно имён свойств в `invoiceData`.

## Заключение

Теперь вы знаете, как **генерировать несколько документов Word** с помощью Aspose.Words, как **создавать счета из шаблона** и как эффективно **пакетно генерировать файлы Word**. Паттерн из четырёх шагов — подготовка данных, загрузка шаблона, слияние, разделение и сохранение — покрывает большинство типовых сценариев автоматизации документов.  

Далее вы можете расширить решение, добавив изображения, таблицы или условную логику в шаблон, либо интегрировать процесс в веб‑API, который будет выдавать счета по запросу.

---

![Скриншот генерации нескольких документов Word](generate-multiple-word-documents.png){: .align-center alt="Скриншот результата генерации нескольких документов Word"}

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Добавление и вставка содержимого в документы Word с помощью Aspose.Words](/words/english/net/document-sections/append-section-content/)
- [Объединение нескольких файлов Word с помощью Aspose.Words для Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)
- [Применение форматирования строк в документах Word с помощью Aspose.Words для .NET](/words/english/net/working-with-table-styles-and-formatting/apply-row-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}