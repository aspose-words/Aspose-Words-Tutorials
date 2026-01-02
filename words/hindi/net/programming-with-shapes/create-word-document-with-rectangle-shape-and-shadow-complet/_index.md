---
category: general
date: 2026-01-02
description: Aspose.Words का उपयोग करके आयताकार आकार के साथ वर्ड दस्तावेज़ बनाएं,
  आकार का भराव रंग सेट करें, और docx फ़ाइल सहेजें। मिनटों में छाया के साथ आयत कैसे
  बनाएं, सीखें।
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: hi
og_description: एक कस्टम आयत के साथ वर्ड दस्तावेज़ बनाएं, उसका भराव रंग सेट करें,
  छाया जोड़ें, और इसे DOCX के रूप में सहेजें। पूर्ण कोड और व्याख्याएँ।
og_title: आयताकार आकार के साथ वर्ड दस्तावेज़ बनाएं – चरण‑दर‑चरण
tags:
- Aspose.Words
- C#
- Document Generation
title: आयताकार आकार और छाया के साथ वर्ड दस्तावेज़ बनाएं – पूर्ण मार्गदर्शिका
url: /hi/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# आयत आकार और छाया के साथ Word दस्तावेज़ बनाएं – पूर्ण गाइड

क्या आपने कभी सोचा है कि **Word दस्तावेज़** को कैसे बनाएं जिसमें एक सुंदर शैली वाला आयत हो? शायद आपको लोगो के लिए एक प्लेसहोल्डर, एक रंगीन बैनर, या रिपोर्ट में सिर्फ एक दृश्य संकेत चाहिए। इस ट्यूटोरियल में हम **आयत आकार जोड़ेंगे**, उसे भरने का रंग देंगे, हल्की छाया लागू करेंगे, और अंत में **docx फ़ाइल सहेजेंगे** – सभी Aspose.Words for .NET के साथ।

आपके पास चलाने योग्य C# स्निपेट, प्रत्येक पंक्ति की स्पष्ट व्याख्या, और कई टिप्स होंगे जिन्हें आप अपने प्रोजेक्ट में पुन: उपयोग कर सकते हैं। कोई फालतू बात नहीं, सिर्फ एक व्यावहारिक समाधान जिसे आप कॉपी‑पेस्ट कर सकते हैं।

## आपको क्या चाहिए

- .NET 6 या बाद का संस्करण (कोड .NET Framework पर भी काम करता है)  
- Visual Studio 2022 (या कोई भी पसंदीदा एडिटर)  
- **Aspose.Words** NuGet पैकेज (`Install-Package Aspose.Words`)  

यदि आपके पास ये सब है, तो चलिए शुरू करते हैं।

## चरण 1 – नया दस्तावेज़ प्रारंभ करें (Word दस्तावेज़ कैसे बनाएं)

