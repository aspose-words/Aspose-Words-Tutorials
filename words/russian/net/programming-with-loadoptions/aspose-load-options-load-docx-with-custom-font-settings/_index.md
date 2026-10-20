---
category: general
date: 2025-12-29
description: Параметры загрузки Aspose позволяют загружать файлы DOCX, настраивая
  параметры шрифтов и обнаруживая отсутствующие шрифты. Узнайте, как загружать DOCX
  с полным контролем.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: ru
og_description: Параметры загрузки Aspose позволяют загружать файлы DOCX, настраивая
  параметры шрифтов и обнаруживая отсутствующие шрифты. Узнайте, как загружать DOCX
  с полным контролем.
og_title: Параметры загрузки Aspose – Загрузка DOCX с пользовательскими настройками
  шрифтов
tags:
- Aspose.Words
- C#
- Document Processing
title: Опции загрузки Aspose – Загрузка DOCX с пользовательскими настройками шрифтов
url: /ru/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Загрузка DOCX с пользовательскими настройками шрифтов

Вы когда‑нибудь задумывались, как загрузить файл DOCX в C# без проблем с отсутствующими шрифтами? Вы не одиноки. **Aspose Load Options** дают вам возможность точно контролировать, как открывается документ Word, позволяя задавать пользовательские настройки шрифтов и даже обнаруживать отсутствующие шрифты до того, как они станут проблемой.

В этом руководстве мы пройдем весь процесс загрузки DOCX с помощью Aspose.Words, настройки **custom font settings**, и подключения обратного вызова предупреждения, который сообщает, какие шрифты отсутствуют. К концу вы сможете **load word document** файлы с уверенностью, независимо от того, какие шрифты использовал оригинальный автор.

> **Prerequisite** – Вам нужен Aspose.Words for .NET (последняя версия), подключенный к вашему проекту, и базовое знакомство с C#. Другие библиотеки не требуются.

## Что вы узнаете

- Как создать объект `LoadOptions` и присоединить обратный вызов предупреждения.  
- Как настроить `FontSettings` для **custom font settings**.  
- Как фактически **load docx** и проверить, что отсутствующие шрифты сообщаются.  
- Советы по обработке edge‑cases, таких как встроенные шрифты или сетевые папки шрифтов.  

## Шаг 1: Установить Aspose.Words и подготовить проект

Для начала убедитесь, что Aspose.Words установлен. Самый простой способ — через NuGet:

```bash
dotnet add package Aspose.Words
```

После добавления пакета создайте новый консольный проект C# (или вставьте код в любое существующее приложение). Пишемый нами код работает с .NET 6+ и .NET Framework 4.7.2+, так что вы покрыты в любом случае.

> **Pro tip:** Если вы нацелены на .NET Core, добавьте `using System;` в начало файла; IDE обычно вставит его автоматически.

## Шаг 2: Настроить Aspose Load Options с обратным вызовом предупреждения

Теперь переходим к сути — **aspose load options**. Класс `LoadOptions` позволяет настроить процесс разбора документа. Мы будем использовать его для:

1. Присоединить обратный вызов, который срабатывает каждый раз, когда загрузчик не может найти запрашиваемый шрифт.  
2. Назначить экземпляр `FontSettings`, который позже можно настроить для **custom font settings**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Почему это важно:** Без обратного вызова предупреждения Aspose тихо заменяет отсутствующие шрифты, что может привести к неожиданным изменениям макета позже. Подключив обратный вызов, вы **detect missing fonts** заранее и можете решить, встраивать ли запасной шрифт или попросить пользователя установить недостающий тип.

## Шаг 3: Загрузить DOCX с использованием настроенных параметров

С готовыми `LoadOptions` загрузка DOCX сводится к одной строке. Конструктор `Document` принимает путь к файлу и параметры, которые мы только что создали.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Если исходный файл ссылается на шрифт, которого нет в системе или в пользовательской папке, вы увидите вывод вроде:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Этот мгновенный отклик бесценен, когда вы создаёте конвейер пакетной обработки, который должен гарантировать визуальную точность.

## Шаг 4: Проверить загруженный документ (необязательно, но полезно)

После загрузки вы можете захотеть убедиться, что содержимое документа доступно. Для быстрой проверки выведем текст первого абзаца.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Запуск программы сейчас выдаст:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Шаг 5: Edge Cases и продвинутые советы

### 5.1 Обработка встроенных шрифтов

Некоторые файлы DOCX встраивают необходимые шрифты напрямую. Aspose.Words автоматически использует их, поэтому вы не увидите предупреждений. Однако, если вы намеренно **load word document** файлы, из которых удалены встроенные шрифты (например, после конвертации), вам может потребоваться предоставить недостающие шрифты через `SetFontsFolder`, как показано выше.

### 5.2 Использование Memory Stream вместо пути к файлу

Если ваш DOCX хранится в базе данных или приходит из HTTP‑запроса, вы можете загрузить его из `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Те же **aspose load options** применяются, и обратный вызов предупреждения по‑прежнему работает.

### 5.3 Глобальное переопределение замены шрифтов

Если вы предпочитаете заменять отсутствующие шрифты конкретным запасным (например, Arial), вы можете добавить правило замены:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Сочетайте это с обратным вызовом предупреждения, чтобы регистрировать событие замены и сохранять консистентность вывода.

## Шаг 6: Полный рабочий пример

Ниже приведена полная, готовая к копированию программа, включающая все шаги выше. Сохраните её как `Program.cs`, восстановите пакеты NuGet и запустите.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Ожидаемый вывод

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Если шрифтов нет, строки предупреждений просто не появятся.

## Визуальный обзор

![aspose load options example](/images/aspose-load-options.png "Diagram showing Aspose Load Options workflow")

*Диаграмма иллюстрирует, как **Aspose Load Options** находятся между источником файла и объектом `Document`, обрабатывая разрешение шрифтов и обнаружение отсутствующих шрифтов.*

## Заключение

Мы прошли полное решение для **aspose load options**, показав вам точно **how to load docx** с применением **custom font settings** и **detect missing fonts**. Настроив обратный вызов предупреждения и при необходимости указав Aspose пользовательскую папку шрифтов, вы получаете полную видимость проблем со шрифтами до того, как они повлияют на рендеринг.  

Отсюда вы можете исследовать связанные темы, такие как конверсия **load word document** в PDF, добавление водяных знаков или пакетная обработка десятков файлов в папке. Та же схема — создать `LoadOptions`, присоединить обратные вызовы и вызвать `new Document(...)` — работает по всему API Aspose.Words.

Есть вопросы о конкретном edge case, например обработка языков справа налево или зашифрованных файлов DOCX? Оставьте комментарий или проверьте документацию Aspose.Words для более глубокого изучения. Приятного кодинга, и пусть ваши документы всегда отображаются точно так, как задумано!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}