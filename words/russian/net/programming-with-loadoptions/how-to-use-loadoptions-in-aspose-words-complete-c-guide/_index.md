---
category: general
date: 2026-04-10
description: Как использовать LoadOptions в Aspose.Words для получения предупреждений
  о замене шрифтов при загрузке документов. Узнайте пошаговое решение на C# с полным
  примером кода.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: ru
og_description: Как использовать LoadOptions в Aspose.Words для захвата предупреждений
  о замене шрифтов при загрузке документов. Это руководство проведёт вас через полную
  реализацию на C#.
og_title: Как использовать LoadOptions в Aspose.Words – Полное руководство по C#
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Как использовать LoadOptions в Aspose.Words – Полное руководство по C#
url: /ru/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как использовать LoadOptions в Aspose.Words – Полное руководство на C#

Как использовать LoadOptions в Aspose.Words — частая проблема, когда требуется точный контроль над загрузкой документа. В этом руководстве мы покажем, **как использовать LoadOptions**, чтобы отлавливать предупреждения о замене шрифтов и реагировать на них в C#.  

Если вы когда‑нибудь открывали DOCX, в котором ссылались на отсутствующий шрифт, и задавались вопросом, почему результат выглядит странно, вы попали по адресу. Мы пройдем весь процесс, от создания экземпляра `LoadOptions` до вывода деталей предупреждения в консоль. К концу вы получите готовый фрагмент кода, который можно вставить в любой .NET‑проект.

## Что вы узнаете

- Почему `LoadOptions` важен для надёжного импорта документов.  
- Как подключить **WarningCallback**, который специально отслеживает **предупреждения о замене шрифтов**.  
- Точный код, необходимый для загрузки Word‑файла с включёнными этими параметрами.  
- Советы по обработке крайних случаев, например, документов, содержащих несколько отсутствующих шрифтов.  

Никакой внешней документации не требуется — всё, что нужно, находится здесь.

## Предварительные требования

| Требование | Причина |
|-------------|--------|
| .NET 6.0 или новее | Предоставляет среду выполнения для синтаксиса C# 10, используемого в примерах. |
| Aspose.Words for .NET (последняя версия) | Библиотека, в которой реализованы `LoadOptions` и инфраструктура предупреждений. |
| DOCX‑файл, который может ссылаться на шрифты, не установленные в системе | Чтобы увидеть работу callback‑а предупреждений. |
| Visual Studio 2022 (или любая другая IDE) | Делает отладку и тестирование простыми. |

Если у вас уже всё готово, отлично — приступаем.

## Шаг 1 – Создайте объект LoadOptions и привяжите WarningCallback

Первое, что нужно сделать, когда вы **как использовать LoadOptions**, — создать его экземпляр. Ключевая часть — назначить делегат `WarningCallback`. Этот делегат вызывается каждый раз, когда Aspose.Words сталкивается с ситуацией, о которой хочет вас предупредить, в частности, при отсутствии шрифта.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Почему это важно:** Без callback‑а Aspose.Words тихо заменяет отсутствующие шрифты стандартными, и вы можете никогда не заметить визуального сдвига. Зарегистрировав `WarningCallback`, вы получаете в реальном времени журнал каждой замены, что критично для конвейеров обработки документов с гарантией качества.

## Шаг 2 – Реагируйте только на предупреждения о замене шрифтов

Возможно, вы задаётесь вопросом, не будет ли callback захламлять вас нерелевантными предупреждениями (например, о устаревших функциях). Ответ — *да*, но мы можем их отфильтровать. В приведённом выше фрагменте кода уже проверяется `args.WarningType == WarningType.FontSubstitution`. Эта строка служит **охраной от предупреждений о замене шрифтов**, вторичным условием, которое сохраняет вывод сфокусированным.

Если понадобится обрабатывать другие типы предупреждений, просто расширьте блок `if`:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Этот шаблон демонстрирует гибкость механизма **warningcallback**, позволяя настроить реакции точно под нужные вам сценарии.

## Шаг 3 – Загрузите документ, используя сконфигурированные LoadOptions

