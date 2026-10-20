---
category: general
date: 2026-08-04
description: Aspose.Words का उपयोग करके C# में फुटनोट सेपरेटर बदलें – जानें कैसे फुटनोट
  सेपरेटर को संपादित करें और वर्ड दस्तावेज़ों में एंडनोट सेपरेटर बदलें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: hi
lastmod: 2026-08-04
og_description: Aspose.Words के साथ C# में फुटनोट सेपरेटर बदलें। यह गाइड आपको दिखाता
  है कि फुटनोट सेपरेटर को कैसे संपादित करें, एंडनोट सेपरेटर को कस्टमाइज़ करें, और
  अपडेटेड दस्तावेज़ को सहेजें।
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: C# में फुटनोट सेपरेटर बदलें – पूर्ण Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Aspose.Words का उपयोग करके C# में फुटनोट सेपरेटर बदलें
url: /hi/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में फुटनोट सेपरेटर बदलें Aspose.Words का उपयोग करके

यदि आपको Word दस्तावेज़ में **फुटनोट सेपरेटर बदलना** है, तो यह ट्यूटोरियल Aspose.Words for .NET के साथ सटीक चरणों को दिखाता है। चाहे आप डिफ़ॉल्ट लाइन को किसी प्रतीक से बदलना चाहते हों, या एंडनोट सेपरेटर पर अलग शैली लागू करना चाहते हों, नीचे दिया गया कोड पूरी प्रक्रिया को कवर करता है।

आप यह भी सीखेंगे कि **फुटनोट सेपरेटर को एडिट** कैसे करें और संबंधित **एंडनोट सेपरेटर बदलें** ऑपरेशन, ताकि वही दस्तावेज़ फुटनोट और एंडनोट दोनों के लिए समान स्टाइलिंग रख सके। कोई बाहरी टूल आवश्यक नहीं—सिर्फ कुछ ही पंक्तियों का C# कोड।

## आप क्या हासिल करेंगे

* एक मौजूदा *.docx* फ़ाइल लोड करें जिसमें फुटनोट और एंडनोट दोनों हों।  
* फुटनोट, फुटनोट कंटिन्यूएशन और एंडनोट के सेपरेटर नोड्स तक पहुँचें।  
* सेपरेटर कैरेक्टर को बदलें (उदाहरण के लिए, डिफ़ॉल्ट लाइन को एस्टेरिस्क `*` में बदलें)।  
* संशोधित दस्तावेज़ को सहेजें बिना किसी अन्य सामग्री को खोए।  

यह ट्यूटोरियल मानता है कि आपके पास C# की बुनियादी समझ है और आपने **Aspose.Words** NuGet पैकेज (संस्करण 24.9 या बाद का) इंस्टॉल किया हुआ है।

---

## पूर्वापेक्षाएँ

| आवश्यकता | कारण |
|-------------|--------|
| .NET 6.0+ or .NET Framework 4.7.2+ | Aspose.Words के लिए आवश्यक रनटाइम |
| Aspose.Words for .NET library | `Document` और `FootnoteOptions` APIs प्रदान करता है |
| एक इनपुट Word फ़ाइल (`input.docx`) जिसमें कम से कम एक फुटनोट या एंडनोट हो | सेपरेटर परिवर्तन को दर्शाता है |

आप अपने प्रोजेक्ट में Aspose.Words को निम्नलिखित CLI कमांड से जोड़ सकते हैं:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## चरण 1: फुटनोट वाले दस्तावेज़ को लोड करें

पहला ऑपरेशन स्रोत फ़ाइल को `Document` ऑब्जेक्ट में पढ़ना है। यह ऑब्जेक्ट मेमोरी में पूरे Word फ़ाइल का प्रतिनिधित्व करता है और आपको उसके सभी नोड्स तक पहुँच प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**यह क्यों महत्वपूर्ण है:** दस्तावेज़ को लोड करना किसी भी परिवर्तन का प्रारंभिक बिंदु है। यदि फ़ाइल नहीं मिलती, तो Aspose.Words `FileNotFoundException` फेंकता है, इसलिए आगे बढ़ने से पहले पथ सही है यह सुनिश्चित करें।

