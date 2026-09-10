---
category: general
date: 2026-01-03
description: Как обнаружить шрифты в Aspose.Words и обрабатывать предупреждения с
  помощью настроек шрифтов Aspose — пошаговое руководство для разработчиков.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: ru
og_description: Как обнаружить шрифты в Aspose.Words и настроить предупреждения с
  помощью параметров шрифтов Aspose. Узнайте полный рабочий процесс за несколько минут.
og_title: Как обнаружить шрифты в Aspose.Words – Обработка предупреждений
tags:
- Aspose.Words
- C#
- Document Processing
title: Как обнаружить шрифты в Aspose.Words – Обработка предупреждений и настроек
url: /ru/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как обнаружить шрифты в Aspose.Words – Обработка предупреждений и настроек

Когда‑нибудь задумывались **как обнаружить шрифты** в документе Word до выхода в продакшн? Вы не одиноки. Отсутствующие шрифты могут вызвать кошмары с разметкой, а без надлежащих предупреждений вы можете выпустить битый PDF или DOCX, даже не заметив этого.  

В этом руководстве мы пройдемся по **обнаружению шрифтов** с помощью Aspose.Words, покажем **как обрабатывать предупреждения** и настроим **Aspose font settings**, чтобы вы могли **конфигурировать предупреждения** именно так, как вам нужно. К концу вы получите готовый фрагмент кода, который выводит каждую замену, выполненную Aspose, и узнаете, как адаптировать его под свои проекты.

## Требования

- .NET 6+ (или .NET Framework 4.6+).  
- Aspose.Words for .NET, установленный через NuGet (`Install-Package Aspose.Words`).  
- Файл Word, который намеренно ссылается на отсутствующий шрифт (например, *DocumentWithMissingFonts.docx*).  

Если у вас уже есть всё необходимое, отлично — приступаем.

![скриншот обнаружения шрифтов](https://example.com/detect-fonts.png "пример вывода обнаружения шрифтов")

## Как обнаружить шрифты с Aspose.Words

Первый шаг — сообщить Aspose.Words, что вас интересуют события замены шрифтов. Это делается путем предоставления пользовательского обратного вызова предупреждений через **Aspose font settings**. Обратный вызов получает объект `WarningInfo` для каждой замены, позволяя **обнаруживать шрифты** во время выполнения.

### Шаг 1: Создать класс обратного вызова предупреждений

Реализуйте интерфейс `IWarningCallback`. Внутри метода `Warning` отфильтруйте `WarningType.FontSubstitution` и запишите детали.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Pro tip:** Строка `info.Description` содержит как имя отсутствующего шрифта, так и выбранный Aspose заменяющий шрифт. Вы можете разобрать её, если нужен структурированный отчёт.

### Шаг 2: Настроить LoadOptions с Aspose Font Settings

Создайте экземпляр `LoadOptions`, присоедините новый объект `FontSettings` и укажите `WarningCallback` на только что построенный обработчик. Это сообщает Aspose, **как настроить предупреждения**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Если у вас есть приватная папка со шрифтами, её можно добавить так:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Эта строка демонстрирует ещё один аспект **aspose font settings** — вы полностью контролируете, где Aspose ищет шрифты перед тем, как решить заменить их.

### Шаг 3: Загрузить документ и вызвать обратный вызов

Теперь загрузите целевой документ, используя `loadOptions`. Пока Aspose разбирает файл, любое отсутствие шрифта вызывает обработчик предупреждений, эффективно **обнаруживая шрифты** «на лету».

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

При запуске программы вы увидите вывод, похожий на:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Шаг 4: (Опционально) Собирать предупреждения для последующего использования

Если нужно сохранить данные о заменах для отчёта, измените обработчик так, чтобы он собирал сообщения в список.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Позже вы можете записать `handler.Substitutions` в JSON‑файл, отправить его в сервис логирования или отобразить в пользовательском интерфейсе.

### Шаг 5: Программно проверить результат

Иногда требуется убедиться, что *никаких* замен не произошло (например, в CI‑сборке). Вот быстрая проверка:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Этот фрагмент демонстрирует **как обрабатывать предупреждения** детерминированным способом, предоставляя полный контроль над конвейером сборки.

## Часто задаваемые вопросы (и особые случаи)

**Что делать, если нужно игнорировать определённые замены?**  
Вы можете добавить условную логику внутри `Warning` и просто вернуть управление, не записывая лог для шрифтов, которые считаете приемлемыми.

**Можно ли отключить все предупреждения и получить только булевый результат?**  
Да — установите `loadOptions.WarningCallback = null`, а затем проверьте `doc.FontInfo` после загрузки (хотя вы потеряете подробный журнал).

**Работает ли это при конвертации в PDF?**  
Абсолютно. Тот же механизм предупреждений срабатывает, когда вы вызываете `doc.Save("out.pdf")`. Обратный вызов захватит любые замены шрифтов, выполненные во время конвертации.

**Есть ли влияние на производительность?**  
Нагрузка минимальна — лишь несколько дополнительных вызовов методов на каждый отсутствующий шрифт. Для больших пакетов вы можете кэшировать результаты.

## Итоги: Что мы рассмотрели

- **Как обнаружить шрифты**, реализовав пользовательский `IWarningCallback`.  
- **Как обрабатывать предупреждения** через `LoadOptions.WarningCallback`.  
- Настройка **Aspose font settings** (добавление пользовательских папок со шрифтами, включение/отключение предупреждений).  
- **Как конфигурировать предупреждения** для мгновенного вывода в консоль и последующего анализа.  

Имея эти инструменты, вы сможете уверенно обрабатывать документы Word, гарантировать, что отсутствующие шрифты будут отмечены, и поддерживать согласованность вывода в разных средах.

## Следующие шаги

- Изучите `FontSettings.SubstitutionSettings` для более тонкой настройки (например, сопоставление конкретных отсутствующих шрифтов с выбранными заменами).  
- Совместите этот подход с Aspose.PDF для генерации PDF‑файлов, сохраняющих точную типографику.  
- Автоматизируйте проверку предупреждений в CI/CD‑конвейере, чтобы блокировать релизы с проблемами шрифтов — идеально для команд, которые **обрабатывают предупреждения** как часть контрольных точек качества.

Есть дополнительные вопросы по **aspose font settings** или нужна помощь с интеграцией в более крупный сервис? Оставьте комментарий ниже, и удачной разработки!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}