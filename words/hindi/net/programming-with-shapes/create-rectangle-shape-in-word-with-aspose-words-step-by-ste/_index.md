---
category: general
date: 2025-12-29
description: Aspose.Words C# का उपयोग करके Word दस्तावेज़ में आयताकार आकार बनाएं।
  आकार की पारदर्शिता सेट करना, छाया का रंग निर्धारित करना सीखें, और आसानी से Word
  दस्तावेज़ को सहेजें।
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: hi
og_description: Aspose.Words C# के साथ Word दस्तावेज़ में आयताकार आकार बनाएं। यह गाइड
  दिखाता है कि कैसे आकार की पारदर्शिता सेट करें, छाया का रंग सेट करें, और Word दस्तावेज़
  को सहेजें।
og_title: Word में आयताकार आकार बनाएं – पूर्ण Aspose.Words ट्यूटोरियल
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words के साथ Word में आयताकार आकार बनाएं – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में आयताकार आकार बनाएं – पूर्ण Aspose.Words ट्यूटोरियल

क्या आपको कभी Word दस्तावेज़ में **आयताकार आकार बनाना** पड़ा है लेकिन शुरुआत नहीं पता थी? आप अकेले नहीं हैं; कई डेवलपर्स रिपोर्ट या इनवॉइस को स्वचालित करते समय इस समस्या का सामना करते हैं। इस गाइड में हम ठीक‑ठीक चरणों के माध्यम से आयताकार आकार बनाना, आकार की पारदर्शिता सेट करना, शैडो का रंग सेट करना, और अंत में Aspose.Words for .NET का उपयोग करके **Word दस्तावेज़ सहेजना** दिखाएंगे।

हम प्रारंभिक दस्तावेज़ ऑब्जेक्ट से लेकर डिस्क पर अंतिम `.docx` फ़ाइल तक सब कुछ कवर करेंगे, ताकि अंत तक आप प्रोग्रामेटिक रूप से **Word दस्तावेज़ बनाना** बिना अनुमान के कर सकें। कोई बाहरी संदर्भ नहीं, सिर्फ एक स्व-निहित समाधान जिसे आप अपने प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं।

## आवश्यकताएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)
- C# सिंटैक्स की बुनियादी जानकारी
- आपका पसंदीदा IDE (Visual Studio, Rider, VS Code, आदि)

> **Pro tip:** यदि आप Aspose.Words का फ्री ट्रायल उपयोग कर रहे हैं, तो लाइब्रेरी आउटपुट फ़ाइल में एक वॉटरमार्क जोड़ देगी। प्रोडक्शन के लिए आपको एक वैध लाइसेंस चाहिए।

## चरण 1: दस्तावेज़ और बिल्डर को इनिशियलाइज़ करें

सबसे पहले हम एक नया, खाली Word दस्तावेज़ और एक `DocumentBuilder` बनाते हैं जो हमें सामग्री डालने देता है। बिल्डर को एक वर्चुअल पेन की तरह समझें जो पृष्ठ पर ड्रॉ करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this matters:** `DocumentBuilder` के बिना आपको लो‑लेवल नोड ट्री को सीधे मैनीपुलेट करना पड़ेगा, जो त्रुटिप्रवण और पढ़ने में कठिन होता है।

## चरण 2: आयताकार आकार बनाएं

अब हम वास्तव में **आयताकार आकार बनाते** हैं। `InsertShape` मेथड एक `ShapeType` एन्नुम, चौड़ाई, और ऊँचाई (पॉइंट्स में) लेता है। लौटाया गया `Shape` ऑब्जेक्ट बाद में विज़ुअल प्रॉपर्टीज़ को समायोजित करने देता है।

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

इस चरण पर आयताकार एक ठोस काली बॉक्स है जो वर्तमान पैराग्राफ से जुड़ी हुई है। आप इसे स्थानांतरित कर सकते हैं, आकार बदल सकते हैं, या आवश्यकता होने पर बाद में घुमा भी सकते हैं।

![शैडो के साथ आयताकार आकार बनाएं](/images/rectangle-shadow.png "एक Word दस्तावेज़ जिसमें ग्रे शैडो के साथ आयताकार आकार दिखाया गया है")

*छवि वैकल्पिक पाठ: Word दस्तावेज़ में शैडो के साथ आयताकार आकार*

## चरण 3: आकार की पारदर्शिता सेट करें

पारदर्शिता आकार की भराव की “देखने‑योग्य” स्तर है। Aspose.Words `Transparency` प्रॉपर्टी का उपयोग करता है जो `0.0` (अपारदर्शी) से `1.0` (पूरी तरह पारदर्शी) तक होती है। यहाँ हम **आकार की पारदर्शिता** को 40 % पर सेट करते हैं ताकि नीचे का टेक्स्ट पढ़ने योग्य बना रहे।

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Edge case:** यदि आपको पूरी तरह अदृश्य आकार चाहिए लेकिन शैडो दिखाना चाहते हैं, तो `Transparency` को `1.0` सेट करें और आकार को शून्य से अलग आउटलाइन चौड़ाई दें।

## चरण 4: शैडो कॉन्फ़िगर करें

