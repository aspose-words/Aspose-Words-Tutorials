---
category: general
date: 2026-03-14
description: Aspose.Words के साथ गायब फ़ॉन्ट्स को जल्दी संभालें। फ़ॉन्ट प्रतिस्थापन
  चेतावनियों को कैसे कैप्चर करें, LoadOptions को कैसे कॉन्फ़िगर करें, और रेंडरिंग
  समस्याओं से बचें, यह सीखें।
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: hi
og_description: Aspose.Words में लापता फ़ॉन्ट्स को एक चेतावनी संग्रहकर्ता का उपयोग
  करके संभालें। यह ट्यूटोरियल चरण‑दर‑चरण दिखाता है कि फ़ॉन्ट प्रतिस्थापन को कैसे पता
  करें और लॉग करें।
og_title: Aspose.Words में गायब फ़ॉन्ट्स को संभालें – पूर्ण C# गाइड
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Aspose.Words में लापता फ़ॉन्ट्स को संभालें – पूर्ण C# गाइड
url: /hi/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में गायब फ़ॉन्ट्स को संभालना – पूर्ण C# गाइड

क्या आपने कभी **गायब फ़ॉन्ट्स** को संभालते समय देखा है कि आपका PDF या इमेज आउटपुट क्यों बिगड़ रहा है? आप अकेले नहीं हैं। गायब फ़ॉन्ट फ़ाइलें एक चुपचाप समस्या पैदा करती हैं जो एक परिपूर्ण डिज़ाइन किए गए रिपोर्ट को गड़बड़ बना देती हैं।  

अच्छी खबर? Aspose.Words आपको फ़ॉन्ट‑सब्स्टिट्यूशन इवेंट्स को पकड़ने, उन्हें लॉग करने और यदि चाहें तो फॉलबैक फ़ॉन्ट से बदलने का साफ़ तरीका देता है। इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने योग्य उदाहरण के माध्यम से दिखाएंगे कि कैसे एक वार्निंग कलेक्टर सेट‑अप करें, उसे `LoadOptions` में जोड़ें, और ऐसे दस्तावेज़ को लोड करें जिसमें संभवतः गायब फ़ॉन्ट्स हों।

इस गाइड के अंत तक आप सक्षम होंगे:

* दस्तावेज़ लोडिंग के दौरान होने वाले प्रत्येक फ़ॉन्ट सब्स्टिट्यूशन का पता लगाना।  
* प्रत्येक गायब फ़ॉन्ट के लिए एक दोस्ताना कंसोल संदेश (या लॉगर) आउटपुट करना।  
* आवश्यकता पड़ने पर समाधान को फ़ॉन्ट बदलने के लिए विस्तारित करना।  

**पूर्वापेक्षाएँ** – आपको चाहिए:

* .NET 6.0 या बाद का (कोड .NET Core और .NET Framework के साथ भी काम करता है)।  
* Aspose.Words for .NET NuGet पैकेज (वर्तमान संस्करण 23.11)।  
* एक Word फ़ाइल जो जानबूझकर ऐसे फ़ॉन्ट को रेफ़रेंस करती है जो आपके सिस्टम में इंस्टॉल नहीं है – इसे हम `doc-with-missing-font.docx` कहेंगे।  

यदि आप पहले से C# से परिचित हैं और प्रोजेक्ट सेट‑अप कर चुके हैं, तो आप सीधे कोड पर जा सकते हैं। अन्यथा, पढ़ते रहें; हम पहले छोटे सेट‑अप चरणों को कवर करेंगे।

---

## क्यों गायब फ़ॉन्ट्स को संभालना महत्वपूर्ण है

जब Aspose.Words कोई दस्तावेज़ लोड करता है, तो वह प्रत्येक ग्लिफ़ को मशीन पर इंस्टॉल किए गए फ़ॉन्ट से मिलाने की कोशिश करता है। यदि वह सटीक फ़ॉन्ट नहीं ढूँढ़ पाता, तो वह चुपचाप सबसे नज़दीकी मिलान को सब्स्टिट्यूट कर देता है। यह सब्स्टिट्यूशन लाइन हाइट, कर्निंग बदल सकता है और यहाँ तक कि अक्षर भी गायब कर सकता है। `WarningType.FontSubstitution` इवेंट को कैप्चर करके आप **क्या** बदला गया और **क्यों** बदला गया, इसका स्पष्ट दृश्य प्राप्त करते हैं, जो निम्नलिखित के लिए आवश्यक है:

