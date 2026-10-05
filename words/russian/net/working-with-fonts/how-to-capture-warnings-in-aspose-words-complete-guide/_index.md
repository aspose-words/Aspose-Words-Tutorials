---
category: general
date: 2026-03-13
description: Как перехватывать предупреждения при загрузке документов с помощью Aspose.Words,
  а также рекомендации по работе с отсутствующими шрифтами и настройке пользовательских
  параметров шрифтов. Узнайте полное решение на C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: ru
og_description: Как перехватывать предупреждения при загрузке файлов Word с помощью
  Aspose.Words, а также практические способы обработки отсутствующих шрифтов и настройки
  пользовательских параметров шрифтов.
og_title: Как захватывать предупреждения в Aspose.Words – Полное руководство
tags:
- Aspose.Words
- C#
- Document Processing
title: Как перехватывать предупреждения в Aspose.Words – полное руководство
url: /ru/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как захватывать предупреждения в Aspose.Words – Полное руководство

Когда‑нибудь задумывались **как захватывать предупреждения**, которые появляются при загрузке документа Aspose.Words? В реальных проектах вы часто сталкиваетесь с уведомлениями о замене шрифтов, заметками об устаревших функциях или даже сообщениями, связанными с безопасностью. Игнорировать их — всё равно что ехать с треснувшим лобовым стеклом: до места вы доберётесь, но никогда не узнаете, когда что‑то сломается.

Хорошая новость в том, что Aspose.Words предоставляет чистый, основанный на обратных вызовах способ перехватывать эти сообщения. В этом руководстве мы пройдём через **полный пример на C#**, который не только захватывает предупреждения, но и показывает, как **обрабатывать отсутствующие шрифты** и **настраивать пользовательские параметры шрифтов**, чтобы ваши документы отображались точно так, как вы ожидаете.

---

## Что вы узнаете

- Как настроить `LoadOptions`, чтобы подключить пользовательский объект `FontSettings`.  
- Как зарегистрировать обратный вызов предупреждений, фильтрующий события `FontSubstitution`.  
- Как выводить детали предупреждений в консоль (или любой другой логгер).  
- Как расширить решение для корректной работы с отсутствующими шрифтами на разных платформах.  

К концу этого руководства у вас будет готовый фрагмент кода, который можно вставить в любой .NET‑проект, а также несколько практических советов по избежанию распространённых подводных камней.

---

## Требования

| Требование | Почему это важно |
|------------|------------------|
| **Aspose.Words for .NET** (v23.12 или новее) | API, которое мы используем (`LoadOptions`, `IWarningCallback`), находится здесь. |
| **.NET 6+** (или .NET Framework 4.7.2+) | Современные возможности языка делают код чище. |
| **Пример DOCX** (с именем `input.docx`) в известной папке | Нужно, чтобы загрузить файл и вызвать предупреждение. |
| **Консоль или фреймворк логирования** (опционально) | Чтобы увидеть захваченные предупреждения в действии. |

Дополнительные пакеты NuGet не требуются, кроме самого Aspose.Words.

---

## Шаг 1: Настройка пользовательских параметров шрифтов  

Прежде чем загружать документ, вы можете указать Aspose.Words, где искать шрифты. Это часть «настройки пользовательских параметров шрифтов».

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Почему это важно:**  
Если DOCX ссылается на шрифт, который не установлен на машине, Aspose.Words тихо заменит его запасным шрифтом *если* вы не указали папку с необходимыми шрифтами. Установив пользовательскую папку, вы уменьшаете вероятность появления предупреждений о «замене шрифтов» сразу же.

> **Pro tip:** На Linux может потребоваться установить пакет `fonts-dejavu-core` или любую коллекцию TrueType, от которой зависят ваши документы.

---

## Шаг 2: Регистрация обратного вызова предупреждений  

Aspose.Words реализует `IWarningCallback`. Мы создадим небольшой обработчик, который выводит только те предупреждения, которые нас интересуют: отсутствующие или заменённые шрифты.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Почему это важно:**  
Сценарий **обработки отсутствующих шрифтов** теперь виден вам. Вместо догадок, какой шрифт был заменён, вы получаете чёткое описание вроде «Font 'Calibri' was substituted with 'Arial'». Это бесценно при отладке проблем с разметкой в генерируемых PDF или печатных отчётах.

---

## Шаг 3: Загрузка документа с настроенными параметрами  

Теперь мы наконец‑то загружаем документ в память, используя подготовленные `LoadOptions`.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Если исходный файл использует шрифт, которого нет в `C:\MyFonts`, вы увидите вывод, похожий на:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Эта строка и есть **результат захвата предупреждений**, который вы искали.

---

## Шаг 4: Полный рабочий пример (готов к копированию)

Ниже представлен весь код программы, готовый к компиляции. Вставьте его в новый консольный проект и запустите — только убедитесь, что пути указывают на реальные места на вашем компьютере.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Ожидаемый вывод:**  

- Если все шрифты доступны:  
  `Document processed. Check console for any warning messages.`  

- Если шрифт отсутствует:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Шаг 5: Распространённые варианты и граничные случаи  

| Ситуация | Что изменить |
|----------|--------------|
| **Несколько папок со шрифтами** | Вызовите `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` для каждой дополнительной локации. |
| **Подавление всех предупреждений** | Реализуйте `Warn`, но оставьте тело пустым, или установите `loadOptions.WarningCallback = null;`. |
| **Захват других типов предупреждений** | Сравнивайте `info.WarningType` с `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent` и т.д. |
| **Запуск на Linux/macOS** | Убедитесь, что папка со шрифтами содержит совместимые с Linux файлы `.ttf`/`.otf`; возможно, понадобится установить `libfontconfig`. |
| **Большие документы** | Рассмотрите возможность потоковой загрузки (`LoadOptions.LoadFormat = LoadFormat.Docx;`), чтобы снизить нагрузку на память. |

Предвидя эти сценарии, вы избежите сюрпризов при переходе с рабочей станции на CI‑конвейер или облачную ВМ.

---

## Шаг 6: Визуальное подтверждение (опционально)

Если вам удобнее видеть быстрый визуальный индикатор, вы можете вывести захваченные предупреждения в небольшой HTML‑отчёт. Вот крошечный фрагмент, который записывает сообщения в `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

После загрузки документа вызовите `handler.WriteReport(@"C:\Docs\warnings.html");` и откройте файл в браузере. На изображении ниже показан пример того, как может выглядеть отчёт:

![Как захватывать предупреждения скриншот](/images/capture-warnings.png)

*Alt text:* **как захватывать предупреждения** – скриншот вывода в консоль и HTML‑отчёта.

---

## Заключение  

Мы рассмотрели **как захватывать предупреждения** в Aspose.Words, продемонстрировали надёжный способ **обработки отсутствующих шрифтов** и показали, как **настраивать пользовательские параметры шрифтов** для детерминированного рендеринга. Полный пример готов к вставке в любой .NET‑проект, а модульный `FontWarningHandler` можно расширять под вашу стратегию логирования или телеметрии.

Что дальше? Попробуйте заменить вызовы `Console.WriteLine` на структурированный логгер, например Serilog, или отправляйте предупреждения в Application Insights для мониторинга в реальном времени. Вы также можете изучить паттерн `DocumentVisitor`, если нужно проанализировать содержимое документа после загрузки.

Есть вопросы о других типах предупреждений или стратегиях встраивания шрифтов? Оставляйте комментарий ниже — happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}