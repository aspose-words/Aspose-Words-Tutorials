---
category: general
date: 2026-01-06
description: Aspose.Words का उपयोग करके दस्तावेज़ लोड करते समय चेतावनियाँ प्राप्त
  करने और फ़ॉन्ट्स की निगरानी करने के तरीके सीखें। यह गाइड चेतावनी कॉलबैक और फ़ॉन्ट‑प्रतिस्थापन
  ट्रैकिंग को कवर करता है।
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: hi
og_description: Aspose.Words में चेतावनियां कैसे प्राप्त करें? दस्तावेज़ लोड करते
  समय फ़ॉन्ट्स की निगरानी करने और प्रतिस्थापन संदेशों को कैप्चर करने के लिए इस चरण‑दर‑चरण
  ट्यूटोरियल का पालन करें।
og_title: Aspose.Words में चेतावनियाँ कैसे प्राप्त करें – फ़ॉन्ट मॉनिटर करें
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Aspose.Words में चेतावनियाँ कैसे प्राप्त करें – C# में फ़ॉन्ट्स की निगरानी
url: /hi/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में चेतावनियाँ कैसे प्राप्त करें – C# में फ़ॉन्ट मॉनिटर करें

क्या आपने कभी सोचा है **चेतावनियाँ कैसे प्राप्त करें** जब एक Word दस्तावेज़ में ऐसे फ़ॉन्ट होते हैं जो आपके सिस्टम में स्थापित नहीं हैं? यह एक आम समस्या है—आपका ऐप चुपचाप गायब फ़ॉन्ट को बदल देता है, और आपको नहीं पता चलता कि क्या बदला। अच्छी बात यह है कि आप Aspose.Words की चेतावनी प्रणाली में हुक कर सकते हैं और **फ़ॉन्ट मॉनिटर** कर सकते हैं रीयल‑टाइम में।

इस ट्यूटोरियल में हम आपको दिखाएंगे कि उन फ़ॉन्ट‑सब्स्टिट्यूशन चेतावनियों को कैसे पकड़ें, यह क्यों महत्वपूर्ण है, और जानकारी मिलने के बाद आप क्या करें। कोई बाहरी दस्तावेज़ नहीं, सिर्फ एक पूर्ण, चलाने योग्य उदाहरण जिसे आप अभी Visual Studio में पेस्ट कर सकते हैं।

> **Pro tip:** यदि आप एक दस्तावेज़‑कन्वर्ज़न पाइपलाइन बना रहे हैं, तो शुरुआती चरण में गायब फ़ॉन्ट को लॉग करना आपको बाद में लेआउट की अनपेक्षित समस्याओं से बचाता है।

---

## आपको क्या चाहिए

