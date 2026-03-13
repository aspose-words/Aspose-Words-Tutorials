---
category: general
date: 2026-03-13
description: Aspose.Words के साथ दस्तावेज़ लोड करते समय चेतावनियों को कैसे पकड़ें,
  साथ ही गायब फ़ॉन्ट्स को संभालने और कस्टम फ़ॉन्ट सेटिंग्स सेट करने के टिप्स। एक पूर्ण
  C# समाधान सीखें।
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: hi
og_description: Aspose.Words के साथ Word फ़ाइलें लोड करते समय चेतावनियों को कैसे पकड़ें,
  साथ ही गायब फ़ॉन्ट्स को संभालने और कस्टम फ़ॉन्ट सेटिंग्स सेट करने के व्यावहारिक
  तरीके।
og_title: Aspose.Words में चेतावनियों को कैसे कैप्चर करें – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words में चेतावनियों को कैसे कैप्चर करें – पूर्ण गाइड
url: /hi/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में चेतावनियों को कैप्चर कैसे करें – पूर्ण गाइड

क्या आपने कभी सोचा है **कैसे चेतावनियों को कैप्चर करें** जब Aspose.Words कोई दस्तावेज़ लोड करता है? कई वास्तविक‑दुनिया प्रोजेक्ट्स में आपको फ़ॉन्ट‑सब्स्टिट्यूशन अलर्ट, डिप्रिकेटेड‑फ़ीचर नोट्स, या यहाँ तक कि सुरक्षा‑संबंधी संदेश भी मिल सकते हैं। इन्हें अनदेखा करना ऐसे है जैसे टूटे हुए विंडशील्ड के साथ गाड़ी चलाना—आप गंतव्य तक पहुँच सकते हैं, लेकिन आपको कभी पता नहीं चलेगा कि कब कुछ बिगड़ने वाला है।

अच्छी खबर यह है कि Aspose.Words आपको एक साफ़, कॉलबैक‑आधारित तरीका देता है जिससे आप इन संदेशों को इंटरसेप्ट कर सकते हैं। इस ट्यूटोरियल में हम एक **पूर्ण C# उदाहरण** के माध्यम से चलेंगे जो न केवल चेतावनियों को कैप्चर करता है बल्कि आपको **गुम फ़ॉन्ट्स को हैंडल करना** और **कस्टम फ़ॉन्ट सेटिंग्स सेट करना** भी दिखाता है ताकि आपके दस्तावेज़ ठीक वैसा ही रेंडर हों जैसा आप चाहते हैं।

---

## आप क्या सीखेंगे

- `LoadOptions` को कॉन्फ़िगर करके एक कस्टम `FontSettings` ऑब्जेक्ट प्लग‑इन करें।  
- एक चेतावनी कॉलबैक रजिस्टर करें जो `FontSubstitution` इवेंट्स को फ़िल्टर करता है।  
- चेतावनी विवरण को कंसोल (या किसी भी लॉगर) में आउटपुट करें।  
- समाधान को विस्तारित करके विभिन्न प्लेटफ़ॉर्म पर गुम फ़ॉन्ट्स को सहजता से हैंडल करें।  

इस गाइड के अंत तक आपके पास एक तैयार‑से‑चलाने वाला स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं, साथ ही कुछ व्यावहारिक टिप्स भी मिलेंगी जो सामान्य समस्याओं से बचाएंगी।

---

## पूर्वापेक्षाएँ

| आवश्यकता | क्यों महत्वपूर्ण है |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 या बाद का) | वह API (`LoadOptions`, `IWarningCallback`) यहाँ स्थित है। |
| **.NET 6+** (या .NET Framework 4.7.2+) | आधुनिक भाषा सुविधाएँ कोड को साफ़ बनाती हैं। |
| **एक सैंपल DOCX** (नाम `input.docx`) जिसे ज्ञात फ़ोल्डर में रखें | हमें लोड करने और चेतावनी ट्रिगर करने के लिए कुछ चाहिए। |
| **एक कंसोल या लॉगिंग फ्रेमवर्क** (वैकल्पिक) | कैप्चर की गई चेतावनियों को कार्रवाई में देखने के लिए। |

Aspose.Words के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

---

## चरण 1: कस्टम फ़ॉन्ट सेटिंग्स सेट करें  

डॉक्यूमेंट लोड करने से पहले आप Aspose.Words को बता सकते हैं कि फ़ॉन्ट्स कहाँ खोजे जाएँ। यही **कस्टम फ़ॉन्ट सेटिंग्स सेट करने** का हिस्सा है।

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**यह क्यों महत्वपूर्ण है:**  
यदि कोई DOCX ऐसे फ़ॉन्ट का संदर्भ देता है जो मशीन पर इंस्टॉल नहीं है, तो Aspose.Words बिना किसी चेतावनी के एक फ़ॉलबैक फ़ॉन्ट का उपयोग करेगा *जब तक* आपने आवश्यक फ़ॉन्ट्स वाले फ़ोल्डर को कॉन्फ़िगर नहीं किया हो। एक कस्टम फ़ोल्डर सेट करके आप शुरुआती चरण में ही “फ़ॉन्ट‑सब्स्टिट्यूशन” चेतावनियों की संभावना कम कर देते हैं।

> **प्रो टिप:** Linux पर आपको `fonts-dejavu-core` पैकेज या कोई भी TrueType कलेक्शन जोड़ना पड़ सकता है जिस पर आपके दस्तावेज़ निर्भर होते हैं।

---

## चरण 2: एक चेतावनी कॉलबैक रजिस्टर करें  

