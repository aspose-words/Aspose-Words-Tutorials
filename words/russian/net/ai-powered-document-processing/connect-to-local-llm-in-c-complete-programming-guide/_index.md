---
category: general
date: 2026-04-28
description: Подключитесь к локальной LLM из C# и попросите большую языковую модель
  загрузить документ Word, вызвать локальную LLM и автоматически переписать текст.
  Пошаговый код включён.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: ru
og_description: Подключитесь к локальной LLM из C# и узнайте, как задавать запросы
  большой языковой модели, загружать документ Word, вызывать локальную LLM и автоматически
  переписывать текст за несколько минут.
og_title: Подключение к локальному LLM на C# — Полное руководство по программированию
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Подключение к локальному LLM в C# — Полное руководство по программированию
url: /ru/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Подключение к локальному LLM в C# – Полное руководство по программированию

Когда‑нибудь вам нужно было **connect to local llm** из .NET‑приложения и вы задавались вопросом, как заставить его работать с файлом Word? Вы не одиноки. В этом руководстве мы пройдем весь процесс — подключение к локальному llm, **prompt large language model**, загрузка документа Word, **call local llm**, и, наконец, **rewrite text automatically**. К концу у вас будет готовый пример, который преобразует любой абзац в формальный стиль без использования внешних API‑ключей.

## Что покрывает этот учебник

Мы начнём с установки необходимых пакетов NuGet, затем запустим простой локальный LLM‑endpoint (например, Ollama на порту 11434). После этого мы загрузим файл `.docx` с помощью Aspose.Words, отправим абзац в LLM, получим переписанную версию и запишем её обратно в тот же документ. Вы также увидите, как справляться с распространёнными подводными камнями — пустыми абзацами, асинхронным освобождением ресурсов и особенностями кодировки — чтобы код работал в продакшене, а не только в демонстрации.

### Требования

- .NET 6.0 SDK или новее (можно также использовать .NET 8, если хотите)
- Visual Studio 2022 или VS Code с расширением C#
- **Aspose.Words for .NET** (бесплатная пробная версия подходит)
- Локально развернутый LLM, поддерживающий контракт `/api/generate` (например, Ollama, LMStudio)
- Базовое знакомство с async/await в C#

> **Pro tip:** Если вы ещё не установили Ollama, запустите `ollama serve` и загрузите модель командой `ollama pull llama3`. По умолчанию HTTP‑endpoint будет `http://localhost:11434/api/generate`.

---

## Шаг 1: Установите необходимые пакеты

Сначала добавьте пакеты NuGet Aspose.Words и Aspose.Words.AI в ваш проект.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Эти библиотеки предоставляют возможность **load word document** и лёгкую обёртку для **call local llm** без ручного формирования HTTP‑запросов.

---

## Шаг 2: Подключитесь к локальному LLM‑endpoint

Подключение к локально развернутой модели так же просто, как создание экземпляра `LocalLargeLanguageModel`. Конструктор ожидает полный URL endpoint‑а генерации.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Зачем мы оборачиваем endpoint в класс? `LocalLargeLanguageModel` обрабатывает сериализацию JSON, повторные попытки и потоковые ответы за вас — так что вы можете сосредоточиться на логике подсказки, а не возиться с `HttpClient`.

---

## Шаг 3: Загрузите исходный документ Word

Далее мы загружаем документ в память. Aspose.Words поддерживает практически любой формат Word, поэтому `Document` разберёт `input.docx` без необходимости установки Office.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Если вам нужно работать со стримом (например, файл, загруженный через ASP.NET), просто замените путь к файлу на `MemoryStream` и передайте его в конструктор `Document`.

---

## Шаг 4: Извлеките текущий текст абзаца

Мы будем использовать `DocumentBuilder` для навигации по документу. В этом примере мы переписываем **the first paragraph**, но вы можете перебрать `sourceDocument.GetChildNodes(NodeType.Paragraph, true)`, чтобы обработать их множество.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

