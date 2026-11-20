---
category: general
date: 2026-11-15
description: تعلم كيفية ترجمة النص باستخدام Google في C#. يوضح هذا الدرس مثالًا على
  Google Translate، ويتعامل مع لغات متعددة وأفضل الممارسات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: ar
lastmod: 2026-11-15
og_description: كيفية ترجمة النص باستخدام Google في C# باستخدام مثال كامل لـ Google
  Translate. اتبع هذا الدرس لترجمة عدة لغات بأمان.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: كيفية ترجمة النص باستخدام واجهة برمجة تطبيقات Google Translate في C# – دليل
  سريع
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
title: كيفية ترجمة النص باستخدام واجهة برمجة تطبيقات Google Translate في C# – دليل
  خطوة بخطوة
url: /ar/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية ترجمة النص باستخدام Google Translate API في C# – دليل خطوة بخطوة

إذا كنت بحاجة إلى **how to translate text** في تطبيق .NET، فإن Google Cloud Translation API يقدم حلاً موثوقًا وغير مرتبط بلغة معينة. في هذا الدرس ستشاهد **Google Translate example** الذي يترجم سلسلة بسيطة، ويتوسع إلى **translate multiple languages**، ويتبع أفضل الممارسات لمفاتيح API ومعالجة الأخطاء.

ستحصل على برنامج C# console جاهز للتشغيل، وفهم واضح لـ **translate text with Google**، والثقة لتكييف الكود لمشاريع أكبر.

## ما يغطيه هذا الدرس

* إعداد مشروع Google Cloud والحصول على مفتاح API.  
* تثبيت حزمة NuGet `Google.Cloud.Translation.V2`.  
* كتابة كود نظيف وقابل لإعادة الاستخدام يقوم بـ **how to translate text** باستخدام SDK الرسمي.  
* توسيع الحل إلى **translate multiple languages** في طلب واحد.  
* المشكلات الشائعة ونصائح للتنفيذ على مستوى الإنتاج.

### المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث (الكود يُترجم مع .NET Core و .NET Framework).  
* حساب Google Cloud مع تمكين **Cloud Translation API**.  
* إلمام أساسي بـ C# وتطبيقات console.  

---

## الخطوة 1: تثبيت مكتبة عميل Google Cloud Translation

مكتبة العميل الرسمية تُجرد استدعاءات HTTP وتتعامل مع المصادقة نيابةً عنك.

```bash
dotnet add package Google.Cloud.Translation.V2
```

تشغيل الأمر يضيف حزمة `Google.Cloud.Translation.V2` إلى مشروعك، مما يمنحك الوصول إلى الفئة `TranslationClient` المستخدمة طوال هذا الدليل.

> **Why this step matters** – استخدام SDK يتجنب بناء الطلبات يدويًا، يقلل الأخطاء، ويضمن توافقك مع أحدث نسخة من API من Google.

## الخطوة 2: إنشاء مساعد ترجمة قابل لإعادة الاستخدام

تغليف منطق الترجمة في فئة ثابتة يجعل الكود قابلًا لإعادة الاستخدام ويعزل معالجة مفتاح API.

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

> **Why we return a dictionary** – عندما تحتاج إلى **translate multiple languages**، فإن تنظيم النتائج حسب رمز اللغة يجعل المعالجة اللاحقة بسيطة.

## الخطوة 3: بناء تطبيق console الذي يستخدم المساعد

فيما يلي ملف `Program.cs` كامل يوضح كل من ترجمة نص واحد وترجمة دفعة.

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

**المخرجات المتوقعة في console**

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

> **Why the try/catch blocks?** – أخطاء الشبكة، حدود الحصة، أو مفتاح API غير صالح تُثير استثناءات. التعامل معها بلطف يحسن تجربة المستخدم ويحافظ على استقرار التطبيق.

## الخطوة 4: تأمين مفتاح API الخاص بك

تضمين مفتاح API مباشرة في الكود، كما هو موضح أعلاه، مقبول لتجربة سريعة لكنه غير مناسب للإنتاج. اتبع هذه الممارسات:

- احفظ المفتاح في متغير بيئي (`GOOGLE_API_KEY`) واقرأه وقت التشغيل:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
- استخدم **Google Application Default Credentials** بدلاً من مفتاح API عند تشغيله على Google Cloud (App Engine, Cloud Run, إلخ).
- قصر المفتاح على Translation API في وحدة تحكم Google Cloud وتحديد الاستخدام لعناوين IP أو مراجع محددة.

## الخطوة 5: توسيع الحل لسيناريوهات العالم الحقيقي

### معالجة اكتشاف اللغة

إذا كنت بحاجة لمعرفة لغة المصدر، يحتوي كائن الاستجابة على `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### ترجمة مستندات كبيرة

يدعم API ما يصل إلى 30 KB لكل طلب. للنصوص الأكبر، قسّم المحتوى إلى أجزاء، ترجم كل جزء، ثم اجمع النتائج. حافظ على حدود الجمل لتجنب الصياغة غير الطبيعية.

### تحديد المعدل والحصص

Google يفرض حدود طلبات لكل دقيقة. نفّذ سياسة إعادة محاولة مع تأخير تصاعدي لتقيد الحصص وتجنب أخطاء `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## أسئلة شائعة وحالات حافة

**س: هل يمكنني ترجمة صفحة HTML كاملة؟**  
ج: نعم. استخدم معامل `Format` (`"text"` أو `"html"`) عند استدعاء `TranslateText`. يتيح SDK ذلك عبر نسخة `TranslateText` التي تقبل `TranslateTextRequest`.

**س: ماذا لو لم تكن اللغة مدعومة؟**  
ج: تُعيد API خطأ. تحقق من رموز اللغات مقابل القائمة التي تُرجعها `client.ListSupportedLanguages()` قبل إرسال الطلب.

**س: هل تُحاسب API حسب عدد الأحرف؟**  
ج: Google تُفوتر حسب كل حرف مُترجم. قدّر التكاليف باستخدام صفحة التسعير وفكّر في تخزين الترجمات المتكررة مؤقتًا.

---

## الخلاصة

أنت الآن تعرف **how to translate text** في C# باستخدام Google Translate API الرسمي. غطى الدرس **Google translate example**، وأظهر **translate multiple languages**، وأبرز ممارسات جاهزة للإنتاج مثل أمان مفتاح API ومعالجة الأخطاء. من خلال إعادة استخدام المساعد `Translator`، يمكنك دمج الترجمة في أي خدمة .NET أو تطبيق سطح مكتب أو مايكروسيرفيس.

**الخطوات التالية**

- استكشف **Google Translate tutorial** للحصول على ميزات متقدمة مثل القواميس والنماذج المخصصة.  
- اجمع هذا الكود مع ASP.NET Core لإنشاء API ويب متعدد اللغات.  
- جرّب ترجمة دفعات من ملفات CSV لأتمتة خطوط أنابيب التعريب.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية حفظ مستند Word مترجم في C# باستخدام Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [ترجمة سلسلة إلى الإسبانية في C# باستخدام Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}