---
category: general
date: 2026-03-06
description: C# में Word दस्तावेज़ लोड करते समय फ़ॉन्ट चेतावनियों को पकड़ें। गायब
  फ़ॉन्ट्स का पता लगाना, दस्तावेज़ के फ़ॉन्ट्स की जाँच करना, और गायब फ़ॉन्ट्स को कुशलतापूर्वक
  संभालना सीखें।
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: hi
og_description: C# में Word दस्तावेज़ लोड करते समय फ़ॉन्ट चेतावनियों को पकड़ें। यह
  ट्यूटोरियल दिखाता है कि कैसे गायब फ़ॉन्ट्स का पता लगाएँ, दस्तावेज़ के फ़ॉन्ट्स की
  जाँच करें, और गायब फ़ॉन्ट्स को संभालें।
og_title: C# में फ़ॉन्ट चेतावनियों को कैप्चर करें – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Font Management
title: C# में फ़ॉन्ट चेतावनियों को कैप्चर करें – पूर्ण मार्गदर्शिका
url: /hi/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Warnings in C# – Complete Guide

क्या आपको कभी Word दस्तावेज़ प्रोसेस करते समय **फ़ॉन्ट चेतावनियों को पकड़ने** की ज़रूरत पड़ी है? फ़ॉन्ट चेतावनियों को पकड़ना **ग़ायब फ़ॉन्ट्स का पता लगाने** और यह सुनिश्चित करने के लिए आवश्यक है कि अंतिम आउटपुट बिल्कुल वही दिखे जैसा आपने चाहा था।  

इस ट्यूटोरियल में हम एक व्यावहारिक, एंड‑टू‑एंड उदाहरण के माध्यम से दिखाएंगे कि कैसे एक `.docx` फ़ाइल को लोड किया जाए, लोडिंग प्रक्रिया की निगरानी की जाए, और किसी भी फ़ॉन्ट प्रतिस्थापन की रिपोर्ट की जाए। अंत तक आप जानेंगे कि कैसे **वर्ड दस्तावेज़ को सुरक्षित रूप से लोड** किया जाए, **दस्तावेज़ के फ़ॉन्ट्स की जाँच** की जाए, और **ग़ायब फ़ॉन्ट्स को बिना आश्चर्यजनक रन‑टाइम त्रुटियों के संभाला** जाए।

## What You’ll Learn

- कैसे Aspose.Words `Document` में एक warning collector जोड़ा जाए।
- कौन‑से warning प्रकार ग़ायब या प्रतिस्थापित फ़ॉन्ट को दर्शाते हैं।
- प्रोडक्शन‑ग्रेड एप्लिकेशन में उन चेतावनियों को लॉग या प्रतिक्रिया देने के तरीके।
- यदि आपको **ग़ायब फ़ॉन्ट्स को सहजता से संभालना** है तो कस्टम फ़ॉन्ट स्रोतों को कॉन्फ़िगर करने के टिप्स।

> **Prerequisite:** आपके पास एक वैध Aspose.Words for .NET लाइसेंस है (या आप फ्री ट्रायल उपयोग कर रहे हैं) और एक .NET डेवलपमेंट एनवायरनमेंट (Visual Studio, Rider, या VS Code) स्थापित है। अन्य कोई लाइब्रेरी आवश्यक नहीं है।

---

## Capture Font Warnings – Step‑by‑Step

नीचे पूरा, चलाने योग्य कोड दिया गया है। प्रत्येक सेक्शन को अलग‑अलग स्टेप में विभाजित किया गया है ताकि आप कॉपी‑पेस्ट, प्रयोग और लॉजिक को विस्तारित कर सकें।

![फ़ॉन्ट चेतावनियों का आरेख](image.png "चेतावनी संग्रह दिखाता आरेख"){: alt="फ़ॉन्ट चेतावनियों का आरेख"}

### Step 1: Load the Word Document

सबसे पहले, हमें **वर्ड दस्तावेज़ को लोड** करना है जिसमें ऐसे फ़ॉन्ट हो सकते हैं जो वर्तमान मशीन पर इंस्टॉल नहीं हैं। `Document` कंस्ट्रक्टर यह भारी काम करता है, लेकिन हम कॉल को अलग रखेंगे ताकि बाद में आवश्यकता पड़ने पर आप इसे स्ट्रीम या बाइट एरे में बदल सकें।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Why this matters:** बिना warning handler के दस्तावेज़ लोड करने पर किसी भी फ़ॉन्ट प्रतिस्थापन को चुपचाप अनदेखा किया जाता है। `WarningCallback` को *लोड से पहले* सेट करके हम सुनिश्चित करते हैं कि हर `FontSubstitution` चेतावनी हमें दिखाई दे।

### Step 2: Attach a Warning Collector

`WarningInfoCollector` क्लास `IWarningCallback` का एक बिल्ट‑इन इम्प्लीमेंटेशन है। यह प्रत्येक चेतावनी को एक लिस्ट में स्टोर करता है जिसे बाद में जांचा जा सकता है।

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Pro tip:** यदि आपको **ग़ायब फ़ॉन्ट्स को** अधिक आक्रामक तरीके से संभालना है (जैसे लोड को रोकना या किसी विशिष्ट फ़ॉलबैक से बदलना), तो आप `Console.WriteLine` को कस्टम लॉजिक से बदल सकते हैं—एक एक्सेप्शन थ्रो करें, फ़ाइल में लॉग करें, या यहाँ तक कि एक कस्टम फ़ॉन्ट स्रोत जोड़ें।

### Step 3: Verify the Output

