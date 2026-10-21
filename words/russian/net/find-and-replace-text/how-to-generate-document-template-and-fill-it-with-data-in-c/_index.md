---
category: general
date: 2026-09-21
description: Узнайте, как создать шаблон документа, заполнить шаблон Word и заменить
  заполнители в файле DOCX с помощью C# — пошаговое руководство.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: ru
lastmod: 2026-09-21
og_description: Создайте шаблон документа на C#, заполняя шаблон Word, заменяя заполнители,
  и сохраняя заполненный файл DOCX. Следуйте этому полному руководству.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Создание шаблона документа на C# – заполнение файлов DOCX данными
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: Как создать шаблон документа и заполнить его данными в C#
url: /ru/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как генерировать шаблон документа и заполнять его данными в C#

Если вам нужно **генерировать шаблоны документов** файлов, которые можно переиспользовать для счетов, контрактов или отчетов, это руководство покажет вам точный процесс. Вы научитесь **заполнять шаблон Word** заполнителями, заменять их реальными значениями и, наконец, **заполнять шаблоны docx** программно.

Создание переиспользуемого шаблона устраняет ручное копирование‑вставку и обеспечивает согласованность всех генерируемых документов. Нижеописанные шаги работают с любым файлом `.docx`, содержащим простые токены‑заполнители, такие как `{{Name}}`.

## Предварительные требования

* .NET 6.0 SDK или более поздняя версия, установленная  
* Visual Studio 2022 (или любая предпочитаемая IDE)  
* Пакет NuGet **Aspose.Words for .NET** — он предоставляет класс `Document`, используемый в примере  

Вы можете добавить пакет следующей командой:

```bash
dotnet add package Aspose.Words
```

## Шаг 1: Подготовьте шаблон Word

Создайте документ Word (`Template.docx`), содержащий заполнители, где должны появляться динамические данные. Распространённая конвенция — двойные фигурные скобки:

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Сохраните файл в папке, к которой можно обратиться из кода, например `C:\Docs\Template.docx`.

## Шаг 2: Загрузите шаблон документа

Первое программное действие — загрузить шаблон в память. Конструктор `Document` читает файл и создает объектную модель, которой вы можете управлять.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Почему это важно:** Загрузка файла создает чистую копию каждый раз, поэтому оригинальный шаблон остаётся нетронутым для будущих запусков.

## Шаг 3: Замените заполнители реальными данными

Aspose.Words предоставляет простой метод `Range.Replace`, который сканирует документ в поиске конкретной строки и заменяет её. Оберните вызов в вспомогательный метод, чтобы основной поток оставался чистым.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**Как это работает:** `Range.Replace` проходит по каждому абзацу, ячейке таблицы, заголовку и нижнему колонтитулу, гарантируя обновление всех вхождений токена. Это самый надёжный способ **как заменить заполнитель** текста в файле DOCX.

### Обработка множественных вхождений и отсутствующих токенов

* Если заполнитель встречается более одного раза, `Replace` автоматически обновляет все экземпляры.  
* Если заполнитель отсутствует, метод просто ничего не делает — исключение не выбрасывается.  
* Для больших документов можно повысить производительность, отключив `doc.UpdateFields()` до завершения всех замен.

## Шаг 4: Сохраните заполненный документ

После замены всех заполнителей запишите результат в новый файл. Сохранение вывода отдельно сохраняет оригинальный шаблон для будущих запусков.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Результат:** `FilledTemplate.docx` теперь содержит персонализированное содержание:

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Шаг 5: Проверьте результат (необязательно)

Если вы хотите программно подтвердить, что замены прошли успешно, вы можете заново прочитать сохранённый файл и искать ожидаемые значения:

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

Выполнение шага проверки выводит `true`, когда заполнитель был заменён корректно.

## Распространённые подводные камни и рекомендации по лучшим практикам

| Issue | Why it happens | Recommended fix |
|-------|----------------|-----------------|
| **Заполнители содержат лишние пробелы** | `"{{ Name }}"` не совпадает с `"{{Name}}"`. | Держите токены заполнителей без пробелов, либо обрезайте их с обеих сторон перед заменой. |
| **Word добавляет скрытое форматирование** | Word может хранить заполнитель, разбитый на несколько ранов, из‑за чего `Replace` может его пропустить. | Используйте `Document.Range.Replace` с параметром `FindReplaceOptions`, где `MatchCase = false` и `FindWholeWordsOnly = false`. |
| **Большие документы вызывают замедление** | Замена токенов по одному вызывает полное сканирование документа каждый раз. | Выполняйте пакетную замену за один проход, вызывая `Range.Replace` для каждого токена перед сохранением. |
| **Сохранение в папку только для чтения** | `doc.Save` бросает `UnauthorizedAccessException`. | Убедитесь, что у целевого каталога есть права на запись, либо выберите путь, доступный для записи пользователем (например, `%TEMP%`). |

## Полный рабочий пример

Ниже представлен полный, автономный пример программы, который вы можете скопировать, вставить и запустить.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Ожидаемый вывод в консоль**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Откройте `FilledTemplate.docx` в Microsoft Word, чтобы увидеть персонализированный текст.

## Заключение

Теперь вы знаете, как **генерировать шаблоны документов**, **заполнять шаблоны Word** и **заполнять шаблоны docx** файлов, заменяя токены **как заменить заполнитель** реальными данными. Этот подход работает с любым количеством заполнителей и масштабируется на большие документы, если следовать рекомендациям по лучшим практикам.

### Что дальше?

* **Динамические таблицы:** Используйте `DocumentBuilder` для вставки строк на основе коллекций.  
* **Условные секции:** Скрывайте или показывайте части шаблона с помощью полей `IF`.  
* **Экспорт в PDF:** Вызовите `doc.Save("output.pdf")`, чтобы создать PDF‑версию заполненного документа.  

Экспериментируйте с этими вариантами, чтобы построить полнофункциональный движок генерации документов для счетов, контрактов или любых повторяющихся отчётов.

---

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Документ Word — поиск и замена текста](/words/english/net/find-and-replace-text/)
- [Создание документа Word](/words/english/java/word-processing/generate-word-document/)
- [Восстановление повреждённого DOCX — открыть и загрузить документ Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}