---
category: general
date: 2026-01-11
description: Восстановление повреждённого документа в C# с использованием Aspose.Words.
  Узнайте, как установить режим восстановления, загрузить docx с восстановлением и
  вывести запрос пользователю при ошибке в несколько простых шагов.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: ru
og_description: Восстановление повреждённого документа в C# с помощью установки режима
  восстановления, загрузки DOCX с восстановлением и вывода сообщения пользователю
  при ошибке. Полный пошаговый учебник.
og_title: Восстановление повреждённого документа в C# – Краткое руководство
tags:
- Aspose.Words
- C#
- Document Recovery
title: Восстановление повреждённого документа в C# – установить режим восстановления
  и запросить действие у пользователя
url: /ru/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Восстановление повреждённого документа в C# – Полное руководство

Когда‑то пытались открыть DOCX, который выглядит нормально в Word, но в вашем коде бросает исключение? Скорее всего, вы столкнулись со сценарием **восстановления повреждённого документа**. Хорошая новость – Aspose.Words предоставляет тонкую настройку того, как обрабатывать такие «негодные» файлы: молча исправлять их, бросать исключение или спрашивать пользователя, что делать.

В этом руководстве мы пройдём всё, что нужно для **восстановления повреждённого документа**, от установки библиотеки до выбора правильного параметра **set recovery mode**, **load docx with recovery**, и, наконец, **prompt user on error**, когда что‑то идёт не так. Без лишних слов, только полностью рабочий пример, который можно вставить в любой .NET‑проект.

> **Краткий обзор:** К концу вы получите консольное приложение, которое загружает потенциально сломанный `corrupt.docx`, выводит любые предупреждения и спрашивает пользователя, продолжать ли работу, если восстановление не удалось.

---

## Что понадобится

- **.NET 6.0** или новее (код также работает на .NET Framework 4.6+).  
- **Aspose.Words for .NET** – установить через NuGet (`Install-Package Aspose.Words`).  
- Файл **повреждённого DOCX** для тестов (можно умышленно испортить файл, открыв его в hex‑редакторе или переименовав расширение).  
- Любая удобная IDE – Visual Studio, Rider или даже VS Code подойдёт.

> *Совет профи:* Сохраняйте резервную копию оригинального файла. Восстановление может переписать части документа, и вы не захотите потерять хорошие данные.

---

## Шаг 1 – Установить Aspose.Words и добавить пространства имён

Сначала получаем библиотеку из NuGet и подключаем необходимые пространства имён.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Это всё, что понадобится для дальнейшего руководства. Пространство имён `Aspose.Words.Loading` содержит класс `LoadOptions`, который является ключом к **set recovery mode**.

---

## Шаг 2 – Выбрать режим восстановления (Primary H2 with Keyword)

### Recover Corrupted Document – Установка правильного режима восстановления

Aspose.Words предлагает три поведения при восстановлении:

| Mode | What Happens | When to Use |
|------|--------------|------------|
| **PromptUser** | Показывает диалог (или вы можете реализовать собственный запрос) и пытается исправить файл. | Идеально для интерактивных инструментов, где пользователь может решить. |
| **Silent** | Пытается исправить автоматически, без UI. | Хорошо для пакетных заданий или сервисов. |
| **ThrowException** | Останавливает обработку и бросает исключение. | Используйте, когда нужна строгая проверка. |

Ниже показано, как **set recovery mode** в `PromptUser`. Если предпочтительнее тихий режим, просто замените значение перечисления.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Почему это важно:** Явно **set recovery mode** сообщает Aspose.Words, насколько агрессивно он должен действовать. По умолчанию — `PromptUser`, но явное указание делает ваш замысел кристально ясным – как для будущих поддерживающих, так и для поисковых систем, сканирующих код.

---

## Шаг 3 – Загрузить DOCX с восстановлением

Теперь **load docx with recovery** с помощью `LoadOptions`, которые мы только что настроили. Если файл повреждён, Aspose.Words либо исправит его, либо выдаст предупреждение, в зависимости от выбранного режима.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

