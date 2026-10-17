---
category: general
date: 2026-04-24
description: Как обнаружить замену отсутствующих шрифтов в Aspose.Words с помощью
  C#. Это руководство показывает, как надёжно обрабатывать отсутствующие шрифты с
  помощью предупреждений FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: ru
og_description: Как обнаружить замену отсутствующих шрифтов в Aspose.Words с помощью
  C#. Узнайте, как обрабатывать отсутствующие шрифты с помощью предупреждений FontSettings.
og_title: Как обнаружить подстановку в Aspose.Words – Полное руководство
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Как обнаружить замену в Aspose.Words — Обрабатывать недостающие шрифты
url: /ru/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как обнаружить замену шрифтов в Aspose.Words – Обработка отсутствующих шрифтов

Задумывались ли вы когда‑нибудь **как обнаружить замену** шрифта, когда документ пытается использовать шрифт, который не установлен на вашем сервере? Это распространённая проблема, особенно когда вы генерируете PDF или Word‑файлы в автоматизированном конвейере. Хорошая новость в том, что Aspose.Words предоставляет встроенный механизм, позволяющий точно обнаружить эту ситуацию, и вы также можете **обрабатывать отсутствующие шрифты** без сбоев.

В этом руководстве мы пройдем реальный пример, показывающий **как обнаружить замену** через событие `FontSettings.Warning`, и объясним, как **обрабатывать отсутствующие шрифты**, не нарушая процесс обработки. К концу вы получите готовый к запуску фрагмент кода, чёткое понимание, почему каждая строка важна, и несколько советов, как избежать типичных подводных камней.

## Необходимые условия

- .NET 6.0 или новее (код также работает на .NET Framework)  
- Aspose.Words for .NET (NuGet‑пакет `Aspose.Words`) – версия 23.11 или новее  
- Пример документа, который ссылается на шрифт, не установленный у вас (например, `MissingFont.docx`)  
- Visual Studio, VS Code или любой другой C# IDE по вашему выбору  

Дополнительная конфигурация не требуется, достаточно добавить NuGet‑пакет.

---

## Как обнаружить замену с помощью FontSettings

Суть **как обнаружить замену** заключается в событии `FontSettings.Warning`. Когда Aspose.Words не может найти запрошенный шрифт, он генерирует предупреждение `WarningType.FontSubstitution`. Подписавшись на это событие, вы получаете уведомление в реальном времени с оригинальным именем шрифта и шрифтом, использованным в качестве резервного.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Почему это работает:**  
- `LoadOptions.FontSettings` указывает Aspose.Words использовать только что созданный объект `FontSettings`.  
- Подписка на `Warning` даёт единую точку мониторинга *всех* проблем, связанных со шрифтами, а не только отсутствующих.  
- Фильтр `WarningType.FontSubstitution` гарантирует, что вы реагируете только на интересующий вас сценарий – суть **как обнаружить замену**.

### Ожидаемый вывод

Запуск кода выше с документом, который ссылается на несуществующий шрифт, выведет что‑то вроде:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Если документ использует только установленные шрифты, консоль остаётся тихой – чёткий сигнал, что **как обнаружить замену** сработало без ложных тревог.

## Обработка отсутствующих шрифтов без сбоев

Обнаружение замены – лишь половина задачи; также нужна стратегия **обрабатывать отсутствующие шрифты**, чтобы итоговый результат выглядел как задумано. Ниже три практических подхода, которые можно комбинировать.

### 1. Предоставьте папку с резервными шрифтами

Aspose.Words может искать шрифты в дополнительных каталогах. Указав папку, содержащую наиболее часто используемые шрифты, вы полностью исключаете вероятность замены.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Почему:** Когда оригинальный шрифт отсутствует, у Aspose.Words теперь есть известный набор альтернатив, что часто приводит к более предсказуемому визуальному результату.

### 2. Заменить отсутствующие шрифты программно

Если нужен полный контроль, после обнаружения можно заменить отсутствующий шрифт на конкретный.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Почему:** Это явно указывает движку, какие шрифты использовать, позволяя соблюдать фирменный стиль компании или требования доступности.

### 3. Журналировать и прерывать (когда замена недопустима)

Иногда отсутствие шрифта делает документ недопустимым для вашего сценария (например, юридические формы). В таком случае можно выбросить исключение сразу при возникновении замены.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Почему:** Немедленный сбой предотвращает последующие ошибки, такие как смещённые таблицы или повреждённые подписи.

## Полный рабочий пример – все шаги вместе

Ниже представлен единый, готовый к копированию и вставке, пример программы, демонстрирующий **как обнаружить замену** *и* несколько способов **обрабатывать отсутствующие шрифты**. При желании закомментируйте ненужные части.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Что ожидать:**  
- Если `MissingFont.docx` ссылается на шрифт, которого нет на машине, консоль выведет предупреждение о замене.  
- Сохранённый `Processed.docx` использует резервный шрифт, который вы настроили (или шрифт по умолчанию библиотеки).  
- Необработанных исключений не будет, если только вы специально не прервете процесс при замене.

## Часто задаваемые вопросы и особые случаи

| Question | Answer |
|----------|--------|
| *What if the document contains many missing fonts?* | The warning event fires for **each** substitution, so you’ll see multiple lines. You can aggregate them into a list for a summary report. |
| *Does this work with PDF conversion?* | Absolutely. The same `FontSettings` are respected when you call `doc.Save("out.pdf")`. The substitution warning still fires, letting you verify the PDF’s visual fidelity. |
| *Can I detect substitution after the document is already loaded?* | Not directly. The warning is raised **during** loading or saving. If you need post‑load analysis, capture the warnings into a collection during the load phase. |
| *What about custom fonts embedded in the DOCX?* | Embedded fonts are considered present, so no substitution occurs. If the embedded font is corrupted, Aspose.Words still raises a warning, which you can catch the same way. |
| *Is there a performance impact?* | Minimal. The warning check is lightweight; the real cost is loading the document itself. Adding a fonts folder may increase search time slightly, but only on the first load. |

## Профессиональные советы и подводные камни

- **Pro tip:** Always set `recursive: true` when pointing to a folder with many fonts; otherwise sub‑folders are ignored.  
- **Watch out for:** Case‑sensitivity on Linux. Font names are case‑insensitive on Windows but not on Linux, so use the exact name or add both variants.  
- **Remember:** If you’re running in a containerized environment, make sure the font folder is part of the image or mounted at runtime.  
- **Tip:** Store warnings in a `List<string>` if you need to present a summary to end‑users or log them to a monitoring system.  

## Заключение

Мы рассмотрели **как обнаружить замену** отсутствующих шрифтов в Aspose.Words, показали несколько способов **обрабатывать отсутствующие шрифты** и предоставили полностью готовый к запуску пример, который можно вставить в любой .NET‑проект. Подключившись к событию `FontSettings.Warning`, вы получаете мгновенную видимость проблем со шрифтами, а с помощью резервных папок или явных правил замены сохраняете вывод точно таким, каким его ожидаете.

Готовы к следующему шагу? Попробуйте расширить решение, автоматически внедряя резервный шрифт в генерируемый PDF, или подключить обработчик предупреждений к централизованному сервису логирования для масштабных конвейеров документов. Обсуждаемые сегодня шаблоны — обнаружение через события, плавный резерв, явная обработка ошибок — применимы ко многим другим API Aspose, так что теперь вы готовы решать задачи, связанные со шрифтами, во всех проектах.

Есть дополнительные вопросы о работе со шрифтами, конвертации в PDF или трюках Aspose.Words? Оставляйте комментарий ниже, и удачной разработки!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}