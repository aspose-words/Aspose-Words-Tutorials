---
category: general
date: 2026-04-21
description: Aspose.Words in C# के साथ फ़ॉन्ट का पता लगाना, चेतावनियों को कैप्चर करना,
  कॉलबैक कॉन्फ़िगर करना और चेतावनियों को सूचीबद्ध करना सीखें। विश्वसनीय फ़ॉन्ट हैंडलिंग
  के लिए चरण‑दर‑चरण गाइड।
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: hi
og_description: Aspose.Words में फ़ॉन्ट्स का पता कैसे लगाएँ? यह ट्यूटोरियल आपको दिखाता
  है कि चेतावनियों को कैसे कैप्चर करें, कॉलबैक को कैसे कॉन्फ़िगर करें, और C# में चेतावनियों
  को कैसे सूचीबद्ध करें।
og_title: Aspose.Words में फ़ॉन्ट कैसे पहचानें – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words में फ़ॉन्ट कैसे पहचानें – पूर्ण गाइड
url: /hi/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में फ़ॉन्ट्स का पता कैसे लगाएँ – पूर्ण गाइड

क्या आपने कभी सोचा है **फ़ॉन्ट्स का पता कैसे लगाएँ** जब आप एक Word दस्तावेज़ लोड करते हैं और कुछ फ़ॉन्ट्स गायब होते हैं? यह वह स्थिति है जो अक्सर सामने आती है, ख़ासकर जब आप लेगेसी फ़ाइलों या क्रॉस‑प्लेटफ़ॉर्म डिप्लॉयमेंट्स के साथ काम कर रहे हों। इस ट्यूटोरियल में हम एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से दिखाएंगे कि **चेतावनियों को कैसे कैप्चर करें**, **कॉलबैक को कैसे कॉन्फ़िगर करें**, और **चेतावनियों को कैसे सूचीबद्ध करें** ताकि आपको हमेशा पता रहे कि कौन‑से फ़ॉन्ट्स बदल दिए गए थे।

हम Aspose.Words for .NET (लेखन के समय v24.9) और साधारण C# का उपयोग करेंगे। कोई बाहरी सर्विस नहीं, कोई जादू नहीं—सिर्फ API और कुछ पंक्तियों का कोड। अंत तक आप हर फ़ॉन्ट प्रतिस्थापन को पहचान पाएँगे, उसे लॉग करेंगे, और यदि कोई महत्वपूर्ण फ़ॉन्ट गायब हो तो लोड को रोकने का विकल्प भी रखेंगे।  

### आपको क्या चाहिए
- **Aspose.Words for .NET** (NuGet से इंस्टॉल करें: `Install-Package Aspose.Words`)
- .NET 6.0 या बाद का संस्करण (कोड .NET Framework पर भी चलता है)
- एक नमूना DOCX जिसमें ऐसी फ़ॉन्ट का रेफ़रेंस हो जो मशीन पर मौजूद नहीं है (उदाहरण के लिए “MyCustomFont.ttf”)
- Visual Studio, Rider, या कोई भी C# एडिटर जो आपको पसंद हो

> **Pro tip:** यदि आपके पास गायब फ़ॉन्ट वाला दस्तावेज़ नहीं है, तो बस अपने सिस्टम में किसी फ़ॉन्ट फ़ाइल का नाम बदल दें या DOCX XML को संपादित करके एक गैर‑मौजूद फ़ॉन्ट फ़ैमिली का रेफ़रेंस जोड़ दें।

---

## Aspose.Words के साथ फ़ॉन्ट्स का पता कैसे लगाएँ

मुख्य विचार यह है कि Aspose.Words की चेतावनी प्रणाली में हुक करें। जब लाइब्रेरी को अनुरोधित फ़ॉन्ट नहीं मिलता, तो वह `WarningType.FontSubstitution` चेतावनी उत्पन्न करती है। एक कस्टम `IWarningCallback` इम्प्लीमेंटेशन प्रदान करके आप **फ़ॉन्ट्स का पता लगा सकते हैं** जो लोड प्रक्रिया के दौरान बदल दिए गए थे।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Why this works:** Aspose.Words हर गैर‑क्रिटिकल मुद्दे के लिए `Warning` मेथड को कॉल करता है। `WarningInfo` ऑब्जेक्ट्स को स्टोर करके आपको प्रकार, संदेश, और संदर्भ तक पूरी पहुँच मिलती है, जो ठीक वही है जिसकी आपको **फ़ॉन्ट्स का पता लगाने** के लिए आवश्यकता है।

---

## दस्तावेज़ लोड करते समय चेतावनियों को कैसे कैप्चर करें

अब जब हमारे पास एक कलेक्टर है, हमें `LoadOptions` को बताना होगा कि वह इसका उपयोग करे। यही **चेतावनियों को कैप्चर करने** का तरीका है।

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Edge case:** यदि आप दस्तावेज़ को स्ट्रीम से लोड करते हैं (`new Document(stream, loadOptions)`), तो वही कॉलबैक काम करता है—सिर्फ फ़ाइल पाथ की जगह स्ट्रीम पास करें।

इस चरण के बाद दस्तावेज़ पूरी तरह लोड हो जाता है, लेकिन सभी फ़ॉन्ट प्रतिस्थापन चेतावनियाँ `warningCollector.Warnings` में सुरक्षित रूप से संग्रहीत रहती हैं।

---

