---
category: general
date: 2026-05-04
description: Aspose फ़ॉन्ट प्रतिस्थापन का उपयोग करके जब आप वर्ड दस्तावेज़ लोड करते
  हैं तो गायब फ़ॉन्ट्स का पता लगाना और गायब फ़ॉन्ट विवरण प्राप्त करना सीखें—स्टेप
  बाय स्टेप गाइड।
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: hi
og_description: Aspose फ़ॉन्ट प्रतिस्थापन में निपुण बनें ताकि Word दस्तावेज़ लोड करते
  समय गायब फ़ॉन्ट का पता लगाया जा सके और पूर्ण C# कोड के साथ गायब फ़ॉन्ट जानकारी प्राप्त
  की जा सके।
og_title: Aspose फ़ॉन्ट प्रतिस्थापन – वर्ड दस्तावेज़ों में लापता फ़ॉन्ट का पता लगाएँ
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose फ़ॉन्ट प्रतिस्थापन: वर्ड दस्तावेज़ों में गायब फ़ॉन्ट्स का पता लगाएँ'
url: /hi/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose फ़ॉन्ट प्रतिस्थापन – Word दस्तावेज़ों में लापता फ़ॉन्ट का पता लगाएँ

क्या आपने कभी सोचा है कि Word दस्तावेज़ दूसरे कंप्यूटर पर क्यों गलत दिखता है? अक्सर इसका कारण लापता फ़ॉन्ट होता है, और **Aspose फ़ॉन्ट प्रतिस्थापन** वह टूल है जो आपको ये गैप्स दृश्य आपदा बनने से पहले ही दिखा देता है। इस ट्यूटोरियल में हम **लापता फ़ॉन्ट का पता लगाने** के लिए दिखाएंगे कि **Word दस्तावेज़ को लोड** करते ही कैसे **लापता फ़ॉन्ट** की जानकारी प्राप्त की जाए ताकि आप उसे ठीक या बदल सकें।

हम चेतावनी कॉलबैक सेट करने से लेकर लापता फ़ॉन्ट की साफ़ सूची निकालने तक सब कुछ कवर करेंगे। अंत तक, आपके पास एक तैयार‑चलाने‑योग्य C# स्निपेट होगा जो आपको ठीक‑ठीक बताता है कि कौन‑से फ़ॉन्ट नहीं मिले, और आप समझेंगे कि यह दस्तावेज़ की सटीकता के लिए क्यों महत्वपूर्ण है।

---

## पूर्वापेक्षाएँ – शुरू करने से पहले आपको क्या चाहिए

- **Aspose.Words for .NET** (v23.12 या बाद का संस्करण सुझाया गया)।  
- एक .NET विकास वातावरण (Visual Studio, Rider, या `dotnet` CLI)।  
- एक नमूना DOCX जो जानबूझकर ऐसे फ़ॉन्ट का उपयोग करता है जो आपके सिस्टम में नहीं है—इसे `DocumentWithMissingFont.docx` कहें।  
- बुनियादी C# ज्ञान—कुछ भी जटिल नहीं, बस एक कंसोल ऐप चलाने की क्षमता।

यदि इनमें से कोई भी चीज़ अपरिचित लगती है, तो रुकें और NuGet पैकेज इंस्टॉल करें:

```bash
dotnet add package Aspose.Words
```

बस इतना ही। कोई अतिरिक्त फ़ॉन्ट नहीं, कोई बाहरी सेवा नहीं।

---

## चरण 1: Word दस्तावेज़ लोड करें (और फ़ॉन्ट जांच ट्रिगर करें)

सबसे पहला काम है **Word दस्तावेज़ को लोड करना**। Aspose.Words फ़ाइल को पार्स करता है और यदि वह संदर्भित फ़ॉन्ट नहीं ढूँढ़ पाता, तो वह *FontSubstitution* चेतावनी को कतार में रख देता है। यहाँ वह कोड है जो लोडिंग करता है:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **यह क्यों महत्वपूर्ण है:** दस्तावेज़ को जल्दी लोड करने से Aspose को हर टेक्स्ट रन, स्टाइल, और एम्बेडेड ऑब्जेक्ट को स्कैन करने का मौका मिलता है। यदि सिस्टम या कस्टम फ़ॉन्ट फ़ोल्डर में फ़ॉन्ट नहीं मिलता, तो बाद में आपको चेतावनी मिलेगी।

