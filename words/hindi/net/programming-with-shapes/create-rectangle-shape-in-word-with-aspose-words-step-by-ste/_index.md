---
category: general
date: 2026-02-18
description: Aspose.Words का उपयोग करके आयताकार आकार बनाएं और कुछ ही मिनटों में छाया
  जोड़ना, आकार सेट करना और Word दस्तावेज़ सहेजना सीखें।
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: hi
og_description: Word फ़ाइल में आयताकार आकार बनाएं, छाया जोड़ना सीखें, आकार निर्धारित
  करें, और Aspose.Words के साथ C# में दस्तावेज़ सहेजें।
og_title: Word में आयताकार आकार बनाएं – पूर्ण Aspose.Words ट्यूटोरियल
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words के साथ Word में आयताकार आकार बनाएं – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

Let's craft final output.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ Word में आयताकार आकार बनाएं – चरण‑दर‑चरण गाइड

क्या आपको कभी **create rectangle shape** Word फ़ाइल में बनाना पड़ा लेकिन शुरुआत कैसे करें, यह नहीं पता चला? आप अकेले नहीं हैं—डेवलपर्स अक्सर पूछते हैं, “मैं आकार में छाया कैसे जोड़ूँ और दस्तावेज़ को अभी भी संपादन योग्य रखूँ?” इस ट्यूटोरियल में हम इसका उत्तर देंगे और साथ ही **छाया कैसे जोड़ें**, **आकार का आकार सेट करें**, और **Word दस्तावेज़ सहेजें** सभी को एक सहज प्रवाह में दिखाएंगे।

हम सब कुछ कवर करेंगे, नई दस्तावेज़ को इनिशियलाइज़ करने से (हाँ, यह **how to create document** का पहला कदम है) लेकर अंतिम *.docx* को डिस्क पर सहेजने तक। कोई बाहरी रेफ़रेंस नहीं, सिर्फ एक स्व-निहित उदाहरण जिसे आप कॉपी‑पेस्ट करके Visual Studio में आज ही चला सकते हैं।

---

## Prerequisites

- .NET 6+ (या .NET Framework 4.7+). Aspose.Words किसी भी हालिया .NET रनटाइम के साथ काम करता है।
- एक वैध Aspose.Words लाइसेंस (या मुफ्त इवैल्यूएशन की) – अन्यथा आपको वॉटरमार्क दिखेगा।
- Visual Studio, Rider, या कोई भी C# एडिटर जो आप पसंद करते हैं।
- बेसिक C# ज्ञान—कुछ भी जटिल नहीं, बस एक कंसोल ऐप चलाने की क्षमता।

> **Pro tip:** यदि आप Mac पर हैं, तो वही कोड .NET 6 के साथ VS Code में चलता है—सिर्फ यह सुनिश्चित करें कि आप `Aspose.Words` NuGet पैकेज को रेफ़रेंस कर रहे हैं।

---

## Step 1: Initialize the document – the foundation of **how to create document**

कुछ भी ड्रॉ करने से पहले, हमें एक खाली कैनवास चाहिए। Aspose.Words इसे `Document` कहता है।  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Why this matters:** `Document` ऑब्जेक्ट पूरे *.docx* फ़ाइल का प्रतिनिधित्व करता है। आप जो भी आकार, पैराग्राफ, और सेक्शन जोड़ते हैं, वे इस ऑब्जेक्ट की चाइल्ड बन जाते हैं। एक साफ़ दस्तावेज़ से शुरू करने से कोई छिपी हुई स्टाइल्स आपके आयताकार में बाधा नहीं बनेंगी।

---

## Step 2: Define the rectangle and **set shape size**

एक आयत सिर्फ `Shape` है जिसमें `ShapeType.Rectangle` सेट किया जाता है। हम इसे स्पष्ट आयाम देंगे ताकि यह ठीक वैसा ही दिखे जैसा हम चाहते हैं।

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **What the numbers mean:** Aspose.Words पॉइंट्स (1 pt = 1/72 in) का उपयोग करता है। मानों को अपने लेआउट के अनुसार समायोजित करें; सामान्य A4 पेज के लिए 200 pt एक आरामदायक चौड़ाई है।

---

## Step 3: **How to add shadow** – making the shape pop

छाया एक विज़ुअल संकेत देती है कि आकार “पेज से उठाया” गया है। `Shadow` प्रॉपर्टी आपको रंग, दूरी, ट्रांसपैरेंसी, और ब्लर को ट्यून करने देती है।

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Why use transparency?** पूरी तरह अपारदर्शी छाया कठोर लग सकती है। इसे 0.4 पर सेट करने से प्रभाव सूक्ष्म और प्रोफेशनल बन जाता है।

---

## Step 4: Position the rectangle – inline flow with surrounding text

