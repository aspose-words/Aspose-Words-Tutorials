---
category: general
date: 2026-02-24
description: Как обнаружить шрифты в документе Word с помощью Aspose.Words. Узнайте,
  как установить обратный вызов и загрузить документ Word с полным примером кода.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: ru
og_description: Как обнаружить шрифты в документе Word с помощью обратного вызова
  предупреждений. Это руководство показывает, как установить обратный вызов и загрузить
  документ Word с помощью Aspose.Words.
og_title: Как определить шрифты в документах Word – пошаговое руководство на C#
tags:
- C#
- Aspose.Words
- Document Processing
title: Как обнаружить шрифты в документах Word – Полное руководство по C#
url: /ru/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как обнаружить шрифты в документах Word – Полное руководство на C#

Вы когда‑нибудь задумывались **how to detect fonts**, которые отсутствуют при загрузке файла Word? Возможно, вы столкнулись с документом, который выглядит нормально в редакторе, но PDF, который вы генерируете, заменяет несколько шрифтов за кулисами. Это классический симптом подстановки шрифтов, и раннее обнаружение может спасти вас от неприятных сюрпризов вёрстки.

В этом руководстве мы пройдем практическое решение: использование **Aspose.Words** для загрузки `.docx`, присоединения callback‑а предупреждений и **how to set callback**, который сообщает о каждой подстановке шрифта. К концу вы не только будете знать **how to detect fonts** программно, вы также поймёте, как правильно **how to set callback** и безопасно **load word document** — всё в одном, готовом к запуску примере на C#.

> **Что вы получите**
> * Полный готовый к копированию и вставке образец кода  
> * Пошаговое объяснение каждой строки  
> * Советы по обработке граничных случаев, таких как несколько отсутствующих шрифтов или пользовательские папки шрифтов  
> * Ожидаемый вывод в консоль, чтобы вы могли убедиться, что всё работает

---

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Core)  
- NuGet‑пакет Aspose.Words для .NET (`Install-Package Aspose.Words`)  
- Файл Word, который намеренно ссылается на шрифт, которого у вас нет (например, `MissingFont.docx`)  
- Visual Studio, Rider или любой другой редактор по вашему выбору

Никакие другие библиотеки не требуются; всё остальное входит в стандартную среду выполнения .NET.

---

## Как обнаружить шрифты в документе Word

### Шаг 1: Создать Load Options и присоединить Warning Callback

Первое, что мы делаем, — сообщаем Aspose.Words, что хотим получать уведомления о любых проблемах, возникающих при загрузке файла. Здесь в дело вступает **how to set callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Почему это важно:**  
`LoadOptions` — это шлюз к настройке процесса загрузки. Присвоив экземпляр `FontWarningCollector` свойству `WarningCallback`, Aspose.Words будет вызывать наш метод `Warning` каждый раз, когда заменяет отсутствующий шрифт на запасной. Это и есть основа **how to detect fonts**, которые отсутствуют на машине.

### Шаг 2: Подготовить экземпляр LoadOptions

Теперь мы создаём экземпляр `LoadOptions` и привязываем наш callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Полезный совет:** Если вам нужно контролировать, *где* Aspose ищет заменяющие шрифты, вы также можете установить `loadOptions.FontSettings` здесь. Это полезно, когда на сервере есть приватная папка со шрифтами.

### Шаг 3: Загрузить документ Word

С готовыми параметрами мы, наконец, **load word document**. Это момент, когда Aspose разбирает DOCX и, если какие‑то шрифты отсутствуют, наш callback срабатывает.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Что происходит под капотом?**  
Aspose.Words читает XML‑части DOCX, разрешает каждую ссылку `<w:font>` и проверяет коллекцию шрифтов системы. Каждый раз, когда ссылка не может быть удовлетворена, он заменяет её первым подходящим запасным шрифтом и генерирует предупреждение `FontSubstitution`.

### Шаг 4: Проверить вывод

Запустите программу и посмотрите консоль. Для каждого отсутствующего шрифта вы увидите строку вроде:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Если в документе нет отсутствующих шрифтов, консоль остаётся тихой — значит, **how to detect fonts** не нашёл ничего.

### Шаг 5: Полный рабочий пример (консольное приложение)

Ниже представлен автономный `Program.cs`, который вы можете добавить в новый консольный проект. Он включает все обсуждаемые части плюс небольшой помощник, чтобы окно консоли оставалось открытым при отладке.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Ожидаемый вывод в консоль** (пример):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Если заменить `MissingFont.docx` файлом, использующим только установленные шрифты, вы увидите только строку «Press any key…» — это подтверждает, что логика обнаружения работает как задумано.

---

## Часто задаваемые вопросы и граничные случаи

### Что если мне нужно захватывать *все* предупреждения, а не только подстановку шрифтов?

Просто удалите условие `if (info.Type == WarningType.FontSubstitution)`. Объект `WarningInfo` содержит перечисление `Type`, по которому вы можете переключаться для других сценариев (например, `DocumentStructure`, `ImageLoading`).

### Можно ли записывать предупреждения в файл вместо консоли?

Конечно. Замените `Console.WriteLine` на любой вызов из фреймворка логирования (`Serilog`, `NLog` и т.д.). Callback выполняется в том же потоке, который загружает документ, поэтому убедитесь, что ваш логгер потокобезопасен.

### Как это работает в веб‑приложении?

В ASP.NET Core обычно внедряют singleton‑реализацию `IWarningCallback` и передают её через `LoadOptions`. Не пишите напрямую в поток ответа — логируйте в базу данных или в коллекцию в памяти, которую позже можно будет открыть через API‑endpoint.

### Как работать с пользовательскими шрифтами, хранящимися в папке вне системы?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Теперь Aspose.Words будет искать в `C:\MyCustomFonts` прежде чем перейти к системным шрифтам, уменьшая количество предупреждений о подстановке, которые вы видите.

---

## Визуальное резюме

![Обнаружение шрифтов с помощью callback‑а предупреждений в Aspose.Words](/images/font-warning-callback.png "Как обнаружить шрифты с помощью callback‑а предупреждений")

*Скриншот показывает вывод в консоль, когда отсутствующий шрифт заменяется. Alt‑текст содержит основной ключевой запрос для SEO.*

---

## Заключение

Теперь у вас есть надёжный, готовый к продакшену шаблон для **how to detect fonts** в любом файле Word, который вы загружаете с помощью Aspose.Words. Благодаря **how to set callback** вы получаете информацию в реальном времени о недостающих или заменённых шрифтах, и вы изучили правильный способ **load word document**, сохраняя код чистым и поддерживаемым.

Что дальше? Попробуйте расширить callback, собирая предупреждения в список, а затем отображать их в UI или автоматическом отчёте. Вы также можете изучить `FontSettings.SubstitutionSettings`, чтобы управлять *тем, какие* шрифты выбираются в качестве запасных.

Не стесняйтесь экспериментировать — заменяйте документ, добавляйте больше отсутствующих шрифтов или интегрируйте логику в более крупный конвейер обработки документов. Если возникнут проблемы, оставьте комментарий ниже или напишите мне на GitHub.

Удачной разработки, и пусть ваши документы всегда отображаются с ожидаемыми шрифтами!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}