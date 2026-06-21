---
category: general
date: 2026-06-20
description: Aspose.Words का उपयोग करके C# में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम
  करें। जानें कि LoadOptions को कैसे कॉन्फ़िगर करें, चेतावनियों को कैसे कैप्चर करें,
  और गायब फ़ॉन्ट्स को प्रभावी ढंग से कैसे संभालें।
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: hi
og_description: Aspose.Words के साथ C# में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम
  करें। यह गाइड दिखाता है कि LoadOptions कैसे सेट करें, WarningInfo पढ़ें, और लापता
  फ़ॉन्ट संदेश प्रदर्शित करें।
og_title: C# में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Aspose.Words के साथ C# में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें
url: /hi/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Aspose.Words के साथ फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें

क्या आपने कभी सोचा है कि **फ़ॉन्ट प्रतिस्थापन चेतावनियों** को कैसे सक्षम किया जाए जब कोई Word दस्तावेज़ ऐसे फ़ॉन्ट को संदर्भित करता है जो सर्वर पर स्थापित नहीं है? आप अकेले नहीं हैं। लापता फ़ॉन्ट्स चुपचाप उत्पन्न PDFs या इमेजेज़ की लेआउट को बिगाड़ सकते हैं, और इसे जल्दी पकड़ने का एकमात्र तरीका है कि Aspose.Words द्वारा उत्पन्न चेतावनियों को सुनें।

इस ट्यूटोरियल में हम एक व्यावहारिक उदाहरण के माध्यम से दिखाएंगे कि इन चेतावनियों को कैसे चालू करें, उन्हें `WarningInfo` संग्रह से निकालें, और कंसोल पर अर्थपूर्ण संदेश प्रिंट करें। अंत तक आप जानेंगे कि **Aspose.Words LoadOptions** को कैसे कॉन्फ़िगर करें, **C# फ़ॉन्ट प्रतिस्थापन चेतावनियों** को कैसे हैंडल करें, और अपने दस्तावेज़‑प्रोसेसिंग पाइपलाइन को बुलेट‑प्रूफ़ रखें।

हम कुछ किनारी मामलों पर भी चर्चा करेंगे—यदि आप चेतावनियों को दबाते हैं, या यदि आपको उन्हें प्रिंट करने के बजाय लॉग करना है—और आपको एक पूर्ण, कॉपी‑एंड‑पेस्ट‑तैयार कोड नमूना देंगे जो नवीनतम Aspose.Words for .NET (संस्करण 24.10) के साथ काम करता है।

## आपको क्या चाहिए

- .NET 6.0 या बाद का (कोड .NET Framework 4.7+ पर भी काम करता है)
- `Aspose.Words` का NuGet रेफ़रेंस ( `dotnet add package Aspose.Words` के माध्यम से स्थापित करें)
- एक Word फ़ाइल जिसमें ऐसा फ़ॉन्ट संदर्भित हो जिसे आप **नहीं** स्थापित किया है (उदाहरण के लिए `DocumentWithMissingFont.docx`)
- एक अच्छा IDE (Visual Studio, Rider, या VS Code)

बस इतना ही—कोई अतिरिक्त सेवाएँ नहीं, कोई स्वामित्व वाले टूल नहीं। तैयार हैं? चलिए शुरू करते हैं।

## चरण 1: फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें

सबसे पहले आपको Aspose.Words को बताना होगा कि जब वह कोई लापता फ़ॉन्ट प्रतिस्थापित करे तो आपको सूचित किया जाए। यह `LoadOptions` ऑब्जेक्ट की `FontSettings` प्रॉपर्टी के माध्यम से किया जाता है। डिफ़ॉल्ट रूप से, चेतावनियाँ **अक्षम** रहती हैं ताकि API शांत रहे, इसलिए हमें स्वयं इसे सक्रिय करना होगा।

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **यह क्यों काम करता है:** जब `FontSettings` `null` नहीं होता, तो लाइब्रेरी स्वचालित रूप से `Document.WarningInfo` को उन सभी `WarningType.FontSubstitution` प्रविष्टियों से भर देती है जो दस्तावेज़ लोड करते समय मिलती हैं। इसे फ़ॉन्ट्स के लिए “डिबग‑मोड” चालू करने जैसा समझें।

## चरण 2: कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें

अब जबकि चेतावनी संग्रह सक्रिय है, अपने दस्तावेज़ को उसी `LoadOptions` के साथ लोड करें जिसे हमने अभी तैयार किया है। यदि दस्तावेज़ में कोई लापता फ़ॉन्ट है, तो Aspose.Words एक फ़ॉलबैक फ़ॉन्ट प्रतिस्थापित करेगा और `WarningInfo` सूची में चेतावनी जोड़ देगा।

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **प्रो टिप:** यदि आप कई फ़ाइलों को लूप में प्रोसेस कर रहे हैं, तो वही `LoadOptions` इंस्टेंस पुनः उपयोग करें—इसे एक बार बनाना प्रत्येक इटरेशन में कुछ मिलीसेकंड बचाता है।

## चरण 3: WarningInfo पर इटररेट करें और फ़ॉन्ट प्रतिस्थापन संदेश दिखाएँ

