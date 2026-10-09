---
category: general
date: 2026-03-17
description: Как обнаружить шрифты в C# с помощью Aspose.Words и обратного вызова
  предупреждений. Узнайте, как использовать обратный вызов для захвата замен недостающих
  шрифтов при загрузке документов.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: ru
og_description: Как обнаружить шрифты в C# с помощью Aspose.Words. Это руководство
  показывает, как использовать обратный вызов для захвата предупреждений о недостающих
  шрифтах при загрузке документа.
og_title: Как определить шрифты в C# – использовать обратный вызов с Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Как обнаружить шрифты в C# – использовать обратный вызов с Aspose.Words
url: /ru/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как обнаружить шрифты в C# – Использовать обратный вызов с Aspose.Words

Когда‑нибудь вам нужно было **как обнаружить шрифты** в документе Word программно и вы задавались вопросом, почему некоторые символы выглядят странно после конвертации? Вы не одиноки. Во многих реальных проектах — генераторах счетов, экспортёрах отчетов или конвейерах пакетной обработки — отсутствие шрифтов вызывает тихие сбои в разметке, которые трудно отладить.  

Хорошая новость? Aspose.Words предоставляет простой способ выявить эти проблемы с помощью обратного вызова предупреждения. В этом руководстве вы увидите **как использовать обратный вызов**, чтобы перехватывать каждую замену шрифта, которую Aspose выполняет при загрузке документа, и получите готовый к запуску пример, выводящий чёткий отчёт о недостающих шрифтах.

Мы рассмотрим:

* Минимальные предпосылки (проект .NET и пакет Aspose.Words NuGet).  
* Как реализовать `IWarningCallback` для прослушивания `WarningType.FontSubstitution`.  
* Как подключить обратный вызов к `LoadOptions` и загрузить документ.  
* Как выглядит вывод, а также несколько практических советов для production‑кода.

К концу вы сможете автоматически **обнаруживать шрифты** в любом файле DOCX, DOC или RTF и реагировать на информацию о недостающих шрифтах — будь то логирование, оповещение пользователя или подстановка резервного шрифта.

---

![Как обнаружить шрифты в документе Word с помощью обратного вызова предупреждения Aspose.Words](https://example.com/images/detect-fonts.png "как обнаружить шрифты в документе Word")

## Что понадобится

* **.NET 6.0** или новее (пример также компилируется с .NET Framework 4.6+).  
* **Aspose.Words for .NET** — установить через NuGet: `Install-Package Aspose.Words`.  
* Пример файла Word, который намеренно ссылается на шрифт, отсутствующий в системе (например, `MissingFont.docx`).  

Дополнительные библиотеки не требуются; всё находится в пространстве имён Aspose.

---

## Как обнаружить шрифты с помощью обратного вызова предупреждения

### Шаг 1: Создать класс обратного вызова предупреждения

Обратный вызов реализует `IWarningCallback`. Когда Aspose.Words сталкивается с шрифтом, который не может найти, он генерирует `WarningInfo` с типом `WarningType.FontSubstitution`. Наш класс просто выводит дружелюбную строку в консоль.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Почему это важно:** Фильтруя по `WarningType.FontSubstitution`, мы избегаем шумных предупреждений (например, о устаревших функциях) и держим журнал сосредоточенным на именно той проблеме, которую решаем — **обнаружении шрифтов**, отсутствующих на машине.

---

### Шаг 2: Подключить обратный вызов к `LoadOptions`

`LoadOptions` позволяет настроить процесс парсинга документа. Присвоив наш `FontWarningCollector` свойству `WarningCallback`, мы заставляем Aspose вызывать его каждый раз, когда встречается недостающий шрифт.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Подсказка:** Здесь же можно задать `LoadOptions.FontSettings`, если нужно программно указать резервный шрифт. Это более продвинутый сценарий, о котором мы упомянем позже.

---

### Шаг 3: Загрузить документ и наблюдать вывод

Теперь действительно загружаем файл. Как только Aspose парсит документ, любой шрифт, который он не может найти, вызывает наш обратный вызов.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Ожидаемый вывод в консоли** (при условии, что документ ссылается на *Comic Sans MS*, который не установлен):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Если в документе несколько недостающих шрифтов, вы увидите одну строку на каждый шрифт — именно ту информацию **как обнаружить шрифты**, которая вам нужна.

---

## Как использовать обратный вызов в более сложных сценариях

### Логирование в файл вместо консоли

В продакшене, скорее всего, понадобится постоянный лог. Замените `Console.WriteLine` на `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Сбор предупреждений для последующего анализа

Иногда нужен список недостающих шрифтов после загрузки документа, например, для отображения диалогового окна UI. Сохраните предупреждения в `List<string>` и предоставьте их наружу:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Программное указание резервного шрифта

Если в компании есть фирменный шрифт, который нужно принудительно использовать, добавьте его в `FontSettings` перед загрузкой:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Теперь Aspose заменяет недостающие шрифты на *Arial Unicode MS*, одновременно сообщая о замене через обратный вызов. Это удобный способ **как использовать обратный вызов** как для обнаружения, так и для автоматического исправления.

---

## Распространённые подводные камни и профессиональные советы

| Подводный камень | Почему происходит | Как избежать |
|------------------|-------------------|--------------|
| **Забыли подключить `Aspose.Words.Warnings`** | Интерфейс `IWarningCallback` находится в этом пространстве имён. | Добавьте `using Aspose.Words.Warnings;` в начале файла. |
| **Загрузка документа без `LoadOptions`** | Стандартный загрузчик тихо подменяет шрифты без уведомления. | Всегда создавайте экземпляр `LoadOptions` и назначайте свой обратный вызов. |
| **Запуск на сервере с ограниченными правами** | Запись в файл журнала может вызвать `UnauthorizedAccessException`. | Используйте папку с правом записи (например, каталог данных приложения) или храните данные в памяти. |
| **Несколько потоков используют один и тот же collector** | `FontWarningCollector` по умолчанию не потокобезопасен. | Создавайте отдельный collector для каждого потока или защищайте список блокировкой. |
| **Считается, что обратный вызов срабатывает для встроенных шрифтов** | Встроенные шрифты уже присутствуют в документе; предупреждение не генерируется. | Если нужно проверять целостность встроенных шрифтов, исследуйте `FontInfo` через `FontSettings`. |

---

## Полный рабочий пример (готовый к копированию)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Что вы должны увидеть** (при условии, что файл ссылается на два отсутствующих шрифта):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Если файл использует только установленные шрифты, консоль просто выведет:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Итоги

Мы прошли процесс **как обнаружить шрифты** в документе Word, подключив пользовательский обратный вызов предупреждения к Aspose.Words. Этот подход лёгок, требует

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}