Теперь, когда слушатель готов, последний шаг — передать экземпляр `LoadOptions` конструктору `Document`. Именно в этот момент **пример Aspose.Words LoadOptions** действительно проявляет свою силу.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Что вы увидите:** Если DOCX ссылается на шрифт, который не установлен на машине, консоль выведет строку вроде:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Этот вывод подтверждает, что вы успешно **как использовать LoadOptions** для мониторинга проблем со шрифтами.

## Полный рабочий пример (готов к копированию)

Ниже представлена полная программа, которую можно сразу скомпилировать и запустить. Она объединяет все три шага, добавляет несколько приятных деталей (например, приветственный баннер) и демонстрирует обработку ошибок.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Ожидаемый вывод

Запуск программы на машине, где отсутствует шрифт, указанный в `input.docx`, даст примерно следующее:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Если все шрифты присутствуют, вы увидите только сообщения об успешном выполнении — строк с предупреждениями не будет.

## Распространённые ошибки и профессиональные советы

- **Ошибка:** Не задали `WarningCallback`. Код всё равно загрузит документ, но вы упустите детали замены.  
  **Совет:** Всегда назначайте callback сразу после создания `LoadOptions`; это дешево и окупается позже.

- **Ошибка:** Используете относительный путь, который указывает не в ту папку.  
  **Совет:** Применяйте `Path.Combine(Environment.CurrentDirectory, "input.docx")` для более надёжного поиска файла.

- **Ошибка:** Считаете, что предупреждение остановит загрузку.  
  **Совет:** Предупреждения о замене шрифтов *информационные*; они не прерывают загрузку. Если нужна более строгая проверка, бросайте исключение внутри callback при обнаружении замены.

- **Ошибка:** Запускаете приложение на сервере без установленных шрифтов (например, минимальный Docker‑образ).  
  **Совет:** Предустановите необходимые шрифты или включите их в пакет приложения, затем проверьте через callback, что в продакшене нет замен.

## Когда использовать LoadOptions вместо пост‑загрузочной инспекции

Вы можете спросить: «Зачем проверять документ после загрузки?» Ответ кроется в производительности и корректности. Обрабатывая предупреждения **во время** загрузки, вы ловите проблемы сразу — до расчётов макета или конвертации в PDF. Это особенно ценно в пакетных конвейерах, где каждый лишний шаг добавляет время.

## Расширение примера: сохранение отчёта о всех заменённых шрифтах

Если нужен постоянный журнал (например, для соответствия требованиям), измените callback так, чтобы он собирал сообщения в список и записывал их в файл после загрузки:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Теперь у вас есть как консольный вывод, так и надёжный лог.

## Связанные темы для дальнейшего изучения

- **Как встроить пользовательские шрифты в Aspose.Words** — полностью устраняет замену.  
- **Использование LoadOptions для ограничения размера документа** — помогает защититься от злонамеренно больших файлов.  
- **Конвертация Word в PDF с сохранением типографии** — отлично сочетается с подходом через warning‑callback.  

Каждая из этих тем опирается на основу, которую вы только что создали с помощью `LoadOptions`.

## Заключение

Мы рассмотрели **как использовать LoadOptions** в Aspose.Words от начала до конца: создали параметры, привязали `WarningCallback`, сфокусированный на **предупреждениях о замене шрифтов**, и загрузили документ с уверенностью. Полный пример работает «из коробки», а дополнительные советы помогут избежать типичных ловушек.  

Экспериментируйте — заменяйте callback на другие типы предупреждений, записывайте их в базу данных или интегрируйте логику в веб‑службу, проверяющую загружаемые Word‑файлы. Этот паттерн гибок, надёжен и, что самое главное, даёт вам видимость скрытого процесса замены шрифтов, который иначе может испортить отображение ваших документов.

Счастливого кодинга, и пусть ваши документы всегда отображаются точно так, как задумано! 

![Диаграмма, показывающая поток использования LoadOptions с callback‑ом предупреждений в Aspose.Words](https://example.com/images/loadoptions-flow.png "Диаграмма как использовать LoadOptions")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}