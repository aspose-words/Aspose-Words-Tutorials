---
category: general
date: 2026-10-13
description: C# का उपयोग करके दस्तावेज़ में फ़ॉन्ट प्रतिस्थापन सीखें। यह गाइड दिखाता
  है कि कैसे बिग5 एन्कोडिंग सेट करें, DOCX लोड करें, और पुरानी फ़ॉन्ट्स को आधुनिक
  फ़ॉन्ट्स से बदलें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: hi
lastmod: 2026-10-13
og_description: दस्तावेज़ में फ़ॉन्ट प्रतिस्थापन लेगेसी चीनी फ़ाइलों के साथ काम करते
  समय आवश्यक है। इस चरण-दर-चरण ट्यूटोरियल का पालन करके बिग5 एन्कोडिंग वाले DOCX को
  लोड करें और पुराने फ़ॉन्ट को बदलें।
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: C# के साथ दस्तावेज़ में फ़ॉन्ट प्रतिस्थापन – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: C# के साथ दस्तावेज़ में फ़ॉन्ट प्रतिस्थापन कैसे करें
url: /hi/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ में फ़ॉन्ट प्रतिस्थापन – पूर्ण C# ट्यूटोरियल

यदि आपको **font substitution in document** की आवश्यकता है ताकि लेगेसी चीनी फ़ाइलें सही ढंग से रेंडर हों, तो यह गाइड आपको बिल्कुल बताता है कि इसे कैसे करें। उचित टेक्स्ट एन्कोडिंग को कॉन्फ़िगर करके और पुराने फ़ॉन्ट को आधुनिक फ़ॉन्ट से बदलकर, आप सुनिश्चित करते हैं कि अंतिम DOCX इच्छित रूप में प्रदर्शित हो।

डॉक्यूमेंट प्रोसेसिंग अक्सर तब टूट जाता है जब स्रोत में **big5** जैसी पुरानी एन्कोडिंग का उपयोग किया जाता है या ऐसा फ़ॉन्ट संदर्भित किया जाता है जो सिस्टम में अब मौजूद नहीं है। यह ट्यूटोरियल आपको सही **big5 encoding** के साथ DOCX लोड करने, **legacy font replacement** लागू करने, और एक साफ़ आउटपुट उत्पन्न करने के चरणों से ले जाता है जो किसी भी Windows मशीन पर काम करता है।

आप सीखेंगे:

* कैसे `LoadOptions` ऑब्जेक्ट को **big5 encoding** के साथ बनाया जाए।  
* कैसे **C# LoadOptions** का उपयोग करके DOCX फ़ाइल खोली जाए।  
* कैसे पुराने फ़ॉन्ट को आधुनिक समकक्ष से मैप करके **font substitution in document** किया जाए।  
* गायब फ़ॉन्ट्स और कई फ़ॉन्ट फ़ैमिलीज़ के लिए एज‑केस हैंडलिंग।

Aspose.Words for .NET लाइब्रेरी के अलावा कोई बाहरी टूल आवश्यक नहीं है, और पूरा कोड कॉन्सोल प्रोजेक्ट में कॉपी करके तुरंत चलाया जा सकता है।

## आवश्यकताएँ

* .NET 6.0 या बाद का संस्करण (उदाहरण में .NET 6 कॉन्सोल सिंटैक्स का उपयोग किया गया है)।  
* Aspose.Words for .NET – `dotnet add package Aspose.Words` के माध्यम से इंस्टॉल करें।  
* **big5 encoding** के साथ सहेजी गई DOCX फ़ाइल जो लेगेसी फ़ॉन्ट `MingLiU-ExtB` को संदर्भित करती है।  
* C# और Visual Studio या आपके पसंद के किसी भी IDE की बुनियादी जानकारी।

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेसेस इम्पोर्ट करें

एक नया कॉन्सोल एप्लिकेशन बनाएं और आवश्यक `using` निर्देश जोड़ें। यह सुनिश्चित करता है कि कोड बिना अतिरिक्त संशोधनों के कम्पाइल हो।

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Pro tip:** `Main` मेथड को न्यूनतम रखें; यह पठनीयता को बढ़ाता है और ट्यूटोरियल को फॉलो करना आसान बनाता है।

## चरण 2: सही टेक्स्ट एन्कोडिंग (परम्परागत चीनी के लिए big5) के साथ लोड विकल्प निर्धारित करें

`LoadOptions` क्लास Aspose.Words को बताती है कि स्रोत फ़ाइल में रॉ बाइट्स को कैसे व्याख्या किया जाए। **big5 encoding** का उपयोग परम्परागत चीनी अक्षरों के लिए महत्वपूर्ण है जो उस लेगेसी कोड पेज के साथ सहेजे गए थे।

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Why this matters:** यदि आप एन्कोडिंग को छोड़ देते हैं या डिफ़ॉल्ट UTF‑8 का उपयोग करते हैं, तो अक्षर गड़बड़ प्रतीकों (mojibake) के रूप में दिख सकते हैं। `big5` निर्दिष्ट करने से किसी भी फ़ॉन्ट प्रतिस्थापन से पहले मूल ग्लिफ़ संरक्षित रहते हैं।

## चरण 3: निर्दिष्ट एन्कोडिंग का उपयोग करके DOCX फ़ाइल लोड करें

`loadOptions` इंस्टेंस को `Document` कंस्ट्रक्टर में पास करें। यह फ़ाइल को लोड करता है जबकि आपने पहले परिभाषित **document encoding for Chinese** का सम्मान करता है।

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

यदि फ़ाइल नहीं मिलती है, तो प्रोग्राम `FileNotFoundException` फेंकेगा। सुनिश्चित करें कि पाथ सही है और एप्लिकेशन के पास पढ़ने की अनुमति है।