Aspose.Words `IWarningCallback` को इम्प्लीमेंट करता है। हम एक छोटा हैंडलर बनाएँगे जो केवल उन चेतावनियों को प्रिंट करेगा जो हमें चाहिए: गुम या सब्स्टिट्यूटेड फ़ॉन्ट्स।

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**यह क्यों महत्वपूर्ण है:**  
अब **गुम फ़ॉन्ट्स को हैंडल करने** का परिदृश्य आपके सामने स्पष्ट है। यह अनुमान लगाने के बजाय कि कौन सा फ़ॉन्ट बदला गया, आपको “Font 'Calibri' was substituted with 'Arial'” जैसी स्पष्ट विवरण मिलती है। यह जनरेटेड PDFs या प्रिंटेड रिपोर्ट्स में लेआउट समस्याओं को डिबग करने के लिए अमूल्य है।

---

## चरण 3: कॉन्फ़िगर किए गए विकल्पों के साथ डॉक्यूमेंट लोड करें  

अब हम अंततः `LoadOptions` का उपयोग करके डॉक्यूमेंट को मेमोरी में लाते हैं, जिसे हमने अभी तैयार किया है।

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

यदि स्रोत फ़ाइल में ऐसा फ़ॉन्ट है जो `C:\MyFonts` में मौजूद नहीं है, तो आपको लगभग इस प्रकार का आउटपुट मिलेगा:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

यह लाइन वही **कैसे चेतावनियों को कैप्चर करें** परिणाम है जिसकी आप तलाश में थे।

---

## चरण 4: पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

नीचे पूरा प्रोग्राम दिया गया है, जिसे आप सीधे कंपाइल कर सकते हैं। इसे एक नए कंसोल प्रोजेक्ट में पेस्ट करें और चलाएँ—सिर्फ यह सुनिश्चित करें कि पाथ्स आपके मशीन पर वास्तविक लोकेशन की ओर इशारा कर रहे हों।

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**अपेक्षित आउटपुट:**  

- यदि सभी फ़ॉन्ट उपलब्ध हैं:  
  `Document processed. Check console for any warning messages.`  

- यदि कोई फ़ॉन्ट गुम है:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## चरण 5: सामान्य वैरिएशन और एज केस

| स्थिति | क्या समायोजित करें |
|-----------|----------------|
| **एकाधिक फ़ॉन्ट फ़ोल्डर** | प्रत्येक अतिरिक्त लोकेशन के लिए `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` कॉल करें। |
| **सभी चेतावनियों को दबाएँ** | `Warn` इम्प्लीमेंट करें लेकिन बॉडी खाली छोड़ें, या `loadOptions.WarningCallback = null;` सेट करें। |
| **अन्य चेतावनी प्रकार कैप्चर करें** | `info.WarningType` को `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent` आदि से तुलना करें। |
| **Linux/macOS पर चलाना** | सुनिश्चित करें कि फ़ॉन्ट फ़ोल्डर में Linux‑संगत `.ttf`/`.otf` फ़ाइलें हों; आपको `libfontconfig` इंस्टॉल करना पड़ सकता है। |
| **बड़े दस्तावेज़** | मेमोरी प्रेशर कम करने के लिए डॉक्यूमेंट को स्ट्रीम करने पर विचार करें (`LoadOptions.LoadFormat = LoadFormat.Docx;`)। |

इन परिदृश्यों की पूर्वानुमान करके आप डेवलपमेंट बॉक्स से CI पाइपलाइन या क्लाउड VM में स्थानांतरित होते समय आश्चर्यजनक समस्याओं से बचेंगे।

---

## चरण 6: विज़ुअल कन्फ़र्मेशन (वैकल्पिक)

यदि आप एक त्वरित विज़ुअल संकेत पसंद करते हैं, तो आप कैप्चर की गई चेतावनियों को एक छोटे HTML रिपोर्ट में डंप कर सकते हैं। यहाँ एक छोटा स्निपेट है जो संदेशों को `warnings.html` में लिखता है:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

डॉक्यूमेंट लोड करने के बाद, `handler.WriteReport(@"C:\Docs\warnings.html");` कॉल करें और ब्राउज़र में खोलें। नीचे की छवि दिखाती है कि रिपोर्ट कैसी दिख सकती है:

![How to capture warnings screenshot](/images/capture-warnings.png)

*Alt text:* **how to capture warnings** – कंसोल आउटपुट और HTML रिपोर्ट का स्क्रीनशॉट।

---

## निष्कर्ष  

हमने **Aspose.Words में चेतावनियों को कैप्चर करने** का तरीका कवर किया, **गुम फ़ॉन्ट्स को हैंडल करने** का भरोसेमंद तरीका दिखाया, और **कस्टम फ़ॉन्ट सेटिंग्स सेट करने** को प्रदर्शित किया ताकि रेंडरिंग पूर्वानुमानित हो। पूर्ण उदाहरण किसी भी .NET समाधान में डालने के लिए तैयार है, और मॉड्यूलर `FontWarningHandler` को आपके लॉगिंग या टेलीमेट्री स्ट्रैटेजी के अनुसार विस्तारित किया जा सकता है।

अगला कदम? `Console.WriteLine` कॉल को Serilog जैसे स्ट्रक्चर्ड लॉगर से बदलें, या चेतावनियों को Application Insights में पुश करके रीयल‑टाइम मॉनिटरिंग प्राप्त करें। यदि आपको डॉक्यूमेंट लोड होने के बाद उसकी सामग्री की जाँच करनी है तो `DocumentVisitor` पैटर्न भी एक्सप्लोर कर सकते हैं।

क्या आपके पास अन्य चेतावनी प्रकारों या फ़ॉन्ट‑एम्बेडिंग स्ट्रैटेजी के बारे में प्रश्न हैं? नीचे कमेंट करें—हैप्पी कोडिंग!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}