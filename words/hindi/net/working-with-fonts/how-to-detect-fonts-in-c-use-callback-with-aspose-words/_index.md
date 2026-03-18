---
category: general
date: 2026-03-17
description: C# में Aspose.Words और एक वार्निंग कॉलबैक का उपयोग करके फ़ॉन्ट कैसे पहचानें।
  दस्तावेज़ लोड करते समय गायब फ़ॉन्ट प्रतिस्थापन को पकड़ने के लिए कॉलबैक का उपयोग
  करना सीखें।
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: hi
og_description: Aspose.Words का उपयोग करके C# में फ़ॉन्ट कैसे पता करें। यह गाइड दिखाता
  है कि दस्तावेज़ लोड करते समय लापता फ़ॉन्ट चेतावनियों को कैप्चर करने के लिए कॉलबैक
  का उपयोग कैसे करें।
og_title: C# में फ़ॉन्ट कैसे पहचानें – Aspose.Words के साथ कॉलबैक का उपयोग करें
tags:
- Aspose.Words
- C#
- Document Processing
title: C# में फ़ॉन्ट कैसे पहचानें – Aspose.Words के साथ कॉलबैक का उपयोग करें
url: /hi/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

codes closing.

We must ensure we preserve all shortcodes exactly.

Now produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में फ़ॉन्ट्स का पता कैसे लगाएँ – Aspose.Words के साथ कॉलबैक का उपयोग करें

क्या आपको कभी प्रोग्रामेटिकली Word दस्तावेज़ में **how to detect fonts** की आवश्यकता पड़ी है और आश्चर्य हुआ कि कुछ अक्षर रूपांतरण के बाद अजीब क्यों दिखते हैं? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया प्रोजेक्ट्स—इनवॉइस जेनरेटर, रिपोर्ट एक्सपोर्टर, या बैच‑प्रोसेसिंग पाइपलाइन—में गायब फ़ॉन्ट्स चुपचाप लेआउट गड़बड़ियां पैदा करते हैं जो डिबग करना कठिन होता है।  

अच्छी खबर? Aspose.Words आपको एक चेतावनी कॉलबैक के साथ इन समस्याओं को उजागर करने का साफ़ तरीका देता है। इस ट्यूटोरियल में आप देखेंगे **how to use callback** ताकि Aspose द्वारा दस्तावेज़ लोड करते समय किए गए प्रत्येक फ़ॉन्ट प्रतिस्थापन को कैप्चर किया जा सके, और आप एक तैयार‑चलाने‑योग्य उदाहरण के साथ निकलेंगे जो गायब फ़ॉन्ट्स की स्पष्ट रिपोर्ट प्रिंट करता है।

हम कवर करेंगे:

* न्यूनतम आवश्यकताएँ (एक .NET प्रोजेक्ट और Aspose.Words NuGet पैकेज)।  
* `IWarningCallback` को लागू करके `WarningType.FontSubstitution` को सुनना।  
* कॉलबैक को `LoadOptions` में जोड़ना और दस्तावेज़ लोड करना।  
* आउटपुट कैसा दिखता है, साथ ही प्रोडक्शन कोड के लिए कुछ व्यावहारिक टिप्स।

अंत तक, आप किसी भी DOCX, DOC, या RTF फ़ाइल में स्वचालित रूप से **detect fonts** कर पाएँगे और गायब‑फ़ॉन्ट जानकारी पर कार्रवाई कर सकेंगे—चाहे वह लॉगिंग हो, उपयोगकर्ता को अलर्ट करना हो, या फ़ॉलबैक फ़ॉन्ट का उपयोग करना हो।

---

