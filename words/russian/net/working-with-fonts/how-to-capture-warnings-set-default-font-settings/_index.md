---
category: general
date: 2026-03-19
description: Узнайте, как перехватывать предупреждения в Aspose.Words, задавать настройки
  шрифта по умолчанию и обнаруживать отсутствующие шрифты при загрузке документа Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: ru
og_description: Как перехватывать предупреждения в Aspose.Words, задавать настройки
  шрифта по умолчанию и обнаруживать отсутствующие шрифты при загрузке документа Word.
og_title: Как фиксировать предупреждения – установить настройки шрифта по умолчанию
tags:
- Aspose.Words
- C#
- Document Processing
title: Как захватывать предупреждения — установить настройки шрифта по умолчанию
url: /ru/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как захватывать предупреждения – Установить настройки шрифта по умолчанию

**How to capture warnings** — это распространённая необходимость при работе с Aspose.Words, особенно если ваши документы зависят от конкретных шрифтов, которые могут отсутствовать на целевой машине. Когда‑ли открывали DOCX и задавались вопросом, почему макет выглядит некорректно? Ответ часто скрыт в предупреждении о недостающем шрифте.  

В этом руководстве мы пройдёмся по **how to capture warnings**, пока вы **load word document**, настроите **set default font settings**, и, наконец, **detect missing fonts**, чтобы вы могли реагировать программно. Без лишних слов — только полностью рабочий пример и объяснение каждой строки.

> *Pro tip:* Capturing warnings early saves you from debugging mysterious layout glitches later.

---

## Что понадобится

- **Aspose.Words for .NET** (latest version as of 2026).  
- Среда разработки .NET (Visual Studio, Rider или VS Code).  
- Пример DOCX, который ссылается на шрифт, которого у вас *нет* установленного (например, *Comic Sans MS* на Linux‑машине).  

Вот и всё. Дополнительные пакеты NuGet не требуются, кроме Aspose.Words.

---

## Шаг 1 – Поймите, зачем нужно захватывать предупреждения

Когда Aspose.Words разбирает документ, он может столкнуться со шрифтами, недоступными на хосте. По умолчанию библиотека тихо заменяет их резервным шрифтом, что может изменить переносы строк, интервалы и даже привести к исчезновению текста.  

Использование **WarningCallback** вместе с объектом **FontSettings** даёт вам два преимущества:

1. **Visibility** – вы получаете запись `WarningInfo` для каждой замены.  
2. **Control** – можете предварительно задать шрифт по умолчанию, чтобы минимизировать визуальные сюрпризы.

Это как установить «сторожевого пса», который будет орать каждый раз, когда под капотом меняется деталь.

---

## Шаг 2 – Установить настройки шрифта по умолчанию

Первое вторичное ключевое слово, **set default font settings**, появляется здесь же. Вы создаёте экземпляр `FontSettings` и, при желании, указываете папку, содержащую ваши резервные шрифты.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Почему?**  
> Если не указать резервный шрифт, Aspose.Words выбирает первый системный шрифт, соответствующий стилю, который может сильно отличаться. Установив известный шрифт по умолчанию, вы гарантируете одинаковый рендеринг на разных машинах.

---

## Шаг 3 – Подготовьте обратный вызов предупреждений для захвата предупреждений

Теперь мы **how to capture warnings**, присоединив `WarningInfoCollection` к параметрам загрузки. Эта коллекция будет хранить каждое предупреждение, возникшее во время процесса загрузки.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` реализует `IWarningCallback`, поэтому Aspose.Words автоматически помещает каждое предупреждение в `warningInfos`. Нет необходимости опрашивать.

---

## Шаг 4 – Загрузить Word‑документ с настроенными параметрами

Здесь в игру вступает второе вторичное ключевое слово, **load word document**. Мы передаём как `FontSettings`, так и `WarningCallback` через экземпляр `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Если документ ссылается на шрифт, который не установлен, обратный вызов предупреждений захватит запись `WarningType.FontSubstitution`.

---

## Шаг 5 – Обнаружить недостающие шрифты из собранных предупреждений

Наконец, мы отвечаем на третье вторичное ключевое слово, **detect missing fonts**, перебирая собранные предупреждения.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Типичный вывод выглядит так:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Эта строка точно указывает, какой шрифт отсутствует и какой резервный был использован — информацию, которую можно записать в лог, показать пользователю или даже запустить пользовательскую процедуру установки шрифта.

---

## Полный исполняемый пример

Ниже представлен полный код, который можно скопировать в консольное приложение. Он демонстрирует **how to capture warnings**, **set default font settings**, **load word document** и **detect missing fonts** в одном потоке.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Ожидаемый результат:** Когда указанный DOCX ссылается на шрифт, которого нет, консоль выводит предупреждение для каждой замены. Если все шрифты присутствуют, цикл ничего не выводит.

---

## Распространённые подводные камни и граничные случаи

| Ситуация | Почему происходит | Как решить |
|-----------|-------------------|------------|
| **No warnings appear** even though the layout looks wrong | Документ может использовать *embedded* шрифты, которые Aspose.Words рендерит без замены. | Проверьте `Document.HasEmbeddedFonts` и рассмотрите возможность извлечения встроенных шрифтов, если они нужны на другой машине. |
| **Multiple warnings for the |  |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}