---
category: general
date: 2026-03-16
description: Узнайте, как использовать FontSettings в Aspose.Words для корректной
  обработки отсутствующих шрифтов — полный код, обработка событий и рекомендации по
  лучшим практикам.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: ru
og_description: Как использовать FontSettings в Aspose.Words для обработки отсутствующих
  шрифтов — пошаговое руководство с полным примером на C# и практическими советами.
og_title: Как использовать FontSettings для обработки отсутствующих шрифтов в Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: Как использовать FontSettings для обработки отсутствующих шрифтов в Aspose.Words
url: /ru/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

points, table content, etc.

We must keep code block placeholders unchanged.

Also keep the block shortcodes at start and end.

Let's produce.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как использовать FontSettings для обработки отсутствующих шрифтов в Aspose.Words

Когда‑то задумывались **как использовать FontSettings**, если ваши Word‑документы ссылаются на шрифты, которые не установлены на сервере? Вы не одиноки. Отсутствующие шрифты могут приводить к некрасивым заменам или даже вызывать исключения, и большинство разработчиков просто игнорируют проблему, пока она не проявится в продакшене.  

В этом руководстве мы покажем, **как использовать FontSettings** для **обработки отсутствующих шрифтов** в Aspose.Words, как захватывать подробные предупреждения и делать рендеринг документов предсказуемым. К концу вы получите готовый к запуску пример на C#, поймёте, почему каждая строка важна, и узнаете, как адаптировать решение для крупных проектов.

## Что покрывает это руководство

- Настройка **FontSettings** и подписка на событие `SubstitutionWarning`.  
- Привязка настроек к `LoadOptions`, чтобы они учитывались при загрузке документа.  
- Запуск тестового документа, в котором намеренно отсутствуют шрифты, и чтение вывода в консоль.  
- Советы по логированию, отключению автоматической подстановки и обработке крайних случаев, таких как несколько отсутствующих шрифтов.  

Никакой внешней документации не требуется — всё, что нужно, находится здесь.

## Предварительные требования

- .NET 6+ (или .NET Framework 4.6.2+).  
- Aspose.Words for .NET 23.9 или новее (используемый API стабилен во всех последних версиях).  
- Простой файл `.docx`, который ссылается на шрифт, который вы знаете, что не установлен (например, *Comic Sans MS* в Linux‑контейнере).  

И всё — никаких дополнительных пакетов NuGet, кроме Aspose.Words.

## Почему важно обрабатывать отсутствующие шрифты

Когда документ ссылается на шрифт, который среда выполнения не может найти, Aspose.Words автоматически подставляет ближайший аналог. Такая подстановка часто приемлема, но иногда необходимо **записать в журнал**, какие шрифты отсутствовали (для соответствия требованиям), или **полностью запретить** подстановку (например, для брендированных PDF). Подключившись к `FontSettings.SubstitutionWarning`, вы получаете полную видимость и контроль.

## Шаг 1: Создать FontSettings и подписаться на событие Substitution‑Warning

Первое, что нужно сделать, — создать экземпляр `FontSettings`. Этот объект хранит всю конфигурацию, связанную со шрифтами, для библиотеки. Ключевая часть — привязать обработчик к событию `SubstitutionWarning`, которое срабатывает **каждый раз**, когда Aspose.Words не может найти запрошенный шрифт.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Почему это важно:**  
- **Видимость:** Вы сразу узнаёте, какие шрифты отсутствуют.  
- **Аудит:** Вывод в консоль (или в логгер) можно перенаправить в файл для отчётности.  
- **Контроль:** Позже вы сможете заменить подстановку своим собственным шрифтом.

> **Pro tip:** Если вы предпочитаете использовать фреймворк логирования (Serilog, NLog и т.п.), замените вызовы `Console.WriteLine` на `logger.Information(...)`.

## Шаг 2: Привязать FontSettings к LoadOptions

`LoadOptions` — это объект, который сообщает Aspose.Words, как обрабатывать файл во время загрузки. Присвоив ему объект `FontSettings`, вы гарантируете, что обработчик предупреждений активен *до* начала парсинга содержимого.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Почему это важно:**  
- Если загрузить документ без передачи `LoadOptions`, будет использована обработка шрифтов по умолчанию, и вы пропустите предупреждения.  
- Такой подход также позволяет настроить другие параметры загрузки (например, защиту паролем) в том же объекте.

