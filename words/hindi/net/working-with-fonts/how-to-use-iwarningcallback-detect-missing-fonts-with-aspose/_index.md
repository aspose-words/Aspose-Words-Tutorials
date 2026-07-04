---
category: general
date: 2026-06-24
description: Aspose.Words दस्तावेज़ों में लापता फ़ॉन्ट्स का पता लगाने के लिए IWarningCallback
  का उपयोग कैसे करें। एक पूर्ण, चलाने योग्य उदाहरण और सर्वोत्तम प्रथाएँ सीखें।
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: hi
og_description: Aspose.Words में लापता फ़ॉन्ट्स का पता लगाने के लिए IWarningCallback
  का उपयोग कैसे करें। पूर्ण, प्रोडक्शन‑रेडी समाधान के लिए चरण‑दर‑चरण गाइड का पालन
  करें।
og_title: IWarningCallback का उपयोग कैसे करें – गायब फ़ॉन्ट्स का पता लगाएँ
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: IWarningCallback का उपयोग कैसे करें – Aspose.Words के साथ गायब फ़ॉन्ट्स का
  पता लगाएँ
url: /hi/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# IWarningCallback का उपयोग कैसे करें – Aspose.Words के साथ गायब फ़ॉन्ट्स का पता लगाएँ

**IWarningCallback** का उपयोग करना आवश्यक है जब आप Aspose.Words के साथ काम करते हैं और आपको DOCX फ़ाइल में **गायब फ़ॉन्ट्स** का पता लगाना हो। इस गाइड में हम एक पूर्ण, कॉपी‑एंड‑पेस्ट उदाहरण के माध्यम से दिखाएंगे कि IWarningCallback का उपयोग करके फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनियों को कैसे पकड़ें, यह क्यों महत्वपूर्ण है, और उन्हें पकड़ने के बाद क्या करना है।

यदि आपने कभी कोई दस्तावेज़ खोला है और कस्टम फ़ॉन्ट न स्थापित होने के कारण गड़बड़ टेक्स्ट देखा है, तो आप इस निराशा को समझते हैं। इस ट्यूटोरियल के अंत तक आपके पास इन समस्याओं को प्रोग्रामेटिक रूप से उजागर करने, लॉग करने या यहाँ तक कि स्वचालित रूप से फ़ॉलबैक फ़ॉन्ट लागू करने का भरोसेमंद तरीका होगा।

## आप क्या सीखेंगे

- **IWarningCallback** का उद्देश्य और इसे कब उपयोग करना है।  
- एक कस्टम वार्निंग कलेक्टर को लागू करना जो **detect missing fonts** इवेंट को अलग करता है।  
- **LoadOptions** में कलेक्टर को जोड़ना ताकि हर दस्तावेज़ लोड की निगरानी हो सके।  
- आउटपुट की पुष्टि करना और एज केस (एकाधिक गायब फ़ॉन्ट्स, साइलेंट वार्निंग्स, आदि) को संभालना।  

### पूर्वापेक्षाएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.6+ पर भी काम करता है)।  
- NuGet (`Install-Package Aspose.Words`) के माध्यम से Aspose.Words for .NET स्थापित होना चाहिए।  
- एक DOCX फ़ाइल जिसमें मशीन पर मौजूद नहीं होने वाला फ़ॉन्ट संदर्भित हो (उदाहरण के लिए `DocumentWithMissingFont.docx`)।  

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है—सब कुछ Aspose.Words के अंदर रहता है।

---

## Aspose.Words में गायब फ़ॉन्ट्स का पता लगाने के लिए IWarningCallback का उपयोग कैसे करें

नीचे **पूर्ण, चलाने योग्य प्रोग्राम** दिया गया है। इसे एक नए कंसोल प्रोजेक्ट में कॉपी करें, फ़ाइल पाथ समायोजित करें, और चलाएँ। आपको हर गायब‑फ़ॉन्ट चेतावनी के लिए कंसोल आउटपुट दिखाई देगा।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### अपेक्षित आउटपुट

यदि `DocumentWithMissingFont.docx` में *“MyFancyFont”* नाम का फ़ॉन्ट संदर्भित है जो स्थापित नहीं है, तो आपको कुछ इस तरह दिखेगा:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

प्रत्येक पंक्ति जो **[Missing Font]** से शुरू होती है, हमारी **IWarningCallback** इम्प्लीमेंटेशन द्वारा जेनरेट की गई है, यह सिद्ध करती है कि हमने सफलतापूर्वक **detect missing fonts** किया है।

---

## चरण 1: IWarningCallback इंटरफ़ेस को लागू करें

हमें कस्टम क्लास की क्यों जरूरत है? Aspose.Words विभिन्न कारणों से **वार्निंग्स** उठाता है—फ़ाइल फ़ॉर्मेट समस्याएँ, डिप्रिकेटेड फीचर्स, और हमारे लिए सबसे महत्वपूर्ण फ़ॉन्ट सब्स्टिट्यूशन। `IWarningCallback` को लागू करके हमें एक हुक मिलता है जो हर वार्निंग को वास्तविक समय में प्राप्त करता है। `WarningType.FontSubstitution` के लिए फ़िल्टर करने से वह विशेष स्थिति अलग हो जाती है जहाँ फ़ॉन्ट गायब है।

**Pro tip:** यदि आपको डायग्नॉस्टिक्स के लिए *सभी* वार्निंग्स कैप्चर करनी हैं, तो बस `if` चेक को हटा दें और हर `info.Type` को लॉग करें।

## चरण 2: LoadOptions में कॉलबैक को जोड़ें

