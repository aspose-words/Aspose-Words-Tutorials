---
category: general
date: 2026-06-08
description: Aspose.Words में LoadOptions का उपयोग करके दस्तावेज़ आयात के दौरान गायब
  फ़ॉन्ट्स का पता लगाना सीखें। कोड, स्पष्टीकरण और सर्वोत्तम प्रथाओं के साथ चरण-दर-चरण
  मार्गदर्शिका।
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: hi
og_description: Aspose.Words में LoadOptions का उपयोग कैसे करें और दस्तावेज़ लोड करते
  समय गायब फ़ॉन्ट्स का पता कैसे लगाएँ। कोड और व्यावहारिक सुझावों के साथ पूर्ण मार्गदर्शिका।
og_title: लॉडऑप्शन्स का उपयोग करके गायब फ़ॉन्ट्स का पता कैसे लगाएँ
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: LoadOptions का उपयोग करके गायब फ़ॉन्ट्स का पता कैसे लगाएँ
url: /hi/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LoadOptions का उपयोग करके लापता फ़ॉन्ट्स का पता कैसे लगाएँ

क्या आपने कभी सोचा है कि Aspose.Words के साथ Word दस्तावेज़ लोड करते समय **LoadOptions का उपयोग कैसे करें**? इस ट्यूटोरियल में हम आपको बिल्कुल **LoadOptions का उपयोग कैसे करें** यह दिखाएंगे कि **लापता फ़ॉन्ट्स का पता कैसे लगाएँ** और उन्हें सहजता से संभालें। चाहे आप दस्तावेज़ रूपांतरण सेवा बना रहे हों या रिपोर्टिंग इंजन, लापता फ़ॉन्ट्स लेआउट में आश्चर्य पैदा कर सकते हैं, इसलिए उन्हें जल्दी पकड़ना आवश्यक है।

हम हर चरण को विस्तार से बताएँगे—warning callback को जोड़ने से लेकर परिणामों की व्याख्या तक—ताकि आप किसी भी .NET प्रोजेक्ट में डाल सकने वाला पूर्ण कार्यशील C# उदाहरण प्राप्त कर सकें। कोई बाहरी दस्तावेज़ नहीं, केवल एक स्व-समाहित समाधान। अंत तक आप जानेंगे कि warning सिस्टम क्यों मौजूद है, इसे कैसे सक्षम करें, और callback फायर होने पर क्या करें।

## पूर्वापेक्षाएँ

