---
category: general
date: 2026-04-05
description: Руководство по замене шрифтов Aspose для обнаружения отсутствующих шрифтов
  при загрузке документа Word. Узнайте, как настроить параметры шрифтов и эффективно
  обрабатывать отсутствующие шрифты.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: ru
og_description: Руководство по замене шрифтов Aspose для обнаружения отсутствующих
  шрифтов при загрузке документа Word. Узнайте, как настроить параметры шрифтов и
  эффективно обрабатывать недостающие шрифты.
og_title: Подстановка шрифтов Aspose – Обнаружение отсутствующих шрифтов в документах
  Word
tags:
- Aspose.Words
- C#
- Font Management
title: Подстановка шрифтов Aspose – обнаружение отсутствующих шрифтов в документах
  Word
url: /ru/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Обнаружение отсутствующих шрифтов в документах Word

Случалось ли вам открывать файл Word, который выглядит идеально на одном компьютере, но показывает странные изменения шрифтов на другом? Это классическая проблема **aspose font substitution**, обычно означающая, что некоторые шрифты отсутствуют в целевой системе. В этом руководстве мы покажем вам шаг за шагом, как **обнаружить отсутствующие шрифты** при **загрузке документа Word**, как **настроить параметры шрифтов**, и что делать, чтобы **корректно обрабатывать отсутствующие шрифты**.

Мы пройдем через полный, исполняемый пример на C#, объясним, почему каждая строка важна, и даже покажем ожидаемый вывод в консоль. К концу вы сможете обнаруживать замену шрифтов в момент загрузки документа — без догадок.

## Что вы узнаете

- Как включить диагностический сборщик Aspose.Words для предупреждений о шрифтах.  
- Точный код, необходимый для **загрузки документа Word** с пользовательскими **настройками шрифтов**.  
- Как перебрать объекты `WarningInfo`, чтобы вывести список всех замененных шрифтов.  
- Советы по подавлению нежелательных предупреждений или предоставлению резервных шрифтов.  
- Готовый к запуску пример, который вы можете скопировать и вставить в Visual Studio.

### Требования

- .NET 6.0 или новее (API работает одинаково на .NET Framework).  
- Aspose.Words for .NET (пакет NuGet `Aspose.Words`).  
- Файл Word, который использует шрифт, не установленный у вас (например, `MissingFont.docx`).  

Если у вас есть всё это, давайте приступим.

## Шаг 1 – Включить диагностический сборщик (Настроить параметры шрифтов)

Сначала: Aspose.Words записывает предупреждения о замене шрифтов только если вы его об этом попросите. Это делается путем создания объекта `FontSettings` и назначения его экземпляру `LoadOptions`. Считайте это включением «отладочных индикаторов» для обработки шрифтов.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Почему?**  
Без объекта `FontSettings` сборщик предупреждений будет молчать, и вы никогда не узнаете, какие шрифты были заменены. Инициализируя его пустым, мы позволяем Aspose использовать шрифты системы по умолчанию *и* отслеживать любые замены.

> **Совет:** Если вы знаете, что в определенной папке находятся корпоративные шрифты, укажите её в `FontSettings` с помощью `SetFontsFolder("path")`. Это может уменьшить количество предупреждений об отсутствующих шрифтах.

## Шаг 2 – Загрузить документ с настроенными параметрами (Загрузка документа Word)

Теперь, когда сборщик активен, загрузите ваш файл `.docx`, используя те же `LoadOptions`. Это момент, когда Aspose сканирует документ, ищет каждое упоминание шрифта и решает, нужна ли замена.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Почему это важно?**  
Если вы просто вызовете `new Document("MissingFont.docx")`, применятся настройки по умолчанию *и* список предупреждений останется пустым. Передача `loadOptions` гарантирует, что диагностический сборщик будет подключен к процессу загрузки.

## Шаг 3 – Получить и отобразить предупреждения о замене шрифтов (Обнаружить отсутствующие шрифты)

