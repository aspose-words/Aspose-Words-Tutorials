---
category: general
date: 2026-11-18
description: Узнайте, как переводить файлы docx на французский с помощью Google AI,
  переводить весь документ и сохранять переведённый документ всего за три шага.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- google ai translation
- translate entire document
- save translated document
- how to translate docx
language: ru
lastmod: 2026-11-18
og_description: Мгновенно переводите DOCX на французский с помощью Google AI Translation.
  Следуйте этому руководству, чтобы перевести весь документ и без усилий сохранить
  переведённый файл.
og_image_alt: Screenshot showing a DOCX file translated to French using Google AI
og_title: Перевести docx на французский с помощью Google AI — краткое руководство
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  headline: How to translate docx to French using Google AI
  type: TechArticle
- description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  name: How to translate docx to French using Google AI
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the NuGet packages that the tutorial relies on:'
    text: 'Add the NuGet packages that the tutorial relies on:'
  - name: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
    text: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
  type: HowTo
tags:
- C#
- Google AI
- Document translation
- Localization
title: Как перевести docx на французский с помощью Google AI
url: /ru/net/ai-powered-document-processing/how-to-translate-docx-to-french-using-google-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как переводить docx на французский с помощью Google AI

Если вам нужно **перевести docx на французский**, перевод Google AI позволяет выполнить перевод всего документа всего несколькими строками кода C#. В этом руководстве показано, как именно перевести файл DOCX, перевести содержимое всего документа и сохранить переведённый документ надёжным способом.

Вы узнаете, как настроить клиент Google Cloud Translation, загрузить файл Word, вызвать API для перевода каждого абзаца и, наконец, выполнить шаг **save translated document**. Никакие внешние скрипты или ручное копирование‑вставка не требуются — всё работает внутри вашего .NET‑приложения.

## Что вам понадобится

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия  
* Проект в Google Cloud с включённым **Cloud Translation API**  
* Файл JSON‑ключа сервисного аккаунта (скачанный из консоли Google Cloud)  
* Visual Studio 2022 (или любой другой предпочитаемый IDE для C#)  

Эти предварительные условия гарантируют успешный вызов **google ai translation** и позволяют читать/писать файлы DOCX с помощью Open XML SDK.

## Настройка проекта и установка необходимых SDK

1. Создайте новый консольный проект:

   ```bash
   dotnet new console -n DocxFrenchTranslator
   cd DocxFrenchTranslator
   ```

2. Добавьте NuGet‑пакеты, от которых зависит руководство:

   ```bash
   dotnet add package Google.Cloud.Translate.V3
   dotnet add package DocumentFormat.OpenXml
   ```

   *`Google.Cloud.Translate.V3`* предоставляет клиент **google ai translation**, а *`DocumentFormat.OpenXml`* позволяет работать с файлами DOCX без установки Microsoft Office.

3. (Опционально) Если вы предпочитаете более высокий уровень абстракции, можно также установить `GroupDocs.Translator`:

   ```bash
   dotnet add package GroupDocs.Translator
   ```

   Приведённые ниже примеры кода работают с любым из подходов; версия с Open XML показана полностью для прозрачности.

## Загрузка исходного файла DOCX

Первый практический шаг — прочитать Word‑документ, который требуется перевести. С помощью Open XML SDK можно извлечь текст каждого абзаца в список.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Reads all paragraph texts from a DOCX file.
    /// </summary>
    public static class DocxReader
    {
        public static List<string> GetParagraphs(string path)
        {
            var paragraphs = new List<string>();

            using (WordprocessingDocument wordDoc = WordprocessingDocument.Open(path, false))
            {
                Body body = wordDoc.MainDocumentPart.Document.Body;
                foreach (Paragraph para in body.Elements<Paragraph>())
                {
                    paragraphs.Add(para.InnerText);
                }
            }

            return paragraphs;
        }
    }
}
```

**Почему это важно:** Загрузка файла один раз и хранение текста в памяти позволяет **translate entire document** одним вызовом API на каждый абзац, избегая повторных операций ввода‑вывода.

## Выполнение перевода Google AI

Теперь, когда у вас есть оригинальные абзацы, вызовите Translation API, чтобы преобразовать каждую строку с английского (или любого исходного языка) на французский. Клиент автоматически определяет исходный язык, если передать `null`.

```csharp
using Google.Cloud.Translate.V3;
using System.Collections.Generic;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Handles translation using Google Cloud Translation (v3).
    /// </summary>
    public static class Translator
    {
        private static readonly TranslationServiceClient client;

        static Translator()
        {
            // The GOOGLE_APPLICATION_CREDENTIALS environment variable should point to your JSON key.
            client = TranslationServiceClient.Create();
        }

        /// <summary>
        /// Translates a list of strings to French.
        /// </summary>
        public static async Task<List<string>> TranslateToFrenchAsync(List<string> texts)
        {
            var request = new TranslateTextRequest
            {
                Parent = $"projects/{client.ProjectId}/locations/global",
                TargetLanguageCode = "fr",
                // SourceLanguageCode can be omitted for auto‑detection.
            };

            // Add all texts to the request.
            request.Contents.AddRange(texts);

            // Execute the translation.
            TranslateTextResponse response = await client.TranslateTextAsync(request);

            var translated = new List<string>();
            foreach (Translation translation in response.Translations)
            {
                translated.Add(translation.TranslatedText);
            }

            return translated;
        }
    }
}
```

**Почему это важно:** Использование **google ai translation** в пакетном запросе снижает задержку и стоимость по сравнению с циклами «один вызов — один абзац». Метод также демонстрирует **how to translate docx** программно.

## Создание нового DOCX с переведённым текстом

После получения французских строк запишите их обратно в новый файл DOCX. Ниже представлена вспомогательная класс, который собирает новый документ из переведённых абзацев.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Writes a list of paragraphs to a new DOCX file.
    /// </summary>
    public static class DocxWriter
    {
        public static void Write(string outputPath, List<string> frenchParagraphs)
        {
            // Ensure the directory exists.
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath)!);

            // Create a new document.
            using (WordprocessingDocument wordDoc = WordprocessingDocument.Create(outputPath, DocumentFormat.OpenXml.WordprocessingDocumentType.Document))
            {
                MainDocumentPart mainPart = wordDoc.AddMainDocumentPart();
                mainPart.Document = new Document();
                Body body = mainPart.Document.AppendChild(new Body());

                foreach (string paraText in frenchParagraphs)
                {
                    Paragraph para = new Paragraph(new Run(new Text(paraText)));
                    body.AppendChild(para);
                }

                mainPart.Document.Save();
            }
        }
    }
}
```

