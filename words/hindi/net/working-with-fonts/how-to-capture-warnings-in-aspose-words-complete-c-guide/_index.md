---
category: general
date: 2026-03-28
description: Aspose.Words के साथ DOCX लोड करते समय चेतावनियों को कैसे पकड़ें और गायब
  फ़ॉन्ट्स के लिए चेतावनी संदेश प्राप्त करें। गायब फ़ॉन्ट्स को प्रभावी ढंग से संभालना
  सीखें।
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: hi
og_description: Aspose.Words के साथ DOCX लोड करते समय चेतावनियों को कैसे कैप्चर करें,
  चेतावनी संदेश प्राप्त करें, और व्यावहारिक कोड उदाहरणों के साथ गायब फ़ॉन्ट्स को कैसे
  संभालें।
og_title: Aspose.Words में चेतावनियों को कैसे कैप्चर करें – पूर्ण C# गाइड
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words में चेतावनियों को कैसे कैप्चर करें – पूर्ण C# गाइड
url: /hi/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में चेतावनियों को कैप्चर करने का तरीका – पूर्ण C# गाइड

क्या आपने कभी सोचा है **कैसे चेतावनियों को कैप्चर किया जाए** जब आप Aspose.Words से Word दस्तावेज़ लोड करते हैं? शायद आपको अजीब फ़ॉन्ट परिवर्तन दिख रहे हैं और आपको ठीक‑ठीक कारण जानना है। संक्षेप में, आप लाइब्रेरी की चेतावनी प्रणाली में हुक कर सकते हैं, **चेतावनी संदेश प्राप्त कर सकते हैं**, और यहाँ तक कि **गुम फ़ॉन्ट्स** को संभाल सकते हैं इससे पहले कि वे आपके लेआउट को बिगाड़ें।  

इस ट्यूटोरियल में हम एक वास्तविक परिदृश्य पर चलते हैं: एक DOCX लोड करना, इंजन द्वारा उत्पन्न हर चेतावनी को एकत्र करना, और किसी भी फ़ॉन्ट प्रतिस्थापन के विवरण को प्रिंट करना। अंत तक आपके पास चलाने योग्य कोड नमूना होगा, प्रत्येक चरण के “क्यों” को समझेंगे, और अपने प्रोजेक्ट्स के लिए इस दृष्टिकोण को कैसे विस्तारित करें, यह जानेंगे।

## आप क्या सीखेंगे

- `LoadOptions` को इस तरह कॉन्फ़िगर करना कि चेतावनियाँ स्वचालित रूप से कैप्चर हों।  
- `WarningInfoCollection` से **चेतावनी संदेश प्राप्त करने** का सटीक तरीका।  
- `WarningType.FontSubstitution` फ़्लैग के माध्यम से **गुम फ़ॉन्ट्स** की पहचान और प्रतिक्रिया देना।  
- किनारे के मामलों का निवारण करने के टिप्स, जैसे एम्बेडेड फ़ॉन्ट्स वाले दस्तावेज़ या कस्टम फ़ॉन्ट फ़ोल्डर।  

कोई बाहरी संदर्भ आवश्यक नहीं – सब कुछ यहाँ उपलब्ध है।

---

## पूर्वापेक्षाएँ

- .NET 6.0 या बाद का (कोड .NET Framework 4.7+ पर भी काम करता है)।  
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)।  
- एक नमूना DOCX (`input.docx`) जिसमें कुछ फ़ॉन्ट्स नहीं हैं या ऐसे फ़ॉन्ट्स उपयोग किए गए हैं जो आपके मशीन पर इंस्टॉल नहीं हैं।  

बस इतना ही। यदि आप पहले से C# और Visual Studio में सहज हैं, तो आप कोड को कॉपी‑पेस्ट करके तुरंत चला सकते हैं।

---

## चरण 1: Load Options और Warning Callback तैयार करें

जब आप `new Document(path, loadOptions)` कॉल करते हैं, तो Aspose.Words सबसे पहले फ़ाइल को पार्स करता है। पार्सिंग के दौरान यह गुम फ़ॉन्ट्स, असमर्थित फीचर्स, या डिप्रिकेटेड मार्कअप का सामना कर सकता है। इन घटनाओं को पकड़ने के लिए आपको एक **warning callback** ऑब्जेक्ट चाहिए।

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**यह क्यों महत्वपूर्ण है:** बिना callback के, Aspose.Words चेतावनियों को silently कंसोल में लॉग करता है (या उन्हें डिस्कार्ड कर देता है), जिससे आप फ़ॉन्ट प्रतिस्थापन से अनभिज्ञ रह जाते हैं जो लेआउट को प्रभावित कर सकता है। एक समर्पित `WarningInfoCollection` प्रदान करके आप पूरी दृश्यता प्राप्त करते हैं।

