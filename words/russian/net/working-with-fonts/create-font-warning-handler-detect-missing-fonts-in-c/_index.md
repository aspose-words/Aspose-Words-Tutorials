---
category: general
date: 2026-02-12
description: Создайте обработчик предупреждений о шрифтах, чтобы обнаруживать отсутствующие
  шрифты и отслеживать их в Aspose.Words. Узнайте, как эффективно вести журнал предупреждений.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: ru
og_description: Создайте обработчик предупреждений о шрифтах в C#, чтобы обнаруживать
  отсутствующие шрифты, и узнайте, как регистрировать предупреждения, когда Aspose.Words
  заменяет шрифты.
og_title: Создать обработчик предупреждений о шрифтах — обнаружить недостающие шрифты
tags:
- Aspose.Words
- C#
- Document Processing
title: Создать обработчик предупреждений о шрифтах – обнаружить отсутствующие шрифты
  в C#
url: /ru/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание обработчика предупреждений о шрифтах – обнаружение отсутствующих шрифтов в C#

Когда‑то вам нужно было **create font warning handler** потому что документ Word тихо заменил шрифт, которого вы не ожидали? Вы не одиноки. Когда Aspose.Words загружает DOCX, в котором указанный шрифт отсутствует на сервере, он тихо переходит к шрифту по умолчанию — оставляя ваш макет слегка испорченным.  

В этом руководстве мы покажем вам точно, как **detect missing fonts**, **track missing fonts**, и **how to log warnings**, чтобы вы могли заметить эти замены до того, как они причинят проблемы. К концу вы получите переиспользуемый обработчик предупреждений, который выводит каждое событие замены шрифта в консоль (или любой другой логгер по вашему выбору). Никаких загадок, только понятный, практический код.

## Предварительные требования

- .NET 6.0 или новее (API одинаковый для .NET Framework 4.6+)
- Aspose.Words for .NET установлен (`dotnet add package Aspose.Words`)
- Файл Word, который ссылается на шрифт, не установленный на вашем компьютере (например, `MissingFont.docx`)

Если у вас уже есть всё это, отлично — приступаем.

## Шаг 1: Настройка LoadOptions с обратным вызовом предупреждения  

Первое, что вы делаете, когда хотите **create font warning handler**, — сообщаете Aspose.Words генерировать обратный вызов каждый раз, когда он сталкивается с проблемой. `LoadOptions` является контейнером для этой конфигурации.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Почему это важно:**  
`LoadOptions` — единственное место, где можно подключить `IWarningCallback`. Без него Aspose.Words будет записывать предупреждения внутренне, но вы их никогда не увидите. Присвоив `FontWarningHandler`, мы получаем полный контроль над тем, что происходит при замене отсутствующего шрифта.

## Шаг 2: Реализация класса FontWarningHandler  

Теперь мы действительно пишем код **create font warning handler**. Класс реализует `IWarningCallback` и получает объект `WarningInfo` для каждого предупреждения, генерируемого Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Объяснение:**  
- `info.Type` сообщает нам категорию предупреждения. Нас интересует `WarningType.FontSubstitution`, потому что именно он указывает на отсутствие шрифта.  
- `info.Description` содержит человекочитаемое сообщение, например *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Записывая в `Console.WriteLine`, мы **log warnings** мгновенно. В реальном приложении вы можете заменить это на `ILogger`, запись в файл или сервис телеметрии.  

> **Pro tip:** Если вам нужно собрать все отсутствующие шрифты для последующего отчёта, сохраняйте `info.Description` в `List<string>` вместо вывода на экран.

## Шаг 3: Загрузка документа с использованием настроенных LoadOptions  

С установленным обратным вызовом загрузка документа автоматически вызовет наш обработчик каждый раз, когда шрифт отсутствует.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Что вы увидите:**  
```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Эта строка подтверждает, что вы успешно **detected missing fonts** и теперь **track missing fonts** в реальном времени.

## Шаг 4: Проверка работы обработчика в разных сценариях  

Легко предположить, что обработчик работает только с файлами DOCX, но Aspose.Words поддерживает множество форматов. Попробуйте загрузить PDF, который ссылается на встроенный шрифт, или более старый файл `.doc`. Один и тот же обратный вызов срабатывает для любого формата, проходящего через конвейер разрешения шрифтов.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Если PDF ссылается на шрифт, который не установлен, вы получите тот же вывод в консоль. Это демонстрирует, что ваше решение **create font warning handler** независимо от формата.

## Шаг 5: Расширение обработчика — запись в файл  

Вывод в консоль удобен для демонстраций, но в продакшн‑коде обычно пишут в файл журнала. Вот небольшое изменение.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Теперь каждый раз, когда шрифт заменяется, сообщение добавляется в `font-warnings.log`. Это удовлетворяет часть задания **how to log warnings** и предоставляет постоянный журнал аудита.

## Шаг 6: Сборка всего вместе — полный, исполняемый пример  

Ниже приведена полная программа, которую вы можете скопировать и вставить в консольное приложение. Ничего не пропущено; просто замените путь к файлу на свой документ.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Ожидаемый результат:**  

- Консоль выводит каждую строку замены.  
- `font-warnings.log` теперь содержит запись с отметкой времени о каждом событии отсутствующего шрифта.  
- Файл `output.pdf` создаётся с использованием заменённых шрифтов, обеспечивая успешное преобразование даже при недоступности оригинальных шрифтов.

## Часто задаваемые вопросы и крайние случаи  

| Question | Answer |
|----------|--------|
| *Что если я хочу игнорировать определённые шрифты?* | Внутри `Warning` проверьте `info.Description` на имя шрифта и выполните `return;` сразу для шрифтов, которые вы считаете приемлемыми. |
| *Будет ли обработчик срабатывать для встроенных шрифтов?* | Нет — встроенные шрифты всегда доступны документу, поэтому предупреждения о замене не возникает. |
| *Могу ли я захватывать другие типы предупреждений (например, проблемы с разрешением изображений)?* | Конечно. Удалите условие `if (info.Type == WarningType.FontSubstitution)` или добавьте дополнительные `if`‑блоки для `WarningType.ImageResolution`. |
| *Является ли обработчик потокобезопасным?* | Показанная реализация записывает в файл без синхронизации. Для многопоточных сценариев оберните запись в файл в `lock` или используйте конкурентный логгер. |

## Следующие шаги  

Теперь, когда вы знаете **how to log warnings** для отсутствующих шрифтов, вы можете:

- **Detect missing fonts** во время пакетного импорта и генерировать сводный отчёт.  
- **Track missing fonts** в нескольких документах и отправлять email‑уведомление, когда определённый шрифт появляется часто.  
- **Integrate with a monitoring system** (например, Azure Application Insights), чтобы отображать тенденции замены шрифтов со временем.  

Все эти расширения опираются на одну и ту же основу `IWarningCallback`, которую мы создали.

*Счастливого кодинга! Если столкнётесь с особенностями — возможно, пользовательской папкой шрифтов или сетевой папкой — оставьте комментарий ниже. Сообщество (и я) всегда рады помочь вам отточить вашу стратегию предупреждений о шрифтах.* 

![пример создания обработчика предупреждений о шрифтах](image-placeholder.png "пример создания обработчика предупреждений о шрифтах")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}