## चेतावनियों को सूचीबद्ध करें और फ़ॉन्ट प्रतिस्थापन की रिपोर्ट बनाएं

अंत में, हम एकत्रित चेतावनियों को फ़िल्टर करके **चेतावनियों को सूचीबद्ध** करते हैं जो विशेष रूप से फ़ॉन्ट प्रतिस्थापन से संबंधित हैं। यह चरण कच्चे डेटा को एक पठनीय रिपोर्ट में बदल देता है।

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**अपेक्षित आउटपुट** (उदाहरण):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

यदि दस्तावेज़ में कोई गायब फ़ॉन्ट नहीं है, तो लूप कोई आउटपुट नहीं देगा—कोई चिंता नहीं।

---

## पूर्ण कार्यशील उदाहरण (सभी चरण एक फ़ाइल में)

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉन्सोल प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं। यह **फ़ॉन्ट्स का पता कैसे लगाएँ**, **चेतावनियों को कैसे कैप्चर करें**, **कॉलबैक को कैसे कॉन्फ़िगर करें**, और **चेतावनियों को कैसे सूचीबद्ध करें** को एक ही प्रवाह में जोड़ता है।

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**इस प्रोग्राम को चलाने** पर Aspose.Words द्वारा बदले गए प्रत्येक फ़ॉन्ट का नाम प्रिंट होगा। आप आउटपुट को लॉग फ़ाइल में रीडायरेक्ट कर सकते हैं, अलर्ट जेनरेट कर सकते हैं, या यदि कोई महत्वपूर्ण फ़ॉन्ट गायब हो तो लोड को रोक भी सकते हैं।

---

## सामान्य प्रश्न और संभावित समस्याएँ

### यदि आवश्यक फ़ॉन्ट गायब हो तो लोडिंग को रोकना चाहूँ तो क्या करें?
आप कॉलबैक के भीतर `WarningInfo` ऑब्जेक्ट्स की जाँच कर सकते हैं और जब कोई विशेष फ़ॉन्ट नाम मिले तो एक्सेप्शन थ्रो कर सकते हैं। एक्सेप्शन लोड को रोक देगा, जिससे आपको पूर्ण नियंत्रण मिलेगा।

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### क्या यह PDFs या अन्य फ़ॉर्मैट्स के साथ भी काम करता है?
हां। Aspose.Words PDFs, RTF, और HTML के लिए भी वही चेतावनी इन्फ्रास्ट्रक्चर उपयोग करता है। फ़ाइल एक्सटेंशन बदलें और बाकी कोड समान रहेगा।

### चेतावनियों को कंसोल के बजाय फ़ाइल में कैसे लॉग करें?
`Console.WriteLine` को अपनी पसंद के किसी भी लॉगिंग फ्रेमवर्क (`Serilog`, `NLog`, आदि) से बदलें। `WarningInfo` क्लास `Message`, `Source` और `Exception` प्रदान करती है जिससे विस्तृत लॉग बन सके।

### क्या इससे प्रदर्शन पर असर पड़ेगा?
ओवरहेड नगण्य है—Aspose.Words पहले से ही चेतावनियों को जनरेट करता है। कॉलबैक जोड़ने से केवल उन्हें एक लिस्ट में स्टोर किया जाता है, जो चेतावनियों की संख्या के अनुसार O(n) है। सामान्य दस्तावेज़ों के लिए प्रभाव कुल लोड समय का 1 % से भी कम रहता है।

---

## दृश्य सारांश

![How to Detect Fonts in Aspose.Words – warning flow diagram](https://example.com/images/font-detection-diagram.png "how to detect fonts")

*Alt text:* **फ़ॉन्ट्स का पता कैसे लगाएँ** – डायग्राम जिसमें चेतावनी कॉलबैक, कलेक्शन, और एन्ह्यूमरेशन चरण दिखाए गए हैं।

---

## निष्कर्ष

हमने **फ़ॉन्ट्स का पता कैसे लगाएँ** Aspose.Words में **चेतावनियों को कैप्चर करके**, **कॉलबैक को कॉन्फ़िगर करके**, और **चेतावनियों को सूचीबद्ध करके** समझा। पूरा कोड सैंपल एक प्रोडक्शन‑रेडी पैटर्न दिखाता है जिसे आप किसी भी .NET एप्लिकेशन में उपयोग कर सकते हैं।  

आगे आप देख सकते हैं:

- **चेतावनियों को कैप्चर** करने के लिए अन्य मुद्दों (जैसे इमेज कन्वर्ज़न समस्याएँ) के लिए
- **कॉलबैक को कॉन्फ़िगर** करने के लिए कस्टम लॉगिंग फ्रेमवर्क
- **चेतावनियों को सूचीबद्ध** करने के लिए बैच जॉब में कई दस्तावेज़ों पर
- **Aspose.Words.Fonts.FontSettings** का उपयोग करके फ़ॉलबैक फ़ॉन्ट फ़ोल्डर सेट करना, जिससे प्रारम्भ में ही प्रतिस्थापनों की संख्या घटेगी

इसे आज़माएँ, कलेक्टर को अपनी लॉगिंग शैली के अनुसार अनुकूलित करें, और अब आप अनपेक्षित फ़ॉन्ट स्वैप से कभी आश्चर्यचकित नहीं होंगे। यदि कोई अजीब बात मिले, तो नीचे टिप्पणी करें—हैप्पी कोडिंग!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}