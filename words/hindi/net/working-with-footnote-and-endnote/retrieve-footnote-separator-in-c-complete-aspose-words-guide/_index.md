---
category: general
date: 2026-08-07
description: Aspose.Words for .NET का उपयोग करके फुटनोट सेपरेटर प्राप्त करें। सीखें
  कि फुटनोट और एंडनोट सेपरेटर्स को कैसे निकालें, नोड प्रकारों की जाँच करें, और C#
  में उन्हें संशोधित करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: hi
lastmod: 2026-08-07
og_description: Aspose.Words for .NET के साथ फुटनोट सेपरेटर प्राप्त करें। यह गाइड
  दिखाता है कि फुटनोट और एंडनोट सेपरेटर कैसे निकालें, उनके नोड प्रकार कैसे जांचें,
  और परिवर्तन सहेजें।
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: C# में फुटनोट सेपरेटर प्राप्त करें – स्टेप बाय स्टेप Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: C# में फुटनोट विभाजक प्राप्त करें – पूर्ण Aspose.Words गाइड
url: /hi/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में फुटनोट सेपरेटर प्राप्त करें – पूर्ण Aspose.Words गाइड

यदि आपको Word दस्तावेज़ से **retrieve footnote separator** प्राप्त करना है, तो यह ट्यूटोरियल आपको Aspose.Words for .NET के साथ इसे कैसे करना है, बिल्कुल दिखाता है। चाहे आप एक दस्तावेज़‑प्रोसेसिंग सेवा बना रहे हों या फुटनोट फ़ॉर्मेटिंग को साफ़ कर रहे हों, आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो फुटनोट और एंडनोट दोनों सेपरेटर निकालता है।

इस गाइड में आप सीखेंगे कि कैसे `.docx` फ़ाइल लोड करें, `FootnoteSeparator` और `EndnoteSeparator` प्रॉपर्टी को कॉल करें, लौटाए गए `Node` ऑब्जेक्ट्स की जांच करें, और वैकल्पिक रूप से सेपरेटर लाइन को बदलें। कोई बाहरी दस्तावेज़ीकरण आवश्यक नहीं है—नीचे सब कुछ शामिल है।

## आवश्यकताएँ

* .NET 6.0 या बाद का (कोड .NET Framework 4.7.2 पर भी काम करता है)
* Aspose.Words for .NET NuGet पैकेज (संस्करण 24.9 या नया)
* एक Word दस्तावेज़ जिसमें फुटनोट और/या एंडनोट हों (उदाहरण के लिए `Footnotes.docx`)

आप निम्नलिखित CLI कमांड से Aspose.Words पैकेज जोड़ सकते हैं:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेस इम्पोर्ट करें

एक नया कंसोल प्रोजेक्ट बनाएं या कोड को मौजूदा प्रोजेक्ट में जोड़ें। आवश्यक `using` निर्देश नीचे सूचीबद्ध हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

ये नेमस्पेस आपको `Document` क्लास, `Node` हाइरार्की, और `NodeType` एनेमरेशन तक पहुंच प्रदान करते हैं जो **retrieve footnote separator** ऑपरेशन्स के लिए आवश्यक हैं।

## चरण 2: वह दस्तावेज़ लोड करें जिसमें फुटनोट और एंडनोट हों

किसी भी Aspose.Words वर्कफ़्लो में पहला ऑपरेशन स्रोत फ़ाइल को लोड करना है। प्लेसहोल्डर पाथ को अपनी `.docx` फ़ाइल के वास्तविक स्थान से बदलें।

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

फ़ाइल को लोड करने से आंतरिक नोड ट्री तैयार होती है, जो **retrieve footnote separator** के लिए आवश्यक है क्योंकि सेपरेटर नोड्स उस ट्री के भीतर होते हैं।

## चरण 3: फुटनोट सेपरेटर नोड प्राप्त करें