Оператор `?.` предотвращает `NullReferenceException`, если документ окажется пустым. Это один из тех **edge cases**, которые ставят в тупик новичков.

---

## Шаг 5: Подайте запрос LLM для переписывания абзаца

Теперь мы действительно **prompt large language model**. Подсказка написана простым английским; обёртка отправит её как JSON на локальный endpoint.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Почему запрос сформулирован именно так? LLM лучше реагируют на чёткие, одно‑задачные инструкции. Добавление новой строки после двоеточия отделяет инструкцию от содержимого, уменьшая вероятность того, что модель просто повторит подсказку.

**Expected output** – Если `originalParagraph` было `"Hey, what's up?"`, LLM может вернуть:

> “Good day, how may I assist you?”

Вы можете проверить результат, выведя его на печать:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Шаг 6: Вставьте переписанный текст обратно в документ

Имея новый текст, мы заменяем старый абзац. `DocumentBuilder.Writeln` пишет новую строку и перемещает курсор вперёд, что идеально подходит для добавления. Если вам нужно *replace* тот же самый абзац, вы можете вызвать `docBuilder.CurrentParagraph.RemoveAllChildren()` перед записью.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Оба подхода показаны, чтобы вы могли выбрать тот, который соответствует вашему рабочему процессу.

---

## Шаг 7: Сохраните обновлённый документ

Наконец, мы сохраняем изменения в новый файл. Aspose.Words автоматически выбирает формат на основе расширения файла.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Откройте `output.docx` в Word, и вы увидите, что абзац теперь написан в формальном тоне.

---

## Полный рабочий пример

Ниже представлен **complete, self‑contained program**. Скопируйте‑вставьте его в консольный проект, восстановите пакеты NuGet и запустите — никаких дополнительных настроек не требуется, кроме работающего локального LLM.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Что ожидать при запуске

1. Консоль выводит оригинальный и переписанный абзацы.  
2. `output.docx` появляется рядом с `input.docx`.  
3. При открытии файла новый формальный абзац вставлен после оригинального (или заменён, если вы переключились на альтернативный код).

---

## Обработка распространённых edge cases

| Situation | Solution |
|-----------|----------|
| **Empty or whitespace‑only paragraph** | Проверьте `string.IsNullOrWhiteSpace` перед отправкой подсказки (см. Шаг 3). |
| **LLM returns an error or empty string** | Оберните `PromptAsync` в `try/catch` и вернитесь к оригинальному тексту в случае ошибки. |
| **Multiple paragraphs need rewriting** | Пройдите в цикле `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` и примените ту же логику подсказки. |
| **Large documents cause latency** | Группируйте абзацы и отправляйте их одним запросом (подсказка до 4 KB за вызов). |
| **Non‑ASCII characters get garbled** | Убедитесь, что endpoint LLM использует UTF-8 (это делают большинство современных моделей). |

---

## Следующие шаги и связанные темы

- **Prompt large language model** с более подробными инструкциями (например, руководства по стилю, ограничения по длине).  
- Используйте **call local llm** в веб‑API, чтобы предоставить автоматизацию документов как сервис.  
- Исследуйте **load word document** в параллельных потоках для сценариев с высокой пропускной способностью.  
- Скомбинируйте этот подход с **rewrite text automatically** для массовой генерации писем или стандартизации отчетов.  

Если хотите углубиться, ознакомьтесь с документацией Aspose по **document merging** и справочником API Ollama для настройки параметров сэмплинга.

---

## Заключение

Мы только что продемонстрировали, как **connect to local llm** из C#, **prompt large language model**, **load word document**, **call local llm** и **rewrite text automatically** — всё в одном готовом к запуску консольном приложении. Этот подход масштабируется: меняйте подсказку, перебирайте абзацы или открывайте логику через endpoint ASP.NET. Главный вывод — локальные AI‑модели могут быть тесно интегрированы с классическими библиотеками обработки документов, предоставляя мощную автоматизацию, не покидая надёжную on‑prem среду.

Есть вопросы по потокам,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}