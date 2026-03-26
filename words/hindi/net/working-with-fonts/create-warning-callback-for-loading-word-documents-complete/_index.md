---
category: general
date: 2026-03-25
description: वर्ड दस्तावेज़ लोड करने और लापता फ़ॉन्ट्स का पता लगाने के लिए चेतावनी
  कॉलबैक बनाएं। Aspose.Words for .NET में फ़ॉन्ट सेटिंग्स को कैसे कॉन्फ़िगर करें,
  जानें।
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: hi
og_description: वर्ड दस्तावेज़ लोड करते समय गायब फ़ॉन्ट्स का पता लगाने के लिए चेतावनी
  कॉलबैक बनाएं। यह गाइड Aspose.Words में फ़ॉन्ट सेटिंग्स को कॉन्फ़िगर करने का तरीका
  दिखाता है।
og_title: चेतावनी कॉलबैक बनाएं – वर्ड दस्तावेज़ लोड करें और लापता फ़ॉन्ट्स का पता
  लगाएँ
tags:
- Aspose.Words
- C#
- Font handling
title: Word दस्तावेज़ लोड करने के लिए चेतावनी कॉलबैक बनाएं – पूर्ण गाइड
url: /hi/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चेतावनी कॉलबैक बनाएं – Word दस्तावेज़ लोड करें और लापता फ़ॉन्ट्स का पता लगाएँ

क्या आपको कभी Word दस्तावेज़ लोड करते समय **चेतावनी कॉलबैक बनाना** पड़ा है और आप आश्चर्यचकित हुए हैं कि कुछ फ़ॉन्ट्स क्यों गायब हो जाते हैं? आप अकेले नहीं हैं। कई एंटरप्राइज़ ऐप्स में, लापता फ़ॉन्ट्स लेआउट आपदाएँ पैदा करते हैं, और उचित कॉलबैक के बिना आप समस्या को कभी नहीं देख पाएंगे।  

अच्छी खबर? Aspose.Words for .NET के साथ आप **Word दस्तावेज़ लोड** कर सकते हैं, **लापता फ़ॉन्ट्स का पता लगा सकते हैं**, और **फ़ॉन्ट सेटिंग्स कॉन्फ़िगर** कर सकते हैं, वह भी कुछ ही साफ़ कोड लाइनों में। इस ट्यूटोरियल में हम एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से चलेंगे, समझाएंगे कि प्रत्येक भाग क्यों महत्वपूर्ण है, और दिखाएंगे कि कैसे सत्यापित करें कि चेतावनी कॉलबैक अपना काम कर रहा है।

> **आप क्या सीखेंगे**  
> * एक पूर्ण C# प्रोग्राम जो DOCX लोड करता है, किसी भी फ़ॉन्ट प्रतिस्थापन की रिपोर्ट करता है, और आपको फ़ॉन्ट सर्च पाथ को कस्टमाइज़ करने देता है।  
> * `FontSettings`, `LoadOptions`, और `IWarningCallback` क्लासेज़ की समझ।  
> * एम्बेडेड फ़ॉन्ट्स या सिस्टम‑वाइड फ़ॉन्ट फ़ोल्डर्स जैसी एज‑केस को संभालने के टिप्स।

---

## आवश्यकताएँ

- .NET 6+ (या .NET Framework 4.7.2+) जिसमें C# कंपाइलर हो।  
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)।  
- एक सैंपल Word फ़ाइल (`input.docx`) जिसमें कम से कम एक ऐसा फ़ॉन्ट हो जो मशीन पर इंस्टॉल न हो (जैसे, *Calibri Light* एक न्यूनतम Windows कंटेनर में)।  
- C# कंसोल ऐप्स की बुनियादी जानकारी।

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है; सब कुछ Aspose.Words के अंदर रहता है।

---

## चरण 1: लापता फ़ॉन्ट्स का पता लगाने के लिए चेतावनी कॉलबैक बनाएं