यदि आप चाहते हैं कि आकार पैराग्राफ में एक कैरेक्टर की तरह व्यवहार करे, तो उसका `WrapType` `Inline` सेट करें। यह लेआउट को भविष्य में दस्तावेज़ संपादित करने पर भी पूर्वानुमेय रखता है।

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Edge case:** यदि आपको आयत को टेक्स्ट के ऊपर फ्लोट करना है (जैसे वॉटरमार्क), तो `WrapType` को `Square` या `BehindText` में बदलें।

---

## Step 5: Insert the shape into the document body

अब हम वास्तव में आयत को पहले पैराग्राफ में डालते हैं। यदि दस्तावेज़ में अभी तक कोई कंटेंट नहीं है, तो `FirstParagraph` स्वचालित रूप से बना लिया जाता है।

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tip:** आप पहले एक नया पैराग्राफ बना सकते हैं और फिर आकार को जोड़ सकते हैं—यह तब उपयोगी होता है जब आपको आसपास का टेक्स्ट चाहिए हो।

---

## Step 6: **Save Word document** – the final step

सब कुछ तैयार होने के बाद, फ़ाइल को सहेजना एक‑लाइनर है। कोई भी पाथ चुनें; उदाहरण में एक प्लेसहोल्डर उपयोग किया गया है जिसे आपको अपने डायरेक्टरी से बदलना चाहिए।

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Result:** उत्पन्न *.docx* को Microsoft Word में खोलें। आपको एक काली‑छाया वाली आयत दिखेगी, 200 pt चौड़ी और 100 pt ऊँची, जो पहले पैराग्राफ के साथ इनलाइन बैठी है।

---

## Expected output

जब आप **ShadowShape.docx** खोलेंगे, दस्तावेज़ दिखाएगा:

- एकल पैराग्राफ जिसमें आयताकार आकार है।
- आयत में 5 pt की ऑफ़सेट वाली सूक्ष्म काली छाया है।
- आकार का आकार Step 2 में सेट किए गए आयामों से मेल खाता है।
- अतिरिक्त टेक्स्ट नहीं दिखेगा जब तक आप उसे मैन्युअली न जोड़ें।

यदि आकार नहीं दिख रहा है, तो सुनिश्चित करें कि आपने सही Aspose.Words संस्करण रेफ़रेंस किया है और आपका लाइसेंस (या ट्रायल) सक्रिय है।

---

## Common Questions & Variations

| Question | Answer |
|----------|--------|
| *क्या मैं छाया का रंग काले के अलावा किसी और रंग में बदल सकता हूँ?* | बिल्कुल—`rectangleShape.Shadow.Color = Color.Blue;` या कोई भी `System.Drawing.Color` सेट करें। |
| *यदि मुझे बड़ी आयत चाहिए तो क्या करें?* | `Width` और `Height` मानों को समायोजित करें। याद रखें ये पॉइंट्स में हैं; 72 pt = 1 in। |
| *क्या आकार को एब्सोल्यूट पोजीशन पर रखना संभव है?* | हाँ—`WrapType = WrapType.Absolute` उपयोग करें और `Top`/`Left` प्रॉपर्टीज़ सेट करें। |
| *क्या यह .NET Core के साथ काम करता है?* | करता है। Aspose.Words क्रॉस‑प्लेटफ़ॉर्म है; बस .NET Standard के लिए NuGet पैकेज इंस्टॉल करें। |
| *क्या मैं आयत के अंदर टेक्स्ट जोड़ सकता हूँ?* | सीधे नहीं; इसके लिए आपको साधारण आयत के बजाय `TextBox` आकार डालना होगा। |

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

प्रोग्राम चलाएँ, `C:\Temp\ShadowShape.docx` पर जाएँ, और आपको वही आयत छाया के साथ दिखेगी जैसा बताया गया है।

---

## Conclusion

अब आप जानते हैं कि Aspose.Words का उपयोग करके Word फ़ाइल में **create rectangle shape** कैसे बनाते हैं, **shape size** कैसे सेट करते हैं, **छाया कैसे जोड़ते हैं**, और अंत में **Word दस्तावेज़ सहेजते** हैं। पूरी प्रक्रिया—**how to create document** से लेकर परिणाम को स्थायी करने तक—केवल कुछ ही C# लाइनों में समाहित है और इसे अधिक जटिल लेआउट्स के लिए विस्तारित किया जा सकता है।

अगली चुनौती के लिए तैयार हैं? आयत को गोल‑कोने वाले आकार से बदलें, विभिन्न छाया रंगों के साथ प्रयोग करें, या आकार को टेबल सेल के अंदर एम्बेड करें। प्रत्येक बदलाव यहाँ कवर किए गए मूल सिद्धांतों को मजबूत करता है।

यदि आपको यह गाइड उपयोगी लगा, तो इसे शेयर करें, अपने खुद के वैरिएशन के साथ कमेंट करें, या Word ऑटोमेशन पर हमारे अन्य ट्यूटोरियल देखें, जैसे इमेज इन्सर्ट करना या Aspose.Words के साथ टेबल जनरेट करना। Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}