* ब्रांड स्थिरता बनाए रखना (आपका कॉर्पोरेट फ़ॉन्ट ठीक वैसा ही दिखना चाहिए जैसा डिज़ाइन किया गया है)।  
* PDF कन्वर्ज़न समस्याओं का डीबगिंग – अक्सर कारण एक गायब फ़ॉन्ट होता है।  
* स्वचालित दस्तावेज़ पाइपलाइन बनाना जहाँ आपको समस्याग्रस्त फ़ाइलों को मैन्युअल रिव्यू के लिए फ़्लैग करना पड़ता है।

अब “क्यों” स्पष्ट हो गया, चलिए **कैसे** पर आते हैं।

---

## चरण 1 – वार्निंग कलेक्टर सेट‑अप करें

सबसे पहले हमें एक ऑब्जेक्ट चाहिए जो Aspose.Words की वार्निंग्स को सुन सके। `DocumentWarnings` `IWarningCallback` को इम्प्लीमेंट करता है, जिससे लाइब्रेरी द्वारा वार्निंग उठाए जाने पर हम प्रतिक्रिया दे सकते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**क्या हो रहा है?**  
* `DocumentWarnings` कॉलबैक इंटरफ़ेस के चारों ओर एक हल्का रैपर है।  
* लैम्ब्डा `e.WarningType` की जाँच करता है ताकि हम असंबंधित वार्निंग्स (जैसे डिप्रिकेटेड फीचर्स) को अनदेखा कर सकें।  
* `e.WarningInfo` में गायब फ़ॉन्ट का नाम होता है, जिसे हम कंसोल पर प्रिंट करते हैं।  

*प्रो टिप*: प्रोडक्शन में `Console.WriteLine` को स्ट्रक्चर्ड लॉगर (Serilog, NLog) से बदलें—इससे आपको टाइमस्टैम्प और लॉग लेवल मुफ्त में मिलेंगे।

---

## चरण 2 – कलेक्टर को LoadOptions में जोड़ें

`LoadOptions` वह गेटकीपर है जो आप Aspose.Words से खोलते हर दस्तावेज़ के लिए उपयोग करते हैं। हमारे `fontWarnings` इंस्टेंस को उसकी `WarningCallback` प्रॉपर्टी में असाइन करके हम सुनिश्चित करते हैं कि लोड प्रक्रिया के दौरान कलेक्टर सक्रिय रहे।

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**LoadOptions क्यों उपयोग करें?**  
वार्निंग्स के अलावा, `LoadOptions` आपको पासवर्ड हैंडलिंग, एन्कोडिंग, और कस्टम रिसोर्स लोडिंग को नियंत्रित करने की सुविधा देता है। यहाँ हम केवल वार्निंग पक्ष पर ध्यान दे रहे हैं, लेकिन वही पैटर्न अन्य कॉलबैक्स के लिए भी काम करता है।

---

## चरण 3 – कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ लोड करें

अब हम अंततः दस्तावेज़ को मेमोरी में लाते हैं। यदि कोई फ़ॉन्ट गायब है, तो हमारा कलेक्टर फायर होगा और आप प्रत्येक सब्स्टिट्यूशन के लिए एक कंसोल लाइन देखेंगे।

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

यदि आप इस स्निपेट को ऐसे दस्तावेज़ के साथ चलाते हैं जो *Calibri Light* को रेफ़रेंस करता है जबकि आपके टेस्ट मशीन में केवल *Calibri* है, तो आपको इस प्रकार का आउटपुट मिलेगा:

```
Font 'Calibri Light' was substituted.
```

यही पूरी डिटेक्शन लूप है—सरल, फिर भी शक्तिशाली।

---

## चरण 4 – (वैकल्पिक) गायब फ़ॉन्ट्स को ज्ञात सब्स्टिट्यूट से बदलें

