---
category: general
date: 2026-05-04
description: Узнайте, как использовать замену шрифтов Aspose для обнаружения отсутствующих
  шрифтов при загрузке документа Word и получения сведений об отсутствующих шрифтах
  — пошаговое руководство.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: ru
og_description: Освойте замену шрифтов Aspose для обнаружения отсутствующих шрифтов
  при загрузке документа Word и получения информации об отсутствующих шрифтах с полным
  кодом C#.
og_title: Подстановка шрифтов Aspose – обнаружение отсутствующих шрифтов в документах
  Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Подстановка шрифтов Aspose: обнаружение отсутствующих шрифтов в документах
  Word'
url: /ru/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Обнаружение отсутствующих шрифтов в документах Word

Вы когда‑нибудь задавались вопросом, почему документ Word выглядит неправильно на другом компьютере? Часто виновником является отсутствующий шрифт, а **Aspose font substitution** — это инструмент, позволяющий обнаружить такие пробелы до того, как они превратятся в визуальную катастрофу. В этом руководстве мы пройдемся по тому, как **обнаружить отсутствующие шрифты** сразу после **загрузки документа Word**, а затем **получить сведения об отсутствующих шрифтах**, чтобы вы могли исправить или заменить их.

Мы рассмотрим всё: от настройки обратного вызова предупреждений до получения чистого списка отсутствующих шрифтов. К концу вы получите готовый к запуску фрагмент C#, который точно укажет, какие шрифты не были найдены, и поймёте, почему это важно для точности документа.

---

## Prerequisites – Что вам нужно перед началом

- **Aspose.Words for .NET** (рекомендована версия v23.12 или новее).  
- Среда разработки .NET (Visual Studio, Rider или `dotnet` CLI).  
- Пример DOCX, который намеренно использует шрифт, не установленный у вас — назовите его `DocumentWithMissingFont.docx`.  
- Базовые знания C# — ничего сложного, только возможность запустить консольное приложение.

Если что‑то из перечисленного вам незнакомо, сделайте паузу и установите пакет NuGet:

```bash
dotnet add package Aspose.Words
```

Вот и всё. Никаких дополнительных шрифтов, никаких внешних сервисов.

## Шаг 1: Загрузка документа Word (и запуск проверки шрифтов)

Первое, что вы делаете, — **загружаете документ Word**. Aspose.Words разбирает файл и, если не может найти указанный шрифт, ставит в очередь предупреждение *FontSubstitution*. Вот код, который выполняет загрузку:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Почему это важно:** Ранняя загрузка документа даёт Aspose возможность просканировать каждый фрагмент текста, стиль и встроенный объект. Если шрифт не найден в системе или в пользовательской папке шрифтов, позже вы получите предупреждение.

## Шаг 2: Присоединить обратный вызов предупреждений для захвата событий подстановки

Aspose.Words использует механизм обратного вызова, чтобы информировать вас о проблемах, таких как отсутствующие шрифты. Присвоив реализацию `IWarningCallback` свойству `doc.WarningCallback`, вы можете перехватывать каждое предупреждение в момент его возникновения.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Полезный совет:** Вы можете присоединить несколько обратных вызовов (например, логирование, обновление UI), обернув их в составной шаблон, но для этого руководства один обратный вызов делает всё понятнее.

## Шаг 3: Реализовать обратный вызов предупреждения о подстановке шрифтов

Теперь мы определяем класс, который действительно выполняет работу. Обратный вызов получает объект `WarningInfo`; мы фильтруем его по `WarningType.FontSubstitution` и сохраняем описание для последующего использования.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Что происходит:** Когда Aspose сталкивается с отсутствующим шрифтом, он создаёт предупреждение вроде “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Наш обратный вызов выводит эту строку и сохраняет её.

## Шаг 4: Обработать документ (по желанию) и собрать отсутствующие шрифты

