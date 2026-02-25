---
category: general
date: 2026-02-24
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में फ़ॉन्ट्स का पता कैसे लगाएँ।
  कॉलबैक सेट करने और पूर्ण कोड उदाहरण के साथ Word दस्तावेज़ लोड करने के बारे में जानें।
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: hi
og_description: एक वॉर्निंग कॉलबैक का उपयोग करके वर्ड दस्तावेज़ में फ़ॉन्ट्स का पता
  कैसे लगाएँ। यह गाइड दिखाता है कि कॉलबैक कैसे सेट करें और Aspose.Words के साथ वर्ड
  दस्तावेज़ कैसे लोड करें।
og_title: वर्ड दस्तावेज़ों में फ़ॉन्ट कैसे पहचानें – चरण‑दर‑चरण C# ट्यूटोरियल
tags:
- C#
- Aspose.Words
- Document Processing
title: वर्ड दस्तावेज़ों में फ़ॉन्ट कैसे पहचानें – पूर्ण C# गाइड
url: /hi/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

placeholders. Keep them unchanged.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ों में फ़ॉन्ट कैसे पता करें – पूर्ण C# गाइड

क्या आपने कभी सोचा है कि **how to detect fonts** जब आप एक Word फ़ाइल लोड करते हैं तो कौन‑से फ़ॉन्ट गायब हैं? शायद आप ऐसे दस्तावेज़ से मिले हैं जो एडिटर में ठीक दिखता है, लेकिन उत्पन्न PDF कुछ टाइपफ़ेस को पीछे से बदल देता है। यह फ़ॉन्ट प्रतिस्थापन का क्लासिक लक्षण है, और इसे जल्दी पकड़ना आपको अप्रिय लेआउट आश्चर्यों से बचा सकता है।

इस ट्यूटोरियल में हम एक व्यावहारिक समाधान पर चलेंगे: **Aspose.Words** का उपयोग करके एक `.docx` लोड करना, एक warning callback संलग्न करना, और **how to set callback** जो हर फ़ॉन्ट प्रतिस्थापन की रिपोर्ट करता है। अंत तक आप न केवल **how to detect fonts** प्रोग्रामेटिक रूप से जानेंगे, बल्कि **how to set callback** को सही तरीके से समझेंगे और **load word document** को सुरक्षित रूप से लोड करेंगे—सभी एक ही चलाने योग्य C# उदाहरण में।

> **आपको क्या मिलेगा**
> * एक पूर्ण, कॉपी‑पेस्ट‑तैयार कोड नमूना  
> * प्रत्येक पंक्ति की चरण‑दर‑चरण व्याख्या  
> * कई गायब फ़ॉन्ट या कस्टम फ़ॉन्ट फ़ोल्डर जैसी किनारी स्थितियों को संभालने के टिप्स  
> * अपेक्षित कंसोल आउटपुट ताकि आप सत्यापित कर सकें कि सब कुछ काम कर रहा है

---

## आवश्यकताएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Core के साथ भी काम करता है)  
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)  
- एक Word फ़ाइल जो जानबूझकर ऐसे फ़ॉन्ट का संदर्भ देती है जो आपके सिस्टम में स्थापित नहीं है (उदाहरण के लिए `MissingFont.docx`)  
- Visual Studio, Rider, या कोई भी पसंदीदा एडिटर

कोई अन्य लाइब्रेरी आवश्यक नहीं है; बाकी सब मानक .NET रनटाइम का हिस्सा है।

## Word दस्तावेज़ में फ़ॉन्ट कैसे पता करें

### चरण 1: Load Options बनाएं और Warning Callback संलग्न करें

पहला काम हम Aspose.Words को बताते हैं कि हम फ़ाइल लोड करते समय उत्पन्न होने वाली किसी भी समस्या की सूचना चाहते हैं। यही वह जगह है जहाँ **how to set callback** काम आता है।

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**यह क्यों महत्वपूर्ण है:**  
`LoadOptions` लोडिंग प्रक्रिया को अनुकूलित करने का द्वार है। `WarningCallback` को `FontWarningCollector` की एक इंस्टेंस असाइन करके, Aspose.Words हर बार जब वह किसी गायब फ़ॉन्ट को फॉलबैक से बदलता है, हमारे `Warning` मेथड को कॉल करेगा। यह **how to detect fonts** का मूल है जो मशीन पर मौजूद नहीं हैं।

### चरण 2: LoadOptions इंस्टेंस तैयार करें

अब हम `LoadOptions` को इंस्टैंशिएट करते हैं और अपना callback जोड़ते हैं।

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Pro tip:** यदि आपको नियंत्रित करना है कि Aspose प्रतिस्थापन फ़ॉन्ट कहाँ देखे, तो आप यहाँ `loadOptions.FontSettings` भी सेट कर सकते हैं। यह तब उपयोगी होता है जब आपके सर्वर पर एक निजी फ़ॉन्ट फ़ोल्डर हो।

### चरण 3: Word दस्तावेज़ लोड करें

विकल्प तैयार होने के बाद, हम अंततः **load word document** करते हैं। यही वह क्षण है जब Aspose DOCX को पार्स करता है और यदि कोई फ़ॉन्ट गायब है, तो हमारा callback सक्रिय हो जाता है।

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**आंतरिक रूप से क्या होता है?**  
Aspose.Words DOCX के XML भागों को पढ़ता है, प्रत्येक `<w:font>` रेफ़रेंस को हल करता है, और सिस्टम के फ़ॉन्ट संग्रह को जांचता है। जब भी कोई रेफ़रेंस संतुष्ट नहीं हो पाता, यह पहला मिलता‑जुलता फॉलबैक फ़ॉन्ट प्रतिस्थापित करता है और एक `FontSubstitution` चेतावनी उत्पन्न करता है।

