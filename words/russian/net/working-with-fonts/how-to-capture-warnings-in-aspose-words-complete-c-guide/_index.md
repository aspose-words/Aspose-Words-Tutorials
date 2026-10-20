---
category: general
date: 2026-03-28
description: Как перехватывать предупреждения при загрузке DOCX с помощью Aspose.Words
  и получать сообщения о недостающих шрифтах. Узнайте, как эффективно обрабатывать
  недостающие шрифты.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: ru
og_description: Как перехватывать предупреждения при загрузке DOCX с помощью Aspose.Words,
  получать сообщения предупреждений и обрабатывать отсутствие шрифтов с практическими
  примерами кода.
og_title: Как перехватывать предупреждения в Aspose.Words – Полное руководство по
  C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Как перехватывать предупреждения в Aspose.Words – Полное руководство по C#
url: /ru/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как захватывать предупреждения в Aspose.Words – Полное руководство на C#

Когда‑то задавались вопросом **как перехватывать предупреждения**, возникающие при загрузке Word‑документа с помощью Aspose.Words? Возможно, вы замечаете странные изменения шрифтов и хотите точно знать причину. Кратко: можно подключиться к системе предупреждений библиотеки, **получать сообщения предупреждений** и даже **обрабатывать отсутствующие шрифты**, пока они не испортят ваш макет.  

В этом руководстве мы пройдем реальный сценарий: загрузим DOCX, соберём все предупреждения, которые генерирует движок, и выведем детали о любой подстановке шрифтов. К концу вы получите готовый к запуску пример кода, поймёте «почему» каждого шага и узнаете, как расширить подход для своих проектов.

## Что вы узнаете

- Как настроить `LoadOptions`, чтобы предупреждения автоматически собирались.  
- Точный способ **получить сообщения предупреждений** из `WarningInfoCollection`.  
- Как определить и отреагировать на **отсутствующие шрифты** через флаг `WarningType.FontSubstitution`.  
- Советы по устранению сложных случаев, таких как документы с внедрёнными шрифтами или пользовательскими папками шрифтов.  

Никаких внешних ссылок не требуется – всё, что нужно, находится здесь.

---

## Предварительные требования

- .NET 6.0 или новее (код также работает на .NET Framework 4.7+).  
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Пример DOCX (`input.docx`), в котором либо отсутствуют некоторые шрифты, либо используются шрифты, не установленные на вашей машине.  

Вот и всё. Если вы уже уверенно работаете с C# и Visual Studio, можете скопировать‑вставить код и сразу запустить его.

---

## Шаг 1: Подготовьте параметры загрузки и обратный вызов предупреждений

Первое, что делает Aspose.Words при вызове `new Document(path, loadOptions)`, – это разбор файла. Во время разбора могут встретиться отсутствующие шрифты, неподдерживаемые функции или устаревшая разметка. Чтобы перехватить эти события, нужен объект **обратного вызова предупреждений**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Почему это важно:** Без обратного вызова Aspose.Words молча пишет предупреждения в консоль (или просто отбрасывает их), оставляя вас в неведении о подстановках шрифтов, которые могут повлиять на макет. Предоставив собственный `WarningInfoCollection`, вы получаете полную видимость.

> **Pro tip:** Если вас интересуют только предупреждения, связанные со шрифтами, их можно отфильтровать позже – но сбор *всех* предупреждений даёт запас прочности для будущих проблем.

---

## Шаг 2: Загрузите документ с настроенными параметрами

Теперь, когда обратный вызов готов, загрузите файл. Конструктор `Document` автоматически вызовет обратный вызов для любых найденных проблем.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Что происходит «под капотом»?** Aspose.Words разбирает Open XML, разрешает стили и пытается сопоставить каждую ссылку на шрифт с установленным в системе шрифтом. Если совпадения нет, создаётся запись `WarningInfo` типа `FontSubstitution`.

---

## Шаг 3: Получите и проанализируйте собранные предупреждения

После завершения загрузки ваш `warningCollector` содержит каждое возникшее предупреждение. Достанем их и сосредоточимся на сообщениях о подстановке шрифтов.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Пример вывода** (в вашей консоли может появиться что‑то вроде):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Если хотите увидеть *все* предупреждения, просто уберите проверку `if` или выводите `warning.Type` для каждой записи.

---

## Шаг 4: Обработка отсутствующих шрифтов – не только логирование

