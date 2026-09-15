---
category: general
date: 2026-09-14
description: C# का उपयोग करके Word में आकृति को छिपाना सीखें—जिसमें Word दस्तावेज़
  बनाने का कोड, Word में आयताकार आकृति सम्मिलित करना, और प्रोग्रामेटिक रूप से Word
  में आकृति को छिपाना शामिल है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: hi
lastmod: 2026-09-14
og_description: C# का उपयोग करके Word में शैप को कैसे छुपाएँ—स्टेप‑बाय‑स्टेप गाइड
  जो वर्ड डॉक्यूमेंट कोड बनाना और रेक्टैंगल शैप इन्सर्ट करना भी दिखाता है।
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: C# कोड के साथ Word दस्तावेज़ में आकार को कैसे छुपाएँ
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# कोड के साथ Word दस्तावेज़ में आकृति को कैसे छुपाएँ
url: /hi/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में C# कोड के साथ shape को छुपाने का तरीका

यदि आपको Word फ़ाइल में **shape को छुपाने का तरीका** की आवश्यकता है, तो यह ट्यूटोरियल पूर्ण समाधान दिखाता है। आप देखेंगे कि कैसे एक Word दस्तावेज़ बनाएं, एक rectangle shape डालें, एक ellipse जोड़ें, और उस ellipse को छुपाएं ताकि फ़ाइल खोलने पर केवल rectangle दिखाई दे।

गाइड में वह सब कुछ कवर किया गया है जिसकी आपको ज़रूरत है—कोई बाहरी रेफ़रेंस नहीं, सिर्फ कोड और व्याख्याएँ। अंत तक आप किसी भी Word दस्तावेज़ में प्रोग्रामेटिक रूप से छुपी हुई ग्राफ़िक्स एम्बेड कर सकेंगे।

## आवश्यकताएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
- Aspose.Words for .NET (फ्री ट्रायल या लाइसेंस्ड संस्करण)  
  इसे NuGet के माध्यम से इंस्टॉल करें: `dotnet add package Aspose.Words`
- C# और Visual Studio या आपके पसंदीदा किसी भी IDE की बुनियादी जानकारी

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेसेस इम्पोर्ट करें

एक नया console application शुरू करें और आवश्यक `using` स्टेटमेंट्स जोड़ें। ये इम्पोर्ट्स आपको `Document`, `DocumentBuilder`, और drawing क्लासेज़ तक पहुंच देते हैं जो shapes को मैनीपुलेट करने के लिए आवश्यक हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**यह क्यों महत्वपूर्ण है** – सही नेमस्पेसेस इम्पोर्ट करने से कंपाइलेशन एरर नहीं होते और API सतह shape निर्माण और विज़िबिलिटी कंट्रोल के लिए उपलब्ध हो जाती है।

## चरण 2: नया Word दस्तावेज़ और एक builder बनाएं

