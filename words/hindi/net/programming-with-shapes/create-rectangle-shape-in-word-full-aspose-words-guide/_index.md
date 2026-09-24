---
category: general
date: 2026-02-26
description: Aspose.Words का उपयोग करके Word में आयताकार आकार बनाएं और सीखें कि कैसे
  आकार को Word में जोड़ें, आकार पर छाया लागू करें, और मिनटों में आकार की पारदर्शिता
  सेट करें।
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: hi
og_description: Aspose.Words का उपयोग करके Word में आयताकार आकार बनाएं। Word में आकार
  जोड़ना, आकार पर छाया लागू करना, और आकार की पारदर्शिता जल्दी सेट करना सीखें।
og_title: वर्ड में आयताकार आकार बनाएं – पूर्ण Aspose.Words गाइड
tags:
- Aspose.Words
- C#
- Word Automation
title: Word में आयताकार आकार बनाएं – पूर्ण Aspose.Words गाइड
url: /hi/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Rectangle Shape in Word – Full Aspose.Words Guide

क्या आपको कभी **Word दस्तावेज़ में आयताकार आकार** बनाना पड़ा लेकिन शुरुआत नहीं पता थी? आप अकेले नहीं हैं—कई डेवलपर्स रिपोर्ट या इनवॉइस ऑटोमेट करते समय इस समस्या से जूझते हैं। इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने‑योग्य उदाहरण के माध्यम से दिखाएंगे कि **Word में shape कैसे जोड़ें**, एक सूक्ष्म शैडो लागू करें, और shape की transparency कैसे नियंत्रित करें, वह भी Aspose.Words for .NET के साथ।

गाइड के अंत तक आपके पास एक `.docx` फ़ाइल होगी जिसमें एक साफ़ आयताकार आकार और पॉलिश्ड शैडो होगा—ब्रांडिंग, कॉल‑आउट या सिर्फ़ दस्तावेज़ को थोड़ा प्रोफ़ेशनल दिखाने के लिए एकदम सही। कोई बाहरी टूल नहीं चाहिए, सिर्फ़ कुछ ही लाइनें C# की।

## What You’ll Need

