---
category: general
date: 2026-02-26
description: Обрабатывайте отсутствие шрифтов в C# с помощью Aspose.Words. Узнайте,
  как перехватывать предупреждения о замене шрифтов, реализовать IWarningCallback
  и сохранять правильный вид ваших документов.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: ru
og_description: Быстро решайте проблему отсутствующих шрифтов в C#. В этом руководстве
  показано, как перехватывать предупреждения о замене шрифтов с помощью Aspose.Words,
  реализовать IWarningCallback и проверить результаты.
og_title: Обработка отсутствующих шрифтов в C# – пошаговое руководство Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Обработка отсутствующих шрифтов в C# с Aspose.Words – полное руководство
url: /ru/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Обработка отсутствующих шрифтов в C# с Aspose.Words – Полное руководство

Когда‑нибудь вам нужно было **обрабатывать отсутствующие шрифты** при загрузке Word‑документа в C# и вы задавались вопросом, почему результат выглядит странно? Вы не одиноки. Когда исходный файл ссылается на шрифт, который не установлен на машине, Aspose.Words тихо заменяет его другим, что может нарушить макет или фирменный стиль.  

Хорошая новость? Подключив **callback предупреждения**, вы можете отлавливать каждое событие замены шрифта, записывать его и решать, предоставить ли замену. В этом руководстве мы пройдем весь процесс — от настройки проекта до проверки вывода в консоли — чтобы вы больше никогда не были удивлены невидимым шрифтом.

> **Что вы получите**: готовое к запуску консольное приложение C#, которое сообщает о каждом отсутствующем шрифте, объясняет, почему возникает предупреждение, и показывает, как расширить обработчик для пользовательской логики.

---

## Необходимые условия

- .NET 6.0 или новее (код работает как на .NET Core, так и на .NET Framework)
- Visual Studio 2022 (или любой предпочитаемый вами IDE для C#)
- **Лицензия** для Aspose.Words for .NET (бесплатная пробная версия подходит для тестирования)
- Word‑документ, который ссылается на шрифт, не установленный у вас (например, *Comic Sans MS* на Linux‑машине)

Если у вас есть всё перечисленное, давайте приступим.

---

## Шаг 1: Создайте новый консольный проект и добавьте Aspose.Words

Чтобы всё было аккуратно, начните с нового консольного проекта.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Совет**: используйте флаг `--framework net6.0`, если хотите нацелиться на конкретную среду выполнения.

Это скачает последнюю версию пакета Aspose.Words NuGet, который содержит типы `LoadOptions` и `IWarningCallback`, необходимые нам.

---

## Шаг 2: Реализуйте обработчик предупреждений (IWarningCallback)

Aspose.Words генерирует объект `WarningInfo` для каждой некритической проблемы, с которой он сталкивается при загрузке документа. Реализуя `IWarningCallback`, вы решаете, что делать с этими предупреждениями.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Почему это важно**: без обработчика предупреждения о замене шрифтов игнорируются. Выводя их в консоль, вы сразу видите, какие шрифты отсутствуют и какой шрифт использовал Aspose.Words вместо них.

---

## Шаг 3: Настройте LoadOptions с обработчиком предупреждений

Теперь мы привязываем обработчик к процессу загрузки документа. `LoadOptions` позволяет подключить callback до того, как файл будет разобран.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Примечание**: замените `YOUR_DIRECTORY` на реальную папку, где находится ваш тестовый `.docx`. Экземпляр `LoadOptions` должен быть передан конструктору `Document`; иначе будет использоваться поведение по умолчанию — тихое игнорирование.

---

## Шаг 4: Запустите приложение и проверьте вывод

Compile and run:

```bash
dotnet run
```

Если документ ссылается на шрифт, который не установлен на вашей машине (например, *Papyrus*), вы увидите что‑то вроде:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Эта единственная строка точно указывает, какой шрифт отсутствует и какой запасной вариант выбрал Aspose.Words. Теперь вы можете решить, встраивать ли отсутствующий шрифт, изменить исходный документ или принять замену.

---

## Шаг 5: Продвинутое – Сбор предупреждений для последующего использования

Иногда вы хотите сохранять предупреждения, а не выводить их сразу. Ниже показано небольшое изменение обработчика, которое собирает сообщения в список.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

And update `Main` accordingly:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Теперь у вас есть переиспользуемый список, который можно записать в файл журнала, отправить в сервис мониторинга или отобразить в пользовательском интерфейсе.

---

## Шаг 6: Распространённые подводные камни и как их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Предупреждения не появляются** | Callback не был подключён, или документ загружен без `LoadOptions`. | Убедитесь, что `LoadOptions.WarningCallback` установлен **до** вызова конструктора `Document`. |
| **Неправильное имя шрифта в сообщении** | Некоторые шрифты встроены в документ; Aspose.Words сообщает *исходное* имя, а не встроенное. | Проверьте ссылки на шрифты в исходном файле; встраивание шрифтов полностью устраняет предупреждение. |
| **Влияние на производительность** | Сбор предупреждений для тысяч документов может добавить накладные расходы. | Используйте простой `Console.WriteLine` для быстрой отладки; переключайтесь на сборщик только когда нужны данные. |

---

## Визуальное резюме

![Иллюстрация обработки отсутствующих шрифтов, показывающая поток callback предупреждений](/images/handle-missing-fonts.png "Диаграмма обработки отсутствующих шрифтов с Aspose.Words")

*Диаграмма (alt‑текст включает основной ключевой запрос) визуализирует, как callback предупреждения перехватывает события замены шрифтов во время загрузки документа.*

---

## Заключение

Теперь вы знаете **как обрабатывать отсутствующие шрифты** в C# с помощью Aspose.Words. Подключив `IWarningCallback` к `LoadOptions`, вы получаете полную видимость каждого события замены шрифта, можете записать его в журнал или выполнить действие, и в конечном итоге гарантировать, что сгенерированные документы сохраняют задуманное оформление.

> **Краткое резюме**:  
> 1. Добавьте Aspose.Words в консольное приложение.  
> 2. Реализуйте `FontWarningHandler` (или сборщик).  
> 3. Передайте его через `LoadOptions` при загрузке документа.  
> 4. Проверьте вывод в консоли или сохранённые предупреждения.  

Отсюда вы можете изучить **встраивание отсутствующих шрифтов** (`FontSettings.SubstitutionSettings`) или **автоматическую загрузку их с корпоративного сервера шрифтов** — оба естественных продолжения построенного нами шаблона.

Есть дополнительные вопросы о **предупреждениях шрифтов Aspose.Words**, **C# LoadOptions** или **загрузке документов с отсутствующими шрифтами**? Оставьте комментарий, и приятного кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}