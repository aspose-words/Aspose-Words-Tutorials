---
category: general
date: 2026-08-23
description: ترجمة النص إلى الإسبانية في C# باستخدام Aspose.Words AI Translator ومزود
  Google. اتبع الدليل خطوة بخطوة لترجمة النص في C# بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: ar
lastmod: 2026-08-23
og_description: ترجمة سلسلة إلى الإسبانية في C# باستخدام Aspose.Words AI. يوضح هذا
  البرنامج التعليمي كيفية إعداد موفر Google، وترجمة سلسلة، وعرض النتيجة.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: ترجمة السلسلة إلى الإسبانية في C# – مثال كامل للكود
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
title: ترجمة السلسلة إلى الإسبانية في C# باستخدام Aspose.Words AI
url: /ar/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ترجمة سلسلة إلى الإسبانية في C# باستخدام Aspose.Words AI

إذا كنت بحاجة إلى **translate string to Spanish** في تطبيق .NET، فإن هذا الدليل يوضح بالضبط كيفية القيام بذلك. سترى مثالًا كاملاً قابلاً للتنفيذ ينشئ مترجمًا، يستدعي خدمة Google، ويطبع النص بالإسبانية.

يغطي الدليل أيضًا **translate string in C#** باستخدام مكتبة Aspose.Words AI، بحيث يمكنك دمج التعريب مباشرةً في قاعدة الشيفرة الخاصة بك دون الحاجة إلى سكريبتات خارجية.

## ما ستحتاجه

- .NET 6.0 SDK أو أحدث (الكود يُجمّع مع .NET Core و .NET Framework)
- مفتاح Google Cloud Translation API نشط
- حزمة NuGet `Aspose.Words.AI` (تثبيت باستخدام `dotnet add package Aspose.Words.AI`)
- محرر شيفرة أو بيئة تطوير متكاملة مثل Visual Studio 2022

هذه المتطلبات المسبقة تضمن تشغيل العينة مباشرةً دون أي إعداد إضافي.

## ترجمة سلسلة إلى الإسبانية باستخدام Aspose.Words AI

هذا القسم ينشئ كائن `Translator` المُكوَّن لمزود Google. يتعامل المزود مع طلب HTTP إلى نقطة ترجمة Google.

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

**لماذا هذا يعمل:**  
- `Translator` يُجَزل استدعاء HTTP، ويتعامل مع المصادقة باستخدام مفتاح API الذي تزوده.  
- `TranslationProvider.Google` يُخبر SDK بتوجيه الطلب إلى Google Cloud Translation.  
- `Language.Spanish` يختار رمز اللغة الهدف (`es`).  
- طريقة `Translate` تُعيد السلسلة المترجمة، والتي يمكنك استخدامها في أي مكان في تطبيقك.

## إعداد مزود ترجمة Google

1. **Obtain an API key** من Google Cloud Console → APIs & Services → Credentials.  
2. **Enable the Cloud Translation API** لمشروعك.  
3. احفظ المفتاح بأمان (متغيّر بيئة، مدير أسرار، إلخ). يستخدم المثال قيمة حرفية للتوضيح، لكن في الكود الإنتاجي يجب تجنّب كتابة الأسرار صراحةً.

## ترجمة السلسلة في C# – خطوة بخطوة

| الخطوة | الإجراء | السبب |
|------|--------|--------|
| 1 | إنشاء كائن `Translator` باستخدام `TranslationProvider.Google` | يربط SDK بخدمة Google |
| 2 | استدعاء `Translate(source, Language.Spanish)` | يرسل النص الأصلي ويتلقى النتيجة بالإسبانية |
| 3 | طباعة النتيجة باستخدام `Console.WriteLine` | يتحقق من الترجمة ويظهر كيفية الاستخدام |

تشغيل البرنامج يطبع:

```
¡Hola mundo!
```

> **ملاحظة:** قد يختلف الناتج الدقيق قليلاً اعتمادًا على نموذج ترجمة Google (مثال: “Hola mundo” مقابل “¡Hola mundo!”). كلاهما يعادل الإسبانية الصحيحة.

## تشغيل البرنامج والتحقق من الناتج

1. افتح طرفية في مجلد المشروع.  
2. نفّذ `dotnet run`.  
3. تأكد من أن الطرفية تعرض العبارة بالإسبانية.

إذا أظهرت الطرفية خطأً مثل *“401 Unauthorized”*، فتحقق مرة أخرى من صحة مفتاح API وأن خدمة Cloud Translation API مفعلة للمشروع.

## المشكلات الشائعة وأفضل الممارسات

- **API quota limits** – يفرض Google حدودًا على الطلبات لكل حساب فوترة. راقب الاستخدام في Cloud Console لتجنب التقييد غير المتوقع.  
- **Network latency** – استدعاءات الترجمة هي طلبات HTTP عن بُعد. فكر في تخزين السلاسل المترجمة بشكل مؤقت لتقليل زمن الاستجابة.  
- **Encoding issues** – يعمل SDK مع سلاسل UTF‑8؛ تأكد من حفظ ملفات المصدر بترميز UTF‑8 للحفاظ على الأحرف الخاصة.  
- **Error handling** – غلف استدعاء `Translate` بكتلة try‑catch لمعالجة `ApiException` وتوفير نص بديل.

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

## توسيع المثال

- **Translate to other languages** – استبدل `Language.Spanish` بـ `Language.French` أو `Language.German`، إلخ.  
- **Batch translation** – استدعِ `Translate` داخل حلقة لمعالجة قائمة من السلاسل.  
- **Integrate with UI** – استخدم السلسلة المترجمة في صفحات ASP.NET Core Razor، أو Windows Forms، أو تطبيقات WPF.

## الخلاصة

أنت الآن تعرف كيف **translate string to Spanish** في C# باستخدام Aspose.Words AI وخدمة ترجمة Google. يغطي الحل الكامل إعداد المزود، استدعاء الترجمة، معالجة الأخطاء، والتحقق من الناتج.

من هنا، جرب لغات إضافية، خزن النتائج مؤقتًا لتحسين الأداء، ودمج المترجم في خطوط أنابيب التعريب الأكبر.

--- 

*هل أنت مستعد لتعريب محتوى أكثر؟ اطلع على الدليل التالي حول **translate string in C# with Azure Cognitive Services** للحصول على مزود سحابي بديل.*

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Replace With String](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [Replace With String](/words/english/net/find-and-replace-text/replace-with-string/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}