- **Aspose.Words for .NET** (2026 की शुरुआत तक का नवीनतम संस्करण)। इसे NuGet से प्राप्त करें (`Install-Package Aspose.Words`)।
- एक .NET विकास पर्यावरण (Visual Studio, Rider, या C# एक्सटेंशन वाला VS Code)।
- C# सिंटैक्स की बुनियादी समझ—कुछ खास नहीं, बस सामान्य `using` स्टेटमेंट्स और ऑब्जेक्ट निर्माण।

यदि आपके पास ये सब है, तो चलिए शुरू करते हैं।

## Create Rectangle Shape – Core Steps

नीचे पूरा स्रोत कोड दिया गया है। इसे एक नए कंसोल प्रोजेक्ट में कॉपी‑पेस्ट करें, **F5** दबाएँ, और आप निर्दिष्ट फ़ोल्डर में `ShadowDemo.docx` देखेंगे।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Why This Works

- **`Document`** एंट्री पॉइंट है; यह पूरे Word फ़ाइल का प्रतिनिधित्व करता है।
- **`Shape`** के साथ `ShapeType.Rectangle` बताता है कि हमें एक आयताकार ड्रॉइंग ऑब्जेक्ट चाहिए।
- **`Width`** और **`Height`** सेट करने से shape का आकार निश्चित हो जाता है; अन्यथा यह एक बहुत छोटा प्लेसहोल्डर बन जाता है।
- **`Shadow`** ऑब्जेक्ट हमें प्रत्येक दृश्य पहलू को फाइन‑ट्यून करने देता है: ब्लर, दूरी, दिशा, रंग, ट्रांसपेरेंसी, और स्प्रेड। यही *shape पर शैडो लागू करने* का मुख्य भाग है।
- अंत में, **`AppendChild`** shape को दस्तावेज़ के पहले पैराग्राफ में डालता है, जो *Word में shape जोड़ने* का सबसे सरल तरीका है, बिना टेबल या हेडर/फ़ूटर की जटिलता के।

जब आप `ShadowDemo.docx` खोलेंगे, तो आपको एक ग्रे आयताकार आकार दस्तावेज़ में आराम से बैठा दिखेगा, जिसकी शैडो 45° कोण पर नीचे‑दाएँ की ओर झुकी होगी। शैडो एक ठोस ब्लॉक नहीं है; ब्लर रेडियस किनारों को नरम करता है, और ट्रांसपेरेंसी इसे एक प्राकृतिक ड्रॉप शैडो जैसा बनाता है, न कि कठोर ओवरले।

![create rectangle shape example](image.png "Aspose.Words का उपयोग करके Word में शैडो के साथ आयताकार आकार बनाएं")

*(ऊपर की छवि कोड स्निपेट के अंतिम परिणाम को दर्शाती है।)*

## Add Shape to Word Document – Placement Options

उदाहरण में **पहले पैराग्राफ** का उपयोग किया गया है क्योंकि यह स्क्रीन पर कुछ दिखाने का सबसे तेज़ तरीका है। वास्तविक परिस्थितियों में आप चाह सकते हैं:

- shape को किसी विशिष्ट **section** या **header/footer** में डालें।
- shape को **टेबल सेल** के भीतर रखें ताकि टेबल डेटा के साथ संरेखण हो सके।
- **टेक्स्ट रैपिंग** विकल्प (जैसे `WrapType.Square`) के साथ इसे रैप करें ताकि आसपास का टेक्स्ट आयत के चारों ओर बह सके।

यहाँ एक त्वरित वैरिएशन है जो shape को एक नई पैराग्राफ में कस्टम स्टाइल के साथ रखता है:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Pro tip:* हमेशा shape की प्रॉपर्टीज़ सेट करने के **बाद** उसे जोड़ें; अन्यथा आपको दृश्य रूप को रिफ्रेश करने के लिए `UpdateLayout` कॉल करना पड़ सकता है।

## Apply Shadow to Shape – Fine‑Tuning the Look

शैडो दस्तावेज़ की सौंदर्यशास्त्र को काफी बदल सकता है। `Shadow` क्लास कई प्रॉपर्टीज़ प्रदान करती है:

| प्रॉपर्टी      | यह क्या नियंत्रित करता है                                   | सामान्य मान |
|---------------|----------------------------------------------------|----------------|
| `BlurRadius`  | शैडो किनारों की नरमी                      | 2.0 – 10.0      |
| `Distance`    | shape से शैडो की दूरी        | 1.0 – 8.0       |
| `Direction`   | डिग्री में कोण (0 = बायाँ, 90 = ऊपर)              | 0 – 360         |
| `Color`       | शैडो का रंग (कोई भी `System.Drawing.Color`)        | ग्रे, ब्लैक, कस्टम |
| `Transparency`| अपारदर्शिता (0 = पूरी तरह अपारदर्शी, 1 = अदृश्य)        | 0.0 – 0.5       |
| `Spread`      | ब्लर लागू होने से पहले शैडो का विस्तार    | 0.0 – 1.0       |

यदि आप **सूक्ष्म, प्रोफ़ेशनल लुक** चाहते हैं, तो `BlurRadius` को 4‑6 के आसपास रखें और `Transparency` को 0.2 के करीब रखें, जैसा कि ऊपर के कोड में है। **ड्रामेटिक इफ़ेक्ट** के लिए, `Distance` को 6 तक बढ़ाएँ, `Direction` को 135° सेट करें, और `Transparency` को 0.05 तक घटाएँ।

## Set Shape Transparency and Shadow Spread

ट्रांसपेरेंसी केवल शैडो तक सीमित नहीं है; आप आयताकार shape को भी अंशतः पारदर्शी बना सकते हैं:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

सेमी‑ट्रांसपेरेंट फ़िल और सॉफ्ट शैडो का संयोजन अक्सर एक आधुनिक UI फ़ील देता है—डैशबोर्ड या रिपोर्ट में एम्बेडेड डिज़ाइन मॉक‑अप के लिए बेहतरीन।

### Edge Cases to Watch

1. **पुराने Word संस्करण** (pre‑2007) कुछ शैडो प्रॉपर्टीज़ को सपोर्ट नहीं करते। यदि आप `.doc` फ़ाइलें टार्गेट कर रहे हैं, तो शैडो को सरल बनाएं (जैसे `BlurRadius` को 0 सेट करें)।
2. **हाई DPI डिस्प्ले** शैडो को थोड़ा अलग रेंडर कर सकते हैं। यदि दृश्य सटीकता महत्वपूर्ण है, तो लक्ष्य पर्यावरण पर टेस्ट करें।
3. **ओवरलैपिंग शैप्स**—Aspose शैडो को उसी क्रम में रेंडर करता है जिसमें वे जोड़े गए हों। अनचाहे ओक्लूज़न से बचने के लिए पीछे से आगे की ओर शैप्स डालें।

## Save and Verify the Result

`Document.Save` मेथड फ़ाइल एक्सटेंशन से आउटपुट फ़ॉर्मेट को स्वचालित रूप से पहचान लेता है। **`.docx`** फ़ाइल के लिए आपको Open XML फ़ॉर्मेट मिलता है, जिसे अधिकांश आधुनिक Word प्रोसेसर समझते हैं। यदि आपको समान दृश्य शैली के साथ **PDF** चाहिए, तो सिर्फ़ एक्सटेंशन बदल दें:

```csharp
document.Save("ShadowDemo.pdf");
```

जनरेटेड `ShadowDemo.docx` (या `ShadowDemo.pdf`) खोलने पर आपको एक साफ़ **शैडो वाला आयताकार** दिखना चाहिए, जिससे पुष्टि होगी कि आपने Aspose.Words का उपयोग करके *आयताकार shape बनाना* और *shape पर शैडो लागू करना* सफलतापूर्वक किया है।

## Frequently Asked Questions

**Q: क्या मैं कोई अन्य shape, जैसे ellipse, उपयोग कर सकता हूँ?**  
A: बिल्कुल। `ShapeType.Rectangle` को `ShapeType.Ellipse` (या किसी अन्य `ShapeType` enum) से बदल दें। शैडो प्रॉपर्टीज़ वही रहेंगी।

**Q: अगर मैं चाहता हूँ कि आयताकार क्लिक‑योग्य हो?**  
A: आप shape को एक हाइपरलिंक असाइन कर सकते हैं:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: क्या यह .NET 6+ पर काम करता है?**  
A: हाँ। Aspose.Words 23.11 और बाद के संस्करण पूरी तरह से .NET 6, .NET 7, और .NET 8 को सपोर्ट करते हैं। बस उचित NuGet पैकेज रेफ़रेंसेस जोड़ें।

**Q: शैडो का रंग मेरे ब्रांड से मिलाने के लिए कैसे बदलूँ?**  
A: कोई भी `System.Drawing.Color` उपयोग करें:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Wrap‑Up

हमने वह सब कवर किया जो आपको **Word दस्तावेज़ में आयताकार shape बनाना**, **shape को Word में जोड़ना**, **shape पर शैडो लागू करना**, और **shape की ट्रांसपेरेंसी सेट करना** के लिए चाहिए। पूरा, चलाने योग्य कोड इस पेज के शीर्ष पर है, और व्याख्याएँ आपको आकार, रंग और शैडो पैरामीटर को किसी भी प्रोजेक्ट के लिए समायोजित करने का आत्मविश्वास देती हैं।

अगला कदम क्या है? इन चीज़ों के साथ प्रयोग करें:

- बैज इफ़ेक्ट के लिए कई शैप्स को लेयर करें।
- दस्तावेज़ सामग्री के आधार पर डायनामिक साइजिंग (जैसे टेबल कॉलम से चौड़ाई निकालना)।
- शैडो को बरकरार रखते हुए दस्तावेज़ को PDF या HTML में एक्सपोर्ट करना।

यदि आपको कोई समस्या आती है तो टिप्पणी छोड़ें, या “शैडो वाला आयताकार” थीम पर अपने स्वयं के वैरिएशन शेयर करें।

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}