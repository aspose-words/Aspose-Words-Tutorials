---
category: general
date: 2026-04-24
description: C# का उपयोग करके Aspose.Words में गायब फ़ॉन्ट्स के प्रतिस्थापन का पता
  कैसे लगाएँ। यह गाइड आपको FontSettings चेतावनियों के साथ गायब फ़ॉन्ट्स को विश्वसनीय
  रूप से संभालना दिखाता है।
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: hi
og_description: C# के साथ Aspose.Words में गायब फ़ॉन्ट्स के प्रतिस्थापन का पता कैसे
  लगाएँ। FontSettings चेतावनियों का उपयोग करके गायब फ़ॉन्ट्स को संभालना सीखें।
og_title: Aspose.Words में प्रतिस्थापन का पता कैसे लगाएँ – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Aspose.Words में प्रतिस्थापन का पता कैसे लगाएँ – लापता फ़ॉन्ट्स को संभालें
url: /hi/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में Substitution कैसे Detect करें – Missing Fonts को Handle करें

क्या आप कभी सोचते हैं **how to detect substitution** जब कोई दस्तावेज़ ऐसे फ़ॉन्ट का उपयोग करने की कोशिश करता है जो आपके सर्वर पर इंस्टॉल नहीं है? यह एक सामान्य समस्या है, विशेष रूप से जब आप स्वचालित पाइपलाइन में PDFs या Word फ़ाइलें जनरेट कर रहे होते हैं। अच्छी खबर यह है कि Aspose.Words आपको एक बिल्ट‑इन हुक देता है जिससे आप इस स्थिति को पहचान सकते हैं, और आप **handle missing fonts** को भी सहजता से कर सकते हैं।

इस ट्यूटोरियल में हम एक वास्तविक‑दुनिया का उदाहरण देखेंगे जो **how to detect substitution** को `FontSettings.Warning` इवेंट के माध्यम से दिखाता है, और हम बताएँगे कि **handle missing fonts** को बिना आपके प्रोसेसिंग फ्लो को तोड़े कैसे किया जाए। अंत तक आपके पास एक तैयार‑चलाने योग्य स्निपेट, प्रत्येक लाइन के महत्व की स्पष्ट समझ, और सामान्य pitfalls से बचने के लिए कुछ टिप्स होंगी।

## आवश्यकताएँ

