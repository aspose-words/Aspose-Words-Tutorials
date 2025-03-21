---
title: Встроить подмножество шрифтов в PDF-документ
linktitle: Встроить подмножество шрифтов в PDF-документ
second_title: API обработки документов Aspose.Words
description: Уменьшите размер файла PDF, встраивая только необходимые подмножества шрифтов с помощью Aspose.Words для .NET. Следуйте нашему пошаговому руководству, чтобы эффективно оптимизировать ваши PDF-файлы.
weight: 10
url: /ru/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Встроить подмножество шрифтов в PDF-документ

## Введение

Вы когда-нибудь замечали, что некоторые файлы PDF намного больше других, даже если они содержат схожее содержимое? Виновником часто являются шрифты. Встраивание шрифтов в PDF гарантирует, что он будет выглядеть одинаково на любом устройстве, но это также может раздуть размер файла. К счастью, Aspose.Words для .NET предлагает удобную функцию для встраивания только необходимых подмножеств шрифтов, сохраняя ваши PDF-файлы компактными и эффективными. Это руководство проведет вас через этот процесс шаг за шагом.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующее:

-  Aspose.Words для .NET: Вы можете скачать его[здесь](https://releases.aspose.com/words/net/).
- Среда .NET: убедитесь, что у вас есть рабочая среда разработки .NET.
- Базовые знания C#: знакомство с программированием на C# поможет вам в дальнейшем изучении.

## Импорт пространств имен

Чтобы использовать Aspose.Words для .NET, вам нужно импортировать необходимые пространства имен в ваш проект. Добавьте их в начало вашего файла C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Шаг 1: Загрузите документ

 Сначала нам нужно загрузить документ Word, который мы хотим преобразовать в PDF. Это делается с помощью`Document` класс предоставлен Aspose.Words.

```csharp
// Путь к каталогу документов.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Этот фрагмент кода загружает документ, расположенный по адресу`dataDir` . Обязательно замените`"YOUR DOCUMENT DIRECTORY"` с фактическим путем к вашему документу.

## Шаг 2: Настройте параметры сохранения PDF-файла

 Далее мы настраиваем`PdfSaveOptions` чтобы гарантировать, что будут внедрены только необходимые подмножества шрифтов. Установив`EmbedFullFonts` к`false`, мы говорим Aspose.Words встраивать только глифы, используемые в документе.

```csharp
// Выходной PDF-файл будет содержать подмножества шрифтов документа.
// В шрифты PDF включены только те глифы, которые используются в документе.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Этот небольшой, но важный шаг помогает значительно уменьшить размер PDF-файла.

## Шаг 3: Сохраните документ как PDF.

 Наконец, мы сохраняем документ в формате PDF с помощью`Save` метод, применяя настроенный`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 Этот код сгенерирует PDF-файл с именем`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` в указанном каталоге, со встроенными только необходимыми подмножествами шрифтов.

## Заключение

И вот оно! Выполнив эти простые шаги, вы сможете эффективно уменьшить размер ваших PDF-файлов, встраивая только необходимые подмножества шрифтов с помощью Aspose.Words for .NET. Это не только экономит место на диске, но и обеспечивает более быструю загрузку и лучшую производительность, особенно для документов с обширным количеством шрифтов.

## Часто задаваемые вопросы

### Почему в PDF-файл следует встраивать только подмножества шрифтов?
Внедрение только необходимых подмножеств шрифтов может значительно уменьшить размер файла PDF без ущерба для внешнего вида и читабельности документа.

### Могу ли я вернуться к внедрению полных шрифтов при необходимости?
 Да, можно. Просто установите`EmbedFullFonts`собственность`true` в`PdfSaveOptions`.

### Поддерживает ли Aspose.Words for .NET другие функции оптимизации PDF?
Конечно! Aspose.Words для .NET предлагает ряд возможностей для оптимизации PDF-файлов, включая сжатие изображений и удаление неиспользуемых объектов.

### Какие типы шрифтов можно встроить с помощью Aspose.Words для .NET?
Aspose.Words для .NET поддерживает внедрение подмножеств для всех шрифтов TrueType, используемых в документе.

### Как проверить, какие шрифты встроены в мой PDF-файл?
Вы можете открыть PDF-файл в Adobe Acrobat Reader и проверить свойства на вкладке «Шрифты», чтобы увидеть встроенные шрифты.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
