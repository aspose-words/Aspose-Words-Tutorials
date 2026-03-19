---
category: general
date: 2026-03-19
description: Aspose.Words में चेतावनियों को कैप्चर करना, डिफ़ॉल्ट फ़ॉन्ट सेटिंग्स
  सेट करना, और वर्ड दस्तावेज़ लोड करते समय गायब फ़ॉन्ट्स का पता लगाना सीखें।
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: hi
og_description: Aspose.Words में चेतावनियों को कैसे कैप्चर करें, डिफ़ॉल्ट फ़ॉन्ट सेटिंग्स
  सेट करें, और वर्ड दस्तावेज़ लोड करते समय गायब फ़ॉन्ट्स का पता लगाएँ।
og_title: चेतावनियों को कैसे कैप्चर करें – डिफ़ॉल्ट फ़ॉन्ट सेटिंग्स सेट करें
tags:
- Aspose.Words
- C#
- Document Processing
title: चेतावनियों को कैसे कैप्चर करें – डिफ़ॉल्ट फ़ॉन्ट सेटिंग्स सेट करें
url: /hi/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चेतावनियों को कैप्चर कैसे करें – डिफ़ॉल्ट फ़ॉन्ट सेटिंग्स सेट करें

**चेतावनियों को कैसे कैप्चर करें** Aspose.Words के साथ काम करते समय एक सामान्य आवश्यकता है, विशेष रूप से जब आपके दस्तावेज़ विशिष्ट फ़ॉन्ट्स पर निर्भर होते हैं जो लक्ष्य मशीन पर मौजूद नहीं हो सकते। क्या आपने कभी एक DOCX खोला है और सोचा है कि लेआउट क्यों बिगड़ गया? अक्सर उत्तर एक गायब फ़ॉन्ट की चेतावनी में छिपा होता है।  

इस गाइड में हम **चेतावनियों को कैसे कैप्चर करें** को चरणबद्ध रूप से देखेंगे जबकि आप **load word document** करेंगे, **set default font settings** को कॉन्फ़िगर करेंगे, और अंत में **detect missing fonts** करेंगे ताकि आप प्रोग्रामेटिक रूप से प्रतिक्रिया दे सकें। कोई फालतू बातें नहीं—सिर्फ एक पूर्ण, चलाने योग्य उदाहरण और प्रत्येक पंक्ति के पीछे की तर्कसंगतता।

> *Pro tip:* चेतावनियों को जल्दी कैप्चर करने से बाद में रहस्यमय लेआउट गड़बड़ियों को डिबग करने से बचा जा सकता है।

---

## आप को क्या चाहिए

- **Aspose.Words for .NET** (2026 तक का नवीनतम संस्करण)।  
- एक .NET विकास पर्यावरण (Visual Studio, Rider, या VS Code)।  
- एक नमूना DOCX जो ऐसे फ़ॉन्ट को संदर्भित करता है जो आपके पास *स्थापित नहीं* है (उदाहरण के लिए, *Comic Sans MS* एक Linux बॉक्स पर)।  

बस इतना ही। Aspose.Words के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

---

## चरण 1 – समझें कि आपको चेतावनियों को कैप्चर क्यों करना चाहिए

जब Aspose.Words किसी दस्तावेज़ को पार्स करता है, तो उसे होस्ट पर उपलब्ध नहीं होने वाले फ़ॉन्ट्स मिल सकते हैं। डिफ़ॉल्ट रूप से लाइब्रेरी चुपचाप एक फॉलबैक फ़ॉन्ट का उपयोग करती है, जो लाइन ब्रेक, स्पेसिंग बदल सकता है, और यहाँ तक कि टेक्स्ट को गायब भी कर सकता है।  

**WarningCallback** को **FontSettings** ऑब्जेक्ट के साथ उपयोग करने से आपको दो चीज़ें मिलती हैं:

1. **Visibility** – आपको प्रत्येक प्रतिस्थापन के लिए एक `WarningInfo` एंट्री मिलती है।  
2. **Control** – आप दृश्य आश्चर्य को कम करने के लिए एक डिफ़ॉल्ट फ़ॉन्ट पहले से कॉन्फ़िगर कर सकते हैं।  

इसे एक “वॉचडॉग” स्थापित करने जैसा समझें जो हर बार इंजन के हुड के नीचे कोई भाग बदलने पर चिल्लाता है।

---

## चरण 2 – डिफ़ॉल्ट फ़ॉन्ट सेटिंग्स सेट करें

