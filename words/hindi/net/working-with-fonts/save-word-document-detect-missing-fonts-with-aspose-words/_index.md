---
category: general
date: 2026-03-22
description: Aspose.Words का उपयोग करके Word दस्तावेज़ सहेजें और लापता फ़ॉन्ट्स का
  पता लगाएँ। जानें कि कैसे लापता फ़ॉन्ट्स को ट्रैक करें और C# में फ़ॉन्ट त्रुटियों
  को कैप्चर करें।
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: hi
og_description: C# में Word दस्तावेज़ सहेजें और लापता फ़ॉन्ट्स का पता लगाएँ। यह गाइड
  दिखाता है कि लापता फ़ॉन्ट्स को कैसे ट्रैक करें और चेतावनी कॉलबैक का उपयोग करके फ़ॉन्ट
  त्रुटियों को कैसे कैप्चर करें।
og_title: वर्ड दस्तावेज़ सहेजें – Aspose.Words के साथ गायब फ़ॉन्ट्स का पता लगाएँ
tags:
- Aspose.Words
- C#
- Document Processing
title: वर्ड दस्तावेज़ सहेजें – Aspose.Words के साथ लापता फ़ॉन्ट्स का पता लगाएँ
url: /hi/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ सहेजें – Aspose.Words के साथ गायब फ़ॉन्ट्स का पता लगाएँ

क्या आपको कभी **Word दस्तावेज़ सहेजना** पड़ा और यह नहीं पता था कि अंदर के कुछ फ़ॉन्ट्स राउंड‑ट्रिप में बचेंगे या नहीं? यह आपके सोच से अधिक बार होता है, ख़ासकर जब दस्तावेज़ विभिन्न फ़ॉन्ट लाइब्रेरी वाले मशीनों के बीच घूमते हैं। अच्छी खबर? Aspose.Words आपको एक बिल्ट‑इन तरीका देता है **गायब फ़ॉन्ट्स का पता लगाने** का, जब आप **Word दस्तावेज़ सहेजते** हैं, ताकि आप उन्हें लॉग, चेतावनी दे या फ़ाइल उपयोगकर्ता की स्क्रीन पर पहुँचने से पहले बदल सकें।

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने योग्य उदाहरण के माध्यम से चलेंगे, जो न केवल Word दस्तावेज़ सहेजता है बल्कि **गायब फ़ॉन्ट्स को ट्रैक** करता है और **फ़ॉन्ट त्रुटियों को कैप्चर** करता है एक कस्टम वार्निंग हैंडलर की मदद से। अंत तक आप समझ जाएंगे कि वार्निंग कॉलबैक क्यों महत्वपूर्ण है, इसे कैसे जोड़ना है, और जब प्रतिस्थापन होता है तो कंसोल आउटपुट कैसा दिखता है। कोई अतिरिक्त फज़ूल बातें नहीं—सिर्फ वह कोड जिसे आप अभी .NET प्रोजेक्ट में डाल सकते हैं।

> **Prerequisites**  
> • .NET 6 (या कोई भी हालिया .NET Framework) स्थापित हो  
> • Visual Studio 2022 या आपका पसंदीदा IDE  
> • **Aspose.Words for .NET** की लाइसेंस प्राप्त कॉपी (टेस्टिंग के लिए फ्री ट्रायल चलती है)  

यदि आपके पास ये सब है, तो चलिए शुरू करते हैं।

---

## Word दस्तावेज़ सहेजें और गायब फ़ॉन्ट्स का पता लगाएँ

मुख्य विचार सरल है: `Document.Save` को कॉल करने से पहले, `Document.WarningCallback` को एक ऐसा ऑब्जेक्ट असाइन करें जो `IWarningCallback` को इम्प्लीमेंट करता हो। Aspose.Words इस ऑब्जेक्ट को हर वार्निंग के लिए कॉल करेगा, जिसमें **फ़ॉन्ट प्रतिस्थापन** वार्निंग भी शामिल है जब स्रोत दस्तावेज़ ऐसे फ़ॉन्ट का रेफ़रेंस देता है जो आपके सिस्टम में नहीं मिला।

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**आप क्या देखेंगे:**  
यदि `input.docx` ऐसा फ़ॉन्ट रेफ़रेंस करता है जो इंस्टॉल नहीं है, तो कंसोल कुछ इस तरह प्रिंट करेगा:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

