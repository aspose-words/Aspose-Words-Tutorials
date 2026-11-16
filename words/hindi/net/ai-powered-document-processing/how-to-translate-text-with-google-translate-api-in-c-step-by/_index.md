---
category: general
date: 2026-11-15
description: C# में Google के साथ टेक्स्ट का अनुवाद कैसे करें सीखें। यह ट्यूटोरियल
  एक Google Translate उदाहरण दिखाता है, कई भाषाओं को संभालता है और सर्वोत्तम प्रथाओं
  को दर्शाता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: hi
lastmod: 2026-11-15
og_description: C# में Google का उपयोग करके टेक्स्ट कैसे अनुवादित करें, एक पूर्ण Google
  Translate उदाहरण के साथ। कई भाषाओं को सुरक्षित रूप से अनुवाद करने के लिए इस ट्यूटोरियल
  का पालन करें।
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: C# में Google Translate API के साथ टेक्स्ट कैसे अनुवादित करें – त्वरित ट्यूटोरियल
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
title: C# में Google Translate API के साथ टेक्स्ट कैसे ट्रांसलेट करें – चरण‑दर‑चरण
  गाइड
url: /hi/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Google Translate API के साथ टेक्स्ट कैसे अनुवादित करें – चरण‑दर‑चरण गाइड

यदि आपको **how to translate text** की आवश्यकता है, तो Google Cloud Translation API एक विश्वसनीय, भाषा‑निर्पेक्ष समाधान प्रदान करता है। इस ट्यूटोरियल में आप एक **Google Translate example** देखेंगे जो एक सरल स्ट्रिंग का अनुवाद करता है, **translate multiple languages** तक विस्तारित होता है, और API कुंजियों और त्रुटि संभालने के लिए सर्वोत्तम प्रथाओं का पालन करता है।

आप एक तैयार‑चलाने योग्य C# कंसोल प्रोग्राम, **translate text with Google** की स्पष्ट समझ, और बड़े प्रोजेक्ट्स के लिए कोड को अनुकूलित करने का आत्मविश्वास प्राप्त करेंगे।

## इस ट्यूटोरियल में क्या कवर किया गया है

* Google Cloud प्रोजेक्ट सेट अप करना और API कुंजी प्राप्त करना।  
* `Google.Cloud.Translation.V2` NuGet पैकेज स्थापित करना।  
* आधिकारिक SDK का उपयोग करके **how to translate text** करने वाला साफ़, पुन: उपयोग योग्य कोड लिखना।  
* एक ही कॉल में **translate multiple languages** करने के लिए समाधान का विस्तार करना।  
* प्रोडक्शन‑ग्रेड इम्प्लीमेंटेशन्स के लिए सामान्य समस्याएँ और टिप्स।

### पूर्वापेक्षाएँ

* .NET 6.0 SDK या बाद का संस्करण (कोड .NET Core और .NET Framework के साथ कंपाइल होता है)।  
* एक Google Cloud खाता जिसमें **Cloud Translation API** सक्षम हो।  
* C# और कंसोल एप्लिकेशन्स की बुनियादी परिचितता।  

---

## चरण 1: Google Cloud Translation क्लाइंट लाइब्रेरी स्थापित करें

आधिकारिक क्लाइंट लाइब्रेरी HTTP कॉल्स को एब्स्ट्रैक्ट करती है और आपके लिए प्रमाणीकरण संभालती है।

```bash
dotnet add package Google.Cloud.Translation.V2
```

कमांड चलाने से `Google.Cloud.Translation.V2` पैकेज आपके प्रोजेक्ट में जोड़ दिया जाता है, जिससे आपको इस गाइड में उपयोग की गई `TranslationClient` क्लास तक पहुंच मिलती है।

> **Why this step matters** – SDK का उपयोग करने से मैन्युअल अनुरोध निर्माण से बचा जा सकता है, बग्स कम होते हैं, और आप Google के नवीनतम API संस्करण के साथ संरेखित रहते हैं।

## चरण 2: पुन: उपयोग योग्य ट्रांसलेशन हेल्पर बनाएं

एक स्थैतिक क्लास में ट्रांसलेशन लॉजिक को संलग्न करने से कोड पुन: उपयोग योग्य बनता है और API‑key हैंडलिंग अलग रहती है।

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

> **Why we return a dictionary** – जब आपको **translate multiple languages** की आवश्यकता हो, तो भाषा कोड द्वारा परिणामों को व्यवस्थित करने से डाउनस्ट्रीम प्रोसेसिंग सरल हो जाती है।

## चरण 3: हेल्पर का उपयोग करने वाला कंसोल एप्लिकेशन बनाएं

नीचे एक पूर्ण `Program.cs` है जो एकल‑टेक्स्ट अनुवाद और बैच अनुवाद दोनों को दर्शाता है।

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

**अपेक्षित कंसोल आउटपुट**

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

