---
category: general
date: 2026-04-04
description: Aspose.Words LoadOptions का उपयोग करके C# में चेतावनियों को कैप्चर करना,
  गायब फ़ॉन्ट्स का पता लगाना, और प्रतिस्थापन घटनाओं को लॉग करना सीखें।
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: hi
og_description: Aspose.Words LoadOptions का उपयोग करके C# में चेतावनियों को कैप्चर
  करने, गायब फ़ॉन्ट्स का पता लगाने और प्रतिस्थापन घटनाओं को लॉग करने का तरीका।
og_title: C# में चेतावनियों को कैसे कैप्चर करें – गायब फ़ॉन्ट्स का पता लगाएँ और प्रतिस्थापन
  को लॉग करें
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: C# में चेतावनियों को कैसे पकड़ें – गायब फ़ॉन्ट्स का पता लगाएँ और प्रतिस्थापन
  को लॉग करें
url: /hi/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में चेतावनियों को कैसे कैप्चर करें – लापता फ़ॉन्ट्स का पता लगाएँ और प्रतिस्थापन को लॉग करें

क्या आपने कभी सोचा है **कैसे चेतावनियों को कैप्चर किया जाए** जब आप लापता फ़ॉन्ट्स वाले Word दस्तावेज़ को लोड करते हैं? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया प्रोजेक्ट्स में माइग्रेशन के दौरान फ़ॉन्ट्स खो जाते हैं, और चुपचाप फ़ॉलबैक आपके लेआउट को बिगाड़ सकता है। अच्छी खबर? Aspose.Words आपको इन चेतावनियों को सुनने, लापता फ़ॉन्ट्स का पता लगाने और प्रत्येक प्रतिस्थापन को लॉग करने का साफ़ तरीका देता है ताकि आप बाद में स्रोत को ठीक कर सकें।

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य समाधान के माध्यम से चलेंगे जो **कैसे चेतावनियों को कैप्चर किया जाए** दिखाता है, **लापता फ़ॉन्ट्स का पता लगाता** है, और **कैसे प्रतिस्थापन को लॉग किया जाए** समझाता है। अंत तक, आपके पास एक पुन: उपयोग योग्य चेतावनी हैंडलर, पूरी तरह कॉन्फ़िगर किया गया `LoadOptions` ऑब्जेक्ट, और एक नमूना कंसोल आउटपुट होगा जिसे आप सत्यापित कर सकते हैं।

> **Prerequisite:** आपको NuGet के माध्यम से Aspose.Words for .NET (v24.x या बाद का) स्थापित करना होगा और एक बेसिक C# डेवलपमेंट एनवायरनमेंट (Visual Studio 2022 या VS Code ठीक रहेगा) चाहिए।

---

## दस्तावेज़ लोड करते समय चेतावनियों को कैसे कैप्चर करें

समाधान का मूल भाग एक क्लास है जो `IWarningCallback` को इम्प्लीमेंट करती है। Aspose.Words इस कॉलबैक को स्वचालित रूप से प्रत्येक चेतावनी के लिए कॉल करता है जो दस्तावेज़ लोडिंग के दौरान उत्पन्न होती है, जिसमें फ़ॉन्ट प्रतिस्थापन चेतावनियाँ भी शामिल हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Why this step?**  
> By filtering on `WarningType.FontSubstitution` we avoid clutter from unrelated warnings (like deprecated features). This makes the log focused on the exact problem you care about—missing fonts.

> **इस चरण की आवश्यकता क्यों है?**  
> `WarningType.FontSubstitution` पर फ़िल्टर करके हम असंबंधित चेतावनियों (जैसे डिप्रिकेटेड फीचर्स) से उत्पन्न अव्यवस्था से बचते हैं। इससे लॉग केवल उसी समस्या पर केंद्रित रहता है जिसमें आपकी रुचि है—लापता फ़ॉन्ट्स।

---

## Aspose.Words के साथ लापता फ़ॉन्ट्स का पता लगाएँ

जब कोई दस्तावेज़ ऐसी फ़ॉन्ट का संदर्भ देता है जो मशीन पर स्थापित नहीं है, तो Aspose.Words सबसे नज़दीकी मिलान को प्रतिस्थापित करता है और एक चेतावनी उत्पन्न करता है। हमारा ऊपर का हैंडलर प्रत्येक घटना को पकड़ लेगा, प्रभावी रूप से **लापता फ़ॉन्ट्स का पता लगाता** है।

इसे काम में देखने के लिए हमें `LoadOptions` को कॉन्फ़िगर करना होगा और हैंडलर को अटैच करना होगा:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** If you prefer to collect warnings for later processing (e.g., write to a file), replace `Console.WriteLine` with code that adds the message to a `List<string>`.

> **टिप:** यदि आप बाद में प्रोसेसिंग के लिए चेतावनियों को एकत्र करना चाहते हैं (जैसे फ़ाइल में लिखना), तो `Console.WriteLine` को उस कोड से बदलें जो संदेश को `List<string>` में जोड़ता है।

---

## प्रतिस्थापन घटनाओं को कैसे लॉग करें

