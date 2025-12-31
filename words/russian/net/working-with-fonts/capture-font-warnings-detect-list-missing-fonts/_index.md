---
category: general
date: 2025-12-31
description: Перехватывайте предупреждения о шрифтах в Aspose.Words, чтобы обнаруживать
  отсутствующие шрифты и выводить список недостающих шрифтов в вашем приложении .NET.
  Узнайте пошаговое решение на C#.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: ru
og_description: Перехватывайте предупреждения о шрифтах в Aspose.Words, чтобы обнаруживать
  отсутствующие шрифты и выводить их список. Полное руководство по C# с кодом и советами.
og_title: Отслеживание предупреждений о шрифтах – обнаружение и список недостающих
  шрифтов
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Отслеживание предупреждений о шрифтах – обнаружение и список недостающих шрифтов
url: /ru/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Захват предупреждений о шрифтах – обнаружение и список отсутствующих шрифтов

Когда‑то вам нужно было **захватить предупреждения о шрифтах** при загрузке Word‑документа, но вы не знали, как вывести детали отсутствующих шрифтов? Вы не одиноки. Во многих реальных проектах отсутствие шрифтов приводит к сбоям в разметке, а без надлежащих предупреждений вы гоняетесь за призрачными ошибками.  

В этом руководстве мы покажем, как **обнаружить отсутствующие шрифты** и **вывести список отсутствующих шрифтов** с помощью Aspose.Words for .NET. К концу вы получите готовый фрагмент C#, который печатает каждое предупреждение о замене, чтобы вы могли вести журнал, оповещать или даже автоматически заменять шрифты.

---

## Почему важно захватывать предупреждения о шрифтах

Когда Aspose.Words открывает DOCX, в котором указаны шрифты, не установленные на сервере, он молча заменяет их запасным. Документ выглядит нормально, но визуальная точность нарушена — представьте логотип компании, отрисованный другим шрифтом.  

Захват этих предупреждений позволяет:

* **Поддерживать согласованность бренда** — вы точно знаете, какие шрифты отсутствуют.  
* **Автоматизировать исправление** — программно заменять недостающие шрифты.  
* **Проводить аудит соответствия** — генерировать отчёты для юридических или дизайнерских проверок.  

Короче говоря, **захват предупреждений о шрифтах** — первая линия защиты от скрытой замены шрифтов.

---

## Настройка LoadOptions для обнаружения отсутствующих шрифтов

Ключ к выводу предупреждений — свойство `LoadOptions.FontSubstitutionWarning`. По умолчанию оно установлено в `None`, что означает, что Aspose.Words поглощает сообщения. Переключив его на `All`, вы заставляете библиотеку фиксировать каждое событие замены.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Совет:** Если у вас уже есть пользовательская папка со шрифтами, назначьте её через `FontSettings.SetFontsFolder("path")` перед загрузкой документа. Так вы сможете **обнаружить отсутствующие шрифты**, которых нет в системном каталоге.

---

## Загрузка документа и вывод списка отсутствующих шрифтов

Теперь, когда `LoadOptions` настроены, следующий шаг — загрузить Word‑файл. Конструктор принимает объект опций, и любая замена будет записана в `WarningInfoCollection` документа.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Если файл ссылается на шрифты, которые недоступны, каждый отсутствующий шрифт генерирует запись `WarningInfo`. Вы можете **вывести список отсутствующих шрифтов**, пройдясь по этой коллекции.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Обычный вывод выглядит так:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Каждая строка точно указывает, какой шрифт отсутствовал, удовлетворяя требование **вывести список отсутствующих шрифтов**.

---

## Чтение и интерпретация WarningInfoCollection

`WarningInfoCollection` может содержать разные типы предупреждений (например, `DocumentStructure`, `ImageLoading`). Чтобы сосредоточиться только на проблемах со шрифтами, отфильтруйте по `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Зачем фильтровать? Потому что большой документ может также генерировать предупреждения о повреждённых изображениях или неподдерживаемых функциях. Сужая коллекцию, вы избавляетесь от шума и сохраняете вывод **захвата предупреждений о шрифтах** чистым.

---

## Полный рабочий пример — захват предупреждений о шрифтах в действии

Ниже представлена полностью самостоятельная программа, которую можно вставить в любой .NET‑консольный проект. Она демонстрирует каждый шаг от настройки `LoadOptions` до печати аккуратного списка отсутствующих шрифтов.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Ожидаемый вывод в консоли**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Если в документе нет отсутствующих шрифтов, вы увидите:

```
All referenced fonts are available – no warnings captured.
```

---

## Распространённые граничные случаи и способы их обработки

| Ситуация | Почему происходит | Рекомендуемое решение |
|-----------|-------------------|-----------------------|
| **Документ использует встроенный OpenType‑шрифт** | Aspose.Words может читать встроенные шрифты, но только если файл не повреждён. | Сначала проверьте DOCX в Word; при необходимости повторно внедрите шрифт. |
| **Большое количество предупреждений** (например, 200+ отсутствующих шрифтов) | Массовый импорт из устаревших систем часто ссылается на широкую палитру шрифтов. | Пакетно обрабатывайте предупреждения: сохраняйте их в базе данных, затем запускайте скрипт установки шрифтов. |
| **WarningInfoCollection пуст** | Либо в документе все шрифты присутствуют, либо `FontSubstitutionWarning` оставлен в `None`. | Проверьте конфигурацию `LoadOptions` и убедитесь, что загружаете правильный путь к файлу. |
| **Пользовательские шрифты находятся на сетевом ресурсе** | Сетевые задержки могут вызывать тайм‑ауты при поиске шрифтов. | Предзагрузите шрифты в `FontSettings` через `SetFontsFolder` и установите `CacheFontData = true`. |

Эти советы помогут вам **обнаружить отсутствующие шрифты** надёжно, даже в сложных окружениях.

---

## Иллюстрация

![пример захвата предупреждений о шрифтах](https://example.com/images/capture-font-warnings.png "пример захвата предупреждений о шрифтах")

*Скриншот показывает запуск консоли, где сообщаются два отсутствующих шрифта.*

---

## Следующие шаги — выход за рамки простого отчёта

Теперь, когда вы умеете **захватывать предупреждения о шрифтах**, подумайте об автоматизации исправления:

1. **Автоматическая замена шрифтов** — заменяйте отсутствующие шрифты на утверждённый компанией запасной вариант, изменяя `FontSettings.SubstitutionSettings`.  
2. **Логирование в систему мониторинга** — передавайте сообщения предупреждений в Serilog, ELK или Azure Application Insights.  
3. **Отчёты для пользователей** — генерируйте HTML‑ или PDF‑резюме, чтобы дизайнеры могли просмотреть, какие шрифты необходимо установить.

Все эти расширения базируются на том же фундаменте, который мы рассмотрели: настройка `LoadOptions`, загрузка документа и чтение `WarningInfoCollection`.

---

## Заключение

Вы только что узнали, как **захватывать предупреждения о шрифтах** в Aspose.Words, **обнаруживать отсутствующие шрифты** и **выводить список отсутствующих шрифтов** с чистым консольным выводом. Подход прост, требует всего несколько строк C# и работает с любой версией .NET, поддерживающей Aspose.Words 23.x и новее.  

Попробуйте на образце DOCX, в котором намеренно удалён один шрифт — вы сразу увидите появление предупреждений. Затем решайте, устанавливать ли недостающие гарнитуры, заменять их программно или просто фиксировать проблему для последующего анализа.

Счастливого кодинга, и пусть ваши документы всегда отображаются правильными шрифтами!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}