---

## चरण 2: चेतावनी कॉलबैक संलग्न करें ताकि प्रतिस्थापन इवेंट्स को कैप्चर किया जा सके

Aspose.Words एक कॉलबैक मैकेनिज़्म का उपयोग करता है ताकि आपको लापता फ़ॉन्ट जैसी समस्याओं के बारे में सूचित किया जा सके। `doc.WarningCallback` को `IWarningCallback` की एक इम्प्लीमेंटेशन असाइन करके आप प्रत्येक चेतावनी को वास्तविक‑समय में पकड़ सकते हैं।

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **प्रो टिप:** आप कई कॉलबैक (जैसे लॉगिंग, UI अपडेट) को कॉम्पोज़िट पैटर्न से रैप करके संलग्न कर सकते हैं, लेकिन इस ट्यूटोरियल के लिए एक ही कॉलबैक चीज़ों को स्पष्ट रखता है।

---

## चरण 3: फ़ॉन्ट प्रतिस्थापन चेतावनी कॉलबैक लागू करें

अब हम वह क्लास परिभाषित करते हैं जो वास्तविक कार्य करता है। कॉलबैक एक `WarningInfo` ऑब्जेक्ट प्राप्त करता है; हम `WarningType.FontSubstitution` के लिए फ़िल्टर करते हैं और विवरण को बाद में उपयोग के लिए संग्रहित करते हैं।

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **क्या हो रहा है:** जब Aspose को लापता फ़ॉन्ट मिलता है, तो वह “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” जैसी चेतावनी बनाता है। हमारा कॉलबैक वह लाइन प्रिंट करता है और उसे सहेजता है।

---

## चरण 4: दस्तावेज़ प्रोसेस करें (वैकल्पिक) और लापता फ़ॉन्ट एकत्र करें

यदि आपको केवल **लापता फ़ॉन्ट का पता लगाना** है, तो लोडिंग चरण पर्याप्त है—चेतावनियाँ स्वतः फ़ायर हो जाती हैं। हालांकि, कई डेवलपर्स को कुछ ऑपरेशन (जैसे सेविंग, कनवर्टिंग) करने के बाद **लापता फ़ॉन्ट** की जानकारी चाहिए होती है। नीचे हम एक छोटा ऑपरेशन—PDF में सेविंग—को मजबूर करते हैं ताकि सभी चेतावनियाँ उत्पन्न हों, फिर हम संग्रहीत संदेश निकालते हैं।

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **अपेक्षित कंसोल आउटपुट** (उदाहरण):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

ध्यान दें कि प्रत्येक पंक्ति स्पष्ट रूप से मूल फ़ॉन्ट और Aspose द्वारा चुने गए फॉलबैक को बताती है। यही **aspose फ़ॉन्ट प्रतिस्थापन** रिपोर्टिंग का मूल है।

---

## चरण 5: उन्नत – प्रतिस्थापन कम करने के लिए कस्टम फ़ॉन्ट स्रोतों का उपयोग

कभी‑कभी आपके पास लापता फ़ॉन्ट होते हैं, बस डिफ़ॉल्ट सिस्टम फ़ोल्डर में नहीं होते। Aspose.Words आपको `FontSettings` के माध्यम से एक कस्टम डायरेक्टरी इंगित करने की अनुमति देता है। इस चरण को जोड़ने से प्रतिस्थापन चेतावनियों की संख्या में काफी कमी आ सकती है।

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **यह क्यों जोड़ें?** यदि आप दस्तावेज़ों को कई मशीनों पर वितरित कर रहे हैं, तो आवश्यक फ़ॉन्ट को एक ज्ञात फ़ोल्डर में बंडल करने से हर जगह समान दृश्य रूप मिलता है। यह आपके **detect missing fonts** रूटीन को भी अधिक सटीक बनाता है क्योंकि Aspose पहले उस फ़ोल्डर को चेक करता है, फिर फॉलबैक पर जाता है।

---

## पूर्ण कार्यशील उदाहरण

