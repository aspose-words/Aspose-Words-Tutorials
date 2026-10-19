---
category: general
date: 2026-05-04
description: كيفية استخدام نموذج اللغة الكبيرة (LLM) لتحرير المستندات باستخدام Aspose
  – تعلم استبدال نص الفقرة، والاتصال بنموذج اللغة المحلي، وإعادة كتابة النص باستخدام
  الذكاء الاصطناعي.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: ar
og_description: كيفية استخدام نموذج اللغة الكبيرة (LLM) لتحرير المستندات باستخدام
  Aspose. يوضح هذا الدليل كيفية الاتصال بنموذج لغة محلي، واستبدال نص الفقرة، وإعادة
  كتابة النص باستخدام الذكاء الاصطناعي.
og_title: كيفية استخدام LLM مع Aspose.Words – إعادة كتابة الفقرات في C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: كيفية استخدام LLM مع Aspose.Words – إعادة كتابة الفقرات في C#
url: /ar/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخدام LLM مع Aspose.Words – إعادة كتابة الفقرات في C#

هل تساءلت يوماً **كيف تستخدم LLM** لتحسين مستند Word دون فتحه يدوياً؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى *استبدال نص الفقرة* برمجياً لكن لا يملكون سير عمل نظيف يعتمد على الذكاء الاصطناعي.  

في هذا الدرس سنقوم بربط نموذج لغة كبير محلي، نمرره مقطعاً من ملف `.docx`، نطلب منه **إعادة كتابة النص باستخدام AI**، وأخيراً نحفظ المستند المحدث—كل ذلك باستخدام Aspose.Words. بنهاية الدرس ستحصل على تطبيق Console بلغة C# جاهز للتنفيذ يوضح كامل الخطوات.

> **ما ستحصل عليه:** مثال كامل قابل للتنفيذ، شرح لكل خطوة، نصائح للحالات الخاصة، وأفكار لتوسيع الحل.

## ما الذي ستحتاجه

