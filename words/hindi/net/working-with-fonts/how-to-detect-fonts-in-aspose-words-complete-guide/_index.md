---
category: general
date: 2026-04-07
description: Aspose.Words का उपयोग करके C# में फ़ॉन्ट्स का पता लगाना और लापता फ़ॉन्ट्स
  को संभालते समय चेतावनियों को कैप्चर करना सीखें। चरण‑दर‑चरण कोड शामिल है।
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: hi
og_description: Aspose.Words में फ़ॉन्ट कैसे पता करें? चेतावनियों को पकड़ने और लापता
  फ़ॉन्ट्स को आसानी से संभालने के लिए इस ट्यूटोरियल का पालन करें।
og_title: Aspose.Words में फ़ॉन्ट कैसे पहचानें – पूर्ण मार्गदर्शिका
tags:
- Aspose.Words
- C#
- Font handling
title: Aspose.Words में फ़ॉन्ट कैसे पहचानें – पूर्ण गाइड
url: /hi/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में फ़ॉन्ट्स का पता कैसे लगाएँ – पूर्ण गाइड

क्या आपने कभी सोचा है **how to detect fonts** जो Word दस्तावेज़ में अनुपलब्ध हैं, उसे प्रोडक्शन में भेजने से पहले? आप अकेले नहीं हैं। कई एंटरप्राइज़ परिदृश्यों में एक अनजाना फ़ॉन्ट PDF रूपांतरण पाइपलाइन को तोड़ सकता है या लेआउट गड़बड़ियां पैदा कर सकता है जो पेशेवर नहीं लगतीं। अच्छी बात यह है कि Aspose.Words आपको इन अनुपस्थित टाइपफ़ेस को पहचानने और स्पष्ट चेतावनियाँ दिखाने का अंतर्निहित तरीका प्रदान करता है।

इस ट्यूटोरियल में हम बिल्कुल **how to detect fonts**, **how to capture warnings**, और **handle missing fonts** के सर्वोत्तम अभ्यासों को देखेंगे ताकि आपका एप्लिकेशन मजबूत बना रहे। कोई बाहरी टूल नहीं, कोई अनुमान नहीं—सिर्फ शुद्ध C# कोड जिसे आप अभी अपने प्रोजेक्ट में जोड़ सकते हैं।

> **Quick preview:** अंत तक आपके पास एक पुन: उपयोग योग्य `FontSubstitutionWarningCollector` होगा जो दस्तावेज़ लोडिंग के दौरान प्रत्येक फ़ॉन्ट‑सब्स्टिट्यूशन संदेश एकत्र करता है, और आप जानेंगे कि जब कोई फ़ॉन्ट नहीं मिला तो कैसे प्रतिक्रिया दें।

---

## आप क्या सीखेंगे

- `LoadOptions` को इस तरह कॉन्फ़िगर करें कि वह फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनियों को सुन सके।  
- इन चेतावनियों को एक कस्टम कलेक्टर क्लास में कैप्चर करें।  
- एकत्रित चेतावनियों को प्रोसेस करें और तय करें कि एबॉर्ट करना है, लॉग करना है, या फ़ॉन्ट्स को बदलना है।  
- रिमोट या एम्बेडेड फ़ॉन्ट्स का संदर्भ देने वाले दस्तावेज़ों के लिए एज‑केस हैंडलिंग।  

**Prerequisites:** .NET 6+ (या .NET Framework 4.6+), Aspose.Words for .NET (नवीनतम संस्करण), और C# की बुनियादी परिचितता। यदि आपने पहले कभी Aspose.Words का उपयोग नहीं किया है, तो चिंता न करें—यह गाइड केवल कुछ मिनटों की सेटअप समय मानता है।

## Aspose.Words LoadOptions का उपयोग करके फ़ॉन्ट्स का पता कैसे लगाएँ

गायब फ़ॉन्ट्स का पता लगाने की पहली कदम है Aspose.Words को उन्हें रिपोर्ट करने के लिए कहना। यह `LoadOptions.WarningCallback` प्रॉपर्टी के माध्यम से किया जाता है, जो किसी भी क्लास को स्वीकार करती है जो `IWarningCallback` को इम्प्लीमेंट करती है। नीचे हम एक छोटा कलेक्टर बनाते हैं जो प्रत्येक चेतावनी को बाद में निरीक्षण के लिए संग्रहीत करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Why this matters:** बिना वार्निंग कॉलबैक के, Aspose.Words चुपचाप गायब फ़ॉन्ट्स को डिफ़ॉल्ट फ़ॉन्ट से बदल देता है, और आपको कभी पता नहीं चलता कि समस्या मौजूद है। `WarningType.FontSubstitution` को कैप्चर करके हमें पूरी दृश्यता मिलती है—बिल्कुल वही डेटा जो आपको **detect fonts** करने के लिए चाहिए जो होस्ट मशीन पर उपलब्ध नहीं हैं।

अब हम कलेक्टर को `LoadOptions` में जोड़ते हैं और एक दस्तावेज़ लोड करते हैं:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Pro tip:** यदि आप बैच में कई दस्तावेज़ों के साथ काम करते हैं, तो वही `FontSubstitutionWarningCollector` इंस्टेंस पुन: उपयोग करें लेकिन लोड्स के बीच `Clear()` को कॉल करना याद रखें ताकि विभिन्न फ़ाइलों की चेतावनियों का मिश्रण न हो।