कंसोल से प्रोग्राम चलाएँ। यदि आपका `input.docx` ऐसा फ़ॉन्ट उपयोग करता है जो इंस्टॉल नहीं है, तो आपको इस तरह की लाइन्स दिखेंगी:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

यदि कोई आउटपुट नहीं आता, तो दस्तावेज़ या तो केवल उपलब्ध फ़ॉन्ट्स ही उपयोग कर रहा है **या** Aspose.Words ने अपने बिल्ट‑इन फ़ॉलबैक कलेक्शन में मिलते‑जुलते फ़ॉन्ट को पाया है। किसी भी स्थिति में, आपने सफलतापूर्वक **दस्तावेज़ के फ़ॉन्ट्स की जाँच** कर ली है।

---

## Detect Missing Fonts Without a License (Free Trial)

भले ही आप 30‑दिन के ट्रायल पर हों, warning मैकेनिज़्म बिल्कुल वही काम करता है। केवल अंतर यह है कि ट्रायल जनरेटेड आउटपुट में एक वॉटरमार्क जोड़ता है, जो **warning संग्रह को प्रभावित नहीं करता**। इसलिए आप पूरी लाइसेंस खरीदने से पहले सुरक्षित रूप से **ग़ायब फ़ॉन्ट्स का पता** लगा सकते हैं।

---

## Handle Missing Fonts – Advanced Options

कभी‑कभी आप अपने स्वयं के फ़ॉन्ट फ़ाइलें (जैसे कॉरपोरेट ब्रांड फ़ॉन्ट्स) प्रदान करना चाहते हैं ताकि प्रतिस्थापन न हो। Aspose.Words आपको कस्टम फ़ॉन्ट फ़ोल्डर्स रजिस्टर करने की सुविधा देता है:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

ऊपर दिया गया कोड **दस्तावेज़ लोड करने से पहले** रखें यदि आप चाहते हैं कि लोडर प्रारंभिक पार्सिंग चरण में इन फ़ॉन्ट्स को विचार करे। यह **ग़ायब फ़ॉन्ट्स को** डिफ़ॉल्ट सिस्टम फ़ॉन्ट्स पर निर्भर हुए बिना संभालने का सबसे भरोसेमंद तरीका है।

---

## Common Pitfalls & How to Avoid Them

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Warning collector attached after loading** | दस्तावेज़ पहले ही पार्स हो चुका है, इसलिए कोई चेतावनी रिकॉर्ड नहीं होती। | `new Document(path)` को कॉल करने **से पहले** `WarningCallback` जोड़ें। |
| **Only generic warnings appear** | आप गलत `WarningType` फ़िल्टर कर रहे हैं। | फ़ॉन्ट समस्याओं पर फोकस करने के लिए `WarningType.FontSubstitution` उपयोग करें। |
| **No output despite missing fonts** | Aspose.Words ने एक बिल्ट‑इन फ़ॉलबैक (जैसे Arial) पाया। | `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` के द्वारा बिल्ट‑इन फ़ॉलबैक्स को डिसेबल करें। |
| **Performance hit when scanning large docs** | हर चेतावनी को इकट्ठा करना महंगा हो सकता है। | संग्रह को केवल `FontSubstitution` तक सीमित रखें, या बैच में चेतावनियों को प्रोसेस करें। |

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Expected console output** (मान लीजिए दो ग़ायब फ़ॉन्ट्स हैं):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

यदि कंसोल केवल “Document loaded successfully” दिखाता है और अन्य कोई आउटपुट नहीं, तो आपने **दस्तावेज़ के फ़ॉन्ट्स की जाँच** कर ली है और कोई ग़ायब फ़ॉन्ट नहीं मिला।

---

## Conclusion

हमने दिखाया कि कैसे C# में Aspose.Words का उपयोग करके **फ़ॉन्ट चेतावनियों को पकड़ें**, **ग़ायब फ़ॉन्ट्स का पता लगाएँ**, **वर्ड दस्तावेज़ को सुरक्षित रूप से लोड करें**, **दस्तावेज़ के फ़ॉन्ट्स की जाँच करें**, और कस्टम फ़ॉन्ट स्रोतों के माध्यम से **ग़ायब फ़ॉन्ट्स को संभालें**।  

इस पैटर्न के साथ आप किसी भी ऑटोमेशन पाइपलाइन में फ़ॉन्ट‑वैलिडेशन को इंटीग्रेट कर सकते हैं—चाहे आप PDFs जेनरेट कर रहे हों, HTML में कन्वर्ट कर रहे हों, या बस Word फ़ाइलों को आर्काइव कर रहे हों।

### What’s Next?

- अपना खुद का फ़ॉलबैक नियम परिभाषित करने के लिए **FontSettings.SubstitutionSettings** API को एक्सप्लोर करें।
- प्रोडक्शन मॉनिटरिंग के लिए warning संग्रह को Serilog, NLog जैसे लॉगिंग फ्रेमवर्क के साथ जोड़ें।
- उसी दृष्टिकोण को अन्य चेतावनी प्रकारों (जैसे इमेज रिज़ॉल्यूशन या असमर्थित फीचर्स) को पकड़ने के लिए उपयोग करें।

फ़ॉन्ट हैंडलिंग या Aspose.Words के बारे में और प्रश्न हैं? टिप्पणी छोड़ें या Aspose कम्युनिटी फ़ोरम में जुड़ें। Happy coding, और आपके दस्तावेज़ हमेशा वही फ़ॉन्ट्स दिखाएँ जो आप चाहते हैं!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}