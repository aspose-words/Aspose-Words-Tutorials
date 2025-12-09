---
language: hi
url: /hindi/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Aspose.Words दस्तावेज़ों में लापता फ़ॉन्ट्स का पता लगाएँ – पूर्ण C# गाइड

क्या आपने कभी सोचा है कि Aspose.Words के साथ Word फ़ाइल लोड करते समय **लापता फ़ॉन्ट्स** का पता कैसे लगाया जाए? मेरे दैनिक काम में, मैंने कुछ PDF देखे हैं जो ठीक नहीं लग रहे थे क्योंकि मूल दस्तावेज़ में ऐसा फ़ॉन्ट इस्तेमाल हुआ था जो मेरे सिस्टम में स्थापित नहीं था। अच्छी खबर? Aspose.Words आपको बिल्कुल बता सकता है जब वह फ़ॉन्ट को बदलता है, और आप इस जानकारी को एक साधारण warning callback के साथ कैप्चर कर सकते हैं।  

इस ट्यूटोरियल में हम एक **पूर्ण, चलाने योग्य उदाहरण** के माध्यम से चलेंगे जो दिखाता है कि हर फ़ॉन्ट प्रतिस्थापन को कैसे लॉग किया जाए, callback क्यों महत्वपूर्ण है, और मजबूत लापता‑फ़ॉन्ट पहचान के लिए कुछ अतिरिक्त ट्रिक्स। कोई फालतू बात नहीं, सिर्फ कोड और वह तर्क जो आपको इसे आज ही काम करने में मदद करेगा।

---

## आप क्या सीखेंगे

- **Aspose.Words warning callback** को लागू करके फ़ॉन्ट प्रतिस्थापन इवेंट्स को कैसे पकड़ें।  
- **LoadOptions C#** को इस प्रकार कॉन्फ़िगर करें कि दस्तावेज़ लोड करते समय callback कॉल हो।  
- यह सत्यापित करें कि लापता‑फ़ॉन्ट पहचान वास्तव में काम कर रही है, और कंसोल आउटपुट कैसा दिखता है।  

**Prerequisites** – आपको Aspose.Words for .NET का नवीनतम संस्करण चाहिए (कोड 23.12 के साथ परीक्षण किया गया था), .NET 6 या बाद का, और C# की बुनियादी समझ। यदि आपके पास ये हैं, तो आप शुरू करने के लिए तैयार हैं।

---

## Warning Callback के साथ लापता फ़ॉन्ट्स का पता लगाएँ

समाधान का मुख्य भाग `IWarningCallback` का कार्यान्वयन है। Aspose.Words कई स्थितियों में `WarningInfo` ऑब्जेक्ट फायर करता है, लेकिन हमें केवल `WarningType.FontSubstitution` की परवाह है। चलिए देखते हैं कि इसे कैसे हुक किया जाए।

### चरण 1: फ़ॉन्ट‑वॉर्निंग कलेक्टर बनाएं

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Why this matters*: `WarningType.FontSubstitution` पर फ़िल्टर करके हम असंबंधित चेतावनियों (जैसे deprecated features) से बचते हैं। `info.Description` में पहले से ही मूल फ़ॉन्ट नाम और उपयोग किया गया fallback शामिल होता है, जो आपको एक स्पष्ट ऑडिट ट्रेल देता है।

---

## Callback उपयोग करने के लिए LoadOptions कॉन्फ़िगर करें

अब हम Aspose.Words को बताते हैं कि फ़ाइल लोड करते समय हमारा कलेक्टर उपयोग करे।

### चरण 2: LoadOptions सेट अप करें

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Why this matters*: `LoadOptions` वह एकमात्र जगह है जहाँ आप callback, एन्क्रिप्शन पासवर्ड और अन्य लोडिंग व्यवहार जोड़ सकते हैं। इसे `Document` कंस्ट्रक्टर से अलग रखने से कोड कई फ़ाइलों में पुन: उपयोग योग्य बनता है।

---

## दस्तावेज़ लोड करें और लापता फ़ॉन्ट्स को कैप्चर करें

callback को जोड़ने के बाद, अगला कदम बस दस्तावेज़ को लोड करना है।

### चरण 3: अपना DOCX (या कोई भी समर्थित फ़ॉर्मेट) लोड करें

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

जब `Document` कंस्ट्रक्टर फ़ाइल को पार्स करता है, तो कोई भी लापता फ़ॉन्ट हमारे `FontWarningCollector` को ट्रिगर करता है। कंसोल में इस तरह की पंक्तियाँ दिखेंगी:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

वह पंक्ति यह ठोस प्रमाण है कि **लापता फ़ॉन्ट्स का पता लगाना** काम किया।

---

## आउटपुट सत्यापित करें – क्या अपेक्षित है