पहला सेकेंडरी कीवर्ड, **set default font settings**, यहाँ दिखता है। आप एक `FontSettings` इंस्टेंस बनाते हैं और वैकल्पिक रूप से इसे उस फ़ोल्डर की ओर इंगित कर सकते हैं जिसमें आपके फॉलबैक फ़ॉन्ट्स हों।

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **क्यों?**  
> यदि आप फॉलबैक निर्दिष्ट नहीं करते हैं, तो Aspose.Words उस शैली से मेल खाने वाला पहला सिस्टम फ़ॉन्ट चुनता है, जो बहुत अलग हो सकता है। एक ज्ञात डिफ़ॉल्ट सेट करके, आप मशीनों के बीच सुसंगत रेंडरिंग की गारंटी देते हैं।

---

## चरण 3 – चेतावनियों को कैप्चर करने के लिए एक Warning Callback तैयार करें

अब हम **चेतावनियों को कैसे कैप्चर करें** को एक `WarningInfoCollection` को लोड विकल्पों से जोड़कर करेंगे। यह कलेक्शन लोड प्रक्रिया के दौरान उत्पन्न प्रत्येक चेतावनी को संग्रहीत करेगा।

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` `IWarningCallback` को लागू करता है, इसलिए Aspose.Words स्वचालित रूप से प्रत्येक चेतावनी को `warningInfos` में पुश करता है। कोई पोलिंग आवश्यक नहीं।

---

## चरण 4 – कॉन्फ़िगर किए गए विकल्पों के साथ Word दस्तावेज़ लोड करें

यहाँ वह जगह है जहाँ दूसरा सेकेंडरी कीवर्ड, **load word document**, चमकता है। हम `FontSettings` और `WarningCallback` दोनों को एक `LoadOptions` इंस्टेंस के माध्यम से पास करते हैं।

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

यदि दस्तावेज़ ऐसा फ़ॉन्ट संदर्भित करता है जो स्थापित नहीं है, तो चेतावनी कॉलबैक एक `WarningType.FontSubstitution` एंट्री को कैप्चर करेगा।

---

## चरण 5 – एकत्रित चेतावनियों से गायब फ़ॉन्ट्स का पता लगाएँ

अंत में, हम तीसरे सेकेंडरी कीवर्ड, **detect missing fonts**, का उत्तर एकत्रित चेतावनियों पर इटरेट करके देते हैं।

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

सामान्य आउटपुट इस प्रकार दिखता है:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

वह पंक्ति आपको बिल्कुल बताती है कि कौन सा फ़ॉन्ट गायब है और कौन सा फॉलबैक उपयोग किया गया—यह जानकारी आप लॉग कर सकते हैं, उपयोगकर्ता को दिखा सकते हैं, या यहां तक कि एक कस्टम फ़ॉन्ट‑इंस्टॉल रूटीन को ट्रिगर कर सकते हैं।

---

## पूर्ण चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी‑पेस्ट करके एक कंसोल एप्लिकेशन में उपयोग कर सकते हैं। यह **चेतावनियों को कैसे कैप्चर करें**, **डिफ़ॉल्ट फ़ॉन्ट सेटिंग्स सेट करें**, **Word दस्तावेज़ लोड करें**, और **गायब फ़ॉन्ट्स का पता लगाएँ** को एक ही प्रवाह में प्रदर्शित करता है।

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**अपेक्षित परिणाम:** जब निर्दिष्ट DOCX ऐसा फ़ॉन्ट संदर्भित करता है जो स्थापित नहीं है, तो कंसोल प्रत्येक प्रतिस्थापन के लिए एक चेतावनी प्रिंट करता है। यदि सभी फ़ॉन्ट्स मौजूद हैं, तो लूप कोई आउटपुट नहीं देता।

---

## सामान्य गलतियाँ और किनारे के मामले

| Situation | Why it Happens | How to Handle It |
|-----------|----------------|------------------|
| **कोई चेतावनी नहीं दिखती** जबकि लेआउट गलत दिख रहा है | दस्तावेज़ *एम्बेडेड* फ़ॉन्ट्स का उपयोग कर रहा हो सकता है, जिन्हें Aspose.Words बिना प्रतिस्थापन के रेंडर करता है। | `Document.HasEmbeddedFonts` जांचें और यदि आपको उन्हें किसी अन्य मशीन पर चाहिए तो एम्बेडेड फ़ॉन्ट्स को निकालने पर विचार करें। |
| **कई चेतावनियाँ** |  |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}