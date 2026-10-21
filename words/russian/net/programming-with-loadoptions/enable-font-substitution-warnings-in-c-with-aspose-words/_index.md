---
category: general
date: 2026-06-20
description: Включите предупреждения о замене шрифтов в C# с помощью Aspose.Words.
  Узнайте, как настроить LoadOptions, перехватывать предупреждения и эффективно обрабатывать
  отсутствующие шрифты.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: ru
og_description: Включите предупреждения о замене шрифтов в C# с Aspose.Words. Это
  руководство покажет, как настроить LoadOptions, прочитать WarningInfo и отобразить
  сообщения о недостающих шрифтах.
og_title: Включение предупреждений о замене шрифтов в C# – Полное руководство
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Включить предупреждения о подстановке шрифтов в C# с Aspose.Words
url: /ru/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Включение предупреждений о замене шрифтов в C# с Aspose.Words

Задумывались ли вы когда‑нибудь, как **включить предупреждения о замене шрифтов**, когда документ Word ссылается на шрифт, который не установлен на сервере? Вы не одиноки. Отсутствующие шрифты могут тихо испортить макет сгенерированных PDF или изображений, и единственный способ обнаружить это заранее — прослушивать предупреждения, генерируемые Aspose.Words.

В этом руководстве мы пошагово разберём практический пример, показывающий, как включить эти предупреждения, извлечь их из коллекции `WarningInfo` и вывести понятные сообщения в консоль. К концу вы узнаете, как настроить **Aspose.Words LoadOptions**, обрабатывать **C# font substitution warnings** и делать ваш конвейер обработки документов надёжным.

Мы также коснёмся нескольких крайних случаев — что происходит, если подавлять предупреждения, или если их нужно логировать вместо вывода, — и предоставим готовый к копированию пример кода, работающий с последней версией Aspose.Words for .NET (версия 24.10).

## Что понадобится

- .NET 6.0 или новее (код также работает на .NET Framework 4.7+)
- Ссылка NuGet на `Aspose.Words` (установить через `dotnet add package Aspose.Words`)
- Файл Word, который ссылается на шрифт, которого **нет** у вас в системе (например, `DocumentWithMissingFont.docx`)
- Хорошая IDE (Visual Studio, Rider или VS Code)

И всё — никаких дополнительных сервисов, никаких проприетарных инструментов. Готовы? Поехали.

## Шаг 1: Включить предупреждения о замене шрифтов

Первое, что нужно сделать, — сообщить Aspose.Words, что вы хотите получать уведомления, когда он заменяет отсутствующий шрифт. Это делается через свойство `FontSettings` объекта `LoadOptions`. По умолчанию предупреждения **отключены**, чтобы API был тихим, поэтому нам придётся включить их вручную.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Почему это работает:** Когда `FontSettings` не `null`, библиотека автоматически заполняет `Document.WarningInfo` записями `WarningType.FontSubstitution`, которые она встречает при загрузке документа. Это как включить «режим отладки» для шрифтов.

## Шаг 2: Загрузить документ с настроенными параметрами

Теперь, когда коллекция предупреждений активна, загрузите документ, используя подготовленный `LoadOptions`. Если в документе есть отсутствующий шрифт, Aspose.Words заменит его запасным и добавит предупреждение в список `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro tip:** Если вы обрабатываете множество файлов в цикле, переиспользуйте один экземпляр `LoadOptions` — создание его один раз экономит несколько миллисекунд на каждую итерацию.

## Шаг 3: Пройти по WarningInfo и вывести сообщения о замене шрифтов

После загрузки документа коллекция `WarningInfo` содержит все предупреждения, возникшие во время загрузки. Нас интересует только `WarningType.FontSubstitution`, поэтому отфильтруем остальные.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Запуск приведённого фрагмента кода для документа, который ссылается на отсутствующий шрифт “Papyrus”, может дать вывод вроде:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Это **сообщения о замене шрифтов**, которые вы искали — чёткие, практичные и готовые к логированию или отправке в систему оповещений.

## Полный рабочий пример

Ниже представлена автономная консольная программа, объединяющая всё вместе. Скопируйте‑вставьте её в новый проект `.csproj` и нажмите **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Ожидаемый вывод

Если документ ссылается на шрифты, которых нет в системе, вы увидите что‑то похожее на:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Если все шрифты присутствуют на машине, программа просто выведет:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Распространённые подводные камни и профессиональные советы

| Проблема | Почему происходит | Как исправить / избежать |
|----------|-------------------|--------------------------|
| **Предупреждения исчезают** | Вы очистили `FontSettings` или использовали `LoadOptions` без него. | Всегда создавайте `FontSettings`, даже если не меняете свойства. |
| **Слишком много предупреждений** | В документе используется множество экзотических шрифтов. | Добавьте пользовательскую папку со шрифтами в `FontSettings` через `SetFontsFolder`, чтобы уменьшить количество замен. |
| **Падение производительности в плотном цикле** | При каждой итерации заново создаётся `LoadOptions`, что добавляет накладные расходы. | Переиспользуйте один экземпляр `LoadOptions` для всех документов. |
| **Отсутствие вывода в консоль** | Приложение работает в GUI, где `Console.WriteLine` игнорируется. | Перенаправьте предупреждения в логгер (`ILogger`) или запишите их в файл. |

### Обработка предупреждений в реальном сервисе

В веб‑API вы, вероятно, не захотите писать в консоль. Вместо этого перенаправьте предупреждения в структурированный лог:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Таким образом вы сохраняете **обработку предупреждений документа**, при этом сервис остаётся чистым.

## Расширение примера

- **Отлавливать другие типы предупреждений** (например, `WarningType.UnknownFileFormat`), убрав фильтр `if`.
- **Сохранять отчёт** обо всех предупреждениях в JSON для последующего анализа.
- **Принудительно использовать конкретный запасной шрифт**, задав `FontSettings.SubstitutionSettings.DefaultFontName`.

Все эти возможности естественно расширяются после того, как вы освоили **включение предупреждений о замене шрифтов**.

## Заключение

Мы показали, как **включить предупреждения о замене шрифтов** в C# с помощью Aspose.Words, от настройки `LoadOptions` до перебора `WarningInfo` и вывода дружелюбных сообщений. Следуя описанным шагам, вы сможете защитить свои конвейеры обработки документов от тихих изменений макета, вызванных отсутствием шрифтов.

Далее попробуйте добавить пользовательскую папку со шрифтами, вести лог предупреждений в файл или даже отправлять их на панель мониторинга. Та же схема работает для любой задачи **обработки предупреждений документа**, будь то конвертация в PDF, рендеринг изображений или выполнение слияния писем.

Есть вопросы по **C# font substitution warnings** или хотите поделиться хитрым решением? Оставляйте комментарий ниже — happy coding!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом гайде. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Включение предупреждений о замене шрифтов в Aspose.Words – Полное руководство](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Как обнаружить шрифты в Aspose.Words – Обработка предупреждений и настроек](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Отслеживание предупреждений о замене шрифтов в Java с Aspose.Words – Полное руководство](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}