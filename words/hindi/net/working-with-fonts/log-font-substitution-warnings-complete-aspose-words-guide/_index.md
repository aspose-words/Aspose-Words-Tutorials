---
category: general
date: 2026-01-14
description: Aspose.Words के साथ Word दस्तावेज़ लोड करते समय फ़ॉन्ट प्रतिस्थापन चेतावनियों
  को लॉग करें। गायब फ़ॉन्ट्स का पता लगाना और C# में गायब फ़ॉन्ट्स को कैसे कैप्चर करें,
  सीखें।
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: hi
og_description: Aspose.Words के साथ Word दस्तावेज़ लोड करते समय फ़ॉन्ट प्रतिस्थापन
  चेतावनियों को लॉग करें। जानें कैसे गायब फ़ॉन्ट्स का पता लगाएँ और C# में उन्हें कैप्चर
  करें।
og_title: फ़ॉन्ट प्रतिस्थापन चेतावनियों का लॉग – पूर्ण Aspose.Words गाइड
tags:
- Aspose.Words
- C#
- Document Processing
title: फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करें – Aspose.Words का पूर्ण गाइड
url: /hi/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करें – पूर्ण Aspose.Words गाइड

फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करना आवश्यक है जब आपको यह सुनिश्चित करना हो कि Aspose.Words द्वारा लोड किए जाने के बाद Word दस्तावेज़ बिल्कुल वही दिखे जैसा था। यदि आप कभी यह जानना चाहते थे कि **missing fonts का पता कैसे लगाएँ** या यह जानना चाहते हैं **missing fonts को कैसे कैप्चर करें**, तो आप सही जगह पर हैं।  

इस ट्यूटोरियल में हम एक वास्तविक परिदृश्य से गुजरेंगे, आपको पूरा C# कोड दिखाएंगे, और समझाएंगे कि प्रत्येक पंक्ति क्यों महत्वपूर्ण है। अंत तक आप हर फ़ॉन्ट प्रतिस्थापन इवेंट को लॉग कर सकेंगे और उस पर कार्रवाई कर सकेंगे—कोई रहस्यमयी चेतावनी नहीं रहेगी।

