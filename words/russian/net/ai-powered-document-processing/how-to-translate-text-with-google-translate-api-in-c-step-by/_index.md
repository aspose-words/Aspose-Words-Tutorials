---
category: general
date: 2026-11-15
description: Узнайте, как переводить текст с помощью Google в C#. Этот учебник демонстрирует
  пример использования Google Translate, работу с несколькими языками и лучшие практики.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: ru
lastmod: 2026-11-15
og_description: Как переводить текст с помощью Google в C#, используя полный пример
  Google Translate. Следуйте этому руководству, чтобы безопасно переводить на несколько
  языков.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Как переводить текст с помощью Google Translate API в C# – быстрый учебник
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Как переводить текст с помощью Google Translate API в C# – пошаговое руководство
url: /ru/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как переводить текст с помощью Google Translate API на C# – пошаговое руководство

Если вам нужно **перевести текст** в .NET‑приложении, Google Cloud Translation API предлагает надёжное, независимое от языка решение. В этом руководстве вы увидите **пример использования Google Translate**, который переводит простую строку, расширяется до **перевода на несколько языков** и следует лучшим практикам работы с API‑ключами и обработкой ошибок.

Вы получите готовую к запуску консольную программу на C#, чёткое понимание **перевода текста с помощью Google**, и уверенность в адаптации кода для более крупных проектов.

## Что покрывает это руководство

* Настройка проекта Google Cloud и получение API‑ключа.  
* Установка пакета NuGet `Google.Cloud.Translation.V2`.  
* Написание чистого, переиспользуемого кода, который **переводит текст** с использованием официального SDK.  
* Расширение решения для **перевода на несколько языков** одним вызовом.  
* Распространённые подводные камни и советы для реализации в продакшн‑среде.

### Предварительные требования

* .NET 6.0 SDK или новее (код компилируется с .NET Core и .NET Framework).  
* Учётная запись Google Cloud с включённым **Cloud Translation API**.  
* Базовое знакомство с C# и консольными приложениями.  

---

## Шаг 1: Установить клиентскую библиотеку Google Cloud Translation

Официальная клиентская библиотека абстрагирует HTTP‑запросы и обрабатывает аутентификацию за вас.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Выполнение команды добавляет пакет `Google.Cloud.Translation.V2` в ваш проект, предоставляя доступ к классу `TranslationClient`, используемому во всём руководстве.

> **Почему этот шаг важен** – Использование SDK избавляет от ручного построения запросов, уменьшает количество ошибок и гарантирует соответствие последней версии API от Google.

## Шаг 2: Создать переиспользуемый помощник для перевода

Инкапсуляция логики перевода в статическом классе делает код переиспользуемым и изолирует работу с API‑ключом.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Почему мы возвращаем словарь** – Когда вам нужно **перевести на несколько языков**, организация результатов по коду языка упрощает последующую обработку.

## Шаг 3: Создать консольное приложение, использующее помощник

Ниже приведён полный `Program.cs`, демонстрирующий как перевод одиночного текста, так и пакетный перевод.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Ожидаемый вывод в консоли**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **Зачем блоки try/catch?** – Ошибки сети, ограничения квоты или недействительный API‑ключ вызывают исключения. Их корректная обработка улучшает пользовательский опыт и поддерживает стабильность приложения.

## Шаг 4: Защитить ваш API‑ключ

Жёсткое кодирование API‑ключа, как показано выше, приемлемо для быстрой демонстрации, но не для продакшна. Следуйте этим рекомендациям:

* Сохраните ключ в переменной окружения (`GOOGLE_API_KEY`) и считывайте её во время выполнения:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Используйте **Google Application Default Credentials** вместо API‑ключа при работе в Google Cloud (App Engine, Cloud Run и т.д.).
* Ограничьте ключ только API Translation в консоли Google Cloud и задайте ограничения по IP‑адресам или реферерам.

## Шаг 5: Расширить решение для реальных сценариев

### Обнаружение языка

Если необходимо узнать исходный язык, объект ответа содержит `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Перевод больших документов

API поддерживает до 30 KB за запрос. Для более длинных текстов разбейте содержимое на фрагменты, переведите каждый фрагмент и затем объедините результаты. Сохраняйте границы предложений, чтобы избежать неестественных формулировок.

### Ограничения по скорости и квоты

Google накладывает ограничения на количество запросов в минуту. Реализуйте политику повторных попыток с экспоненциальным увеличением задержки, чтобы соблюдать лимиты квоты и избегать ошибок `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Часто задаваемые вопросы и особые случаи

**Q: Можно ли перевести целую HTML‑страницу?**  
A: Да. Используйте параметр `Format` (`"text"` или `"html"`) при вызове `TranslateText`. SDK предоставляет это через перегрузку `TranslateText`, принимающую `TranslateTextRequest`.

**Q: Что делать, если язык не поддерживается?**  
A: API возвращает ошибку. Проверьте коды языков против списка, возвращаемого `client.ListSupportedLanguages()`, перед отправкой запроса.

**Q: Платит ли API за каждый символ?**  
A: Google взимает плату за каждый переведённый символ. Оцените расходы, используя страницу с ценами, и рассмотрите кэширование часто используемых переводов.

---

## Заключение

Теперь вы знаете **как переводить текст** в C# с использованием официального Google Translate API. Руководство охватило **пример использования Google Translate**, продемонстрировало **перевод на несколько языков** и выделило готовые к продакшну практики, такие как безопасность API‑ключа и обработка ошибок. Переиспользуя помощник `Translator`, вы можете интегрировать перевод в любой сервис .NET, настольное приложение или микросервис.

**Следующие шаги**

* Изучите **Google Translate tutorial** для расширенных возможностей, таких как глоссарии и пользовательские модели.  
* Объедините этот код с ASP.NET Core для создания многоязычного веб‑API.  
* Поэкспериментируйте с пакетным переводом CSV‑файлов для автоматизации процессов локализации.

Удачной разработки и приятного создания глобально доступных приложений!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [перевести docx на французский с Aspose.Words и Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Как сохранить переведённый документ Word в C# с Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Перевести строку на испанский в C# с Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}