> **Pro tip:** यदि आप केवल फ़ॉन्ट‑संबंधी चेतावनियों में रुचि रखते हैं, तो बाद में फ़िल्टर कर सकते हैं – लेकिन *सभी* चेतावनियों को एकत्र करना भविष्य के मुद्दों के लिए एक सुरक्षा जाल देता है।

---

## चरण 2: कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें

अब callback तैयार है, फ़ाइल लोड करें। `Document` कंस्ट्रक्टर स्वचालित रूप से किसी भी समस्या के लिए callback को invoke करेगा।

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**आंतरिक रूप से क्या हो रहा है?** Aspose.Words Open XML को पार्स करता है, स्टाइल्स को रिजॉल्व करता है, और प्रत्येक फ़ॉन्ट रेफ़रेंस को सिस्टम‑इंस्टॉल्ड फ़ॉन्ट से मैप करने की कोशिश करता है। यदि मिलान नहीं मिलता, तो यह `FontSubstitution` प्रकार की `WarningInfo` एंट्री बनाता है।

---

## चरण 3: एकत्रित चेतावनियों को प्राप्त करें और निरीक्षण करें

लोड पूरा होने के बाद, आपका `warningCollector` अब हर हुई चेतावनी को रखता है। चलिए उन्हें निकालते हैं और फ़ॉन्ट प्रतिस्थापन संदेशों पर ध्यान केंद्रित करते हैं।

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**उदाहरण आउटपुट** (आपका कंसोल कुछ इस तरह दिखा सकता है):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

यदि आप *सभी* चेतावनियों को चाहते हैं, तो बस `if` चेक को हटा दें या प्रत्येक एंट्री के लिए `warning.Type` को लॉग करें।

---

## चरण 4: गुम फ़ॉन्ट्स को संभालना – केवल लॉगिंग से आगे

चेतावनियों को कैप्चर करना उपयोगी है, लेकिन अक्सर आपको **गुम फ़ॉन्ट्स को प्रोग्रामेटिक रूप से संभालना** पड़ता है। यहाँ दो सामान्य रणनीतियाँ हैं:

### 4.1 गुम फ़ॉन्ट्स को एक विशिष्ट फ़ॉलबैक से बदलें

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

अब कोई भी गुम फ़ॉन्ट लाइब्रेरी के डिफ़ॉल्ट फ़ॉलबैक की बजाय *Calibri* से बदल दिया जाएगा।

### 4.2 डायनामिक रूप से एक प्रतिस्थापन फ़ॉन्ट एम्बेड करें

यदि आपके पास एक कस्टम फ़ॉन्ट फ़ाइल (जैसे `MyFallback.ttf`) है, तो आप इसे रन‑टाइम पर रजिस्टर कर सकते हैं:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

यह तरीका तब उपयोगी होता है जब आप अपने एप्लिकेशन के साथ एक विशिष्ट कॉरपोरेट फ़ॉन्ट वितरित करते हैं।

> **Edge case:** ऐसे दस्तावेज़ जो पहले से आवश्यक फ़ॉन्ट एम्बेड करते हैं, सिस्टम प्रतिस्थापन नियमों को अनदेखा करेंगे। इस स्थिति में, उस फ़ॉन्ट के लिए चेतावनी संग्रह खाली रहेगा, जो बिल्कुल वही है जो आप चाहते हैं।

---

## चरण 5: पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

नीचे एक स्व-समाहित प्रोग्राम है जो शुरुआत से अंत तक सब कुछ दर्शाता है। बस `YOUR_DIRECTORY/input.docx` को अपने परीक्षण फ़ाइल के पथ से बदलें।

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**क्या उम्मीद करें**

- कंसोल हर फ़ॉन्ट‑सबस्टीट्यूशन चेतावनी को एक चेतावनी इमोजी के साथ प्रिंट करेगा, जिससे दृश्यता बढ़ेगी।  
- आउटपुट DOCX (`output.docx`) में जहाँ भी गुम फ़ॉन्ट पाया गया, वहाँ *Calibri* उपयोग किया जाएगा।  
- कोई अनहैंडल्ड एक्सेप्शन नहीं – चेतावनी प्रणाली किसी भी अज्ञात फ़ॉन्ट को सुगमता से संभालती है।

---

## सामान्य प्रश्न एवं उत्तर

