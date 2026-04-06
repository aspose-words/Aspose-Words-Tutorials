---
category: general
date: 2026-04-05
description: Aspose फ़ॉन्ट प्रतिस्थापन गाइड वर्ड दस्तावेज़ लोड करते समय गायब फ़ॉन्ट्स
  का पता लगाने के लिए। फ़ॉन्ट सेटिंग्स को कॉन्फ़िगर करना और गायब फ़ॉन्ट्स को कुशलतापूर्वक
  संभालना सीखें।
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: hi
og_description: Aspose फ़ॉन्ट प्रतिस्थापन गाइड जो वर्ड दस्तावेज़ लोड करते समय गायब
  फ़ॉन्ट्स का पता लगाता है। फ़ॉन्ट सेटिंग्स को कॉन्फ़िगर करना सीखें और गायब फ़ॉन्ट्स
  को प्रभावी ढंग से संभालें।
og_title: Aspose फ़ॉन्ट प्रतिस्थापन – वर्ड दस्तावेज़ों में गायब फ़ॉन्ट का पता लगाएँ
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose फ़ॉन्ट प्रतिस्थापन – वर्ड दस्तावेज़ों में लापता फ़ॉन्ट का पता लगाएँ
url: /hi/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Word दस्तावेज़ों में लापता फ़ॉन्ट्स का पता लगाएँ

क्या कभी ऐसा हुआ है कि एक Word फ़ाइल एक मशीन पर एकदम सही दिखती है, लेकिन दूसरी पर फ़ॉन्ट बदलकर दिखती है? यही क्लासिक **aspose font substitution** समस्या है, और आमतौर पर इसका मतलब है कि लक्ष्य सिस्टम में कुछ फ़ॉन्ट्स नहीं हैं। इस ट्यूटोरियल में हम आपको चरण‑बद्ध तरीके से दिखाएंगे कि **Word दस्तावेज़ लोड करते समय लापता फ़ॉन्ट्स का पता कैसे लगाएँ**, **फ़ॉन्ट सेटिंग्स को कैसे कॉन्फ़िगर करें**, और **लापता फ़ॉन्ट्स को सुगमता से कैसे हैंडल करें**।

हम एक पूर्ण, चलने योग्य C# उदाहरण के माध्यम से चलेंगे, समझाएंगे कि प्रत्येक पंक्ति क्यों महत्वपूर्ण है, और वह कंसोल आउटपुट भी दिखाएंगे जिसकी आपको उम्मीद करनी चाहिए। अंत तक आप दस्तावेज़ लोड होते ही फ़ॉन्ट प्रतिस्थापन को पहचान सकेंगे—बिना किसी अनुमान के।

## आप क्या सीखेंगे

- Aspose.Words के फ़ॉन्ट चेतावनियों के लिए डायग्नोस्टिक कलेक्टर को कैसे सक्षम करें।  
- कस्टम **फ़ॉन्ट सेटिंग्स** के साथ **Word दस्तावेज़ लोड** करने के लिए आवश्यक सटीक कोड।  
- `WarningInfo` ऑब्जेक्ट्स पर इटरेट करके हर प्रतिस्थापित फ़ॉन्ट की सूची कैसे बनाएं।  
- अनचाही चेतावनियों को दबाने या फॉलबैक फ़ॉन्ट प्रदान करने के टिप्स।  
- एक तैयार‑से‑चलाने वाला सैंपल जिसे आप Visual Studio में कॉपी‑पेस्ट कर सकते हैं।

### आवश्यकताएँ