Сбор предупреждений полезен, но часто требуется **программно обрабатывать отсутствующие шрифты**. Ниже два распространённых подхода:

### 4.1 Заменить отсутствующие шрифты конкретным запасным шрифтом

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Теперь любой отсутствующий шрифт будет заменён на *Calibri* вместо стандартного запасного шрифта библиотеки.

### 4.2 Динамически внедрить заменяющий шрифт

Если у вас есть пользовательский файл шрифта (например, `MyFallback.ttf`), его можно зарегистрировать во время выполнения:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Этот подход удобен, когда вы распространяете определённый корпоративный шрифт вместе с приложением.

> **Edge case:** Документы, уже содержащие необходимый шрифт, игнорируют правила системной подстановки. В таком случае коллекция предупреждений будет пустой для этого шрифта – именно то, что нужно.

---

## Шаг 5: Полный рабочий пример (готов к копированию)

Ниже представлена автономная программа, демонстрирующая всё от начала до конца. Просто замените `YOUR_DIRECTORY/input.docx` на путь к вашему тестовому файлу.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Что ожидать**

- Консоль выводит каждое предупреждение о подстановке шрифта, предварённое эмодзи‑предупреждением для лучшей заметности.  
- Выходной DOCX (`output.docx`) использует *Calibri* везде, где был обнаружен отсутствующий шрифт.  
- Нет необработанных исключений – система предупреждений аккуратно справляется с любыми неизвестными шрифтами.

---

## Часто задаваемые вопросы

**В: Будет ли это работать с PDF, сгенерированными из Word?**  
О: Да. Aspose.Words рассматривает PDF как другой формат вывода. Захват предупреждений происходит на этапе *загрузки*, поэтому он независим от финального экспорта.

**В: Как захватывать предупреждения для **всех** операций с документом (сохранение, конвертация и т.д.)?**  
О: Вы можете переиспользовать тот же `WarningInfoCollection`, присвоив его `Document.WarningCallback` после создания документа. Каждая последующая операция будет добавлять новые записи в ту же коллекцию.

**В: Влияет ли обратный вызов предупреждений на производительность?**  
О: Незначительно. Коллекция просто хранит объекты; если вы не обрабатываете тысячи предупреждений в тесном цикле, замедления не заметите.

**В: Как подавить предупреждения, которые меня не интересуют?**  
О: Реализуйте собственный класс, наследующий `IWarningCallback`, и фильтруйте внутри метода `Warning`. Встроенный `WarningInfoCollection` только хранит, но не фильтрует.

---

## Полезные советы и подводные камни

- **Pro tip:** Всегда проверяйте `Warning.Description` – в нём указано точное название отсутствующего шрифта. Это поможет решить, стоит ли включать шрифт в поставку вашего приложения.  
- **Следите за внедрёнными шрифтами:** Если исходный DOCX уже содержит нужный шрифт, Aspose.Words не будет генерировать предупреждение о подстановке, даже если шрифт не установлен локально.  
- **Потокобезопасность:** `WarningInfoCollection` не является потокобезопасным. При одновременной загрузке нескольких документов дайте каждому потоку свою коллекцию.  
- **Проверка версии:** API предупреждений стабилен, начиная с Aspose.Words 20.8. Убедитесь, что используете актуальную версию, чтобы не пропустить новые типы предупреждений.

---

## Заключение

Мы рассмотрели **как захватывать предупреждения** из Aspose.Words, продемонстрировали **получение сообщений предупреждений** и показали практические способы **обработки отсутствующих шрифтов** через запасные шрифты или пользовательские папки шрифтов. Полный пример готов к вставке в любой .NET‑проект, а концепции масштабируются до больших автоматизированных конвейеров.

Дальше вы можете изучить:

- Использование `Document.WarningCallback` для захвата предупреждений во время **сохранения**.  
- Запись предупреждений в файл или систему телеметрии для мониторинга в продакшене.  
- Расширение обратного вызова для автоматической замены отсутствующих шрифтов на фирменные типографские решения.

Экспериментируйте – меняйте запасный шрифт, добавляйте больше документов в пакет или интегрируйте сборщик предупреждений в CI‑конвейер, который будет отмечать регрессии, связанные со шрифтами. Приятного кодинга, и пусть ваши документы всегда отображаются точно так, как вы ожидаете!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}