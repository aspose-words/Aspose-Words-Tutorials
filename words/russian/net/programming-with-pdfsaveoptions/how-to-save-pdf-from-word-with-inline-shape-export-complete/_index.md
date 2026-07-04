---
category: general
date: 2026-06-02
description: Как сохранить PDF из DOCX с помощью Aspose.Words, экспортировать фигуры
  как встроенные теги span и преобразовать Word в PDF всего за несколько шагов.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: ru
og_description: Как сохранить PDF из документа Word с помощью Aspose.Words, экспортируя
  плавающие объекты как встроенные span‑теги для чистого результата преобразования
  Word в PDF.
og_title: Как сохранить PDF из Word – учебник по экспорту встроенных объектов
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Как сохранить PDF из Word с экспортом встроенных фигур — полное руководство
url: /ru/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как сохранить PDF из Word с экспортом встроенных фигур – Полное руководство

Когда‑нибудь задавались вопросом, **как сохранить PDF** из файла Word, при этом удерживая каждую плавающую форму аккуратно в потоке? Вы не одиноки. Во многих корпоративных приложениях нам нужно *конвертировать Word в PDF* без появления смещённых изображений или лишних графических объектов. Хорошая новость? Aspose.Words делает это без проблем, и вы даже можете указать библиотеке **экспортировать фигуры как встроенные `<span>` теги**, чтобы PDF выглядел точно как оригинальный DOCX.

В этом руководстве мы пройдем весь процесс — загрузку DOCX, настройку `PdfSaveOptions` и окончательное сохранение чистого PDF. К концу вы будете знать **как сохранить PDF**, **как сохранить docx как pdf**, и даже **как экспортировать фигуры** с использованием *inline span tags*.

## Что понадобится

- **Aspose.Words for .NET** (последняя версия, 24.x на момент написания).  
- **.NET 6.0** или новее — код также работает на .NET Framework 4.7.2, но .NET 6 — оптимальный вариант.  
- Простой документ Word, содержащий хотя бы одну плавающую форму (изображение, текстовое поле или рисунок).  
- Любая IDE по вашему выбору (Visual Studio, Rider, VS Code + C# extension).  

Вот и всё — никаких дополнительных пакетов NuGet, без заморочек с COM interop. Готовы? Погрузимся.

## Шаг 1: Настройте проект и добавьте Aspose.Words

Сначала создайте консольное приложение (или интегрируйте код в ваш существующий сервис).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Если вы используете Visual Studio, вы можете добавить пакет через UI NuGet Package Manager — просто найдите *Aspose.Words*.

## Шаг 2: Загрузите исходный документ

Теперь, когда библиотека подключена, мы можем загрузить DOCX. Это первая конкретная действие части **how to save pdf** — загрузка источника в память.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Почему это важно:** Загрузка файла проверяет правильность пути и то, что Aspose может разобрать структуру Word. Если файл содержит плавающие формы, они станут частью дерева узлов объекта `Document`.

## Шаг 3: Настройте параметры сохранения PDF — экспорт фигур как встроенных тегов

Это суть **how to export shapes**. По умолчанию Aspose.Words рендерит плавающие формы как отдельные объекты в PDF, что может сместить макет. Установка `ExportFloatingShapesAsInlineTag` в `true` заставляет движок оборачивать каждую форму во встроенный элемент `<span>`, сохраняя поток.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Зачем включать этот флаг?** Представьте контракт с полем подписи, которое плавает над текстом. При конвертации в PDF без этой настройки поле может оказаться на другой странице. Встроенные `<span>` теги фиксируют форму к окружающему абзацу, создавая точную визуальную копию.

## Шаг 4: Сохраните документ как PDF

Наконец, вызываем `doc.Save` с параметрами, которые мы только что создали. Это момент, когда вы действительно **save docx as pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Запустите программу (`dotnet run`) и проверьте `output.pdf`. Вы должны увидеть ваши плавающие формы, отрисованные встроенно, точно так же, как они выглядели в Word.

## Шаг 5: Проверьте результат — быстрый чек‑лист

1. **Весь текст присутствует** — нет пропущенных абзацев.  
2. **Плавающие формы находятся там, где должны** — они теперь часть текстового потока.  
3. **Размер PDF разумный** — экспорт как встроенных тегов обычно уменьшает размер файла по сравнению с отдельными потоками изображений.  

Если что‑то выглядит неправильно, проверьте, действительно ли исходный DOCX использует *плавающие* формы (правый клик → Layout → “In line with text” vs “Square/Behind text”). Переключение формы в “In line” перед конвертацией тоже работает, но опция inline‑tag дает вам контроль без изменения оригинального файла.

## Особые случаи и часто задаваемые вопросы

### Что если мой документ содержит **SmartArt** или **Charts**?

SmartArt и диаграммы рассматриваются как графические объекты. Флаг `ExportFloatingShapesAsInlineTag` всё равно обернёт их в теги `<span>`, но сложные графики могут потерять часть точности. В таких случаях рассмотрите возможность сначала экспортировать диаграмму как изображение (`Chart.ToImage()`) и затем вставить её встроенно.

### Могу ли я **сохранять гиперссылки** и **закладки**?

Конечно. Эти элементы не затрагиваются настройкой `ExportFloatingShapesAsInlineTag`. Aspose.Words автоматически сохраняет всю информацию о гиперссылках и закладках.

### Как я могу **изменить сжатие PDF** или **встроить шрифты**?

`PdfSaveOptions` предоставляет множество дополнительных свойств:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

## Полный рабочий пример (готовый к копированию)

Ниже полная программа, которую вы можете скопировать в `Program.cs`. Замените `YOUR_DIRECTORY` реальным путём к папке.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Ожидаемый вывод в консоли:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Откройте `output.pdf` — вы увидите оригинальный макет, где каждая плавающая форма аккуратно размещена внутри текстового потока.

## Заключение

Мы рассмотрели **how to save PDF** из документа Word, обеспечивая, что плавающие формы становятся встроенными тегами `<span>`. Загрузив DOCX, настроив `PdfSaveOptions` и вызвав `doc.Save`, вы надёжно можете **save docx as pdf** и **convert word to pdf** без сюрпризов в макете.  

Следующие шаги? Попробуйте сочетать этот подход с соблюдением **PDF/A** для архивирования, или пакетно обработать папку файлов DOCX простым циклом `foreach`. Вы также можете исследовать **custom rendering** (например, добавление водяных знаков), используя API `DocumentVisitor` Aspose.Words.  

Есть дополнительные вопросы о работе с фигурами, встраивании шрифтов или оптимизации производительности? Оставьте комментарий ниже, и удачной разработки!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как сохранить документ как PDF с Aspose.Words для Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Конвертировать Word в PDF с Aspose.Words для Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf — Конвертировать DOCX в PDF на Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}