---
category: general
date: 2026-04-10
description: Aspose.Words में LoadOptions का उपयोग करके दस्तावेज़ लोड करते समय फ़ॉन्ट
  प्रतिस्थापन चेतावनियों को कैसे कैप्चर करें। एक चरण‑दर‑चरण C# समाधान के साथ पूर्ण
  कोड उदाहरण सीखें।
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: hi
og_description: Aspose.Words में LoadOptions का उपयोग करके दस्तावेज़ लोड करते समय
  फ़ॉन्ट प्रतिस्थापन चेतावनियों को कैसे कैप्चर करें। यह गाइड आपको पूरी C# कार्यान्वयन
  के माध्यम से ले जाता है।
og_title: Aspose.Words में LoadOptions का उपयोग कैसे करें – पूर्ण C# गाइड
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Aspose.Words में LoadOptions का उपयोग कैसे करें – पूर्ण C# गाइड
url: /hi/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words में LoadOptions का उपयोग कैसे करें – पूर्ण C# गाइड

LoadOptions का उपयोग कैसे करें, यह अक्सर एक बाधा बन जाता है जब आपको दस्तावेज़ लोडिंग पर कड़ी नियंत्रण चाहिए। इस ट्यूटोरियल में हम आपको बिल्कुल **LoadOptions का उपयोग कैसे करें** दिखाएंगे ताकि फ़ॉन्ट‑सबस्टीट्यूशन चेतावनियों को पकड़ सकें और उन्हें C# में संभाल सकें।

यदि आपने कभी कोई DOCX खोला है जिसमें कोई गायब फ़ॉन्ट रेफ़रेंस था और आउटपुट अजीब दिख रहा था, तो आप सही जगह पर हैं। हम पूरी प्रक्रिया को समझाएंगे, `LoadOptions` इंस्टेंस बनाने से लेकर कंसोल पर चेतावनी विवरण प्रिंट करने तक। अंत तक आपके पास एक तैयार‑से‑चलाने वाला स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

## आप क्या सीखेंगे

- विश्वसनीय दस्तावेज़ आयात के लिए `LoadOptions` क्यों महत्वपूर्ण है।  
- **WarningCallback** को कैसे प्लग‑इन करें जो विशेष रूप से **फ़ॉन्ट सब्स्टीट्यूशन चेतावनियों** को देखता है।  
- इन विकल्पों को सक्षम करके Word फ़ाइल लोड करने के लिए आवश्यक सटीक कोड।  
- किनारे के मामलों को संभालने के टिप्स, जैसे कि कई गायब फ़ॉन्ट वाले दस्तावेज़।  

कोई बाहरी दस्तावेज़ आवश्यक नहीं—सब कुछ यहाँ उपलब्ध है।

## पूर्वापेक्षाएँ

| आवश्यकता | कारण |
|-------------|--------|
| .NET 6.0 या बाद का संस्करण | उदाहरणों में उपयोग किए गए C# 10 सिंटैक्स के लिए रनटाइम प्रदान करता है। |
| Aspose.Words for .NET (नवीनतम संस्करण) | वह लाइब्रेरी जो `LoadOptions` और चेतावनी इन्फ्रास्ट्रक्चर देती है। |
| एक DOCX फ़ाइल जिसमें ऐसे फ़ॉन्ट रेफ़रेंस हों जो आपके सिस्टम में स्थापित नहीं हैं | चेतावनी कॉलबैक को क्रियाशील देखना। |
| Visual Studio 2022 (या कोई भी पसंदीदा IDE) | डिबगिंग और टेस्टिंग को सरल बनाता है। |

यदि आपके पास ये सब हैं, तो चलिए शुरू करते हैं।

## चरण 1 – LoadOptions ऑब्जेक्ट बनाएं और WarningCallback को जोड़ें

