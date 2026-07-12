---
category: general
date: 2026-06-27
description: Aspose.Words में चेतावनी कॉलबैक पंजीकृत करें ताकि फ़ॉन्ट प्रतिस्थापन
  और लोडिंग समस्याओं को पकड़ा जा सके। Aspose.Words के साथ LoadOptions के चरण‑दर‑चरण
  उपयोग को सीखें।
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: hi
og_description: Aspose.Words में चेतावनी कॉलबैक पंजीकृत करें ताकि फ़ॉन्ट प्रतिस्थापन
  और अन्य लोडिंग चेतावनियों की निगरानी की जा सके। एक मजबूत कार्यान्वयन के लिए इस पूर्ण
  ट्यूटोरियल का पालन करें।
og_title: Aspose.Words में चेतावनी कॉलबैक पंजीकृत करें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Aspose.Words में वार्निंग कॉलबैक रजिस्टर करें – पूर्ण प्रोग्रामिंग गाइड
url: /hi/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में Warning Callback रजिस्टर करना – पूर्ण प्रोग्रामिंग गाइड

क्या आपने कभी सोचा है कि **Aspose.Words में warning callback कैसे रजिस्टर करें** ताकि आप ठीक‑ठीक देख सकें कि दस्तावेज़ लोड होने पर कौन‑से फ़ॉन्ट बदल दिए गए? आप अकेले नहीं हैं। कई डेवलपर्स को तब समस्या आती है जब चुपचाप फ़ॉन्ट प्रतिस्थापन उत्पन्न PDF या Word फ़ाइल की लेआउट को बिगाड़ देता है।  

इस ट्यूटोरियल में हम एक व्यावहारिक समाधान के माध्यम से चलते हैं जो न केवल Aspose.Words में warning callback रजिस्टर करता है बल्कि यह भी समझाता है *क्यों* आपको यह करना चाहिए, callback कैसे काम करता है, और किन किन किनारे‑के‑मामलों (edge cases) का सामना हो सकता है। अंत तक आप हर फ़ॉन्ट प्रतिस्थापन को लॉग कर पाएँगे, अन्य लोडिंग warnings को पकड़ पाएँगे, और अपने दस्तावेज़‑प्रोसेसिंग पाइपलाइन को पारदर्शी बना पाएँगे।

## आप क्या सीखेंगे

- **LoadOptions** को सेट‑अप करना ताकि दस्तावेज़ लोडिंग व्यवहार को नियंत्रित किया जा सके।  
- एक **warning callback** रजिस्टर करना जो फ़ॉन्ट प्रतिस्थापन और अन्य warning प्रकारों के लिए फायर होता है।  
- कॉन्फ़िगर किए गए विकल्पों के साथ DOCX लोड करना और callback आउटपुट को समझना।  
- सामान्य pitfalls (ग़ायब फ़ॉन्ट, कस्टम फ़ॉन्ट फ़ोल्डर, और प्रदर्शन संबंधी विचार)।  

