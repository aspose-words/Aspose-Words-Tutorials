---
category: general
date: 2025-12-31
description: Aspose.Words में फ़ॉन्ट चेतावनियों को पकड़ें ताकि गायब फ़ॉन्ट्स का पता
  लगाया जा सके और अपने .NET ऐप में गायब फ़ॉन्ट्स की सूची बनाएं। चरण‑दर‑चरण C# समाधान
  सीखें।
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: hi
og_description: Aspose.Words में फ़ॉन्ट चेतावनियों को पकड़ें ताकि गायब फ़ॉन्ट का पता
  लगाया जा सके और गायब फ़ॉन्ट की सूची बनाई जा सके। कोड और टिप्स के साथ पूर्ण C# गाइड।
og_title: फ़ॉन्ट चेतावनियों को कैप्चर करें – गायब फ़ॉन्ट्स का पता लगाएँ और सूचीबद्ध
  करें
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: फ़ॉन्ट चेतावनियों को पकड़ें – लापता फ़ॉन्ट्स का पता लगाएँ और सूचीबद्ध करें
url: /hi/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ॉन्ट चेतावनियों को कैप्चर करें – लापता फ़ॉन्ट्स का पता लगाएँ और सूचीबद्ध करें

क्या आपको कभी **फ़ॉन्ट चेतावनियों को कैप्चर** करने की ज़रूरत पड़ी है जब आप एक Word दस्तावेज़ लोड कर रहे थे, लेकिन लापता‑फ़ॉन्ट विवरण को कैसे दिखाएँ, यह नहीं पता था? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया प्रोजेक्ट्स में, लापता फ़ॉन्ट्स लेआउट गड़बड़ियों का कारण बनते हैं, और उचित चेतावनियों के बिना आप भूतिया बग्स का पीछा करते रहते हैं।  

इस ट्यूटोरियल में हम आपको दिखाएंगे कि **लापता फ़ॉन्ट्स का पता कैसे लगाएँ** और **लापता फ़ॉन्ट्स की सूची कैसे बनाएँ** Aspose.Words for .NET का उपयोग करके। अंत तक आपके पास एक तैयार‑चलाने योग्य C# स्निपेट होगा जो हर प्रतिस्थापन चेतावनी को प्रिंट करता है, ताकि आप उसे लॉग, अलर्ट या यहाँ तक कि फ़ॉन्ट्स को स्वचालित रूप से बदल सकें।

---

## फ़ॉन्ट चेतावनियों को कैप्चर करना क्यों महत्वपूर्ण है

जब Aspose.Words एक DOCX खोलता है जिसमें सर्वर पर स्थापित नहीं किया गया फ़ॉन्ट संदर्भित है, तो यह चुपचाप एक फॉलबैक फ़ॉन्ट का उपयोग करता है। दस्तावेज़ ठीक दिखता है, लेकिन दृश्य सटीकता प्रभावित होती है—जैसे कि एक कॉर्पोरेट ब्रांड लोगो गलत टाइपफ़ेस में रेंडर हो रहा हो।  

इन चेतावनियों को कैप्चर करने से आप:

* **ब्रांड स्थिरता बनाए रखें** – आपको ठीक‑ठीक पता होगा कौन‑से फ़ॉन्ट्स लापता हैं।  
* **स्वचालित सुधार** – प्रोग्रामेटिक रूप से लापता फ़ॉन्ट्स को बदलें।  
* **ऑडिट अनुपालन** – कानूनी या डिज़ाइन रिव्यू के लिए रिपोर्ट जेनरेट करें।  

संक्षेप में, **फ़ॉन्ट चेतावनियों को कैप्चर करना** चुपचाप फ़ॉन्ट प्रतिस्थापन के खिलाफ पहली रक्षा पंक्ति है।

---

## लापता फ़ॉन्ट्स का पता लगाने के लिए LoadOptions सेट करें

