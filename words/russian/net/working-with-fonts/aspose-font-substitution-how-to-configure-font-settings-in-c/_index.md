---
category: general
date: 2026-03-27
description: 'Подмена шрифтов Aspose стала проще: узнайте, как настроить параметры
  шрифтов, отлавливать предупреждения и обрабатывать отсутствующие шрифты в ваших
  приложениях .NET.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: ru
og_description: Освойте замену шрифтов в Aspose, настроив параметры шрифтов и обработав
  отсутствие шрифтов с помощью обратного вызова предупреждения. Полное руководство
  по C#.
og_title: Замена шрифтов Aspose – настройка параметров шрифтов в C#
tags:
- Aspose.Words
- C#
- Font Management
title: Замена шрифтов Aspose – Как настроить параметры шрифтов в C#
url: /ru/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Полное руководство по настройке параметров шрифтов

Случалось ли вам сталкиваться с документом, который внезапно заменяет ваш пользовательский шрифт на что‑то общее? Это **aspose font substitution** делает свою работу — заменяя отсутствующие шрифты на самое близкое совпадение, которое она может найти. Это удобно, но если вам нужно точно знать, какой шрифт был заменён, вам придётся воспользоваться системой предупреждений библиотеки и самостоятельно настроить параметры шрифтов.

В этом руководстве мы пройдём реальный сценарий: загрузим DOCX, который ссылается на шрифт, которого у вас нет, зафиксируем событие замены и выведем дружелюбное сообщение в консоль. К концу вы будете уверенно работать с **configure font settings**, настроив **Aspose.Words warning callback**, и сможете расширить пример под любой рабочий процесс.

> **Что вам понадобится**  
> • .NET 6+ (или .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (последний NuGet)  
> • DOCX, который ссылается на отсутствующий шрифт (назовём его `MissingFont.docx`)  

Давайте начнём.

---

## Шаг 1: Установите Aspose.Words и подготовьте проект

Прежде чем писать код, убедитесь, что пакет Aspose.Words подключён:

```bash
dotnet add package Aspose.Words
```

> **Подсказка:** Используйте последнюю стабильную версию; по состоянию на март 2026 она 23.11.0. Более новые релизы улучшают алгоритмы сопоставления шрифтов и добавляют дополнительные типы предупреждений.

Создайте новое консольное приложение (или вставьте код в существующий проект) и добавьте обычные директивы `using`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Эти пространства имён дают нам доступ к `Document`, `LoadOptions` и классам, связанным со шрифтами, которые нам понадобятся.

## Шаг 2: Настройте параметры шрифтов с помощью LoadOptions

Ядро управления **aspose font substitution** находится в `LoadOptions.FontSettings`. Предоставив пустой объект `FontSettings`, мы говорим Aspose использовать его пути поиска по умолчанию *и* сообщать о любой замене через callback предупреждений.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Почему не полагаться только на значения по умолчанию? Потому что привязка callback предупреждений (следующий шаг) работает только когда свойство `FontSettings` не равно null. Эта небольшая строка даёт нам точку входа в процесс замены без изменения поведения поиска шрифтов.

## Шаг 3: Присоедините callback предупреждений для захвата замен

Aspose.Words реализует интерфейс `IWarningCallback`. Каждый раз, когда происходит что‑то значимое — например, отсутствует шрифт — вызывается наш метод `Warning`. Мы реализуем небольшой обработчик, который фильтрует `WarningType.FontSubstitution` и выводит описание.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

А вот сам обработчик:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Почему это важно** – Без callback Aspose тихо заменяет шрифты, и вы никогда не узнаёте, какой был использован. Callback делает процесс прозрачным, что важно для отчётности по соответствию или отладки проблем верстки.

## Шаг 4: Загрузите документ, используя настроенные параметры

Теперь мы наконец загружаем документ, передавая `loadOptions`, которые только что подготовили. Если исходный файл ссылается на шрифт, который не установлен, наш обработчик сработает.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Замените `YOUR_DIRECTORY` реальным путём, где находится `MissingFont.docx`. При запуске программы вы должны увидеть вывод, похожий на:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Эта строка точно указывает, какой шрифт был отсутствующим и какой запасной шрифт выбрал Aspose.

## Шаг 5: (Опционально) Тонкая настройка путей поиска шрифтов

Если у вас есть приватная папка с корпоративными шрифтами, вы можете указать Aspose, где искать их, прежде чем он перейдёт к системным шрифтам. Это расширенное использование **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Установка `recursive: true` заставляет Aspose сканировать также подпапки. Теперь библиотека будет сначала проверять ваши приватные шрифты, уменьшая вероятность нежелательной замены.

## Полный рабочий пример

Собрав всё вместе, представляем полностью готовую к запуску программу:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Ожидаемый вывод** (когда обнаружен отсутствующий шрифт):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Если все шрифты присутствуют, программа работает тихо (без предупреждений) и всё равно создаёт PDF.

## Часто задаваемые вопросы и особые случаи

### Что делать, если нужно полностью *запретить* замену?

Установите `FontSettings.SubstitutionSettings` в `null` или используйте `FontSettings.FontSubstitutionSettings` для управления поведением. Например:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Теперь Aspose будет бросать исключение вместо тихой замены, которое можно перехватить и обработать.

### Работает ли это с другими форматами файлов (например, .doc, .rtf)?

Абсолютно. Тот же объект `LoadOptions` можно передать любому конструктору `Document`, принимающему путь к файлу. Callback предупреждений сработает для всех форматов, использующих шрифты.

### Можно ли получить *точное* название запасного шрифта?

Да. Строка `info.Description` содержит как отсутствующий шрифт, так и замену. Если вам нужно получить название программно, вы можете разобрать её или использовать объект `FontInfo` (доступен в новых версиях).

### Как это работает в многопоточном окружении?

`FontSettings` **не** является потокобезопасным. Создавайте отдельный `LoadOptions` (со своим `FontSettings`) для каждого потока или защищайте доступ с помощью блокировки.

## Заключение

Мы рассмотрели всё, что нужно, чтобы освоить **aspose font substitution** и **configure font settings** в приложении C#:

1. Установите Aspose.Words и добавьте необходимые директивы `using`.  
2. Создайте объект `LoadOptions` с новым `FontSettings`.  
3. Присоедините пользовательский `IWarningCallback`, чтобы выводить события замены.  
4. Загрузите документ, позволяя callback сообщать о любых отсутствующих шрифтах.  
5. (Опционально) Расширьте путь поиска или полностью отключите замену.

Обладая этим шаблоном, вы можете вести журнал отсутствующих шрифтов для соответствия требованиям, оповещать пользователей в UI или автоматически внедрять запасные шрифты перед публикацией. Далее вы можете изучить **Aspose.Words font substitution policies** или интегрировать процесс в более крупный конвейер обработки документов.

Удачной разработки, и пусть ваши документы всегда отображаются правильным шрифтом!  

---  

![Диаграмма, показывающая загрузку документа Aspose.Words, вызов FontSettings, срабатывание callback предупреждений и вывод информации о замене шрифтов](image-placeholder.png "рабочий процесс замены шрифтов Aspose")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}