**प्रश्न: क्या यह PDFs के साथ भी काम करेगा जो Word से जेनरेट किए गए हैं?**  
उत्तर: हाँ। Aspose.Words PDFs को एक अन्य आउटपुट फ़ॉर्मेट मानता है। चेतावनी कैप्चर *लोड* चरण के दौरान होता है, इसलिए यह अंतिम एक्सपोर्ट से स्वतंत्र है।

**प्रश्न: यदि मुझे सभी दस्तावेज़ ऑपरेशन्स (save, convert, आदि) के लिए चेतावनियाँ कैप्चर करनी हों तो क्या करें?**  
उत्तर: आप वही `WarningInfoCollection` को `Document.WarningCallback` में असाइन कर सकते हैं जब दस्तावेज़ इंस्टैंशिएट हो गया हो। प्रत्येक बाद के ऑपरेशन नई एंट्रीज़ को उसी संग्रह में जोड़ देगा।

**प्रश्न: क्या warning callback प्रदर्शन को प्रभावित करता है?**  
उत्तर: नगण्य रूप से। संग्रह केवल ऑब्जेक्ट्स को स्टोर करता है; जब तक आप हजारों चेतावनियों को कड़ी लूप में प्रोसेस नहीं कर रहे, आपको कोई slowdown नहीं दिखेगा।

**प्रश्न: मैं उन चेतावनियों को कैसे दबा सकता हूँ जिनकी मुझे परवाह नहीं है?**  
उत्तर: एक कस्टम क्लास इम्प्लीमेंट करें जो `IWarningCallback` को इनहेरिट करे और `Warning` मेथड के अंदर फ़िल्टर करें। बिल्ट‑इन `WarningInfoCollection` केवल स्टोर करता है, फ़िल्टर नहीं करता।

---

## प्रो टिप्स और सामान्य गलतियाँ

- **Pro tip:** हमेशा `Warning.Description` को देखें – इसमें ठीक‑वही फ़ॉन्ट नाम होता है जो गुम था। यह आपको यह तय करने में मदद कर सकता है कि फ़ॉन्ट को अपने ऐप के साथ शिप करना है या नहीं।  
- **Embedded फ़ॉन्ट्स पर ध्यान दें:** यदि स्रोत DOCX पहले से आवश्यक फ़ॉन्ट एम्बेड करता है, तो Aspose.Words प्रतिस्थापन चेतावनी नहीं देगा, भले ही फ़ॉन्ट स्थानीय रूप से इंस्टॉल न हो।  
- **थ्रेड सुरक्षा:** `WarningInfoCollection` थ्रेड‑सेफ़ नहीं है। यदि आप एक साथ कई दस्तावेज़ लोड कर रहे हैं, तो प्रत्येक थ्रेड को अपना संग्रह दें।  
- **वर्ज़न चेक:** चेतावनी API Aspose.Words 20.8 से स्थिर है। नवीनतम वर्ज़न का उपयोग करें ताकि नए चेतावनी प्रकार न चूके।

---

## निष्कर्ष

हमने **Aspose.Words से चेतावनियों को कैप्चर करने** का तरीका कवर किया, **चेतावनी संदेश प्राप्त करने** को प्रदर्शित किया, और गुम फ़ॉन्ट्स को फ़ॉलबैक फ़ॉन्ट या कस्टम फ़ॉन्ट फ़ोल्डर के माध्यम से **हैंडल करने** के व्यावहारिक तरीके दिखाए। पूर्ण उदाहरण किसी भी .NET प्रोजेक्ट में डालने के लिए तैयार है, और अवधारणाएँ बड़े ऑटोमेशन पाइपलाइन में भी स्केल करती हैं।

आगे आप खोज सकते हैं:

- `Document.WarningCallback` का उपयोग करके **सेव** ऑपरेशन्स के दौरान चेतावनियों को कैप्चर करना।  
- उत्पादन मॉनिटरिंग के लिए चेतावनियों को फ़ाइल या टेलीमेट्री सिस्टम में लॉग करना।  
- कॉलबैक को विस्तारित करके गुम फ़ॉन्ट्स को स्वचालित रूप से ब्रांड‑स्पेसिफिक टाइपफ़ेस से बदलना।

प्रयोग करने में संकोच न करें—फ़ॉलबैक फ़ॉन्ट बदलें, बैच में अधिक दस्तावेज़ जोड़ें, या चेतावनी कलेक्टर को CI पाइपलाइन में इंटीग्रेट करें जो फ़ॉन्ट‑संबंधी रिग्रेशन को फ़्लैग करे। कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा वैसा ही रेंडर हों जैसा आप चाहते हैं!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}