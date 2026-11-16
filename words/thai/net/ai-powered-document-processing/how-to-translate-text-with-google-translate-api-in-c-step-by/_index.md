---
category: general
date: 2026-11-15
description: เรียนรู้วิธีแปลข้อความด้วย Google ใน C# บทเรียนนี้แสดงตัวอย่างการใช้
  Google Translate การจัดการหลายภาษาและแนวปฏิบัติที่ดีที่สุด.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: th
lastmod: 2026-11-15
og_description: วิธีแปลข้อความด้วย Google ใน C# โดยใช้ตัวอย่าง Google Translate ที่ครบถ้วน
  ทำตามบทเรียนนี้เพื่อแปลหลายภาษาอย่างปลอดภัย
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: วิธีแปลข้อความด้วย Google Translate API ใน C# – บทเรียนสั้น
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
title: วิธีแปลข้อความด้วย Google Translate API ใน C# – คู่มือแบบขั้นตอนต่อขั้นตอน
url: /th/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีแปลข้อความด้วย Google Translate API ใน C# – คู่มือขั้นตอนต่อขั้นตอน

หากคุณต้องการ **how to translate text** ในแอปพลิเคชัน .NET, Google Cloud Translation API ให้โซลูชันที่เชื่อถือได้และไม่จำกัดภาษา ในบทเรียนนี้คุณจะได้เห็น **Google Translate example** ที่แปลสตริงง่าย ๆ, ขยายเป็น **translate multiple languages**, และปฏิบัติตามแนวทางปฏิบัติที่ดีที่สุดสำหรับคีย์ API และการจัดการข้อผิดพลาด.

คุณจะได้โปรแกรมคอนโซล C# ที่พร้อมใช้งาน, ความเข้าใจที่ชัดเจนเกี่ยวกับ **translate text with Google**, และความมั่นใจในการปรับโค้ดสำหรับโครงการที่ใหญ่ขึ้น.

## สิ่งที่บทเรียนนี้ครอบคลุม

* ตั้งค่าโครงการ Google Cloud และรับคีย์ API.  
* ติดตั้งแพคเกจ NuGet `Google.Cloud.Translation.V2`.  
* เขียนโค้ดที่สะอาดและนำกลับมาใช้ใหม่ที่ **how to translate text** ด้วย SDK อย่างเป็นทางการ.  
* ขยายโซลูชันเพื่อ **translate multiple languages** ในการเรียกครั้งเดียว.  
* ข้อผิดพลาดทั่วไปและเคล็ดลับสำหรับการใช้งานระดับผลิตภัณฑ์.  

### ข้อกำหนดเบื้องต้น

* .NET 6.0 SDK หรือใหม่กว่า (โค้ดสามารถคอมไพล์กับ .NET Core และ .NET Framework).  
* บัญชี Google Cloud ที่เปิดใช้งาน **Cloud Translation API**.  
* ความคุ้นเคยพื้นฐานกับ C# และแอปพลิเคชันคอนโซล.  

---

## ขั้นตอนที่ 1: ติดตั้งไลบรารีไคลเอนต์ Google Cloud Translation

ไลบรารีไคลเอนต์อย่างเป็นทางการจะทำให้การเรียก HTTP เป็นนามธรรมและจัดการการรับรองความถูกต้องให้คุณ.

```bash
dotnet add package Google.Cloud.Translation.V2
```

การรันคำสั่งจะเพิ่มแพคเกจ `Google.Cloud.Translation.V2` ไปยังโครงการของคุณ, ทำให้คุณเข้าถึงคลาส `TranslationClient` ที่ใช้ตลอดคู่มือนี้.

> **ทำไมขั้นตอนนี้จึงสำคัญ** – การใช้ SDK ช่วยหลีกเลี่ยงการสร้างคำขอด้วยตนเอง, ลดบั๊ก, และทำให้คุณสอดคล้องกับเวอร์ชัน API ล่าสุดของ Google.

## ขั้นตอนที่ 2: สร้างตัวช่วยการแปลที่นำกลับมาใช้ใหม่ได้

การห่อหุ้มตรรกะการแปลไว้ในคลาสสถิตทำให้โค้ดนำกลับมาใช้ใหม่ได้และแยกการจัดการคีย์ API ออกจากกัน.

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

> **ทำไมเราถึงคืนค่าเป็น dictionary** – เมื่อคุณต้องการ **translate multiple languages**, การจัดระเบียบผลลัพธ์ตามรหัสภาษา ทำให้การประมวลผลต่อไปง่ายขึ้น.

## ขั้นตอนที่ 3: สร้างแอปพลิเคชันคอนโซลที่ใช้ตัวช่วย

ด้านล่างเป็นไฟล์ `Program.cs` ฉบับเต็มที่แสดงการแปลข้อความเดี่ยวและการแปลแบบชุด.

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

**ผลลัพธ์คอนโซลที่คาดหวัง**

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

