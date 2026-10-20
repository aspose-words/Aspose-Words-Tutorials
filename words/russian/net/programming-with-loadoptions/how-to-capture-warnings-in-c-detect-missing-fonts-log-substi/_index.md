---
category: general
date: 2026-04-04
description: Узнайте, как перехватывать предупреждения, обнаруживать отсутствующие
  шрифты и вести журнал событий замены с помощью Aspose.Words LoadOptions в C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: ru
og_description: Как захватывать предупреждения, обнаруживать отсутствующие шрифты
  и вести журнал событий замены с использованием Aspose.Words LoadOptions в C#.
og_title: Как перехватывать предупреждения в C# – обнаруживать отсутствующие шрифты
  и фиксировать замену
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Как перехватывать предупреждения в C# – обнаруживать отсутствующие шрифты и
  фиксировать замену
url: /ru/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как захватывать предупреждения в C# – обнаружение отсутствующих шрифтов и журнал замены

Когда‑нибудь задумывались **как захватывать предупреждения**, которые появляются при загрузке Word‑документа с отсутствующими шрифтами? Вы не одиноки. Во многих реальных проектах шрифты теряются при миграции, и тихая подстановка может сломать ваш макет. Хорошая новость? Aspose.Words предоставляет удобный способ прослушивать такие предупреждения, обнаруживать отсутствующие шрифты и даже вести журнал каждой подстановки, чтобы позже исправить источник.

В этом руководстве мы пройдём через полностью готовое к запуску решение, которое показывает **как захватывать предупреждения**, демонстрирует **обнаружение отсутствующих шрифтов** и объясняет **как вести журнал подстановок**. К концу вы получите переиспользуемый обработчик предупреждений, полностью сконфигурированный объект `LoadOptions` и пример вывода в консоль, который можно проверить.

> **Prerequisite:** Вам нужен Aspose.Words for .NET (v24.x или новее), установленный через NuGet, и базовая среда разработки C# (Visual Studio 2022 или VS Code подойдут).

---

## Как захватывать предупреждения при загрузке документов

Суть решения — класс, реализующий `IWarningCallback`. Aspose.Words автоматически вызывает этот колбэк для каждого предупреждения, возникшего во время загрузки документа, включая предупреждения о подстановке шрифтов.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Why this step?**  
> By filtering on `WarningType.FontSubstitution` we avoid clutter from unrelated warnings (like deprecated features). This makes the log focused on the exact problem you care about—missing fonts.

---

## Обнаружение отсутствующих шрифтов с помощью Aspose.Words

Когда документ ссылается на шрифт, который не установлен на машине, Aspose.Words подставляет наиболее близкий вариант и генерирует предупреждение. Наш обработчик выше поймает каждое такое событие, эффективно **обнаруживая отсутствующие шрифты**.

Чтобы увидеть это в действии, нужно настроить `LoadOptions` и привязать обработчик:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** If you prefer to collect warnings for later processing (e.g., write to a file), replace `Console.WriteLine` with code that adds the message to a `List<string>`.

---

## Как вести журнал событий подстановки

Ведение журнала сводится к перенаправлению вывода предупреждений в постоянное хранилище. Ниже простой пример, который записывает каждое предупреждение о подстановке в текстовый файл `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Why log to a file?**  
> Persistent logs let you audit font issues across multiple runs, automate alerts, or feed the data into a build‑pipeline check.

---

## Полный рабочий пример

Объединив всё вместе, получаем автономное консольное приложение, которое можно скопировать, вставить и запустить. Оно демонстрирует **как захватывать предупреждения**, **обнаруживать отсутствующие шрифты** и **как вести журнал подстановок** в одном процессе.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Ожидаемый вывод в консоль

Если `input.docx` ссылается на шрифт, который не установлен, вы увидите примерно следующее:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Если вы переключились на `FileLoggingWarningHandler`, те же строки появятся внутри `font-warnings.log` с отметками времени.

![how to capture warnings console output](image-placeholder.png)

---

## Часто задаваемые вопросы и особые случаи

### Что если нужно захватывать *все* предупреждения, а не только подстановку шрифтов?

Просто удалите проверку `if (info.Type == WarningType.FontSubstitution)`. Колбэк будет получать каждый тип предупреждения (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent` и т.д.). Затем можно ветвить по `info.Type`, обрабатывая каждый случай по‑разному.

### Работает ли это с PDF или только с Word‑документами?

`LoadOptions` и `IWarningCallback` являются частью Aspose.Words, поэтому они применимы к форматам, совместимым с Word (`.docx`, `.doc`, `.rtf`, `.html`). Для PDF следует использовать собственные механизмы предупреждений Aspose.PDF.

### Как подавить предупреждения вместо их журналирования?

Установите `LoadOptions.WarningCallback = null` или реализуйте колбэк, но оставьте тело метода пустым. Библиотека всё равно выполнит подстановку тихо.

### А как насчёт потокобезопасности?

Экземпляр колбэка вызывается в том же потоке, который загружает документ, поэтому дополнительная синхронизация не требуется, если только вы не используете один обработчик для параллельных загрузок. В этом случае защищайте общие ресурсы (например, файл журнала) с помощью блокировки или используйте конкурентные коллекции.

---

## Заключение

Мы рассмотрели **как захватывать предупреждения** из Aspose.Words, показали **как обнаруживать отсутствующие шрифты** и объяснили **как вести журнал подстановок** для последующего анализа. Подключив простую реализацию `IWarningCallback` к `LoadOptions`, вы получаете полную видимость проблем, связанных со шрифтами, без засорения кода.

Что дальше? Попробуйте расширить журнал, чтобы отправлять письма, интегрировать его с Azure Monitor или автоматически устанавливать недостающие шрифты на сервере сборки. Также можно изучить другие типы предупреждений — `WarningType.DegradedDocument` может сигнализировать о функциях, не выживших при конвертации.

Есть дополнительные вопросы по работе со шрифтами или Aspose.Words в целом? Оставьте комментарий или откройте новую тему на форумах Aspose. Приятного кодинга, и пусть ваши документы всегда отображаются правильным шрифтом!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}