यह लाइन आपको बिल्कुल बताती है कि कौन सा फ़ॉन्ट गायब था और Aspose.Words ने किस फ़ॉन्ट को बदले में इस्तेमाल किया—फ़ाइल शिप करने से पहले **फ़ॉन्ट त्रुटियों को कैप्चर** करने के लिए एकदम सही।

---

## Warning Callback के साथ गायब फ़ॉन्ट्स को ट्रैक करें (Step‑by‑Step)

### 1️⃣ Aspose.Words इंस्टॉल करें

अपने प्रोजेक्ट के NuGet कंसोल को खोलें और चलाएँ:

```bash
dotnet add package Aspose.Words
```

यह नवीनतम स्थिर संस्करण (वर्तमान में 24.10) को डाउनलोड करेगा। लाइब्रेरी को अप‑टू‑डेट रखना सुनिश्चित करता है कि आपको नवीनतम **गायब फ़ॉन्ट्स का पता लगाने** की क्षमताएँ और बग फिक्स मिलें।

### 2️⃣ Warning Handler परिभाषित करें

हमें एक अलग क्लास की क्यों ज़रूरत है? `IWarningCallback` को इम्प्लीमेंट करने से आप सभी वार्निंग लॉजिक को एक जगह केंद्रीकृत कर सकते हैं। आप फ़ाइल में लॉग कर सकते हैं, टेलीमेट्री भेज सकते हैं, या यदि आपके वर्कफ़्लो में गायब फ़ॉन्ट एक गंभीर त्रुटि है तो एक्सेप्शन भी थ्रो कर सकते हैं।

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** यदि आपको कई दस्तावेज़ों में **गायब फ़ॉन्ट्स को ट्रैक** करना है, तो हैंडलर के अंदर `List<string>` में संदेशों को स्टोर करें और बाद में रिपोर्टिंग के लिए एक्सपोज़ करें।

### 3️⃣ अपना स्रोत दस्तावेज़ लोड करें

`Document` कंस्ट्रक्टर फ़ाइल पाथ, स्ट्रीम, या यहाँ तक कि रॉ बाइट्स को भी स्वीकार कर सकता है। अधिकांश मामलों में आप इसे उस `.docx` फ़ाइल की ओर इंगित करेंगे जो आपको उपयोगकर्ता या किसी अन्य सिस्टम से मिली है।

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

यदि फ़ाइल बड़ी है, तो मेमोरी प्रेशर कम करने के लिए `LoadOptions` के साथ लेज़ी लोडिंग सक्षम करने पर विचार करें।

### 4️⃣ Callback अटैच करें

इंस्टेंस को `doc.WarningCallback` को असाइन करें। इस बिंदु से आगे, हर वार्निंग (फ़ॉन्ट प्रतिस्थापन सहित) आपके हैंडलर के माध्यम से जाएगी।

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ दस्तावेज़ सहेजें

अब आप सुरक्षित रूप से `Save` को कॉल कर सकते हैं। वार्निंग हैंडलर **सिंक्रोनस** रूप से सेव ऑपरेशन के दौरान चलता है, इसलिए आउटपुट तुरंत दिखेगा।

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

यदि आप किसी अलग फ़ॉर्मेट (PDF, HTML, आदि) में सहेजना पसंद करते हैं, तो वही वार्निंग मैकेनिज़्म काम करेगा—Aspose.Words अभी भी कन्वर्ज़न से पहले गायब फ़ॉन्ट्स की रिपोर्ट करेगा।

---

## फ़ॉन्ट त्रुटियों को कैप्चर करें – सामान्य एज केस

बेसिक फ्लो अधिकांश परिदृश्यों को कवर करता है, लेकिन वास्तविक प्रोजेक्ट अक्सर कुछ अड़चनें पेश करते हैं। नीचे कुछ वैरिएशन दिए गए हैं जो आप देख सकते हैं और उन्हें कैसे हैंडल करें।

### Header/Footer में गायब फ़ॉन्ट

हेडर और फुटर अलग नोड्स होते हैं, लेकिन वार्निंग सिस्टम उन्हें बॉडी टेक्स्ट की तरह ही ट्रीट करता है। अतिरिक्त कोड की ज़रूरत नहीं; कॉलबैक उन फ़ॉन्ट्स के लिए भी फायर होगा। बस यह सुनिश्चित करें कि आप पूरा दस्तावेज़ लोड करें (डिफ़ॉल्ट व्यवहार यह करता है)।