- .NET 6.0 या बाद का (API .NET Framework पर भी समान काम करता है)।  
- Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`)।  
- एक Word फ़ाइल जिसमें ऐसा फ़ॉन्ट रेफ़रेंस हो जो आपके सिस्टम में इंस्टॉल न हो (जैसे `MissingFont.docx`)।  

यदि आपके पास ये सब है, तो चलिए शुरू करते हैं।

## चरण 1 – डायग्नोस्टिक कलेक्टर को सक्षम करें (फ़ॉन्ट सेटिंग्स कॉन्फ़िगर करें)

सबसे पहले: Aspose.Words केवल तब ही फ़ॉन्ट प्रतिस्थापन चेतावनियों को रिकॉर्ड करता है जब आप उसे बताते हैं। यह `FontSettings` ऑब्जेक्ट बनाकर और उसे `LoadOptions` इंस्टेंस में असाइन करके किया जाता है। इसे फ़ॉन्ट हैंडलिंग के लिए “डिबग लाइट्स” चालू करने जैसा समझें।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**क्यों?**  
यदि `FontSettings` ऑब्जेक्ट नहीं बनाया गया, तो चेतावनी कलेक्टर चुप रहता है, और आपको कभी नहीं पता चलता कि कौन से फ़ॉन्ट बदल दिए गए। इसे खाली इनिशियलाइज़ करके हम Aspose को डिफ़ॉल्ट सिस्टम फ़ॉन्ट्स उपयोग करने देते हैं *और* किसी भी प्रतिस्थापन को ट्रैक करते हैं।

> **प्रो टिप:** यदि आपको पता है कि कोई विशेष फ़ोल्डर कॉरपोरेट फ़ॉन्ट्स रखता है, तो `FontSettings` को `SetFontsFolder("path")` के साथ वहाँ पॉइंट करें। इससे लापता‑फ़ॉन्ट चेतावनियों की संख्या घट सकती है।

## चरण 2 – कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें (Word दस्तावेज़ लोड करें)

अब जब कलेक्टर सक्रिय है, तो वही `LoadOptions` का उपयोग करके अपनी `.docx` फ़ाइल लोड करें। यही वह क्षण है जब Aspose दस्तावेज़ को स्कैन करता है, हर फ़ॉन्ट रेफ़रेंस देखता है, और तय करता है कि प्रतिस्थापन आवश्यक है या नहीं।

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**यह क्यों महत्वपूर्ण है?**  
यदि आप केवल `new Document("MissingFont.docx")` कॉल करते, तो डिफ़ॉल्ट सेटिंग्स लागू होतीं *और* चेतावनी सूची खाली रहती। `loadOptions` पास करने से यह सुनिश्चित होता है कि डायग्नोस्टिक कलेक्टर लोडिंग पाइपलाइन में जुड़ा हुआ है।

## चरण 3 – फ़ॉन्ट प्रतिस्थापन चेतावनियों को प्राप्त करें और प्रदर्शित करें (लापता फ़ॉन्ट्स का पता लगाएँ)

दस्तावेज़ मेमोरी में लोड हो जाने के बाद, Aspose किसी भी चेतावनी को `document.WarningCallback.Warnings` में स्टोर करता है। उस कलेक्शन पर लूप लगाएँ, `WarningType.FontSubstitution` के लिए फ़िल्टर करें, और विवरण प्रिंट करें। प्रत्येक विवरण बताता है कि कौन सा फ़ॉन्ट लापता था और उसकी जगह कौन सा फ़ॉन्ट उपयोग किया गया।

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**अपेक्षित कंसोल आउटपुट**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

यह आउटपुट आपको ठीक‑ठीक बताता है कि कोड चलाने वाली मशीन पर कौन‑से फ़ॉन्ट्स लापता हैं। अब आप तय कर सकते हैं कि लापता फ़ॉन्ट्स इंस्टॉल करें, उन्हें दस्तावेज़ में एम्बेड करें, या प्रतिस्थापन को जैसा है वैसा रखें।

![Console output showing aspose font substitution warnings](/images/aspose-font-substitution-console.png)

*छवि वैकल्पिक पाठ:* aspose फ़ॉन्ट प्रतिस्थापन – कंसोल आउटपुट जिसमें प्रतिस्थापित फ़ॉन्ट्स की सूची है

## चरण 4 – वैकल्पिक: प्रतिस्थापन व्यवहार को कस्टमाइज़ करें (लापता फ़ॉन्ट्स को हैंडल करें)

कभी‑कभी आप सिर्फ यह जानना नहीं चाहते कि *किसी* फ़ॉन्ट का प्रतिस्थापन हुआ, बल्कि आप यह नियंत्रित करना चाहते हैं कि *कैसे* हुआ। Aspose.Words आपको एक कस्टम `IFontSubstitutionRule` रजिस्टर करने की सुविधा देता है। नीचे एक त्वरित उदाहरण है जो किसी भी लापता फ़ॉन्ट को `Tahoma` पर फॉलबैक करने के लिए मजबूर करता है।

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**आप इसे कब उपयोग करेंगे?**  
यदि आप वेब सर्विस के लिए PDFs जेनरेट कर रहे हैं और आपको पता है कि हर क्लाइंट `Tahoma` रेंडर कर सकता है, तो फॉलबैक को मजबूर करने से विज़ुअल कंसिस्टेंसी सुनिश्चित होती है, बिना कई फ़ॉन्ट फ़ाइलें शिप किए।

## पूर्ण कार्यशील उदाहरण (सभी चरणों का संयोजन)

यहाँ पूरा प्रोग्राम है जिसे आप नई कंसोल प्रोजेक्ट में पेस्ट कर सकते हैं। यह जैसा है वैसा ही कंपाइल हो जाएगा, बशर्ते आपने Aspose.Words NuGet पैकेज इंस्टॉल किया हो।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

प्रोग्राम चलाएँ, कंसोल देखें, और आपको हर लापता‑फ़ॉन्ट इवेंट प्रिंट होते दिखेंगे। इसके बाद आप तय कर सकते हैं कि फ़ॉन्ट्स इंस्टॉल करें, एम्बेड करें, या फॉलबैक रखें।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या यह PDF रूपांतरण के साथ काम करता है?**  
हाँ। जब आप बाद में `doc.Save("output.pdf")` कॉल करेंगे, तो लोडिंग के दौरान प्रतिस्थापित किए गए फ़ॉन्ट्स ही PDF में एम्बेड होंगे। इसलिए चेतावनियों को पहले पकड़ना आपको अंतिम PDF में आश्चर्यजनक फ़ॉन्ट बदलावों से बचाता है।

**प्रश्न: यदि मेरे पास कई दस्तावेज़ प्रोसेस करने हैं तो क्या करें?**  
लोडिंग लॉजिक को `try‑catch` ब्लॉक में रखें और कई दस्तावेज़ों में एक ही `FontSettings` इंस्टेंस को पुनः उपयोग करें। इससे ओवरहेड कम होता है और प्रत्येक फ़ाइल के लिए चेतावनी कलेक्टर सक्रिय रहता है।

**प्रश्न: क्या मैं चेतावनियों को पूरी तरह से दबा सकता हूँ?**  
आप `loadOptions.WarningCallback = null;` सेट करके लोडिंग से पहले चेतावनियों को बंद कर सकते हैं, लेकिन इससे **लापता फ़ॉन्ट्स का पता लगाना** संभव नहीं रहेगा—जो आमतौर पर आपका लक्ष्य नहीं होता।

## निष्कर्ष

हमने **aspose font substitution** को पूरी तरह से समझने के लिए सभी आवश्यक कदम कवर किए: डायग्नोस्टिक कलेक्टर को सक्षम करना, कस्टम **फ़ॉन्ट सेटिंग्स** के साथ Word फ़ाइल लोड करना, लापता फ़ॉन्ट्स की सूची निकालना, और यहाँ तक कि डिफ़ॉल्ट प्रतिस्थापन नियम को ओवरराइड करके **लापता फ़ॉन्ट्स** को अपनी इच्छा अनुसार हैंडल करना। कुछ ही C# लाइनों से आप उन फ़ॉन्ट समस्याओं पर पूरी नज़र रख सकते हैं, जो अन्यथा सूक्ष्म लेआउट बदलावों के पीछे छिपी रहती हैं।

अगला कदम? `FontSettings.SetFontsFolder` के साथ मूल फ़ॉन्ट्स को दस्तावेज़ में एम्बेड करने की कोशिश करें या `FontSourceBase` का उपयोग करके फ़ॉन्ट्स को डेटाबेस से लोड करें। आप `Document.BuiltInStyle` कलेक्शन के साथ प्रयोग करके देख सकते हैं कि स्टाइल‑लेवल फ़ॉन्ट बदलाव कैसे प्रसारित होते हैं।

Aspose.Words या फ़ॉन्ट मैनेजमेंट के बारे में और सवाल हैं? टिप्पणी छोड़ें, आधिकारिक Aspose दस्तावेज़ देखें, या नई प्रोजेक्ट बनाकर ऊपर दिया गया कोड आज़माएँ। खुशहाल कोडिंग, और आपके दस्तावेज़ हमेशा इच्छित रूप में रेंडर हों!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}