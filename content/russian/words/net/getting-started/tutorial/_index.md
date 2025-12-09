---
language: ru
url: /russian/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Обнаружение отсутствующих шрифтов в документах Aspose.Words – Полное руководство на C#  

Вы когда‑нибудь задумывались, как **обнаружить отсутствующие шрифты** при загрузке Word‑файла с помощью Aspose.Words? В своей повседневной работе я сталкивался с несколькими PDF, которые выглядели некорректно, потому что исходный документ использовал шрифт, которого у меня не было установлено. Хорошая новость? Aspose.Words может точно сообщить, когда он заменяет шрифт, и вы можете захватить эту информацию с помощью простого обратного вызова предупреждения.  

В этом руководстве мы пройдём через **полный, готовый к запуску пример**, который покажет, как вести журнал каждой замены шрифта, почему обратный вызов важен, а также несколько дополнительных приёмов для надёжного обнаружения отсутствующих шрифтов. Без лишних слов — только код и объяснения, необходимые для работы уже сегодня.  

---  

## Что вы узнаете  

- Как реализовать **Aspose.Words warning callback** для перехвата событий замены шрифтов.  
- Как настроить **LoadOptions C#**, чтобы обратный вызов вызывался при загрузке документа.  
- Как проверить, что обнаружение отсутствующего шрифта действительно сработало, и как выглядит вывод в консоли.  
- Опциональные настройки для больших пакетов или безголовых (headless) сред.  

**Требования** – Вам нужна актуальная версия Aspose.Words для .NET (код тестировался с 23.12), .NET 6 или новее, а также базовые знания C#. Если всё это у вас есть, можно начинать.  

---  

## Обнаружение отсутствующих шрифтов с помощью обратного вызова предупреждения  

Суть решения — реализация `IWarningCallback`. Aspose.Words генерирует объект `WarningInfo` во многих ситуациях, но нас интересует только `WarningType.FontSubstitution`. Давайте посмотрим, как подключиться к этому событию.  

### Шаг 1: Создать сборщик предупреждений о шрифтах  

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Почему это важно*: Фильтруя по `WarningType.FontSubstitution`, мы избегаем захламления от нерелевантных предупреждений (например, устаревших функций). `info.Description` уже содержит оригинальное название шрифта и используемый запасной, предоставляя вам чёткую аудиторскую запись.  

---  

## Настройка LoadOptions для использования обратного вызова  

Теперь мы укажем Aspose.Words использовать наш сборщик при загрузке файла.  

### Шаг 2: Настроить LoadOptions  

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Почему это важно*: `LoadOptions` — единственное место, где можно подключить обратный вызов, пароли шифрования и другие параметры загрузки. Хранение его отдельно от конструктора `Document` делает код переиспользуемым для множества файлов.  

---  

## Загрузка документа и захват отсутствующих шрифтов  

С подключённым обратным вызовом следующий шаг — просто загрузить документ.  

### Шаг 3: Загрузите ваш DOCX (или любой поддерживаемый формат)  

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Когда конструктор `Document` разбирает файл, любой отсутствующий шрифт активирует наш `FontWarningCollector`. В консоли появятся строки вроде:  

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Эта строка является конкретным доказательством того, что **обнаружение отсутствующих шрифтов** сработало.  

---  

## Проверка вывода – чего ожидать  

Запустите программу из терминала или Visual Studio. Если исходный документ содержит шрифт, которого нет у вас в системе, вы увидите хотя бы одну строку «Font substituted». Если документ использует только установленные шрифты, обратный вызов будет молчать, и вы увидите лишь сообщение «Document loaded successfully.».  

**Подсказка**: Чтобы убедиться, откройте файл Word в Microsoft Word и посмотрите список шрифтов. Любой шрифт, который появляется в *Replace Fonts* в группе *Home → Font*, является кандидатом на замену.  

---  

## Продвинутое: Обнаружение отсутствующих шрифтов пакетно  

Часто требуется просканировать десятки файлов. Та же схема легко масштабируется:  

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Поскольку `FontWarningCollector` пишет в консоль каждый раз, когда вызывается, вы получаете отчёт по каждому файлу без дополнительного кода. Для production‑сценариев вы можете логировать в файл или базу данных — просто замените `Console.WriteLine` на ваш предпочтительный логгер.  

---  

## Распространённые ошибки и профессиональные советы  

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Нет предупреждений** | Документ действительно содержит только установленные шрифты. | Проверьте, открыв файл в Word, или умышленно удалив шрифт из системы. |
| **Обратный вызов не вызывается** | `LoadOptions.WarningCallback` никогда не был назначен или позже использовался новый экземпляр `LoadOptions`. | Сохраните один объект `LoadOptions` и переиспользуйте его для каждой загрузки. |
| **Слишком много нерелевантных предупреждений** | Вы не фильтруете по `WarningType.FontSubstitution`. | Добавьте условие `if (info.Type == WarningType.FontSubstitution)` как показано. |
| **Снижение производительности на больших файлах** | Обратный вызов выполняется для каждого предупреждения, их может быть много в больших документах. | Отключите другие типы предупреждений через `LoadOptions.WarningCallback` или задайте `LoadOptions.LoadFormat` конкретный тип, если он известен. |

---  

## Полный рабочий пример (готовый к копированию)  

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Ожидаемый вывод в консоли** (когда обнаружен отсутствующий шрифт):  

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Если замена не происходит, вы увидите только строку успеха.  

---  

## Заключение  

Теперь у вас есть **полный, готовый к продакшну способ обнаружения отсутствующих шрифтов** в любом документе, обрабатываемом Aspose.Words. Используя **Aspose.Words warning callback** и настраивая **LoadOptions C#**, вы можете вести журнал каждой замены шрифта, устранять проблемы с разметкой и гарантировать, что ваши PDF сохраняют задуманное оформление.  

От одного файла до огромного пакета шаблон остаётся тем же — реализуйте `IWarningCallback`, подключите его к `LoadOptions` и позвольте Aspose.Words выполнить тяжёлую работу.  

Готовы к следующему шагу? Попробуйте сочетать это с **font embedding** или **fallback font families**, чтобы автоматически исправлять проблему, либо изучите API **DocumentVisitor** для более глубокого анализа содержимого. Приятного кодинга, и пусть все ваши шрифты остаются там, где вы их ожидаете!  

---  

![Обнаружение отсутствующих шрифтов в Aspose.Words – скриншот вывода в консоль](https://example.com/images/detect-missing-fonts.png "вывод обнаружения отсутствующих шрифтов в консоли")

{{< layout-end >}}

{{< layout-end >}}