### एक दस्तावेज़ में कई प्रतिस्थापन

यदि दस्तावेज़ कई अज्ञात फ़ॉन्ट्स इस्तेमाल करता है, तो हैंडलर प्रत्येक प्रतिस्थापन के लिए एक बार कॉल होगा। कंसोल को फ़्लडिंग से बचाने के लिए आप संदेशों को डिडुप्लिकेट कर सकते हैं:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### वार्निंग को एक्सेप्शन में बदलें

कभी‑कभी गायब फ़ॉन्ट एक डील‑ब्रेकर होता है। हैंडलर के अंदर एक्सेप्शन थ्रो करके सेव को एबॉर्ट कर सकते हैं:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

`doc.Save` को `try/catch` ब्लॉक में रैप करना न भूलें ताकि एक्सेप्शन को ग्रेसफ़ुली हैंडल किया जा सके।

---

## परिणाम सत्यापित करें – क्या उम्मीद करें

सेव पूरा होने के बाद, `output.docx` को Microsoft Word (या कोई भी संगत व्यूअर) में खोलें। आपको मूल लेआउट जैसा ही दिखना चाहिए, लेकिन प्रतिस्थापित फ़ॉन्ट्स कंसोल में देखे गए फॉलबैक के रूप में दिखेंगे। दोबारा जाँचने के लिए आप कर सकते हैं:

1. **File → Options → Advanced → Show document content → Use draft quality** खोलें – यह Word को किसी भी छिपे फ़ॉन्ट प्रतिस्थापन को दिखाने के लिए मजबूर करता है।  
2. Word के **Replace Fonts** डायलॉग (`Ctrl+Shift+F`) का उपयोग करके देखें कि वास्तव में कौन से फ़ॉन्ट एम्बेडेड हैं।

यदि सब कुछ मेल खाता है, तो आपने सफलतापूर्वक **Word दस्तावेज़ सहेजा** जबकि **गायब फ़ॉन्ट्स का पता लगाया**, और **फ़ॉन्ट त्रुटियों को कैप्चर** किया। 🎉

---

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

नीचे पूरा प्रोग्राम दिया गया है जिसे आप नई Console App प्रोजेक्ट में डाल सकते हैं। केवल `YOUR_DIRECTORY` को अपने मशीन पर वास्तविक फ़ोल्डर पाथ से बदलें।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**अपेक्षित कंसोल आउटपुट** (उदाहरण):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

यही पूरी कहानी है—कोई छिपे कदम नहीं, कोई बाहरी डॉक्यूमेंट नहीं जिसे आपको ढूँढ़ना पड़े।

---

## निष्कर्ष

हमने अभी दिखाया कि कैसे **Word दस्तावेज़ सहेजें** जबकि सक्रिय रूप से **गायब फ़ॉन्ट्स का पता लगाएँ**, **गायब फ़ॉन्ट्स को ट्रैक करें**, और **फ़ॉन्ट त्रुटियों को कैप्चर** करें Aspose.Words के वार्निंग कॉलबैक की मदद से। एक छोटा `IWarningCallback` इम्प्लीमेंटेशन जोड़कर, आप सेव टाइम पर फ़ॉन्ट प्रतिस्थापन की पूरी दृश्यता प्राप्त करते हैं, जिससे आप लॉग, बदल या एबॉर्ट कर सकते हैं।  

अगली चुनौती के लिए तैयार हैं? हैंडलर को विस्तारित करके वार्निंग को स्ट्रक्चर्ड JSON लॉग में लिखें, या इसे Aspose.PDF के साथ मिलाकर वही दस्तावेज़ कन्वर्ट करें जबकि फ़ॉन्ट जानकारी सुरक्षित रहे। आप `LoadOptions.FontSettings` के ज़रिए आउटपुट फ़ाइल में सीधे गायब फ़ॉन्ट्स एम्बेड भी कर सकते हैं।  

इसे आज़माएँ, कोड को अपने पाइपलाइन के अनुसार ट्यून करें, और हमें बताएं कि यह आपके लिए कैसे काम करता है। Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}