Если вам нужно только **обнаружить отсутствующие шрифты**, достаточно шага загрузки — предупреждения генерируются автоматически. Однако многим разработчикам также необходимо **получить сведения об отсутствующих шрифтах** после выполнения некоторых операций (например, сохранения, конвертации). Ниже мы принудительно выполняем небольшую операцию — сохранение в PDF — чтобы гарантировать выдачу всех предупреждений, затем извлекаем собранные сообщения.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Ожидаемый вывод в консоль** (пример):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Обратите внимание, что каждая строка чётко указывает исходный шрифт и замену, выбранную Aspose. Это суть отчётов **aspose font substitution**.

## Шаг 5: Продвинутое — Использование пользовательских источников шрифтов для снижения подстановок

Иногда у вас *есть* недостающие шрифты, просто они находятся не в стандартной системной папке. Aspose.Words позволяет указать пользовательскую директорию через `FontSettings`. Добавление этого шага может значительно уменьшить количество предупреждений о подстановке.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Зачем это добавлять?** Если вы распространяете документы между машинами, упаковка необходимых шрифтов в известную папку гарантирует одинаковый визуальный вид везде. Это также делает вашу процедуру **detect missing fonts** более точной, поскольку Aspose проверяет эту папку перед тем, как использовать замену.

## Полный рабочий пример

Собрав всё вместе, представляем готовую к копированию консольную программу. Сохраните её как `Program.cs` и запустите с помощью `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Что вы должны увидеть:** Если исходный DOCX ссылается на шрифты, которых у вас нет, консоль выведет каждую строку подстановки, а затем краткое резюме. Если все шрифты присутствуют, вы получите сообщение «No missing fonts were detected.»

## Распространённые подводные камни и как их избежать

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **No warnings appear** | Документ использует только системные шрифты, или вы уже добавили пользовательскую папку, содержащую недостающие шрифты. | Проверьте, действительно ли DOCX ссылается на недоступный шрифт. Вы можете открыть его в Word и изменить абзац на редкий шрифт (например, “Papyrus”). |
| **Duplicate messages** | Тот же шрифт используется в нескольких фрагментах, вызывая множественные предупреждения. | Уберите дубликаты из списка с помощью `Distinct()`, если вам нужен только уникальный набор. |
| **Performance hit on large docs** | Каждое предупреждение обрабатывается в UI‑потоке. | Запускайте загрузку в фоновом задании или используйте `Parallel.ForEach` для пост‑обработки. |
| **Wrong fallback font** | Стандартный шрифт‑замена Aspose может не соответствовать вашему бренду. | Установите `FontSettings.SubstitutionSettings.DefaultFontName` на предпочтительный шрифт‑замену (например, “Calibri”). |

## Расширение решения — Экспорт отсутствующих шрифтов в JSON

Если вы создаёте веб‑службу, которой необходимо сообщать о недостающих шрифтах клиенту, сериализация списка тривиальна:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Теперь ваш API может возвращать чистый JSON‑payload, который может использовать другая система.

## Заключение

В этом руководстве мы продемонстрировали **Aspose font substitution** от начала до конца: загрузку документа Word, присоединение обратного вызова предупреждений, захват каждого события *detect missing fonts* и, наконец, **retrieve missing font** для отчётов или исправления. Добавив необязательные пользовательские папки шрифтов, вы можете сократить список подстановок, а с несколькими дополнительными строками можно даже экспортировать результаты в JSON.

Помните, визуальная целостность ваших документов зависит от используемых шрифтов. С помощью показанной здесь техники вы больше не будете удивлены неожиданной заменой.

Готовы к следующему шагу? Попробуйте интегрировать эту логику в более крупный конвейер обработки документов или изучите другие возможности Aspose.Words, такие как встраивание шрифтов (`doc.FontSettings.EmbeddedFonts`). Возможностей бесконечно много, и ваши пользователи оценят безупречный результат.

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}