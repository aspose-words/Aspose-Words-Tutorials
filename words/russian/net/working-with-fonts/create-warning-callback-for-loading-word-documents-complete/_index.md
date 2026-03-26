---
category: general
date: 2026-03-25
description: Создайте обратный вызов предупреждения для загрузки документа Word и
  обнаружения отсутствующих шрифтов. Узнайте, как настроить параметры шрифтов в Aspose.Words
  для .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: ru
og_description: Создайте обратный вызов предупреждения при загрузке документа Word
  с обнаружением отсутствующих шрифтов. Это руководство показывает, как настроить
  параметры шрифтов в Aspose.Words.
og_title: Создать обратный вызов предупреждения — загрузить документ Word и обнаружить
  недостающие шрифты
tags:
- Aspose.Words
- C#
- Font handling
title: Создание обратного вызова предупреждения при загрузке Word‑документов – Полное
  руководство
url: /ru/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать обратный вызов предупреждения – загрузка Word‑документа и обнаружение отсутствующих шрифтов

Когда‑нибудь нужно **создать обратный вызов предупреждения** при загрузке Word‑документа и возникает вопрос, почему некоторые шрифты просто исчезают? Вы не одиноки. Во многих корпоративных приложениях отсутствие шрифтов приводит к катастрофическим нарушениям разметки, и без правильного обратного вызова вы можете даже не заметить проблему.  

Хорошие новости? С Aspose.Words for .NET вы можете **загрузить Word‑документ**, **обнаружить отсутствующие шрифты** и **настроить параметры шрифтов** всего в нескольких строках кода. В этом руководстве мы пройдемся по полностью готовому примеру, объясним, почему каждый элемент важен, и покажем, как проверить, что обратный вызов предупреждения работает.

> **Что вы получите**  
> * Полную программу на C#, которая загружает DOCX, сообщает о любых заменах шрифтов и позволяет настраивать пути поиска шрифтов.  
> * Понимание классов `FontSettings`, `LoadOptions` и `IWarningCallback`.  
> * Советы по обработке крайних случаев, таких как встроенные шрифты или системные папки шрифтов.

---

## Требования

- .NET 6+ (или .NET Framework 4.7.2+) с компилятором C#.  
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Пример Word‑файла (`input.docx`), использующего хотя бы один шрифт, не установленный на машине (например, *Calibri Light* в минимальном Windows‑контейнере).  
- Базовое знакомство с консольными приложениями C#.

Дополнительные библиотеки не нужны; всё находится внутри Aspose.Words.

---

## Шаг 1: Создать обратный вызов предупреждения для обнаружения отсутствующих шрифтов

**Основной** элемент этой головоломки — класс, реализующий `IWarningCallback`. Aspose.Words будет вызывать этот обратный вызов каждый раз, когда встречает ситуацию, требующую предупреждения — наиболее частый случай — подстановку шрифта.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Почему это важно** — без обратного вызова вам пришлось бы просматривать логи уже после выполнения. Обрабатывая предупреждения в реальном времени, вы можете решить, прервать загрузку, заменить отсутствующий шрифт запасным или просто записать проблему в журнал для последующего анализа.

---

## Шаг 2: Настроить FontSettings для пользовательской обработки шрифтов

Прежде чем действительно загрузить документ, мы можем указать Aspose.Words, где искать шрифты, которых нет в системе. Для этого и служит `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Почему это важно** — указав Aspose.Words папку, содержащую недостающие шрифты, вы часто полностью избегаете подстановки. Когда это невозможно, разумный шрифт по умолчанию (например, *Arial*) сохраняет читаемость документа.

---

## Шаг 3: Загрузить Word‑документ с настроенным обратным вызовом предупреждения

Теперь соединяем всё вместе: создаём `LoadOptions`, подключаем наши `FontSettings` и `FontWarningHandler`, и наконец загружаем документ.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Почему это важно** — `LoadOptions` — единственное место, где вы задаёте *как* документ будет читаться. Передавая как конфигурацию шрифтов, так и обратный вызов предупреждения, мы гарантируем, что любой отсутствующий шрифт будет сразу найден в нужных местах **и** сразу же сообщён.

---

## Шаг 4: Проверка вывода — что вы должны увидеть?

Запустите программу из консоли. Если `input.docx` использует шрифт, который не установлен и также не находится в `C:\SharedFonts`, вы увидите примерно следующее:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Если все шрифты доступны, строка предупреждения просто не появится. Такой мгновенный цикл обратной связи бесценен в автоматизированных конвейерах обработки документов, где скрытая подмена шрифтов может нарушить фирменный стиль.

---

## Шаг 5: Распространённые подводные камни и рекомендации

| Подводный камень | Как избежать |
|------------------|--------------|
| **Забыли добавить `Aspose.Words.Fonts`** | Убедитесь, что в начале файла есть `using Aspose.Words.Fonts;` — иначе компилятор будет ругаться на отсутствующие типы. |
| **Неправильный путь к папке шрифтов** | Проверьте путь и установите `recursive: true`, если есть подпапки. Для отладки используйте `Path.GetFullPath`. |
| **Несколько обратных вызовов предупреждения** | Aspose.Words учитывает только последний назначенный `WarningCallback`. Оставляйте один обработчик, который делегирует дальнейшую логику при необходимости. |
| **Запуск на сервере без UI** | Вывод в консоль подходит, но для веб‑приложений лучше писать в файл журнала или систему мониторинга вместо `Console.WriteLine`. |
| **Большие документы снижают производительность** | Переиспользуйте один экземпляр `FontSettings` для нескольких загрузок; создание его каждый раз дорого. |

**Совет профессионала:** если нужно *собирать* предупреждения для последующего анализа, храните их в `List<string>` внутри обработчика вместо прямого вывода.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

После загрузки документа вы сможете проверить `handler.Messages`.

---

## Шаг 6: Расширение решения — а что если нужно встроить запасной шрифт?

Иногда требуется, чтобы отсутствующий шрифт был *встроен* в итоговый PDF, чтобы downstream‑просмотрщики отображали точный вид. После загрузки документа можно принудительно включить встраивание:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Этот фрагмент показывает, как тот же подход **настройки шрифтов** можно расширить и за пределы простой загрузки.

---

## Полный рабочий пример

Ниже полностью готовая программа, которую можно скопировать в новый проект Console App. В ней собраны все обсуждаемые части.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Ожидаемый вывод** (когда присутствует отсутствующий шрифт):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Если подстановки не происходит, выводятся только сообщения об успешном завершении.

---

## Заключение

Мы только что **создали обратный вызов предупреждения**, который надёжно **обнаруживает отсутствующие шрифты** при **загрузке Word‑документа** с помощью Aspose.Words, и продемонстрировали, как **настроить параметры шрифтов**, чтобы управлять поиском шрифтов и выбором запасного варианта. Связав `FontSettings` и `LoadOptions`, вы получаете полную видимость проблем, связанных со шрифтами — больше никаких тихих сбоев в разметке.

Что дальше? Попробуйте заменить `FontWarningHandler` на логгер, записывающий в базу данных, или поэкспериментируйте с **правилами подстановки шрифтов**, сопоставляющими конкретные отсутствующие шрифты с одобренными брендом альтернативами. Вы также можете исследовать **динамическую загрузку шрифтов** из облачного хранилища, если ваше приложение работает в контейнеризованной среде.

Есть вопросы о специфических случаях — например, обработка OpenType‑фич или зашифрованных DOCX? Оставляйте комментарий ниже, и happy coding!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}