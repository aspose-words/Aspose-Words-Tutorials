---
category: general
date: 2026-05-04
description: Как использовать LLM для редактирования документов с Aspose — узнайте,
  как заменять текст абзаца, подключать локальный LLM и переписывать текст с помощью
  ИИ.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: ru
og_description: Как использовать LLM для редактирования документов с помощью Aspose.
  Это руководство показывает, как подключиться к локальному LLM, заменить текст абзаца
  и переписать текст с использованием ИИ.
og_title: Как использовать LLM с Aspose.Words – переписать абзацы на C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Как использовать LLM с Aspose.Words — переписывать абзацы на C#
url: /ru/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как использовать LLM с Aspose.Words – Переписать абзацы на C#

Когда‑то задумывались **как использовать LLM**, чтобы полировать документ Word, не открывая его вручную? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда нужно *заменить текст абзаца* программно, но нет чистого AI‑ориентированного рабочего процесса.  

В этом руководстве мы подключим локальную большую языковую модель, передадим ей фрагмент из файла `.docx`, попросим **переписать текст с помощью ИИ**, а затем сохраним обновлённый документ — всё с помощью Aspose.Words. К концу вы получите готовое к запуску консольное приложение C#, демонстрирующее весь конвейер.

> **Что вы получите:** полностью готовый пример, объяснения каждого шага, советы по граничным случаям и идеи для расширения решения.

## Что понадобится

- **.NET 6+** (или .NET Framework 4.7.2 – код работает в обеих средах)
- **Aspose.Words for .NET** (NuGet‑пакет `Aspose.Words`)
- **Локальный сервер LLM**, предоставляющий простой HTTP‑эндпоинт `/generate` (например, Ollama, LMStudio или собственный Flask‑сервис)
- Базовое знакомство с C# и кодом HTTP‑клиента  

Дополнительные SDK не требуются; всё остальное находится в коде, который мы напишем вместе.

## Шаг 1: Как использовать LLM для замены текста абзаца

Первое, что нам нужно сделать – определить абзац, который будем изменять. Aspose.Words упрощает эту задачу, предоставляя богатую объектную модель.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Почему это важно:**  
Выбор правильного узла предотвращает случайную перезапись заголовков или таблиц. Используя подход **replace paragraph text**, мы сохраняем структуру документа, изменяя только нужный контент.

> **Совет профессионала:** Если в документе есть секции переменной длины, используйте `document.GetChildNodes(NodeType.Paragraph, true)` и LINQ, чтобы найти абзац по его тексту или стилю.

## Шаг 2: Подключение к локальному LLM эндпоинту

Теперь, когда у нас есть текст, нужно отправить его в LLM. В примере используется простой класс‑обёртка `LocalLargeLanguageModel`, скрывающий HTTP‑механику. При желании замените его вызовами `HttpClient`.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Почему мы подключаемся так:**  
Настройка **connect to local llm** устраняет задержки, сохраняет данные в пределах предприятия и избавляет от расходов на API. Обёртка также делает последующий код чище, позволяя сосредоточиться на логике **rewrite text using ai**.

## Шаг 3: Переписать текст с помощью ИИ в Aspose.Words

Имея текст абзаца и готовый LLM, формируем запрос, который точно указывает модели, что нужно – переписать в формальном тоне. При желании измените запрос для других стилей (дружелюбный, технический и т.д.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Почему это работает:**  
LLM работают на основе подсказок; чёткие инструкции («Rewrite … in a formal tone») дают предсказуемый результат. Шаг **rewrite text using ai** является сердцем руководства – он демонстрирует, как ИИ можно встроить непосредственно в рабочие процессы с документами.

## Шаг 4: Редактировать документ и сохранить изменения

Теперь заменяем оригинальные `Run`‑ы новым содержимым. Aspose.Words хранит текст в объектах `Run`, поэтому их предварительное очищение избавляет от оставшихся артефактов форматирования.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Примечание по граничному случаю:**  
Если исходный абзац содержал смешанное форматирование (жирный, курсив), возможно, понадобится сохранить стили. В этом случае создайте новый `Run`, скопируйте настройки оригинального `Font`, а затем задайте `Text` равным `revisedText`.

## Полный рабочий пример

Ниже представлен весь код программы, который можно скопировать в консольный проект. Не забудьте сначала установить NuGet‑пакет Aspose.Words (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Ожидаемый вывод

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Откройте `output.docx` – вы увидите, что третий абзац теперь содержит отшлифованную версию.

## Часто задаваемые вопросы и подводные камни

| Вопрос | Ответ |
|----------|--------|
| **Что делать, если мой LLM возвращает JSON с дополнительными полями?** | Скорректируйте `GenerateText`, чтобы десериализовать нужное свойство, или разберите ответ вручную. |
| **Можно ли обрабатывать несколько абзацев одновременно?** | Да – итеративно проходите `document.FirstSection.Body.Paragraphs` и применяйте ту же логику подсказки, возможно, добавив индекс абзаца в запрос для контекста. |
| **Мой LLM‑сервер требует аутентификации?** | Добавьте заголовок к `HttpClient` перед POST‑запросом: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **После замены форматирование теряется.** | Сохраните оригинальные настройки `Run.Font`: создайте новый `Run`, скопируйте `originalRun.Font.Clone()`, затем задайте его `Text`. |
| **LLM иногда возвращает пустые строки.** | Реализуйте резервный вариант – если `revisedText.Trim().Length == 0`, оставьте оригинальный текст или повторите запрос с более простой подсказкой. |

## Расширение решения

Теперь, когда вы освоили **как использовать llm** для одного абзаца, рассмотрите следующие шаги:

- **Пакетная обработка:** Пройдите по каждому абзацу и перепишите в выбранном стиле (например, «сделать весь текст лаконичным»).  
- **Переписывание с учётом стиля:** Передавайте в запрос название оригинального стиля абзаца, чтобы LLM учитывал различия между заголовками и основным текстом.  
- **Интеграция в CI‑конвейер:** Автоматизируйте полировку документов как часть процесса сборки документации.  
- **Альтернативные подсказки:** Попробуйте «summarize this paragraph» или «translate this paragraph to Spanish», чтобы исследовать весь потенциал **rewrite text using ai**.

## Заключение

Мы прошли весь процесс **как использовать llm** с Aspose.Words: загрузка документа, **connect to local llm**, извлечение абзаца, **rewrite text using ai**, **replace paragraph text** и, наконец, сохранение результата. Код автономный, работает «из коробки» и демонстрирует практический способ объединения ИИ с традиционной автоматизацией документов.

Попробуйте, поиграйте с подсказками, и дайте

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}