दस्तावेज़ लोड हो जाने के बाद, `WarningInfo` संग्रह में लोड के दौरान हुई सभी चेतावनियाँ होती हैं। हमें केवल `WarningType.FontSubstitution` में रुचि है, इसलिए हम उसी के अनुसार फ़िल्टर करेंगे।

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

उपर्युक्त स्निपेट को लापता “Papyrus” फ़ॉन्ट वाले दस्तावेज़ पर चलाने पर आउटपुट कुछ इस प्रकार हो सकता है:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

यही **फ़ॉन्ट प्रतिस्थापन संदेश** हैं जिन्हें आप खोज रहे थे—स्पष्ट, क्रियाशील, और लॉग या अलर्टिंग सिस्टम को भेजने के लिए तैयार।

## पूर्ण कार्यशील उदाहरण

नीचे एक स्व-निहित कंसोल प्रोग्राम है जो सब कुछ एक साथ जोड़ता है। इसे नई `.csproj` में कॉपी‑पेस्ट करें और **Run** दबाएँ।

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### अपेक्षित आउटपुट

यदि दस्तावेज़ में ऐसे फ़ॉन्ट्स हैं जो स्थापित नहीं हैं, तो आप कुछ इस तरह देखेंगे:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

यदि सभी फ़ॉन्ट्स मशीन पर मौजूद हैं, तो प्रोग्राम केवल यह प्रिंट करेगा:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## सामान्य समस्याएँ एवं प्रो टिप्स

| समस्या | क्यों होता है | समाधान / बचाव |
|-------|----------------|--------------------|
| **चेतावनियाँ गायब हो जाती हैं** | आपने `FontSettings` साफ़ कर दिया या बिना इसे सेट किए `LoadOptions` इस्तेमाल किया। | हमेशा `FontSettings` का इंस्टेंस बनाएं, भले ही आप कोई प्रॉपर्टी न बदलें। |
| **बहुत अधिक चेतावनियाँ** | दस्तावेज़ में कई विदेशी फ़ॉन्ट्स हैं। | `FontSettings` में `SetFontsFolder` के माध्यम से एक कस्टम फ़ॉन्ट फ़ोल्डर जोड़ें ताकि प्रतिस्थापन कम हो। |
| **कसकर लूप में प्रदर्शन गिरावट** | प्रत्येक इटरेशन में `LoadOptions` फिर से बनाना ओवरहेड जोड़ता है। | सभी दस्तावेज़ों के लिए एक ही `LoadOptions` इंस्टेंस पुनः उपयोग करें। |
| **कंसोल आउटपुट नहीं दिख रहा** | GUI एप्लिकेशन में `Console.WriteLine` अनदेखा हो रहा है। | चेतावनियों को लॉगर (`ILogger`) में रीडायरेक्ट करें या फ़ाइल में लिखें। |

### वास्तविक‑विश्व सेवा में चेतावनियों को संभालना

वेब API में आप संभवतः कंसोल में लिखना नहीं चाहते। इसके बजाय, चेतावनियों को संरचित लॉग में पाइप करें:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

इस तरह आप **दस्तावेज़ चेतावनी हैंडलिंग** को बनाए रखते हुए अपनी सेवा को साफ़ रख सकते हैं।

## उदाहरण का विस्तार

- **अन्य चेतावनी प्रकार कैप्चर करें** (जैसे `WarningType.UnknownFileFormat`) `if` फ़िल्टर हटाकर।
- **सभी चेतावनियों की रिपोर्ट JSON में सहेजें** ताकि डाउनस्ट्रीम एनालिटिक्स हो सके।
- **एक विशिष्ट फ़ॉलबैक फ़ॉन्ट फोर्स करें** `FontSettings.SubstitutionSettings.DefaultFontName` सेट करके।

इन सभी को आप **फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करने** के बाद आसानी से लागू कर सकते हैं।

## निष्कर्ष

हमने दिखाया कि कैसे C# में Aspose.Words का उपयोग करके **फ़ॉन्ट प्रतिस्थापन चेतावनियों** को सक्षम किया जाता है, `LoadOptions` को कॉन्फ़िगर करने से लेकर `WarningInfo` पर इटररेट करने और उपयोगी संदेश प्रिंट करने तक। ऊपर बताए गए चरणों का पालन करके आप अपने दस्तावेज़‑प्रोसेसिंग पाइपलाइन को लापता फ़ॉन्ट्स के कारण होने वाले चुपचाप लेआउट बदलावों से सुरक्षित रख सकते हैं।

अब एक कस्टम फ़ॉन्ट फ़ोल्डर जोड़ें, चेतावनियों को फ़ाइल में लॉग करें, या उन्हें मॉनिटरिंग डैशबोर्ड पर भेजें। यही पैटर्न किसी भी **दस्तावेज़ चेतावनी हैंडलिंग** परिदृश्य में काम करता है, चाहे आप PDF में कनवर्ट कर रहे हों, इमेज रेंडर कर रहे हों, या मेल‑मर्ज कर रहे हों।

**C# फ़ॉन्ट प्रतिस्थापन चेतावनियों** के बारे में प्रश्न हैं या कोई चतुर समाधान साझा करना चाहते हैं? नीचे टिप्पणी करें—हैप्पी कोडिंग!


## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}