> **Why the try/catch blocks?** – नेटवर्क त्रुटियां, कोटा सीमाएं, या अमान्य API कुंजी अपवाद उठाती हैं। उन्हें सुगमता से संभालने से उपयोगकर्ता अनुभव बेहतर होता है और आपका एप्लिकेशन स्थिर रहता है।

## चरण 4: अपनी API कुंजी सुरक्षित करें

ऊपर दिखाए अनुसार API कुंजी को हार्ड‑कोड करना त्वरित डेमो के लिए स्वीकार्य है लेकिन प्रोडक्शन के लिए नहीं। इन प्रथाओं का पालन करें:

* की को एक पर्यावरण चर (`GOOGLE_API_KEY`) में संग्रहीत करें और रनटाइम पर पढ़ें:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* **Google Application Default Credentials** का उपयोग करें बजाय API कुंजी के जब आप Google Cloud (App Engine, Cloud Run, आदि) पर चल रहे हों।
* Google Cloud कंसोल में कुंजी को Translation API तक सीमित करें और उपयोग को विशिष्ट IP पतों या रेफ़रर तक सीमित करें।

## चरण 5: वास्तविक‑दुनिया परिदृश्यों के लिए समाधान का विस्तार करें

### भाषा पहचान को संभालना

यदि आपको स्रोत भाषा जाननी है, तो प्रतिक्रिया ऑब्जेक्ट में `DetectedSourceLanguage` शामिल होता है:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### बड़े दस्तावेज़ों का अनुवाद

API प्रति अनुरोध अधिकतम 30 KB का समर्थन करता है। बड़े टेक्स्ट के लिए, सामग्री को भागों में विभाजित करें, प्रत्येक भाग का अनुवाद करें, और फिर परिणामों को जोड़ें। असहज वाक्यांशों से बचने के लिए वाक्य सीमाओं को बरकरार रखें।

### रेट‑लिमिटिंग और कोटा

Google प्रति मिनट अनुरोध सीमाएँ लागू करता है। कोटा सीमाओं का सम्मान करने और `429 Too Many Requests` त्रुटियों से बचने के लिए एक्सपोनेंशियल बैक‑ऑफ़ के साथ रीट्राई पॉलिसी लागू करें।

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## सामान्य प्रश्न और किनारे के मामलों

**Q: क्या मैं पूरी HTML पेज का अनुवाद कर सकता हूँ?**  
A: हाँ। `TranslateText` को कॉल करते समय `Format` पैरामीटर (`"text"` या `"html"`) का उपयोग करें। SDK इसे `TranslateText` ओवरलोड के माध्यम से उजागर करता है जो `TranslateTextRequest` को स्वीकार करता है।

**Q: यदि कोई भाषा समर्थित नहीं है तो क्या होगा?**  
A: API एक त्रुटि लौटाता है। अनुरोध करने से पहले `client.ListSupportedLanguages()` द्वारा लौटाए गए सूची के विरुद्ध भाषा कोड की वैधता जांचें।

**Q: क्या API प्रति अक्षर शुल्क लेता है?**  
A: Google अनुवादित प्रत्येक अक्षर के लिए बिल करता है। मूल्य निर्धारण पृष्ठ का उपयोग करके लागत का अनुमान लगाएँ और अक्सर उपयोग होने वाले अनुवादों को कैश करने पर विचार करें।

---

## निष्कर्ष

अब आप आधिकारिक Google Translate API का उपयोग करके C# में **how to translate text** करना जानते हैं। ट्यूटोरियल ने एक **Google translate example** को कवर किया, **translate multiple languages** को प्रदर्शित किया, और API‑key सुरक्षा तथा त्रुटि संभालने जैसी प्रोडक्शन‑रेडी प्रथाओं को उजागर किया। `Translator` हेल्पर को पुन: उपयोग करके, आप अनुवाद को किसी भी .NET सेवा, डेस्कटॉप ऐप, या माइक्रोसर्विस में एकीकृत कर सकते हैं।

**अगले कदम**

* **Google Translate tutorial** का अन्वेषण करें उन्नत सुविधाओं जैसे ग्लॉसरी और कस्टम मॉडल के लिए।  
* इस कोड को ASP.NET Core के साथ मिलाकर एक बहुभाषी वेब API बनाएं।  
* CSV फ़ाइलों के बैच अनुवाद के साथ प्रयोग करें ताकि स्थानीयकरण पाइपलाइन को स्वचालित किया जा सके।

कोडिंग का आनंद लें, और वैश्विक रूप से सुलभ एप्लिकेशन बनाने का मज़ा लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स निकट‑संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words और Google API के साथ docx को फ्रेंच में अनुवाद करें](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Google AI के साथ C# में अनूदित Word दस्तावेज़ को कैसे सहेजें](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Aspose.Words AI के साथ C# में स्ट्रिंग को स्पेनिश में अनुवाद करें](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}