## Собираем всё вместе — полная программа

Ниже полностью готовое консольное приложение, которое объединяет предыдущие фрагменты. Оно демонстрирует **translate docx to french**, выполняет **google ai translation** и, наконец, **save translated document**.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    class Program
    {
        static async Task Main(string[] args)
        {
            // ------------------------------------------------------------------
            // 1️⃣ Load the source document
            // ------------------------------------------------------------------
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"Input file not found: {inputPath}");
                return;
            }

            var originalParagraphs = DocxReader.GetParagraphs(inputPath);
            Console.WriteLine($"Loaded {originalParagraphs.Count} paragraphs from input.docx.");

            // ------------------------------------------------------------------
            // 2️⃣ Translate the entire document to French using Google AI
            // ------------------------------------------------------------------
            var frenchParagraphs = await Translator.TranslateToFrenchAsync(originalParagraphs);
            Console.WriteLine("Translation completed – document is now in French.");

            // ------------------------------------------------------------------
            // 3️⃣ Save the translated document
            // ------------------------------------------------------------------
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output_fr.docx");
            DocxWriter.Write(outputPath, frenchParagraphs);
            Console.WriteLine($"Saved translated document to: {outputPath}");
        }
    }
}
```

### Ожидаемый вывод

При запуске программы (`dotnet run`) консоль выведет что‑то вроде:

```
Loaded 12 paragraphs from input.docx.
Translation completed – document is now in French.
Saved translated document to: C:\Path\To\Your\Project\output_fr.docx
```

Откройте `output_fr.docx` в Word, LibreOffice или любом другом просмотрщике, и вы увидите, что оригинальное английское содержание заменилось французскими переводами.

## Translate docx to French – пошаговый обзор

### 1. Надёжно настроить учётные данные Google

* Поместите файл JSON сервисного аккаунта в безопасное место, например

## Что следует изучить дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [How to save translated Word document in C# with Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [How to translate DOCX to French and automate document translation](/words/english/net/ai-powered-document-processing/how-to-translate-docx-to-french-and-automate-document-transl/)
- [translate docx to french with Aspose.Words and Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}