चेतावनियों को दिखाने की कुंजी `LoadOptions.FontSubstitutionWarning` प्रॉपर्टी है। डिफ़ॉल्ट रूप से यह `None` पर सेट होती है, जिसका मतलब है कि Aspose.Words संदेशों को निगल लेता है। इसे `All` पर बदलने से लाइब्रेरी हर प्रतिस्थापन इवेंट को रिकॉर्ड करती है।

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **प्रो टिप:** यदि आपके पास पहले से एक कस्टम फ़ॉन्ट फ़ोल्डर है, तो दस्तावेज़ लोड करने से पहले `FontSettings.SetFontsFolder("path")` को असाइन करें। इस तरह आप **लापता फ़ॉन्ट्स का पता लगा** सकते हैं जो सिस्टम डायरेक्टरी में नहीं हैं।

---

## दस्तावेज़ लोड करें और लापता फ़ॉन्ट्स की सूची बनाएं

अब जब `LoadOptions` तैयार हैं, अगला कदम Word फ़ाइल को लोड करना है। कन्स्ट्रक्टर विकल्प ऑब्जेक्ट को स्वीकार करता है, और कोई भी प्रतिस्थापन दस्तावेज़ की `WarningInfoCollection` में रिकॉर्ड हो जाएगा।

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

यदि फ़ाइल ऐसे फ़ॉन्ट्स को संदर्भित करती है जो उपलब्ध नहीं हैं, तो प्रत्येक लापता फ़ॉन्ट एक `WarningInfo` एंट्री उत्पन्न करता है। आप उस कलेक्शन पर इटरेट करके **लापता फ़ॉन्ट्स की सूची बना** सकते हैं।

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

सामान्य आउटपुट इस प्रकार दिखता है:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

प्रत्येक पंक्ति ठीक‑ठीक बताती है कौन‑सा फ़ॉन्ट लापता था, जिससे **लापता फ़ॉन्ट्स की सूची** की आवश्यकता पूरी होती है।

---

## WarningInfoCollection को पढ़ें और समझें

`WarningInfoCollection` में विभिन्न प्रकार की चेतावनियाँ हो सकती हैं (जैसे, `DocumentStructure`, `ImageLoading`)। केवल फ़ॉन्ट समस्याओं पर ध्यान केंद्रित करने के लिए, `WarningType.FontSubstitution` द्वारा फ़िल्टर करें।

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

फ़िल्टर क्यों? क्योंकि बड़े दस्तावेज़ में भ्रष्ट इमेज या असमर्थित फीचर जैसी चेतावनियाँ भी उत्पन्न हो सकती हैं। कलेक्शन को संकीर्ण करके आप शोर से बचते हैं और **फ़ॉन्ट चेतावनियों को कैप्चर** करने का आउटपुट साफ़ रहता है।

---

## पूर्ण कार्यशील उदाहरण – फ़ॉन्ट चेतावनियों को कार्रवाई में देखें

नीचे पूरा, स्व-निहित प्रोग्राम है जिसे आप किसी भी .NET कंसोल प्रोजेक्ट में डाल सकते हैं। यह `LoadOptions` को कॉन्फ़िगर करने से लेकर लापता फ़ॉन्ट्स की साफ़-सुथरी सूची प्रिंट करने तक हर कदम दर्शाता है।

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**अपेक्षित कंसोल आउटपुट**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

यदि दस्तावेज़ में कोई लापता फ़ॉन्ट नहीं है तो आप देखेंगे:

```
All referenced fonts are available – no warnings captured.
```

---

## सामान्य किनारे के मामले और उनका समाधान

