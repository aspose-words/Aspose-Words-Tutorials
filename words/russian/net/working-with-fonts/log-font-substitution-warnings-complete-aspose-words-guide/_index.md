---
category: general
date: 2026-01-14
description: Ведите журнал предупреждений о замене шрифтов при загрузке документов
  Word с помощью Aspose.Words. Узнайте, как обнаруживать отсутствующие шрифты и как
  фиксировать их в C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: ru
og_description: Ведите журнал предупреждений о замене шрифтов при загрузке документов
  Word с помощью Aspose.Words. Узнайте, как обнаруживать отсутствующие шрифты и фиксировать
  их в C#.
og_title: Ведение журнала предупреждений о замене шрифтов – Полное руководство по
  Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Журнал предупреждений о замене шрифтов – Полное руководство по Aspose.Words
url: /ru/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Предупреждения о замене шрифтов в журнале – Полное руководство по Aspose.Words

Запись предупреждений о замене шрифтов необходима, когда нужно гарантировать, что документ Word будет выглядеть точно так же после загрузки Aspose.Words. Если вы когда‑нибудь задавались вопросом, как **обнаружить отсутствующие шрифты**, или хотите знать, **как фиксировать отсутствующие шрифты**, вы попали по адресу.  

В этом руководстве мы пройдём через реальный сценарий, покажем полный код C# и объясним, почему важна каждая строка. К концу вы сможете фиксировать каждое событие замены шрифта и реагировать на него – никаких загадочных предупреждений.

![Пример предупреждений о замене шрифтов](/images/font-warnings.png "Скриншот, показывающий вывод в консоль предупреждений о замене шрифтов")

## Что вы узнаете

- Как настроить `LoadOptions`, чтобы Aspose.Words генерировал типизированные предупреждения о замене шрифтов.  
- Точные шаги для **обнаружения отсутствующих шрифтов** во время загрузки документа.  
- Чистый способ **фиксировать отсутствующие шрифты** и записывать их в собственный журнал или систему мониторинга.  
- Обработку граничных случаев (например, когда документ содержит шрифт, не установленный на сервере).  

### Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+).  
- Действительная лицензия Aspose.Words for .NET (или бесплатная пробная версия).  
- Базовые знания C# и консольных приложений.  

Если всё это у вас есть, приступим.

## Шаг 1 – Настройка LoadOptions для генерации типизированных предупреждений

Суть решения заключается в `LoadOptions.FontSubstitutionWarning`. Переключив его в `RaiseTypedWarnings`, вы заставляете Aspose.Words генерировать событие **каждый раз**, когда не может найти точно запрошенный шрифт.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Почему это важно:**  
> По умолчанию отсутствующий шрифт заменяется на ближайший аналог без уведомления, что может привести к неожиданным сбоям вёрстки. Генерация типизированных предупреждений даёт полную видимость.

## Шаг 2 – Подписка на событие предупреждения

Теперь привязываемся к `loadOptions.FontSubstitutionWarning`. Лямбда‑выражение получает объект `e`, который точно сообщает, какой шрифт отсутствовал и какой был использован вместо него.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Совет:** Если вы запускаете это на веб‑сервере, замените `Console.WriteLine` на структурированный логгер (Serilog, NLog и т.п.), чтобы позже можно было выполнять запросы к данным.

## Шаг 3 – Загрузка документа с использованием настроенных параметров

С включённым механизмом предупреждений просто загрузите документ, как обычно. Событие сработает автоматически для каждого отсутствующего шрифта.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Ожидаемый вывод в консоль

Если `input.docx` ссылается на шрифт *MyFancyFont*, которого нет в системе, вы увидите:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Каждая строка соответствует событию **обнаружения отсутствующего шрифта**, формируя полную аудиторскую запись.

## Шаг 4 – Обработка граничных случаев и продвинутые сценарии

### 4.1 Когда замена не происходит

Иногда документ использует только системные шрифты, уже установленные в системе. В этом случае событие предупреждения не срабатывает, и консоль остаётся пустой. Это хороший знак – все необходимые шрифты уже присутствуют.

### 4.2 Сбор предупреждений для последующего анализа

Если нужно сохранять предупреждения для ночного отчёта, собирайте их в список:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

После загрузки вы можете сериализовать `missingFonts` в JSON, записать в базу данных или отправить сводку по электронной почте.

### 4.3 Работа с PDF и другими форматами

Тот же подход с `LoadOptions` работает и для вызовов `Load` с PDF, RTF и даже HTML‑файлами. Просто передайте тот же экземпляр параметров, и Aspose.Words будет генерировать предупреждения для любого шрифта, который не удалось сопоставить.

## Шаг 5 – Программная проверка результата

Если предпочитаете автоматический тест вместо визуального контроля, проверьте, что список содержит ожидаемые элементы:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Этот фрагмент демонстрирует **как фиксировать отсутствующие шрифты** в коде, а не только в журналах.

## Распространённые ошибки и способы их избежать

| Ошибка | Почему происходит | Как исправить |
|--------|-------------------|---------------|
| Не установлен `RaiseTypedWarnings` | По умолчанию значение `DoNotRaise`, поэтому события не генерируются. | Явно задайте `FontSubstitutionWarning`, как показано в Шаге 1. |
| Использование `Console.WriteLine` в веб‑приложении | Вывод в консоль исчезает в IIS/ASP.NET Core. | Перейдите на постоянный логгер (например, Serilog). |
| Загрузка документа по относительному пути | Рабочая директория может отличаться во время выполнения. | Используйте абсолютные пути или `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Игнорирование `SubstitutedFontName` | Вы теряете информацию о том, какой шрифт был использован в качестве замены. | Всегда фиксируйте и `FontName`, и `SubstitutedFontName`. |

## Плюс: Автоматическая установка шрифтов

Если вы контролируете среду развертывания, можно предварительно установить недостающие шрифты с помощью PowerShell‑скрипта:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Запуск этого скрипта перед стартом приложения устраняет большинство предупреждений **об обнаружении отсутствующих шрифтов**.

## Заключение

Мы рассмотрели всё, что нужно для **записи предупреждений о замене шрифтов** при загрузке документов Word с помощью Aspose.Words. Настроив `LoadOptions`, подписавшись на событие предупреждения и, при необходимости, сохранив результаты, вы сможете надёжно **обнаруживать отсутствующие шрифты** и понимать **как фиксировать отсутствующие шрифты** в любом .NET‑проекте.

Возьмите код, адаптируйте логгер под ваш стек, и больше никогда не будет неожиданной замены шрифтов. Дальнейшие шаги могут включать:

- Интеграцию списка предупреждений в ваш CI/CD‑pipeline для провала сборки при отсутствии критических шрифтов.  
- Расширение подхода для мониторинга использования шрифтов в большом наборе документов.  
- Исследование API `FontSettings` в Aspose.Words для предоставления пользовательских шрифтов‑заменителей.

Есть вопросы или сложный сценарий? Оставьте комментарий, и мы разберёмся вместе. Счастливого кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}