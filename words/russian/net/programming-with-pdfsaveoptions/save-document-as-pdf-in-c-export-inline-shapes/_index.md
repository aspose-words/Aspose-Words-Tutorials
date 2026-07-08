---
category: general
date: 2026-06-30
description: Сохранить документ как PDF в C#, преобразуя docx в PDF и обрабатывая
  встроенные объекты. Следуйте этому пошаговому руководству, чтобы правильно экспортировать
  Word в PDF.
draft: false
keywords:
- save document as pdf
- convert docx to pdf
- convert word to pdf
- save word as pdf
- how to export inline
language: ru
og_description: Сохранить документ в PDF в C# с помощью Aspose.Words. Узнайте, как
  конвертировать DOCX в PDF и экспортировать плавающие объекты как встроенные элементы.
og_title: Сохранить документ в PDF в C# – экспорт встроенных фигур
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  headline: Save Document as PDF in C# – Export Inline Shapes
  type: TechArticle
- description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  name: Save Document as PDF in C# – Export Inline Shapes
  steps:
  - name: '**.NET 6+** (or .NET Framework 4.6+).'
    text: '**.NET 6+** (or .NET Framework 4.6+).'
  - name: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
    text: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
  - name: A sample `input.docx` that contains at least one floating picture or text
      box.
    text: A sample `input.docx` that contains at least one floating picture or text
      box.
  type: HowTo
tags:
- C#
- PDF
- Aspose.Words
title: Сохранить документ как PDF в C# – экспорт встроенных фигур
url: /ru/net/programming-with-pdfsaveoptions/save-document-as-pdf-in-c-export-inline-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить документ как PDF в C# – экспорт встроенных фигур

Когда‑нибудь задумывались, как **save document as PDF** напрямую из C# без потери макета плавающих изображений? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда файл Word содержит картинки или текстовые поля, плавающие над текстом — эти элементы часто исчезают или смещаются, если просто вызвать `doc.Save("output.pdf")`.  

В этом руководстве мы пройдем точные шаги, чтобы **convert docx to pdf**, сохраняя плавающие объекты как встроенные элементы, фактически отвечая на вопрос *how to export inline* shapes. К концу вы получите готовый к запуску фрагмент кода, который **save word as pdf** так, как вы ожидаете.

## Что вы узнаете

- Загрузить файл `.docx` с помощью Aspose.Words (или любой совместимой библиотеки).  
- Настроить `PdfSaveOptions` так, чтобы плавающие фигуры стали встроенными.  
- Выполнить операцию сохранения, чтобы **convert word to pdf**.  
- Обработать распространённые проблемы, такие как отсутствие шрифтов или большие изображения.  

Никаких внешних инструментов, никакой ручной работы с COM‑объектами автоматизации Word — только чистый, чистый C# код.

## Предварительные требования

1. **.NET 6+** (or .NET Framework 4.6+).  
2. The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).  
3. Пример `input.docx`, содержащий хотя бы одну плавающую картинку или текстовое поле.  

Если вы используете другую PDF‑библиотеку, концепции остаются теми же — ищите свойство, похожее на `ExportFloatingShapesAsInlineTag`.

## Шаг 1: Загрузка исходного документа – основы сохранения документа как PDF  

Первое, что нужно сделать, — загрузить файл Word в память. Здесь и начинается процесс **save document as pdf**.

```csharp
using Aspose.Words;

// Step 1: Load the source DOCX file
string inputPath = @"C:\MyDocs\input.docx";
Document doc = new Document(inputPath);
```

*Почему это важно*: Загрузка документа проверяет, что файл существует, и разбирает все его части (стили, изображения, колонтитулы). Если загрузка не удалась, последующее преобразование в PDF никогда не выполнится, поэтому обработка ошибок здесь экономит много времени на отладку.

## Шаг 2: Настройка параметров сохранения PDF – как экспортировать встроенные фигуры  

Теперь мы указываем библиотеке, как обрабатывать плавающие фигуры. Ключевой флаг — `ExportFloatingShapesAsInlineTag`. Установка его в `true` заставляет каждую плавающую картинку или текстовое поле отображаться **inline**, как обычный фрагмент абзаца.

```csharp
// Step 2: Prepare PDF save options
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // true → inline (text‑flow); false → keep as block‑level floating objects
    ExportFloatingShapesAsInlineTag = true,

    // Optional: improve compatibility with older PDF viewers
    Compliance = PdfCompliance.PdfA1b
};
```

*Почему это важно*: По умолчанию Aspose.Words оставляет плавающие фигуры на их исходных позициях, что может привести к их обрезке или исчезновению в результирующем PDF. Включение экспорта как inline гарантирует, что фигуры станут частью потока текста, сохраняя визуальную точность во всех PDF‑просмотрщиках.

## Шаг 3: Сохранение документа как PDF – преобразование Word в PDF  

После загрузки документа и установки параметров последний шаг — однострочная команда, которая действительно **save document as pdf**.

```csharp
// Step 3: Save the document as a PDF file
string outputPath = @"C:\MyDocs\FloatingShapes.pdf";
doc.Save(outputPath, pdfOptions);
```

Вот и всё! Вызов `doc.Save` записывает PDF, который отражает оригинальный макет Word, при этом плавающие изображения теперь аккуратно встроены в текст.

## Полный рабочий пример  

