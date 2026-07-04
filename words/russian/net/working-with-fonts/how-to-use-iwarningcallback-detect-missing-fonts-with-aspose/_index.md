---
category: general
date: 2026-06-24
description: Как использовать IWarningCallback для обнаружения отсутствующих шрифтов
  в документах Aspose.Words. Узнайте полный, исполняемый пример и лучшие практики.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: ru
og_description: Как использовать IWarningCallback для обнаружения отсутствующих шрифтов
  в Aspose.Words. Следуйте пошаговому руководству для получения полного, готового
  к использованию в продакшене решения.
og_title: Как использовать IWarningCallback – обнаружение отсутствующих шрифтов
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Как использовать IWarningCallback – обнаружение отсутствующих шрифтов с Aspose.Words
url: /ru/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как использовать IWarningCallback – Обнаружение отсутствующих шрифтов с помощью Aspose.Words

Использование **IWarningCallback** необходимо, когда вы работаете с Aspose.Words и нужно **обнаружить отсутствующие шрифты** в файле DOCX. В этом руководстве мы пройдем полный пример, который можно скопировать и вставить, показывающий, как использовать IWarningCallback для перехвата предупреждений о замене шрифтов, почему это важно и что делать после их получения.

Если вы когда‑либо открывали документ и видели искажённый текст из‑за того, что пользовательский шрифт не был установлен, вы знаете, насколько это раздражает. К концу этого урока у вас будет надёжный способ программно выявлять такие проблемы, регистрировать их или даже автоматически применять резервный шрифт.

## Что вы узнаете

- Назначение **IWarningCallback** и когда его использовать.  
- Как реализовать пользовательский сборщик предупреждений, который изолирует **detect missing fonts** события.  
- Подключение сборщика к **LoadOptions**, чтобы каждый загрузка документа отслеживалась.  
- Проверка вывода и обработка граничных случаев (несколько отсутствующих шрифтов, тихие предупреждения и т.д.).  

### Предварительные требования

- .NET 6.0 или новее (код также работает на .NET Framework 4.6+).  
- Aspose.Words for .NET, установленный через NuGet (`Install-Package Aspose.Words`).  
- Файл DOCX, который ссылается на шрифт, отсутствующий на машине (например, `DocumentWithMissingFont.docx`).  

Дополнительные библиотеки не требуются — всё находится внутри Aspose.Words.

---

## Как использовать IWarningCallback для обнаружения отсутствующих шрифтов в Aspose.Words

Ниже представлен **полный, исполняемый пример**. Скопируйте его в новый консольный проект, скорректируйте путь к файлу и запустите. Вы увидите вывод в консоль для каждого предупреждения об отсутствующем шрифте.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Ожидаемый вывод

Если `DocumentWithMissingFont.docx` ссылается на шрифт под названием *“MyFancyFont”*, который не установлен, вы увидите что‑то вроде:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Каждая строка, начинающаяся с **[Missing Font]**, генерируется нашей реализацией **IWarningCallback**, подтверждая, что мы успешно **detect missing fonts**.

---

## Шаг 1: Реализовать интерфейс IWarningCallback

Зачем нужен пользовательский класс? Aspose.Words генерирует **warnings** по разным причинам — проблемы с форматом файла, устаревшие возможности и, что самое важное для нас, замена шрифтов. Реализуя `IWarningCallback`, мы получаем точку входа, которая получает каждое предупреждение в момент его возникновения. Фильтрация по `WarningType.FontSubstitution` изолирует конкретный сценарий, когда шрифт отсутствует.

**Совет:** Если вам нужно захватывать *все* предупреждения для диагностики, просто удалите проверку `if` и регистрируйте каждый `info.Type`.

## Шаг 2: Подключить обратный вызов к LoadOptions

`LoadOptions` — это шлюз, который указывает Aspose.Words, как обрабатывать входящий документ. Установка `WarningCallback` в экземпляр нашего сборщика гарантирует, что обратный вызов будет активен на протяжении всей операции загрузки. Вы можете переиспользовать один объект `LoadOptions` для нескольких документов, что удобно в пакетных конвейерах обработки.

**Распространённый вопрос:** *Что если я загружаю документ без указания LoadOptions?*  
Ответ: Aspose.Words всё равно будет генерировать предупреждения внутри, но без обратного вызова они будут тихо отбрасываться, и вы потеряете возможность **detect missing fonts**.

## Шаг 3: Загрузить документ и захватить предупреждения об отсутствующих шрифтах

Конструктор `Document`, принимающий путь к файлу и `LoadOptions`, выполняет основную работу. При разборе файла любое отсутствие шрифта вызывает наш метод `FontWarningCollector.Warning`. Вывод в консоль подтверждает, что механизм работает.

**Граничный случай:** Один документ может ссылаться на несколько отсутствующих шрифтов. Обратный вызов срабатывает один раз для каждого отсутствующего шрифта, поэтому вы увидите несколько строк — идеально для построения полного отчёта.

## Почему использовать IWarningCallback вместо ручных проверок шрифтов?

Вы могли бы вручную просканировать свойства `Run.Font` документа после загрузки, но для этого документ должен успешно загрузиться — что не происходит, если шрифт полностью недоступен. Система предупреждений работает **до** любой замены, предоставляя реальное представление о том, чего не хватает.

Кроме того, обратный вызов выполняется **в рамках конвейера загрузки**, что позволяет прервать процесс раннее, заменять шрифты «на лету» или вести подробную диагностику без дополнительных проходов по дереву документа.

## Обработка нескольких отсутствующих шрифтов корректно

Если вы ожидаете множество отсутствующих шрифтов, рассмотрите возможность их агрегации в коллекцию:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

После загрузки вы можете пройтись по `MissingFonts` и, например, записать их в CSV‑файл для команды дизайнеров.

## Бонус: Запись предупреждений в файл

Вывод в консоль подходит для демонстраций, но в продакшн‑коде обычно используют запись в постоянное хранилище. Замените вызов `Console.WriteLine` на что‑то вроде:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Теперь у вас есть журнал аудита, который можно просмотреть позже, удовлетворяя требования соответствия.

---

## Заключение

Мы рассмотрели **как использовать IWarningCallback** для **detect missing fonts** в Aspose.Words, от реализации обратного вызова до подключения его к `LoadOptions` и обработки полученных предупреждений. Этот подход предоставляет вам информацию в реальном времени о проблемах, связанных со шрифтами, позволяя регистрировать их, заменять или оповещать пользователей до рендеринга документа.

Следующие шаги, которые вы можете изучить:

- **Fallback fonts:** программно назначать шрифт по умолчанию, когда происходит замена.  
- **Batch processing:** проходить по папке с документами, переиспользуя один `AggregatingFontCollector`.  
- **User feedback:** выводить предупреждения об отсутствующих шрифтах в пользовательском интерфейсе, а не в консоли.

Попробуйте в своём проекте — больше никаких загадочных искажённых текстов, только чёткая, практичная диагностика. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как загрузить DOCX и обнаружить отсутствующие шрифты – Полное руководство C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Как обнаружить шрифты в Aspose.Words – Обработка предупреждений и настроек](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Как использовать LoadOptions в Aspose.Words – Полное руководство](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}