---

## चरण 2: फुटनोट और एंडनोट सेपरेटर नोड्स तक पहुँचें

`Document.FootnoteOptions` तीन सेपरेटर नोड्स प्रदान करता है:

* `Separator` – वह लाइन जो पहले पृष्ठ पर फुटनोट संग्रह के बाद दिखाई देती है।  
* `ContinuationSeparator` – वह लाइन जो तब उपयोग होती है जब फुटनोट अगले पृष्ठ पर जारी रहते हैं।  
* `EndnoteSeparator` – वह लाइन जो मुख्य टेक्स्ट को एंडनोट सूची से अलग करती है।

आप इन नोड्स को सामान्य `Node` ऑब्जेक्ट्स के रूप में प्राप्त करते हैं, फिर उन्हें `Run` में कास्ट करके टेक्स्ट संशोधित करते हैं।

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**यह क्यों महत्वपूर्ण है:** ये नोड्स ही वे एकमात्र स्थान हैं जहाँ विज़ुअल सेपरेटर कैरेक्टर मौजूद होता है। किसी अन्य नोड (जैसे सामान्य पैराग्राफ) को बदलने से फुटनोट फ़ॉर्मेटिंग पर असर नहीं पड़ेगा।

---

## चरण 3: फुटनोट सेपरेटर कैरेक्टर बदलें

सबसे सामान्य आवश्यकता डिफ़ॉल्ट लाइन को किसी प्रतीक जैसे एस्टेरिस्क (`*`) से बदलना है। चूँकि सेपरेटर `Run` के रूप में संग्रहीत है, आप सुरक्षित रूप से उसकी `Text` प्रॉपर्टी को संशोधित कर सकते हैं।

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**यह क्यों महत्वपूर्ण है:** `Run.Text` को सीधे संपादित करने से अंतिम दस्तावेज़ में विज़ुअल प्रतिनिधित्व अपडेट हो जाता है बिना अन्य फुटनोट सामग्री को प्रभावित किए। वही पैटर्न किसी भी स्ट्रिंग, जिसमें यूनिकोड प्रतीक भी शामिल हैं, को लागू करने के लिए इस्तेमाल किया जा सकता है।

---

## चरण 4: एंडनोट सेपरेटर बदलें (वैकल्पिक)

यदि आपको भी **एंडनोट सेपरेटर बदलना** है, तो प्रक्रिया फुटनोट परिवर्तन के समान है। `endnoteSeparator` के टेक्स्ट को अपनी इच्छित कैरेक्टर से बदलें।

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**यह क्यों महत्वपूर्ण है:** एंडनोट अक्सर फुटनोट से अलग शैली में होते हैं। अलग सेपरेटर प्रदान करने से आप अपने दस्तावेज़ के डिज़ाइन गाइडलाइन के साथ विज़ुअल संगतता बनाए रख सकते हैं।

---

## चरण 5: संशोधित दस्तावेज़ को सहेजें

सभी संशोधनों के बाद, `Document.Save` का उपयोग करके बदलावों को स्थायी बनाएं। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई जगह पर लिख सकते हैं।

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**यह क्यों महत्वपूर्ण है:** `Save` इन‑मेमोरी प्रतिनिधित्व को डिस्क पर लिखता है, सभी अन्य तत्वों (स्टाइल, इमेज, टेबल) को अपरिवर्तित रखता है।

---

## पूर्ण, चलाने योग्य उदाहरण

सभी भागों को मिलाकर, यहाँ एक स्व‑निहित कंसोल एप्लिकेशन है जो पूरी प्रक्रिया को दर्शाता है:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**अपेक्षित परिणाम:** Microsoft Word में *ModifiedSeparators.docx* खोलें। पहले फुटनोट पृष्ठ के नीचे की फुटनोट सेपरेटर लाइन अब एकल एस्टेरिस्क (`*`) होगी। यदि दस्तावेज़ में एंडनोट हैं, तो मुख्य टेक्स्ट को एंडनोट सूची से अलग करने वाली लाइन डैश (`-`) के रूप में दिखाई देगी। सभी अन्य सामग्री (टेक्स्ट, इमेज, टेबल) अपरिवर्तित रहती है।

