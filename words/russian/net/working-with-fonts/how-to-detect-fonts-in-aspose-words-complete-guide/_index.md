---
category: general
date: 2026-04-07
description: Узнайте, как обнаруживать шрифты и как перехватывать предупреждения при
  работе с отсутствующими шрифтами в C# с использованием Aspose.Words. Пошаговый код
  включён.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: ru
og_description: Как обнаружить шрифты в Aspose.Words? Следуйте этому руководству,
  чтобы фиксировать предупреждения и легко обрабатывать отсутствующие шрифты.
og_title: Как обнаружить шрифты в Aspose.Words – Полное руководство
tags:
- Aspose.Words
- C#
- Font handling
title: Как обнаружить шрифты в Aspose.Words – Полное руководство
url: /ru/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как обнаружить шрифты в Aspose.Words – Полное руководство

Когда‑нибудь задумывались **как обнаружить шрифты**, которые отсутствуют в документе Word, прежде чем отправлять его в продакшн? Вы не одиноки. Во многих корпоративных сценариях случайный шрифт может сломать конвейер конвертации PDF или вызвать визуальные сбои, выглядящие непрофессионально. Хорошая новость в том, что Aspose.Words предоставляет встроенный способ выявлять такие отсутствующие гарнитуры и выводить понятные предупреждения.

В этом руководстве мы подробно рассмотрим **как обнаружить шрифты**, **как захватывать предупреждения**, а также лучшие практики **обработки отсутствующих шрифтов**, чтобы ваше приложение оставалось надёжным. Никаких внешних инструментов, без догадок — только чистый C#‑код, который вы можете сразу добавить в свой проект.

> **Быстрый обзор:** к концу вы получите переиспользуемый `FontSubstitutionWarningCollector`, собирающий каждое сообщение о замене шрифта во время загрузки документа, и будете знать, как реагировать, когда шрифт не найден.

---

## Что вы узнаете

- Как настроить `LoadOptions` для прослушивания предупреждений о замене шрифтов.  
- Как захватывать эти предупреждения в пользовательском классе‑коллекторе.  
- Как обрабатывать собранные предупреждения и решать, прерывать процесс, вести журнал или заменять шрифты.  
- Обработка крайних случаев для документов, ссылающихся на удалённые или встроенные шрифты.  

**Требования:** .NET 6+ (или .NET Framework 4.6+), Aspose.Words for .NET (последняя версия) и базовое знакомство с C#. Если вы никогда не использовали Aspose.Words, не переживайте — это руководство предполагает лишь несколько минут на настройку.

## Как обнаружить шрифты с помощью Aspose.Words LoadOptions

Первый шаг к обнаружению отсутствующих шрифтов — сообщить Aspose.Words о необходимости их отчёта. Это делается через свойство `LoadOptions.WarningCallback`, которое принимает любой класс, реализующий `IWarningCallback`. Ниже мы создаём небольшой коллектор, сохраняющий каждое предупреждение для последующего анализа.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Почему это важно:** без обратного вызова предупреждений Aspose.Words тихо заменяет отсутствующие шрифты на шрифт по умолчанию, и вы никогда не узнаете о проблеме. Захватывая `WarningType.FontSubstitution`, мы получаем полную видимость — именно те данные, которые нужны для **обнаружения шрифтов**, недоступных на хост‑машине.

Теперь подключим коллектор к `LoadOptions` и загрузим документ:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Совет:** если вы обрабатываете множество документов пакетно, переиспользуйте один экземпляр `FontSubstitutionWarningCollector`, но не забудьте вызывать `Clear()` между загрузками, чтобы не смешивать предупреждения из разных файлов.

## Захват предупреждений во время загрузки документа

После загрузки документа коллектор уже содержит все предупреждения, связанные со шрифтами. Следующий логичный вопрос: *Как захватывать предупреждения* так, чтобы их было легко записать в журнал или отобразить?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Типичный вывод выглядит так:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Что это показывает:** каждая строка раскрывает оригинальное имя шрифта и замену, выбранную Aspose.Words. Имея эту информацию, вы можете решить, приемлема ли замена, или необходимо вручную встроить отсутствующий шрифт.

## Обрабатывайте отсутствующие шрифты корректно

Обнаружение и захват предупреждений — лишь половина задачи. Настоящая ценность появляется, когда вы **обрабатываете отсутствующие шрифты** готовым к продакшену способом. Ниже представлены три распространённые стратегии:

1. **Log and Continue** — Подходит для пакетной обработки, когда нужен лишь журнал аудита.  
2. **Abort on Critical Fonts** — Выбрасывать исключение, если отсутствует конкретный шрифт (например, фирменный типографический набор).  
3. **Embed the Font On‑The‑Fly** — Загружать отсутствующий шрифт из известной папки и регистрировать его в Aspose.Words перед повторной загрузкой документа.

### Пример: Прерывание при критическом шрифте

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Пример: Автоматическое встраивание отсутствующих шрифтов

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Почему эти шаблоны полезны:** явно решая, что делать при отсутствии шрифта, вы устраняете тихие замены, которые могут подорвать фирменный стиль или читаемость. Это суть **обработки отсутствующих шрифтов** контролируемым способом.

## Полный рабочий пример

Объединив всё вместе, представляем единый готовый к запуску пример программы, демонстрирующий **как обнаружить шрифты**, **как захватывать предупреждения**, а также простую политику **обработки отсутствующих шрифтов** через журналирование.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Ожидаемый результат:** при запуске программы с документом, который ссылается на шрифт, отсутствующий на машине, консоль выведет каждое предупреждение о замене. Если какое‑либо предупреждение касается шрифта из набора `critical`, программа завершится преждевременно, предотвращая создание некорректного PDF.

## Часто задаваемые вопросы (FAQ)

| Question | Answer |
|----------|--------|
| *Нужна ли лицензия на Aspose.Words для использования этого кода?* | Да, действительная лицензия Aspose.Words удаляет водяные знаки оценки и открывает полный функционал. |
| *Может ли этот подход обнаруживать встроенные шрифты?* | Встроенные шрифты уже находятся в файле, поэтому Aspose.Words не будет выдавать предупреждение о замене. При необходимости можно проверить `Document.FontInfos`, чтобы перечислить встроенные шрифты. |
| *Что если отсутствующий шрифт является системным на Windows, но не установлен на Linux?* | То же предупреждение будет сгенерировано на Linux, поскольку шрифт там не установлен. Используйте стратегию «обработки отсутствующих шрифтов», чтобы поставлять необходимые файлы `.ttf` вместе с приложением. |
| *Является ли коллектор предупреждений поток* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}