इस पहेली का **मुख्य** भाग एक क्लास है जो `IWarningCallback` को इम्प्लीमेंट करती है। Aspose.Words इस कॉलबैक को तब कॉल करेगा जब भी उसे ऐसी स्थिति मिले जो चेतावनी की हक़दार हो – सबसे आम है फ़ॉन्ट प्रतिस्थापन।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**यह क्यों महत्वपूर्ण है** – बिना कॉलबैक के आपको बाद में लॉग्स को छानना पड़ेगा। रीयल‑टाइम में चेतावनियों को हैंडल करके आप तय कर सकते हैं कि लोड को रोकना है, लापता फ़ॉन्ट को फॉलबैक से बदलना है, या बस बाद में समीक्षा के लिए समस्या को लॉग करना है।

---

## चरण 2: कस्टम फ़ॉन्ट हैंडलिंग के लिए FontSettings कॉन्फ़िगर करें

डॉक्यूमेंट को वास्तव में लोड करने से पहले, हमें Aspose.Words को बताना पड़ सकता है कि उन फ़ॉन्ट्स को कहाँ खोजा जाए जो सिस्टम पर मौजूद नहीं हैं। यहीं `FontSettings` काम आता है।

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**यह क्यों महत्वपूर्ण है** – Aspose.Words को उस फ़ोल्डर की ओर इंगित करके जिसमें लापता फ़ॉन्ट्स हों, आप अक्सर प्रतिस्थापन से बच सकते हैं। जब यह संभव न हो, तो एक समझदार डिफ़ॉल्ट (जैसे *Arial*) दस्तावेज़ को पढ़ने योग्य बनाता है।

---

## चरण 3: कॉन्फ़िगर किए गए चेतावनी कॉलबैक के साथ Word दस्तावेज़ लोड करें

अब सब कुछ जोड़ते हैं: हम `LoadOptions` बनाते हैं, उसमें हमारे `FontSettings` और `FontWarningHandler` को प्लग‑इन करते हैं, और अंत में दस्तावेज़ लोड करते हैं।

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**यह क्यों महत्वपूर्ण है** – `LoadOptions` वह एकल जगह है जहाँ आप तय करते हैं कि दस्तावेज़ कैसे पढ़ा जाए। फ़ॉन्ट कॉन्फ़िगरेशन और चेतावनी कॉलबैक दोनों प्रदान करके हम सुनिश्चित करते हैं कि कोई भी लापता फ़ॉन्ट सही स्थानों में खोजा जाए **और** तुरंत रिपोर्ट हो।

---

## चरण 4: आउटपुट सत्यापित करें – आपको क्या दिखना चाहिए?

कंसोल से प्रोग्राम चलाएँ। यदि `input.docx` में ऐसा फ़ॉन्ट है जो इंस्टॉल नहीं है और `C:\SharedFonts` में भी नहीं है, तो आपको कुछ इस तरह दिखेगा:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

यदि सभी फ़ॉन्ट उपलब्ध हैं, तो चेतावनी वाली लाइन कभी नहीं आएगी। यह त्वरित फीडबैक लूप स्वचालित दस्तावेज़ प्रोसेसिंग पाइपलाइन में अमूल्य है जहाँ चुपचाप फ़ॉन्ट स्वैप्स ब्रांडिंग गाइडलाइन्स को तोड़ सकते हैं।

---

## चरण 5: सामान्य गलतियाँ और सर्वोत्तम‑प्रैक्टिस टिप्स