जब आप **LoadOptions का उपयोग कैसे करें** तो पहला कदम इसे इंस्टैंशिएट करना है। महत्वपूर्ण भाग `WarningCallback` को एक डेलीगेट असाइन करना है। यह डेलीगेट हर बार फायर होता है जब Aspose.Words ऐसी स्थिति का सामना करता है जिसे वह आपको बताना चाहता है—मुख्यतः, एक गायब फ़ॉन्ट।

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**यह क्यों महत्वपूर्ण है:** कॉलबैक के बिना, Aspose.Words चुपचाप गायब फ़ॉन्ट को डिफ़ॉल्ट फ़ॉन्ट से बदल देता है, और आपको दृश्य परिवर्तन का पता नहीं चलता। `WarningCallback` रजिस्टर करके, आपको हर सब्स्टीट्यूशन का रीयल‑टाइम लॉग मिलता है, जो गुणवत्ता‑सुनिश्चित दस्तावेज़ पाइपलाइन के लिए आवश्यक है।

## चरण 2 – केवल फ़ॉन्ट सब्स्टीट्यूशन चेतावनियों पर प्रतिक्रिया दें

आप सोच सकते हैं कि क्या कॉलबैक आपको अनावश्यक चेतावनियों (जैसे डिप्रिकेटेड फीचर) से भर देगा। उत्तर *हां* है—पर हम उन्हें फ़िल्टर कर सकते हैं। ऊपर के स्निपेट में हमने पहले ही `args.WarningType == WarningType.FontSubstitution` की जाँच की है। वह लाइन **फ़ॉन्ट सब्स्टीट्यूशन चेतावनी** गार्ड है, एक द्वितीयक कीवर्ड जो आउटपुट को केंद्रित रखता है।

यदि आपको अन्य चेतावनी प्रकारों को संभालना है, तो बस `if` ब्लॉक को विस्तारित करें:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

यह पैटर्न दिखाता है कि **warningcallback** मैकेनिज़्म कितना लचीला है, जिससे आप ठीक वही परिदृश्य संभाल सकते हैं जिनकी आपको परवाह है।

## चरण 3 – कॉन्फ़िगर किए गए LoadOptions के साथ अपना दस्तावेज़ लोड करें

अब जब लिस्नर तैयार है, अंतिम कदम `LoadOptions` इंस्टेंस को `Document` कंस्ट्रक्टर में पास करना है। यही वह क्षण है जहाँ **Aspose.Words LoadOptions उदाहरण** वास्तव में चमकता है।

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**आप क्या देखेंगे:** यदि DOCX में ऐसा फ़ॉन्ट रेफ़रेंस है जो मशीन पर स्थापित नहीं है, तो कंसोल में इस तरह की लाइन प्रिंट होगी:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

यह आउटपुट पुष्टि करता है कि आपने सफलतापूर्वक **LoadOptions का उपयोग कैसे करें** को फ़ॉन्ट समस्याओं की निगरानी के लिए लागू किया है।

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

नीचे पूरा प्रोग्राम है जिसे आप तुरंत कंपाइल और रन कर सकते हैं। यह तीनों चरणों को जोड़ता है, कुछ अतिरिक्त सौंदर्य (जैसे एक फ्रेंडली बैनर) जोड़ता है, और एरर हैंडलिंग को दर्शाता है।

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### अपेक्षित आउटपुट

यदि आप प्रोग्राम को ऐसे मशीन पर चलाते हैं जहाँ `input.docx` में रेफ़रेंस किया गया फ़ॉन्ट मौजूद नहीं है, तो आपको कुछ इस तरह मिलेगा:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

यदि सभी फ़ॉन्ट मौजूद हैं, तो आपको केवल सफलता संदेश दिखेंगे—कोई चेतावनी लाइन नहीं आएगी।

## सामान्य गलतियाँ और प्रो टिप्स

- **गलती:** `WarningCallback` सेट करना भूल जाना। कोड अभी भी लोड होगा, पर आप सब्स्टीट्यूशन विवरण नहीं देख पाएंगे।  
  **प्रो टिप:** `LoadOptions` बनाने के तुरंत बाद कॉलबैक असाइन करें; यह हल्का है और बाद में बहुत काम आता है।

- **गलती:** रिलेटिव पाथ का उपयोग करना जो गलत फ़ोल्डर की ओर इशारा करता है।  
  **प्रो टिप:** `Path.Combine(Environment.CurrentDirectory, "input.docx")` का उपयोग करके फ़ाइल लुकअप को अधिक मजबूत बनाएं।