![How to detect fonts in a Word document using Aspose.Words warning callback](https://example.com/images/detect-fonts.png "how to detect fonts in a Word document")

## आपको क्या चाहिए

* **.NET 6.0** या बाद का संस्करण (उदाहरण .NET Framework 4.6+ के साथ भी कम्पाइल होता है)।  
* **Aspose.Words for .NET** – NuGet के माध्यम से इंस्टॉल करें: `Install-Package Aspose.Words`।  
* एक सैंपल Word फ़ाइल जो जानबूझकर ऐसे फ़ॉन्ट का रेफ़रेंस देती है जो आपके सिस्टम में नहीं है (जैसे `MissingFont.docx`)।  

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है; सब कुछ Aspose नेमस्पेस के अंदर रहता है।

---

## Warning कॉलबैक के साथ फ़ॉन्ट्स का पता कैसे लगाएँ

### Step 1: Create a warning‑callback class

यह कॉलबैक `IWarningCallback` को इम्प्लीमेंट करता है। जब Aspose.Words किसी ऐसे फ़ॉन्ट से मिलता है जिसे वह नहीं ढूँढ़ पाता, तो वह `WarningInfo` को `WarningType.FontSubstitution` के साथ उठाता है। हमारा क्लास बस कंसोल पर एक मित्रवत लाइन लिखता है।

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Why this matters:** `WarningType.FontSubstitution` पर फ़िल्टर करके हम शोरभरे चेतावनियों (जैसे डिप्रिकेटेड फीचर्स) से बचते हैं और लॉग को ठीक उसी समस्या पर केंद्रित रखते हैं—**detecting fonts** जो मशीन पर मौजूद नहीं हैं।

---

### Step 2: Wire the callback into `LoadOptions`

`LoadOptions` आपको दस्तावेज़ पार्सिंग को कस्टमाइज़ करने की सुविधा देता है। हमारे `FontWarningCollector` को `WarningCallback` प्रॉपर्टी में असाइन करने से Aspose हर बार जब कोई फ़ॉन्ट मिसिंग हो, उसे कॉल करेगा।

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tip:** यदि आप प्रोग्रामेटिकली फ़ॉलबैक फ़ॉन्ट देना चाहते हैं, तो यहाँ `LoadOptions.FontSettings` भी सेट कर सकते हैं। यह एक एडवांस्ड सीनारियो है जिसे हम बाद में उल्लेख करेंगे।

---

### Step 3: Load the document and watch the output

अब हम वास्तविक फ़ाइल लोड करते हैं। जैसे ही Aspose दस्तावेज़ को पार्स करता है, कोई भी फ़ॉन्ट जो वह नहीं ढूँढ़ पाता है, हमारे कॉलबैक को ट्रिगर करता है।

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Expected console output** (मान लीजिए दस्तावेज़ में *Comic Sans MS* रेफ़रेंस है जो इंस्टॉल नहीं है):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

यदि दस्तावेज़ में कई मिसिंग फ़ॉन्ट्स हैं, तो आपको प्रत्येक फ़ॉन्ट के लिए एक लाइन दिखेगी—बिल्कुल वही **how to detect fonts** जानकारी जो आपको चाहिए।

---

## अधिक जटिल सीनारियो के लिए कॉलबैक का उपयोग कैसे करें

### Logging to a file instead of the console

प्रोडक्शन में आप संभवतः एक स्थायी लॉग चाहते हैं। `Console.WriteLine` को `StreamWriter` से बदलें:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Collecting warnings for later analysis

कभी‑कभी आपको दस्तावेज़ लोड होने के बाद मिसिंग फ़ॉन्ट्स की सूची चाहिए होती है, शायद UI डायलॉग दिखाने के लिए। चेतावनियों को `List<string>` में स्टोर करें और एक्सपोज़ करें:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Providing a fallback font programmatically

यदि आपके पास कोई कॉरपोरेट फ़ॉन्ट है जिसे आप लागू करना चाहते हैं, तो लोड करने से पहले उसे `FontSettings` में जोड़ सकते हैं:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

अब Aspose मिसिंग फ़ॉन्ट्स को *Arial Unicode MS* से प्रतिस्थापित करता है जबकि फिर भी कॉलबैक के माध्यम से प्रतिस्थापन की रिपोर्ट देता है। यह **how to use callback** को दोनों—डिटेक्शन और ऑटोमैटिक रेमेडिएशन—के लिए उपयोग करने का एक शानदार तरीका है।

---

## Common Pitfalls and Pro Tips

| समस्या | क्यों होता है | कैसे बचें |
|--------|----------------|--------------|
| **`Aspose.Words.Warnings` को रेफ़र करना भूल जाना** | `IWarningCallback` इंटरफ़ेस वहीं स्थित है। | फ़ाइल के शीर्ष पर `using Aspose.Words.Warnings;` जोड़ें। |
| **`LoadOptions` के बिना दस्तावेज़ लोड करना** | डिफ़ॉल्ट लोडर बिना सूचना के चुपचाप फ़ॉन्ट्स को प्रतिस्थापित करता है। | हमेशा एक `LoadOptions` इंस्टेंस बनाएं और अपना कॉलबैक असाइन करें। |
| **सीमित अनुमतियों वाले सर्वर पर चलाना** | लॉग फ़ाइल में लिखने से `UnauthorizedAccessException` हो सकता है। | एक लिखने योग्य फ़ोल्डर (जैसे ऐप का डेटा डायरेक्टरी) उपयोग करें या इन‑मेमोरी कलेक्शन पर रहें। |
| **एक ही कलेक्टर को कई थ्रेड्स द्वारा साझा करना** | `FontWarningCollector` डिफ़ॉल्ट रूप से थ्रेड‑सेफ़ नहीं है। | प्रति थ्रेड एक अलग कलेक्टर बनाएं या सूची को लॉक के साथ सुरक्षित रखें। |
| **एम्बेडेड फ़ॉन्ट्स के लिए कॉलबैक फायर होगा, ऐसा मान लेना** | एम्बेडेड फ़ॉन्ट्स पहले से ही दस्तावेज़ में मौजूद होते हैं; कोई चेतावनी नहीं आती। | यदि आपको एम्बेडेड फ़ॉन्ट की अखंडता जांचनी है, तो `FontSettings` के माध्यम से `FontInfo` जांचें। |

---

## Full Working Example (Copy‑Paste Ready)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**What you should see** (मान लीजिए फ़ाइल दो अनुपलब्ध फ़ॉन्ट्स रेफ़रेंस करती है):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

यदि फ़ाइल केवल इंस्टॉल किए गए फ़ॉन्ट्स का उपयोग करती है, तो कंसोल बस यह प्रिंट करेगा:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Wrapping Up

हमने Aspose.Words में एक कस्टम चेतावनी कॉलबैक को जोड़कर Word दस्तावेज़ में **detect fonts** करने की प्रक्रिया को समझा। यह तरीका हल्का है, और आवश्यक है:

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}