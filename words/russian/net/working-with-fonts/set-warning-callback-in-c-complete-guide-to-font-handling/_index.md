---
category: general
date: 2026-02-10
description: Установите обратный вызов предупреждений, чтобы отслеживать изменения
  шрифтов при настройке шрифта по умолчанию и установке шрифта импорта по умолчанию
  в Aspose.Words. Ознакомьтесь с полным пошаговым решением.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: ru
og_description: Установите обратный вызов предупреждений, чтобы отслеживать изменения
  шрифтов при настройке шрифта по умолчанию и установке шрифта импорта по умолчанию.
  Следуйте полному руководству по Aspose.Words.
og_title: Установить обратный вызов предупреждения в C# – Полное руководство
tags:
- Aspose.Words
- C#
- Document Import
title: Установить обратный вызов предупреждения в C# — Полное руководство по работе
  со шрифтами
url: /ru/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

craft translation carefully.

Be careful with preserving markdown formatting like **, *.

Also ensure not to translate code placeholders.

Now write final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Установить обратный вызов предупреждения в C# – Полное руководство по работе со шрифтами

Когда‑ли вам когда‑нибудь нужно было **set warning callback** при загрузке Word‑документа и вы задавались вопросом, как одновременно *configure default font*? Вы не одиноки. Во многих реальных проектах — например, в автоматических генераторах отчетов или конвейерах конвертации документов — отсутствие шрифтов может тихо нарушить макет, и единственный способ обнаружить эти проблемы — **monitor font changes** через обратный вызов предупреждения.

В этом руководстве мы пройдем практический пример, показывающий, как **set warning callback**, **configure default font**, а также **set default import font** с помощью Aspose.Words for .NET. К концу вы получите готовый к запуску фрагмент кода, поймёте, почему каждый элемент важен, и узнаете, как адаптировать его для особых случаев, таких как пользовательские папки со шрифтами или тихие подстановки.

---

## Необходимые условия

- .NET 6.0 или новее (код также работает на .NET Framework 4.6+)  
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Папка, содержащая резервный шрифт, который вы хотите использовать (например, `fonts/Arial.ttf`)  
- Базовое знакомство с консольными приложениями C#  

Дополнительные библиотеки не требуются.

---

## Шаг 1: Создать LoadOptions и **configure default font**

Первое, что нужно сделать, когда вы хотите контролировать работу со шрифтами, — построить экземпляр `LoadOptions`. Этот объект сообщает Aspose.Words, как обрабатывать отсутствующие шрифты во время импорта.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Почему это важно:**  
Если исходный документ ссылается на шрифт, который не установлен на сервере, Aspose.Words посмотрит в указанную вами папку. Это и есть суть **set default import font** — вы явно указываете библиотеке, где искать замену ещё до появления каких‑либо предупреждений.

---

## Шаг 2: **Set warning callback** to **monitor font changes**

Aspose.Words генерирует `WarningInfoCollection` каждый раз, когда необходимо заменить шрифт, а также в других ситуациях. Подключив обработчик, вы сможете записывать или реагировать на каждую подстановку.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Почему это важно:**  
Просто **configure default font** недостаточно, если нужно отследить, какие именно шрифты были заменены. Обратный вызов предоставляет журнал в реальном времени, удовлетворяя требование **monitor font changes** и помогая быстро обнаружить неожиданные подстановки в CI‑конвейере.

---

## Шаг 3: Load the document with the prepared options

Теперь, когда параметры загрузки полностью подготовлены, вы можете безопасно загрузить любой файл `.docx`. При возникновении подстановки обратный вызов сработает автоматически.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Что вы увидите:**  
Если в источнике используется шрифт, которого нет, консоль выведет что‑то вроде:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Этот вывод подтверждает, что вы успешно **set warning callback** и что **default import font** сработал.

---

## Шаг 4: (Optional) Fine‑tune font substitution behavior

Иногда требуется заменить *все* отсутствующие шрифты одной семьёй, независимо от оригинального запроса. Aspose.Words позволяет задать *fallback font* глобально.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Когда использовать это:**  
Если вы генерируете PDF‑файлы для бренда, допускающего только ограниченный набор шрифтов, это гарантирует единообразие во всех документах, даже если исходный файл пытается использовать что‑то экзотическое.

---

## Шаг 5: Save or further process the document

После загрузки вы можете продолжать любую необходимую обработку — редактирование, конвертацию в PDF, извлечение текста и т.д. Ниже пример сохранения документа как PDF с сохранением подставленных шрифтов.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Полученный PDF будет отображать резервный шрифт в местах подстановки, предоставляя визуальное подтверждение того, что **set warning callback** сработал как ожидалось.

---

## Распространённые ошибки и профессиональные советы

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Callback never fires** | `LoadOptions.WarningCallback` не был назначен *до* загрузки документа. | Всегда подключайте обратный вызов **до** вызова `new Document(...)`. |
| **Wrong font folder** | Ошибка в пути или отсутствие прав на чтение. | Убедитесь, что папка существует и приложение имеет доступ `Read`. Для надёжности используйте абсолютные пути. |
| **Multiple substitutions, noisy output** | Большие документы с множеством отсутствующих шрифтов. | Фильтруйте предупреждения по `WarningType.FontSubstitution` (как показано) или записывайте их в файл журнала вместо консоли. |
| **Fallback font not applied** | Резервный шрифт не установлен на машине. | Поместите файл `.ttf`/`.otf` в папку, переданную в `SetFontsFolder`. Aspose.Words загрузит его напрямую, установка в ОС не требуется. |

**Pro tip:** При запуске в CI/CD‑конвейере перенаправляйте вывод консоли в артефакт сборки. Так вы получите аудит‑лог каждой подстановки шрифта, произошедшей во время сборки.

---

## Полный рабочий пример (готов к копированию)

Ниже представлена полностью готовая программа, которую можно вставить в новый проект Console App. В ней включены все шаги, `using`‑директивы и комментарии.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Ожидаемый вывод в консоли** (при отсутствии `Times New Roman`):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Запустите программу, откройте `output.pdf` — вы увидите документ, отрисованный резервным шрифтом там, где это было необходимо.

---

## Заключение

Теперь у вас есть надёжный, готовый к продакшену шаблон для **set warning callback** в C#, **configure default font**, **monitor font changes** и **set default import font** при работе с Aspose.Words. Подключив сборщик предупреждений до загрузки, указав `FontSettings` на надёжную папку со шрифтами и, при необходимости, задав глобальный fallback, вы получаете полную видимость и контроль над подстановкой шрифтов — именно то, что требуется любой надёжной системе обработки документов.

Готовы к следующему уровню? Попробуйте комбинировать этот подход с:

- **Dynamic font loading** из базы данных (используйте `FontSettings.SetFontsFolder` во время выполнения).  
- **Custom warning handlers**, записывающие в структурированный лог (JSON или CSV) для аналитики.  
- **Parallel document processing**, где каждый поток получает собственный `LoadOptions`, чтобы избежать взаимных конфликтов.

Экспериментируйте, адаптируйте код под свою архитектуру и делитесь находками в комментариях. Приятного кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}