`Document` फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` कंटेंट जोड़ने के लिए एक फ्लुएंट API प्रदान करता है। यह वह पहला स्थान है जहाँ आप **shape को छुपाने का तरीका** लॉजिक लागू करते हैं: आपको किसी भी shape के अस्तित्व से पहले एक दस्तावेज़ कॉन्टेक्स्ट चाहिए।

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explanation** – `Document` ऑब्जेक्ट खाली से शुरू होता है। `DocumentBuilder` पहले पैराग्राफ की शुरुआत में स्थित होता है, जो shape या टेक्स्ट डालने के लिए तैयार है।

## चरण 3: एक दृश्यमान rectangle shape डालें

rectangle वह shape होगा जो दस्तावेज़ खोलने पर दृश्यमान रहेगा। आप उसके आकार, स्थिति, और फ़ॉर्मेटिंग को सीधे shape ऑब्जेक्ट के माध्यम से नियंत्रित कर सकते हैं।

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Why this step** – एक rectangle जोड़ने से **insert rectangle shape word** आवश्यकता प्रदर्शित होती है। `FillColor` और `LineColor` सेट करने से अंतिम दस्तावेज़ में shape को देखना आसान हो जाता है।

## चरण 4: एक ellipse shape डालें और उसे छुपाएँ

अब आप वह shape जोड़ते हैं जिसे आप छुपाना चाहते हैं। `Hidden` प्रॉपर्टी Word को बताती है कि UI में shape को रेंडर न किया जाए, हालांकि वह दस्तावेज़ संरचना का हिस्सा बना रहता है।

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explanation** – `Hidden = true` सेट करना **hide shape in word** का मूल है। Word सामान्य दृश्य और प्रिंटिंग के दौरान इस फ़्लैग का सम्मान करता है, लेकिन आवश्यकता पड़ने पर shape को प्रोग्रामेटिक रूप से अभी भी एक्सेस किया जा सकता है।

## चरण 5: दस्तावेज़ को सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। वह फ़ोल्डर चुनें जहाँ आपके पास लिखने की अनुमति हो, और फ़ाइल को ऐसा स्पष्ट नाम दें जो ट्यूटोरियल के उद्देश्य को दर्शाए।

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Result** – Microsoft Word में `ShapeVisibility.docx` खोलने पर केवल हल्के‑नीले रंग का rectangle दिखेगा। छुपा हुआ ellipse दिखाई नहीं देगा, जिससे पुष्टि होती है कि आपने Word फ़ाइल में **shape को छुपाने का तरीका** सफलतापूर्वक सीख लिया है।

## पूर्ण कार्यशील उदाहरण

सभी स्निपेट्स को एक साथ जोड़ने से आपको एक एकल, चलाने योग्य प्रोग्राम मिलता है:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### अपेक्षित आउटपुट

- **Visual**: जब आप `ShapeVisibility.docx` खोलते हैं, तो आपको बाएँ मार्जिन के पास स्थित हल्के‑नीले रंग का rectangle दिखाई देगा। कोई ellipse दिखाई नहीं देगा।
- **Programmatic**: छुपा हुआ ellipse दस्तावेज़ के XML (`<w:drawing>` एलिमेंट) में `w:hidden` एट्रिब्यूट सेट के साथ मौजूद रहता है, जिसे आप फ़ाइल को zip के रूप में खोलकर और `document.xml` की जाँच करके सत्यापित कर सकते हैं।

## सामान्य प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| *क्या मैं कई shapes को छुपा सकता हूँ?* | हाँ। आप जिस प्रत्येक shape को छुपाना चाहते हैं, उस पर `Hidden = true` सेट करें। |
| *क्या छुपी हुई shapes प्रिंट होती हैं?* | डिफ़ॉल्ट रूप से Word छुपी हुई ऑब्जेक्ट्स को प्रिंट नहीं करता। यदि आपको उन्हें प्रिंट करना है, तो प्रिंट करने से पहले `Hidden` फ़्लैग को साफ़ कर दें। |
| *क्या यह hidden प्रॉपर्टी पुराने Word संस्करणों में समर्थित है?* | `Hidden` एट्रिब्यूट Office Open XML मानक का हिस्सा है और Word 2007 और बाद के संस्करणों में काम करता है। |
| *यदि मुझे रनटाइम पर विज़िबिलिटी टॉगल करनी हो तो?* | `document.GetChildNodes(NodeType.Shape, true)` के माध्यम से shape प्राप्त करें और अपनी लॉजिक के आधार पर `Hidden` प्रॉपर्टी को बदलें। |

## प्रो टिप्स

- **Performance**: यदि आप कई दस्तावेज़ जनरेट करते हैं, तो प्रत्येक फ़ाइल के लिए नया `DocumentBuilder` बनाने के बजाय एक ही `DocumentBuilder` इंस्टेंस को पुनः उपयोग करें।
- **Version control**: जनरेट किए गए `.docx` फ़ाइलों को एक version‑controlled फ़ोल्डर में रखें; छुपी हुई shapes डाउनस्ट्रीम प्रोसेसिंग के लिए मेटाडाटा मार्कर के रूप में काम कर सकती हैं।
- **Testing**: Aspose.Words (`document.Save("out.pdf")`) के साथ DOCX को PDF में बदलकर एक त्वरित विज़ुअल टेस्ट ऑटोमेट करें। PDF भी ellipse को छुपाएगा, जिससे पुष्टि होती है कि hidden फ़्लैग फ़ॉर्मेट रूपांतरणों में भी बरकरार रहता है।

## निष्कर्ष

आप अब C# का उपयोग करके Word दस्तावेज़ में **shape को छुपाने का तरीका** जानते हैं। ट्यूटोरियल ने दस्तावेज़ बनाना, **insert rectangle shape word**, एक ellipse जोड़ना, और `Hidden` फ़्लैग लागू करके **hide shape in word** व्यवहार हासिल करना दिखाया। पूर्ण, चलाने योग्य कोड के साथ आप किसी भी स्वचालित रिपोर्टिंग या टेम्पलेटिंग वर्कफ़्लो में छुपी हुई ग्राफ़िक्स को इंटीग्रेट कर सकते हैं।

### अगले कदम

- rotation, shadow, और text wrapping जैसी अन्य shape प्रॉपर्टीज़ का अन्वेषण करें।  
- छुपी हुई shapes को कस्टम दस्तावेज़ प्रॉपर्टीज़ के साथ मिलाकर मशीन‑रीडेबल डेटा एम्बेड करें।  
- अपने ऑटोमेशन टूलकिट को विस्तारित करने के लिए टेबल, चार्ट, और कंटेंट कंट्रोल्स के लिए **create word document code** पैटर्न देखें।

विभिन्न shape प्रकारों और विज़िबिलिटी सेटिंग्स के साथ प्रयोग करने में संकोच न करें—आपका अगला Word ऑटोमेशन प्रोजेक्ट बस कुछ लाइनों के कोड दूर है!

## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [C# का उपयोग करके Word में rectangle shape बनाएं – चरण-दर-चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Shadowed rectangle shape के साथ खाली Word दस्तावेज़ बनाएं – चरण-दर-चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow ट्यूटोरियल – C# में Word shape में शैडो जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}