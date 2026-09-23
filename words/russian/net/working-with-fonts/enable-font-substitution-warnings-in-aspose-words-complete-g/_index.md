---
category: general
date: 2026-01-11
description: Включите предупреждения о замене шрифтов, чтобы обнаруживать отсутствующие
  шрифты в ваших .NET‑документах. Узнайте, как получить имя отсутствующего шрифта
  и вывести список отсутствующих шрифтов с помощью Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: ru
og_description: Включите предупреждения о замене шрифтов в Aspose.Words, чтобы обнаруживать
  отсутствующие шрифты, получать их названия и выводить список недостающих шрифтов
  в ваших документах.
og_title: Включить предупреждения о замене шрифтов – пошаговое руководство по C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Включение предупреждений о замене шрифтов в Aspose.Words – Полное руководство
url: /ru/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Включение предупреждений о замене шрифтов – Полное руководство

Когда‑нибудь задавались вопросом, почему документ Word выглядит слегка иначе после загрузки на сервер? Скорее всего, шрифт, использованный оригинальным автором, недоступен на вашей машине, и Aspose.Words тихо заменил его на ближайший аналог. **Включите предупреждения о замене шрифтов**, и вы мгновенно узнаете, какие шрифты отсутствуют, чем они были заменены и как действовать с этой информацией.

В этом руководстве мы пройдем практический пример от начала до конца, показывающий, как **обнаружить отсутствующие шрифты**, получить **имя отсутствующего шрифта**, и даже **список отсутствующих шрифтов** для отчётности. Без лишних деталей, просто чёткое решение, которое вы можете внедрить в любой .NET‑проект уже сегодня.

---

## Что вы узнаете

- Как настроить `LoadOptions`, чтобы Aspose.Words выдавал подробные предупреждения.
- Точный код, необходимый для загрузки документа и перечисления предупреждений, связанных со шрифтами.
- Способы извлечения имени отсутствующего шрифта и его замены, а затем вывода аккуратного отчёта.
- Советы по обработке крайних случаев, таких как документы с десятками отсутствующих шрифтов или пользовательскими папками шрифтов.

### Требования