Конструктор `Document` делает всю тяжёлую работу. В режиме **PromptUser** вы увидите запрос в консоли (или пользовательский UI, если подпишетесь на события `LoadOptions`), спрашивающий, продолжать ли. В режиме **Silent** метод просто делает всё, что может, и идёт дальше.

---

## Шаг 4 – Просмотреть предупреждения и спросить пользователя

Aspose.Words записывает любые найденные проблемы в коллекцию `Warnings`. Пройдемся по ней и дадим пользователю шанс решить, что делать дальше.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Этот фрагмент **prompt user on error** в консольном виде. Если вы создаёте приложение Windows Forms или WPF, замените `Console.ReadLine` на `MessageBox` или собственный диалог.

---

## Шаг 5 – Работа с восстановленным документом

На данном этапе документ находится в памяти, исправлен насколько это возможно Aspose.Words. Теперь можно читать его содержимое, сохранять чистую копию или выполнять любые нужные манипуляции.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Запуск полной программы против повреждённого файла выдаст вывод в консоль, похожий на этот:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Если файл оказался целым, вы увидите «Document loaded without any warnings.» и чистая копия будет идентична исходнику.

---

## Полный рабочий пример

Вот вся программа в одном месте. Скопируйте‑вставьте её в новый консольный проект и нажмите **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Запустите, испортите тестовый файл и наблюдайте за процессом восстановления. 🎉

---

## Пограничные случаи и варианты

| Scenario | What to Change | Why |
|----------|----------------|-----|
| **Batch processing** (no user interaction) | Set `RecoveryMode = RecoveryMode.Silent` and remove the console prompt. | Keeps the pipeline moving automatically. |
| **Strict validation** (fail fast) | Use `RecoveryMode.ThrowException`. Wrap the load call in a try/catch and log the exception. | Guarantees you never work with a partially repaired file. |
| **Custom UI** (WinForms/WPF) | Subscribe to `LoadOptions.LoadingProgress` or use `Document.LoadOptions` events to show a dialog. | Provides a richer experience than the console. |
| **Large documents** (memory constraints) | Load with `LoadOptions.LoadFormat = LoadFormat.Docx` and consider `Document.SaveOptions` to stream output. | Prevents OutOfMemory exceptions. |

---

## Практические советы (E‑E‑A‑T сигналы)

- **Всегда делайте резервную копию** перед попыткой восстановления; процесс может перезаписать части файла.  
- **Записывайте предупреждения** в файл для последующего анализа; они часто указывают на коренную причину (например, отсутствующие части, повреждённый XML).  
- **Тестируйте разные типы повреждений** – обрезайте файл, портите XML‑теги или меняйте структуру zip‑архива, чтобы увидеть, как каждый режим реагирует.  
- **Регулярно обновляйте Aspose.Words**; новые версии улучшают алгоритмы восстановления и добавляют новые типы предупреждений.  
- **Комбинируйте с валидацией** – после восстановления выполните быстрый `document.UpdateFields()` и `document.Save()`, чтобы убедиться, что документ полностью функционирует.

---

## Заключение

Теперь вы знаете, как **восстанавливать повреждённые документы** в C# с помощью **set recovery mode**, **load docx with recovery** и **prompt user on error**, когда что‑то идёт не так. Полный пример демонстрирует чистый, сквозной процесс, который работает в консольных приложениях, сервисах и UI‑проектах.

Что дальше? Попробуйте заменить консольный запрос на модальное окно в WinForms, поэкспериментируйте с режимом **Silent** для фоновых задач или интегрируйте логику восстановления в конечную точку загрузки файлов ASP.NET, чтобы пользователи могли загружать сломанные DOCX и получать сразу исправленную версию.

Счастливого кодинга, и пусть ваши документы остаются целыми!  

---

![Пример восстановления повреждённого документа](/images/recover-corrupted-document.png "восстановление повреждённого документа")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}