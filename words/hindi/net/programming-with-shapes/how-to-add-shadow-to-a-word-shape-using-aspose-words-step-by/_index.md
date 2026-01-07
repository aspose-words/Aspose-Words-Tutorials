---
category: general
date: 2026-01-06
description: Aspose.Words C# के साथ Word आकृति में छाया कैसे जोड़ें। आकृति पर छाया
  लागू करना, छाया का कोण सेट करना, और छाया की दूरी को जल्दी से समायोजित करना सीखें।
draft: false
keywords:
- how to add shadow
- apply shadow to shape
- add shape shadow
- set shadow angle
- adjust shadow distance
language: hi
og_description: C# में Word आकृति पर छाया कैसे जोड़ें। यह ट्यूटोरियल दिखाता है कि
  कैसे आकृति पर छाया लागू करें, छाया का कोण सेट करें, और Aspose.Words के साथ छाया
  की दूरी समायोजित करें।
og_title: Word आकार में छाया कैसे जोड़ें – पूर्ण Aspose.Words गाइड
tags:
- Aspose.Words
- C#
- Document Processing
- Graphics
title: Word आकार में छाया कैसे जोड़ें – Aspose.Words के साथ चरण-दर-चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/how-to-add-shadow-to-a-word-shape-using-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words का उपयोग करके Word आकार में शैडो कैसे जोड़ें

क्या आपने कभी **शैडो कैसे जोड़ें** को Word दस्तावेज़ में बिना Word खोले करने के बारे में सोचा है? आप अकेले नहीं हैं—डेवलपर्स को अक्सर रिपोर्ट, इनवॉइस या मार्केटिंग फ़्लायर के लिए वह विज़ुअल पॉलिश चाहिए, लेकिन वे हर बार UI नहीं खोलना चाहते।  

इस ट्यूटोरियल में हम **शैडो कैसे जोड़ें** को प्रोग्रामेटिकली करने की प्रक्रिया दिखाएंगे, समझाएंगे कि प्रत्येक प्रॉपर्टी क्यों महत्वपूर्ण है, और आपको दिखाएंगे कि *shape पर शैडो लागू करना*, *शैडो एंगल सेट करना*, और *शैडो दूरी समायोजित करना* केवल कुछ ही C# कोड लाइनों से कैसे किया जाता है।

> **आपको क्या मिलेगा:** एक पूरी‑चलाने योग्य उदाहरण जो DOCX लोड करता है, पहले shape पर यथार्थवादी ड्रॉप शैडो जोड़ता है, और परिणाम को नई फ़ाइल के रूप में सहेजता है। कोई बाहरी टूल आवश्यक नहीं, केवल Aspose.Words for .NET।

## Prerequisites

- .NET 6.0 (या कोई भी नवीनतम .NET Framework संस्करण)  
- Aspose.Words for .NET ≥ 23.10 (लेखन के समय उपलब्ध नवीनतम स्थिर संस्करण)  
- एक Word दस्तावेज़ (`shapes.docx`) जिसमें कम से कम एक ड्रॉइंग shape मौजूद हो  
- Visual Studio, Rider, या कोई भी पसंदीदा C# IDE  

यदि लाइब्रेरी आपके पास नहीं है, तो इसे NuGet से प्राप्त करें:

```bash
dotnet add package Aspose.Words
```

अब बुनियादी बातें कवर हो गई हैं, चलिए वास्तविक चरणों में उतरते हैं।

## shape पर शैडो कैसे जोड़ें – Overview

**शैडो कैसे जोड़ें** का मुख्य भाग `ShadowFormat` ऑब्जेक्ट में रहता है, जिसे हर `Shape` एक्सपोज़ करता है। `ShadowFormat` को शैडो का “स्टाइल शीट” समझें—इसके प्रॉपर्टीज़ शैडो की दृश्यता, रंग, ब्लर, ऑफ़सेट और दिशा निर्धारित करती हैं।

नीचे एक उच्च‑स्तरीय रोडमैप दिया गया है:

1. स्रोत दस्तावेज़ लोड करें।  
2. लक्ष्य `Shape` प्राप्त करें।  
3. उसका `ShadowFormat` प्राप्त करें।  
4. शैडो की दृश्य प्रॉपर्टीज़ सेट करें (जिसमें *शैडो एंगल सेट करना* और *शैडो दूरी समायोजित करना* शामिल है)।  
5. संशोधित दस्तावेज़ सहेजें।

