---
category: general
date: 2026-01-06
description: Узнайте, как получать предупреждения при загрузке документов и отслеживать
  шрифты с помощью Aspose.Words. Это руководство охватывает обратные вызовы предупреждений
  и отслеживание подстановки шрифтов.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: ru
og_description: Как получить предупреждения в Aspose.Words? Следуйте этому пошаговому
  руководству, чтобы отслеживать шрифты и фиксировать сообщения о замене при загрузке
  документов.
og_title: Как получать предупреждения в Aspose.Words — мониторинг шрифтов
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Как получать предупреждения в Aspose.Words – мониторинг шрифтов в C#
url: /ru/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как получать предупреждения в Aspose.Words – мониторинг шрифтов в C#

Когда‑нибудь задавались вопросом **как получать предупреждения**, когда документ Word содержит шрифты, которые у вас не установлены? Это распространённая проблема — ваше приложение тихо заменяет отсутствующие шрифты, и вы никогда не узнаёте, что изменилось. Хорошая новость в том, что вы можете подключиться к системе предупреждений Aspose.Words и **мониторить шрифты** в реальном времени.

В этом руководстве мы покажем, как точно захватывать такие предупреждения о замене шрифтов, почему это важно и что делать с полученной информацией. Никакой внешней документации, только полностью готовый к запуску пример, который вы можете вставить в Visual Studio прямо сейчас.

> **Pro tip:** Если вы строите конвейер конвертации документов, ранний журнал отсутствующих шрифтов спасает от неприятных сюрпризов в разметке дальше по цепочке.

---

## Что понадобится

- **Aspose.Words for .NET** (последняя версия; API не менялся с v23.10)
- Среда разработки .NET (Visual Studio, Rider или VS Code с расширением C#)
- Пример файла `.docx`, в котором используется шрифт, которого у вас нет (например, **«NonExistentFont»**)

Это всё — никаких дополнительных пакетов NuGet, кроме Aspose.Words.

---

## Шаг 1 – Настройка сборщика предупреждений (Primary Keyword in Header)

Первое, что вам нужно, — место для хранения предупреждений по мере их появления. Aspose.Words предоставляет свойство `WarningCallback` в `LoadOptions` именно для этой цели.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Почему это важно:**  
Когда библиотека сталкивается с отсутствующим шрифтом, она не бросает исключение; она генерирует объект `WarningInfo`. Подключив сборщик, вы получаете полную видимость каждого события замены, позволяя **мониторить шрифты** без засорения консоли посторонними сообщениями.

---

## Шаг 2 – Загрузка документа с включёнными параметрами предупреждений

Теперь мы действительно читаем файл. `LoadOptions`, подготовленные на предыдущем шаге, гарантируют, что любые предупреждения, связанные со шрифтами, будут захвачены.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Что происходит «под капотом»?**  
Aspose.Words парсит файл Word, разрешает шрифты и каждый раз, когда не может найти запрошенный шрифт, переключается на замену (обычно Arial). Эта замена вызывает предупреждение `WarningType.FontSubstitution`, которое попадает в `warningCollector`.

---

## Шаг 3 – Проверка собранных предупреждений (Primary Keyword Appears Again)

После загрузки документа мы просто перебираем `warningCollector` и выводим любые сообщения о замене шрифтов.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Ожидаемый вывод** (при условии, что отсутствующий шрифт — *«FancyScript»*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Если документ содержит несколько неизвестных шрифтов, вы увидите одну строку на каждую замену — идеально для журналирования или оповещения.

---

## Шаг 4 – Необязательно: журналировать или сохранять информацию о предупреждениях

В продакшене вам, вероятно, понадобится больше, чем `Console.WriteLine`. Вот быстрый пример, который записывает предупреждения в JSON‑файл для последующего анализа.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Теперь у вас есть постоянный журнал, который можно передать в панель мониторинга или даже инициировать автоматический запрос недостающих файлов шрифтов.

---

## Шаг 5 – Проверка результата и очистка

Запустите программу. Если вы видите сообщения о замене, вы успешно **получили предупреждения** и теперь активно **мониторите шрифты**. Если ничего не появляется, дважды проверьте, действительно ли тестовый документ ссылается на шрифт, который не установлен на машине.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Нулевой счёт обычно означает одно из следующего:

1. Все шрифты были найдены (возможно, шрифт *установлен* локально), или
2. В документе не было ссылок на шрифты, требующие замены.

---

## Распространённые подводные камни и как их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Предупреждения не появляются** | Шрифт действительно существует в системе, либо документ использует только встроенные шрифты. | Переименуйте шрифт в исходном файле на что‑то невозможное (например, `XYZ123`) и попробуйте снова. |
| **Слишком много предупреждений (шум)** | Вы загружаете множество документов в цикле, не очищая сборщик. | Переинициализируйте `WarningInfoCollection` для каждого документа или вызовите `warningCollector.Clear()` после обработки. |
| **Влияние на производительность** | Чрезмерное журналирование на диск может замедлить пакетную обработку. | Буферизуйте предупреждения в памяти и записывайте их блоками, либо используйте асинхронный ввод‑вывод. |
| **Отсутствует `using Aspose.Words.Loading;`** | Класс `LoadOptions` находится в этом пространстве имён. | Добавьте недостающую директиву `using`, как показано в Шаге 1. |

---

## Расширение решения – мониторинг других типов предупреждений

Хотя замена шрифтов самая заметная, Aspose.Words может генерировать предупреждения для:

- **Устаревших функций** (`WarningType.Deprecated`),
- **Потенциальной потери данных** (`WarningType.DataLoss`),
- **Неподдерживаемых форматов файлов** (`WarningType.UnsupportedFileFormat`).

Вы можете расширить фильтр в Шаге 3, чтобы захватывать их тоже:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Таким образом, вы получаете не только **как мониторить шрифты**, но и **как получать предупреждения** для любой ситуации, с которой может столкнуться ваше приложение.

---

## Полный рабочий пример (готовый к копированию и вставке)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Запустите:** Скомпилируйте проект, выполните его, и вы увидите вывод предупреждений, а также их сохранение. Это полный ответ на **как получать предупреждения** и **как мониторить шрифты** с помощью Aspose.Words.

---

## Заключение

Теперь вы знаете **как получать предупреждения** от Aspose.Words, в частности для сценариев замены шрифтов, и вы научились **как мониторить шрифты** в процессе загрузки документа. Подключив `WarningCallback`, перебирая собранные объекты `WarningInfo` и при необходимости сохранять данные, вы получаете полную прозрачность относительно событий отсутствующих шрифтов — важную возможность для любого конвейера обработки документов.

Что дальше? Попробуйте расширить фильтр предупреждений, чтобы охватить потери данных или устаревшие функции, либо интегрировать JSON‑лог в панель мониторинга, например Grafana. Один и тот же шаблон работает для всех типов предупреждений, так что вы будете готовы следить за любой проблемой, которую Aspose.Words может вам выдать.

Счастливого кодинга, и пусть ваши документы всегда отображаются точно так, как вы ожидаете! 

---

<img src="font-warnings.png" alt="как получить предупреждения в Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}