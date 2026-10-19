---
category: general
date: 2026-03-01
description: C# में FontSettings बनाएं ताकि गायब फ़ॉन्ट्स का पता लगाया जा सके, फ़ॉन्ट
  संदेशों को कैप्चर किया जा सके, और Aspose.Words के साथ गायब फ़ॉन्ट्स को संभाला जा
  सके। डेवलपर्स के लिए चरण‑दर‑चरण गाइड।
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: hi
og_description: C# में FontSettings बनाकर गायब फ़ॉन्ट्स का पता लगाएँ, फ़ॉन्ट संदेशों
  को कैप्चर करें, और Aspose.Words का उपयोग करके गायब फ़ॉन्ट्स को संभालें। कोड सहित
  पूर्ण ट्यूटोरियल।
og_title: C# में FontSettings बनाएं – गायब फ़ॉन्ट्स का पता लगाएँ और फ़ॉन्ट संदेशों
  को कैप्चर करें
tags:
- Aspose.Words
- C#
- Font Management
title: C# में FontSettings बनाएं – लापता फ़ॉन्ट्स का पता लगाएँ और फ़ॉन्ट संदेशों को
  कैप्चर करें
url: /hi/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में FontSettings बनाएं – गायब फ़ॉन्ट्स का पता लगाएँ और फ़ॉन्ट संदेश कैप्चर करें

क्या आपको कभी .NET प्रोजेक्ट में **create FontSettings** करने की ज़रूरत पड़ी है लेकिन यह नहीं पता था कि लक्ष्य मशीन पर कौन से फ़ॉन्ट इंस्टॉल नहीं हैं? आप अकेले नहीं हैं। कई वास्तविक‑दुनिया के ऐप्स—जैसे स्वचालित रिपोर्ट जेनरेटर या दस्तावेज़ कन्वर्टर—में गायब फ़ॉन्ट्स चुपचाप लेआउट को बिगाड़ सकते हैं, और आपको तब तक पता नहीं चलता जब तक PDF अजीब नज़र न आए।  

क्या होगा अगर आप **detect missing fonts**, **capture font messages**, और **handle missing fonts** को अपने आउटपुट को बिगाड़ने से पहले कर सकें? अच्छी खबर यह है कि Aspose.Words इसे बहुत आसान बना देता है। इस ट्यूटोरियल में हम पूरी प्रक्रिया को चरण‑दर‑चरण देखेंगे, `FontSettings` ऑब्जेक्ट को सेटअप करने से लेकर एक वार्निंग कॉलबैक को जोड़ने तक जो आपको ठीक‑ठीक बताता है कि कौन से glyphs को प्रतिस्थापित किया गया।  

> **TL;DR:** अंत तक आपके पास एक तैयार‑चलाने‑योग्य C# कंसोल ऐप होगा जो हर फ़ॉन्ट प्रतिस्थापन को लॉग करता है, जिससे आप तय कर सकें कि प्रतिस्थापन को एम्बेड करना है या उपयोगकर्ता को चेतावनी देनी है।

---

## आवश्यकताएँ

- .NET 6 SDK (या कोई भी नवीनतम .NET संस्करण)  
- Visual Studio 2022 या VS Code के साथ C# एक्सटेंशन  
- Aspose.Words for .NET लाइसेंस (इस डेमो के लिए फ्री ट्रायल काम करता है)  
- एक सैंपल DOCX जो ऐसे फ़ॉन्ट को रेफ़रेंस करता है जो आपके सिस्टम में इंस्टॉल नहीं है (उदाहरण के लिए, *Comic Sans MS* Linux बॉक्स पर)  

`Aspose.Words` के अलावा कोई विशेष NuGet पैकेज आवश्यक नहीं हैं।

---

## चरण 1 – Aspose.Words इंस्टॉल करें और प्रोजेक्ट सेट अप करें

सबसे पहले, एक नया कंसोल प्रोजेक्ट बनाएं और Aspose.Words लाइब्रेरी को इसमें जोड़ें।

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** यदि आपके पास पहले से एक सॉल्यूशन है, तो पैकेज को NuGet पैकेज मैनेजर UI के माध्यम से जोड़ें—यह संस्करण ट्रैकिंग को आसान बनाता है।

---

## चरण 2 – FontSettings बनाएं (मुख्य कीवर्ड यहाँ प्रकट होता है)