![Log font substitution warnings example](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## आप क्या सीखेंगे

- कैसे `LoadOptions` को कॉन्फ़िगर करें ताकि Aspose.Words फ़ॉन्ट प्रतिस्थापन के लिए टाइप्ड चेतावनियाँ उठाए।  
- दस्तावेज़ लोड के दौरान **missing fonts का पता लगाने** के सटीक चरण।  
- **missing fonts को कैप्चर करने** और उन्हें अपने लॉग या मॉनिटरिंग सिस्टम में लिखने का साफ़ तरीका।  
- एज‑केस हैंडलिंग (जैसे, जब दस्तावेज़ में ऐसा फ़ॉन्ट हो जो सर्वर पर इंस्टॉल नहीं है)।  

### आवश्यकताएँ

- .NET 6.0 या बाद का (कोड .NET Framework 4.6+ के साथ भी काम करता है)।  
- एक वैध Aspose.Words for .NET लाइसेंस (या फ्री ट्रायल)।  
- C# और कंसोल एप्लिकेशन की बुनियादी समझ।  

यदि आपके पास ये सब हैं, तो चलिए शुरू करते हैं।

## चरण 1 – टाइप्ड चेतावनियों को उठाने के लिए LoadOptions सेट करें

समाधान का मुख्य भाग `LoadOptions.FontSubstitutionWarning` में निहित है। इसे `RaiseTypedWarnings` पर स्विच करके आप Aspose.Words को हर बार जब वह अनुरोधित फ़ॉन्ट नहीं पा सके, एक इवेंट फायर करने के लिए कहते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **यह क्यों महत्वपूर्ण है:**  
> डिफ़ॉल्ट व्यवहार चुपचाप एक गायब फ़ॉन्ट को सबसे नज़दीकी मिलते‑जुलते फ़ॉन्ट से बदल देता है, जिससे लेआउट गड़बड़ियां हो सकती हैं जिनका आपको पहले पता नहीं चलता। टाइप्ड चेतावनियों को उठाने से आपको पूरी दृश्यता मिलती है।

## चरण 2 – चेतावनी इवेंट की सदस्यता लें

अब हम `loadOptions.FontSubstitutionWarning` में हुक करते हैं। लैम्ब्डा को एक `e` ऑब्जेक्ट मिलता है जो हमें ठीक‑ठीक बताता है कि कौन सा फ़ॉन्ट गायब था और उसकी जगह कौन सा फ़ॉन्ट उपयोग किया गया।

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **प्रो टिप:** यदि आप इसे वेब सर्वर पर चला रहे हैं, तो `Console.WriteLine` को एक स्ट्रक्चर्ड लॉगर (Serilog, NLog, आदि) से बदलें ताकि बाद में डेटा को क्वेरी किया जा सके।

## चरण 3 – कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें

चेतावनी तंत्र स्थापित होने के बाद, बस दस्तावेज़ को सामान्य रूप से लोड करें। इवेंट हर गायब फ़ॉन्ट के लिए स्वचालित रूप से फायर होगा।

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### अपेक्षित कंसोल आउटपुट

यदि `input.docx` में *MyFancyFont* नामक फ़ॉन्ट का संदर्भ है जो इंस्टॉल नहीं है, तो आपको यह दिखेगा:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

हर पंक्ति एक **missing fonts का पता लगाने** इवेंट से मेल खाती है, जिससे आपको एक पूर्ण ऑडिट ट्रेल मिलती है।

## चरण 4 – एज केस और उन्नत परिदृश्यों को संभालना

### 4.1 जब कोई प्रतिस्थापन नहीं होता

कभी‑कभी दस्तावेज़ केवल सिस्टम फ़ॉन्ट्स का उपयोग करता है जो पहले से मौजूद होते हैं। ऐसे में चेतावनी इवेंट कभी नहीं फायर होता, और आपको कोई आउटपुट नहीं मिलती—यह एक अच्छा संकेत है कि आपका वातावरण सभी आवश्यक फ़ॉन्ट्स रखता है।

### 4.2 बाद के विश्लेषण के लिए चेतावनियों को कैप्चर करना

यदि आपको रात‑भर की रिपोर्ट के लिए चेतावनियों को संग्रहीत करना है, तो उन्हें एक सूची में एकत्र करें:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

लोड करने के बाद, आप `missingFonts` को JSON में सीरियलाइज़ कर सकते हैं, डेटाबेस में लिख सकते हैं, या सारांश ईमेल कर सकते हैं।

### 4.3 PDFs या अन्य फ़ॉर्मेट्स के साथ काम करना

उसी `LoadOptions` दृष्टिकोण को PDFs, RTF, और यहाँ तक कि HTML फ़ाइलों के `Load` कॉल्स पर भी लागू किया जा सकता है। बस वही विकल्प इंस्टेंस पास करें, और Aspose.Words किसी भी फ़ॉन्ट के लिए चेतावनी उठाएगा जिसे वह मैच नहीं कर पाएगा।

## चरण 5 – परिणाम को प्रोग्रामेटिकली सत्यापित करें

यदि आप कंसोल को आँखों से देखने के बजाय एक ऑटोमेटेड टेस्ट पसंद करते हैं, तो यह सुनिश्चित करें कि सूची में अपेक्षित एंट्रीज़ मौजूद हैं:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

यह स्निपेट **missing fonts को कैसे कैप्चर करें** को कोड में दर्शाता है, न कि केवल लॉग में।

## सामान्य pitfalls & उन्हें कैसे टालें

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| `RaiseTypedWarnings` सेट करना भूल जाना | डिफ़ॉल्ट `DoNotRaise` है, इसलिए कोई इवेंट फायर नहीं होते। | चरण 1 में दिखाए अनुसार स्पष्ट रूप से `FontSubstitutionWarning` सेट करें। |
| वेब ऐप में `Console.WriteLine` का उपयोग | IIS/ASP.NET Core में कंसोल आउटपुट गायब हो जाता है। | एक स्थायी लॉगर (जैसे, Serilog) पर स्विच करें। |
| रिलेटिव पाथ से दस्तावेज़ लोड करना | रन‑टाइम पर वर्किंग डायरेक्टरी अलग हो सकती है। | एब्सोल्यूट पाथ या `Path.Combine(AppContext.BaseDirectory, "input.docx")` उपयोग करें। |
| `SubstitutedFontName` को अनदेखा करना | आपको नहीं पता चलता कि कौन सा फ़ॉलबैक चुना गया। | हमेशा `FontName` और `SubstitutedFontName` दोनों को लॉग करें। |

## बोनस: फ़ॉन्ट इंस्टॉलेशन का ऑटोमेशन

यदि आप डिप्लॉयमेंट वातावरण को नियंत्रित करते हैं, तो आप एक PowerShell स्क्रिप्ट के माध्यम से गायब फ़ॉन्ट्स को पहले से इंस्टॉल कर सकते हैं:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

ऐप्लिकेशन शुरू होने से पहले इसे चलाने से अधिकांश **missing fonts का पता लगाने** चेतावनियों को पूरी तरह समाप्त किया जा सकता है।

## निष्कर्ष

हमने वह सब कवर किया है जो आपको Aspose.Words के साथ Word दस्तावेज़ लोड करते समय **फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करने** के लिए चाहिए। `LoadOptions` को कॉन्फ़िगर करके, चेतावनी इवेंट की सदस्यता लेकर, और वैकल्पिक रूप से परिणामों को स्थायी बनाकर, आप विश्वसनीय रूप से **missing fonts का पता लगा** सकते हैं और **missing fonts को कैसे कैप्चर करें** को समझ सकते हैं किसी भी .NET प्रोजेक्ट के लिए।

कोड को अपनाएँ, अपने स्टैक के अनुसार लॉगर को ट्यून करें, और अब आप साइलेंट फ़ॉन्ट स्वैप से कभी आश्चर्यचकित नहीं होंगे। आगे के कदम हो सकते हैं:

- चेतावनी सूची को अपने CI/CD पाइपलाइन के साथ एकीकृत करना ताकि महत्वपूर्ण फ़ॉन्ट्स गायब होने पर बिल्ड फेल हो जाए।  
- दस्तावेज़ों के एक फ़्लीट में फ़ॉन्ट उपयोग की निगरानी के लिए इस दृष्टिकोण का विस्तार करना।  
- कस्टम फ़ॉलबैक फ़ॉन्ट्स प्रदान करने के लिए Aspose.Words के `FontSettings` API का अन्वेषण करना।

कोई प्रश्न या जटिल परिदृश्य है? टिप्पणी छोड़ें, और चलिए साथ में ट्रबलशूट करते हैं। Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}