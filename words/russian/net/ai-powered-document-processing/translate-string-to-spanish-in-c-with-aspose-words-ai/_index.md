---
category: general
date: 2026-08-23
description: Переведите строку на испанский в C# с использованием Aspose.Words AI
  Translator и провайдера Google. Следуйте пошаговому руководству, чтобы быстро перевести
  строку в C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: ru
lastmod: 2026-08-23
og_description: Перевести строку на испанский в C# с помощью Aspose.Words AI. Этот
  учебник показывает, как настроить провайдера Google, перевести строку и отобразить
  результат.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: Перевести строку на испанский в C# – полный пример кода
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: Перевести строку на испанский в C# с помощью Aspose.Words AI
url: /ru/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Перевод строки на испанский в C# с помощью Aspose.Words AI

Если вам нужно **перевести строку на испанский** в приложении .NET, это руководство покажет, как это сделать. Вы увидите полный, исполняемый пример, который создает переводчик, вызывает сервис Google и выводит испанский текст.

В руководстве также рассматривается **перевод строки в C#** с использованием библиотеки Aspose.Words AI, что позволяет интегрировать локализацию непосредственно в ваш код без внешних скриптов.

## Что понадобится

- .NET 6.0 SDK или новее (код компилируется с .NET Core и .NET Framework)
- Активный ключ Google Cloud Translation API
- Пакет NuGet `Aspose.Words.AI` (установить с помощью `dotnet add package Aspose.Words.AI`)
- Редактор кода или IDE, например Visual Studio 2022

Эти предварительные требования гарантируют, что пример работает сразу же.

## Перевод строки на испанский с Aspose.Words AI

В этом разделе создаётся объект `Translator`, настроенный для провайдера Google. Провайдер обрабатывает HTTP‑запрос к конечной точке перевода Google.

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**Почему это работает:**  
- `Translator` абстрагирует HTTP‑вызов, обрабатывая аутентификацию с предоставленным вами API‑ключом.  
- `TranslationProvider.Google` указывает SDK направлять запрос в Google Cloud Translation.  
- `Language.Spanish` выбирает код целевого языка (`es`).  
- Метод `Translate` возвращает переведённую строку, которую можно использовать в любой части приложения.

## Настройка провайдера перевода Google

1. **Получите API‑ключ** в Google Cloud Console → APIs & Services → Credentials.  
2. **Включите Cloud Translation API** для вашего проекта.  
3. Сохраните ключ безопасно (переменная окружения, менеджер секретов и т.д.). В примере используется литерал для наглядности, но в продакшн‑коде следует избегать жёсткого кодирования секретов.

## Перевод строки в C# – пошагово

| Шаг | Действие | Причина |
|------|--------|--------|
| 1 | Создать экземпляр `Translator` с `TranslationProvider.Google` | Подключает SDK к сервису Google |
| 2 | Вызвать `Translate(source, Language.Spanish)` | Отправляет исходный текст и получает результат на испанском |
| 3 | Вывести результат с помощью `Console.WriteLine` | Проверяет перевод и демонстрирует использование |

Running the program prints:

```
¡Hola mundo!
```

> **Примечание:** Точный вывод может немного отличаться в зависимости от модели перевода Google (например, “Hola mundo” vs. “¡Hola mundo!”). Оба варианта являются корректными эквивалентами на испанском.

## Запуск и проверка вывода

1. Откройте терминал в папке проекта.  
2. Выполните `dotnet run`.  
3. Убедитесь, что консоль отображает испанскую фразу.

Если в консоли появляется ошибка, например *“401 Unauthorized”*, проверьте, что API‑ключ правильный и что Cloud Translation API включён для проекта.

## Распространённые подводные камни и лучшие практики

- **Ограничения квоты API** – Google ограничивает количество запросов на счёт‑фактурный аккаунт. Следите за использованием в Cloud Console, чтобы избежать неожиданного ограничения.  
- **Сетевая задержка** – Вызовы перевода являются удалёнными HTTP‑запросами. Рассмотрите кэширование часто переводимых строк для снижения задержки.  
- **Проблемы кодировки** – SDK работает со строками UTF‑8; убедитесь, что ваши исходные файлы сохранены в кодировке UTF‑8, чтобы сохранить специальные символы.  
- **Обработка ошибок** – Оберните вызов `Translate` в блок try‑catch, чтобы обрабатывать `ApiException` и предоставлять запасной текст.

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## Расширение примера

- **Перевод на другие языки** – Замените `Language.Spanish` на `Language.French`, `Language.German` и т.д.  
- **Пакетный перевод** – Вызывайте `Translate` внутри цикла для обработки списка строк.  
- **Интеграция с UI** – Используйте переведённую строку в страницах ASP.NET Core Razor, Windows Forms или приложениях WPF.

## Заключение

Теперь вы знаете, как **перевести строку на испанский** в C# с помощью Aspose.Words AI и сервиса Google Translation. Полное решение охватывает настройку провайдера, вызов перевода, обработку ошибок и проверку вывода.

Отсюда экспериментируйте с дополнительными языками, кэшируйте результаты для повышения производительности и интегрируйте переводчик в более крупные конвейеры локализации.

--- 

*Готовы локализовать больше контента? Ознакомьтесь с следующим руководством по **переводу строки в C# с Azure Cognitive Services** для альтернативного облачного провайдера.*

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и изучить альтернативные подходы к реализации в ваших проектах.

- [Заменить строкой](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [Заменить строкой](/words/english/net/find-and-replace-text/replace-with-string/)
- [Создать документ Word с Aspose.Words – пошаговое руководство](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}