- **Aspose.Words for .NET** (नवीनतम संस्करण; API v23.10 से बदल नहीं है)
- एक .NET विकास पर्यावरण (Visual Studio, Rider, या VS Code C# एक्सटेंशन के साथ)
- एक नमूना `.docx` जो ऐसे फ़ॉन्ट को संदर्भित करता है जो आपके सिस्टम में स्थापित नहीं है (उदाहरण के लिए **“NonExistentFont”**)

बस इतना ही—Aspose.Words के अलावा कोई अतिरिक्त NuGet पैकेज नहीं।

## चरण 1 – चेतावनी कलेक्टर सेट अप करें (हेडर में मुख्य कीवर्ड)

सबसे पहले आपको एक ऐसी जगह चाहिए जहाँ आप चेतावनियों को उनके उत्पन्न होते ही संग्रहीत कर सकें। Aspose.Words `LoadOptions` पर `WarningCallback` प्रॉपर्टी प्रदान करता है, जो इस उद्देश्य के लिए है।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**यह क्यों महत्वपूर्ण है:**  
जब लाइब्रेरी को कोई गायब फ़ॉन्ट मिलता है, तो वह अपवाद नहीं फेंकती; बल्कि एक `WarningInfo` ऑब्जेक्ट जारी करती है। कलेक्टर को जोड़कर आप हर सब्स्टिट्यूशन इवेंट को पूरी तरह देख सकते हैं, जिससे आप **फ़ॉन्ट मॉनिटर** कर सकते हैं बिना आपके कंसोल को असंबंधित संदेशों से भरने के।

## चरण 2 – चेतावनी‑सक्षम विकल्पों के साथ दस्तावेज़ लोड करें

अब हम वास्तव में फ़ाइल पढ़ते हैं। पिछले चरण में तैयार किए गए `LoadOptions` यह सुनिश्चित करते हैं कि सभी फ़ॉन्ट‑संबंधित चेतावनियाँ पकड़ी जाएँ।

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**आंतरिक रूप से क्या हो रहा है?**  
Aspose.Words Word फ़ाइल को पार्स करता है, फ़ॉन्ट्स को रिजॉल्व करता है, और जब भी वह अनुरोधित फ़ॉन्ट नहीं पा पाता, तो वह एक वैकल्पिक फ़ॉन्ट (आमतौर पर Arial) का उपयोग करता है। यह वैकल्पिक उपयोग `WarningType.FontSubstitution` चेतावनी उत्पन्न करता है, जो `warningCollector` में आती है।

## चरण 3 – संग्रहीत चेतावनियों की जाँच करें (मुख्य कीवर्ड फिर से प्रकट होता है)

दस्तावेज़ लोड होने के बाद, हम बस `warningCollector` पर इटरेट करते हैं और सभी फ़ॉन्ट‑सब्स्टिट्यूशन संदेश प्रिंट करते हैं।

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**अपेक्षित आउटपुट** (मान लेते हैं कि गायब फ़ॉन्ट *“FancyScript”* है):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

यदि दस्तावेज़ में कई अज्ञात फ़ॉन्ट हैं, तो आपको प्रत्येक सब्स्टिट्यूशन के लिए एक पंक्ति दिखेगी—लॉगिंग या अलर्टिंग के लिए उत्तम।

## चरण 4 – वैकल्पिक: चेतावनी जानकारी को लॉग या स्थायी बनाएं

प्रोडक्शन में आप संभवतः `Console.WriteLine` से अधिक चाहते हैं। यहाँ एक त्वरित उदाहरण है जो चेतावनियों को बाद के विश्लेषण के लिए JSON फ़ाइल में लिखता है।

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

अब आपके पास एक स्थायी रिकॉर्ड है जिसे आप मॉनिटरिंग डैशबोर्ड में फीड कर सकते हैं, या यहाँ तक कि गायब फ़ॉन्ट फ़ाइलों के लिए स्वचालित अनुरोध ट्रिगर कर सकते हैं।

## चरण 5 – परिणाम सत्यापित करें और साफ़ करें

प्रोग्राम चलाएँ। यदि आप सब्स्टिट्यूशन संदेश देखते हैं, तो आपने सफलतापूर्वक **चेतावनियाँ प्राप्त की हैं** और अब सक्रिय रूप से **फ़ॉन्ट मॉनिटर** कर रहे हैं। यदि कुछ नहीं दिखता, तो दोबारा जांचें कि परीक्षण दस्तावेज़ वास्तव में ऐसे फ़ॉन्ट को संदर्भित करता है जो मशीन पर स्थापित नहीं है।

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

शून्य की गिनती आमतौर पर इसका मतलब है या तो:

1. सभी फ़ॉन्ट हल हो गए (शायद फ़ॉन्ट *स्थानीय रूप से* स्थापित है), या
2. दस्तावेज़ में कोई ऐसा फ़ॉन्ट संदर्भ नहीं था जिसे सब्स्टिट्यूशन की आवश्यकता थी।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | कारण | समाधान |
|---------|----------------|-----|
| **कोई चेतावनी नहीं दिखती** | फ़ॉन्ट वास्तव में सिस्टम पर मौजूद है, या दस्तावेज़ केवल बिल्ट‑इन फ़ॉन्ट्स का उपयोग करता है। | स्रोत फ़ाइल में फ़ॉन्ट का नाम कुछ असंभव (जैसे `XYZ123`) रखकर पुनः प्रयास करें। |
| **बहुत अधिक चेतावनियाँ (शोर)** | आप लूप में कई दस्तावेज़ लोड कर रहे हैं बिना कलेक्टर को साफ़ किए। | प्रत्येक दस्तावेज़ के लिए `WarningInfoCollection` को पुनः बनाएं, या प्रोसेसिंग के बाद `warningCollector.Clear()` कॉल करें। |
| **प्रदर्शन पर प्रभाव** | डिस्क पर अत्यधिक लॉगिंग बैच प्रोसेसिंग को धीमा कर सकता है। | चेतावनियों को मेमोरी में बफ़र करें और एक साथ लिखें, या असिंक्रोनस फ़ाइल I/O का उपयोग करें। |
| **`using Aspose.Words.Loading;` गायब** | `LoadOptions` क्लास इस नेमस्पेस में स्थित है। | जैसा कि चरण 1 में दिखाया गया है, गायब `using` निर्देश जोड़ें। |

## समाधान का विस्तार – अन्य चेतावनी प्रकारों की निगरानी

जबकि फ़ॉन्ट सब्स्टिट्यूशन सबसे स्पष्ट है, Aspose.Words निम्नलिखित के लिए चेतावनियाँ उत्पन्न कर सकता है:

- **Deprecated features** (`WarningType.Deprecated`),
- **Potential data loss** (`WarningType.DataLoss`),
- **Unsupported file formats** (`WarningType.UnsupportedFileFormat`).

आप चरण 3 में फ़िल्टर को विस्तारित करके इन्हें भी पकड़ सकते हैं:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

इस तरह आप केवल **फ़ॉन्ट मॉनिटर कैसे करें** ही नहीं, बल्कि **चेतावनियाँ कैसे प्राप्त करें** भी किसी भी परिदृश्य के लिए कर सकते हैं जो आपका एप्लिकेशन सामना कर सकता है।

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**चलाएँ:** प्रोजेक्ट बनाएं, निष्पादित करें, और आप चेतावनियों को प्रिंट होते और सहेजे होते देखेंगे। यह Aspose.Words के साथ **चेतावनियाँ कैसे प्राप्त करें** और **फ़ॉन्ट मॉनिटर कैसे करें** का पूर्ण उत्तर है।

## निष्कर्ष

अब आप Aspose.Words से **चेतावनियाँ कैसे प्राप्त करें** जानते हैं, विशेष रूप से फ़ॉन्ट‑सब्स्टिट्यूशन परिदृश्यों के लिए, और आपने दस्तावेज़‑लोडिंग प्रक्रिया के दौरान **फ़ॉन्ट मॉनिटर कैसे करें** सीखा है। `WarningCallback` को जोड़कर, संग्रहीत `WarningInfo` ऑब्जेक्ट्स को इटरेट करके, और वैकल्पिक रूप से डेटा को स्थायी बनाकर, आप गायब‑फ़ॉन्ट इवेंट्स पर पूरी स्पष्टता प्राप्त करते हैं—जो किसी भी दस्तावेज़‑प्रोसेसिंग पाइपलाइन के लिए आवश्यक क्षमता है।

अगले कदम? चेतावनी फ़िल्टर को डेटा‑लॉस या डिप्रिकेटेड‑फ़ीचर चेतावनियों को शामिल करने के लिए विस्तारित करने का प्रयास करें, या JSON लॉग को Grafana जैसे मॉनिटरिंग डैशबोर्ड में एकीकृत करें। वही पैटर्न सभी चेतावनी प्रकारों पर काम करता है, इसलिए आप Aspose.Words द्वारा उत्पन्न किसी भी समस्या पर नज़र रखने के लिए पूरी तरह तैयार रहेंगे।

कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा उसी तरह रेंडर हों जैसा आप उम्मीद करते हैं!

---

<img src="font-warnings.png" alt="Aspose.Words में चेतावनियाँ कैसे प्राप्त करें" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}