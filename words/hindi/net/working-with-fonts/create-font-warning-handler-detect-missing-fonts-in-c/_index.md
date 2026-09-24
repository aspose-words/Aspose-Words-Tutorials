---
category: general
date: 2026-02-12
description: Aspose.Words में गायब फ़ॉन्ट्स का पता लगाने और उनका ट्रैक रखने के लिए
  फ़ॉन्ट वार्निंग हैंडलर बनाएं। जानें कि वार्निंग्स को प्रभावी ढंग से कैसे लॉग करें।
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: hi
og_description: C# में फ़ॉन्ट चेतावनी हैंडलर बनाएं ताकि गायब फ़ॉन्ट्स का पता लगाया
  जा सके और Aspose.Words फ़ॉन्ट बदलने पर चेतावनियों को लॉग करने का तरीका सीखें।
og_title: फ़ॉन्ट चेतावनी हैंडलर बनाएं – लापता फ़ॉन्ट का पता लगाएँ
tags:
- Aspose.Words
- C#
- Document Processing
title: फ़ॉन्ट चेतावनी हैंडलर बनाएं – C# में गायब फ़ॉन्ट्स का पता लगाएँ
url: /hi/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ॉन्ट चेतावनी हैंडलर बनाएं – C# में लापता फ़ॉन्ट का पता लगाएँ

क्या आपको कभी **फ़ॉन्ट चेतावनी हैंडलर बनाना** पड़ा है क्योंकि कोई Word दस्तावेज़ चुपचाप वह फ़ॉन्ट बदल देता है जिसकी आप उम्मीद नहीं कर रहे थे? आप अकेले नहीं हैं। जब Aspose.Words एक DOCX लोड करता है जिसमें सर्वर पर उपलब्ध नहीं होने वाला फ़ॉन्ट संदर्भित होता है, तो यह चुपचाप डिफ़ॉल्ट फ़ॉन्ट पर स्विच कर देता है—जिससे आपका लेआउट सूक्ष्म रूप से बिगड़ जाता है।  

इस ट्यूटोरियल में हम आपको ठीक‑ठीक दिखाएंगे कि **लापता फ़ॉन्ट्स का पता कैसे लगाएँ**, **लापता फ़ॉन्ट्स को ट्रैक कैसे करें**, और **चेतावनियों को कैसे लॉग करें** ताकि आप उन प्रतिस्थापनों को पहले ही पकड़ सकें। अंत तक आपके पास एक पुन: उपयोग योग्य चेतावनी हैंडलर होगा जो प्रत्येक फ़ॉन्ट‑सब्स्टिट्यूशन इवेंट को कंसोल (या आपके पसंदीदा लॉगर) पर प्रिंट करता है। कोई रहस्य नहीं, केवल स्पष्ट, कार्यात्मक कोड।

## Prerequisites

- .NET 6.0 या बाद का संस्करण (API .NET Framework 4.6+ के लिए भी समान है)
- Aspose.Words for .NET स्थापित है (`dotnet add package Aspose.Words`)
- एक Word फ़ाइल जो आपके मशीन पर स्थापित नहीं किए गए फ़ॉन्ट को संदर्भित करती है (उदा., `MissingFont.docx`)

यदि आपके पास ये सब हैं, बढ़िया—चलें शुरू करते हैं।

## चरण 1: Warning Callback के साथ LoadOptions सेट करें  

जब आप **फ़ॉन्ट चेतावनी हैंडलर बनाना** चाहते हैं, तो पहला काम Aspose.Words को बताना है कि उसे समस्या मिलने पर एक कॉलबैक फायर करना चाहिए। `LoadOptions` इस कॉन्फ़िगरेशन का कंटेनर है।

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**यह क्यों महत्वपूर्ण है:**  
`LoadOptions` वह एकमात्र जगह है जहाँ आप `IWarningCallback` को प्लग‑इन कर सकते हैं। इसके बिना, Aspose.Words आंतरिक रूप से चेतावनियों को लॉग करेगा लेकिन आप उन्हें कभी नहीं देख पाएंगे। `FontWarningHandler` को असाइन करके हम लापता फ़ॉन्ट के प्रतिस्थापन होने पर पूरी तरह से नियंत्रण प्राप्त करते हैं।