प्रत्येक चरण अपने‑अपने सेक्शन में विस्तृत है, ताकि आप अपनी आवश्यकता अनुसार चुन‑सकें।

<img src="shadow-example.png" alt="how to add shadow example in Word document">

## Step 1 – Word दस्तावेज़ लोड करें

सबसे पहले, हमें एक `Document` इंस्टेंस चाहिए जो हमारे स्रोत फ़ाइल की ओर इशारा करे। यह ऑपरेशन हल्का है; Aspose.Words फ़ाइल को स्ट्रीम करता है और इन‑मेमोरी DOM बनाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Load the DOCX that already contains a shape.
Document doc = new Document("YOUR_DIRECTORY/shapes.docx");
```

**क्यों महत्वपूर्ण है:** दस्तावेज़ लोड करने से हमें नोड ट्री तक पहुँच मिलती है, जहाँ shapes `NodeType.Shape` के रूप में मौजूद होते हैं। यदि आप इसे छोड़ देते हैं, तो आपके पास शैडो लगाने के लिए कोई shape नहीं रहेगा।

## Step 2 – पहला shape प्राप्त करें (या कोई भी shape जो आप चाहते हैं)

आप shape को इंडेक्स, नाम, या कस्टम प्रेडिकेट से प्राप्त कर सकते हैं। सरलता के लिए, हम दस्तावेज़ में पहला shape लेंगे। `GetChild` मेथड ट्री को डेप्थ‑फ़र्स्ट ट्रैवर्स करता है और वह नोड रिटर्न करता है जिसकी आप माँग करते हैं।

```csharp
// Grab the first shape – change the index if you need a different one.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (shape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

**Pro tip:** यदि आपके दस्तावेज़ में कई shapes हैं, तो `doc.GetChildNodes(NodeType.Shape, true)` पर लूप लगाएँ और प्रत्येक पर शैडो लागू करें। यह एक सामान्य वैरिएशन है जब आपको पूरे स्लाइड या पेज पर *add shape shadow* लागू करना हो।

## Step 3 – शैडो फ़ॉर्मेटिंग ऑब्जेक्ट तक पहुँचें और कॉन्फ़िगर करें

अब हम अंततः **शैडो कैसे जोड़ें** के दिल तक पहुँचते हैं: `ShadowFormat`। यह ऑब्जेक्ट शैडो की उपस्थिति को बदलने वाली हर चीज़ रखता है।

```csharp
// Step 3: Get the shadow format for the shape.
ShadowFormat shadow = shape.ShadowFormat;

// Make the shadow visible.
shadow.Visible = true;

// Choose a dark gray color for a subtle effect.
shadow.Color = Color.DarkGray;

// Set transparency to 30 % (0.0 = opaque, 1.0 = fully transparent).
shadow.Transparency = 0.3;

// Blur radius – larger values give a softer edge.
shadow.Size = 5;
```

### शैडो एंगल सेट करें और शैडो दूरी समायोजित करें

*शैडो एंगल सेट करना* और *शैडो दूरी समायोजित करना* कीवर्ड यहाँ काम आते हैं। एंगल यह निर्धारित करता है कि प्रकाश किस दिशा से आ रहा है, जबकि दूरी यह तय करती है कि शैडो shape से कितनी दूर ऑफ़सेट हो।

```csharp
// Angle in degrees – 45° points down‑right.
shadow.Angle = 45;

// Distance in points – how far the shadow is shifted.
shadow.Distance = 3;
```

**इन संख्याओं का कारण:** 45° का एंगल और 3 pts की दूरी मिलकर ऊपर‑बाएँ से प्रकाश का स्रोत बनाते हैं, जो अधिकांश दस्तावेज़ लेआउट में प्राकृतिक दिखता है। आप प्रयोग कर सकते हैं: 0° शैडो को सीधे नीचे रखता है, 180° इसे ऊपर की ओर उलट देता है।

## Step 4 – दस्तावेज़ सहेजें और परिणाम सत्यापित करें

एक बार शैडो प्रॉपर्टीज़ सेट हो जाने पर, आप बस दस्तावेज़ को डिस्क पर लिख देते हैं। Aspose.Words सभी लो‑लेवल OOXML को आपके लिए संभालता है।

```csharp
// Save the modified document with the new shadow effect.
doc.Save("YOUR_DIRECTORY/shadowed.docx");
```