अब आप `Document` ऑब्जेक्ट की `FootnoteSeparator` प्रॉपर्टी को एक्सेस करके **retrieve footnote separator** कर सकते हैं। यह नोड फुटनोट को मुख्य बॉडी टेक्स्ट से अलग करने वाली लाइन को दर्शाता है।

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType` मानक सेपरेटर लाइन के लिए `Paragraph` होगा। नोड टाइप जानने से आपको यह तय करने में मदद मिलती है कि आपको सेपरेटर को संशोधित करना है या पूरी तरह बदलना है।

## चरण 4: एंडनोट सेपरेटर नोड प्राप्त करें

इसी तरह, आप `EndnoteSeparator` प्रॉपर्टी का उपयोग करके **retrieve endnote separator** कर सकते हैं। यह नोड एंडनोट को मुख्य सामग्री से अलग करता है।

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

अधिकांश दस्तावेज़ों में दोनों सेपरेटर नोड्स समान `NodeType` (`Paragraph`) साझा करते हैं, लेकिन उन्हें स्वतंत्र रूप से कस्टमाइज़ किया जा सकता है।

## चरण 5: सेपरेटर सामग्री की जांच या संशोधन करें (वैकल्पिक)

यदि आपको सेपरेटर की दृश्य उपस्थिति बदलनी है—जैसे डैश की लाइन को पतली रूल से बदलना—तो आप सीधे `Paragraph` नोड को संपादित कर सकते हैं। नीचे एक उदाहरण है जो डिफ़ॉल्ट सेपरेटर टेक्स्ट को कस्टम स्ट्रिंग से बदलता है।

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

नोड्स को संशोधित करने के बाद, आप दस्तावेज़ को सहेज सकते हैं ताकि परिवर्तन Word में दिखें।

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## अपेक्षित कंसोल आउटपुट

जब आप मूल `Footnotes.docx` के साथ प्रोग्राम चलाते हैं, तो आपको कुछ इस तरह दिखना चाहिए:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

यदि आप Microsoft Word में `Footnotes_Updated.docx` खोलते हैं, तो फुटनोट और एंडनोट सेपरेटर आपके द्वारा डाली गई कस्टम टेक्स्ट दिखाएंगे।

## सामान्य प्रश्न और किनारे के मामले

**यदि दस्तावेज़ में कोई फुटनोट नहीं है तो?**  
`FootnoteSeparator` प्रॉपर्टी अभी भी एक `Paragraph` नोड लौटाती है क्योंकि Word हमेशा एक सेपरेटर प्लेसहोल्डर शामिल करता है। नोड खाली होगा, इसलिए आप सुरक्षित रूप से सामग्री जोड़ सकते हैं या जैसा है वैसा छोड़ सकते हैं।

**क्या मैं किसी विशिष्ट सेक्शन के लिए सेपरेटर प्राप्त कर सकता हूँ?**  
फुटनोट और एंडनोट सेपरेटर पूरे दस्तावेज़ के लिए होते हैं, न कि सेक्शन‑विशिष्ट। यदि आपको सेक्शन‑स्तर का नियंत्रण चाहिए, तो आपको ग्लोबल सेपरेटर नोड्स के बजाय `Section.FootnoteOptions` और `Section.EndnoteOptions` के साथ काम करना होगा।

**क्या यह .NET Core के साथ काम करता है?**  
हां। Aspose.Words for .NET क्रॉस‑प्लेटफ़ॉर्म है, और वही कोड Windows, Linux, और macOS पर .NET 6+ के साथ चलता है।

**मैं किस नोड टाइप की अपेक्षा करूँ?**  
`FootnoteSeparator` और `EndnoteSeparator` दोनों एक `Paragraph` नोड (`NodeType.Paragraph`) लौटाते हैं। यदि आपको अलग प्रकार मिलता है, तो दस्तावेज़ भ्रष्ट हो सकता है, और आपको स्रोत फ़ाइल को पुनः लोड या वैधता जाँच करनी चाहिए।

## तेज़ कॉपी‑पेस्ट के लिए पूर्ण स्रोत कोड

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

कोड को `Program.cs` फ़ाइल में कॉपी करें, फ़ाइल पाथ को समायोजित करें, और `dotnet run` चलाएँ। यह प्रोग्राम पूर्ण **retrieve footnote separator** वर्कफ़्लो दिखाता है, दस्तावेज़ लोड करने से लेकर बदलावों को सहेजने तक।

## निष्कर्ष

अब आप Aspose.Words for .NET का उपयोग करके **retrieve footnote separator** और **endnote separator retrieval** करना जानते हैं, उनके `document node type` की जांच कर सकते हैं, और वैकल्पिक रूप से उनकी सामग्री बदल सकते हैं। यह तकनीक आपको फुटनोट फ़ॉर्मेटिंग को स्वचालित करने, कस्टम सेपरेटर लाइन्स बनाने, या किसी भी C# एप्लिकेशन में दस्तावेज़ संरचना को वैध करने की अनुमति देती है।

अगले चरण में, आप संबंधित विषयों का अन्वेषण कर सकते हैं जैसे व्यक्तिगत फुटनोट टेक्स्ट के लिए **C# footnote extraction**, या `FootnoteOptions` का उपयोग करके **footnote reference marks** को **modify** करना सीख सकते हैं। दोनों अवधारणाएँ यहाँ कवर किए गए नोड‑ट्री मूलभूत सिद्धांतों पर सीधे आधारित हैं।

कोडिंग का आनंद लें, और विभिन्न सेपरेटर शैलियों के साथ प्रयोग करने में संकोच न करें ताकि वे आपके प्रोजेक्ट की ब्रांडिंग से मेल खाएँ!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [फुटनोट और एंडनोट के साथ शब्द प्रोसेसिंग](/words/english/net/working-with-footnote-and-endnote/)
- [Aspose.Words for .NET में Document Builder का उपयोग करके सामग्री जोड़ें](/words/english/net/add-content-using-document-builder/)
- [फुटनोट और एंडनोट के साथ कार्य करना](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}