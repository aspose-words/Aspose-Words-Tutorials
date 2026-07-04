---
category: general
date: 2026-06-17
description: Обрабатывайте замену шрифтов в Aspose.Words и быстро обнаруживайте отсутствующие
  шрифты с помощью этого пошагового руководства для разработчиков .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: ru
og_description: Обрабатывайте замену шрифтов в Aspose.Words и узнайте, как обнаруживать
  отсутствующие шрифты в ваших документах с помощью понятных примеров кода.
og_title: Обработка замены шрифтов в Aspose.Words – Полное руководство
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Обработка замены шрифтов в Aspose.Words – Полное руководство по программированию
url: /ru/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Обработка замены шрифтов в Aspose.Words – Полное руководство по программированию

Задумывались ли вы когда‑нибудь, как **обрабатывать замену шрифтов**, когда документ Word ссылается на шрифт, который не установлен на сервере? Вы не одиноки. Во многих реальных приложениях — например, генераторах счетов или автоматических сервисах отчетов — отсутствие шрифтов приводит к тихим заменам, портящим макет.  

Хорошая новость в том, что Aspose.Words предоставляет встроенную систему предупреждений, позволяющую **обнаруживать отсутствующие шрифты** и реагировать так, как вам нужно. В этом руководстве мы пройдем регистрацию обработчика предупреждений, загрузку документа и извлечение точных событий замены шрифтов, о которых необходимо знать. К концу вы также увидите, как ответить на классический вопрос «**как обнаружить отсутствующие шрифты**?», используя чистый, готовый к продакшену код.

## Что покрывает это руководство

* Настройка Aspose.Words для генерации предупреждений при каждой замене шрифта.  
* Перехват этих предупреждений в пользовательском обработчике, чтобы вы могли вести журнал, заменять или прерывать процесс.  
* Использование полученных данных для **обнаружения отсутствующих шрифтов** до сохранения или рендеринга документа.  
* Советы по устранению краевых случаев — например, когда запасной шрифт выбирается без уведомления.  
* Полный, готовый к запуску пример, который можно вставить в любое консольное приложение .NET.  

> **Требования** — Вам понадобится актуальный .NET SDK (подойдёт 6.0+), действующая лицензия Aspose.Words for .NET (или временный оценочный ключ) и пример DOCX, который намеренно ссылается на шрифт, отсутствующий в системе. Другие сторонние библиотеки не требуются.

---

## ## Обработка замены шрифтов с помощью пользовательского обработчика предупреждений

Aspose.Words поднимает объект `WarningInfo` каждый раз, когда не может найти запрошенный шрифт. По умолчанию такие предупреждения игнорируются, поэтому вы часто не замечаете замену. Чтобы **обрабатывать замену шрифтов**, замените обработчик предупреждений по умолчанию на тот, который действительно что‑то делает.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Почему это работает

* `FontSettings.DefaultWarningHandler` — глобальное статическое свойство; после его установки **каждая** операция Aspose.Words в текущем AppDomain будет использовать ваш делегат.  
* `WarningInfoCollectionHandler` получает объект `WarningInfo`, содержащий `WarningType` и человекочитаемое `Description`. Фильтрация по `WarningType.FontSubstitution` гарантирует, что вы видите только интересующие вас события.  
* Вызов `doc.Save` заставляет библиотеку разрешить все шрифты, в этот момент генерируются предупреждения. Если нужно лишь проанализировать документ без сохранения, вместо этого можно вызвать `doc.UpdatePageLayout()`.

