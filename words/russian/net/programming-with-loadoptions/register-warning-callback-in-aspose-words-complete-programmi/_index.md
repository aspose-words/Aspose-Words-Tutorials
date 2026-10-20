---
category: general
date: 2026-06-27
description: Зарегистрируйте обратный вызов предупреждений в Aspose.Words, чтобы отлавливать
  замену шрифтов и проблемы загрузки. Изучите пошаговое использование LoadOptions
  с Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: ru
og_description: Зарегистрируйте обратный вызов предупреждений в Aspose.Words, чтобы
  отслеживать замену шрифтов и другие предупреждения при загрузке. Следуйте этому
  полному руководству для надёжной реализации.
og_title: Регистрация обратного вызова предупреждений в Aspose.Words – Полное руководство
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Регистрация обработчика предупреждений в Aspose.Words – Полное руководство
  по программированию
url: /ru/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Регистрация обратного вызова предупреждений в Aspose.Words – Полное руководство по программированию

Когда‑то задумывались, как **зарегистрировать обратный вызов предупреждений в Aspose.Words**, чтобы точно видеть, какие шрифты заменяются при загрузке документа? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда тихая замена шрифтов портит разметку сгенерированного PDF или Word‑файла.  

В этом руководстве мы пошагово рассмотрим решение, которое не только регистрирует обратный вызов предупреждений в Aspose.Words, но и объясняет *почему* это стоит делать, как работает обратный вызов изнутри и с какими краевыми случаями вы можете столкнуться. К концу вы сможете логировать каждую замену шрифта, перехватывать другие предупреждения загрузки и делать ваш конвейер обработки документов прозрачным.

## Что вы узнаете

- Настройку **LoadOptions** для управления поведением загрузки документа.  
- Регистрацию **обратного вызова предупреждений**, срабатывающего при замене шрифтов и других типах предупреждений.  
- Загрузку DOCX с сконфигурированными параметрами и интерпретацию вывода обратного вызова.  
- Распространённые подводные камни (отсутствующие шрифты, пользовательские папки шрифтов и соображения производительности).  

