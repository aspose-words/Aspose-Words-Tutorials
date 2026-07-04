---
category: general
date: 2026-05-29
description: Узнайте, как установить FontSettings в Aspose.Words и корректно обрабатывать
  отсутствующие шрифты. Пошаговое руководство с полным кодом и лучшими практиками.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: ru
og_description: Как установить FontSettings в Aspose.Words и быстро обработать отсутствующие
  шрифты. Следуйте этому руководству для получения полного, готового к запуску решения.
og_title: Как настроить FontSettings – Обработка отсутствующих шрифтов
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Как задать FontSettings — обработка отсутствующих шрифтов
url: /ru/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить FontSettings – Обработка отсутствующих шрифтов

Когда‑то задумывались **как установить FontSettings** при работе с Aspose.Words и вдруг сталкиваетесь с документом, который ссылается на шрифт, которого у вас нет? Это распространённая проблема, особенно при обработке файлов, предоставленных клиентом, на сервере, где установлен лишь минимальный набор шрифтов. Хорошая новость: вы можете отлавливать такие пробелы и **обрабатывать отсутствующие шрифты**, не позволяя приложению падать или генерировать некрасивые PDF‑файлы.

В этом руководстве мы пройдём реальный сценарий: загрузка DOCX, который требует “Calibri”, тогда как ваш Linux‑контейнер содержит только “DejaVu Sans”. Вы увидите, как настроить FontSettings, подписаться на предупреждения о подстановке и задать резервные шрифты, чтобы документ отобразился так, как задумал автор. Без лишних слов — только код, который можно сразу вставить в проект.

## Требования

- .NET 6.0 или новее (API работает одинаково и в .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 или новее (имя NuGet‑пакета — `Aspose.Words`)
- Базовая среда разработки C# (Visual Studio, Rider или VS Code)

Если всё это у вас есть, приступаем.

## Шаг 1: Создайте FontSettings и подпишитесь на события подстановки

Сердце решения — объект `FontSettings`. Подключив обработчик к событию `FontSubstitutionWarning`, вы будете получать живой отчёт каждый раз, когда Aspose.Words придётся заменить отсутствующий тип шрифта.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Почему это важно:**  
Когда движок не может найти *Calibri*, он может тихо переключиться на *Arial*. Подписавшись на предупреждение, вы сохраняете прозрачный журнал — идеально для отладки или отчётности.

> **Pro tip:** Если вы запускаете это на CI‑сервере, перенаправьте вывод в файл журнала, чтобы позже проанализировать, какие шрифты отсутствовали после пакетного запуска.

## Шаг 2: Присоедините FontSettings к LoadOptions

`LoadOptions` — шлюз для управления тем, как документ парсится. Присвоив ему только что сконфигурированный `FontSettings`, каждый последующий вызов `Document` будет учитывать нашу логику подстановки.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Что происходит под капотом?**  
Во время конструктора `Document` Aspose.Words читает XML DOCX, разрешает ссылки на шрифты и — если шрифт не найден — генерирует предупреждение, которое мы настроили ранее. Без этого хука вы никогда не узнаете, что произошла подстановка.

## Шаг 3: Загрузите документ и (по желанию) задайте резервные шрифты

Теперь наконец загружаем файл в память. Если у вас уже есть папка с резервными шрифтами (например, каталог OpenType‑шрифтов, поставляемый с приложением), укажите `FontSettings`, где её искать. Этот шаг необязателен, но часто самый чистый способ *обработать отсутствующие шрифты*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Внимание к краевым случаям:**  
Если документ содержит пользовательский шрифт, встроенный как бинарный поток, Aspose.Words использует его автоматически — подстановка не требуется. Предупреждение срабатывает только для *отсутствующих* системных шрифтов.

### Проверка результата

После загрузки вы можете сохранить документ в PDF или Word, чтобы убедиться, что всё выглядит правильно.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

При запуске программы в консоли появятся строки вида:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Если вы видите эти сообщения, вы успешно **обработали отсутствующие шрифты** и точно знаете, какие подстановки произошли.

## Шаг 4: Продвинутое – Пользовательские правила подстановки шрифтов (опционально)

Иногда нужна детерминированная карта, например, всегда заменять *Times New Roman* на *Liberation Serif*. Это можно сделать с помощью `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Зачем это нужно?**  
Явные правила дают контроль над типографикой, обеспечивая согласованность бренда в генерируемых PDF, особенно когда вы создаёте маркетинговые материалы.

## Распространённые подводные камни и как их избежать

| Проблема | Симптом | Решение |
|----------|----------|----------|
| **Нет вывода предупреждений** | Вы считаете, что шрифты в порядке, но документ выглядит некорректно. | Убедитесь, что `FontSubstitutionWarning` подключён **до** загрузки документа. |
| **Папка резервных шрифтов не сканируется** | Подстановки всё равно переходят к системным шрифтам по умолчанию. | Вызовите `SetFontsFolder(path, true)`, где второй параметр `true` включает рекурсивный поиск подпапок. |
| **Падение производительности при больших партиях** | Загрузка 10 000 документов становится медленной. | Кешируйте один экземпляр `FontSettings` и переиспользуйте его между загрузками; не создавайте новый каждый раз. |
| **Встроенные шрифты игнорируются** | Вы ожидали, что пользовательский встроенный шрифт будет использован, но произошла подстановка. | Проверьте, действительно ли исходный DOCX встраивает шрифт (см. Word → Файл → Свойства → Шрифты). |

## Полный рабочий пример

Ниже представлена полностью готовая к копированию программа. Она демонстрирует всё: от обработки событий до сохранения итогового PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Ожидаемый вывод в консоль** (пример):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Запустите программу, откройте `Output.pdf` — вы увидите текст, отрисованный резервными шрифтами, без квадратов вместо глифов и без сбоев.

## Заключение

Теперь у вас есть надёжный, готовый к продакшену шаблон для **установки FontSettings** в Aspose.Words и **обработки отсутствующих шрифтов**. Подключив событие `FontSubstitutionWarning`, указав каталог резервных шрифтов и (при необходимости) задав явные правила подстановки, вы получаете полную видимость и контроль над типографикой в автоматизированных конвейерах документов.

Что дальше? Попробуйте добавить собственную коллекцию шрифтов для фирменных наборов или изучите API `FontSourceBase` для загрузки шрифтов из базы данных или облачного хранилища. Принципы те же — просто подключите другой источник к `FontSettings`.

Есть вопросы о краевых случаях, например, обработке сценариев справа‑налево или шрифтов‑эмодзи? Оставляйте комментарий ниже, и happy coding!

## Что изучать дальше?

- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}