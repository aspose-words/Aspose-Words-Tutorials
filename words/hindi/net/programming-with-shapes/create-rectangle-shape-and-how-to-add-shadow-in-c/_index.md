---
category: general
date: 2026-04-04
description: Aspose.Words के साथ C# में आयताकार आकार बनाएं और सीखें कि कैसे छाया जोड़ें,
  छाया पर ब्लर लागू करें, और छाया को पारदर्शी बनाएं – चरण‑दर‑चरण मार्गदर्शिका।
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: hi
og_description: Aspose.Words के साथ C# में आयताकार आकार बनाएं। एक संक्षिप्त ट्यूटोरियल
  में सीखें कि कैसे शैडो जोड़ें, शैडो पर ब्लर लागू करें, और शैडो को पारदर्शी बनाएं।
og_title: C# में आयताकार आकार बनाएं और शैडो कैसे जोड़ें
tags:
- Aspose.Words
- C#
- Document Automation
title: C# में आयताकार आकार बनाएं और शैडो कैसे जोड़ें
url: /hi/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में आयत आकार बनाना और शैडो जोड़ना

क्या आपको कभी **आयत आकार बनाना** Word दस्तावेज़ में चाहिए था लेकिन यह नहीं पता था कि उसे सूक्ष्म ड्रॉप‑शैडो कैसे दें? आप अकेले नहीं हैं। कई रिपोर्टिंग या ब्रांडिंग परिदृश्यों में एक साधारण आयत जिसमें हल्की, अर्ध‑पारदर्शी शैडो हो, लेआउट को बहुत अधिक प्रयास के बिना परिष्कृत बना देती है।

इस ट्यूटोरियल में हम **दस्तावेज़ कैसे बनाएं** Aspose.Words का उपयोग करके दिखाएंगे, फिर **शैडो कैसे जोड़ें**, **शैडो पर ब्लर लागू करें**, और यहाँ तक कि **शैडो को पारदर्शी बनाएं**। अंत तक आपके पास एक तैयार‑चलाने योग्य C# स्निपेट होगा जो *.docx* फ़ाइल में एक सुंदर शेडेड आयत उत्पन्न करता है—सिर्फ कुछ ही मिनटों में।

## आपको क्या चाहिए

- .NET 6 या बाद का (API .NET Framework 4.6+ के साथ भी काम करता है)
- Aspose.Words for .NET (इस उदाहरण के लिए फ्री ट्रायल पर्याप्त है)
- एक कोड एडिटर – Visual Studio, VS Code, Rider, या जो भी आप पसंद करें
- बुनियादी C# ज्ञान – कुछ भी जटिल नहीं, बस एक कंसोल एप चलाने की क्षमता

यदि आपके पास ये सब है, तो हम सीधे समाधान की ओर बढ़ सकते हैं।

## चरण 1 – दस्तावेज़ कैसे बनाएं और कैनवास को इनिशियलाइज़ करें

सबसे पहले आपको एक खाली `Document` ऑब्जेक्ट चाहिए। इसे एक खाली कागज़ की शीट समझें जिसे Aspose.Words बाद में Word फ़ाइल में बदल देगा।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

हम `Document` को टेम्पलेट लोड करने के बजाय इंस्टैंशिएट क्यों करते हैं? शुरुआत से शुरू करने से यह सुनिश्चित होता है कि कोई छिपी हुई स्टाइल या सेक्शन हमारे आयत में बाधा न बनें। यह फ़ाइल आकार को भी छोटा रखता है – जब आप लूप में कई दस्तावेज़ जनरेट कर रहे हों तो यह एक अच्छी आदत है।

## चरण 2 – आयत आकार बनाएं (हमारे मुख्य कीवर्ड का कोर)

अब हम वास्तव में **आयत आकार बनाते** हैं। `Shape` क्लास लचीला है; आप इसे प्रकार (Rectangle), आकार, और आसपास के टेक्स्ट के साथ कैसे रैप होना चाहिए, बताते हैं।

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

ध्यान दें कि हमने ऑब्जेक्ट इनिशियलाइज़र सिंटैक्स का उपयोग किया है – यह संक्षिप्त है और बाद में किसी प्रॉपर्टी को भूलने की संभावना कम करता है। आयत पहले पैराग्राफ के अंदर बैठेगी, जिसे हम अगले चरण में जोड़ेंगे।

## चरण 3 – शैडो कैसे जोड़ें और उसकी दिखावट को कस्टमाइज़ करें

शैडो जोड़ना सिर्फ एक लाइन नहीं है; इसमें कई प्रॉपर्टी को ट्यून करना पड़ता है। यहाँ पर द्वितीयक कीवर्ड **शैडो पर ब्लर लागू करें** और **शैडो को पारदर्शी बनाएं** काम आते हैं।

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

संख्याओं पर एक त्वरित नोट: `BlurRadius` को 5 सेट करने से हल्का फेदरिंग मिलता है; 10 करने पर अधिक नरम लुक मिलेगा, या 2 करने पर तेज़ किनारा रहेगा। `Transparency` का मान 0 (अपारदर्शी) से 1 (अदृश्य) तक होता है। इसे अपने ब्रांड के कंट्रास्ट आवश्यकताओं के अनुसार समायोजित करें।