**Предварительные требования:** Visual Studio 2022 (или любой IDE для C#), runtime .NET 6+, активная лицензия Aspose.Words (бесплатная пробная версия подходит для экспериментов). Дополнительные пакеты NuGet, кроме `Aspose.Words`, не требуются.

---

![Диаграмма, иллюстрирующая процесс регистрации обратного вызова предупреждений в Aspose.Words и обработку предупреждений о замене шрифтов](register-warning-callback-aspose-words.png "диаграмма регистрации обратного вызова предупреждений aspose.words")

## Шаг 1: Создание LoadOptions – точка входа для обработки предупреждений  

Прежде чем обратный вызов сможет сработать, вам нужен экземпляр **LoadOptions**. Считайте его панелью управления, которую вы передаёте Aspose.Words, говоря: «загрузи этот файл, но сообщи, если что‑то выглядит странно».  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Почему это важно:** `LoadOptions` позволяет настроить всё — от паролей шифрования до каталогов шрифтов. Присоединив к этому объекту обратный вызов предупреждений, вы превращаете тихий процесс в наблюдаемый.

## Шаг 2: Регистрация обратного вызова предупреждений – захват замен шрифтов  

Теперь к главному элементу: **обратному вызову предупреждений**. Мы зарегистрируем анонимный метод (lambda), который Aspose.Words будет вызывать для каждого предупреждения загрузки. Внутри обратного вызова отфильтруем `WarningType.FontSubstitution` и выведем дружелюбное сообщение.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Совет профессионала:** Если хотите также логировать отсутствующие изображения или неподдерживаемые функции, добавьте дополнительные ветви `if`, проверяющие `args.WarningType`. Так ваша **регистрация обратного вызова предупреждений в Aspose.Words** станет универсальным решением для всех диагностик загрузки.

## Шаг 3: Загрузка документа с использованием сконфигурированных LoadOptions  

После того как обратный вызов подключён, следующий шаг — просто загрузить документ. Передайте экземпляр `loadOptions` в конструктор `Document`. Каждый раз, когда Aspose.Words не найдёт шрифт, ваш обратный вызов сработает и запишет сообщение в консоль.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Запустите программу, и вы увидите вывод, похожий на:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Это и есть ядро **регистрации обратного вызова предупреждений aspose.words** — трёхшаговый шаблон, который можно переиспользовать в любом проекте.

## Шаг 4: Расширение обратного вызова для реальных сценариев  

### 4.1 Логирование в файл вместо консоли  

В продакшене обычно не нужен спам в консоли. Замените `Console.WriteLine` на логгер (например, `Serilog`, `NLog`) или запишите в текстовый файл:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Указание пользовательского каталога шрифтов  

Если в вашей среде используются корпоративные шрифты, сообщите Aspose.Words, где их искать, прежде чем он перейдёт к замене:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Теперь обратный вызов будет срабатывать *реже*, потому что движок найдёт нужные шрифты.

### 4.3 Обработка предупреждений, не связанных со шрифтами  

Можно расширить область захвата, чтобы фиксировать любые предупреждения загрузки:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Шаг 5: Тестирование реализации – чего ожидать  

### 5.1 Проверка на документе с отсутствующими шрифтами  

Создайте небольшой DOCX, в котором используется шрифт, не установленный на вашей машине (например, “Comic Sans MS” на Linux‑сервере). Запустите загрузчик; вы должны увидеть сообщение о замене.  

### 5.2 Оценка накладных расходов  

Обратный вызов добавляет незначительные накладные расходы — порядка нескольких микросекунд на каждое предупреждение. Если вы загружаете тысячи документов, можно группировать записи в журнал или отключать обратный вызов для некритичных запусков.

### 5.3 Краевые случаи  

- **Несколько замен одного и того же шрифта:** Aspose.Words может вызвать обратный вызов несколько раз, если один и тот же отсутствующий шрифт встречается на разных страницах. При необходимости выполните дедупликацию в журнале.  
- **Зашифрованные документы:** Если DOCX защищён паролем, также задайте `loadOptions.Password`. Обратный вызов всё равно сработает после расшифровки.  
- **Асинхронная загрузка:** API синхронный, но вы можете обернуть вызов загрузки в `Task.Run` для фоновой обработки; обратный вызов остаётся потокобезопасным.

## Распространённые подводные камни и способы их избежать  

| Подводный камень | Почему происходит | Как исправить |
|------------------|-------------------|---------------|
| **Отсутствие вывода вообще** | Обратный вызов не назначен *или* `WarningCallback` переопределён позже. | Убедитесь, что вы назначаете обратный вызов **один раз** до загрузки и не переassign `loadOptions` после назначения. |
| **Исключение неверного приведения типа** | Попытка привести предупреждение, которое не является `FontSubstitutionWarningInfo`. | Всегда проверяйте `args.WarningType` перед приведением. |
| **Замедление производительности** | Синхронное логирование в медленную I/O цель. | Используйте асинхронные фреймворки логирования или буферизуйте записи. |
| **Отсутствие пользовательских шрифтов** | Папка шрифтов не добавлена в `FontSettings`. | Добавьте `SetFontsFolder`, как показано в Шаге 4.2. |

## Полный рабочий пример – скопировать‑и‑вставить  

Ниже представлена автономная программа, которую можно скопировать в новый проект консольного приложения. Она демонстрирует весь процесс от начала до конца.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Ожидаемый вывод в консоль** (при отсутствии шрифтов):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Запустите программу, и вы точно увидите, какие шрифты заменил Aspose.Words, получив полную видимость процесса загрузки.

---

## Заключение  

Мы только что рассмотрели **как зарегистрировать обратный вызов предупреждений в Aspose.Words**, почему это лучшая практика для любого рабочего процесса обработки документов и как расширить шаблон для логирования, пользовательских шрифтов и более широкого охвата предупреждений. Всего тремя строками кода вы превращаете черный ящик загрузки в аудируемый, отлаживаемый шаг — больше никаких загадочных изменений разметки.

Что дальше? Попробуйте сочетать этот обратный вызов с **Aspose.Words SaveOptions**, чтобы логировать предупреждения как при загрузке, так и при сохранении, или подключите обратный вызов к веб‑API, обрабатывающему загрузки в реальном времени. Вы также можете исследовать другие вспомогательные ключевые слова, которые мы упомянули — такие как *loadoptions font substitution warning* — для тонкой настройки производительности или интеграции с панелью мониторинга.

Есть вопросы или сложный сценарий? Оставьте комментарий, и мы разберёмся вместе. Приятного кодинга, и пусть ваши PDF‑файлы всегда отображаются с правильными шрифтами!

## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом гиде. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}