---
category: general
date: 2026-03-06
description: Перехватывайте предупреждения о шрифтах при загрузке документа Word в
  C#. Узнайте, как обнаруживать отсутствующие шрифты, проверять шрифты документа и
  эффективно обрабатывать недостающие шрифты.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: ru
og_description: Перехватывайте предупреждения о шрифтах при загрузке документа Word
  в C#. Этот учебник показывает, как обнаружить отсутствующие шрифты, проверить шрифты
  документа и обработать их отсутствие.
og_title: Перехват предупреждений о шрифтах в C# — Полное руководство
tags:
- Aspose.Words
- C#
- Font Management
title: Перехват предупреждений о шрифтах в C# – Полное руководство
url: /ru/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Захват предупреждений о шрифтах в C# – Полное руководство

Когда‑нибудь нужно было **захватывать предупреждения о шрифтах** при обработке документа Word? Захват таких предупреждений важен для **обнаружения отсутствующих шрифтов** и гарантии того, что итоговый результат выглядит точно так, как вы задумали.  

В этом руководстве мы пройдем практический, сквозной пример, который загружает файл `.docx`, отслеживает процесс загрузки и сообщает о любых заменах шрифтов. К концу вы узнаете, как **безопасно загрузить документ Word**, **проверить шрифты документа** и **обработать отсутствующие шрифты** без неожиданностей во время выполнения.

## Что вы узнаете

- Как прикрепить сборщик предупреждений к `Document` из Aspose.Words.  
- Какие типы предупреждений указывают на отсутствующий или заменённый шрифт.  
- Способы логировать или реагировать на эти предупреждения в приложении промышленного уровня.  
- Советы по настройке пользовательских источников шрифтов, если нужно **корректно обрабатывать отсутствующие шрифты**.

> **Требование:** У вас есть действующая лицензия Aspose.Words for .NET (или вы используете бесплатную trial‑версию) и среда разработки .NET (Visual Studio, Rider или VS Code). Других библиотек не требуется.

---

## Захват предупреждений о шрифтах – пошагово

Ниже приведён полностью готовый к запуску код. Каждый раздел вынесен в отдельный шаг, чтобы вы могли копировать‑вставлять, экспериментировать и расширять логику.

![Capture font warnings diagram](image.png "Diagram showing warning collection"){: alt="диаграмма сбора предупреждений о шрифтах"}

### Шаг 1: Загрузка документа Word

Сначала нам нужно **загрузить документ Word**, который может содержать шрифты, не установленные на текущей машине. Конструктор `Document` делает основную работу, но мы оставим вызов изолированным, чтобы при необходимости позже заменить его на поток или массив байтов.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Почему это важно:** Загрузка документа без обработчика предупреждений приводит к тихому игнорированию любой замены шрифта. Установив `WarningCallback` *до* загрузки, мы гарантируем, что увидим каждое предупреждение `FontSubstitution`, которое возникнет.

### Шаг 2: Прикрепление сборщика предупреждений

Класс `WarningInfoCollector` – это встроенная реализация `IWarningCallback`. Он просто сохраняет каждое предупреждение в список, который мы позже можем проанализировать.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Профессиональный совет:** Если вам нужно **обрабатывать отсутствующие шрифты** более агрессивно (например, прервать загрузку или заменить их конкретным запасным шрифтом), замените `Console.WriteLine` на собственную логику — выбросьте исключение, запишите в файл или добавьте пользовательский источник шрифтов.

### Шаг 3: Проверка результата

Запустите программу из консоли. Если ваш `input.docx` использует шрифт, который не установлен, вы увидите строки вроде:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Если вывод отсутствует, значит документ использовал только уже доступные шрифты **или** Aspose.Words нашёл подходящий шрифт в своей встроенной коллекции запасных вариантов. В любом случае вы успешно **проверили шрифты документа**.

---

## Обнаружение отсутствующих шрифтов без лицензии (бесплатная trial‑версия)

Даже если вы используете 30‑дневную trial‑версию, механизм предупреждений работает точно так же. Единственное отличие — trial добавляет водяной знак к генерируемому выводу, что **не влияет** на сбор предупреждений. Поэтому вы можете безопасно **обнаруживать отсутствующие шрифты**, прежде чем решать, покупать полную лицензию.

---

## Обработка отсутствующих шрифтов — расширенные варианты

Иногда требуется предоставить свои файлы шрифтов (например, фирменные шрифты компании), чтобы замена никогда не происходила. Aspose.Words позволяет регистрировать пользовательские папки со шрифтами:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Разместите этот код **до** загрузки документа, если хотите, чтобы загрузчик учитывал эти шрифты уже на этапе начального парсинга. Это самый надёжный способ **обрабатывать отсутствующие шрифты**, не полагаясь на системные шрифты по умолчанию.

---

## Распространённые ошибки и как их избежать

| Ошибка | Почему происходит | Как исправить |
|--------|-------------------|---------------|
| **Сборщик предупреждений прикреплён после загрузки** | Документ уже разобран, поэтому предупреждения не записываются. | Прикрепите `WarningCallback` **до** вызова `new Document(path)`. |
| **Появляются только общие предупреждения** | Вы отфильтровали неправильный `WarningType`. | Используйте `WarningType.FontSubstitution`, чтобы сосредоточиться на проблемах со шрифтами. |
| **Нет вывода, хотя шрифты отсутствуют** | Aspose.Words нашёл встроенный запасной шрифт (например, Arial). | Отключите встроенные запасные варианты через `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;`. |
| **Падение производительности при сканировании больших документов** | Сбор всех предупреждений может быть дорогим. | Ограничьте сбор только `FontSubstitution` или обрабатывайте предупреждения пакетами. |

---

## Полный рабочий пример (готов к копированию)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Ожидаемый вывод в консоли** (при двух отсутствующих шрифтах):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Если консоль молчит, кроме сообщения «Document loaded successfully», вы **проверили шрифты документа** и не нашли отсутствующих.

---

## Заключение

Мы показали, как **захватывать предупреждения о шрифтах** в C# с помощью Aspose.Words, надёжный способ **обнаруживать отсутствующие шрифты**, **безопасно загружать документ Word**, **проверять шрифты документа** и **обрабатывать отсутствующие шрифты** через пользовательские источники шрифтов.  

Имея этот шаблон, вы можете интегрировать проверку шрифтов в любой конвейер автоматизации — будь то генерация PDF, конвертация в HTML или простое архивирование файлов Word.

### Что дальше?

- Изучите API **FontSettings.SubstitutionSettings**, чтобы задать собственные правила запасных шрифтов.  
- Скомбинируйте сбор предупреждений с системой логирования (Serilog, NLog) для мониторинга в продакшене.  
- Примените тот же подход для захвата других типов предупреждений, например, разрешения изображений или неподдерживаемых функций.

Есть вопросы по работе со шрифтами или Aspose.Words в целом? Оставьте комментарий или зайдите на форумы сообщества Aspose. Приятного кодинга, и пусть ваши документы всегда отображаются с ожидаемыми шрифтами!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}