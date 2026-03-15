---
category: general
date: 2026-03-14
description: Быстро обрабатывайте отсутствующие шрифты с помощью Aspose.Words. Узнайте,
  как перехватывать предупреждения о замене шрифтов, настраивать LoadOptions и избегать
  проблем с отображением.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: ru
og_description: Обрабатывайте отсутствующие шрифты в Aspose.Words с помощью сборщика
  предупреждений. Этот учебник пошагово показывает, как обнаруживать и фиксировать
  замену шрифтов.
og_title: Обработка отсутствующих шрифтов в Aspose.Words – Полное руководство по C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Обработка отсутствующих шрифтов в Aspose.Words – Полное руководство по C#
url: /ru/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

translation.

Be careful with bullet points: use same markdown list syntax.

Tables: keep same.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Обработка отсутствующих шрифтов в Aspose.Words – Полное руководство на C#

Когда‑то вам приходилось **обрабатывать отсутствующие шрифты** при загрузке Word‑документа и задаваться вопросом, почему ваш PDF или изображение выглядят некорректно? Вы не одиноки. Отсутствующие файлы шрифтов – это тихий виновник, который может превратить идеально оформленный отчёт в набор символов.  

Хорошая новость? Aspose.Words предоставляет удобный способ отлавливать события подстановки шрифтов, логировать их и даже заменять шрифт‑запасом, если нужно. В этом руководстве мы пройдём через полностью готовый к запуску пример, показывающий, как настроить сборщик предупреждений, привязать его к `LoadOptions` и загрузить документ, в котором могут отсутствовать шрифты.

К концу этого руководства вы сможете:

* Выявлять каждую подстановку шрифта, происходящую во время загрузки документа.  
* Выводить дружелюбное сообщение в консоль (или направлять его в логгер) для каждого отсутствующего шрифта.  
* Расширять решение для замены шрифтов, если потребуется.  

**Предварительные требования** – вам понадобится:

* .NET 6.0 или новее (код работает и с .NET Core, и с .NET Framework).  
* NuGet‑пакет Aspose.Words for .NET (текущая версия 23.11).  
* Word‑файл, который намеренно ссылается на шрифт, не установленный у вас – назовём его `doc-with-missing-font.docx`.  

Если вы уже уверенно владеете C# и у вас настроен проект, можете сразу перейти к коду. В противном случае читайте дальше – мы сначала рассмотрим небольшие шаги настройки.

---

## Почему важно обрабатывать отсутствующие шрифты

Когда Aspose.Words загружает документ, он пытается сопоставить каждый глиф с шрифтом, установленным на машине. Если точный шрифт не найден, он тихо подставляет ближайший вариант. Такая подстановка может изменить высоту строк, кернинг и даже привести к исчезновению символов. Отлавливая событие `WarningType.FontSubstitution`, вы получаете прозрачный обзор **что** было заменено и **почему**, что необходимо для:

* Поддержания фирменного стиля (корпоративный шрифт должен выглядеть точно так же, как задуман).  
* Отладки проблем конвертации в PDF — часто виновником является отсутствующий шрифт.  
* Создания автоматизированных конвейеров обработки документов, где нужно помечать проблемные файлы для ручной проверки.

Теперь, когда «почему» понятно, перейдём к «как».

---

## Шаг 1 – Настройка сборщика предупреждений

Первое, что нам нужно, – объект, способный слушать предупреждения Aspose.Words. `DocumentWarnings` реализует `IWarningCallback`, позволяя реагировать каждый раз, когда библиотека генерирует предупреждение.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Что происходит?**  
* `DocumentWarnings` – это лёгкая оболочка вокруг интерфейса обратного вызова.  
* Лямбда‑выражение проверяет `e.WarningType`, поэтому мы игнорируем несвязанные предупреждения (например, устаревшие возможности).  
* `e.WarningInfo` содержит название отсутствующего шрифта, которое мы выводим в консоль.  

*Совет*: замените `Console.WriteLine` на структурированный логгер (Serilog, NLog) в продакшене — так вы получите метки времени и уровни логов «из коробки».

---

