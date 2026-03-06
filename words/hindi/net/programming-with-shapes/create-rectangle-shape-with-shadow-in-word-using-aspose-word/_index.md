---
category: general
date: 2026-03-06
description: Aspose.Words के साथ Word में आयताकार आकार बनाएं और आकार में छाया जोड़ें।
  जानें कि Word में आयत कैसे डालें और C# में आकार में छाया कैसे जोड़ें।
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: hi
og_description: Word में आयताकार आकार बनाएं और Aspose.Words के साथ आकार में छाया जोड़ें।
  Word में आयत कैसे डालें और आकार में छाया कैसे जोड़ें, इस पर चरण‑दर‑चरण मार्गदर्शिका।
og_title: Aspose.Words का उपयोग करके Word में छाया के साथ आयताकार आकार बनाएं
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words का उपयोग करके Word में शैडो के साथ आयताकार आकार बनाएं
url: /hi/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में Aspose.Words का उपयोग करके आयताकार आकार और छाया बनाएं

क्या आपको कभी **आयताकार आकार** Word दस्तावेज़ में बनाना पड़ा, लेकिन उसे परिपूर्ण लुक देने का तरीका नहीं पता था? आप अकेले नहीं हैं—ज्यादातर डेवलपर्स को पहली बार स्वचालित दस्तावेज़ों में दृश्य आकर्षण जोड़ते समय यही समस्या आती है। अच्छी खबर? Aspose.Words for .NET के साथ आप कुछ ही C# लाइनों में **आयताकार आकार** बना सकते हैं और **आकार पर छाया** जोड़ सकते हैं।

इस ट्यूटोरियल में हम बिल्कुल **Word में आयत कैसे डालें**, फिर **आकार पर छाया कैसे जोड़ें** ताकि वह पेज से उभरे, यह दिखाएंगे। अंत तक आपके पास एक तैयार‑से‑सेव `Shadow.docx` होगा, जिसे आप Word में खोलकर ग्रे‑टिंटेड आयत और नरम ड्रॉप शैडो देख सकेंगे। कोई अतिरिक्त इमेज फ़ाइल नहीं, कोई मैन्युअल ट्यूनिंग नहीं—सिर्फ कोड।

## What You’ll Learn

- Aspose.Words के साथ **आयताकार आकार** बनाने के लिए आवश्यक सटीक C# स्टेटमेंट्स।  
- `Shadow` ऑब्जेक्ट का उपयोग करके छाया को सक्षम और कॉन्फ़िगर करना।  
- प्रत्येक प्रॉपर्टी क्यों महत्वपूर्ण है (जैसे, `Transparency`, `Blur`, `Angle`)।  
- सामान्य pitfalls (यूनिट्स, संस्करण संगतता) और त्वरित समाधान।  
- एक पूर्ण, कॉपी‑एंड‑पेस्ट‑तैयार प्रोग्राम जिसे आप आज ही चला सकते हैं।

### Prerequisites