## चरण 2: FontWarningHandler क्लास लागू करें  

अब हम वास्तव में **फ़ॉन्ट चेतावनी हैंडलर** कोड बनाते हैं। यह क्लास `IWarningCallback` को इम्प्लीमेंट करती है और Aspose.Words द्वारा उठाई गई प्रत्येक चेतावनी के लिए एक `WarningInfo` ऑब्जेक्ट प्राप्त करती है।

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**व्याख्या:**  
- `info.Type` हमें चेतावनी की श्रेणी बताता है। हम `WarningType.FontSubstitution` में रुचि रखते हैं क्योंकि यह लापता फ़ॉन्ट को दर्शाता है।  
- `info.Description` में एक मानव‑पठनीय संदेश होता है जैसे *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- `Console.WriteLine` में लिखकर हम **चेतावनियों को तुरंत लॉग** करते हैं। वास्तविक एप्लिकेशन में आप इसे `ILogger`, फ़ाइल राइटर, या टेलीमेट्री सर्विस से बदल सकते हैं।  

> **प्रो टिप:** यदि आपको बाद में रिपोर्टिंग के लिए सभी लापता फ़ॉन्ट एकत्र करने की आवश्यकता है, तो `info.Description` को `List<string>` में संग्रहित करें बजाय उसे प्रिंट करने के।

## चरण 3: कॉन्फ़िगर किए गए LoadOptions का उपयोग करके दस्तावेज़ लोड करें  

कॉलबैक सेट होने पर, दस्तावेज़ लोड करने से स्वचालित रूप से हमारा हैंडलर तब ट्रिगर होगा जब भी कोई फ़ॉन्ट लापता होगा।

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**आपको क्या दिखेगा:**  
प्रोग्राम चलाने पर कुछ इस तरह प्रिंट होगा:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

यह पंक्ति पुष्टि करती है कि आपने सफलतापूर्वक **लापता फ़ॉन्ट्स का पता लगा लिया** है और अब वास्तविक समय में **लापता फ़ॉन्ट्स को ट्रैक** कर रहे हैं।

## चरण 4: विभिन्न परिदृश्यों में हैंडलर की जाँच करें  

हैंडलर केवल DOCX फ़ाइलों के लिए काम करता है, यह मानना आसान है, लेकिन Aspose.Words कई फ़ॉर्मेट्स को सपोर्ट करता है। एक PDF लोड करने की कोशिश करें जिसमें एम्बेडेड फ़ॉन्ट का संदर्भ हो, या पुरानी `.doc` फ़ाइल। वही कॉलबैक किसी भी फ़ॉर्मेट के लिए फायर होता है जो फ़ॉन्ट‑रिज़ॉल्यूशन पाइपलाइन से गुजरता है।

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

यदि PDF में ऐसा फ़ॉन्ट संदर्भित है जो स्थापित नहीं है, तो आपको वही कंसोल आउटपुट मिलेगा। यह दर्शाता है कि आपका **फ़ॉन्ट चेतावनी हैंडलर** समाधान फ़ॉर्मेट‑अज्ञेय है।

## चरण 5: हैंडलर को विस्तारित करना – फ़ाइल में लॉगिंग  

डेमो के लिए कंसोल आउटपुट सुविधाजनक है, लेकिन प्रोडक्शन कोड आमतौर पर लॉग फ़ाइल में लिखता है। यहाँ एक त्वरित बदलाव है।

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

अब हर बार जब फ़ॉन्ट प्रतिस्थापित होता है, संदेश `font-warnings.log` में जोड़ दिया जाता है। यह **चेतावनियों को कैसे लॉग करें** भाग को पूरा करता है और आपको एक स्थायी ऑडिट ट्रेल देता है।

## चरण 6: सब कुछ एक साथ रखें – पूर्ण, चलाने योग्य उदाहरण  