`LoadOptions` वह गेटवे है जो Aspose.Words को बताता है कि आने वाले दस्तावेज़ को कैसे संभालना है। `WarningCallback` को हमारे कलेक्टर की इंस्टेंस पर सेट करने से कॉलबैक पूरे लोड ऑपरेशन के दौरान सक्रिय रहता है। आप एक ही `LoadOptions` ऑब्जेक्ट को कई दस्तावेज़ों के लिए पुनः उपयोग कर सकते हैं, जो बैच‑प्रोसेसिंग पाइपलाइन में सुविधाजनक है।

**Common question:** *यदि मैं LoadOptions निर्दिष्ट किए बिना दस्तावेज़ लोड करता हूँ तो क्या होगा?*  
Answer: Aspose.Words अभी भी आंतरिक रूप से वार्निंग्स उठाएगा, लेकिन बिना कॉलबैक के वे चुपचाप डिस्कार्ड हो जाएँगे, और आप **detect missing fonts** करने का मौका खो देंगे।

## चरण 3: एक दस्तावेज़ लोड करें और गायब फ़ॉन्ट चेतावनियों को कैप्चर करें

फ़ाइल पाथ और `LoadOptions` लेने वाला `Document` कंस्ट्रक्टर भारी काम करता है। फ़ाइल पार्स होते ही, कोई भी गायब फ़ॉन्ट हमारे `FontWarningCollector.Warning` मेथड को ट्रिगर करता है। कंसोल आउटपुट इस मैकेनिज़्म की सफलता को प्रमाणित करता है।

**Edge case:** एक ही दस्तावेज़ कई अनुपलब्ध फ़ॉन्ट्स का संदर्भ दे सकता है। कॉलबैक प्रत्येक गायब फ़ॉन्ट पर एक बार फायर होता है, इसलिए आपको कई पंक्तियाँ मिलेंगी—सम्पूर्ण रिपोर्ट बनाने के लिए यह आदर्श है।

## मैनुअल फ़ॉन्ट जांच के बजाय IWarningCallback का उपयोग क्यों करें?

आप दस्तावेज़ लोड होने के बाद `Run.Font` प्रॉपर्टीज़ को मैन्युअली स्कैन कर सकते हैं, लेकिन यह तभी संभव है जब दस्तावेज़ सफलतापूर्वक लोड हो—जो तब विफल हो जाता है जब फ़ॉन्ट पूरी तरह अनुपलब्ध हो। वार्निंग सिस्टम **सब्स्टिट्यूशन होने से पहले** काम करता है, जिससे आपको वास्तव में क्या गायब है, इसका स्पष्ट चित्र मिलता है।

इसके अतिरिक्त, कॉलबैक **लोडिंग पाइपलाइन के हिस्से के रूप में** चलता है, जिससे आप जल्दी abort कर सकते हैं, फ़ॉन्ट्स को ऑन‑द‑फ़्लाई बदल सकते हैं, या दस्तावेज़ ट्री पर अतिरिक्त पास किए बिना विस्तृत डायग्नॉस्टिक्स लॉग कर सकते हैं।

## कई गायब फ़ॉन्ट्स को सहजता से संभालना

यदि आप कई गायब फ़ॉन्ट्स की उम्मीद करते हैं, तो उन्हें एक कलेक्शन में एकत्र करने पर विचार करें:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

लोडिंग के बाद, आप `MissingFonts` पर इटररेट कर सकते हैं और उदाहरण के तौर पर उन्हें डिज़ाइन टीम के लिए CSV फ़ाइल में लिख सकते हैं।

## बोनस: चेतावनियों को फ़ाइल में लॉग करना

डेमो के लिए कंसोल आउटपुट ठीक है, लेकिन प्रोडक्शन कोड आमतौर पर स्थायी स्टोर में लॉग करता है। `Console.WriteLine` कॉल को इस प्रकार बदलें:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

अब आपके पास एक ऑडिट ट्रेल है जिसे बाद में रिव्यू किया जा सकता है, जिससे कंप्लायंस आवश्यकताओं को पूरा किया जा सके।

## निष्कर्ष

हमने **IWarningCallback का उपयोग कैसे करें** को **Aspose.Words में गायब फ़ॉन्ट्स का पता लगाने** के लिए कवर किया, कॉलबैक को लागू करने से लेकर `LoadOptions` में जोड़ने और प्राप्त वार्निंग्स को संभालने तक। यह दृष्टिकोण आपको फ़ॉन्ट‑संबंधी समस्याओं पर रीयल‑टाइम अंतर्दृष्टि देता है, जिससे आप लॉग, रिप्लेस या उपयोगकर्ताओं को रेंडरिंग से पहले ही अलर्ट कर सकते हैं।

आगे आप निम्नलिखित कदमों को एक्सप्लोर कर सकते हैं:

- **Fallback fonts:** जब सब्स्टिट्यूशन हो तो प्रोग्रामेटिक रूप से डिफ़ॉल्ट फ़ॉन्ट असाइन करें।  
- **Batch processing:** दस्तावेज़ों के फ़ोल्डर पर लूप चलाएँ, वही `AggregatingFontCollector` पुनः उपयोग करें।  
- **User feedback:** कंसोल के बजाय UI में गायब‑फ़ॉन्ट वार्निंग्स दिखाएँ।

इसे अपने प्रोजेक्ट में आज़माएँ—अब कोई रहस्यमय गड़बड़ टेक्स्ट नहीं, सिर्फ स्पष्ट, कार्यात्मक डायग्नॉस्टिक्स। Happy coding!

## आप आगे क्या सीखें?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}