- .NET 6+ (या .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 या बाद का (NuGet पैकेज `Aspose.Words`)।  
- C# और Visual Studio (या आपका पसंदीदा IDE) का बुनियादी ज्ञान।  

यदि आपके पास ये सब है, तो चलिए सीधे शुरू करते हैं।

---

## Step 1: Set up the project and import namespaces

पहले, एक नया console app बनाएं (या मौजूदा को पुनः उपयोग करें) और Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

अब आवश्यक नेमस्पेसेज़ को अपने `Program.cs` में लाएँ:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** यदि आप .NET 6+ को टार्गेट कर रहे हैं, तो आप ग्लोबल `using` डायरेक्टिव्स को सक्षम कर सकते हैं ताकि हर फ़ाइल में इन लाइनों को दोहराने की ज़रूरत न पड़े।

---

## Step 2: **Create rectangle shape** in a blank Word document

हम एक नया `Document` ऑब्जेक्ट और उसे मैनीपुलेट करने के लिए `DocumentBuilder` से शुरू करेंगे। बिल्डर की `InsertShape` मेथड वह जादू है।

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

200 × 100 पॉइंट क्यों? Word में एक पॉइंट 1/72 इंच के बराबर होता है, इसलिए आयत लगभग 2.8 × 1.4 इंच बनती है—ध्यान आकर्षित करने के लिए पर्याप्त बड़ी, लेकिन बहुत बड़ी नहीं। आप अपनी लेआउट के अनुसार इन संख्याओं को बदल सकते हैं; बस याद रखें कि ये **पॉइंट्स** में मापी जाती हैं, पिक्सेल में नहीं।

---

## Step 3: **Add shape shadow** – configuring the look

अब जब हमारे पास आयत है, चलिए उसे एक सूक्ष्म ग्रे शैडो देते हैं। `Shadow` ऑब्जेक्ट `Shape` पर रहता है और कई उपयोगी प्रॉपर्टीज़ प्रदान करता है।

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### What each property does

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | छाया को ऑन/ऑफ़ करता है | `true` या `false` |
| **Color** | शैडो का बेस रंग | कोई भी `System.Drawing.Color` |
| **Transparency** | अपारदर्शिता (0 = सॉलिड, 1 = अदृश्य) | 0.0 – 1.0 |
| **Blur** | किनारे की मुलायमता | 0 – 10 (ज्यादा = नरम) |
| **Distance** | आकार और शैडो के बीच की दूरी | 0 – 20 पॉइंट्स |
| **Angle** | प्रकाश की दिशा | 0 – 360 डिग्री |
| **Size** | आकार के सापेक्ष शैडो का स्केल | 0 – 200 % |

> **Why bother with these settings?**  
> शैडो को फाइन‑ट्यून करने से आप कॉर्पोरेट ब्रांडिंग गाइडलाइन्स (जैसे, प्रोफ़ेशनल लुक के लिए 20 % ट्रांसपेरेंसी) के अनुरूप बना सकते हैं, बिना बाहरी इमेज एडिटर की जरूरत के।

---

## Step 4: Save the document and verify the result

अंत में, फ़ाइल को डिस्क पर लिखें। आप कोई भी फ़ोल्डर चुन सकते हैं; बस `YOUR_DIRECTORY` को वास्तविक पाथ से बदलें।

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

`Shadow.docx` को Microsoft Word में खोलें और आपको ग्रे आयत के साथ एक हल्की ड्रॉप शैडो 45° एंगल पर दिखाई देगी। यह विज़ुअल क्यू आकार को पेज से “उठा” हुआ महसूस कराता है—बिल्कुल वही जो एक परिष्कृत रिपोर्ट या इनवॉइस से अपेक्षित है।

---

## Full Working Example

नीचे पूरा प्रोग्राम दिया गया है जिसे आप `Program.cs` में कॉपी‑पेस्ट कर सकते हैं। कोई हिस्सा गायब नहीं है; यह जैसा है वैसा ही कम्पाइल और रन होगा।

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Expected Output

- **File:** `Shadow.docx` प्रोजेक्ट की execution फ़ोल्डर में रखी जाएगी।  
- **Visual:** पेज के केंद्र में एकल आयत, डिफ़ॉल्ट सफ़ेद भराव के साथ, और ग्रे शैडो 4 पॉइंट्स नीचे‑दाएँ की ओर, हल्की ब्लर के साथ, जिससे प्राकृतिक लुक मिलेगा।

---

## Common Questions & Edge Cases

### 1. What if I need a different unit (e.g., centimeters)?

Aspose.Words पॉइंट्स में काम करता है, लेकिन आप सेंटीमीटर को पॉइंट्स में सरल फ़ॉर्मूला से बदल सकते हैं:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Does this work with older Aspose.Words versions?

`Shadow` API संस्करण 14.0 में पेश किया गया था। यदि आप पुराने रिलीज़ पर हैं, तो आपको NuGet के माध्यम से अपग्रेड करना होगा। आकार बनाने वाला बाकी कोड कई वर्षों से स्थिर है, इसलिए आपको ब्रेकिंग चेंजेज़ का सामना नहीं करना पड़ेगा।

### 3. Can I add a shadow to other shapes (e.g., circles)?

बिल्कुल—किसी भी `Shape` ऑब्जेक्ट में `Shadow` प्रॉपर्टी होती है। बस `ShapeType.Rectangle` को `ShapeType.Ellipse` या `ShapeType.Cloud` से बदलें, फिर वही शैडो सेटिंग्स लागू करें।

### 4. What if I need a colored shadow (e.g., blue for a brand)?

`Color.Gray` को अपनी पसंद के किसी भी `Color` से बदलें:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

ध्यान रखें कि `Transparency` को समायोजित करें ताकि रंग बहुत अधिक प्रमुख न हो।

---

## 🎨 Visual Summary

![create rectangle shape with shadow in Word using Aspose.Words](image-placeholder.png "create rectangle shape with shadow in Word using Aspose.Words")

*Alt text: Word में Aspose.Words का उपयोग करके आयताकार आकार और छाया बनाना*

प्लेसहोल्डर स्क्रीनशॉट अंतिम दस्तावेज़ दिखाता है—सिर्फ आयत और उसकी नरम ग्रे छाया।

---

## Conclusion

अब आप जानते हैं कि **Word फ़ाइल में आयताकार आकार** कैसे बनाएं, **आकार पर छाया** कैसे जोड़ें, और Aspose.Words for .NET का उपयोग करके हर दृश्य पहलू को कैसे फाइन‑ट्यून करें। हमने जो छोटा प्रोग्राम बनाया, वह पूरे वर्कफ़्लो को कवर करता है—से

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}