- .NET 6.0 या बाद का (कोड .NET Framework पर भी काम करता है)  
- Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`) – संस्करण 23.11 या नया  
- एक सैंपल दस्तावेज़ जो ऐसे फ़ॉन्ट को संदर्भित करता है जो आपके सिस्टम में इंस्टॉल नहीं है (उदा., `MissingFont.docx`)  
- Visual Studio, VS Code, या कोई भी C# IDE जो आप पसंद करते हैं  

कोई अतिरिक्त कॉन्फ़िगरेशन आवश्यक नहीं है, केवल NuGet पैकेज जोड़ना पर्याप्त है।

---

## FontSettings के साथ Substitution कैसे Detect करें

मुख्य बात **how to detect substitution** `FontSettings.Warning` इवेंट में निहित है। जब Aspose.Words किसी अनुरोधित फ़ॉन्ट को नहीं ढूँढ पाता, तो वह `WarningType.FontSubstitution` चेतावनी उत्पन्न करता है। इस इवेंट को सब्सक्राइब करके आपको वास्तविक‑समय में सूचना मिलती है, जिसमें मूल फ़ॉन्ट नाम और फॉलबैक फ़ॉन्ट दोनों शामिल होते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**यह क्यों काम करता है:**  
- `LoadOptions.FontSettings` Aspose.Words को बताता है कि वह अभी‑ही‑बनाए गए `FontSettings` ऑब्जेक्ट का उपयोग करे।  
- `Warning` को सब्सक्राइब करने से आपको *सभी* फ़ॉन्ट‑संबंधी समस्याओं को एक ही जगह मॉनिटर करने का अवसर मिलता है, न कि केवल missing फ़ॉन्ट्स को।  
- `WarningType.FontSubstitution` फ़िल्टर सुनिश्चित करता है कि आप केवल वही सीनारियो पर प्रतिक्रिया दें जिसमें आप रुचि रखते हैं – अर्थात **how to detect substitution** का मूल सार।

### अपेक्षित आउटपुट

ऊपर दिया गया कोड ऐसे दस्तावेज़ के साथ चलाने पर जो गैर‑मौजूद फ़ॉन्ट को संदर्भित करता है, कुछ इस प्रकार प्रिंट करेगा:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

यदि दस्तावेज़ केवल इंस्टॉल किए गए फ़ॉन्ट्स का उपयोग करता है, तो कंसोल शांत रहता है – यह स्पष्ट संकेत है कि **how to detect substitution** बिना झूठी चेतावनियों के सफल रहा।

## Missing Fonts को Gracefully Handle करना

Substitution का पता लगाना केवल आधा काम है; आपको एक रणनीति भी चाहिए जिससे **handle missing fonts** किया जा सके ताकि अंतिम आउटपुट इच्छित रूप में दिखे। नीचे तीन व्यावहारिक दृष्टिकोण दिए गए हैं जिन्हें आप मिलाकर उपयोग कर सकते हैं।

### 1. Fallback Font फ़ोल्डर प्रदान करें

Aspose.Words अतिरिक्त डायरेक्टरीज़ में फ़ॉन्ट्स की खोज कर सकता है। एक ऐसे फ़ोल्डर की ओर इशारा करके जिसमें आप सबसे सामान्य फ़ॉन्ट्स रखेंगे, आप Substitution की संभावना को पूरी तरह से घटा सकते हैं।

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**क्यों:** जब मूल फ़ॉन्ट अनुपलब्ध हो, तो Aspose.Words के पास अब ज्ञात विकल्पों का सेट होता है, जिससे अक्सर अधिक पूर्वानुमेय दृश्य परिणाम मिलता है।

### 2. Missing Fonts को प्रोग्रामेटिकली बदलें

यदि आप पूर्ण नियंत्रण चाहते हैं, तो डिटेक्शन के बाद आप missing फ़ॉन्ट को किसी विशिष्ट फ़ॉन्ट से बदल सकते हैं।

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**क्यों:** यह इंजन को ठीक‑ठीक बताता है कि कौन से फ़ॉन्ट्स को आज़माना है, जिससे आप कॉर्पोरेट ब्रांडिंग या एक्सेसिबिलिटी मानकों को लागू कर सकते हैं।

### 3. लॉग करें और Abort करें (जब Substitution अस्वीकार्य हो)

कभी‑कभी missing फ़ॉन्ट का मतलब दस्तावेज़ आपके उपयोग केस के लिए अमान्य हो जाता है (जैसे, कानूनी फॉर्म)। ऐसे परिदृश्य में आप Substitution होते ही एक एक्सेप्शन फेंक सकते हैं।

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**क्यों:** तुरंत विफलता डाउनस्ट्रीम त्रुटियों को रोकती है, जैसे कि गलत‑संगठित टेबल्स या टूटे हुए सिग्नेचर।

## पूर्ण कार्यशील उदाहरण – सभी चरणों का संयोजन

नीचे एक एकल, कॉपी‑पेस्ट‑तैयार प्रोग्राम है जो **how to detect substitution** *और* कई तरीकों से **handle missing fonts** को दर्शाता है। आप अपनी आवश्यकता के अनुसार सेक्शन को टिप्पणी (comment) कर सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**क्या अपेक्षित है:**  
- यदि `MissingFont.docx` ऐसा फ़ॉन्ट संदर्भित करता है जो मशीन पर नहीं है, तो कंसोल substitution चेतावनी प्रिंट करेगा।  
- सहेजा गया `Processed.docx` आपके द्वारा कॉन्फ़िगर किए गए fallback फ़ॉन्ट (या लाइब्रेरी का डिफ़ॉल्ट) का उपयोग करेगा।  
- जब तक आप जानबूझकर substitution पर abort नहीं करते, तब तक कोई अनहैंडल्ड एक्सेप्शन नहीं आएगा।

## सामान्य प्रश्न एवं किनारी मामलों

| प्रश्न | उत्तर |
|----------|--------|
| *यदि दस्तावेज़ में कई missing फ़ॉन्ट्स हों तो क्या होगा?* | चेतावनी इवेंट प्रत्येक substitution के लिए फायर होता है, इसलिए आपको कई लाइनों का आउटपुट मिलेगा। आप इन्हें एक सूची में एकत्रित करके सारांश रिपोर्ट बना सकते हैं। |
| *क्या यह PDF कन्वर्ज़न के साथ काम करता है?* | बिल्कुल। वही `FontSettings` `doc.Save("out.pdf")` कॉल करने पर भी मान्य होते हैं। substitution चेतावनी अभी भी फायर होती है, जिससे आप PDF की दृश्य सटीकता की पुष्टि कर सकते हैं। |
| *क्या मैं दस्तावेज़ लोड होने के बाद substitution का पता लगा सकता हूँ?* | सीधे नहीं। चेतावनी **लोडिंग या सेविंग के दौरान** उठाई जाती है। यदि आपको पोस्ट‑लोड विश्लेषण चाहिए, तो लोड चरण के दौरान चेतावनियों को एक संग्रह में कैप्चर करें। |
| *DOCX में एम्बेडेड कस्टम फ़ॉन्ट्स के बारे में क्या?* | एम्बेडेड फ़ॉन्ट्स को मौजूद माना जाता है, इसलिए कोई substitution नहीं होता। यदि एम्बेडेड फ़ॉन्ट भ्रष्ट है, तो Aspose.Words फिर भी चेतावनी उठाता है, जिसे आप उसी तरह पकड़ सकते हैं। |
| *क्या इसका प्रदर्शन पर कोई असर पड़ता है?* | न्यूनतम। चेतावनी जाँच हल्की होती है; वास्तविक लागत दस्तावेज़ लोड करने में है। फ़ॉन्ट फ़ोल्डर जोड़ने से पहले लोड पर थोड़ा खोज समय बढ़ सकता है, लेकिन केवल पहली बार। |

## प्रो टिप्स और Pitfalls से बचें

- **Pro tip:** जब आप कई फ़ॉन्ट्स वाले फ़ोल्डर की ओर इशारा कर रहे हों, तो हमेशा `recursive: true` सेट करें; अन्यथा सब‑फ़ोल्डर अनदेखे रहेंगे।  
- **Watch out for:** Linux पर केस‑सेंसिटिविटी। Windows पर फ़ॉन्ट नाम केस‑इन्सेंसिटिव होते हैं, लेकिन Linux पर नहीं, इसलिए सटीक नाम उपयोग करें या दोनों वैरिएंट जोड़ें।  
- **Remember:** यदि आप कंटेनराइज़्ड वातावरण में चल रहे हैं, तो सुनिश्चित करें कि फ़ॉन्ट फ़ोल्डर इमेज का हिस्सा हो या रन‑टाइम पर माउंट किया गया हो।  
- **Tip:** यदि आपको अंत‑उपयोगकर्ताओं को सारांश प्रस्तुत करना है या मॉनिटरिंग सिस्टम में लॉग करना है, तो चेतावनियों को `List<string>` में संग्रहित करें।  

## निष्कर्ष

हमने Aspose.Words में missing फ़ॉन्ट्स की **how to detect substitution** को कवर किया, कई तरीकों से **handle missing fonts** दिखाए, और एक पूर्ण, चलाने योग्य उदाहरण प्रदान किया जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं। `FontSettings.Warning` इवेंट को उपयोग करके आप फ़ॉन्ट समस्याओं पर वास्तविक‑समय दृश्यता प्राप्त करते हैं, और fallback फ़ोल्डर या स्पष्ट प्रतिस्थापन नियमों के साथ आप अपने आउटपुट को ठीक‑ठीक वैसा ही रख सकते हैं जैसा आप चाहते हैं।

अगला कदम तैयार है? समाधान को इस तरह विस्तारित करें कि fallback फ़ॉन्ट को स्वचालित रूप से उत्पन्न PDF में एम्बेड किया जाए, या बड़े‑पैमाने पर दस्तावेज़ पाइपलाइन के लिए चेतावनी हैंडलर को केंद्रीकृत लॉगिंग सर्विस में जोड़ें। आज हमने जिन पैटर्न्स पर चर्चा की—इवेंट‑ड्रिवन डिटेक्शन, ग्रेसफ़ुल फॉलबैक, और स्पष्ट एरर हैंडलिंग—वे कई अन्य Aspose APIs पर भी लागू होते हैं, इसलिए अब आप फ़ॉन्ट‑संबंधी चुनौतियों को पूरी तरह से निपटा सकते हैं।

फ़ॉन्ट हैंडलिंग, PDF कन्वर्ज़न, या Aspose.Words के ट्रिक्स के बारे में और प्रश्न हैं? नीचे टिप्पणी करें, और कोडिंग का आनंद लें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}