## Шаг 3: Загрузить документ с настроенными параметрами

Теперь мы действительно читаем Word‑файл. Путь может быть абсолютным или относительным; Aspose.Words учтёт `LoadOptions`, которые мы только что подготовили.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Если в документе присутствует шрифт, который не установлен, событие `SubstitutionWarning` сработает, и вы увидите вывод, похожий на пример ниже.

### Ожидаемый вывод в консоль

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Точная подстановка может различаться в зависимости от цепочки резервных шрифтов операционной системы, но **имя отсутствующего шрифта** будет всегда указано.

## Шаг 4: Проверить результат (необязательно рендеринг)

Часто хочется убедиться, что документ выглядит приемлемо после подстановки. Быстрый способ — сохранить его как PDF и открыть полученный файл.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Если необходимо **полностью запретить** подстановку, установите `FontSettings.SubstitutionSettings.TableSubstitution = false` перед загрузкой. Тогда Aspose.Words бросит исключение при отсутствии шрифтов, которое вы сможете перехватить и обработать.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Полный рабочий пример

Ниже представлен полностью готовый к запуску код. Вставьте его в консольное приложение, поправьте путь к файлу и нажмите **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Что ожидать

- Консоль выводит каждое отсутствующее имя шрифта вместе с выбранной подстановкой.  
- Полученный PDF (если вы оставили необязательное сохранение) отображает документ с резервным шрифтом, сохраняя целостность макета.

## Часто задаваемые вопросы и крайние случаи

| Вопрос | Ответ |
|----------|--------|
| **Что делать, если отсутствует несколько шрифтов?** | Событие срабатывает один раз для каждого отсутствующего шрифта, поэтому вы получите отдельную строку журнала для каждого. |
| **Можно ли заменить резервный шрифт своим?** | Да. Внутри обработчика события вы можете вызвать `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **Выдаётся ли предупреждение для встроенных шрифтов, которые не удалось загрузить?** | Да — независимо от того, внешний шрифт или встроенный, механизм предупреждения одинаков. |
| **Нужно ли освобождать `Document`?** | `Document` реализует `IDisposable`. Оберните его в `using`, если загружаете много файлов в цикле. |
| **Будет ли работать в Linux‑контейнерах?** | При условии, что Aspose.Words может находить системные шрифты (например, через `fontconfig`), механизм событий работает одинаково. |

## Лучшие практики и профессиональные советы

- **Централизуйте логирование:** Создайте вспомогательный метод, который пишет одновременно в консоль и в постоянный файл журнала.  
- **Пакетная обработка:** При конвертации десятков документов переиспользуйте один экземпляр `FontSettings`, чтобы избежать повторных подписок на события.  
- **Производительность:** Предупреждения о подстановке добавляют незначительные накладные расходы, но при обработке тысяч файлов можно отключать их после проверки набора шрифтов.  
- **Безопасность версии:** API `SubstitutionWarning` стабилен, начиная с Aspose.Words 16.0, поэтому на него можно рассчитывать в будущих обновлениях.

## Заключение

Мы прошли путь от **использования FontSettings** в Aspose.Words до **элегантной обработки отсутствующих шрифтов**. Создав объект `FontSettings`, подписавшись на `SubstitutionWarning` и загрузив документы через `LoadOptions`, вы получаете полную видимость проблем со шрифтами и можете решить, логировать, заменять или прекращать работу при их отсутствии.  

От простого вывода в консоль до пользовательской логики подстановки — этот шаблон масштабируется до больших конвейеров обработки документов, гарантируя согласованность и проверяемость результатов.

**Следующие шаги:**  

- Исследуйте **кастомную подстановку шрифтов**, присваивая `e.SubstitutedFont` внутри обработчика.  
- Сочетайте этот подход с **рендерингом документов в изображения** для генерации миниатюр.  
- Обратите внимание на **Aspose.PDF**, если нужно встроить подставленные шрифты непосредственно в финальный PDF для полной портативности.

Счастливого кодинга, и пусть ваши документы больше никогда не страдают от непокорных отсутствующих шрифтов!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}