**create FontSettings** चरण किसी भी फ़ॉन्ट‑संबंधित वर्कफ़्लो की रीढ़ है। `FontSettings` Aspose.Words को बताता है कि फ़ॉन्ट्स कहाँ खोजें, सिस्टम फ़ोल्डर्स का उपयोग करना है या नहीं, और जब कुछ गायब हो तो कैसे बैकअप ले।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

यह क्यों महत्वपूर्ण है? यदि `FontSettings` सही ढंग से कॉन्फ़िगर नहीं है, तो इंजन चुपचाप गायब glyphs को डिफ़ॉल्ट सिस्टम फ़ॉन्ट से बदल देता है, और आपको कभी कोई चेतावनी नहीं दिखेगी।

---

## चरण 3 – LoadOptions को FontSettings के साथ जोड़ें

`LoadOptions` आपको `FontSettings` को डॉक्यूमेंट लोडर में पास करने देता है। यह वह पुल है जो इंजन को `Document` निर्माण चरण के दौरान **detect missing fonts** करने में सक्षम बनाता है।

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

अब हर बार जब आप `loadOptions` के साथ एक DOCX लोड करेंगे, Aspose.Words पहले सेट किए गए `FontSettings` को देखेगा।

---

## चरण 4 – एक वार्निंग कॉलबैक जोड़ें ताकि **Capture Font Messages** किया जा सके

Aspose.Words विभिन्न स्थितियों के लिए वार्निंग जारी करता है—फ़ॉन्ट प्रतिस्थापन एक सामान्य उदाहरण है। `IWarningCallback` का इम्प्लीमेंटेशन प्रदान करके, आप वास्तविक समय में **capture font messages** कर सकते हैं।

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### वार्निंग हैंडलर क्लास

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

`info.Description` फ़ील्ड में एक मानव‑पठनीय संदेश होता है जैसे *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* यह वही प्रकार का आउटपुट है जिसकी आपको **handle missing fonts** को सुगमता से करने के लिए आवश्यकता है।

---

## चरण 5 – डॉक्यूमेंट लोड करें और कॉलबैक को अपना काम करने दें

सब कुछ सेट हो जाने पर, डॉक्यूमेंट लोड करना सरल है। यदि स्रोत फ़ाइल सिस्टम में मौजूद नहीं होने वाले फ़ॉन्ट को रेफ़रेंस करती है, तो हमारा वार्निंग हैंडलर ट्रिगर होगा।

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

जब आप प्रोग्राम चलाएंगे, तो आपको कंसोल आउटपुट इस प्रकार दिखेगा:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

यह आउटपुट हमारे वर्कफ़्लो का **capture font messages** भाग है। आप हैंडलर को फ़ाइल में लॉग करने, टेलीमेट्री भेजने, या यदि महत्वपूर्ण फ़ॉन्ट्स गायब हों तो कन्वर्ज़न को रोकने के लिए भी विस्तारित कर सकते हैं।

---

## चरण 6 – पूर्ण कार्यशील उदाहरण (सभी भाग एक साथ)

नीचे एक पूर्ण, कॉपी‑पेस्ट‑तैयार प्रोग्राम दिया गया है। इसे `Program.cs` में पेस्ट करें, फ़ाइल पाथ्स को समायोजित करें, और `dotnet run` चलाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### अपेक्षित आउटपुट

यदि आप प्रोग्राम को ऐसे मशीन पर चलाते हैं जिसमें *Comic Sans MS* नहीं है, तो यह कुछ इस तरह प्रिंट करेगा:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

आपके पास `Result.pdf` भी होगा जो प्रतिस्थापित फ़ॉन्ट्स का उपयोग करता है, जिससे कन्वर्ज़न कभी क्रैश नहीं होगा।

---

