---
category: general
date: 2026-05-23
description: Aspose.Words में फ़ॉन्ट प्रतिस्थापन चेतावनियों को पकड़ने के लिए चेतावनी
  कॉलबैक सेट करें। LoadOptions, FontSettings और IWarningCallback कार्यान्वयन सीखें।
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: hi
og_description: Aspose.Words में फ़ॉन्ट प्रतिस्थापन की निगरानी के लिए Aspose चेतावनी
  कॉलबैक सेट करें। यह ट्यूटोरियल LoadOptions, FontSettings, और चेतावनी हैंडलर कार्यान्वयन
  दिखाता है।
og_title: Aspose में चेतावनी कॉलबैक सेट करें – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: सेट वार्निंग कॉलबैक अस्पोज़ – वर्ड दस्तावेज़ लोडिंग के लिए पूर्ण गाइड
url: /hi/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – वर्ड दस्तावेज़ लोडिंग के लिए पूर्ण गाइड

क्या आप कभी सोचते हैं कि **set warning callback aspose** कैसे सेट करें ताकि आप फिर कभी फ़ॉन्ट‑सबस्टीट्यूशन अलर्ट न चूकें? आप अकेले नहीं हैं। जब कोई DOCX ऐसे फ़ॉन्ट का संदर्भ देता है जो स्थापित नहीं है, Aspose.Words चुपचाप उसे बदल देता है, और उचित कॉलबैक के बिना आप शायद नहीं जान पाएँगे कि कुछ बदला है।

इस ट्यूटोरियल में हम एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से दिखाएँगे कि इन चेतावनियों को कैसे पकड़ें। अंत तक आप **Aspose.Words LoadOptions**, **FontSettings** को कैसे कॉन्फ़िगर करें, और **IWarningCallback** को लागू करना क्यों सबसे साफ़ तरीका है, समझ जाएंगे। कोई फालतू बातें नहीं—सिर्फ वह कोड जो आप आज ही .NET प्रोजेक्ट में डाल सकते हैं।

## What You’ll Learn

- कैसे **set warning callback aspose** को `LoadOptions` इंस्टेंस पर सेट करें।  
- दस्तावेज़ खोलते समय **Aspose.Words LoadOptions** की भूमिका।  
- `FontSettings` के साथ **Aspose फ़ॉन्ट सबस्टीट्यूशन** हैंडलिंग को कॉन्फ़िगर करना।  
- फ़ॉन्ट समस्याओं को लॉग करने के लिए कस्टम **IWarningCallback** इम्प्लीमेंटेशन लिखना।  
- **Aspose document loading** की सर्वोत्तम प्रैक्टिसेज़ के साथ दस्तावेज़ को सुरक्षित रूप से लोड करना।

### Prerequisites

- .NET 6.0 या बाद का (कोड .NET Framework 4.5+ पर भी काम करता है)।  
- एक वैध Aspose.Words for .NET लाइसेंस या ट्रायल की।  
- Visual Studio, Rider, या कोई भी C# एडिटर जो आप पसंद करते हैं।  
- एक सैंपल DOCX (`fontTest.docx`) जिसमें मिसिंग फ़ॉन्ट हो (वैकल्पिक लेकिन उपयोगी)।

> **Pro tip:** अगर आपके पास मिसिंग‑फ़ॉन्ट DOCX नहीं है, तो दस्तावेज़ की स्टाइल में फ़ॉन्ट का नाम बदल दें और चेतावनी को ट्रिगर होते देखें।

---

## How to set warning callback aspose for document loading

नीचे पूरा, स्व-निहित प्रोग्राम दिया गया है। इसे `Program.cs` के रूप में सेव करें, NuGet पैकेज रिस्टोर करें, और चलाएँ। कंसोल में Aspose.Words द्वारा फ़ाइल लोड करते समय उत्पन्न हर फ़ॉन्ट‑सबस्टीट्यूशन चेतावनी प्रिंट होगी।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Expected console output

यदि `fontTest.docx` ऐसा फ़ॉन्ट संदर्भित करता है जो स्थापित नहीं है, तो आपको कुछ इस तरह दिखेगा:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

यदि सभी फ़ॉन्ट मौजूद हैं, तो केवल एक ही लाइन प्रिंट होगी *Document loaded successfully*—कोई चेतावनी नहीं, कोई शोर नहीं।

![set warning callback aspose उदाहरण](image.png "set warning callback aspose उदाहरण")

---

## Understanding LoadOptions in Aspose.Words

`LoadOptions` वह द्वार है जिसके द्वारा आप **aspose document loading** को हर तरह से ट्यून कर सकते हैं। यह आपको:

1. **कस्टम `FontSettings` निर्दिष्ट करने** की अनुमति देता है – उपयोगी जब आपका एप्लिकेशन अपने फ़ॉन्ट स्वयं प्रदान करता है।  
2. **एक चेतावनी कॉलबैक संलग्न करने** – ठीक वही जो हमने फ़ॉन्ट सबस्टीट्यूशन पकड़ने के लिए किया।  
3. दस्तावेज़ फ़ॉर्मेट डिटेक्शन, पासवर्ड हैंडलिंग, और अधिक को नियंत्रित करने की सुविधा देता है।

चूँकि `LoadOptions` को `Document` कंस्ट्रक्टर में पास किया जाता है, सेटिंग्स **एक बार** फ़ाइल के पार्स होते ही लागू हो जाती हैं। इसलिए हम गारंटी दे सकते हैं कि हमारा चेतावनी हैंडलर हर सबस्टीट्यूशन को देखेगा, इससे पहले कि दस्तावेज़ मेमोरी में बना हो।

### When to use a custom LoadOptions