### चरण 4: आउटपुट सत्यापित करें

प्रोग्राम चलाएँ और कंसोल देखें। प्रत्येक गायब फ़ॉन्ट के लिए आपको इस प्रकार की एक पंक्ति दिखाई देगी:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

यदि दस्तावेज़ में कोई गायब फ़ॉन्ट नहीं है, तो कंसोल चुप रहता है—जिसका अर्थ है कि **how to detect fonts** ने कोई परिणाम नहीं दिया।

### चरण 5: पूर्ण कार्यशील उदाहरण (कंसोल ऐप)

नीचे एक स्वतंत्र `Program.cs` दिया गया है जिसे आप नए कंसोल प्रोजेक्ट में डाल सकते हैं। इसमें हमने चर्चा किए सभी हिस्से शामिल हैं साथ ही डिबगिंग के दौरान कंसोल विंडो को खुला रखने के लिए एक छोटा हेल्पर भी है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**अपेक्षित कंसोल आउटपुट** (उदाहरण):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

यदि आप `MissingFont.docx` को ऐसी फ़ाइल से बदलते हैं जो केवल स्थापित फ़ॉन्ट का उपयोग करती है, तो आपको केवल “Press any key…” पंक्ति दिखेगी—जिससे पुष्टि होती है कि डिटेक्शन लॉजिक इच्छित रूप से काम कर रहा है।

## सामान्य प्रश्न और किनारी स्थितियाँ

### यदि मुझे केवल फ़ॉन्ट प्रतिस्थापन नहीं, बल्कि *सभी* चेतावनियों को पकड़ना हो तो क्या करें?

सिर्फ `if (info.Type == WarningType.FontSubstitution)` गार्ड को हटाएँ। `WarningInfo` ऑब्जेक्ट में एक `Type` enum होता है जिसे आप अन्य परिदृश्यों (जैसे `DocumentStructure`, `ImageLoading`) के लिए स्विच कर सकते हैं।

### क्या मैं चेतावनियों को कंसोल के बजाय फ़ाइल में लॉग कर सकता हूँ?

बिल्कुल। `Console.WriteLine` को किसी भी लॉगिंग फ्रेमवर्क कॉल (`Serilog`, `NLog`, आदि) से बदल दें। कॉलबैक उसी थ्रेड पर चलता है जो दस्तावेज़ लोड करता है, इसलिए सुनिश्चित करें कि आपका लॉगर थ्रेड‑सेफ़ हो।

### वेब एप्लिकेशन में यह कैसे व्यवहार करता है?

ASP.NET Core में आप सामान्यतः एक singleton `IWarningCallback` इम्प्लीमेंटेशन को इंजेक्ट करेंगे और उसे `LoadOptions` के माध्यम से पास करेंगे। सीधे रिस्पॉन्स स्ट्रीम में लिखने से बचें—डेटाबेस या इन‑मेमोरी कलेक्शन में लॉग करें जिसे आप बाद में API एंडपॉइंट के माध्यम से एक्सपोज़ कर सकते हैं।

### गैर‑सिस्टम फ़ोल्डर में संग्रहीत कस्टम फ़ॉन्ट के बारे में क्या?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

अब Aspose.Words `C:\MyCustomFonts` को OS फ़ॉन्ट्स के फॉलबैक से पहले खोजेगा, जिससे आपको मिलने वाले प्रतिस्थापन चेतावनियों की संख्या कम होगी।

## दृश्य सारांश

![Aspose.Words में फ़ॉन्ट चेतावनी कॉलबैक का पता लगाएँ](/images/font-warning-callback.png "फ़ॉन्ट्स का पता लगाने के लिए चेतावनी कॉलबैक का उपयोग कैसे करें")

*स्क्रीनशॉट दिखाता है कि जब कोई फ़ॉन्ट गायब होता है तो कंसोल आउटपुट क्या होता है। alt टेक्स्ट में SEO के लिए मुख्य कीवर्ड शामिल है।*

## निष्कर्ष

अब आपके पास Aspose.Words के साथ लोड किए गए किसी भी Word फ़ाइल में **how to detect fonts** के लिए एक ठोस, प्रोडक्शन‑रेडी पैटर्न है। **how to set callback** द्वारा आप गायब या प्रतिस्थापित टाइपफ़ेस की रीयल‑टाइम जानकारी प्राप्त करते हैं, और आपने **load word document** को साफ़ और मेंटेनेबल कोड रखते हुए सही तरीके से करना सीख लिया है।

अगले कदम? कॉलबैक को विस्तारित करके चेतावनियों को एक सूची में एकत्रित करने का प्रयास करें, फिर उन्हें UI या स्वचालित रिपोर्ट में प्रदर्शित करें। आप `FontSettings.SubstitutionSettings` को भी एक्सप्लोर कर सकते हैं ताकि यह नियंत्रित किया जा सके कि *कौन‑से* फ़ॉन्ट फॉलबैक के रूप में चुने जाएँ।

बिना झिझक प्रयोग करें—दस्तावेज़ बदलें, अधिक गायब फ़ॉन्ट जोड़ें, या इस लॉजिक को बड़े दस्तावेज़‑प्रोसेसिंग पाइपलाइन में एकीकृत करें। यदि आपको कोई समस्या आती है, तो नीचे टिप्पणी छोड़ें या GitHub पर मुझे ping करें।

कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा वही फ़ॉन्ट्स दिखाएँ जो आप अपेक्षा करते हैं!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}