नीचे पूरा प्रोग्राम है जिसे आप कॉन्सोल ऐप में कॉपी‑पेस्ट कर सकते हैं। कोई हिस्सा गायब नहीं है; केवल फ़ाइल पाथ को अपने दस्तावेज़ के साथ बदलें।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**अपेक्षित परिणाम:**  

- कंसोल प्रत्येक प्रतिस्थापन पंक्ति को प्रिंट करता है।  
- `font-warnings.log` अब प्रत्येक लापता‑फ़ॉन्ट इवेंट का टाइमस्टैम्प वाला रिकॉर्ड रखता है।  
- `output.pdf` फ़ाइल प्रतिस्थापित फ़ॉन्ट्स का उपयोग करके बनाई गई है, जिससे मूल फ़ॉन्ट उपलब्ध न होने पर भी रूपांतरण सफल हो जाता है।

## सामान्य प्रश्न और किनारे के मामले  

| प्रश्न | उत्तर |
|----------|--------|
| *यदि मैं कुछ फ़ॉन्ट्स को अनदेखा करना चाहूँ तो?* | `Warning` के अंदर, फ़ॉन्ट नाम के लिए `info.Description` जांचें और उन फ़ॉन्ट्स के लिए जो आप स्वीकार्य मानते हैं, जल्दी `return;` करें। |
| *क्या हैंडलर एम्बेडेड फ़ॉन्ट्स के लिए फायर करेगा?* | नहीं—एम्बेडेड फ़ॉन्ट्स हमेशा दस्तावेज़ के लिए उपलब्ध होते हैं, इसलिए कोई प्रतिस्थापन चेतावनी नहीं आती। |
| *क्या मैं अन्य चेतावनी प्रकारों (जैसे, image‑resolution issues) को कैप्चर कर सकता हूँ?* | बिल्कुल। `if (info.Type == WarningType.FontSubstitution)` गार्ड को हटाएँ या `WarningType.ImageResolution` के लिए अतिरिक्त `if` ब्लॉक्स जोड़ें। |
| *क्या हैंडलर थ्रेड‑सेफ़ है?* | दिखाए गए डिफ़ॉल्ट इम्प्लीमेंटेशन फ़ाइल में बिना सिंक्रोनाइज़ेशन के लिखता है। मल्टी‑थ्रेडेड परिदृश्यों के लिए, फ़ाइल लिखने को लॉक में रैप करें या एक concurrent logger उपयोग करें। |

## अगले कदम  

अब जब आप लापता फ़ॉन्ट्स के लिए **चेतावनियों को कैसे लॉग करें** जानते हैं, आप चाह सकते हैं:

- **बैच इम्पोर्ट प्रक्रिया** के दौरान लापता फ़ॉन्ट्स का पता लगाएँ और एक सारांश रिपोर्ट बनाएं।  
- कई दस्तावेज़ों में लापता फ़ॉन्ट्स को ट्रैक करें और जब कोई विशेष फ़ॉन्ट बार‑बार दिखाई दे तो ईमेल अलर्ट भेजें।  
- एक मॉनिटरिंग सिस्टम (जैसे, Azure Application Insights) के साथ इंटीग्रेट करें ताकि समय के साथ फ़ॉन्ट‑सब्स्टिट्यूशन ट्रेंड दिखाए जा सकें।  

इन सभी एक्सटेंशन का आधार वही `IWarningCallback` फाउंडेशन है जिसे हमने बनाया।

*हैप्पी कोडिंग! यदि आपको कोई अजीब समस्या आती है—शायद कस्टम फ़ॉन्ट फ़ोल्डर या नेटवर्क शेयर—नीचे टिप्पणी छोड़ें। समुदाय (और मैं) हमेशा आपके फ़ॉन्ट‑चेतावनी रणनीति को फाइन‑ट्यून करने में मदद करने के लिए तैयार हैं।*  

![फ़ॉन्ट चेतावनी हैंडलर उदाहरण](image-placeholder.png "फ़ॉन्ट चेतावनी हैंडलर उदाहरण")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}