## सामान्य प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| **यदि मैं प्रतिस्थापन के बजाय कन्वर्ज़न को फेल करना चाहता हूँ तो क्या करें?** | `FontSubstitutionWarningHandler` के अंदर, जब `info.Description` में कोई महत्वपूर्ण फ़ॉन्ट नाम हो तो एक्सेप्शन थ्रो करें। |
| **क्या मैं स्वचालित रूप से एक प्रतिस्थापन फ़ॉन्ट एम्बेड कर सकता हूँ?** | हाँ। गायब फ़ॉन्ट का पता चलने के बाद, आप ज्ञात पाथ से एक फ़ॉलबैक `FontInfo` लोड कर सकते हैं और उसे `fontSettings.SetFontsFolder` के माध्यम से `fontSettings` में जोड़ सकते हैं। |
| **क्या यह Linux/macOS पर काम करता है?** | बिल्कुल। `FontSettings` क्रॉस‑प्लेटफ़ॉर्म काम करता है; बस यह सुनिश्चित करें कि फ़ॉलबैक फ़ोल्डर में उपयुक्त `.ttf` या `.otf` फ़ाइलें हों। |
| **क्या वार्निंग कॉलबैक थ्रेड‑सेफ़ है?** | कॉलबैक उसी थ्रेड पर चलता है जो डॉक्यूमेंट लोड करता है, इसलिए कंसोल लॉगिंग के लिए अतिरिक्त सिंक्रोनाइज़ेशन की आवश्यकता नहीं है। मल्टी‑थ्रेडेड स्थितियों में, साझा संसाधनों की रक्षा करें। |
| **मैं वार्निंग्स को फ़ाइल में कैसे लॉग करूँ?** | `Console.WriteLine` को `File.AppendAllText("font_warnings.log", ...)` से बदलें या कोई भी लॉगिंग फ्रेमवर्क (Serilog, NLog) उपयोग करें। |

---

## प्रोडक्शन‑रेडी फ़ॉन्ट हैंडलिंग के लिए प्रो टिप्स

1. फ़ॉन्ट लुकअप को कैश करें – कई डॉक्यूमेंट लोड्स में एक ही `FontSettings` इंस्टेंस को पुन: उपयोग करने से फ़ाइल सिस्टम स्कैन दोहराने से बचा जा सकता है।  
2. क्रिटिकल फ़ॉन्ट्स को व्हाइटलिस्ट करें – यदि आपके ब्रांड को कोई विशेष फ़ॉन्ट चाहिए, तो उसकी उपस्थिति प्रारंभ में जांचें और स्पष्ट त्रुटि संदेश के साथ एबॉर्ट करें।  
3. `SetFontFolder` को रिकर्सिवली उपयोग करें – `recursive: true` सेट करने से सबफ़ोल्डर्स स्कैन होते हैं, जो पूरी फ़ॉन्ट कलेक्शन शिप करने पर उपयोगी है।  
4. `FontSubstitutionSettings` के साथ संयोजन करें – आप प्रतिस्थापन नियमों को बारीकी से ट्यून कर सकते हैं (जैसे, समान फ़ैमिली नाम वाले फ़ॉन्ट्स को प्राथमिकता देना)।  

---

## निष्कर्ष

हमने अभी-अभी **FontSettings** बनाई, `LoadOptions` को **detect missing fonts** के लिए कॉन्फ़िगर किया, एक कॉलबैक जो **captures font messages** करता है, उसे जोड़ा, और दिखाया कि कैसे **handle missing fonts** को एक साफ़, प्रोडक्शन‑रेडी तरीके से किया जाए। पूरी प्रक्रिया कुछ दर्जन लाइनों के C# कोड में समा जाती है, फिर भी यह आपको किसी भी प्रोसेस किए गए DOCX के फ़ॉन्ट परिदृश्य की पूरी दृश्यता देती है।  

आगे, आप निम्नलिखित का अन्वेषण कर सकते हैं:

- **फ़ॉलबैक फ़ॉन्ट्स को एम्बेड करना** सीधे आउटपुट PDF में (`PdfSaveOptions.FontEmbeddingMode`)।  
- **प्रोग्रामेटिकली फ़ॉन्ट्स को प्रतिस्थापित करना** कॉर्पोरेट ब्रांडिंग नियमों के आधार पर।  
- **CI पाइपलाइन के साथ इंटीग्रेट करना** ताकि अनधिकृत फ़ॉन्ट्स वाले दस्तावेज़ों को स्वचालित रूप से फ़्लैग किया जा सके।  

इसे आज़माएँ, अपनी ज़रूरतों के अनुसार वार्निंग हैंडलर को समायोजित करें, और अपने डॉक्यूमेंट पाइपलाइन्स को भरोसे के साथ चलने दें—अब अदृश्य फ़ॉन्ट स्वैप्स के कारण होने वाले रहस्यमय लेआउट गड़बड़ियों का सामना नहीं करना पड़ेगा।  

कोडिंग का आनंद लें! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}