---

## सामान्य प्रश्न और किनारे‑के‑केस हैंडलिंग

| प्रश्न | उत्तर |
|----------|--------|
| **यदि दस्तावेज़ में कोई फुटनोट नहीं है तो क्या होगा?** | `FootnoteOptions.Separator` अभी भी एक `Run` नोड लौटाता है, लेकिन उसका टेक्स्ट खाली हो सकता है। कोड संशोधित करने से पहले नोड प्रकार की सुरक्षित जाँच करता है। |
| **क्या मैं मल्टी‑कैरेक्टर स्ट्रिंग (जैसे "***") उपयोग कर सकता हूँ?** | हां। `Run.Text` प्रॉपर्टी किसी भी स्ट्रिंग को स्वीकार करती है, जिसमें यूनिकोड कैरेक्टर भी शामिल हैं। |
| **क्या सेपरेटर बदलने से मौजूदा फुटनोट नंबरिंग प्रभावित होगी?** | नहीं। सेपरेटर नंबरिंग स्कीम से स्वतंत्र है। |
| **क्या मुझे `Document` ऑब्जेक्ट को डिस्पोज़ करना चाहिए?** | `Document` `Node` के माध्यम से अप्रत्यक्ष रूप से `IDisposable` को लागू करता है। एक छोटे‑समय वाले कंसोल ऐप में यह वैकल्पिक है, लेकिन लंबी‑चलाने वाली सर्विसेज़ के लिए आप इसे `using` ब्लॉक में रख सकते हैं। |
| **यह .NET Core बनाम .NET Framework में कैसे काम करता है?** | API सभी रनटाइम्स में समान है; केवल लक्ष्य फ्रेमवर्क संस्करण मायने रखता है (जो Aspose.Words पैकेज द्वारा समर्थित होना चाहिए)। |

**प्रो टिप:** यदि आपको विभिन्न सेक्शन के लिए अलग‑अलग सेपरेटर लागू करने की आवश्यकता है, तो आप `doc.GetChildNodes(NodeType.Footnote, true)` पर इटरेट करके प्रत्येक फुटनोट की `Separator` प्रॉपर्टी को व्यक्तिगत रूप से समायोजित कर सकते हैं। यह अधिक उन्नत है लेकिन जटिल दस्तावेज़ों के लिए उपयोगी है।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for C# का उपयोग करके Word फ़ाइल में **फुटनोट सेपरेटर बदलें** और **एंडनोट सेपरेटर बदलें** कैसे किया जाता है। गाइड में दस्तावेज़ लोड करना, संबंधित सेपरेटर नोड्स तक पहुँचना, उनके टेक्स्ट को संशोधित करना, और परिणाम सहेजना—सब कुछ एक ही स्व‑निहित प्रोग्राम में कवर किया गया है।

अब आप संबंधित विषयों जैसे **फुटनोट सेपरेटर स्टाइल एडिट करें**, फुटनोट नंबरिंग को कस्टमाइज़ करना, या पेज लेआउट के आधार पर कंडीशनल फ़ॉर्मेटिंग लागू करना आदि का अन्वेषण कर सकते हैं। वही पैटर्न (नोड प्राप्त करना, `Run` में कास्ट करना, `Text` संशोधित करना) कई अन्य Word‑प्रोसेसिंग परिदृश्यों में काम करता है।

कोडिंग का आनंद लें, और विभिन्न प्रतीकों के साथ प्रयोग करने या यहाँ तक कि इमेज को सेपरेटर के रूप में एम्बेड करने में संकोच न करें, जिससे आपका दस्तावेज़ लेआउट वास्तव में अनोखा बन सके!

## आगे आप क्या सीख सकते हैं?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [फुटनोट और एंडनोट के साथ शब्द प्रोसेसिंग](/words/english/net/working-with-footnote-and-endnote/)
- [Word दस्तावेज़ में पैराग्राफ स्टाइल सेपरेटर प्राप्त करें](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Word में डॉक्यूमेंट स्टाइल सेपरेटर डालें](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}