---
category: general
date: 2026-06-05
description: Настройте параметры загрузки документа в C#, чтобы обрабатывать предупреждения
  о замене шрифтов и настраивать поведение загрузки с помощью обратного вызова предупреждений.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: ru
og_description: Настройте параметры загрузки документа в C#, чтобы управлять предупреждениями
  о замене шрифтов и точно настроить загрузку документа с помощью обратного вызова
  предупреждений.
og_title: Настройка параметров загрузки документа в C# – Полное руководство
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Настройка параметров загрузки документа в C# – Полное руководство
url: /ru/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Настройка параметров загрузки документа в C# – Полное руководство

Когда‑нибудь вам нужно было **configure document load options** в C#, потому что поведение загрузки по умолчанию просто не устраивало? Возможно, вы видите неожиданные замены шрифтов или хотите регистрировать каждое предупреждение, появляющееся при импорте файла. В этом руководстве мы пройдем практическое, сквозное решение, которое не только настраивает эти параметры, но и демонстрирует **warning callback** для предупреждений о замене шрифтов.

Мы охватим всё от небольшого фрагмента кода, создающего callback, до момента, когда вы наконец откроете документ с вашими пользовательскими настройками. К концу вы получите переиспользуемый шаблон, который можно вставить в любой проект Aspose.Words, будь то обработка счетов, юридических контрактов или простых отчетов.

## Что вы узнаете

- Как **configure document load options** с помощью `LoadOptions`.
- Как реализовать **warning callback**, который перехватывает оповещения `FontSubstitution`.
- Почему ранняя обработка **font substitution warning** может спасти от сюрпризов в макете.
- Обработка граничных случаев для отсутствующих шрифтов и как корректно переключаться на запасные варианты.
- Полный готовый к копированию и вставке пример кода, который вы можете запустить уже сегодня.

### Требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+).
- Aspose.Words for .NET установлен (`dotnet add package Aspose.Words`).
- Базовое знакомство с синтаксисом C#.

Если у вас всё это есть, давайте погрузимся.

## Настройка параметров загрузки документа – пошагово

Ниже представлен полный рабочий процесс, разбитый на четыре четких шага. Каждый шаг объясняется, после чего следует лаконичный блок кода, который можно сразу вставить в Visual Studio.

### Шаг 1: Реализовать warning callback для замены шрифтов

Сначала — что такое **warning callback**? В Aspose.Words это делегат, который вызывается каждый раз, когда библиотека сталкивается с чем‑то, что стоит отметить, например, с отсутствующим шрифтом. Перехватывая `WarningType.FontSubstitution`, мы можем записать точный шрифт, который заменил движок.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Почему это важно:** Без callback библиотека молча заменяет отсутствующие шрифты, что может привести к искажённому тексту в конечном PDF или DOCX. Выводя предупреждение, вы получаете видимость и можете решить, встраивать ли отсутствующий шрифт, переключаться на запасной или оповестить пользователя.

> **Pro tip:** Если нужно захватить *все* предупреждения, уберите проверку `if`. Просто логируйте `warningInfo.Description` для каждого события.

### Шаг 2: Настроить LoadOptions с callback‑ом

Теперь, когда у нас есть callback, нам нужно **configure document load options**, чтобы действительно использовать его. `LoadOptions` — это лёгкий контейнер, который сообщает Aspose.Words, как вести себя во время вызова конструктора `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Почему это важно:** Присваивая `WarningCallback`, каждое предупреждение, возникшее в фазе загрузки, проходит через наш делегат. Здесь же можно настроить другие свойства `LoadOptions` — например, `LoadFormat`, если известен точный тип файла, или `Password` для зашифрованных документов.

### Шаг 3: Загрузить документ, используя настроенные параметры

С подключённым callback последний шаг — действительно **load the document**. Конструктор `Document` принимает путь к файлу и `LoadOptions`, которые мы только что подготовили.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Если исходный файл ссылается на шрифт, который не установлен на машине, вы увидите строку вроде:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

в консоли. Этот мгновенный отклик позволяет решить, поставлять ли отсутствующий шрифт вместе с приложением или заменять его программно.

### Шаг 4: Необязательно — проверить загруженные шрифты (обработка граничных случаев)

Иногда может потребоваться *pre‑validate* документ перед полной загрузкой, особенно в сценариях пакетной обработки. Aspose.Words предлагает класс `FontSettings`, который может перечислять требуемые шрифты.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Когда использовать:** Если у вас есть частный репозиторий шрифтов (например, фирменные шрифты компании), указание `FontSettings` на эту папку гарантирует, что движок найдёт нужные гарнитуры без отката к общим.

## Полный рабочий пример

Ниже приведена вся программа — просто скопируйте, вставьте и запустите. Она демонстрирует всё от создания callback до финальной загрузки документа.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Ожидаемый вывод**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Если отсутствующих шрифтов нет, callback просто молчит — о чём беспокоиться не требуется.

## Часто задаваемые вопросы и граничные случаи

### Что если callback предупреждения бросает исключение?

Callback выполняется в том же потоке, который загружает документ. Исключение внутри делегата прервет загрузку и распространит ошибку. Оберните вашу логику в `try/catch`, если нужна устойчивость.

### Можно ли подавить *все* предупреждения вместо их обработки?

Да — установите `loadOptions.WarningCallback = null;` или предоставьте callback, который ничего не делает. Учтите, что вы потеряете видимость потенциальных проблем.

### Работает ли это с зашифрованными DOCX‑файлами?

Абсолютно. Просто добавьте `Password = "yourPassword"` в `LoadOptions` перед созданием `Document`. Callback предупреждений по‑прежнему будет срабатывать для проблем со шрифтами.

### Чем это отличается от использования `DocumentBuilder`?

`DocumentBuilder` предназначен для *создания* или *модификации* документа после его загрузки. **Configure document load options** влияет на *начальный* этап парсинга, где принимаются решения о замене шрифтов.

## Визуальный обзор

![Диаграмма, показывающая поток настройки параметров загрузки документа](https://example.com/images/load-options-flow.png "Диаграмма, показывающая поток настройки параметров загрузки документа")

*Изображение иллюстрирует поток: callback → LoadOptions → конструктор Document → обработка предупреждений.*

## Заключение

Теперь вы знаете, как **configure document load options** в C# для захвата предупреждений о замене шрифтов, внедрения пользовательских папок со шрифтами и полного контроля над процессом загрузки. Этот шаблон даёт уверенность, что каждый отсутствующий шрифт будет сообщён, позволяя поддерживать точность отображения документов в любой среде.

Следующие шаги? Попробуйте заменить вывод в консоль на более надёжную систему телеметрии или комбинируйте этот подход с `DocumentBuilder`, чтобы автоматически заменять отсутствующие шрифты на корпоративный вариант по умолчанию. Вы также можете изучить другие значения `WarningType`, такие как `DocumentStructure`, для ещё более глубокого понимания.

Счастливого кодинга, и пусть ваши документы всегда отображаются точно так, как вы задумали!

## Что вам изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Освойте параметры загрузки Markdown в Aspose.Words на Python для улучшенной обработки документов](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Оптимизация загрузки документов с параметрами HTML, RTF и TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Использование параметров и настроек документа в Aspose.Words для Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}