---
category: general
date: 2026-04-21
description: Узнайте, как обнаруживать шрифты, фиксировать предупреждения, настраивать
  обратный вызов и перечислять предупреждения с помощью Aspose.Words в C#. Пошаговое
  руководство по надёжной работе со шрифтами.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: ru
og_description: Как обнаружить шрифты в Aspose.Words? Этот учебник показывает, как
  перехватывать предупреждения, настраивать обратный вызов и перечислять предупреждения
  в C#.
og_title: Как обнаружить шрифты в Aspose.Words – Полное руководство
tags:
- Aspose.Words
- C#
- Document Processing
title: Как обнаружить шрифты в Aspose.Words – Полное руководство
url: /ru/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как обнаружить шрифты в Aspose.Words – Полное руководство

Вы когда‑нибудь задумывались **как обнаружить шрифты**, которые отсутствуют при загрузке документа Word? Это ситуация, которая возникает чаще, чем хотелось бы, особенно при работе со старыми файлами или кросс‑платформенными развертываниями. В этом руководстве мы пройдем полный, исполняемый пример, который **захватывает предупреждения**, **настраивает обратный вызов** и **перебирает предупреждения**, чтобы вы всегда знали, какие шрифты были заменены.

Мы будем использовать Aspose.Words for .NET (v24.9 на момент написания) и обычный C#. Никаких внешних сервисов, никакой магии — только API и несколько строк кода. К концу вы сможете отследить каждую замену шрифта, записать её в журнал и даже решить, прервать ли загрузку, если отсутствует критически важный шрифт.  

### Что понадобится
- **Aspose.Words for .NET** (установить через NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 или новее (код также работает на .NET Framework)
- Пример DOCX, в котором используется шрифт, отсутствующий на машине (например, “MyCustomFont.ttf”)
- Visual Studio, Rider или любой другой предпочитаемый редактор C#

> **Pro tip:** Если у вас нет документа с отсутствующими шрифтами, просто переименуйте файл шрифта в системе или отредактируйте XML DOCX, указав несуществующее семейство шрифтов.

---

## Как обнаружить шрифты с помощью Aspose.Words

Суть идеи — подключиться к системе предупреждений Aspose.Words. Когда библиотека не может найти запрошенный шрифт, она генерирует предупреждение `WarningType.FontSubstitution`. Предоставив собственную реализацию `IWarningCallback`, вы сможете **обнаружить шрифты**, которые были заменены во время загрузки.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Почему это работает:** Aspose.Words вызывает метод `Warning` для каждой не‑критической проблемы. Сохраняя объекты `WarningInfo`, вы получаете полный доступ к типу, сообщению и контексту, что именно необходимо для **обнаружения заменённых шрифтов**.

---

## Как захватывать предупреждения при загрузке документа

Теперь, когда у нас есть сборщик, нужно указать `LoadOptions` использовать его. Это часть «как захватывать предупреждения» головоломки.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Edge case:** Если вы загружаете документ из потока (`new Document(stream, loadOptions)`), тот же обратный вызов работает — просто передайте поток вместо пути к файлу.

На этом этапе документ полностью загружен, но любые предупреждения о замене шрифтов безопасно сохранены внутри `warningCollector.Warnings`.

---

## Как перечислять предупреждения и формировать отчёт о заменах шрифтов

Наконец, мы проходим собранные предупреждения и **перечисляем предупреждения**, относящиеся конкретно к замене шрифтов. Этот шаг превращает сырые данные в читаемый отчёт.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Ожидаемый вывод** (пример):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Если в документе нет отсутствующих шрифтов, цикл просто не выводит ничего — повода для беспокойства нет.

---

## Полный рабочий пример (все шаги в одном файле)

Ниже представлен полный код программы, который можно скопировать и вставить в консольный проект. Он объединяет **как обнаружить шрифты**, **как захватывать предупреждения**, **как настроить обратный вызов** и **как перечислять предупреждения** в едином, согласованном потоке.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Запуск этой программы** выведет каждый шрифт, который Aspose.Words пришлось заменить. Вы можете перенаправить вывод в файл журнала, поднять оповещение или даже прервать загрузку, если отсутствует критически важный шрифт.

---

## Часто задаваемые вопросы и подводные камни

### Что делать, если нужно остановить загрузку при отсутствии обязательного шрифта?
Вы можете проверять объекты `WarningInfo` внутри обратного вызова и бросать исключение, когда появляется определённое имя шрифта. Исключение прервет загрузку, предоставив вам полный контроль.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Работает ли это с PDF или другими форматами?
Да. Aspose.Words использует одинаковую инфраструктуру предупреждений для PDF, RTF и HTML. Достаточно заменить расширение файла, а остальной код останется неизменным.

### Как записывать предупреждения в файл вместо консоли?
Замените `Console.WriteLine` любой предпочитаемой системой логирования (`Serilog`, `NLog` и т.д.). Класс `WarningInfo` предоставляет свойства `Message`, `Source` и `Exception` для детального логирования.

### Влияет ли это на производительность?
Нагрузка незначительна — Aspose.Words уже генерирует предупреждения внутри. Добавление обратного вызова просто сохраняет их в список, что имеет сложность O(n) от количества предупреждений. Для типичных документов влияние составляет гораздо менее 1 % от общего времени загрузки.

---

## Визуальное резюме

![Как обнаружить шрифты в Aspose.Words – схема потока предупреждений](https://example.com/images/font-detection-diagram.png "как обнаружить шрифты")

*Alt text:* **как обнаружить шрифты** – диаграмма, показывающая обратный вызов предупреждения, сбор и перебор шагов.

---

## Итоги

Мы рассмотрели **как обнаружить шрифты** в Aspose.Words, **захватывая предупреждения**, **настраивая обратный вызов** и **перебирая предупреждения**. Полный пример кода демонстрирует готовый к использованию шаблон, который можно внедрить в любое .NET‑приложение.  

Дальше вы можете изучить:

- **Как захватывать предупреждения** для других проблем (например, проблем конвертации изображений)
- **Как настроить обратный вызов** для пользовательских систем логирования
- **Как перечислять предупреждения** по нескольким документам в пакетной обработке
- Использование **Aspose.Words.Fonts.FontSettings** для указания резервных папок со шрифтами, что может уменьшить количество замен сразу же.

Попробуйте, адаптируйте сборщик под свой стиль логирования, и вы больше никогда не будете удивлены неожиданной заменой шрифта. Если возникнут вопросы, оставляйте комментарий ниже — приятного кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}