कभी‑कभी आप केवल समस्या को लॉग नहीं करना चाहते; आप चाहते हैं कि रेंडर किया गया आउटपुट सुसंगत दिखे, इसलिए एक फॉलबैक फ़ॉन्ट लागू करें। Aspose.Words आपको एक कस्टम `FontSettings` ऑब्जेक्ट प्रदान करने की अनुमति देता है जो गायब फ़ॉन्ट्स को किसी अन्य फ़ॉन्ट से मैप करता है।

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**व्याख्या**  
* वाइल्डकार्ड `"*"` Aspose.Words को बताता है कि *किसी भी* गायब फ़ॉन्ट को समान तरीके से ट्रीट करें।  
* यदि आप अधिक सूक्ष्म नियंत्रण चाहते हैं तो आप विशिष्ट फ़ॉन्ट्स को व्यक्तिगत रूप से भी मैप कर सकते हैं।  
* `document.FontSettings` सेट करने के बाद, कोई भी बाद का रेंडरिंग (PDF, इमेज, HTML) इस सब्स्टिट्यूशन को मानता है।

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉन्सोल ऐप में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी आवश्यक `using` स्टेटमेंट्स, एरर हैंडलिंग, और स्पष्टता के लिए कमेंट्स शामिल हैं।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**अपेक्षित आउटपुट** (जब कोई फ़ॉन्ट गायब हो):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

यदि स्रोत दस्तावेज़ में पहले से सभी आवश्यक फ़ॉन्ट्स मौजूद हैं, तो वार्निंग लाइन नहीं आएगी—कोई चिंता नहीं।

---

## सामान्य प्रश्न एवं किनारी स्थितियाँ

| प्रश्न | उत्तर |
|----------|--------|
| **यदि मैं केवल लॉग करना चाहता हूँ, फ़ॉन्ट नहीं बदलना?** | `FontSettings` ब्लॉक को पूरी तरह छोड़ दें; केवल वार्निंग कलेक्टर पर्याप्त है। |
| **क्या मैं वार्निंग्स को फ़ाइल में रीडायरेक्ट कर सकता हूँ?** | हाँ—`Console.WriteLine` को `File.AppendAllText("font-warnings.log", …)` से बदलें। |
| **क्या यह DOC, DOCX, और ODT के लिए काम करता है?** | बिल्कुल। `LoadOptions` सभी फ़ॉर्मैट्स पर लागू होता है जो Aspose.Words सपोर्ट करता है। |
| **दस्तावेज़ में एम्बेडेड कस्टम फ़ॉन्ट्स के बारे में क्या?** | एम्बेडेड फ़ॉन्ट्स सब्स्टिट्यूशन मैकेनिज़्म को बायपास करते हैं; वे जैसा है वैसा ही उपयोग होते हैं। |
| **क्या इससे प्रदर्शन पर असर पड़ेगा?** | ओवरहेड न्यूनतम है—केवल प्रत्येक गायब फ़ॉन्ट पर एक कॉलबैक चलता है। बड़े बैच के लिए आप प्रत्येक इवेंट पर लिखने के बजाय वार्निंग्स को एग्रीगेट करने पर विचार कर सकते हैं। |

---

## निष्कर्ष

हमने दिखाया **कैसे Aspose.Words में गायब फ़ॉन्ट्स को संभालें** `DocumentWarnings` कलेक्टर को `LoadOptions` से जोड़कर, वैकल्पिक रूप से फॉलबैक फ़ॉन्ट सेट करके, और परिणाम को सेव करके। यह पैटर्न आपको फ़ॉन्ट‑सब्स्टिट्यूशन इवेंट्स की पूरी दृश्यता देता है, जिससे आप PDF, इमेज, या HTML कन्वर्ज़न में विज़ुअल फ़िडेलिटी बनाए रख सकते हैं।

अगले कदम जिन पर आप विचार कर सकते हैं:

* वार्निंग कलेक्टर को एक केंद्रीकृत लॉगिंग फ्रेमवर्क के साथ इंटीग्रेट करें।  
* एक UI डैशबोर्ड बनाएं जो गायब फ़ॉन्ट्स वाले दस्तावेज़ों की सूची दिखाए और बैच प्रोसेसिंग को सक्षम करे।  
* इस एप्रोच को Aspose.PDF के साथ मिलाकर सत्यापित करें कि जेनरेटेड PDFs वास्तव में फॉलबैक फ़ॉन्ट का उपयोग कर रहे हैं।  

बिना झिझक प्रयोग करें—`"Arial"` को `"Tahoma"` से बदलें या अलग दस्तावेज़ सेट लोड करें। मूल विचार वही रहता है: वार्निंग को कैप्चर करें, उस पर कार्रवाई करें, और अपने दस्तावेज़ों को ठीक वैसा ही रखें जैसा आप चाहते हैं।

कोडिंग का आनंद लें! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}