> **ทำไมต้องใช้บล็อก try/catch?** – ข้อผิดพลาดเครือข่าย, ขีดจำกัดโควต้า, หรือคีย์ API ที่ไม่ถูกต้องจะทำให้เกิดข้อยกเว้น. การจัดการอย่างราบรื่นช่วยปรับปรุงประสบการณ์ผู้ใช้และทำให้แอปพลิเคชันของคุณเสถียร.

## ขั้นตอนที่ 4: ปกป้องคีย์ API ของคุณ

การใส่คีย์ API ลงในโค้ดโดยตรงตามที่แสดงข้างต้นเป็นที่ยอมรับสำหรับการสาธิตอย่างรวดเร็วแต่ไม่เหมาะสำหรับการใช้งานจริง. ปฏิบัติตามแนวทางต่อไปนี้:

* เก็บคีย์ไว้ในตัวแปรสภาพแวดล้อม (`GOOGLE_API_KEY`) และอ่านค่าในเวลารัน:  
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* ใช้ **Google Application Default Credentials** แทนคีย์ API เมื่อรันบน Google Cloud (App Engine, Cloud Run ฯลฯ).
* จำกัดคีย์ให้ใช้เฉพาะ Translation API ในคอนโซล Google Cloud และจำกัดการใช้งานให้กับที่อยู่ IP หรือผู้อ้างอิงที่ระบุ.

## ขั้นตอนที่ 5: ขยายโซลูชันสำหรับสถานการณ์จริง

### การตรวจจับภาษาที่ใช้

หากคุณต้องการทราบภาษาต้นฉบับ, วัตถุตอบสนองจะมี `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### การแปลเอกสารขนาดใหญ่

API รองรับสูงสุด 30 KB ต่อคำขอ. สำหรับข้อความที่ยาวกว่า, แบ่งเนื้อหาเป็นส่วนย่อย, แปลแต่ละส่วน, แล้วต่อผลลัพธ์เข้าด้วยกัน. รักษาขอบเขตประโยคให้ครบถ้วนเพื่อหลีกเลี่ยงการแปลที่ไม่ราบรื่น.

### การจำกัดอัตราและโควต้า

Google กำหนดขีดจำกัดจำนวนคำขอต่อวินาที. ใช้นโยบายการลองใหม่ด้วยการหน่วงเวลาแบบเอ็กซ์โพเนนเชียลเพื่อให้สอดคล้องกับขีดจำกัดโควต้าและหลีกเลี่ยงข้อผิดพลาด `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## คำถามทั่วไปและกรณีขอบ

**Q: ฉันสามารถแปลหน้า HTML ทั้งหน้าได้หรือไม่?**  
A: ใช่. ใช้พารามิเตอร์ `Format` (`"text"` หรือ `"html"`) เมื่อเรียก `TranslateText`. SDK เปิดให้ใช้ผ่านการโอเวอร์โหลดของ `TranslateText` ที่รับ `TranslateTextRequest`.

**Q: ถ้าภาษาหนึ่งไม่รองรับจะทำอย่างไร?**  
A: API จะคืนข้อผิดพลาด. ตรวจสอบรหัสภาษาเทียบกับรายการที่ `client.ListSupportedLanguages()` คืนมาก่อนทำคำขอ.

**Q: API คิดค่าบริการต่ออักขระหรือไม่?**  
A: Google เรียกเก็บตามจำนวนอักขระที่แปล. ประมาณค่าใช้จ่ายโดยใช้หน้าราคาและพิจารณาการแคชการแปลที่บ่อยครั้ง.

---

## สรุป

ตอนนี้คุณรู้แล้วว่า **how to translate text** ใน C# ด้วย Google Translate API อย่างเป็นทางการ. บทเรียนได้ครอบคลุม **Google translate example**, แสดงการ **translate multiple languages**, และเน้นแนวปฏิบัติระดับผลิตภัณฑ์เช่นความปลอดภัยของคีย์ API และการจัดการข้อผิดพลาด. ด้วยการใช้ตัวช่วย `Translator` ซ้ำ, คุณสามารถรวมการแปลเข้าไปในบริการ .NET ใด ๆ, แอปเดสก์ท็อป, หรือไมโครเซอร์วิส.

**ขั้นตอนต่อไป**

* สำรวจ **Google Translate tutorial** สำหรับฟีเจอร์ขั้นสูงเช่นพจนานุกรมและโมเดลกำหนดเอง.  
* ผสานโค้ดนี้กับ ASP.NET Core เพื่อสร้างเว็บ API แบบหลายภาษา.  
* ทดลองการแปลเป็นชุดของไฟล์ CSV เพื่ออัตโนมัติการทำงานของ pipeline การแปล.

ขอให้สนุกกับการเขียนโค้ดและเพลิดเพลินกับการสร้างแอปพลิเคชันที่เข้าถึงได้ทั่วโลก!

## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนต่อขั้นตอนเพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ.

- [แปล docx เป็นภาษาฝรั่งเศสด้วย Aspose.Words และ Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [วิธีบันทึกเอกสาร Word ที่แปลแล้วใน C# ด้วย Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [แปลสตริงเป็นภาษาสเปนใน C# ด้วย Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}