## दस्तावेज़ लोड के दौरान चेतावनियों को कैप्चर करें

दस्तावेज़ लोड होने के बाद, कलेक्टर में पहले से ही प्रत्येक फ़ॉन्ट‑संबंधित चेतावनी मौजूद होती है। अगला तर्कसंगत प्रश्न है: *मैं चेतावनियों को कैसे कैप्चर करूँ* ताकि उन्हें लॉग या प्रदर्शित करना आसान हो?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

सामान्य आउटपुट इस प्रकार दिखता है:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**What this tells you:** प्रत्येक पंक्ति मूल फ़ॉन्ट नाम और वह फॉलबैक दिखाती है जो Aspose.Words ने चुना। इस जानकारी के साथ आप तय कर सकते हैं कि फॉलबैक स्वीकार्य है या आपको गायब फ़ॉन्ट को मैन्युअल रूप से एम्बेड करना चाहिए।

## गायब फ़ॉन्ट्स को सहजता से संभालें

चेतावनियों का पता लगाना और उन्हें कैप्चर करना केवल आधा काम है। वास्तविक मूल्य तब आता है जब आप **handle missing fonts** को प्रोडक्शन‑रेडी तरीके से संभालते हैं। नीचे तीन सामान्य रणनीतियाँ दी गई हैं:

1. **Log and Continue** – बैच प्रोसेसिंग के लिए उपयुक्त जहाँ आपको केवल ऑडिट ट्रेल चाहिए।  
2. **Abort on Critical Fonts** – यदि कोई विशेष फ़ॉन्ट (जैसे, ब्रांड‑विशिष्ट टाइपफ़ेस) गायब है तो एक्सेप्शन फेंके।  
3. **Embed the Font On‑The‑Fly** – ज्ञात फ़ोल्डर से गायब फ़ॉन्ट को लोड करें और दस्तावेज़ को पुनः‑लोड करने से पहले Aspose.Words के साथ रजिस्टर करें।  

### उदाहरण: एक महत्वपूर्ण फ़ॉन्ट पर एबॉर्ट करें

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### उदाहरण: गायब फ़ॉन्ट्स को ऑटो‑एम्बेड करें

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Why these patterns help:** स्पष्ट रूप से तय करके कि फ़ॉन्ट गायब होने पर क्या करना है, आप चुपचाप होने वाले फॉलबैक्स को समाप्त कर देते हैं जो ब्रांडिंग या पठनीयता को नुकसान पहुँचा सकते हैं। यही **handling missing fonts** का सार है, एक नियंत्रित तरीके से।

## पूर्ण कार्यशील उदाहरण

सब कुछ मिलाकर, यहाँ एक एकल, तैयार‑चलाने योग्य प्रोग्राम है जो **how to detect fonts**, **how to capture warnings**, और लॉगिंग द्वारा **handle missing fonts** करने की एक सरल नीति को दर्शाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Expected result:** जब आप प्रोग्राम को ऐसे दस्तावेज़ के खिलाफ चलाते हैं जो मशीन पर मौजूद नहीं होने वाले फ़ॉन्ट का संदर्भ देता है, तो कंसोल प्रत्येक सब्स्टिट्यूशन चेतावनी सूचीबद्ध करेगा। यदि कोई चेतावनी `critical` सेट के फ़ॉन्ट से संबंधित है, तो प्रोग्राम जल्दी समाप्त हो जाएगा, जिससे एक दोषपूर्ण PDF उत्पन्न होने से बचा जा सके।

## अक्सर पूछे जाने वाले प्रश्न (FAQs)

| Question | Answer |
|----------|--------|
| *क्या इस कोड को उपयोग करने के लिए मुझे Aspose.Words का लाइसेंस चाहिए?* | हाँ, एक वैध Aspose.Words लाइसेंस मूल्यांकन वॉटरमार्क को हटाता है और पूरी कार्यक्षमता अनलॉक करता है। |
| *क्या यह तरीका एम्बेडेड फ़ॉन्ट्स का पता लगा सकता है?* | एम्बेडेड फ़ॉन्ट्स पहले से ही फ़ाइल का हिस्सा होते हैं, इसलिए Aspose.Words कोई सब्स्टिट्यूशन चेतावनी नहीं देगा। यदि आवश्यक हो तो आप `Document.FontInfos` की जाँच करके एम्बेडेड फ़ॉन्ट्स की सूची बना सकते हैं। |
| *यदि गायब फ़ॉन्ट Windows पर सिस्टम फ़ॉन्ट है लेकिन Linux पर नहीं है तो क्या होगा?* | Linux पर भी वही चेतावनी आएगी क्योंकि फ़ॉन्ट वहाँ स्थापित नहीं है। आवश्यक `.ttf` फ़ाइलों को अपने ऐप के साथ शिप करने के लिए “handle missing fonts” रणनीति का उपयोग करें। |
| *क्या वार्निंग कलेक्टर थ्रेड* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}