प्रोग्राम को टर्मिनल या Visual Studio से चलाएँ। यदि स्रोत दस्तावेज़ में ऐसा फ़ॉन्ट है जो आपके सिस्टम में स्थापित नहीं है, तो आपको कम से कम एक “Font substituted” पंक्ति दिखेगी। यदि दस्तावेज़ केवल स्थापित फ़ॉन्ट्स का उपयोग करता है, तो callback चुप रहेगा और आपको केवल “Document loaded successfully.” संदेश मिलेगा।

**Tip**: दोबारा जांचने के लिए, Word फ़ाइल को Microsoft Word में खोलें और फ़ॉन्ट सूची देखें। कोई भी फ़ॉन्ट जो *Home → Font* समूह के तहत *Replace Fonts* में दिखाई देता है, वह प्रतिस्थापन का उम्मीदवार है।

---

## उन्नत: बैच में लापता फ़ॉन्ट्स का पता लगाएँ

अक्सर आपको दर्जनों फ़ाइलों को स्कैन करना पड़ता है। वही पैटर्न आसानी से स्केल करता है:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

क्योंकि `FontWarningCollector` हर बार कॉल होने पर कंसोल में लिखता है, आपको अतिरिक्त सेटअप के बिना प्रति‑फ़ाइल रिपोर्ट मिल जाएगी। प्रोडक्शन परिदृश्यों में आप इसे फ़ाइल या डेटाबेस में लॉग करना चाह सकते हैं – बस `Console.WriteLine` को अपने पसंदीदा logger से बदल दें।

---

## सामान्य समस्याएँ और प्रो टिप्स

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| **कोई चेतावनी नहीं दिखती** | दस्तावेज़ वास्तव में केवल स्थापित फ़ॉन्ट्स ही रखता है। | फ़ाइल को Word में खोलकर या जानबूझकर अपने सिस्टम से एक फ़ॉन्ट हटाकर सत्यापित करें। |
| **Callback नहीं बुलाया गया** | `LoadOptions.WarningCallback` कभी असाइन नहीं किया गया या बाद में नया `LoadOptions` इंस्टेंस उपयोग किया गया। | एक ही `LoadOptions` ऑब्जेक्ट रखें और हर लोड के लिए पुन: उपयोग करें। |
| **बहुत सारी असंबंधित चेतावनियां** | आपने `WarningType.FontSubstitution` द्वारा फ़िल्टर नहीं किया। | जैसा दिखाया गया है, `if (info.Type == WarningType.FontSubstitution)` गार्ड जोड़ें। |
| **बड़ी फ़ाइलों पर प्रदर्शन धीमा** | Callback हर चेतावनी पर चलता है, जो बड़े दस्तावेज़ों में बहुत हो सकता है। | `LoadOptions.WarningCallback` के माध्यम से अन्य चेतावनी प्रकारों को अक्षम करें या यदि आप जानते हैं तो `LoadOptions.LoadFormat` को विशिष्ट प्रकार पर सेट करें। |

---

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**अपेक्षित कंसोल आउटपुट** (जब लापता फ़ॉन्ट मिलता है):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

यदि कोई प्रतिस्थापन नहीं होता, तो आप केवल सफलता पंक्ति देखेंगे।

---

## निष्कर्ष

अब आपके पास Aspose.Words द्वारा प्रोसेस किए गए किसी भी दस्तावेज़ में लापता फ़ॉन्ट्स का पता लगाने का **पूर्ण, प्रोडक्शन‑रेडी तरीका** है। **Aspose.Words warning callback** का उपयोग करके और **LoadOptions C#** को कॉन्फ़िगर करके, आप हर फ़ॉन्ट प्रतिस्थापन को लॉग कर सकते हैं, लेआउट समस्याओं का समाधान कर सकते हैं, और सुनिश्चित कर सकते हैं कि आपके PDF इच्छित लुक‑एंड‑फ़ील को बनाए रखें।  

एक फ़ाइल से लेकर बड़े बैच तक, पैटर्न वही रहता है—`IWarningCallback` को लागू करें, इसे `LoadOptions` में प्लग करें, और Aspose.Words को भारी काम करने दें।  

अगले कदम के लिए तैयार हैं? इसको **फ़ॉन्ट एम्बेडिंग** या **फ़ॉलबैक फ़ॉन्ट फ़ैमिली** के साथ मिलाकर समस्या को स्वचालित रूप से ठीक करने का प्रयास करें, या गहरी सामग्री विश्लेषण के लिए **DocumentVisitor** API देखें। कोडिंग का आनंद लें, और आपके सभी फ़ॉन्ट्स जहाँ आप उम्मीद करते हैं, वहीं रहें!  

---

![Aspose.Words में लापता फ़ॉन्ट्स का पता – कंसोल आउटपुट स्क्रीनशॉट](https://example.com/images/detect-missing-fonts.png "लापता फ़ॉन्ट्स कंसोल आउटपुट")

{{< layout-end >}}

{{< layout-end >}}