**Ожидаемый вывод в консоль** (при отсутствии шрифта “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Эта строка подтверждает, что библиотека **обнаружила отсутствующие шрифты** и выбрала запасной.

---

## ## Обнаружение отсутствующих шрифтов перед рендерингом

Иногда требуется полностью остановить процесс, если требуемый шрифт отсутствует — возможно, из‑за строгих бренд‑гайдов, требующих точной типографии. Обработчик предупреждений можно расширить, собирая все сообщения о недостающих шрифтах в список, после чего принимать решение.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Как это отвечает на вопрос «как обнаружить отсутствующие шрифты»

* Список `missingFonts` служит журналом всех событий замены.  
* После `UpdatePageLayout` можно проверить список и решить, продолжать ли процесс, вести журнал или бросить исключение.  
* Этот шаблон работает для любого формата вывода (PDF, HTML, изображения), поскольку система предупреждений не зависит от формата.

---

## ## Продвинутый совет: заменять отсутствующие шрифты конкретным запасным

Если у вас есть корпоративный шрифт, который обязателен к использованию, вы можете указать Aspose.Words автоматически заменять любой отсутствующий шрифт вашим запасным. Это удобно, когда нужно, чтобы документ *по‑прежнему* выглядел приемлемо без ручной пост‑обработки.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Разместите приведённый выше фрагмент **перед** загрузкой документа. Теперь любой отсутствующий шрифт — независимо от его оригинального названия — будет заменён на “Calibri” (или “Arial”, если Calibri недоступен). Вы всё равно получите предупреждение, но документ будет отрисован шрифтом, которым вы управляете.

---

## ## Распространённые подводные камни и как их избежать

| Подводный камень | Почему происходит | Решение |
|------------------|-------------------|---------|
| **Предупреждения исчезают после первого вызова** | Статический `DefaultWarningHandler` переопределяется позже в приложении. | Установите обработчик **один раз** при запуске приложения или сохраните ссылку и переустанавливайте её при изменении. |
| **Отчёт только о первом отсутствующем шрифте** | Некоторые API группируют предупреждения; необходимо вызвать `UpdatePageLayout` или `Save`, чтобы сбросить очередь. | Принудительно обновите макет или сохраните в нужном формате. |
| **Замена всё равно происходит даже после прерывания** | Обработчик предупреждений запускается *после* того, как замена уже произошла. | Используйте обработчик для **логирования**, а затем бросьте исключение, чтобы остановить дальнейшую обработку. |
| **Отсутствие шрифтов в Linux‑контейнерах** | В Linux часто отсутствует каталог шрифтов Windows, что приводит к множеству замен. | Подмонтируйте необходимые шрифты в контейнер или используйте `FontSettings.SetFontsFolder`, чтобы указать пользовательскую папку со шрифтами. |

---

## ## Обнаружение замены шрифтов в сценарии Web API

Если вы обслуживаете документы через ASP.NET Core, вам, вероятно, не нужны выводы в консоль. Вместо этого собирайте предупреждения и возвращайте их в составе HTTP‑ответа.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Теперь API **обнаруживает отсутствующие шрифты** и возвращает понятный JSON‑payload до генерации любого PDF. Это практический пример того, как реализовать «как обнаружить отсутствующие шрифты» в сервисе промышленного уровня.

---

## ## Тестирование вашей реализации

1. **Создайте тестовый DOCX**, который ссылается на шрифт, которого нет на машине (например, “Comic Sans MS” в минимальном Docker‑образе).  
2. Запустите консольное приложение или конечную точку API.  
3. Убедитесь, что консоль (или HTTP‑ответ) содержит предупреждение о замене.  
4. При желании откройте полученный PDF и проверьте свойства шрифта — Aspose.Words должен показать запасной шрифт, который вы настроили.

Если вы видите предупреждение, но PDF всё равно использует неожиданный шрифт, дважды проверьте порядок `SubstitutionSettings`; первое совпадение выигрывает.

---

## ## Заключение

Мы рассмотрели всё, что необходимо для **обработки замены шрифтов** в Aspose.Words: от регистрации обработчика предупреждений до программного **обнаружения отсутствующих шрифтов** и их замены корпоративным типом. Используя встроенную систему предупреждений, вы получаете полную видимость каждого события «шрифт не найден», что напрямую отвечает на вопрос «**как обнаружить отсутствующие шрифты**?», который задаёт каждый разработчик при автоматизации генерации документов.

Что дальше? Попробуйте сочетать эту логику с **динамической загрузкой шрифтов** (`FontSettings.SetFontsFolder`), чтобы поддерживать пользовательские шрифты «на лету», или расширьте обработчик предупреждений, записывая записи в центральный сервис логирования, например Serilog. Чем больше вы инструментаризируете работу со шрифтами, тем надёжнее становится ваш конвейер документооборота.

Есть сложный сценарий замены шрифтов, с которым вы боретесь? Оставьте комментарий ниже, и давайте разберёмся вместе. Happy coding!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом гайде. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}