После того как документ загружен в память, Aspose сохраняет любые предупреждения в `document.WarningCallback.Warnings`. Пройдитесь по этой коллекции, отфильтруйте элементы `WarningType.FontSubstitution` и выведите описание. Каждое описание сообщает, какой шрифт был отсутствующим и какой использован вместо него.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Ожидаемый вывод в консоль**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Этот вывод точно показывает, какие шрифты отсутствуют на машине, где выполняется код. Теперь вы можете решить, установить ли отсутствующие шрифты, внедрить их в документ или оставить замену.

![Вывод консоли, показывающий предупреждения о замене шрифтов Aspose](/images/aspose-font-substitution-console.png)

*Текст альтернативного изображения:* aspose font substitution – вывод консоли со списком замененных шрифтов

## Шаг 4 – Необязательно: Настроить поведение замены (Обработка отсутствующих шрифтов)

Иногда вам нужно не только знать, *что* произошла замена, но и контролировать, *как* она происходит. Aspose.Words позволяет зарегистрировать пользовательское `IFontSubstitutionRule`. Ниже быстрый пример, который заставляет любой отсутствующий шрифт использовать `Tahoma` в качестве резервного.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Когда это может понадобиться?**  
Если вы генерируете PDF для веб‑сервиса и знаете, что каждый клиент может отобразить `Tahoma`, принудительное использование резервного шрифта гарантирует визуальную согласованность без необходимости распространять десятки файлов шрифтов.

## Полный рабочий пример (Все шаги вместе)

Вот полный код программы, который вы можете вставить в новый консольный проект. Он компилируется без изменений, при условии, что вы установили пакет NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Запустите программу, наблюдайте за консолью, и вы увидите вывод каждого события отсутствующего шрифта. После этого вы сможете решить, установить ли отсутствующие шрифты, внедрить их или оставить резервный.

## Часто задаваемые вопросы

**В: Работает ли это при конвертации в PDF?**  
Да. Когда вы позже вызываете `doc.Save("output.pdf")`, любые шрифты, заменённые во время загрузки, будут встроены в PDF. Поэтому раннее обнаружение предупреждений помогает избежать неожиданных изменений шрифтов в конечном PDF.

**В: Что делать, если нужно обработать много документов?**  
Оберните логику загрузки в блок try‑catch и переиспользуйте один экземпляр `FontSettings` для всех документов. Это уменьшает накладные расходы и сохраняет активным сборщик предупреждений для каждого файла.

**В: Можно ли полностью подавлять предупреждения?**  
Вы можете установить `loadOptions.WarningCallback = null;` перед загрузкой, но тогда потеряете возможность **обнаруживать отсутствующие шрифты** — что обычно не желаемо.

## Заключение

Мы рассмотрели всё, что нужно знать, чтобы освоить **aspose font substitution**: включение диагностического сборщика, загрузка файла Word с пользовательскими **настройками шрифтов**, извлечение списка отсутствующих шрифтов и даже переопределение правила замены по‑умолчанию, чтобы **обрабатывать отсутствующие шрифты** по‑своему. Всего несколькими строками C# вы получаете полную видимость проблем со шрифтами, которые иначе скрывались бы за тонкими изменениями макета.

Следующие шаги? Попробуйте внедрить оригинальные шрифты в документ с помощью `FontSettings.SetFontsFolder` или изучить `FontSourceBase` для загрузки шрифтов из базы данных. Вы также можете поэкспериментировать с коллекцией `Document.BuiltInStyle`, чтобы увидеть, как изменения шрифтов на уровне стилей распространяются.

Есть дополнительные вопросы по Aspose.Words или управлению шрифтами? Оставьте комментарий, изучите официальную документацию Aspose или создайте новый проект и поиграйте с приведённым выше кодом. Приятного кодинга, и пусть ваши документы всегда отображаются точно так, как задумано!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}