सब कुछ एक साथ मिलाकर, यहाँ एक एक‑लाइन‑कॉपी‑पेस्ट‑तैयार कंसोल प्रोग्राम है। इसे `Program.cs` के रूप में सेव करें और `dotnet run` से चलाएँ।

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**आपको क्या दिखना चाहिए:** यदि स्रोत DOCX में ऐसे फ़ॉन्ट हैं जो आपके पास नहीं हैं, तो कंसोल प्रत्येक प्रतिस्थापन लाइन के बाद एक संक्षिप्त सारांश प्रिंट करेगा। यदि सभी फ़ॉन्ट मौजूद हैं, तो आपको “No missing fonts were detected.” संदेश मिलेगा।

---

## सामान्य समस्याएँ एवं उनके समाधान

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| **कोई चेतावनी नहीं दिखती** | दस्तावेज़ केवल सिस्टम फ़ॉन्ट उपयोग करता है, या आपने पहले ही कस्टम फ़ोल्डर जोड़ दिया है जिसमें लापता फ़ॉन्ट हैं। | सुनिश्चित करें कि DOCX वास्तव में किसी अनुपलब्ध फ़ॉन्ट का संदर्भ देता है। आप Word में एक पैराग्राफ को दुर्लभ फ़ॉन्ट (जैसे “Papyrus”) में बदल सकते हैं। |
| **डुप्लिकेट संदेश** | वही फ़ॉन्ट कई रन में उपयोग हुआ है, जिससे कई चेतावनियाँ आती हैं। | यदि आपको केवल यूनिक सेट चाहिए तो `Distinct()` से डुप्लिकेशन हटाएँ। |
| **बड़े दस्तावेज़ों पर प्रदर्शन गिरावट** | प्रत्येक चेतावनी UI थ्रेड पर प्रोसेस होती है। | लोडिंग को बैकग्राउंड टास्क में चलाएँ या पोस्ट‑प्रोसेसिंग के लिए `Parallel.ForEach` का उपयोग करें। |
| **गलत फॉलबैक फ़ॉन्ट** | Aspose का डिफ़ॉल्ट फॉलबैक आपके ब्रांडिंग से मेल नहीं खा सकता। | `FontSettings.SubstitutionSettings.DefaultFontName` को अपनी पसंदीदा फ़ॉन्ट (जैसे “Calibri”) पर सेट करें। |

---

## समाधान का विस्तार – लापता फ़ॉन्ट को JSON में निर्यात करना

यदि आप एक वेब सर्विस बना रहे हैं जिसे क्लाइंट को लापता फ़ॉन्ट की रिपोर्ट करनी है, तो सूची को सीरियलाइज़ करना बहुत आसान है:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

अब आपका API एक साफ़ JSON पेलोड वापस कर सकता है जिसे दूसरा सिस्टम आसानी से उपयोग कर सके।

---

## निष्कर्ष

इस गाइड में हमने **Aspose फ़ॉन्ट प्रतिस्थापन** को शुरुआत से अंत तक दिखाया: Word दस्तावेज़ लोड करना, चेतावनी कॉलबैक संलग्न करना, प्रत्येक *detect missing fonts* इवेंट को कैप्चर करना, और अंत में **retrieve missing font** जानकारी को रिपोर्ट या सुधार के लिए निकालना। वैकल्पिक कस्टम फ़ॉन्ट फ़ोल्डर जोड़ने से प्रतिस्थापनों की सूची घटती है, और कुछ अतिरिक्त पंक्तियों से आप परिणामों को JSON में भी एक्सपोर्ट कर सकते हैं।

याद रखें, आपके दस्तावेज़ों की दृश्य अखंडता उनके उपयोग किए गए फ़ॉन्ट पर निर्भर करती है। यहाँ दिखाए गए तकनीक से आप कभी भी अनपेक्षित फॉलबैक से आश्चर्य नहीं करेंगे।  

अगला कदम उठाने के लिए तैयार हैं? इस लॉजिक को बड़े दस्तावेज़‑प्रोसेसिंग पाइपलाइन में इंटीग्रेट करें, या Aspose.Words की अन्य सुविधाओं जैसे फ़ॉन्ट एम्बेडिंग (`doc.FontSettings.EmbeddedFonts`) को एक्सप्लोर करें। संभावनाएँ अनंत हैं, और आपके उपयोगकर्ता आपके परिष्कृत आउटपुट की सराहना करेंगे।

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}