---
category: general
date: 2026-06-02
description: как работать со шрифтами в .NET – обнаруживать отсутствующие шрифты и
  отслеживать изменения шрифтов с помощью LoadOptions и FontSettings. Узнайте полное,
  готовое к запуску решение.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: ru
og_description: как работать со шрифтами в .NET — обнаруживать отсутствующие шрифты
  и отслеживать их изменения. Следуйте этому пошаговому руководству для получения
  полного готового решения.
og_title: Как работать со шрифтами в .NET — обнаружить недостающие шрифты
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: Как работать со шрифтами в .NET – обнаружение отсутствующих шрифтов
url: /ru/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# как работать со шрифтами в .NET – обнаружение отсутствующих шрифтов

Когда‑нибудь задавались вопросом **как работать со шрифтами**, когда документ Word ссылается на шрифт, который не установлен на компьютере? Вы не одиноки. Отсутствующие шрифты могут превратить отшлифованный отчёт в бессвязный набор, и без надлежащих предупреждений вы можете никогда не узнать, что было заменено.  

В этом руководстве мы покажем, **как работать со шрифтами**, обнаруживая отсутствующие шрифты **и** отслеживая изменения шрифтов во время выполнения. К концу вы получите автономное консольное приложение, которое будет логировать каждую подстановку, чтобы вы никогда не были удивлены появлением загадочного Helvetica вместо Times New Roman.

> **Что вы получите:** полностью готовый к копированию и вставке образец кода, объяснение каждой строки, советы для реальных проектов и быстрый обзор граничных случаев, с которыми вы можете столкнуться.

## Требования

- .NET 6.0 или новее (в примере используется `Program.cs` верхнего уровня для краткости)  
- Aspose.Words for .NET 23.9 или новее – его можно установить из NuGet с помощью `dotnet add package Aspose.Words`  
- Документ Word, который намеренно ссылается на шрифт, которого у вас нет (например, `MissingFont.docx`)  

Никакие другие библиотеки не требуются.

![Диаграмма, показывающая, как LoadOptions передаётся в FontSettings и событие предупреждения о подстановке – пример обработки шрифтов в .NET](https://example.com/images/font‑handling‑flow.png "пример обработки шрифтов в .NET")

## Шаг 1: Настройка LoadOptions с FontSettings  

Первое, что нам нужно, – это объект `LoadOptions`, который сообщает Aspose.Words следить за проблемами шрифтов.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Почему это важно:** `LoadOptions` — контроллер доступа, когда документ читается с диска. Предоставив пользовательский `FontSettings`, мы получаем точку входа во внутренний механизм разрешения шрифтов, что является единственным способом **обнаружить отсутствующие шрифты** до рендеринга документа.

## Шаг 2: Подписка на событие SubstitutionWarning  

Aspose.Words генерирует событие `SubstitutionWarning` каждый раз, когда не может найти точно запрошенный шрифт. Мы будем логировать детали, чтобы вы могли увидеть, какие шрифты запрашивались и какие фактически использовались.

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Почему мы слушаем:** Без этого обработчика вы никогда не узнаете, что произошла подстановка. Событие предоставляет полный журнал аудита, удовлетворяя требование «отслеживать изменения шрифтов».

## Шаг 3: Загрузка документа с использованием наших настроек  

Теперь мы действительно читаем файл. Поскольку мы передали `loadOptions`, Aspose.Words вызовет событие предупреждения для любого отсутствующего шрифта, который встретит.

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

Вот и всё — документ загружен, а все проблемы со шрифтами уже выведены в консоль.

## Шаг 4: (Опционально) Проверка подставленных шрифтов в документе  

Если вы хотите двойную проверку, какие шрифты оказались в конечном PDF или DOCX, можете пройтись по коллекции шрифтов документа:

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Выполнение этого после загрузки перечислит каждый шрифт, который движок решил внедрить или сослаться. Удобно, когда нужно сформировать отчёт для QA‑команд.

## Полный рабочий пример  

Скопируйте блок ниже в новый консольный проект (`dotnet new console`) и запустите его. Программа выведет каждую подстановку, а затем перечислит шрифты, которые выжили после загрузки.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Ожидаемый вывод  

Если `MissingFont.docx` запрашивает *«Comic Sans MS»* (который не установлен), вы увидите примерно следующее:

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

Первая строка доказывает, что мы **обнаруживаем отсутствующие шрифты** и **отслеживаем изменения шрифтов**. Вторая строка показывает подстановку, которая не потребовалась (без предупреждения, потому что шрифт существовал).

## Распространённые подводные камни и профессиональные советы  

| Проблема | Что происходит | Как исправить / избежать |
|----------|----------------|--------------------------|
| **События предупреждения не срабатывают** | Вы можете подумать, что API сломан. | Убедитесь, что вы *назначили* `FontSettings` в `LoadOptions` **до** загрузки документа. Хук события должен быть подключён **до** вызова `new Document(...)`. |
| **Подставленные шрифты всё равно выглядят некорректно** | Aspose.Words переходит к общему шрифту, который не соответствует стилю. | Укажите пользовательскую папку со шрифтами через `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. Это даст движку больше вариантов перед тем, как он по умолчанию выберет общий шрифт. |
| **Падение производительности на больших документах** | Сканирование каждого шрифта может добавить несколько миллисекунд. | Кешируйте объект `FontSettings`, если загружаете много документов подряд. Переиспользование того же экземпляра избавляет от повторного чтения системных таблиц шрифтов. |
| **Вывод консоли теряется в GUI‑приложениях** | Вы не увидите предупреждения. | Перенаправьте событие в логгер (например, `Serilog`) или запишите в файл: `File.AppendAllText("font-warnings.log", …)`. |

## Расширение решения  

- **Экспорт в PDF с внедрёнными шрифтами** — после загрузки вызовите `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` и обязательно установите `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Пакетная обработка** — оберните логику загрузки в `foreach` по папке с DOCX‑файлами. Записывайте предупреждения каждого файла в CSV для аудита.  
- **Удобный пользовательский интерфейс** — выведите ту же логику за кнопку в WinForms/WPF‑приложении, показывая предупреждения в `ListBox`.  

## Заключение  

Мы прошли процесс **как работать со шрифтами** в .NET, настроив `LoadOptions`, подписавшись на событие `SubstitutionWarning` и, наконец, загрузив документ. Пример не только **обнаруживает отсутствующие шрифты**, но и **отслеживает изменения шрифтов**, позволяя вам аудировать каждую подстановку.  

Попробуйте с вашими собственными документами, измените путь к папке со шрифтами, и вы больше никогда не будете застигнуты врасплох неожиданной заменой шрифта. Если этот гид оказался полезным, изучите связанные темы, такие как *«внедрить пользовательские шрифты в PDF с Aspose.Words»* или *«создать стратегию резервных шрифтов для кроссплатформенных .NET‑приложений»*.  

Счастливого кодинга, и пусть ваши документы всегда отображаются точно так, как вы задумали!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом пособии. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Как загрузить DOCX и обнаружить отсутствующие шрифты – Полное руководство C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Как обнаружить шрифты в Aspose.Words – Обработка предупреждений и настроек](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Как использовать LoadOptions в Aspose.Words – Полное руководство](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}