## Шаг 2 – Подключение сборщика к LoadOptions

`LoadOptions` – это контроллер доступа для каждого документа, открываемого через Aspose.Words. Присвоив наш экземпляр `fontWarnings` свойству `WarningCallback`, мы гарантируем, что сборщик будет активен во время загрузки.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Зачем использовать LoadOptions?**  
Помимо предупреждений, `LoadOptions` позволяет управлять паролями, кодировкой и даже пользовательской загрузкой ресурсов. Здесь мы сосредоточились на части с предупреждениями, но тот же шаблон работает и с другими обратными вызовами.

---

## Шаг 3 – Загрузка документа с настроенными параметрами

Теперь мы наконец‑то загружаем документ в память. Если какой‑либо шрифт отсутствует, наш сборщик сработает, и вы увидите строку в консоли для каждой подстановки.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Если запустить этот фрагмент с документом, который, скажем, ссылается на *Calibri Light*, а на тестовой машине установлен только *Calibri*, вы получите вывод, похожий на:

```
Font 'Calibri Light' was substituted.
```

Это весь цикл обнаружения — простой, но мощный.

---

## Шаг 4 – (Опционально) Замена отсутствующих шрифтов известным запасным

Иногда недостаточно лишь залогировать проблему; нужно обеспечить подстановочный шрифт, чтобы результирующее отображение выглядело одинаково. Aspose.Words позволяет задать пользовательский объект `FontSettings`, который сопоставляет отсутствующие шрифты заменой.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Пояснение**  
* Шаблон `"*"` сообщает Aspose.Words обрабатывать *любой* отсутствующий шрифт одинаково.  
* При необходимости можно сопоставлять конкретные шрифты по отдельности для более тонкой настройки.  
* После установки `document.FontSettings` любые последующие рендеры (PDF, изображение, HTML) учитывают эту подстановку.

---

## Полный рабочий пример

Ниже представлен полностью готовый к копированию в консольное приложение код. В нём присутствуют все необходимые `using`, обработка ошибок и комментарии для ясности.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Ожидаемый вывод** (при обнаружении отсутствующего шрифта):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Если исходный документ уже содержит все требуемые шрифты, строка предупреждения просто не появится — о чём беспокоиться не нужно.

---

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **А что если я хочу только логировать, а не заменять шрифты?** | Просто пропустите блок `FontSettings`; одного сборщика предупреждений достаточно. |
| **Можно ли перенаправить предупреждения в файл?** | Да — замените `Console.WriteLine` на `File.AppendAllText("font-warnings.log", …)`. |
| **Работает ли это для DOC, DOCX и ODT?** | Абсолютно. `LoadOptions` применяется ко всем форматам, поддерживаемым Aspose.Words. |
| **Что насчёт пользовательских шрифтов, встроенных в документ?** | Встроенные шрифты обходят механизм подстановки; они используются как есть. |
| **Есть ли влияние на производительность?** | Нагрузка минимальна — вызывается один обратный вызов на каждый отсутствующий шрифт. Для больших пакетов рекомендуется агрегировать предупреждения вместо записи по событию. |

---

## Заключение

Мы продемонстрировали **как обрабатывать отсутствующие шрифты** в Aspose.Words, подключив сборщик `DocumentWarnings` к `LoadOptions`, при желании заменив их запасным шрифтом и сохранив результат. Этот шаблон даёт полную видимость событий подстановки шрифтов, помогая поддерживать визуальную целостность при конвертации в PDF, изображения или HTML.

Возможные дальнейшие шаги:

* Интегрировать сборщик предупреждений с централизованным фреймворком логирования.  
* Создать UI‑дашборд, перечисляющий документы с отсутствующими шрифтами для пакетной обработки.  
* Сочетать этот подход с Aspose.PDF, чтобы проверять, действительно ли сгенерированные PDF используют запасной шрифт.  

Экспериментируйте — заменяйте `"Arial"` на `"Tahoma"` или загружайте другой набор документов. Основная идея остаётся той же: фиксировать предупреждение, реагировать на него и сохранять документы в точном виде, как задумано.

Счастливого кодинга! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}