| समस्या | कैसे बचें |
|---------|-----------------|
| **`Aspose.Words.Fonts` को रेफ़रेंस करना भूल गए** | सुनिश्चित करें कि फ़ाइल के शीर्ष पर `using Aspose.Words.Fonts;` मौजूद हो; अन्यथा कंपाइलर टाइप्स नहीं मिलने की शिकायत करेगा। |
| **फ़ॉन्ट फ़ोल्डर पाथ गलत है** | पाथ को दोबारा जाँचें और यदि सब‑फ़ोल्डर हैं तो `recursive: true` सेट करें। डिबग करने के लिए `Path.GetFullPath` उपयोग करें। |
| **एकाधिक चेतावनी कॉलबैक** | Aspose.Words केवल अंतिम `WarningCallback` को मानता है जो आप असाइन करते हैं। यदि जटिल लॉजिक चाहिए तो एक ही हैंडलर रखें जो आवश्यकतानुसार डेलीगेट करे। |
| **सर्वर पर UI नहीं है** | कंसोल लिखना ठीक है, लेकिन वेब ऐप्स के लिए `Console.WriteLine` की जगह फ़ाइल या मॉनिटरिंग सिस्टम में लॉग करना बेहतर रहेगा। |
| **बड़े दस्तावेज़ों से प्रदर्शन पर असर** | कई लोड्स में एक ही `FontSettings` इंस्टेंस को री‑यूज़ करें; बार‑बार बनाना महंगा पड़ सकता है। |

**प्रो टिप:** यदि आपको चेतावनियों को बाद में विश्लेषण के लिए *एकत्र* करना है, तो हैंडलर के अंदर सीधे प्रिंट करने के बजाय `List<string>` में स्टोर करें।

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

डॉक्यूमेंट लोड होने के बाद आप `handler.Messages` को देख सकते हैं।

---

## चरण 6: समाधान का विस्तार – यदि मुझे फॉलबैक फ़ॉन्ट एम्बेड करना हो तो?

कभी‑कभी आप चाहते हैं कि लापता फ़ॉन्ट को आउटपुट PDF में *एम्बेड* किया जाए ताकि डाउनस्ट्रीम व्यूअर्स ठीक वही लुक देखें। दस्तावेज़ लोड करने के बाद आप एम्बेडिंग को मजबूर कर सकते हैं:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

यह स्निपेट दिखाता है कि वही **फ़ॉन्ट सेटिंग्स कॉन्फ़िगर** करने वाला तरीका लोडिंग से आगे तक कैसे विस्तारित किया जा सकता है।

---

## पूर्ण चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप नई Console App प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं। इसमें ऊपर चर्चा किए सभी हिस्से शामिल हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**अपेक्षित आउटपुट** (जब लापता फ़ॉन्ट मौजूद हो):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

यदि कोई प्रतिस्थापन नहीं होता, तो केवल सफलता संदेश दिखेंगे।

---

## निष्कर्ष

हमने **चेतावनी कॉलबैक** बनाया जो Aspose.Words के साथ **Word दस्तावेज़ लोड** करते समय **लापता फ़ॉन्ट्स का विश्वसनीय पता लगाता** है, और दिखाया कि **फ़ॉन्ट सेटिंग्स** को कॉन्फ़िगर करके लाइब्रेरी को फ़ॉन्ट्स कहाँ खोजने हैं और कौन सा फॉलबैक उपयोग करना है, यह नियंत्रित किया जा सकता है। `FontSettings` और `LoadOptions` को एक साथ जोड़कर आप फ़ॉन्ट‑संबंधी समस्याओं पर पूरी दृश्यता प्राप्त करते हैं—अब और चुपचाप लेआउट गड़बड़ नहीं।

अगले कदम? `FontWarningHandler` को ऐसे लॉगर से बदलें जो डेटाबेस में लिखे, या **फ़ॉन्ट प्रतिस्थापन नियम** के साथ प्रयोग करें ताकि विशिष्ट लापता फ़ॉन्ट्स को ब्रांड‑स्वीकृत विकल्पों से मैप किया जा सके। आप कंटेनराइज़्ड वातावरण में क्लाउड स्टोरेज से डायनामिक फ़ॉन्ट लोडिंग भी एक्सप्लोर कर सकते हैं।

किसी विशेष एज केस—जैसे OpenType फीचर्स को संभालना या एन्क्रिप्टेड DOCX फ़ाइलों से निपटना—के बारे में सवाल हों तो नीचे टिप्पणी करें, और कोडिंग का आनंद लें!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}