## चरण 4: लेगेसी फ़ॉन्ट को आधुनिक समकक्ष से बदलें

कई पुराने चीनी दस्तावेज़ `MingLiU-ExtB` को संदर्भित करते हैं, जो नए Windows इंस्टॉलेशन पर मौजूद नहीं हो सकता। इसे `Microsoft JhengHei` (एक व्यापक रूप से उपलब्ध यूनिकोड फ़ॉन्ट) से मैप करने से सही रेंडरिंग सुनिश्चित होती है।

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Explanation:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` एक ग्लोबल रिप्लेसमेंट नियम पंजीकृत करता है। जब भी Aspose.Words `MingLiU-ExtB` का सामना करता है, वह इसे `Microsoft JhengHei` से बदल देता है।  
* वैकल्पिक लूप मैपिंग को प्रिंट करता है, जो कई फ़ॉन्ट फ़ैमिली वाले बड़े दस्तावेज़ों में डिबगिंग के लिए उपयोगी है।

## चरण 5: प्रोसेस किए गए दस्तावेज़ को सहेजें

प्रतिस्थापन के बाद, दस्तावेज़ को नई फ़ाइल में लिखें। आउटपुट आधुनिक फ़ॉन्ट का उपयोग करके चीनी टेक्स्ट दिखाएगा, जिससे गायब‑ग्लिफ़ चेतावनियों को समाप्त किया जा सकेगा।

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

परिणामी फ़ाइल को Microsoft Word या किसी भी DOCX व्यूअर में खोलें; आपको `Microsoft JhengHei` के साथ परम्परागत चीनी अक्षर साफ़ तौर पर रेंडर होते दिखने चाहिए।

## किनारे के मामलों और सामान्य समस्याओं का समाधान

| स्थिति | सिफ़ारिश किया गया तरीका |
|-----------|----------------------|
| **स्रोत फ़ॉन्ट दस्तावेज़ में सूचीबद्ध नहीं है** | वाइल्डकार्ड पैटर्न के साथ `doc.FontInfos.Substitution.Add` का उपयोग करें, उदाहरण के लिए `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`। |
| **कई लेगेसी फ़ॉन्ट्स को बदलने की आवश्यकता है** | प्रत्येक जोड़ी के लिए `Add` कॉल करें, या कॉन्फ़िगरेशन फ़ाइल से एक सब्स्टिट्यूशन डिक्शनरी लोड करें। |
| **लक्षित फ़ॉन्ट लक्ष्य मशीन पर उपलब्ध नहीं है** | Windows के साथ आने वाला फ़ॉन्ट चुनें (जैसे, `Arial Unicode MS`) या `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll` का उपयोग करके फ़ॉन्ट एम्बेड करें। |
| **एन्कोडिंग त्रुटियां अभी भी दिखाई देती हैं** | सुनिश्चित करें कि स्रोत फ़ाइल वास्तव में **big5** का उपयोग करती है; आप फ़ाइल को हेक्स एडिटर से देख सकते हैं या `File.ReadAllBytes` का उपयोग करके बाइट पैटर्न की तुलना कर सकते हैं। |

## पूर्ण कार्यशील उदाहरण

नीचे पूर्ण, स्व-निहित प्रोग्राम दिया गया है। इसे `Program.cs` में कॉपी करें, फ़ाइल पाथ को समायोजित करें, और चलाएँ।

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Expected result:** `big5_doc_fixed.docx` खोलने पर सभी परम्परागत चीनी अक्षर सही ढंग से रेंडर होते दिखेंगे, बिना किसी गायब‑ग्लिफ़ चेतावनी के, क्योंकि `MingLiU-ExtB` को `Microsoft JhengHei` से बदल दिया गया है।

## निष्कर्ष

अब आपके पास C# का उपयोग करके **font substitution in document** कार्यों के लिए एक विश्वसनीय विधि है। **big5 encoding** को कॉन्फ़िगर करके, `LoadOptions` के साथ DOCX लोड करके, और लेगेसी फ़ॉन्ट्स को आधुनिक समकक्षों से मैप करके, आप पुराने चीनी फ़ाइलों में होने वाली रेंडरिंग समस्याओं को समाप्त कर देते हैं।

अब आप कर सकते हैं:

* सबसे अतिरिक्त लेगेसी फ़ॉन्ट्स को कवर करने के लिए सब्स्टिट्यूशन मैप को विस्तारित करें।  
* दस्तावेज़ों के बैच के लिए प्रक्रिया को स्वचालित करें (डायरेक्टरी पर लूप)।  
* फ़ॉन्ट प्रतिस्थापन को अन्य दस्तावेज़ रूपांतरण जैसे वॉटरमार्किंग या PDF रूपांतरण के साथ संयोजित करें।

विभिन्न लक्ष्य फ़ॉन्ट्स के साथ प्रयोग करने या पूर्ण पोर्टेबिलिटी के लिए कस्टम फ़ॉन्ट्स एम्बेड करने में संकोच न करें। यदि आपको कोई समस्या आती है, तो ऊपर दी गई किनारे के मामलों की तालिका को फिर से देखें या उन्नत फ़ॉन्ट हैंडलिंग के लिए Aspose.Words दस्तावेज़ीकरण देखें।

कोडिंग का आनंद लें!

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words में फ़ॉन्ट प्रतिस्थापन चेतावनियों को सक्षम करें – पूर्ण गाइड](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [फ़ॉन्ट प्रतिस्थापन चेतावनियों को लॉग करें – पूर्ण Aspose.Words गाइड](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [वर्ड दस्तावेज़ में एन्कोडिंग के साथ लोड करें](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}