- **गलती:** यह मान लेना कि चेतावनी लोड को रोक देगी।  
  **प्रो टिप:** फ़ॉन्ट सब्स्टीट्यूशन चेतावनियाँ *सूचनात्मक* होती हैं; वे लोड को एबॉर्ट नहीं करतीं। यदि आपको कड़ी वैधता चाहिए, तो सब्स्टीट्यूशन होने पर कॉलबैक के भीतर एक्सेप्शन थ्रो करें।

- **गलती:** सर्वर पर कोई फ़ॉन्ट नहीं स्थापित होने पर चलाना (जैसे मिनिमल Docker इमेज)।  
  **प्रो टिप:** आवश्यक फ़ॉन्ट पहले से इंस्टॉल करें या उन्हें अपने ऐप के साथ बंडल करें, फिर प्रोडक्शन में कोई सब्स्टीट्यूशन न हो, यह कॉलबैक से सत्यापित करें।

## LoadOptions बनाम पोस्ट‑लोड निरीक्षण कब उपयोग करें

आप पूछ सकते हैं, “लोड के बाद दस्तावेज़ की जाँच क्यों नहीं करते?” उत्तर प्रदर्शन और शुद्धता में है। लोड के **दौरान** चेतावनियों को संभालकर आप समस्याओं को जल्दी पकड़ लेते हैं—लेआउट गणना या PDF रूपांतरण से पहले। यह विशेष रूप से बैच प्रोसेसिंग पाइपलाइन में मूल्यवान है जहाँ हर अतिरिक्त कदम समय जोड़ता है।

## उदाहरण का विस्तार: सभी सब्स्टीट्यूटेड फ़ॉन्ट की रिपोर्ट सहेजना

यदि आपको स्थायी रिकॉर्ड चाहिए (शायद अनुपालन के लिए), तो कॉलबैक को संशोधित करके संदेशों को एक लिस्ट में इकट्ठा करें और लोडिंग के बाद फ़ाइल में लिखें:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

अब आपके पास कंसोल फ़ीडबैक के साथ-साथ एक टिकाऊ लॉग भी है।

## आप अगला कौन‑सा टॉपिक एक्सप्लोर कर सकते हैं

- **Aspose.Words में कस्टम फ़ॉन्ट एम्बेड करने का तरीका** – सब्स्टीट्यूशन को पूरी तरह समाप्त करता है।  
- **LoadOptions का उपयोग करके दस्तावेज़ आकार सीमित करना** – दुर्भावनापूर्ण बड़े फ़ाइलों से बचाव में मदद करता है।  
- **Word को PDF में परिवर्तित करना जबकि टाइपोग्राफी संरक्षित रहे** – चेतावनी‑कॉलबैक दृष्टिकोण के साथ अच्छी तरह मेल खाता है।  

इनमें से प्रत्येक `LoadOptions` के साथ स्थापित बुनियाद पर आगे का निर्माण करता है।

## निष्कर्ष

हमने **Aspose.Words में LoadOptions का उपयोग कैसे करें** को शुरुआत से अंत तक कवर किया: विकल्प बनाना, एक `WarningCallback` जोड़ना जो **फ़ॉन्ट सब्स्टीट्यूशन चेतावनियों** पर केंद्रित हो, और आत्मविश्वास के साथ दस्तावेज़ लोड करना। पूर्ण उदाहरण बॉक्स से बाहर चलाने योग्य है, और अतिरिक्त टिप्स सामान्य जालों से बचने में मदद करेंगे।  

बिना झिझक प्रयोग करें—कॉलबैक को अन्य चेतावनी प्रकारों के लिए बदलें, डेटाबेस में लॉग करें, या इसे वेब सर्विस में इंटीग्रेट करें जो अपलोड किए गए Word फ़ाइलों को वैधता देता है। यह पैटर्न लचीला, विश्वसनीय, और सबसे महत्वपूर्ण, आपको छिपी फ़ॉन्ट‑सब्स्टीट्यूशन प्रक्रिया पर दृश्यता देता है जो अन्यथा आपके दस्तावेज़ रेंडरिंग को बिगाड़ सकता है।

कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा इच्छित रूप में रेंडर हों! 

![LoadOptions के साथ चेतावनी कॉलबैक उपयोग प्रवाह दिखाने वाला आरेख](https://example.com/images/loadoptions-flow.png "LoadOptions का उपयोग कैसे करें आरेख")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}