- **Aspose.Words for .NET** (कोई भी हालिया संस्करण; हम जिस API का उपयोग करते हैं वह 2022 से स्थिर है)।
- एक .NET विकास वातावरण (Visual Studio, Rider, या C# एक्सटेंशन के साथ VS Code)।
- एक नमूना Word फ़ाइल (`input.docx`) जो ऐसे फ़ॉन्ट को संदर्भित करती है जो आपके मशीन पर स्थापित नहीं है।

बस इतना ही—Aspose.Words के अलावा कोई अतिरिक्त NuGet पैकेज नहीं।

## Aspose.Words के साथ LoadOptions का उपयोग कैसे करें

**LoadOptions** क्लास दस्तावेज़ को पढ़ने के तरीके को अनुकूलित करने का द्वार है। इसमें एक warning callback जोड़कर आप Aspose.Words के फ़ाइल को पार्स करते ही **लापता फ़ॉन्ट्स का पता लगा** सकते हैं। चलिए इसे विस्तार से देखते हैं।

### चरण 1: एक Warning Handler बनाएँ

Aspose.Words `IWarningCallback` इंटरफ़ेस का उपयोग करके आपको गैर‑महत्वपूर्ण समस्याओं, जैसे फ़ॉन्ट प्रतिस्थापन, के बारे में सूचित करता है। इस इंटरफ़ेस को लागू करें और तय करें कि जब कोई warning आए तो क्या करना है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**यह क्यों महत्वपूर्ण है:**  
बिना callback के, Aspose.Words चुपचाप लापता फ़ॉन्ट्स को एक डिफ़ॉल्ट फ़ॉन्ट (आमतौर पर Arial) से बदल देता है। `FontSubstitution` warning को पकड़कर आप समस्या को लॉग कर सकते हैं, उपयोगकर्ता को चेतावनी दे सकते हैं, या यहाँ तक कि लापता फ़ॉन्ट को एक कस्टम फ़ॉलबैक से बदल सकते हैं।

### चरण 2: Handler को LoadOptions से जोड़ें

अब हम एक `LoadOptions` इंस्टेंस बनाते हैं और उसे हमारे `FontWarningHandler` का उपयोग करने के लिए बताते हैं। यही वह बिंदु है जहाँ **LoadOptions का उपयोग कैसे करें** वास्तव में चमकता है।

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**यह क्यों महत्वपूर्ण है:**  
`LoadOptions` कई import‑time सेटिंग्स (encoding, password आदि) के लिए एक‑स्टॉप शॉप है। `WarningCallback` सेट करके आप एक हल्का, इवेंट‑ड्रिवन मैकेनिज़्म सक्षम करते हैं जो इन विकल्पों के साथ लोड किए गए किसी भी दस्तावेज़ पर काम करता है।

### चरण 3: कॉन्फ़िगर किए गए Options का उपयोग करके दस्तावेज़ लोड करें

अंत में, हम `LoadOptions` को `Document` कंस्ट्रक्टर में पास करते हैं। यदि स्रोत फ़ाइल ऐसा फ़ॉन्ट संदर्भित करती है जो स्थापित नहीं है, तो Aspose.Words warning फायर करेगा और आपका handler एक संदेश प्रिंट करेगा।

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**आप क्या देखेंगे:**  
मान लीजिए `input.docx` में *“MyCustomFont”* नाम का फ़ॉन्ट उपयोग किया गया है जो मशीन पर नहीं है, तो कंसोल आउटपुट इस प्रकार दिखेगा:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

यदि सभी फ़ॉन्ट्स उपलब्ध हैं, तो callback चुप रहेगा—कोई आउटपुट नहीं, कोई प्रदर्शन हानि नहीं।

## Warning Callback के साथ लापता फ़ॉन्ट्स का पता लगाएँ (द्वितीयक कीवर्ड कार्रवाई में)

वाक्यांश **detect missing fonts** ऊपर के हेडर में स्वाभाविक रूप से प्रकट होता है, जिससे द्वितीयक कीवर्ड को सुदृढ़ किया जाता है। अब हम कुछ विविधताएँ देखते हैं जो वास्तविक प्रोजेक्ट्स में मिल सकती हैं।

### लूप में कई दस्तावेज़

अक्सर आप फ़ाइलों की एक बैच प्रोसेस करेंगे। वही `LoadOptions` इंस्टेंस पुनः उपयोग किया जा सकता है, लेकिन याद रखें कि `WarningCallback` लोड्स के बीच बना रहता है। यदि आपको प्रति‑दस्तावेज़ अलगाव चाहिए, तो प्रत्येक इटरेशन के लिए नया `LoadOptions` बनाएँ।

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### कस्टम फ़ॉन्ट प्रतिस्थापन लॉजिक

सिर्फ लॉग करने के बजाय, आप किसी विशेष लापता फ़ॉन्ट को कंपनी‑स्वीकृत वैकल्पिक फ़ॉन्ट से बदलना चाह सकते हैं। handler को विस्तारित करें:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

अब आप न केवल **लापता फ़ॉन्ट्स का पता लगाते** हैं, बल्कि यह भी तय करते हैं कि उन्हें कैसे बदलना है।

### अनचाहे चेतावनियों को बंद करना

यदि आप केवल फ़ॉन्ट समस्याओं की परवाह करते हैं और बाकी सब कुछ दबाना चाहते हैं, तो नीचे दिखाए अनुसार `WarningType` द्वारा फ़िल्टर करें। इसके विपरीत, *सभी* warnings को लॉग करने के लिए `if` जांच को हटाएँ और `info.WarningType` को `info.Description` के साथ आउटपुट करें।

## पूर्ण, चलाने योग्य उदाहरण

सब कुछ एक साथ रखते हुए, यहाँ एक पूरा प्रोग्राम है जिसे आप कंपाइल और रन कर सकते हैं। `"YOUR_DIRECTORY/input.docx"` को अपने परीक्षण फ़ाइल के पथ से बदलें।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**अपेक्षित कंसोल आउटपुट (जब फ़ॉन्ट लापता हो):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

यदि कोई फ़ॉन्ट लापता नहीं है, तो आप केवल यह देखेंगे:

```
Document loaded successfully.
```

## सामान्य गलतियाँ और प्रो टिप्स

- **गलती:** `WarningCallback` सेट करना भूल जाना। API अभी भी फ़ॉन्ट्स को प्रतिस्थापित करेगा, लेकिन आपको पता नहीं चलेगा कि यह हुआ।  
  **प्रो टिप:** जब आपको फ़ॉन्ट की सटीकता चाहिए, हमेशा एक handler संलग्न करें; इसका खर्च लगभग शून्य है।

- **गलती:** 

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स निकट संबंधी विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करेंगे।

- [Aspose.Words में फ़ॉन्ट्स का पता कैसे लगाएँ – चेतावनियों और सेटिंग्स को संभालें](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words में फ़ॉन्ट्स को कैप्चर कैसे करें – पूर्ण गाइड](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [DOCX को लोड करें और लापता फ़ॉन्ट्स का पता लगाएँ – पूर्ण C# गाइड](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}