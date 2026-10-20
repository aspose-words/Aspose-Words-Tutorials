---
category: general
date: 2026-08-07
description: Сравнивайте документы Word в C# с помощью Aspose.Words. Узнайте, как
  сравнивать файлы docx, генерировать отчёт о сравнении и эффективно обрабатывать
  исправления.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- compare word documents
- word document comparison
- how to compare docx
- compare docx files
- compare word files
language: ru
lastmod: 2026-08-07
og_description: Сравнивайте документы Word в C# с помощью Aspose.Words. Этот учебник
  показывает, как сравнивать файлы docx, включать исправления и сохранять подробный
  отчёт для проверки.
og_image_alt: Comparison report when you compare word documents using Aspose.Words
og_title: Сравнение Word‑документов в C# с Aspose.Words – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Compare word documents in C# with Aspose.Words. Learn how to compare
    docx files, generate a comparison report, and handle revisions efficiently.
  headline: Compare word documents in C# using Aspose.Words
  type: TechArticle
- description: Compare word documents in C# with Aspose.Words. Learn how to compare
    docx files, generate a comparison report, and handle revisions efficiently.
  name: Compare word documents in C# using Aspose.Words
  steps:
  - name: '**Define comparison options** – decide whether to show revisions, ignore
      formatting, etc.'
    text: '**Define comparison options** – decide whether to show revisions, ignore
      formatting, etc.'
  - name: '**Execute the comparison** – the library returns a `ComparisonResult` object.'
    text: '**Execute the comparison** – the library returns a `ComparisonResult` object.'
  - name: '**Save the report** – the result can be saved as a new `.docx` that highlights
      insertions, deletions, and moves.'
    text: '**Save the report** – the result can be saved as a new `.docx` that highlights
      insertions, deletions, and moves.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Comparison
- docx
title: Сравнение документов Word в C# с помощью Aspose.Words
url: /ru/net/compare-documents/compare-word-documents-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сравнение Word‑документов в C# с помощью Aspose.Words

Если вам нужно **сравнивать Word‑документы** программно, Aspose.Words делает это простым. В этом руководстве показано, **как сравнивать docx** файлы, генерировать отчет о сравнении и настраивать параметры, такие как отображение правок.

Сравнение документов является распространённой потребностью для юридических проверок, переговоров по контрактам и версионирования контента. К концу этого руководства вы сможете:

* Загрузить два файла `.docx` и выполнить **сравнение Word‑документов**.  
* Включать или исключать правки в выводе.  
* Сохранить результат в новый Word‑файл, выделяющий изменения.  

Внешние сервисы не требуются — всё работает локально в приложении .NET.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 или новее установлен.  
* Лицензионная копия **Aspose.Words for .NET** (бесплатная пробная версия подходит для тестирования).  
* Два Word‑файла (`Original.docx` и `Modified.docx`), размещённые в известном каталоге.  

Если вы ещё не добавили Aspose.Words в свой проект, выполните:

```bash
dotnet add package Aspose.Words
```

## Сравнение Word‑документов — общий рабочий процесс

Процесс сравнения состоит из трёх логических шагов:

1. **Define comparison options** – определить, показывать ли правки, игнорировать форматирование и т.д.  
2. **Execute the comparison** – библиотека возвращает объект `ComparisonResult`.  
3. **Save the report** – результат можно сохранить в новый `.docx`, выделяющий вставки, удаления и перемещения.

Ниже приведён полный, исполняемый пример, следущий этим шагам.

```csharp
using Aspose.Words.LowCode;

namespace DocumentComparisonDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Define comparison options (e.g., include revisions in the result)
            ComparisonOptions comparisonOptions = new ComparisonOptions
            {
                ShowRevisions = true // Show insertions/deletions as tracked changes
            };

            // Step 2: Compare the original and modified documents
            // This is the core of the word document comparison.
            ComparisonResult comparisonResult = Comparer.Compare(
                "YOUR_DIRECTORY/Original.docx",   // path to the original file
                "YOUR_DIRECTORY/Modified.docx",   // path to the modified file
                comparisonOptions);

            // Step 3: Save the comparison report
            // The report will be a new .docx that visually marks all differences.
            comparisonResult.SaveReport("YOUR_DIRECTORY/ComparisonReport.docx");

            // Optional: Inform the user that the process completed.
            System.Console.WriteLine("Comparison report created successfully.");
        }
    }
}
```

### Почему важна каждая часть

* **ComparisonOptions** – управляет детализацией сравнения. Установка `ShowRevisions = true` имитирует встроенный в Word режим «Отслеживание изменений», что необходимо рецензентам, которым нужно видеть каждое исправление.  
* **Comparer.Compare** – выполняет основную работу. Метод читает оба исходных файла, строит внутреннюю модель различий и возвращает `ComparisonResult`.  
* **SaveReport** – записывает новый `.docx`, содержащий различия в виде отслеживаемых правок, что упрощает открытие в Microsoft Word или любом совместимом просмотрщике.

## Параметры сравнения Word‑документов