**Prerequisites:** Visual Studio 2022 (या कोई भी C# IDE), .NET 6+ runtime, और एक सक्रिय Aspose.Words लाइसेंस (फ़्री ट्रायल प्रयोग के लिए पर्याप्त है)। `Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

---

![Diagram illustrating the flow of registering a warning callback in Aspose.Words and handling font substitution warnings](register-warning-callback-aspose-words.png "register warning callback aspose.words diagram")

## Step 1: LoadOptions बनाएं – Warning Handling का एंट्री पॉइंट  

callback के फायर होने से पहले आपको **LoadOptions** की एक इंस्टेंस चाहिए। इसे आप उस कंट्रोल पैनल की तरह समझें जिसे आप Aspose.Words को देते हैं जब आप कहते हैं “इस फ़ाइल को लोड करो, लेकिन अगर कुछ गड़बड़ हो तो मुझे बताओ।”  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Why this matters:** `LoadOptions` आपको एन्क्रिप्शन पासवर्ड से लेकर फ़ॉन्ट डायरेक्टरी तक सब कुछ ट्यून करने देता है। इस ऑब्जेक्ट पर warning callback जोड़ने से एक चुप‑चाप प्रक्रिया को एक देखी‑जाने वाली प्रक्रिया में बदल दिया जाता है।

## Step 2: Warning Callback रजिस्टर करें – फ़ॉन्ट प्रतिस्थापन को कैप्चर करें  

अब आती है मुख्य बात: **warning callback**। हम एक अनाम मेथड (lambda) रजिस्टर करेंगे जिसे Aspose.Words हर लोडिंग warning पर कॉल करेगा। callback के अंदर हम `WarningType.FontSubstitution` को फ़िल्टर करेंगे और एक दोस्ताना संदेश प्रिंट करेंगे।

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Pro tip:** यदि आप ग़ायब इमेज या असमर्थित फीचर भी लॉग करना चाहते हैं, तो `args.WarningType` की जाँच करने वाले अतिरिक्त `if` ब्रांच जोड़ें। इस तरह आपका **register warning callback in Aspose.Words** इम्प्लीमेंटेशन सभी लोडिंग डायग्नोस्टिक्स के लिए एक‑स्टॉप शॉप बन जाता है।

## Step 3: कॉन्फ़िगर किए गए LoadOptions के साथ दस्तावेज़ लोड करें  

callback को जोड़ने के बाद अगला कदम बस दस्तावेज़ को लोड करना है। `loadOptions` इंस्टेंस को `Document` कन्स्ट्रक्टर में पास करें। जब भी Aspose.Words को कोई फ़ॉन्ट नहीं मिलता, आपका callback फायर होगा और कंसोल पर लिखेगा।

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

प्रोग्राम चलाएँ, और आपको इस तरह का आउटपुट दिखेगा:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

यही है **register warning callback aspose.words** का मूल—एक तीन‑स्टेप पैटर्न जिसे आप किसी भी प्रोजेक्ट में दोहरा सकते हैं।

## Step 4: वास्तविक दुनिया के परिदृश्यों के लिए Callback को विस्तारित करना  

### 4.1 कंसोल के बजाय फ़ाइल में लॉग करना  

प्रोडक्शन में आप आमतौर पर कंसोल स्पैम नहीं चाहते। `Console.WriteLine` को किसी लॉगर (जैसे `Serilog`, `NLog`) या टेक्स्ट फ़ाइल में लिखने के लिए बदलें:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 कस्टम फ़ॉन्ट डायरेक्टरी प्रदान करना  

यदि आपका वातावरण कॉर्पोरेट फ़ॉन्ट इस्तेमाल करता है, तो Aspose.Words को बताएं कि फ़ॉन्ट कहाँ खोजे, इससे प्रतिस्थापन कम होगा:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

अब callback *कम* बार फायर हो सकता है, क्योंकि इंजन सही फ़ॉन्ट पा लेता है।

### 4.3 गैर‑फ़ॉन्ट warnings को हैंडल करना  

आप स्कोप को विस्तारित करके किसी भी लोडिंग warning को कैप्चर कर सकते हैं:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Step 5: इम्प्लीमेंटेशन का परीक्षण – क्या उम्मीद करें  

### 5.1 ग़ायब फ़ॉन्ट वाले दस्तावेज़ से वेरिफ़ाई करें  

एक छोटा DOCX बनाएं जो ऐसे फ़ॉन्ट को रेफ़र करे जो आपके मशीन पर इंस्टॉल नहीं है (जैसे “Comic Sans MS” Linux सर्वर पर)। लोडर चलाएँ; आपको एक substitution संदेश दिखना चाहिए।  

### 5.2 ओवरहेड बेंचमार्क करें  

callback का ओवरहेड नगण्य है—लगभग कुछ माइक्रोसेकंड प्रति warning। यदि आप हजारों दस्तावेज़ लोड कर रहे हैं, तो आप लॉग एंट्रीज़ को बैच कर सकते हैं या गैर‑क्रिटिकल रन के लिए callback को डिसेबल कर सकते हैं।

### 5.3 Edge Cases  

- **एक ही फ़ॉन्ट के कई Substitutions:** यदि वही ग़ायब फ़ॉन्ट विभिन्न पेज़ पर आता है तो Aspose.Words कई बार callback फायर कर सकता है। आवश्यक होने पर अपने लॉगर में डिडुप्लिकेशन करें।  
- **Encrypted Documents:** यदि DOCX पासवर्ड‑प्रोटेक्टेड है, तो आपको `loadOptions.Password` भी सेट करना होगा। डिक्रिप्शन के बाद भी callback फायर होगा।  
- **Async Loading:** API सिंक्रोनस है, लेकिन आप `Task.Run` से लोड कॉल को बैकग्राउंड में चला सकते हैं; callback थ्रेड‑सेफ़ रहता है।

## Common Pitfalls & How to Avoid Them  

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **कोई आउटपुट नहीं** | Callback असाइन नहीं किया गया *या* बाद में `WarningCallback` ओवरराइट हो गया। | लोड करने से पहले **एक बार** callback असाइन करें, और असाइनमेंट के बाद `loadOptions` को फिर से असाइन न करें। |
| **Incorrect cast exception** | ऐसी warning को कास्ट करने की कोशिश करना जो `FontSubstitutionWarningInfo` नहीं है। | हमेशा `args.WarningType` की जाँच करने के बाद ही कास्ट करें। |
| **Performance slowdown** | धीमी I/O टार्गेट पर सिंक्रोनस लॉगिंग। | असिंक्रोनस लॉगिंग फ्रेमवर्क या बफ़रड राइट्स इस्तेमाल करें। |
| **Missing custom fonts** | `FontSettings` में फ़ॉन्ट फ़ोल्डर नहीं जोड़ा गया। | Step 4.2 में दिखाए अनुसार `SetFontsFolder` जोड़ें। |

## Full Working Example – Paste‑And‑Run  

नीचे एक स्व-समाहित प्रोग्राम है जिसे आप नई Console App प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं। यह शुरुआत से अंत तक पूरे फ्लो को दर्शाता है।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Expected console output** (मान लीजिए फ़ॉन्ट ग़ायब हैं):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

प्रोग्राम चलाएँ, और आपको ठीक‑ठीक दिखेगा कि Aspose.Words ने कौन‑से फ़ॉन्ट बदल दिए, जिससे लोडिंग प्रक्रिया पूरी तरह से पारदर्शी हो जाएगी।

---

## निष्कर्ष  

हमने अभी **Aspose.Words में warning callback कैसे रजिस्टर करें** को कवर किया, यह क्यों किसी भी दस्तावेज़‑प्रोसेसिंग वर्कफ़्लो के लिए बेस्ट‑प्रैक्टिस है, और इसे लॉगिंग, कस्टम फ़ॉन्ट और व्यापक warning हैंडलिंग के लिए कैसे विस्तारित किया जा सकता है। सिर्फ तीन लाइनों के कोड से आप एक ब्लैक‑बॉक्स लोड ऑपरेशन को ऑडिटेबल, डिबगेबल स्टेप में बदल देते हैं—अब कोई रहस्यमय लेआउट बदलाव नहीं।

अगला क्या? इस callback को **Aspose.Words SaveOptions** के साथ मिलाकर लोड *और* सेव दोनों के दौरान warnings लॉग करें, या इसे वेब API में इंटीग्रेट करें जो रियल‑टाइम अपलोड प्रोसेस करता है। आप उन सेकेंडरी कीवर्ड्स को भी एक्सप्लोर कर सकते हैं—जैसे *loadoptions font substitution warning*—ताकि प्रदर्शन को फाइन‑ट्यून किया जा सके या मॉनिटरिंग डैशबोर्ड के साथ इंटीग्रेट किया जा सके।

कोई सवाल या जटिल परिदृश्य है? कमेंट करें, और मिलकर समाधान खोजें। Happy coding, और आपके PDFs हमेशा सही फ़ॉन्ट के साथ रेंडर हों!

## आगे क्या सीखें?


नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक रिसोर्स में पूर्ण कार्यशील कोड उदाहरण और स्टेप‑बाय‑स्टेप एक्सप्लानेशन होते हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}