- कई फ़ाइलों की **बैच प्रोसेसिंग** जहाँ आप एक समान लॉगिंग स्ट्रैटेजी चाहते हैं।  
- **क्लाउड सेवाएँ** जिन्हें कॉलर को मिसिंग फ़ॉन्ट की रिपोर्ट करनी होती है।  
- **टेस्टिंग पाइपलाइन** जहाँ दस्तावेज़ को कॉर्पोरेट फ़ॉन्ट पॉलिसी के अनुरूप होना चाहिए।

---

## Configuring FontSettings for Aspose fonts substitution

`FontSettings` ऑब्जेक्ट यह नियंत्रित करता है कि Aspose.Words फ़ॉन्ट कैसे रिजॉल्व करता है। डिफ़ॉल्ट रूप से यह सिस्टम के फ़ॉन्ट फ़ोल्डर खोजता है, फिर बिल्ट‑इन सबस्टीट्यूट्स पर फॉल्बैक करता है। आप इस व्यवहार को फ़ाइन‑ट्यून कर सकते हैं:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

ये लाइनें बेसिक “set warning callback aspose” परिदृश्य के लिए वैकल्पिक हैं, लेकिन यह दर्शाती हैं कि सही फ़ॉन्ट प्रदान करके आप सबस्टीट्यूशन चेतावनियों की संख्या **कम** कर सकते हैं।

---

## Implementing IWarningCallback for font substitution warnings

`IWarningCallback` इंटरफ़ेस बहुत छोटा है—सिर्फ एक `Warning` मेथड। फिर भी यह आपको चेतावनियों को संभालने पर **पूरा नियंत्रण** देता है:

- कंसोल के बजाय **फ़ाइल में लॉग** करें।  
- बाद में विश्लेषण के लिए चेतावनियों को एक लिस्ट में **एकत्रित** करें।  
- गंभीर चेतावनियों (जैसे आवश्यक फ़ॉन्ट गायब होना) के लिए **एक्सेप्शन थ्रो** करें।

यहाँ एक त्वरित उदाहरण है जो चेतावनियों को `List<string>` में स्टोर करता है:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

लोडिंग के बाद आप `handler.Messages` को देख सकते हैं और तय कर सकते हैं कि प्रोसेसिंग को रोकना है या नहीं।

---

## Loading a document with custom warning handling (full workflow)

सब कुछ एक साथ मिलाकर, अंतिम पैटर्न जो आप संभवतः बार‑बार उपयोग करेंगे, इस प्रकार दिखता है:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

यह स्निपेट **aspose document loading** फ्लो को दर्शाता है जिसे आप प्रोडक्शन में उपयोग करेंगे: कॉन्फ़िगर करें, लोड करें, फिर प्रतिक्रिया दें। यह पैटर्न एक फ़ाइल प्रोसेस करने या हजारों फ़ाइलों पर लूप करने दोनों में सहजता से स्केल करता है।

---

## Common Questions & Edge Cases

**यदि दस्तावेज़ पासवर्ड‑प्रोटेक्टेड है तो क्या होगा?**  
`LoadOptions` इनिशियलाइज़र में `Password = "secret"` जोड़ें। फ़ाइल डिक्रिप्ट होने के बाद भी कॉलबैक काम करेगा।

**क्या कॉलबैक अन्य प्रकार की चेतावनियों के लिए भी फायर होगा?**  
हाँ—`WarningInfo.Type` `DocumentStructure`, `UnsupportedFileFormat` आदि हो सकता है। हमारे उदाहरण में हमने `FontSubstitution` के लिए फ़िल्टर किया है, लेकिन `if` चेक हटाकर आप सभी चेतावनियों को लॉग कर सकते हैं।

**क्या इससे प्रदर्शन पर असर पड़ेगा?**  
बहुत कम। कॉलबैक केवल तब बुलाया जाता है जब चेतावनी उत्पन्न होती है, जो सामान्य पार्सिंग स्टेप्स की तुलना में बहुत कम बार होता है।

**क्या मैं फ़ॉन्ट सबस्टीट्यूशन को पूरी तरह से डिसेबल कर सकता हूँ?**  
आप `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` सेट कर सकते हैं, लेकिन तब Aspose.Words मिसिंग फ़ॉन्ट के लिए एक्सेप्शन थ्रो करेगा, स्वैप करने के बजाय।

---

## Conclusion

अब आप बिल्कुल जानते हैं कि **set warning callback aspose** को कैसे सेट करें ताकि **Aspose.Words LoadOptions** प्रोसेसिंग के दौरान फ़ॉन्ट‑सबस्टीट्यूशन इवेंट्स को मॉनिटर किया जा सके। `FontSettings` को कॉन्फ़िगर करके, हल्का `IWarningCallback` इम्प्लीमेंट करके, और उन विकल्पों के साथ दस्तावेज़ लोड करके, आप Aspose के पीछे होने वाले किसी भी फ़ॉन्ट परिवर्तन की पूरी दृश्यता प्राप्त कर लेते हैं।

अब आप आगे कर सकते हैं:

- चेतावनी हैंडलर को एक सेंट्रल लॉगिंग सर्विस में लिखना।  
- कॉलबैक को कस्टम फ़ॉन्ट‑फ़ॉलबैक स्ट्रैटेजी के साथ जोड़ना।  
- क्लाउड API बनाते समय इस पैटर्न को उपयोग करना, जो क्लाइंट‑अपलोडेड दस्तावेज़ों को वैलिडेट करता है।

अपने स्वयं के DOCX फ़ाइलों के साथ इसे आज़माएँ, `FontSettings` को ट्यून करें, और कंसोल को देखें कि कौन‑से फ़ॉन्ट बदले गए। हैप्पी कोडिंग, और आपके दस्तावेज़ हमेशा इच्छित रूप में रेंडर हों!

## Related Tutorials

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}