---
category: general
date: 2026-04-02
description: Как обнаружить шрифты в документах C# с помощью Aspose.Words. Узнайте,
  как настроить параметры шрифтов и эффективно обрабатывать отсутствующие шрифты.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: ru
og_description: Как обнаружить шрифты в документах C# с использованием Aspose.Words.
  Это руководство показывает, как настроить параметры шрифтов и обработать отсутствующие
  шрифты.
og_title: Как обнаружить шрифты в C# – Полное руководство
tags:
- C#
- Aspose.Words
- Document Processing
title: Как обнаружить шрифты в C# – полное руководство
url: /ru/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как обнаружить шрифты в C# – Полное руководство

Когда‑то задавались вопросом **как обнаружить шрифты**, которые отсутствуют или заменяются при загрузке Word‑документа в .NET? Вы не одиноки — разработчики постоянно сталкиваются с проблемой, когда документ ссылается на шрифт, который не установлен на сервере. Хорошая новость в том, что Aspose.Words предоставляет чистый программный способ выявить такие пробелы.

В этом руководстве мы пройдём через практический пример, который не только показывает **как обнаружить шрифты**, но и демонстрирует, как **настроить параметры шрифтов** и **корректно обрабатывать отсутствующие шрифты**. К концу вы получите готовый фрагмент кода, который выводит каждое предупреждение о замене шрифта, чтобы вы могли вести журнал, оповещать или заменять шрифты по необходимости.

---

## Что понадобится

- **Aspose.Words for .NET** (последняя версия работает лучше всего; код ниже ориентирован на .NET 6+)
- Среда разработки .NET (Visual Studio, Rider или VS Code)
- Пример файла `.docx`, который ссылается на шрифт, не установленный у вас (отлично подходит для тестов)

Никаких дополнительных пакетов NuGet, кроме Aspose.Words, не требуется, и решение работает на Windows, Linux и macOS.

---

## Шаг 1: Установить и подключить Aspose.Words

Сначала добавьте библиотеку в проект. Команда NuGet проста:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Если вы работаете на CI‑сервере, зафиксируйте версию пакета, чтобы избежать неожиданных ломающих изменений.

---

## Шаг 2: Настроить параметры шрифтов (и подготовить параметры загрузки)

Прежде чем открывать документ, вы можете указать Aspose.Words, где искать резервные шрифты. Это часть **configure font settings**, которая предотвращает тихую замену шрифтов, которую вы, возможно, не хотите.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Зачем это нужно? Если документ ссылается на *Comic Sans*, а на вашем сервере установлен только *Calibri*, Aspose.Words заменит *Calibri* и выдаст предупреждение. Настроив путь поиска, вы уменьшаете нежелательные сюрпризы.

---

## Шаг 3: Загрузить документ с подготовленными параметрами

Теперь действительно открываем файл. `LoadOptions`, которые мы создали на предыдущем шаге, передаются напрямую конструктору `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Если файл не найден или повреждён, будет выброшено исключение — поэтому в продакшн‑коде имеет смысл обернуть это в try/catch.

---

## Шаг 4: Просканировать предупреждения документа на предмет замен шрифтов

Aspose.Words собирает список предупреждений во время парсинга. Среди них `FontSubstitutionWarning` точно указывает, какой шрифт был заменён.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

Коллекция `Warnings` может также содержать другие элементы (например, `DocumentStructureWarning`). Фильтрация по `FontSubstitutionWarning` гарантирует, что мы сообщаем только о сценарии **handle missing fonts**, который нас интересует.

---

## Шаг 5: Собрать всё вместе — Полный, исполняемый пример

Ниже полный пример программы. Скопируйте‑вставьте его в новое консольное приложение и запустите; вы увидите каждый недостающий шрифт, выведенный в консоль.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Ожидаемый вывод** (пример):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Если документ использует только шрифты, присутствующие на машине, вместо этого появится строка «No font substitutions detected».

---

## Пограничные случаи и часто задаваемые вопросы

### Что если в документе **нет никаких предупреждений**?

Это просто означает, что каждый требуемый шрифт был найден в указанных вами папках поиска. Флаг `anySubstitutions` в примере покрывает этот случай.

### Можно ли **записывать** предупреждения в файл вместо консоли?

Конечно. Замените вызовы `Console.WriteLine` на логгер по вашему выбору (Serilog, NLog и т.д.). Объект `WarningInfo` также предоставляет `WarningType` и `WarningMessage`, если нужны дополнительные детали.

### Как **игнорировать** определённые шрифты, например фирменный шрифт, который никогда не должен заменяться?

Можно добавить собственное правило замены:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Теперь Aspose.Words будет заменять *MyBrandFont* только на перечисленные альтернативы, и вы всё равно получите предупреждение, с которым сможете работать.

### Работает ли это в **Linux**‑контейнерах?

Да — просто убедитесь, что смонтировали папку с необходимыми файлами `.ttf`/`.otf` и указали её в `SetFontsFolder`. Aspose.Words не зависит от шрифтов, установленных в ОС.

---

## Визуальный обзор

![как обнаружить шрифты flowchart](detect-fonts.png "Диаграмма, показывающая шаги обнаружения шрифтов в документе")

*Текст alt изображения:* **как обнаружить шрифты** flowchart, иллюстрирующий конфигурацию, загрузку и проверку предупреждений.

---

## Итоги – Что мы изучили

- **Как обнаружить шрифты**, которые отсутствуют или заменяются, используя предупреждения Aspose.Words.  
- Как **настроить параметры шрифтов**, указав пользовательские папки и задав резервный шрифт по умолчанию.  
- Стратегии **обработки отсутствующих шрифтов**, от логирования до пользовательских правил замены.

Всё это упаковано в компактное, автономное консольное приложение, которое можно добавить в любой .NET‑проект.

---

## Следующие шаги и смежные темы

- **Встраивание шрифтов** непосредственно в итоговый документ, чтобы избежать будущих замен (`SaveOptions` с `EmbedFullFonts`).  
- **Программная замена шрифтов** — заменять отсутствующие шрифты на конкретную альтернативу перед сохранением.  
- **Тонкая настройка производительности** — кэшировать `FontSettings` при обработке большого количества документов пакетно.  

Если вас интересуют эти темы, ищите *configure font settings* и *handle missing fonts* — они приведут к более глубоким материалам по управлению шрифтами в Aspose.Words.

---

Счастливого кодинга! Есть странный случай с шрифтом? Оставьте комментарий, и мы разберёмся вместе.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}