लॉगिंग उतनी ही सरल है जितना कि चेतावनी आउटपुट को एक स्थायी स्टोर की ओर निर्देशित करना। नीचे एक त्वरित उदाहरण है जो प्रत्येक प्रतिस्थापन चेतावनी को `font-warnings.log` नामक टेक्स्ट फ़ाइल में लिखता है।

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Why log to a file?**  
> Persistent logs let you audit font issues across multiple runs, automate alerts, or feed the data into a build‑pipeline check.

> **फ़ाइल में लॉग क्यों रखें?**  
> स्थायी लॉग आपको कई रन में फ़ॉन्ट समस्याओं का ऑडिट करने, अलर्ट को स्वचालित करने, या डेटा को बिल्ड‑पाइपलाइन चेक में फीड करने की सुविधा देते हैं।

---

## पूर्ण कार्यशील उदाहरण

सब कुछ मिलाकर, यहाँ एक स्व-निहित कंसोल एप्लिकेशन है जिसे आप कॉपी, पेस्ट और रन कर सकते हैं। यह **कैसे चेतावनियों को कैप्चर किया जाए**, **लापता फ़ॉन्ट्स का पता लगाया जाए**, और **कैसे प्रतिस्थापन को लॉग किया जाए** एक साथ दिखाता है।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### अपेक्षित कंसोल आउटपुट

यदि `input.docx` ऐसी फ़ॉन्ट का संदर्भ देता है जो स्थापित नहीं है, तो आपको कुछ इस तरह दिखेगा:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

यदि आप `FileLoggingWarningHandler` पर स्विच करते हैं, तो वही लाइन्स `font-warnings.log` में टाइमस्टैम्प के साथ दिखाई देंगी।

![कैसे चेतावनियों को कैप्चर करने का कंसोल आउटपुट](image-placeholder.png)

---

## सामान्य प्रश्न और किनारी मामलों

### यदि मुझे फ़ॉन्ट प्रतिस्थापन के अलावा *सभी* चेतावनियों को कैप्चर करना हो तो क्या करें?

सिर्फ `if (info.Type == WarningType.FontSubstitution)` जांच को हटा दें। कॉलबैक हर चेतावनी प्रकार (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, आदि) को प्राप्त करेगा। फिर आप `info.Type` के आधार पर प्रत्येक केस को अलग‑अलग हैंडल कर सकते हैं।

### क्या यह PDFs के साथ काम करता है या केवल Word दस्तावेज़ों के साथ?

`LoadOptions` और `IWarningCallback` Aspose.Words का हिस्सा हैं, इसलिए वे Word‑संगत फ़ॉर्मैट्स (`.docx`, `.doc`, `.rtf`, `.html`) पर लागू होते हैं। PDFs के लिए आपको Aspose.PDF के अपने चेतावनी तंत्र का उपयोग करना पड़ेगा।

### लॉग करने के बजाय चेतावनियों को दबाना कैसे संभव है?

`LoadOptions.WarningCallback = null` सेट करें या कॉलबैक को इम्प्लीमेंट करें लेकिन मेथड बॉडी को खाली छोड़ दें। लाइब्रेरी फिर भी चुपचाप प्रतिस्थापन करेगी।

### थ्रेड‑सेफ़्टी के बारे में क्या?

कॉलबैक इंस्टेंस उसी थ्रेड पर चलाया जाता है जो दस्तावेज़ को लोड करता है, इसलिए जब तक आप हैंडलर को समानांतर लोड्स में साझा नहीं करते, अतिरिक्त सिंक्रनाइज़ेशन की आवश्यकता नहीं है। यदि आप ऐसा करते हैं, तो साझा संसाधनों (जैसे लॉग फ़ाइल) को लॉक से सुरक्षित रखें या concurrent collections का उपयोग करें।

---

## निष्कर्ष

हमने Aspose.Words से **कैसे चेतावनियों को कैप्चर किया जाए** को कवर किया, आपको **लापता फ़ॉन्ट्स का पता लगाने** का तरीका दिखाया, और बाद में विश्लेषण के लिए **कैसे प्रतिस्थापन को लॉग किया जाए** समझाया। `LoadOptions` में एक सरल `IWarningCallback` इम्प्लीमेंटेशन जोड़कर, आप फ़ॉन्ट‑संबंधी मुद्दों पर पूरी दृश्यता प्राप्त करते हैं बिना कोडबेस को अव्यवस्थित किए।

अगले कदम? लॉगर को ई‑मेल भेजने, Azure Monitor के साथ इंटीग्रेट करने, या बिल्ड सर्वर पर लापता फ़ॉन्ट्स को स्वचालित रूप से इंस्टॉल करने के लिए विस्तारित करें। आप अन्य चेतावनी प्रकारों को भी एक्सप्लोर कर सकते हैं—`WarningType.DegradedDocument` आपको उन फीचर्स के बारे में सूचित कर सकता है जो कन्वर्ज़न प्रक्रिया में नहीं बच पाए।

फ़ॉन्ट हैंडलिंग या Aspose.Words के बारे में और प्रश्न हैं? टिप्पणी छोड़ें या Aspose फ़ोरम पर नया इश्यू खोलें। Happy coding, और आपके दस्तावेज़ हमेशा सही टाइपफ़ेस के साथ रेंडर हों!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}