### प्रो टिप

यदि आपको रंगीन शैडो चाहिए (जैसे कॉरपोरेट ब्लू), तो बस `Color.DarkGray` को `Color.FromArgb(80, 0, 120, 215)` से बदल दें। पहला आर्ग्यूमेंट अल्फा चैनल है – सूक्ष्मता के लिए इसे कम रखें।

## चरण 4 – दस्तावेज़ में आकार डालें

आयत और उसकी शैडो तैयार होने के बाद, हम इसे दस्तावेज़ के पहले पैराग्राफ में डालते हैं। यह चरण सुनिश्चित करता है कि आकार फ़ाइल के सबसे ऊपर दिखाई दे।

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

पहले पैराग्राफ को क्यों चुना? यह एक सुरक्षित डिफ़ॉल्ट है जो तब भी काम करता है जब दस्तावेज़ पूरी तरह खाली हो। यदि आपका कोई विशिष्ट स्थान है (जैसे हेडिंग के बाद), तो आप उस नोड को ढूँढकर वहाँ आकार डालेंगे।

## चरण 5 – फ़ाइल सहेजें और परिणाम सत्यापित करें

अंत में, हम दस्तावेज़ को डिस्क पर सहेजते हैं। आप कोई भी पाथ चुन सकते हैं; बस यह सुनिश्चित कर लें कि फ़ोल्डर मौजूद हो।

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

जब आप *ShadowRectangle.docx* को Microsoft Word में खोलेंगे, तो आपको 200 × 100‑पॉइंट आयत दिखेगी जिसमें डार्क‑ग्रे, हल्का ब्लर किया हुआ, 30 % पारदर्शी शैडो तीन पॉइंट दाएँ और नीचे की ओर ऑफ़सेट किया हुआ होगा। प्रभाव सूक्ष्म है लेकिन समतल लेआउट में गहराई जोड़ता है।

![create rectangle shape with shadow in Aspose.Words](https://example.com/placeholder-image.png "create rectangle shape with shadow in Aspose.Words")

*छवि वैकल्पिक पाठ:* **Aspose.Words में शैडो के साथ आयत आकार बनाना** – चित्र अंतिम दस्तावेज़ में शेडेड आयत को दर्शाता है।

## सामान्य विविधताएँ और किनारी मामलों

### शैडो का रंग गतिशील रूप से बदलना

यदि आपका एप्लिकेशन थीम्स को सपोर्ट करता है, तो आप शैडो का रंग कॉन्फ़िगरेशन फ़ाइल से ले सकते हैं:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### आकार को इनलाइन न बनाना

कभी‑कभी आप चाहते हैं कि आयत टेक्स्ट के ऊपर फ़्लोट करे। `WrapType` को `WrapType.Square` करें और `RelativeHorizontalPosition` को `RelativeHorizontalPosition.Margin` सेट करें ताकि अधिक नियंत्रण मिले।

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### कई पृष्ठों को संभालना

यदि आपको हर पृष्ठ पर आयत चाहिए, तो `doc.Sections` पर लूप चलाएँ और प्रत्येक सेक्शन के पहले पैराग्राफ में क्लोन किया हुआ आकार जोड़ें। शैडो सेटिंग्स को भी डुप्लिकेट करने के लिए `rect.Clone(true)` को कॉल करना न भूलें।

## पुनरावलोकन – हमने क्या हासिल किया

- Aspose.Words का उपयोग करके **आयत आकार बनाया**
- **शैडो कैसे जोड़ें** रंग, ऑफ़सेट, ब्लर और पारदर्शिता के साथ
- **शैडो पर ब्लर लागू करें** और **शैडो को पारदर्शी बनाएं** दर्शाया
- एक Word फ़ाइल सहेजी जो तुरंत खोलने योग्य है

इन सबको केवल कुछ ही लाइनों से हासिल किया गया, यह साबित करता है कि परिष्कृत विज़ुअल ट्यूनिंग के लिए हमेशा भारी ग्राफ़िक्स लाइब्रेरी की आवश्यकता नहीं होती।

## आगे क्या?

- अन्य `ShapeType`s (Ellipse, Cloud, आदि) के साथ प्रयोग करें और देखें शैडो कैसे व्यवहार करती है।
- आयत को टेक्स्ट बॉक्स के साथ मिलाकर लेबल्ड कॉल‑आउट बनाएं।
- **दस्तावेज़ कैसे बनाएं** टेम्पलेट्स के साथ गहराई से जुड़ें जो पहले से ही आकारों के लिए प्लेसहोल्डर रखते हैं, फिर उन्हें प्रोग्रामेटिकली भरें।

ब्लर रेडियस, रंग या पारदर्शिता को तब‑तक समायोजित करें जब तक शैडो आपके डिज़ाइन भाषा के लिए बिल्कुल सही न लगें। API लचीला है, और बदलाव तुरंत दिखते हैं जब आप कंसोल एप को फिर से चलाते हैं।

हैप्पी कोडिंग, और आपके दस्तावेज़ हमेशा गहराई का अतिरिक्त स्पर्श रखें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}