एक सूक्ष्म ड्रॉप शैडो गहराई जोड़ता है। हम **शैडो का रंग** मध्यम ग्रे पर सेट करेंगे, उसके ब्लर रेडियस को समायोजित करेंगे, और इसे क्षैतिज तथा लंबवत कुछ पॉइंट्स से ऑफसेट करेंगे।

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Why this matters:** बहुत तेज़ या बहुत गहरा शैडो प्रिंटिंग आर्टिफैक्ट जैसा दिख सकता है। `Blur` और `Transparency` को तब तक समायोजित करें जब तक यह प्राकृतिक न लगे।

## चरण 5: Word दस्तावेज़ सहेजें

अंत में हम **Word दस्तावेज़** को डिस्क पर सहेजते हैं। `Save` मेथड एक्सटेंशन से फ़ाइल फॉर्मेट को स्वचालित रूप से निर्धारित करता है; `.docx` आधुनिक OpenXML फॉर्मेट है।

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

यदि फ़ोल्डर मौजूद नहीं है, तो Aspose.Words `ArgumentException` फेंकेगा। सुनिश्चित करें कि पाथ वैध है या पहले से डायरेक्टरी बनाएं।

## पूरा कार्यशील उदाहरण

नीचे पूरा, तैयार‑चलाने‑योग्य प्रोग्राम है जो सभी चरणों को एक साथ जोड़ता है। इसे एक नए कंसोल प्रोजेक्ट में कॉपी करें और **F5** दबाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### अपेक्षित परिणाम

`ShadowRectangle.docx` को Microsoft Word में खोलें। आपको एक हल्के‑ग्रे आयताकार दिखेगा जिसमें मुलायम, थोड़ा ऑफसेट शैडो होगा, दोनों 40 % पारदर्शिता पर रेंडर किए गए हैं। आकार एक खाली पृष्ठ पर बैठा है, अतिरिक्त सामग्री के लिए तैयार।

## सामान्य प्रश्न और विविधताएँ

**यदि मुझे अलग आकार चाहिए तो?**  
`ShapeType.Rectangle` को किसी भी अन्य एन्नुम वैल्यू (`Ellipse`, `Triangle`, `Star`, आदि) से बदलें। बाकी कोड वही रहता है।

**क्या मैं आउटलाइन रंग बदल सकता हूँ?**  
हाँ—`rectangleShape.StrokeColor = System.Drawing.Color.Blue;` उपयोग करें और वैकल्पिक रूप से `rectangleShape.StrokeWeight = 1.5;` सेट करें।

**मैं आकार को पृष्ठ पर विशिष्ट स्थान पर कैसे रखूँ?**  
`rectangleShape.WrapType = WrapType.None;` सेट करें और फिर `rectangleShape.Left` और `rectangleShape.Top` प्रॉपर्टीज़ को समायोजित करें (मान पॉइंट्स में हैं)।

**क्या आयताकार के अंदर टेक्स्ट जोड़ना संभव है?**  
बिल्कुल। आकार बनाने के बाद आप `rectangleShape.AppendChild(new Paragraph(document))` कॉल कर सकते हैं और फिर अपने टेक्स्ट के साथ एक `Run` जोड़ सकते हैं। यदि आप अधिक फॉर्मेटिंग चाहते हैं तो `rectangleShape.TextBox` प्रॉपर्टीज़ सेट करना याद रखें।

## प्रो टिप्स और सामान्य गलतियाँ

- **License early:** यदि आप लाइसेंस लागू करना भूल जाते हैं, तो Aspose.Words पहली पृष्ठ पर वॉटरमार्क डाल देगा, जो परीक्षण के दौरान भ्रमित कर सकता है।
- **Performance tip लूप में कई दस्तावेज़ बनाते हैं, तो एक ही `Document` इंस्टेंस को पुन: उपयोग करें और प्रत्येक सहेजने के बाद `document.RemoveAllChildren();` कॉल करें ताकि अत्यधिक GC दबाव से बचा जा सके।
- **Shadow visibility:** कम‑रिज़ॉल्यूशन स्क्रीन पर सूक्ष्म शैडो अदृश्य दिख सकता है। डिबगिंग के लिए `Blur` या `OffsetX/Y` बढ़ाएँ, फिर प्रोडक्शन के लिए घटाएँ।

## अगले कदम

अब जब आप जानते हैं कि कैसे **आयताकार आकार बनाएं**, **आकार की पारदर्शिता सेट करें**, **शैडो का रंग सेट करें**, और **Word दस्तावेज़ सहेजें**, तो ट्यूटोरियल को विस्तारित करने पर विचार करें:

- कई आकार जोड़ें और उन्हें समूहित करें।
- रिपोर्ट लेआउट के लिए टेबल सेल के अंदर आयताकार डालें।
- आकार को `DocumentBuilder.InsertHtml` के साथ मिलाकर HTML‑स्टाइल्ड कंटेंट ओवरले करें।
- `Glow` या `Reflection` जैसे अन्य विज़ुअल इफ़ेक्ट्स का अन्वेषण करें ताकि अधिक UI‑जैसे दस्तावेज़ बन सकें।

प्रयोग करें, चीज़ें तोड़ें, और फिर सुधारें—प्रोग्रामेटिक दस्तावेज़ जनरेशन एक खेल का मैदान है जहाँ विज़ुअल डिज़ाइन कोड से मिलता है।

---

*कोडिंग का आनंद लें! यदि आपको कोई समस्या आती है, तो नीचे टिप्पणी छोड़ें और हम साथ में समाधान करेंगे।*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}