---
category: general
date: 2026-02-13
description: Сохраните DOCX в PDF, сохраняя плавающие фигуры. Узнайте, как конвертировать
  Word в PDF, экспортировать фигуры и обрабатывать особые случаи в C#.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: ru
og_description: Сохранить docx в pdf, сохраняя плавающие объекты. Это руководство
  показывает, как конвертировать Word в PDF, экспортировать объекты и устранять распространённые
  проблемы.
og_title: Сохранить docx в pdf с помощью Shape Export – Полное руководство
tags:
- Aspose.Words
- C#
- PDF conversion
title: Сохранить docx в pdf с помощью Shape Export – Полное руководство
url: /ru/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить docx как pdf – Полный‑стековый учебник (C#)

Когда‑нибудь вам нужно было **save docx as pdf** и сохранить плавающие диаграммы точно такими же? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда формы Word исчезают или искажаются после конвертации. Хорошая новость? С несколькими строками C# вы можете указать библиотеке рассматривать каждую форму как блочный элемент, и результат будет точной копией PDF.

В этом руководстве мы пройдем весь процесс: загрузку файла `.docx`, настройку параметров **convert word to pdf**, чтобы формы экспортировались корректно, и, наконец, запись PDF на диск. К концу вы узнаете **how to export shapes**, поймете компромиссы разных режимов экспорта и получите готовый к запуску пример кода, который можно вставить в любой проект .NET.

> **What you’ll get:** полный, исполняемый пример, объяснения *почему* каждый параметр важен, советы для крайних случаев и идеи по расширению решения (например, обработка изображений, пользовательские шрифты или PDF с паролем).

## Требования

- .NET 6+ (или .NET Framework 4.7+). API, который мы используем, работает в обеих средах.
- Aspose.Words for .NET (бесплатная пробная версия или лицензия). Установите через NuGet: `Install-Package Aspose.Words`.
- Документ Word (`input.docx`), содержащий плавающие формы (текстовые поля, автофигуры, SmartArt и т.д.).
- Visual Studio 2022 или любая другая IDE по вашему выбору.

Другие сторонние библиотеки не требуются.

## Пошаговая реализация

Ниже для каждого шага вы увидите короткий фрагмент кода, простое объяснение на английском и примечание о **how to export shapes** правильно.

### ## Шаг 1 – Загрузка исходного документа (save docx as pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Почему это важно:* Класс `Document` представляет весь файл Word в памяти. Если пропустить этот шаг, нечего будет конвертировать, и последующие параметры PDF не будут иметь над чем работать.

### ## Шаг 2 – Настройка параметров сохранения PDF (how to export shapes)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Объяснение**

- `PdfSaveOptions` — это «набор параметров», который сообщает Aspose.Words, как переводить конструкции Word в PDF.
- Свойство **ExportFloatingShapesAsInlineTag** имеет три возможных значения:
  1. **Inline** — формы становятся встроенными элементами (часто сжатыми в окружающий текст).
  2. **Block** — каждая форма размещается в собственном блоке, что является самым безопасным способом сохранить оригинальный внешний вид.
  3. **Auto** — библиотека решает автоматически (не всегда выбирает лучший вариант).

Выбор **Block** рекомендуется, когда вам *нужно экспортировать формы* точно так, как они выглядят в оригинальном документе. Это предотвращает проблему «форма исчезает», с которой сталкиваются многие при простом вызове `doc.Save("out.pdf")`.

### ## Шаг 3 – Сохранение документа как PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*What you’ll see:* После выполнения этой строки файл `FloatingShapes.pdf` окажется в `C:\MyFolder`. Откройте его, и вы должны увидеть каждый текстовый блок, выноску и SmartArt, расположенные точно так же, как в исходном `.docx`.

## Полный рабочий пример

Ниже представлен **complete program**, который можно собрать и запустить как консольное приложение. Включены все необходимые `using`‑директивы и комментарии для ясности.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Ожидаемый вывод**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Откройте полученный PDF и убедитесь, что все формы сохраняют свои исходные позиции. Если какая‑то форма всё ещё выглядит некорректно, дважды проверьте, что она действительно *плавающая* (а не встроенное изображение) в Word.

## Часто задаваемые вопросы и особые случаи

| Question | Answer |
|----------|--------|
| **Can I export shapes as inline instead of block?** | Да — установите `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline`. Это может быть полезно для простых макетов, но ожидайте более плотного потока текста и возможных перекрытий. |
| **What if my document contains images inside shapes?** | Тот же параметр работает; Aspose.Words растеризует форму вместе с её изображением. Для наивысшего качества также включите `PdfSaveOptions.JpegQuality`, если требуется лучшая компрессия изображений. |
| **Does this work with password‑protected DOCX files?** | Загрузите документ с помощью объекта `LoadOptions`, который предоставляет пароль, затем продолжайте как обычно. |
| **Can I convert multiple DOCX files in a batch?** | Оберните логику из трёх шагов в цикл `foreach` по списку файлов. Не забудьте переиспользовать `PdfSaveOptions` для повышения производительности. |
| **Is the PDF compatible with older readers (Acrobat 7)?** | По умолчанию Aspose.Words создает файлы PDF 1.7. Установите `pdfOptions.Compliance = PdfCompliance.PdfA1b` для архивных PDF, совместимых со старыми читателями. |

## Профессиональные советы и распространённые подводные камни

- **Pro tip:** Если вы замечаете небольшие вертикальные сдвиги после конвертации, попробуйте установить `pdfOptions.UsePdfDocumentStructure = true`. Это заставит PDF‑движок учитывать иерархию макета Word.
- **Watch out for:** Документы, в которых плавающие формы смешаны с привязанными таблицами. В некоторых случаях экспорт в блоке может перенести таблицу на новую страницу; смягчить это можно, скорректировав `pdfOptions.PageSetup` перед сохранением.
- **Performance note:** Переиспользование одного экземпляра `PdfSaveOptions` для множества файлов снижает нагрузку на сборщик мусора и ускоряет пакетные конвертации.

## Визуальная справка

Ниже схематичный скриншот (заполнитель), показывающий «до/после» документа с плавающим текстовым полем.

![save docx as pdf example with floating shapes](image-placeholder.png "save docx as pdf example with floating shapes")

*Изображение демонстрирует, как форма остаётся точно на том же месте в оригинальном файле Word после конвертации.*

## Итоги

Мы рассмотрели **how to save docx as pdf**, сохраняя каждую плавающую форму неизменной, изучили важные настройки **convert word to pdf** и ответили на самые частые вопросы о “**how to export shapes**”. Полный пример кода готов к вставке в любой проект C#, а дополнительные настройки дают гибкость для реальных сценариев, таких как пакетная обработка или соответствие PDF/A.

### Следующие шаги

- Попробуйте **convert word document pdf** с разными уровнями совместимости (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`), чтобы соответствовать нормативным требованиям.
- Поэкспериментируйте с **how to convert docx pdf** для файлов, защищённых паролем — добавьте `LoadOptions` с паролем и `PdfSaveOptions` с `EncryptionDetails`.
- Исследуйте другие форматы вывода (например, XPS, HTML), используя тот же объект `Document`; единственное, что меняется, — аргумент формата в методе `Save`.

Есть дополнительные вопросы? Оставьте комментарий, и счастливого кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}