सबसे पहले आपको मेमोरी में **Word दस्तावेज़** बनाना होगा। इसे एक खाली कैनवास खोलने के रूप में सोचें जहाँ आप बाद में अपना आयत बनाएँगे।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **यह क्यों महत्वपूर्ण है:** `Document` पूरे DOCX फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` एक सुविधाजनक हेल्पर है जो आपको टेक्स्ट, टेबल, इमेज और शैप्स को मैन्युअली नोड ट्री संभाले बिना डालने देता है।

## चरण 2 – आयत आकार डालें (आयत आकार जोड़ें)

अब हम दस्तावेज़ में **आयत आकार** जोड़ेंगे। `InsertShape` मेथड आकार प्रकार और उसके आयाम बिंदुओं में लेता है (1 बिंदु = 1/72 इंच)।

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **प्रो टिप:** यदि आपको कोई अलग ज्यामिति (एलिप्स, त्रिकोण आदि) बनानी है, तो बस `ShapeType.Rectangle` को इच्छित enum मान में बदल दें।

## चरण 3 – छाया कॉन्फ़िगर करें (आकार भरने का रंग और छाया सेट करें)

छाया एक सपाट आकार को अधिक त्रि‑आयामी महसूस करा सकती है। यहाँ हम छाया को सक्षम करते हैं और उसकी उपस्थिति को समायोजित करते हैं।

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **इन मानों का कारण:** एक मध्यम ब्लर रेडियस और 5‑बिंदु दूरी छाया को आकार से अधिक नहीं भरने देती, जबकि 45° प्रकाश स्रोत को ऊपर‑बाएँ से आने का अनुकरण करता है – यह UI में सामान्य प्रथा है।

## चरण 4 – दस्तावेज़ सहेजें (docx फ़ाइल सहेजें)

अंत में, हम **docx फ़ाइल** को डिस्क पर **सहेजते** हैं। अपने वातावरण के अनुसार पाथ को समायोजित करें।

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

जब आप `ShadowDemo.docx` को Word में खोलेंगे, तो आपको हल्के‑नीले आयत के साथ एक नरम ग्रे छाया दिखेगी, ठीक नीचे दी गई स्क्रीनशॉट की तरह।

![आयत आकार और छाया के साथ Word दस्तावेज़ बनाएं](https://example.com/images/rectangle-shadow.png "आयत आकार और छाया के साथ Word दस्तावेज़ बनाएं")

*छवि वैकल्पिक पाठ:* **Word दस्तावेज़ बनाएं** जिसमें छाया वाला आयत आकार दिखाया गया है।

## पूर्ण, चलाने योग्य उदाहरण (आयत बनाएं और सहेजें)

सब कुछ एक साथ मिलाकर, यहाँ पूरा प्रोग्राम है जिसे आप किसी भी कंसोल ऐप में कॉपी कर सकते हैं:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### अपेक्षित परिणाम

- लक्ष्य फ़ोल्डर में **ShadowDemo.docx** नाम की फ़ाइल बनती है।  
- इसे Microsoft Word में खोलने पर एक पृष्ठ पर “Shadow Demo” टेक्स्ट के बाद हल्के‑नीला आयत दिखेगा।  
- आयत पर 45° कोण पर एक नरम ग्रे छाया पड़ेगी, जिससे उसे हल्का 3‑D लुक मिलेगा।

## सामान्य प्रश्न और किनारे के मामलों

### यदि मुझे अलग आकार चाहिए तो?

`InsertShape` में `200, 100` तर्कों को बदल दें। ये मान बिंदुओं में चौड़ाई और ऊँचाई हैं। वर्ग बनाने के लिए समान मान उपयोग करें।

### क्या मैं छाया को अधिक स्पष्ट बना सकता हूँ?

`BlurRadius` बढ़ाएँ ताकि किनारा स्मूद हो, `Distance` बढ़ाएँ ताकि ऑफ़सेट बड़ा हो, या `Transparency` को कम करें (जैसे `0.1`) ताकि छाया गहरी दिखे।

### आयत के चारों ओर बॉर्डर कैसे जोड़ूँ?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### क्या यह पुराने Aspose.Words संस्करणों के साथ संगत है?

हाँ। `ShadowFormat` क्लास शुरुआती 2020 रिलीज़ से मौजूद है। यदि आप बहुत पुराना संस्करण उपयोग कर रहे हैं, तो सभी प्रॉपर्टीज़ तक पहुँचने के लिए अपग्रेड करना पड़ सकता है।

## टिप्स और सामान्य गलतियाँ

- **प्रो टिप:** बड़े दस्तावेज़ों को (`doc.Dispose()`) हमेशा डिस्पोज़ करें, विशेषकर वेब एप्लिकेशन में, ताकि नेटिव रिसोर्सेज़ मुक्त हो सकें।  
- **सावधान रहें:** बिना उचित अनुमति के रिलेटिव पाथ उपयोग करने से `UnauthorizedAccessException` हो सकता है। एब्सोल्यूट पाथ उपयोग करें या सुनिश्चित करें कि एप पूल को लिखने की अनुमति है।  
- **याद रखें:** `FillColor` प्रॉपर्टी कोई भी `System.Drawing.Color` स्वीकार करती है। कस्टम पेस्टल शेड के लिए `Color.FromArgb(255, 173, 216, 230)` उपयोग कर सकते हैं।

## अगले कदम

अब जब आप **Word दस्तावेज़** बनाना, **आयत आकार जोड़ना**, **आकार भरने का रंग सेट करना**, और **docx फ़ाइल सहेजना** जानते हैं, तो आप आगे प्रयोग कर सकते हैं:

- कई शैप्स डालें और उन्हें `RelativeHorizontalPosition` और `RelativeVerticalPosition` से व्यवस्थित करें।  
- आयत को `Shape.TextBox` के साथ टेक्स्ट जोड़कर कैप्शन बनाएं।  
- वही दस्तावेज़ PDF में एक्सपोर्ट करें (`doc.Save("output.pdf")`) वितरण के लिए।

यदि आप अधिक उन्नत ग्राफिक्स में रुचि रखते हैं, तो Aspose.Words की **WordArt**, **चार्ट**, और **इनलाइन इमेज** सपोर्ट देखें। प्रत्येक का पैटर्न समान है: एक नोड बनाएं, उसकी प्रॉपर्टीज़ कॉन्फ़िगर करें, और सहेजें।

---

### TL;DR

- `Document` और `DocumentBuilder` का उपयोग करके **Word दस्तावेज़** बनाएं।  
- `InsertShape(ShapeType.Rectangle, …)` को कॉल करके **आयत आकार जोड़ें**।  
- इच्छित बैकग्राउंड के लिए `FillColor` सेट करें।  
- `ShadowFormat` को सक्षम करें और उसकी प्रॉपर्टीज़ को ट्यून करके पेशेवर लुक प्राप्त करें।  
- `document.Save("yourPath.docx")` से **docx फ़ाइल सहेजें**।

हैप्पी कोडिंग, और अपने Word फ़ाइलों को थोड़ा और स्टाइलिश बनाते रहें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}