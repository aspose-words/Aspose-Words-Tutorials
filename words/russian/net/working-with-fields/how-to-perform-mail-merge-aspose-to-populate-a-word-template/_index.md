---
category: general
date: 2026-09-11
description: Mail merge aspose позволяет загружать шаблон Word и заполнять его данными,
  автоматизируя генерацию документов для создания персонализированных писем.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: ru
lastmod: 2026-09-11
og_description: Mail merge aspose позволяет загружать шаблон Word и заполнять его,
  упрощая генерацию документов, чтобы вы могли быстро создавать персонализированные
  письма.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail merge Aspose: заполните шаблон Word за несколько минут'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Как выполнить слияние почты с помощью Aspose для заполнения шаблона Word
url: /ru/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как выполнить mail merge aspose для заполнения шаблона Word

Если вам нужно **mail merge aspose** для создания партии персонализированных писем, это руководство покажет, как загрузить шаблон Word, заполнить его данными и автоматизировать генерацию документов в несколько строк кода C#. Независимо от того, создаёте ли вы систему рассылки или инструмент отчётности, приведённый ниже полный пример позволяет создавать персонализированные письма без написания ручной логики слияния.

Вы узнаете, как **load word template**, использовать low‑code‑класс `MailMerger` и **populate word template** анонимным источником данных. К концу урока у вас будет готовое консольное приложение, которое генерирует объединённый документ Word, готовый к отправке по электронной почте, печати или архивированию.

## Prerequisites

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия, установленная  
* Действительная лицензия Aspose.Words for .NET (или бесплатный оценочный ключ)  
* Пакет NuGet `Aspose.Words` (версия 23.10 или новее), установленный в вашем проекте  
* Файл Word (`MailMergeTemplate.docx`), содержащий заполнители MERGEFIELD, такие как **«Name»** и **«Age»**  

Шаблон можно создать в Microsoft Word, вставив *Insert → Quick Parts → Field → MergeField* и задав полям имена, точно соответствующие именам свойств в вашем источнике данных.

## Step 1 – Prepare the data source for the mail merge

Low‑code‑слияние работает с любой перечисляемой коллекцией. В этом примере мы используем массив анонимных объектов, но вы также можете передать `DataTable`, список POCO или данные, считанные из базы данных.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Why this matters:**  
Имя свойства каждого объекта (`Name`, `Age`) должно совпадать с MERGEFIELD в шаблоне. Класс `MailMerger` автоматически сопоставляет свойства с полями, устраняя необходимость в ручных событиях `FieldMerging`.

## Step 2 – Load the Word template that contains MERGEFIELDs

Загрузка шаблона проста с помощью класса `Document`. Путь может быть абсолютным или относительным к рабочему каталогу исполняемого файла.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Pro tip:**  
Если вы запускаете код из Visual Studio, установите для файла шаблона параметр *Copy to Output Directory* в **Copy always**. Это гарантирует, что файл будет доступен при выполнении скомпилированного бинарника.

## Step 3 – Create a MailMerger instance bound to the template

Класс `MailMerger` находится в пространстве имён `Aspose.Words.LowCode` и предоставляет единственный метод `Execute`, принимающий источник данных.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Why use MailMerger?**  
`MailMerger` скрывает boilerplate‑вызовы `MailMerge.Execute`, обрабатывая обнаружение полей, привязку данных и клонирование документа внутри. Это делает код идеальным для сценариев **automate document generation**, где требуется чистое low‑code‑решение.

## Step 4 – Execute the low‑code merge using the prepared data

Вызов `Execute` возвращает новый объект `Document`, содержащий


## What Should You Learn Next?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Rename Word Merge Fields with Aspose.Words for Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}