---
category: general
date: 2026-02-18
description: Узнайте, как перехватывать предупреждения о шрифтах и обнаруживать отсутствующие
  шрифты в C# с помощью Aspose.Words. Следуйте этому пошаговому руководству, чтобы
  эффективно обрабатывать недостающие шрифты.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: ru
og_description: Перехватывайте предупреждения о шрифтах в C# и научитесь обнаруживать
  отсутствующие шрифты, обрабатывать их и выводить список недостающих шрифтов с полным
  примером кода.
og_title: Перехват предупреждений шрифтов в C# – Полное руководство
tags:
- Aspose.Words
- C#
- Font Management
title: Перехват предупреждений шрифтов в C# – Полное руководство по программированию
url: /ru/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Захват предупреждений о шрифтах в C# – Полное руководство по программированию

Когда‑то задумывались, как **захватывать предупреждения о шрифтах**, если документ ссылается на шрифт, который не установлен на сервере? Вы не одиноки. Во многих корпоративных приложениях отсутствие шрифтов приводит к искажениям макета, и единственный надёжный способ их обнаружить — слушать предупреждения, которые генерирует библиотека.  

В этом руководстве мы покажем готовое решение, которое не только **захватывает предупреждения о шрифтах**, но и **обнаруживает отсутствующие шрифты**, **обрабатывает их**, а также **выводит список отсутствующих шрифтов**, чтобы вы могли решить, заменять, встраивать их или оповещать пользователя. Никакой внешней документации не требуется — просто скопируйте, вставьте и запустите.

## Что вы узнаете

- Как настроить `LoadOptions` для включения предупреждений о замене шрифтов.  
- Точный код, необходимый для загрузки DOCX и получения всех предупреждений.  
- Почему каждый шаг важен, включая соображения производительности.  
- Обработку граничных случаев, таких как документы со смешанными скриптами или пользовательскими папками шрифтов.  

**Предварительные требования**: .NET 6+ (или .NET Framework 4.6+), ссылка на пакет **Aspose.Words** из NuGet и базовые знания C#. Если вы никогда не работали с Aspose.Words, не переживайте — это руководство проведёт вас через все нюансы.

![Diagram showing capture font warnings flow](image.png){alt="диаграмма захвата предупреждений о шрифтах"}

## Захват предупреждений о шрифтах — зачем это нужно

Когда Aspose.Words загружает документ, он тихо заменяет любой недоступный шрифт запасным. Эта замена сохраняет процесс загрузки, но визуальный результат может быть полностью смещён. Включив флаг **SubstitutionWarningLevel.All**, библиотека добавит запись `WarningInfo` для каждого отсутствующего шрифта, позволяя **обнаружить отсутствующие шрифты** до того, как документ будет отрисован или сохранён.

> **Pro tip:** Если вы обрабатываете сотни файлов в пакетной задаче, запись этих предупреждений в центральное хранилище может сэкономить часы ручного QA позже.

## Шаг 1: Настройка проекта

1. Откройте любимую IDE (Visual Studio, Rider, VS Code).  
2. Создайте новый консольный проект:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Добавьте пакет Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Вот и всё — никаких дополнительных DLL, никакого COM‑interop. Библиотека поставляется со всем, что нужно для **обработки отсутствующих шрифтов**.

## Шаг 2: Подготовьте LoadOptions для захвата всех предупреждений о замене шрифтов

Чтобы движок **захватывал предупреждения о шрифтах**, необходимо указать ему записывать каждую замену. Ниже приведён фрагмент, создающий экземпляр `LoadOptions`, включающий уровень предупреждений и (опционально) указывающий папку с пользовательскими шрифтами, которые вы хотите использовать.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Почему это важно:**  
- `SubstitutionWarningLevel.All` гарантирует, что **каждое** событие отсутствующего шрифта будет зафиксировано, а не только первое.  
- Без этого флага Aspose.Words тихо заменит шрифт, и вы никогда не узнаете о проблеме.

## Шаг 3: Загрузите документ с использованием настроенных параметров

Теперь откроем файл. Замените `DocumentWithMissingFonts.docx` на путь к вашему тестовому документу.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Если в файле есть ссылки на шрифты, которых нет на машине (или в указанной папке), коллекция `document.WarningInfoCollection` будет заполнена.

## Шаг 4: Найдите и отобразите любые предупреждения о замене шрифтов

Это сердце руководства: перебор `WarningInfoCollection` для **вывода списка отсутствующих шрифтов**. Мы отфильтруем по `WarningType.FontSubstitution` и выведем дружелюбное сообщение.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Ожидаемый вывод

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Если документ использует только установленные шрифты, вы увидите строку «✅ No missing fonts detected».

## Шаг 5: Продвинутое — как **обрабатывать отсутствующие шрифты** программно

Простое вывод списка может быть достаточным для диагностического инструмента, но многие производственные системы требуют **автоматической обработки отсутствующих шрифтов**. Ниже два распространённых подхода:

### 5.1 Замена известным запасным шрифтом

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Встраивание пользовательского шрифта «на лету»

Если у вас есть корпоративный файл шрифта (`MyBrand.ttf`), его можно встроить, когда обнаружен отсутствующий шрифт:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Note:** Встраивание шрифтов может увеличить размер выходного файла, поэтому взвесьте компромисс между точностью отображения и объёмом трафика.

## Распространённые подводные камни и как их избежать

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Предупреждения не появляются, хотя документ выглядит некорректно | `SubstitutionWarningLevel` не установлен в `All` | Убедитесь, что на шаге 2 установлен флаг точно как показано |
| В списке предупреждений один и тот же шрифт повторяется | Шрифт используется в нескольких стилях | Удаляйте дубликаты, если нужен уникальный список: `fontWarnings.Select(w => w.Description).Distinct()` |
| Приложение падает при работе с большими DOCX | Загрузка с настройками памяти по умолчанию | Используйте `LoadOptions.LoadFormat` или потоковую загрузку, чтобы снизить нагрузку на память |

## Полный рабочий пример (готов к копированию)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Запустите программу командой `dotnet run`. Вы должны увидеть список отсутствующих шрифтов, выведенный в консоль, что подтвердит успешный **захват предупреждений о шрифтах**.

## Заключение

Теперь у вас есть полноценный, готовый к производству шаблон для **захвата предупреждений о шрифтах**, **обнаружения отсутствующих шрифтов**, **обработки их** и **вывода списка** с помощью Aspose.Words в C#. Подход лёгкий, требует всего несколько строк кода и может быть внедрён в любой существующий конвейер — будь то

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}