- .NET 6+ (код также работает с .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 или новее (можно получить из NuGet)
- Пример DOCX, который ссылается на шрифт, не установленный у вас (назовём его `MissingFont.docx`)

Если у вас есть всё необходимое, давайте начнём.

---

## Шаг 1: Настройте LoadOptions для включения предупреждений о замене шрифтов  

Первое, что нужно сделать, — сообщить Aspose.Words, что вас интересуют отсутствующие шрифты. По умолчанию библиотека только внутренне регистрирует предупреждения. Установка `SubstitutionWarningLevel` в `Typical` (или `All` для самого подробного вывода) включает эту функцию.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Почему это важно:**  
Когда `SubstitutionWarningLevel` установлен, каждый раз, когда Aspose.Words не может найти указанный шрифт, он добавляет `FontSubstitutionWarning` в коллекцию `Warnings` документа. Эта коллекция — единственный надёжный способ **обнаружить отсутствующие шрифты** без ручного парсинга документа.

> **Pro tip:** Если вы работаете с набором документов и хотите быть полностью уверены, что поймаете каждую замену, используйте `FontSubstitutionWarningLevel.All`. Это немного шумнее, но гарантирует, что ни одно предупреждение не ускользнет.

---

## Шаг 2: Загрузите документ, используя настроенные параметры  

Теперь, когда система предупреждений готова, загрузите ваш DOCX с помощью `LoadOptions`, которые мы только что подготовили. Путь может быть абсолютным или относительным; просто убедитесь, что файл существует.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Что происходит под капотом?**  
Aspose.Words парсит XML документа, разрешает каждый элемент `<w:font>` и проверяет системный каталог шрифтов (плюс любые пользовательские папки, добавленные в `FontSettings`). Когда шрифт не найден, он фиксирует предупреждение — именно то, что нам нужно для **списка отсутствующих шрифтов** позже.

---

## Шаг 3: Переберите предупреждения и извлеките детали отсутствующего шрифта  

С документом в памяти, коллекция `Warnings` содержит каждое `FontSubstitutionWarning`. Мы пройдем её в цикле, отфильтруем нужный тип и выведем удобный отчёт.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Ожидаемый вывод** (при условии, что исходный документ ссылается на `MyCustomFont`, который не установлен):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Обратите внимание, что каждая запись предоставляет как **имя отсутствующего шрифта** (`MyCustomFont`), так и замену (`Arial`). Это именно та информация, которая нужна, чтобы решить, встраивать оригинальный шрифт, попросить автора о замене или просто принять замену.

---

## Шаг 4: Необязательно — собрать данные в список для дальнейшей обработки  

Если вам нужно экспортировать отчёт в CSV, отправить его через API или просто хранить в памяти для последующего использования, вы можете сохранить предупреждения в строго типизированный список.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Теперь у вас есть **список отсутствующих шрифтов** в формате, пригодном для любого downstream‑системы. Будь то панель мониторинга или журнал аудита, данные готовы.

---

## Шаг 5: Обработка крайних случаев и распространённых подводных камней  

### Несколько отсутствующих шрифтов за один запуск  

Большие корпоративные шаблоны часто ссылаются на десятки пользовательских шрифтов. Коллекция предупреждений может стать объёмной, но показанный выше шаблон итерации масштабируется линейно, поэтому производительность не является проблемой. Просто помните, что вывод должен оставаться читаемым — группировка по страницам или стилям может быть полезна, если нужен более глубокий анализ.

### Пользовательские папки шрифтов  

Если вы храните шрифты в нестандартной директории (например, на общем сетевом ресурсе), укажите Aspose.Words, где их искать:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Установка этого *до* загрузки документа даёт библиотеке шанс найти шрифты, что может полностью устранить некоторые предупреждения.

### Подавление конкретных предупреждений  

Иногда вы знаете, что конкретная замена приемлема (например, декоративный шрифт, замену которого вы не возражаете). Вы можете отфильтровать их после факта:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Совместимость версий  

Перечисление `FontSubstitutionWarningLevel` стабильно с версии Aspose.Words 20.12. Если вы используете более старую версию, возможно, потребуется обновление для доступа к функции уровня предупреждений.

---

## Полный рабочий пример  

Ниже представлен полный готовый к запуску пример программы, включающий все шаги выше. Вставьте его в новый консольный проект, добавьте пакет Aspose.Words из NuGet и укажите `docPath` на документ, который ссылается на отсутствующий шрифт.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Запуск этой программы **включит предупреждения о замене шрифтов**, **обнаружит отсутствующие шрифты**, **получит имя отсутствующего шрифта** и **выведет список отсутствующих шрифтов** как в консоль, так и в CSV‑файл.

---

## Заключение  

Мы только что рассмотрели всё, что необходимо для **включения предупреждений о замене шрифтов** в Aspose.Words, от начальной конфигурации до получения чистого списка отсутствующих шрифтов. Следуя приведённым шагам, вы сможете проверять свои документы, обеспечивать визуальную точность и избегать неприятных сюрпризов при рендеринге на сервере.

Далее вы можете изучить:

- **Встраивание отсутствующих шрифтов** непосредственно в выходной PDF или DOCX (используйте `FontSettings.EmbeddedFonts`).
- **Автоматизация установки шрифтов** на сборочных агентах на основе сгенерированного отчёта.
- **Интеграция с CI‑конвейерами** для провала сборок, когда критические шрифты отсутствуют.

Попробуйте их, и вы превратите простую систему предупреждений в полноценный процесс управления шрифтами.

Счастливого кодинга, и пусть все ваши шрифты будут найдены!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}