`shadowed.docx` को Microsoft Word या किसी भी संगत व्यूअर में खोलें—आपको पहला shape अब 45° एंगल पर एक नरम, डार्क ग्रे ड्रॉप शैडो के साथ दिखेगा।

### त्वरित सत्यापन चेकलिस्ट

- **Visibility:** क्या शैडो वास्तव में रेंडर हो रहा है? (`shadow.Visible` को `true` होना चाहिए)।  
- **Color & Transparency:** क्या शैडो एक हल्के ग्रे जैसा दिख रहा है, न कि कठोर काला?  
- **Angle & Distance:** क्या शैडो आपके निर्दिष्ट दिशा में ऑफ़सेट दिख रहा है?  
- **Blur (Size):** क्या किनारा आपके डिज़ाइन के लिए पर्याप्त स्मूद है?  

यदि कुछ भी गलत दिखे, तो संबंधित प्रॉपर्टी को समायोजित करें और फिर से सहेजें। परिवर्तन तुरंत दिखेंगे।

## सामान्य वैरिएशन और एज‑केस हैंडलिंग

### कई shapes पर शैडो जोड़ना

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.Visible = true;
    sf.Color = Color.Black;
    sf.Transparency = 0.2;
    sf.Size = 4;
    sf.Angle = 30;
    sf.Distance = 2;
}
doc.Save("YOUR_DIRECTORY/all_shapes_shadowed.docx");
```

### शैडो रीसेट करना (हटाना)

यदि आपको *add shape shadow* को शर्तीय रूप से लागू करना है, तो बाद में इसे बंद भी कर सकते हैं:

```csharp
shape.ShadowFormat.Visible = false;
```

### संगतता नोट्स

- Aspose.Words 23.10+ DOCX, DOC, और यहाँ तक कि PDF एक्सपोर्ट के लिए शैडो प्रॉपर्टीज़ को पूरी तरह सपोर्ट करता है।  
- शैडो इफ़ेक्ट PDF में `doc.Save("out.pdf")` के माध्यम से कन्वर्ट करने पर भी बरकरार रहता है।  
- पुराने Word संस्करण (< 2007) OOXML शैडो को स्टोर नहीं करते, इसलिए यदि आप `.doc` के रूप में सहेजते हैं तो इफ़ेक्ट खो जाएगा। सर्वोत्तम परिणाम के लिए `.docx` का उपयोग करें।

## Pro tip – पुन: उपयोग के लिए हेल्पर मेथड बनाएं

यदि आप कई प्रोजेक्ट्स में समान शैडो सेटिंग्स लागू कर रहे हैं, तो लॉजिक को एक यूटिलिटी मेथड में रैप करें:

```csharp
public static void ApplyStandardShadow(Shape target, Color? color = null,
                                        double transparency = 0.3,
                                        double size = 5,
                                        double angle = 45,
                                        double distance = 3)
{
    ShadowFormat sf = target.ShadowFormat;
    sf.Visible = true;
    sf.Color = color ?? Color.DarkGray;
    sf.Transparency = transparency;
    sf.Size = size;
    sf.Angle = angle;
    sf.Distance = distance;
}
```

अब एक ही लाइन `ApplyStandardShadow(shape);` पूरे *apply shadow to shape* कार्य को कर देती है।

## निष्कर्ष

हमने Aspose.Words का उपयोग करके Word shape में **शैडो कैसे जोड़ें** को शुरू से अंत तक कवर किया। दस्तावेज़ लोड करके, shape प्राप्त करके, `ShadowFormat` को कॉन्फ़िगर करके (जिसमें *शैडो एंगल सेट करना* और *शैडो दूरी समायोजित करना* शामिल है), और फ़ाइल सहेजकर, आप किसी भी डायग्राम को बिना Word खोले प्रोफ़ेशनल‑ग्रेड ड्रॉप शैडो दे सकते हैं।  

विभिन्न रंगों के साथ *apply shadow to shape* आज़माएँ, पूरी कलेक्शन पर *add shape shadow* लागू करें, या नाटकीय लाइटिंग इफ़ेक्ट के लिए *set shadow angle* को बदलें। अगला तार्किक कदम इन शैडो को बॉर्डर, रिफ्लेक्शन, या यहाँ तक कि 3‑D रोटेशन जैसी अन्य स्टाइलिंग फीचर्स के साथ मिलाना है।

एज केस, परफ़ॉर्मेंस, या PDF में कन्वर्ज़न के बारे में प्रश्न हों तो नीचे टिप्पणी करें, और हैप्पी कोडिंग!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}