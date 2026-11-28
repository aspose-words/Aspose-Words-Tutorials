---
category: general
date: 2026-11-18
description: تعلم كيفية ترجمة ملفات docx إلى الفرنسية باستخدام ترجمة جوجل AI، وترجمة
  المستند بالكامل، وحفظ المستند المترجم في ثلاث خطوات فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- google ai translation
- translate entire document
- save translated document
- how to translate docx
language: ar
lastmod: 2026-11-18
og_description: ترجم ملف docx إلى الفرنسية فورًا باستخدام ترجمة جوجل الذكية. اتبع
  هذا الدليل لترجمة المستند بالكامل وحفظ المستند المترجم بسهولة.
og_image_alt: Screenshot showing a DOCX file translated to French using Google AI
og_title: ترجمة ملف docx إلى الفرنسية باستخدام Google AI – دليل سريع
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
title: كيفية ترجمة ملف docx إلى الفرنسية باستخدام جوجل AI
url: /ar/net/ai-powered-document-processing/how-to-translate-docx-to-french-using-google-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية ترجمة ملف docx إلى الفرنسية باستخدام Google AI

إذا كنت بحاجة إلى **ترجمة docx إلى الفرنسية**، فإن ترجمة Google AI تجعل من الممكن ترجمة المستند بالكامل ببضع أسطر من كود C#. يوضح هذا الدرس بالضبط كيفية ترجمة ملف DOCX، وترجمة محتوى المستند بالكامل، وحفظ المستند المترجم بطريقة موثوقة.

ستتعلم كيفية إعداد عميل Google Cloud Translation، تحميل ملف Word، استدعاء الـ API لترجمة كل فقرة، وأخيرًا كتابة خطوة **حفظ المستند المترجم**. لا تحتاج إلى أي سكريبتات خارجية أو نسخ‑لصق يدوي—كل شيء يعمل داخل تطبيق .NET الخاص بك.

## ما ستحتاجه

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 SDK أو أحدث مثبت  
* مشروع Google Cloud مع تمكين **Cloud Translation API**  
* ملف مفتاح خدمة JSON (تم تنزيله من وحدة تحكم Google Cloud)  
* Visual Studio 2022 (أو أي بيئة تطوير C# تفضلها)  

هذه المتطلبات المسبقة تضمن نجاح استدعاءات **google ai translation** وإمكانية قراءة/كتابة ملفات DOCX باستخدام Open XML SDK.

## إعداد المشروع وتثبيت SDKs المطلوبة

1. أنشئ مشروع console جديد:

   ```bash
   dotnet new console -n DocxFrenchTranslator
   cd DocxFrenchTranslator
   ```

2. أضف حزم NuGet التي يعتمد عليها الدرس:

   ```bash
   dotnet add package Google.Cloud.Translate.V3
   dotnet add package DocumentFormat.OpenXml
   ```

   حزمة *`Google.Cloud.Translate.V3`* توفر عميل **google ai translation**، بينما تتيح لك *`DocumentFormat.OpenXml`* العمل مع ملفات DOCX دون الحاجة إلى تثبيت Microsoft Office.

3. (اختياري) إذا كنت تفضل طبقة تغليف أعلى، يمكنك أيضًا تثبيت `GroupDocs.Translator`:

   ```bash
   dotnet add package GroupDocs.Translator
   ```

   أمثلة الكود أدناه تعمل مع أي من الطريقتين؛ تم عرض نسخة Open XML بالكامل للشفافية.

## تحميل ملف DOCX المصدر

الخطوة الوظيفية الأولى هي قراءة مستند Word الذي تريد ترجمته. باستخدام Open XML SDK، يمكنك استخراج نص كل فقرة إلى قائمة.

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

**لماذا هذا مهم:** تحميل الملف مرة واحدة والاحتفاظ بالنص في الذاكرة يتيح لك **ترجمة محتوى المستند بالكامل** باستدعاء API واحد لكل فقرة، مما يجنب عمليات I/O المتكررة على الملف.

## إجراء ترجمة Google AI

الآن بعد أن لديك الفقرات الأصلية، استدعِ Translation API لتحويل كل سلسلة من الإنجليزية (أو أي لغة مصدر) إلى الفرنسية. العميل يكتشف لغة المصدر تلقائيًا إذا مررت `null`.

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

**لماذا هذا مهم:** استخدام **google ai translation** في طلب دفعة يقلل من زمن الاستجابة والتكلفة مقارنةً بحلقات استدعاء واحدة لكل فقرة. الطريقة أيضًا توضح **كيفية ترجمة docx** برمجيًا.

## إنشاء ملف DOCX جديد بالنص المترجم

بعد استلام السلاسل الفرنسية، اكتبها مرة أخرى في ملف DOCX جديد. الفئة المساعدة التالية تبني مستندًا جديدًا من الفقرات المترجمة.

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

## تجميع كل شيء – البرنامج الكامل

فيما يلي تطبيق console كامل وقابل للتنفيذ يجمع المقاطع السابقة معًا. يوضح **translate docx to french**، ينفذ **google ai translation**، وأخيرًا **حفظ المستند المترجم**.

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

### النتيجة المتوقعة

عند تشغيل البرنامج (`dotnet run`)، سيطبع الطرفية شيئًا مشابهًا لـ:

```
Loaded 12 paragraphs from input.docx.
Translation completed – document is now in French.
Saved translated document to: C:\Path\To\Your\Project\output_fr.docx
```

افتح `output_fr.docx` باستخدام Word أو LibreOffice أو أي عارض، وسترى المحتوى الأصلي بالإنجليزية مستبدلًا بالترجمات الفرنسية.

## ترجمة docx إلى الفرنسية – نظرة عامة خطوة بخطوة

### 1. إعداد بيانات اعتماد Google بأمان

* ضع ملف خدمة الـ JSON في مكان آمن، مثلاً

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [كيفية حفظ مستند Word مترجم في C# باستخدام Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [كيفية ترجمة DOCX إلى الفرنسية وأتمتة ترجمة المستند](/words/english/net/ai-powered-document-processing/how-to-translate-docx-to-french-and-automate-document-transl/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}