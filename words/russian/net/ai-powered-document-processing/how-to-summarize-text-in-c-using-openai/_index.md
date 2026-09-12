---
category: general
date: 2026-09-11
description: Узнайте, как суммировать текст на C#, считывая API‑ключ, вызывая OpenAI
  и генерируя краткое резюме документа Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: ru
lastmod: 2026-09-11
og_description: Как суммировать текст в C#? Этот учебник покажет, как прочитать API‑ключ,
  вызвать OpenAI и создать резюме Word‑документа.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Как суммировать текст в C# с помощью OpenAI – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: Как резюмировать текст в C# с помощью OpenAI
url: /ru/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как суммировать текст в C# с использованием OpenAI

Если вам нужно **how to summarize text** в файле .docx, это руководство покажет вам полное готовое к запуску решение. Вы узнаете, как прочитать API‑ключ из вашей среды, как вызвать OpenAI (или Google) из C#, и как создать лаконичное резюме Word‑документа.

Создание резюме Word‑документа — распространённая задача для генерации отчётов, дайджестов по электронной почте или извлечения знаний из базы. К концу этого руководства у вас будет консольная программа, выводящая пяти‑предложное резюме любого предоставленного вами файла `.docx`.

## Требования

- .NET 6.0 SDK или новее (скачать с [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Действительный OpenAI API‑ключ, сохранённый в переменной окружения с именем `OPENAI_API_KEY` (вы увидите **read api key** в действии)
- Пакет NuGet `DocumentFormat.OpenXml` для чтения файлов `.docx`
- Пакет NuGet `OpenAI` (или `Google.AI`, если вы предпочитаете провайдера Google)

## Шаг 1: Настройка проекта и установка зависимостей

Создайте новый консольный проект и добавьте необходимые пакеты:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** Держите ваш `csproj` аккуратным, группируя связанные пакеты внутри `<ItemGroup>`, если позже добавите дополнительные зависимости.

## Шаг 2: Безопасное чтение API‑ключа

Жёсткое кодирование секретов небезопасно. В руководстве показан правильный способ **read api key** из переменных окружения.

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## Шаг 3: Загрузка Word‑документа, который нужно суммировать

Код ниже демонстрирует **how to summarize word document** содержимое, извлекая простой текст из структуры OpenXML.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## Шаг 4: Создание переиспользуемого класса‑суммаризатора

Этот класс инкапсулирует **how to call openai** (или Google) и реализует логику **how to create summary**. Он также позволяет переключать провайдеры одним значением enum.

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### Почему эта структура важна

- **Separation of concerns:** Загрузка документа, чтение API‑ключа и вызов AI‑сервиса изолированы в отдельные методы. Это упрощает тестирование и расширение кода.
- **Provider flexibility:** Используя enum, вы можете переключаться между OpenAI и Google, не меняя вызывающий код, что напрямую отвечает на **how to call openai** и **how to create summary** в переиспользуемом виде.
- **Error handling:** Отсутствие API‑ключей вызывает чёткое исключение, предотвращая тихие сбои.

## Шаг 5: Сборка всего вместе в `Program.cs`

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### Ожидаемый вывод

Запуск программы с примерным документом:

```bash
dotnet run -- "sample/input.docx"
```

может вывести:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Шаг 6: Распространённые варианты и граничные случаи

| Ситуация | Рекомендуемая корректировка |
|-----------|----------------------------|
| **Large documents** ( > 10 KB ) | Разбейте текст на фрагменты и суммируйте каждый фрагмент, затем объедините результаты. |
| **Non‑English content** | Передайте подсказку о языке в запросе, например: “Summarize the following French text …”. |
| **Google provider** | Замените вызов `SummarizeWithOpenAIAsync` на соответствующий клиент Google API; сохраните тот же интерфейс enum. |
| **Custom summary length** | Измените аргумент `maxSentences` при вызове `SummarizeAsync`. |
| **Missing API key** | Метод `GetOpenAIApiKey` уже бросает чёткое исключение; перехватите его в `Main`, если хотите более дружелюбное сообщение. |

## Советы для продакшн‑использования

1. **Cache the API key** – чтение из переменной окружения при каждом вызове добавляет незначительные накладные расходы, но вы можете сохранить его в статическом readonly поле, если вызываете суммаризатор многократно в одном процессе.
2. **Rate‑limit requests** – OpenAI ограничивает количество запросов; реализуйте экспоненциальную задержку при получении `429 Too Many Requests`.
3. **Sanitize input** – удаляйте персональные данные перед отправкой текста во внешнюю AI‑службу.
4. **Unit test the extraction logic** – замокайте `WordprocessingDocument`, чтобы проверить работу `ExtractTextFromDocx` с различными структурами документов.

## Заключение

Теперь вы знаете **how to summarize text** в C#, безопасно читая API‑ключ, вызывая OpenAI и генерируя лаконичное резюме Word‑документа. Та же схема позволяет вам **how to call openai** с другими провайдерами, **how to create summary** логику для разных типов контента и безопасно **read api key** значения из окружения. Экспериментируйте с более длинными документами, различными провайдерами или пользовательскими подсказками, чтобы адаптировать суммирование под ваш конкретный домен.

---

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, основанные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Суммировать Word‑документ в C# с помощью Aspose.Words API – Полное руководство с ИИ](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [как создать pdf из Word – Полное руководство C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word Document - Как удалить содержимое](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}