Объединив всё вместе, представляем автономное консольное приложение, которое вы можете скопировать, скомпилировать и запустить:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToPdfInlineExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\MyDocs\input.docx";
            string outputPath = @"C:\MyDocs\FloatingShapes.pdf";

            // Load the DOCX file
            Document doc = new Document(inputPath);

            // Configure PDF options to export floating shapes as inline
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                ExportFloatingShapesAsInlineTag = true,
                Compliance = PdfCompliance.PdfA1b // optional, ensures PDF/A‑1b compliance
            };

            // Save as PDF
            doc.Save(outputPath, pdfOptions);

            Console.WriteLine($"Document successfully saved as PDF: {outputPath}");
        }
    }
}
```

**Ожидаемый вывод** (в консоли):

```
Document successfully saved as PDF: C:\MyDocs\FloatingShapes.pdf
```

Откройте `FloatingShapes.pdf` в любом просмотрщике; вы увидите, что ранее плавающая картинка теперь плотно встроена в абзац, как и задумано.

## Почему экспортировать плавающие фигуры как Inline?  

Плавающие фигуры удобны в Word, потому что позволяют размещать изображения где угодно на странице. Однако PDF — это *ориентированный на страницу* формат, в нём нет понятия «float», как в Word. Когда движок преобразования оставляет их как блочные объекты, они могут:

- Перекрывать другое содержимое.  
- Обрезаться по краям страницы.  
- Полностью исчезать в старых PDF‑просмотрщиках.  

Преобразуя их в элементы **inline**, вы гарантируете, что PDF сохраняет порядок чтения и что скрин‑ридеры могут правильно интерпретировать документ — важно для соответствия требованиям доступности.

## Распространённые подводные камни при конвертации Docx в PDF  

| Проблема | Симптом | Решение |
|----------|---------|---------|
| Отсутствие шрифтов | Текст отображается как «□» или используется шрифт Arial по умолчанию | Встроить шрифты с помощью `PdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.Always`. |
| Большие изображения вызывают всплеск памяти | Исключение Out‑of‑memory при большом DOCX | Уменьшить размер изображений перед конвертацией или установить `PdfSaveOptions.ImageCompression = PdfImageCompression.Jpeg;` |
| Экспорт как inline не применён | Плавающие фигуры всё ещё плавают в PDF | Убедитесь, что используете последнюю версию Aspose.Words; имя свойства изменилось в более старых версиях. |
| Ошибки пути | `FileNotFoundException` | Используйте `Path.Combine` и убедитесь, что каталог существует (`Directory.CreateDirectory`). |

## Продвинутое: экспорт только определённых фигур как Inline  

Иногда требуется *избирательный* экспорт в inline — только определённые картинки, а не все. Это можно сделать, пройдясь по узлам документа перед сохранением:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.WrapType == WrapType.Inline)
        continue; // already inline

    // Example condition: only convert pictures larger than 300px
    if (shape.HasImage && shape.Width > 300)
        shape.WrapType = WrapType.Inline;
}
```

После настройки `WrapType` выполните тот же вызов `doc.Save`. Это даст вам детальный контроль над поведением **how to export inline**.

## Профессиональные советы и лучшие практики  

- **Pro tip:** Установите `pdfOptions.Compliance = PdfCompliance.PdfA1b`, если ваша организация требует PDF/A для архивирования.  
- **Watch out for:** Скрытые секции (`SectionBreakContinuous`), которые могут скрывать плавающие фигуры; выполните `doc.UpdatePageLayout()` перед сохранением.  
- **Performance tip:** Переиспользуйте один экземпляр `PdfSaveOptions`, если конвертируете много файлов в пакете; это уменьшает накладные расходы на выделение памяти.  
- **Testing:** Всегда открывайте полученный PDF как минимум в двух просмотрщиках (Adobe Reader, Edge), чтобы проверить согласованность макета.  

## Визуальный обзор  

![Схема сохранения документа как PDF, показывающая шаги загрузка → настройка → сохранение](https://example.com/flowchart.png "Схема сохранения документа как PDF")

*Alt text:* **Схема сохранения документа как PDF** — иллюстрирует трёхшаговый процесс загрузки DOCX, настройки экспорта inline и сохранения в PDF.

## Заключение  

Теперь у вас есть надёжный, готовый к продакшену метод **save document as PDF** в C#, который правильно обрабатывает плавающие объекты. Настроив `ExportFloatingShapesAsInlineTag`, вы гарантируете, что каждая картинка, диаграмма или текстовое поле становятся частью потока текста, устраняя типичные сбои, присущие наивному подходу **convert word to pdf**.  

Попробуйте: конвертируйте сложный отчёт с несколькими плавающими изображениями, а затем поэкспериментируйте с избирательной логикой inline, чтобы оставить некоторые фигуры плавающими там, где им место. В следующий раз, когда понадобится **convert docx to pdf**, вы точно будете знать, как сохранить каждый визуальный элемент.  

Не стесняйтесь оставить комментарий, если столкнётесь с проблемами или обнаружите хитрый приём. Счастливого кодинга!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Сохранить docx как pdf с Aspose.Words – Полное руководство C#](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)
- [Сохранить Word как PDF с Aspose.Words – Полное руководство C#](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Конвертировать word в pdf в C# с использованием Aspose.Words – Руководство](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}