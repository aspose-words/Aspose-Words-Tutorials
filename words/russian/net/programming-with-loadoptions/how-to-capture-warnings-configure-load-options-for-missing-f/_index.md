---
category: general
date: 2026-03-30
description: как перехватывать предупреждения при загрузке файла DOCX — узнайте, как
  обнаруживать отсутствующие шрифты, настраивать параметры шрифтов и задавать параметры
  загрузки в C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: ru
og_description: как перехватывать предупреждения при загрузке файла DOCX – пошаговое
  руководство по обнаружению отсутствующих шрифтов и настройке параметров шрифтов
  в C#
og_title: Как отлавливать предупреждения — настройка параметров загрузки для отсутствующих
  шрифтов
tags:
- Aspose.Words
- C#
- Font management
title: как перехватывать предупреждения – настроить параметры загрузки для отсутствующих
  шрифтов
url: /ru/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# как захватывать предупреждения – настройка параметров загрузки для отсутствующих шрифтов

Когда‑нибудь задумывались **как захватывать предупреждения**, которые появляются, когда документ пытается использовать шрифт, которого у вас нет установленного? Это ситуация, которая ставит в тупик многих разработчиков, работающих с библиотеками обработки текста, особенно когда нужно **обнаружить отсутствующие шрифты**, прежде чем они нарушат ваш конвейер экспорта PDF.

В этом руководстве мы покажем вам практическое, готовое к запуску решение, которое **настраивает параметры шрифтов**, **устанавливает параметры загрузки** и выводит каждое предупреждение о замене в консоль. К концу вы точно будете знать, **как обрабатывать отсутствующие шрифты** так, чтобы ваше приложение оставалось надёжным, а пользователи — довольными.

## Что вы узнаете

- Как **установить параметры загрузки**, чтобы библиотека сообщала о проблемах со шрифтами, а не молча заменяла их.
- Точные шаги **настройки параметров шрифтов** для захвата предупреждений.
- Способы **программного обнаружения отсутствующих шрифтов** и реагирования на них.
- Полный пример на C#, который можно скопировать и вставить, работающий с последней версией Aspose.Words for .NET (v24.10 на момент написания).
- Советы по расширению решения: запись предупреждений в лог, переход к пользовательским шрифтам или прерывание обработки при отсутствии критических шрифтов.

> **Prerequisite:** Вам нужен установленный NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`). Других внешних зависимостей не требуется.

---

## Шаг 1: Импорт пространств имён и подготовка проекта

Сначала добавьте необходимые директивы `using`. Это не просто шаблонный код; он указывает компилятору, где находятся `LoadOptions`, `FontSettings` и `Document`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Pro tip:** Если вы используете .NET 6+, можете включить *global using*‑директивы, чтобы не повторять эти строки в каждом файле.

---

## Шаг 2: Установить параметры загрузки и включить предупреждения о замене шрифтов

Суть **как захватывать предупреждения** заключается в объекте `LoadOptions`. Создавая новый экземпляр `FontSettings` и подписываясь на событие `SubstitutionWarning`, вы заставляете библиотеку сообщать каждый раз, когда не может найти запрошенный шрифт.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Почему это важно:** Без подписки на событие Aspose.Words молча переходит к шрифту по умолчанию, и вы никогда не узнаете, какие глифы были заменены. Подписавшись на `SubstitutionWarning`, вы получаете полный журнал событий — это критично в средах с жёсткими требованиями к соответствию.

---

## Шаг 3: Загрузить документ с использованием настроенных параметров

Теперь, когда предупреждения подключены, загрузите ваш DOCX (или любой поддерживаемый формат) с помощью `loadOptions`, которые вы только что подготовили. Конструктор `Document` сразу же запустит проверку шрифтов.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Если файл, например, ссылается на *“Comic Sans MS”* на машине, где установлен только *“Arial”*, вы увидите что‑то вроде:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Эта строка выводится напрямую в консоль благодаря обработчику, который мы подключили ранее.

---

## Шаг 4: Проверить и отреагировать на захваченные предупреждения

Захват предупреждений — это только половина дела; дальше обычно нужно решить, что делать. Ниже показан простой шаблон, который сохраняет предупреждения в список для последующего анализа — идеально, если вы хотите записать их в файл или прервать импорт при отсутствии критического шрифта.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Обработка граничных случаев:**  
- **Несколько отсутствующих шрифтов:** Список будет содержать одну запись на каждую замену, так что вы можете пройтись по нему и сформировать детальный отчёт.  
- **Пользовательские резервные шрифты:** Если у вас есть собственные файлы шрифтов, добавьте их в `FontSettings` перед загрузкой: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Предупреждения тогда покажут ваш пользовательский резерв вместо системного по умолчанию.  

---

## Шаг 5: Полный рабочий пример (готовый к копированию)

Объединив всё вместе, получаем автономное консольное приложение, которое можно сразу собрать и запустить.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Ожидаемый вывод в консоль** (когда DOCX ссылается на отсутствующий шрифт):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Если отсутствует *критический* шрифт, например “Times New Roman”, вы увидите сообщение об остановке вместо него.

---

## Часто задаваемые вопросы и подводные камни

| Вопрос | Ответ |
|----------|--------|
| **Нужно ли вызывать `SetFontsFolder`, чтобы захватывать предупреждения?** | Нет. Событие предупреждения работает с шрифтами системы по умолчанию. Используйте `SetFontsFolder` только когда хотите добавить дополнительные резервные шрифты. |
| **Будет ли это работать на .NET Core / .NET 5+?** | Абсолютно. Aspose.Words 24.10 поддерживает все современные .NET‑рантаймы. Просто убедитесь, что версия NuGet‑пакета соответствует целевой платформе. |
| **А если я хочу записывать предупреждения в файл, а не в консоль?** | Замените `Console.WriteLine(msg);` на вызов любой системы логирования, например `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Можно ли подавлять предупреждения для конкретных шрифтов?** | Да. Внутри обработчика можно отфильтровать: `if (e.FontName == "SomeFont") return;`. Это даёт тонкую настройку. |
| **Есть ли способ рассматривать отсутствующие шрифты как ошибки?** | Вы можете вручную бросить исключение внутри обработчика при выполнении условия, либо установить флаг и прервать процесс после создания `Document`, как показано в примере. |

---

## Заключение

Теперь у вас есть надёжный, готовый к продакшену шаблон **как захватывать предупреждения**, возникающие при загрузке документов с отсутствующими шрифтами. **Обнаруживая отсутствующие шрифты**, **настраивая параметры шрифтов** и **устанавливая параметры загрузки**, вы получаете полную видимость событий замены шрифтов и можете решить, записывать их, использовать резервные шрифты или прерывать процесс.  

Сделайте следующий шаг, интегрировав эту логику в ваш конвейер конвертации в PDF, добавив пользовательские резервные шрифты или передав список предупреждений в систему мониторинга. Подход масштабируется от небольших утилит до корпоративных сервисов обработки документов.

---

### Дополнительные материалы и дальнейшие шаги

- **Изучите дополнительные возможности FontSettings** — встраивание пользовательских шрифтов, управление порядком резервирования и вопросы лицензирования.  
- **Комбинируйте с конвертацией в PDF** — после захвата предупреждений вызовите `doc.Save("output.pdf");` и проверьте, что PDF использует ожидаемые шрифты.  
- **Автоматизируйте тестирование** — напишите модульные тесты, которые загружают документы с известными отсутствующими шрифтами и проверяют, что список предупреждений содержит ожидаемые сообщения.  

Если у вас возникнут сложности или есть идеи по улучшению, оставляйте комментарий. Приятного кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}