Aspose.Words предоставляет несколько дополнительных флагов, которые можно комбинировать с `ComparisonOptions`:

| Option | Description | Typical use case |
|--------|-------------|------------------|
| `ShowRevisions` | Сохраняет изменения как отслеживаемые правки. | Юридические команды, проверяющие правки в контрактах. |
| `IgnoreFormatting` | Игнорирует различия в шрифте, стиле или интервале. | Сравнение только содержимого, где макет не важен. |
| `IgnoreHeadersFooters` | Пропускает изменения в верхних/нижних колонтитулах. | Когда важен только основной текст. |
| `IgnoreCaseChanges` | Считает изменения регистра одинаковыми. | Черновики, где регистр не имеет значения. |

Вы можете включить несколько опций так:

```csharp
ComparisonOptions options = new ComparisonOptions
{
    ShowRevisions = true,
    IgnoreFormatting = true,
    IgnoreHeadersFooters = true
};
```

## Как сравнивать docx‑файлы с правками

Когда необходимо **сравнивать docx‑файлы** и сохранять полный журнал изменений, флаг `ShowRevisions` незаменим. Полученный отчет будет содержать встроенные в Word индикаторы изменений, что делает его сразу узнаваемым для конечных пользователей.

```csharp
ComparisonOptions revOptions = new ComparisonOptions { ShowRevisions = true };
ComparisonResult revResult = Comparer.Compare("A.docx", "B.docx", revOptions);
revResult.SaveReport("RevisionReport.docx");
```

Откройте `RevisionReport.docx` в Microsoft Word, и вы увидите вставки, выделенные зелёным, и удаления, выделенные красным, точно так же, как при использовании встроенной функции Word «Сравнить».

## Сравнение docx‑файлов пакетно

Если у вас есть множество пар документов для оценки, оберните логику сравнения в цикл:

```csharp
string[] originals = Directory.GetFiles("Originals", "*.docx");
string[] modified  = Directory.GetFiles("Modified", "*.docx");

for (int i = 0; i < originals.Length; i++)
{
    var result = Comparer.Compare(originals[i], modified[i], comparisonOptions);
    string reportPath = Path.Combine("Reports", $"Report_{i + 1}.docx");
    result.SaveReport(reportPath);
    Console.WriteLine($"Report {i + 1} saved.");
}
```

Этот шаблон позволяет **сравнивать docx‑файлы** в больших партиях без ручного вмешательства.

## Сравнение Word‑файлов — лучшие практики и подводные камни

* **File paths must be absolute or relative to the running process.** Использование относительного пути, например `"YOUR_DIRECTORY/Original.docx"`, работает, когда рабочий каталог установлен правильно; в противном случае используйте `Path.GetFullPath`.  
* **Large documents (>100 MB) can consume significant memory.** Рассмотрите возможность потоковой передачи файлов или увеличения лимита памяти процесса, если возникает `OutOfMemoryException`.  
* **Ensure both files use the same docx version.** Смешивание более старых файлов `.doc` может привести к неожиданным результатам; сначала конвертируйте их в `.docx` с помощью `Document.Save(..., SaveFormat.Docx)`.  
* **When `ShowRevisions` is false, the result is a clean document without change markers.** Используйте этот режим, если нужен только сводный список различий (например, текстовый diff‑отчёт).  

## Ожидаемый результат

После выполнения примера кода вы найдете `ComparisonReport.docx` в целевой папке. Открывая его в Word, вы увидите:

* **Insertions** – выделены зелёным с левой полосой изменений.  
* **Deletions** – отображаются красным зачёркнутым текстом.  
* **Moved text** – указано двойным стрелочным маркером.

![Отчёт сравнения, показывающий различия между оригинальным и изменённым документами](comparison-report.png "Отчёт сравнения при сравнении Word‑документов с помощью Aspose.Words")

*Изображение выше иллюстрирует типичное оформление отчёта сравнения, созданного кодом.*

## Заключение

Теперь вы знаете, как **сравнивать Word‑документы** в C# с помощью Aspose.Words, от настройки параметров сравнения до создания аккуратного отчёта, выделяющего каждое изменение. Этот подход работает как для отдельных пар файлов, так и для пакетных операций, и вы можете настроить сравнение, чтобы игнорировать форматирование, колонтитулы или изменения регистра по необходимости.

Следующие шаги, которые вы можете изучить:

* Интегрировать процедуру сравнения в веб‑API, чтобы пользователи могли загружать два файла и мгновенно получать отчёт.  
* Сочетать **compare docx files** с SharePoint или OneDrive для автоматизированного управления документами.  
* Использовать API `ComparisonResult` для извлечения текстового сводного отчёта о различиях для журналирования или уведомлений.

Освоив эти техники, вы сможете автоматизировать рабочие процессы проверки документов и сократить ручные усилия.

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Сравнение параметров в Word‑документе](/words/english/net/compare-documents/compare-options/)
- [Сравнение на равенство в Word‑документе](/words/english/net/compare-documents/compare-for-equal/)
- [Как сравнить два Word‑файла с помощью Aspose.Words для Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}