| स्थिति | क्यों होता है | सुझाया गया समाधान |
|-----------|----------------|-----------------|
| **दस्तावेज़ में एम्बेडेड OpenType फ़ॉन्ट है** | Aspose.Words एम्बेडेड फ़ॉन्ट पढ़ सकता है, लेकिन केवल तभी जब फ़ाइल भ्रष्ट न हो। | पहले Word में DOCX को वेरिफ़ाई करें; आवश्यक होने पर फ़ॉन्ट को पुनः‑एम्बेड करें। |
| **चेतावनियों की बड़ी संख्या** (जैसे, 200+ लापता फ़ॉन्ट) | लेगेसी सिस्टम से बड़े इम्पोर्ट अक्सर विस्तृत फ़ॉन्ट पैलेट को संदर्भित करते हैं। | चेतावनियों को बैच‑प्रोसेस करें: उन्हें डेटाबेस में स्टोर करें, फिर फ़ॉन्ट‑इंस्टॉलेशन स्क्रिप्ट चलाएँ। |
| **WarningInfoCollection खाली है** | या तो दस्तावेज़ में सभी फ़ॉन, या `FontSubstitutionWarning` को `None` पर छोड़ दिया गया था। | अपने `LoadOptions` कॉन्फ़िगरेशन को दोबारा जांचें और सुनिश्चित करें कि आप सही फ़ाइल पाथ लोड कर रहे हैं। |
| **कस्टम फ़ॉन्ट्स नेटवर्क शेयर पर स्थित हैं** | नेटवर्क लेटेंसी फ़ॉन्ट लुकअप के दौरान टाइमआउट का कारण बन सकती है। | `FontSettings` में `SetFontsFolder` का उपयोग करके फ़ॉन्ट्स को प्री‑लोड करें और `CacheFontData = true` सेट करें। |

ये टिप्स आपको **लापता फ़ॉन्ट्स का पता लगाने** में विश्वसनीय बनाते हैं, यहाँ तक कि जटिल वातावरण में भी।

---

## छवि चित्रण

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*स्क्रीनशॉट में दिखाया गया है कि दो लापता फ़ॉन्ट्स रिपोर्ट किए जा रहे हैं।*

---

## अगले कदम – साधारण रिपोर्टिंग से आगे बढ़ें

अब जब आप **फ़ॉन्ट चेतावनियों को कैप्चर** कर सकते हैं, तो सुधार को स्वचालित करने पर विचार करें:

1. **स्वचालित फ़ॉन्ट प्रतिस्थापन** – `FontSettings.SubstitutionSettings` को संशोधित करके कंपनी‑स्वीकृत फॉलबैक के साथ लापता फ़ॉन्ट्स बदलें।  
2. **मॉनिटरिंग सिस्टम में लॉगिंग** – चेतावनी संदेशों को Serilog, ELK, या Azure Application Insights में पाइप करें।  
3. **उपयोगकर्ता‑समक्ष रिपोर्ट** – डिज़ाइनर्स के लिए HTML या PDF सारांश जेनरेट करें ताकि वे देख सकें कौन‑से फ़ॉन्ट्स इंस्टॉल करने की आवश्यकता है।  

इन सभी विस्तारों का आधार वही है जो हमने कवर किया: `LoadOptions` को कॉन्फ़िगर करना, दस्तावेज़ लोड करना, और `WarningInfoCollection` पढ़ना।

---

## निष्कर्ष

आपने अभी-अभी सीखा कि Aspose.Words में **फ़ॉन्ट चेतावनियों को कैप्चर** कैसे करें, **लापता फ़ॉन्ट्स का पता लगाएँ**, और **लापता फ़ॉन्ट्स की सूची बनाएँ** एक साफ़, कंसोल‑फ्रेंडली आउटपुट के साथ। यह तरीका सीधा‑सरल है, केवल कुछ ही लाइनों के C# कोड की आवश्यकता है, और किसी भी .NET संस्करण के साथ काम करता है जो Aspose.Words 23.x या बाद के संस्करण को सपोर्ट करता है।  

एक ऐसे नमूना DOCX पर इसे आज़माएँ जिसमें आप जानबूझकर कोई फ़ॉन्ट अनइंस्टॉल कर चुके हों – आपको तुरंत चेतावनियाँ दिखाई देंगी। उसके बाद आप तय कर सकते हैं कि लापता टाइपफ़ेस को इंस्टॉल करें, प्रोग्रामेटिक रूप से प्रतिस्थापित करें, या बाद में समीक्षा के लिए लॉग रखें।

हैप्पी कोडिंग, और आपके दस्तावेज़ हमेशा सही फ़ॉन्ट्स के साथ रेंडर हों!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}