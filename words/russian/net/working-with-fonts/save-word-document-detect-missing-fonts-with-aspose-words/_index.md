---
category: general
date: 2026-03-22
description: Сохраните документ Word и обнаружьте отсутствующие шрифты с помощью Aspose.Words.
  Узнайте, как отслеживать отсутствующие шрифты и фиксировать ошибки шрифтов в C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: ru
og_description: Сохранение документа Word и обнаружение отсутствующих шрифтов в C#.
  Это руководство показывает, как отслеживать отсутствующие шрифты и фиксировать ошибки
  шрифтов с помощью обратного вызова предупреждения.
og_title: Сохранить документ Word – обнаружить отсутствующие шрифты с Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Сохранить документ Word – обнаружить отсутствующие шрифты с помощью Aspose.Words
url: /ru/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить документ Word – обнаружить отсутствующие шрифты с помощью Aspose.Words

Когда‑нибудь вам нужно было **save word document**, но вы не были уверены, выживут ли некоторые шрифты при круговом проходе? Это происходит чаще, чем вы думаете, особенно когда документы перемещаются между машинами с разными библиотеками шрифтов. Хорошая новость? Aspose.Words предоставляет встроенный способ **detect missing fonts** во время **save word document**, так что вы можете вести журнал, выдавать предупреждения или даже заменять их до того, как файл окажется на экране пользователя.

В этом руководстве мы пройдем полностью готовый к запуску пример, который не только сохраняет документ Word, но и **tracks missing fonts** и **captures font errors** с помощью пользовательского обработчика предупреждений. К концу вы точно поймёте, почему важен callback предупреждений, как его подключить и как выглядит вывод в консоль при замене шрифта. Без лишних деталей — только код, который можно сразу вставить в проект .NET.

> **Prerequisites**  
> • .NET 6 (или любой современный .NET Framework) установлен  
> • Visual Studio 2022 или ваша любимая IDE  
> • Лицензированная копия **Aspose.Words for .NET** (бесплатная пробная версия подходит для тестирования)  

Если всё это у вас есть, давайте начнём.

---

## Save Word Document and Detect Missing Fonts

Основная идея проста: перед вызовом `Document.Save` назначьте объект, реализующий `IWarningCallback`, свойству `Document.WarningCallback`. Aspose.Words будет вызывать этот объект для каждого предупреждения, которое он обнаружит, включая предупреждения **font substitution**, возникающие, когда исходный документ ссылается на шрифт, отсутствующий в вашей системе.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**What you’ll see:**  
Если `input.docx` ссылается на шрифт, который не установлен, консоль выведет что‑то вроде:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Эта строка точно указывает, какой шрифт отсутствовал и какой шрифт использовал Aspose.Words вместо него — идеально для **capturing font errors** перед отправкой файла.

---

## Track Missing Fonts with a Warning Callback (Step‑by‑Step)

### 1️⃣ Install Aspose.Words

Откройте консоль NuGet вашего проекта и выполните:

```bash
dotnet add package Aspose.Words
```

Это загрузит последнюю стабильную версию (на данный момент 24.10). Поддержание библиотеки в актуальном состоянии гарантирует доступ к новейшим возможностям **detect missing fonts** и исправлениям ошибок.

### 2️⃣ Define the Warning Handler

Зачем нужен отдельный класс? Реализация `IWarningCallback` позволяет централизовать всю логику предупреждений в одном месте. Вы также можете записывать их в файл, отправлять телеметрию или бросать исключение, если отсутствие шрифта является критической ошибкой для вашего процесса.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** Если вам нужно **track missing fonts** в большом количестве документов, храните сообщения в `List<string>` внутри обработчика и предоставляйте их позже для отчётов.

### 3️⃣ Load Your Source Document

Конструктор `Document` может принимать путь к файлу, поток или даже массив байтов. В большинстве случаев вы указываете путь к `.docx`, полученному от пользователя или из другой системы.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Если файл большой, рассмотрите возможность использования `LoadOptions` для включения ленивой загрузки, что снижает нагрузку на память.

### 4️⃣ Attach the Callback

Назначьте экземпляр свойству `doc.WarningCallback`. С этого момента каждое предупреждение (включая замену шрифтов) будет проходить через ваш обработчик.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Save the Document

Теперь можно безопасно вызвать `Save`. Обработчик предупреждений работает **synchronously** во время операции сохранения, поэтому вывод появится сразу.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Если вы предпочитаете сохранять в другой формат (PDF, HTML и т.д.), тот же механизм предупреждений работает — Aspose.Words всё равно сообщит об отсутствующих шрифтах до конвертации.

---

## Capture Font Errors – Common Edge Cases

Хотя базовый поток покрывает большинство сценариев, в реальных проектах часто возникают нюансы. Ниже перечислены варианты, с которыми вы можете столкнуться, и способы их обработки.

### Missing Font in a Header/Footer

Колонтитулы — отдельные узлы, но система предупреждений обрабатывает их так же, как основной текст. Дополнительный код не нужен; callback сработает и для этих шрифтов. Просто убедитесь, что загружаете весь документ (поведение по умолчанию таково).

### Multiple Substitutions in One Document

Если документ использует несколько неизвестных шрифтов, обработчик будет вызван один раз для каждой замены. Чтобы не захламлять консоль, можно удалять дублирующие сообщения:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Turning Warnings into Exceptions

Иногда отсутствие шрифта является критическим. Бросьте исключение внутри обработчика, чтобы прервать сохранение:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Не забудьте обернуть `doc.Save` в блок `try/catch`, чтобы корректно обработать исключение.

---

## Verify the Result – What to Expect

После завершения сохранения откройте `output.docx` в Microsoft Word (или любом совместимом просмотрщике). Вы должны увидеть тот же визуальный макет, что и в оригинале, но заменённые шрифты отобразятся как fallback, который вы увидели в консоли. Чтобы проверить ещё раз, можно:

1. Открыть **File → Options → Advanced → Show document content → Use draft quality** — это заставит Word показать любые скрытые замены шрифтов.  
2. Воспользоваться диалогом **Replace Fonts** в Word (`Ctrl+Shift+F`), чтобы увидеть, какие шрифты действительно встроены.

Если всё совпадает, вы успешно **saved word document** при **detecting missing fonts** и **capturing font errors**. 🎉

---

## Full Working Example (Copy‑Paste Ready)

Ниже представлен полный код программы, который можно вставить в новый проект Console App. Просто замените `YOUR_DIRECTORY` на реальный путь к папке на вашем компьютере.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Expected console output** (example):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Это весь процесс — без скрытых шагов и внешних документов.

---

## Conclusion

Мы только что показали, как **save word document**, одновременно **detect missing fonts**, **track missing fonts** и **capture font errors** с помощью callback‑а предупреждений Aspose.Words. Подключив небольшую реализацию `IWarningCallback`, вы получаете полную видимость замен шрифтов во время сохранения, что даёт возможность вести журнал, заменять шрифты или прерывать процесс по необходимости.  

Готовы к следующему вызову? Попробуйте расширить обработчик, чтобы записывать предупреждения в структурированный JSON‑лог, или объедините его с Aspose.PDF для конвертации того же документа с сохранением информации о шрифтах. Вы также можете изучить возможность встраивания отсутствующих шрифтов непосредственно в итоговый файл — Aspose.Words поддерживает встраивание шрифтов через `LoadOptions.FontSettings`.  

Запустите пример, адаптируйте код под ваш конвейер и дайте нам знать, как всё работает. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}