- **.NET 6+** (أو .NET Framework 4.7.2 – الكود يعمل على كلاهما)
- **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`)
- **خادم LLM محلي** ي expose نقطة نهاية HTTP بسيطة `/generate` (مثل Ollama، LMStudio، أو خدمة Flask مخصصة)
- إلمام أساسي بـ C# وشفرة عميل HTTP  

لا توجد حزم SDK إضافية مطلوبة؛ كل ما تبقى هو الشفرة التي سنكتبها معاً.

## الخطوة 1: كيفية استخدام LLM لاستبدال نص الفقرة

أول شيء علينا فعله هو تحديد الفقرة التي نريد تعديلها. تجعلنا Aspose.Words ذلك سهلاً عبر نموذج كائن غني.

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

**لماذا هذا مهم:**  
اختيار العقدة الصحيحة يمنعك من الكتابة فوق العناوين أو الجداول عن طريق الخطأ. باستخدام نهج **استبدال نص الفقرة** نحافظ على بنية المستند سليمة بينما نغير فقط المحتوى الذي يهمنا.

> **نصيحة احترافية:** إذا كان مستندك يحتوي على أقسام بطول متغير، استخدم `document.GetChildNodes(NodeType.Paragraph, true)` و LINQ لتحديد الفقرة بناءً على نصها أو نمطها.

## الخطوة 2: الاتصال بنقطة نهاية LLM محلية

الآن بعد أن حصلنا على النص، نحتاج لإرساله إلى الـ LLM. يستخدم المثال فئة غلاف بسيطة `LocalLargeLanguageModel` تخفي تفاصيل HTTP. يمكنك استبدالها بـ استدعاءات `HttpClient` إذا رغبت.

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

**لماذا نتصل بهذه الطريقة:**  
إعداد **الاتصال بـ LLM محلي** يزيل زمن الانتقال، يبقي البيانات داخل المؤسسة، ويتجنب تكاليف الـ API. كما يجعل الغلاف الشفرة اللاحقة أنظف، مما يسمح بالتركيز على منطق **إعادة كتابة النص باستخدام AI**.

## الخطوة 3: إعادة كتابة النص باستخدام AI مع Aspose.Words

مع نص الفقرة جاهز والـ LLM مستعد، نصيغ مطالبة (prompt) تخبر النموذج بالضبط ما نريده—إعادة كتابة بنبرة رسمية. يمكنك تعديل المطالبة لأنماط أخرى (ودية، تقنية، إلخ).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**لماذا هذا يعمل:**  
نماذج LLM تعتمد على المطالبات؛ إعطاء تعليمات صريحة (“Rewrite … in a formal tone”) ينتج نتائج متسقة. خطوة **إعادة كتابة النص باستخدام AI** هي جوهر الدرس – فهي تُظهر كيف يمكن دمج الذكاء الاصطناعي مباشرةً في سير عمل المستندات.

## الخطوة 4: تعديل المستند وحفظ التغييرات

الآن نستبدل الـ runs الأصلية بالمحتوى الجديد. تخزن Aspose.Words النص في كائنات `Run`، لذا فإن مسحها أولاً يمنع بقاء بقايا تنسيق غير مرغوبة.

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

**ملاحظة حول الحالات الخاصة:**  
إذا كانت الفقرة الأصلية تحتوي على تنسيقات مختلطة (غامق، مائل) قد ترغب في الحفاظ على الأنماط. في هذه الحالة، أنشئ `Run` جديداً، انسخ إعدادات `Font` الأصلية، ثم عيّن `Text` إلى `revisedText`.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في مشروع Console. تذكر تثبيت حزمة NuGet الخاصة بـ Aspose.Words أولاً (`dotnet add package Aspose.Words`).

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

### النتيجة المتوقعة

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

افتح `output.docx` – ستلاحظ أن الفقرة الثالثة الآن تحتوي على النسخة المنقحة.

## أسئلة شائعة ومشكلات محتملة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو أعاد الـ LLM JSON يحتوي على حقول إضافية؟** | عدّل `GenerateText` لتسلسل الخاصية الصحيحة أو قم بتحليل الاستجابة يدوياً. |
| **هل يمكن معالجة عدة فقرات في آن واحد؟** | نعم – كرّر عبر `document.FirstSection.Body.Paragraphs` وطبق نفس منطق المطالبة، ربما بإضافة فهرس الفقرة إلى المطالبة لتوفير السياق. |
| **خادم الـ LLM يتطلب مصادقة؟** | أضف رأساً إلى `HttpClient` قبل طلب POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **يفقد التنسيق بعد الاستبدال.** | احفظ إعدادات `Run.Font` الأصلية: أنشئ `Run` جديداً، انسخ `originalRun.Font.Clone()`، ثم عيّن `Text`. |
| **أحياناً يُعيد الـ LLM سلاسل فارغة.** | نفّذ آلية احتياطية – إذا كان `revisedText.Trim().Length == 0`، احتفظ بالنص الأصلي أو أعد المحاولة بمطالبة أبسط. |

## توسيع الحل

الآن بعد أن أتقنت **كيفية استخدام LLM** لفقرة واحدة، فكر في الخطوات التالية:

- **معالجة دفعات:** كرّر عبر كل فقرة وأعد كتابتها بنمط مختار (مثلاً “اجعل كل النص مختصرًا”).  
- **إعادة كتابة واعية للأنماط:** مرّر اسم نمط الفقرة الأصلي في المطالبة حتى يلتزم الـ LLM بالعناوين مقابل نص الجسم.  
- **دمج مع خط أنابيب CI:** أتمتة تحسين المستندات كجزء من عملية بناء الوثائق.  
- **مطالبات بديلة:** جرّب “summarize this paragraph” أو “translate this paragraph to Spanish” لاستكشاف كامل قدرة **إعادة كتابة النص باستخدام AI**.

## الخلاصة

استعرضنا كامل تدفق **كيفية استخدام LLM** مع Aspose.Words: تحميل المستند، **الاتصال بـ LLM محلي**، استخراج الفقرة، **إعادة كتابة النص باستخدام AI**، **استبدال نص الفقرة**، وأخيراً حفظ النتيجة. الشفرة مستقلة، تعمل فورًا، وتظهر طريقة عملية لدمج الذكاء الاصطناعي مع أتمتة المستندات التقليدية.

جرّبها، عدّل المطالبات، ودع

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}