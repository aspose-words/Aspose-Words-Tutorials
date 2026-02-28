---
category: general
date: 2026-02-28
description: Узнайте, как обрабатывать предупреждения о шрифтах и обнаруживать отсутствующие
  шрифты в Aspose.Words с помощью C#. Полное пошаговое руководство с полным кодом.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: ru
og_description: Обрабатывайте предупреждения о шрифтах в Aspose.Words и обнаруживайте
  отсутствующие шрифты с готовым к запуску примером на C#. Следуйте инструкциям и
  посмотрите результат.
og_title: Обработка предупреждений о шрифтах в Aspose.Words – Полное руководство
tags:
- Aspose.Words
- C#
- Document Loading
title: Обработка предупреждений о шрифтах в Aspose.Words – обнаружение отсутствующих
  шрифтов
url: /ru/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Обработка предупреждений о шрифтах в Aspose.Words – Обнаружение отсутствующих шрифтов

Когда‑либо вам приходилось **обрабатывать предупреждения о шрифтах** при загрузке документа Word и задаваться вопросом, почему некоторый текст выглядит странно? Вы не одиноки. Отсутствующие шрифты вызывают предупреждения о подстановке, которые могут незаметно испортить визуальное оформление, и если вы не **обнаружите отсутствующие шрифты**, вы никогда не узнаете, что пошло не так.

В этом руководстве мы покажем вам практический способ **обрабатывать предупреждения о шрифтах** с помощью `IWarningCallback` из Aspose.Words. К концу руководства вы сможете отследить каждое событие подстановки шрифта, записать его в журнал и даже решить, прервать ли загрузку. Никакой внешней документации, только один готовый к копированию пример.

## Что вы узнаете

- Создать пользовательский обработчик предупреждений, реагирующий только на оповещения о подстановке шрифтов.  
- Привязать обработчик к `LoadOptions`, чтобы каждая загрузка документа проходила через него.  
- Проверить вывод в консоли и понять, что означает каждое предупреждение.  

**Требования**

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+).  
- Aspose.Words для .NET, установленный через NuGet (`Install-Package Aspose.Words`).  
- Файл Word, который использует шрифт, не установленный на вашем компьютере (например, пользовательский корпоративный шрифт).  

Если у вас чего‑то не хватает, установите это сейчас — иначе, приступим.

## Как обрабатывать предупреждения о шрифтах в Aspose.Words

Ниже представлен полный, готовый к запуску пример. Он включает всё от операторов `using` до метода `Main`, так что вы можете вставить его в консольное приложение и нажать **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Ожидаемый вывод в консоли** (при условии, что документ использует шрифт, которого у вас нет установленного):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Если документ не содержит **отсутствующих шрифтов**, строка предупреждения никогда не появляется — таким образом вы эффективно **обнаруживаете отсутствующие шрифты** только при необходимости.

### Почему это работает

Aspose.Words генерирует `WarningInfo` для каждой некритической проблемы, с которой он сталкивается при разборе файла. Реализуя `IWarningCallback`, вы получаете точку входа в этот процесс. Флаг `WarningType.FontSubstitution` точно указывает, когда библиотеке пришлось заменить запрошенный шрифт запасным. Это самый надёжный способ **обрабатывать предупреждения о шрифтах**, поскольку он работает *во время* загрузки, до того как вы начнёте работать с объектной моделью документа.

## Обнаружение отсутствующих шрифтов без нарушения работы приложения

Иногда вы можете захотеть рассматривать отсутствующий шрифт как фатальную ошибку — возможно, ваши бренд‑гайды запрещают любую подстановку. Вы можете изменить обработчик, чтобы он бросал исключение вместо простого логирования:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Теперь блок `try…catch` вокруг `new Document(...)` поймает проблему, позволяя вам решить, прервать загрузку, использовать запасной вариант или запросить действие у пользователя.

## Бонус: визуализация предупреждений в UI‑приложении

Если вы разрабатываете приложение WinForms или WPF, замените `Console.WriteLine` на вызов, подходящий для UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Таким образом, конечные пользователи увидят предупреждение сразу, а вы всё равно **обрабатываете предупреждения о шрифтах** последовательно на всех платформах.

## Распространённые подводные камни и профессиональные советы

- **Подводный камень:** Забыть установить `WarningCallback`. Поведение по умолчанию — игнорировать предупреждения о шрифтах, поэтому вы их никогда не увидите.  
  **Профессиональный совет:** Всегда создавайте экземпляр `LoadOptions`, даже если вам нужен только обработчик предупреждений. Это дешево и явно.  

- **Подводный камень:** Использовать неправильный разделитель путей в ОС, отличных от Windows.  
  **Профессиональный совет:** Используйте `Path.Combine` или строковый литерал (`@"C:\Docs\MissingFont.docx"` работает в Windows; в Linux используйте `"/home/user/docs/MissingFont.docx"`).  

- **Подводный камень:** Предполагать, что предупреждение будет срабатывать для встроенных шрифтов.  
  **Профессиональный совет:** Встроенные шрифты считаются присутствующими, поэтому предупреждение о подстановке не появляется. Тестируйте с действительно *отсутствующими* шрифтами, чтобы увидеть работу обработчика.  

- **Подводный камень:** Перелогировать каждый тип предупреждения.  
  **Профессиональный совет:** Фильтруйте по `WarningType.FontSubstitution`, как показано — это сохраняет консоль чистой и сосредотачивает внимание на сценарии **обнаружения отсутствующих шрифтов**.  

## Полный рабочий пример в кратком виде

Вот весь код программы ещё раз, на этот раз без комментариев для тех, кто предпочитает чистый вид:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Скопируйте, вставьте, запустите — ваша консоль теперь будет автоматически **обрабатывать предупреждения о шрифтах** и **обнаруживать отсутствующие шрифты**.

## Следующие шаги

- **Записывать в файл:** Замените `Console.WriteLine` на логгер (например, NLog) для трассировки в продакшн‑среде.  
- **Пакетная обработка:** Пройдитесь по папке с документами, собирая все события подстановки шрифтов в CSV‑отчёт.  
- **Автоматическая установка шрифтов:** Подключите обработчик предупреждений к загрузке, чтобы скачивать отсутствующие шрифты из корпоративного репозитория перед продолжением загрузки.  

Каждое из этих расширений опирается на базовую идею **обработки предупреждений о шрифтах** чистым и переиспользуемым способом.

---

*Счастливого кодинга! Если вы столкнётесь с какими‑либо странностями при попытке **обнаружить отсутствующие шрифты**, оставьте комментарий ниже. Я с радостью помогу разобраться.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}