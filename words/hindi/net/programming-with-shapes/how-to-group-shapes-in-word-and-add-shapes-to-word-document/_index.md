---
category: general
date: 2026-08-07
description: 'Aspose.Words के साथ Word में आकृतियों को समूहित करने और C# का उपयोग
  करके Word दस्तावेज़ में आकृतियों को जोड़ने का तरीका। साफ़ और पुन: उपयोग योग्य कोड
  के लिए इस चरण‑दर‑चरण गाइड का पालन करें।'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: hi
lastmod: 2026-08-07
og_description: Aspose.Words for .NET का उपयोग करके Word में आकृतियों को समूहित कैसे
  करें। यह ट्यूटोरियल आपको दिखाता है कि Word दस्तावेज़ में आकृतियों को कैसे जोड़ें,
  उन्हें समूहित करें, और स्पष्ट C# कोड के साथ फ़ाइल को सहेजें।
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Word में आकृतियों को समूहित कैसे करें – तेज़ C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: वर्ड में शैप्स को ग्रुप कैसे करें और वर्ड दस्तावेज़ में शैप्स जोड़ें
url: /hi/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में आकृतियों को समूहित कैसे करें और Word दस्तावेज़ में आकृतियों को जोड़ें

यदि आपको **how to group shapes in Word** की आवश्यकता है, तो यह गाइड Aspose.Words for .NET का उपयोग करके पूरी प्रक्रिया को आपके सामने लाता है। आप कुछ ही C# कोड लाइनों के साथ **add shapes to Word document** सीखेंगे, जिससे परिणाम किसी भी रिपोर्टिंग या टेम्प्लेटिंग परिदृश्य के लिए तैयार हो जाता है।

यह ट्यूटोरियल वह सब कुछ कवर करता है जिसकी आपको आवश्यकता है: आवश्यक NuGet पैकेज, एक पूर्ण स्रोत फ़ाइल, और प्रत्येक चरण के महत्व की व्याख्या। अंत तक आप एक DOCX बना सकते हैं जिसमें एक आयत और एक दीर्घवृत्त एक ही समूह आकृति में संयोजित होते हैं।

## आवश्यकताएँ

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो  
* Visual Studio 2022 (या कोई भी IDE जो .NET का समर्थन करता है)  
* Aspose.Words for .NET NuGet पैकेज (`Aspose.Words`) – मुफ्त ट्रायल परीक्षण के लिए काम करता है, लेकिन लाइसेंस मूल्यांकन वॉटरमार्क को हटा देता है  

ये आइटम **add shapes to Word document** के लिए एकमात्र बाहरी निर्भरताएँ हैं।

## Word में आकृतियों को समूहित कैसे करें

समाधान का मूल भाग व्यक्तिगत आकृतियों को बनाना, उन्हें पृष्ठ पर रखना, और फिर उन्हें एक `GroupShape` में लपेटना है। निम्नलिखित चरण कोड के तार्किक क्रम को दर्शाते हैं।

### चरण 1: एक दस्तावेज़ और एक बिल्डर बनाएं

`Document` ऑब्जेक्ट पूरे DOCX फ़ाइल का प्रतिनिधित्व करता है। `DocumentBuilder` दस्तावेज़ को संपादित करने के लिए एक सुविधाजनक API प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*यह क्यों महत्वपूर्ण है*: `Document` सभी Word तत्वों के लिए कंटेनर है। `DocumentBuilder` वर्तमान कर्सर स्थिति को ट्रैक करता रहता है, जो बाद में समूहित आकृति डालते समय आवश्यक होता है।

### चरण 2: आयत आकृति जोड़ें

`ShapeType.Rectangle` निर्दिष्ट करके एक आयत बनाई जाती है। चौड़ाई, ऊँचाई, और स्थान पॉइंट्स में सेट किए जाते हैं (1 pt ≈ 1/72 in)。

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*यह क्यों महत्वपूर्ण है*: `StrokeColor` सेट करने से दस्तावेज़ खोलने पर आकृति दिखाई देती है। यदि ठोस अंदरूनी भाग चाहिए तो आप `FillColor` से आकृति को भर भी सकते हैं।

### चरण 3: दीर्घवृत्त आकृति जोड़ें

दीर्घवृत्त `ShapeType.Ellipse` का उपयोग करता है। इसका आकार और स्थिति आयत से स्वतंत्र है, जिससे आप समूह की अंतिम लेआउट को नियंत्रित कर सकते हैं।

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*यह क्यों महत्वपूर्ण है*: `Left = 120` पर दीर्घवृत्त को स्थित करके, यह आयत के साथ ओवरलैप नहीं करता, जिससे समूह दृश्य रूप से अलग दिखता है।

### चरण 4: दो आकृतियों को समूहित करें

`GroupShape` एक कंटेनर के रूप में कार्य करता है जो अपनी चाइल्ड्स को एकल ऑब्जेक्ट के रूप में मानता है। यह **how to group shapes in Word** के लिए आवश्यक ऑपरेशन है।

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*यह क्यों महत्वपूर्ण है*: समूह बनाना आपको दोनों आकृतियों को एक साथ स्थानांतरित, आकार बदलने या घुमाने की अनुमति देता है। `groupShape` पर लागू कोई भी परिवर्तन उसके चाइल्ड्स तक पहुँचता है।

### चरण 5: समूहित आकृति को दस्तावेज़ में डालें

`DocumentBuilder.InsertNode` `GroupShape` को वर्तमान कर्सर स्थान पर रखता है। क्योंकि हमने बिल्डर को नहीं हटाया है, समूह पहले पृष्ठ की शुरुआत में दिखाई देता है।

```csharp
builder.InsertNode(groupShape);
```

*यह क्यों महत्वपूर्ण है*: नोड को सीधे डालने से अलग पैराग्राफ या टेबल सेल की आवश्यकता नहीं रहती। समूह दस्तावेज़ प्रवाह का हिस्सा बन जाता है।

### चरण 6: दस्तावेज़ को सहेजें

अंत में, DOCX फ़ाइल को डिस्क पर लिखें। एक पूर्ण पथ का उपयोग करें जिसे आपका एप्लिकेशन लिख सकता है।

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*यह क्यों महत्वपूर्ण है*: `doc.Save` सभी बदलावों को अंतिम रूप देता है। परिणामी फ़ाइल को Microsoft Word, LibreOffice, या किसी भी DOCX समर्थित व्यूअर में खोला जा सकता है।

## पूर्ण स्रोत फ़ाइल

नीचे दिया गया कोड एक नए कंसोल प्रोजेक्ट (`dotnet new console`) में कॉपी करें और चलाएँ। यह प्रोग्राम `GroupShape.docx` नाम की फ़ाइल बनाता है जिसमें एक समूहित आयत और दीर्घवृत्त होते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### अपेक्षित आउटपुट

`GroupShape.docx` खोलें। आपको एक एकल दृश्य वस्तु दिखाई देगी जिसमें बाएँ ओर एक नीली आयत और दाएँ ओर एक हरी दीर्घवृत्त है। Word में वस्तु का चयन करने पर दोनों आकृतियाँ एक साथ हाइलाइट होती हैं—यह प्रमाण है कि **how to group shapes in Word** सफल रहा।

## आम प्रश्न और किनारे के मामले

* **क्या मैं दो से अधिक आकृतियाँ जोड़ सकता हूँ?**  
  हां। समूह डालने से पहले प्रत्येक अतिरिक्त `Shape` के लिए `groupShape.AppendChild` कॉल करें।

* **यदि मुझे समूह को घुमाना हो तो क्या करें?**  
  समूह बन जाने के बाद `groupShape.RotationAngle = 45;` सेट करें (कोण डिग्री में)।

* **क्या मुझे `doc.UpdatePageLayout()` कॉल करने की आवश्यकता है?**  
  इस परिदृश्य के लिए नहीं। दस्तावेज़ सहेजने पर लेआउट स्वचालित रूप से अपडेट हो जाता है।

* **लाइसेंसिंग कोड को कैसे प्रभावित करती है?**  
  एक वैध Aspose.Words लाइसेंस (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) के साथ उत्पन्न दस्तावेज़ में कोई मूल्यांकन वॉटरमार्क नहीं होता।

## निष्कर्ष

अब आप Aspose.Words for .NET का उपयोग करके **how to group shapes in Word** और **add shapes to Word document** करना जानते हैं। ट्यूटोरियल ने दस्तावेज़ बनाना, व्यक्तिगत आकृतियों को परिभाषित करना, उन्हें समूहित करना, समूह डालना, और फ़ाइल सहेजना कवर किया।  

अब आप प्रयोग कर सकते हैं:

* समूह में टेक्स्ट बॉक्स या चित्र जोड़ना  
* भरने के रंग, लाइन शैलियों, या शैडो प्रभाव बदलना  
* टेबल या हेडर के भीतर आकृतियों को समूहित करना  

ये विस्तार आपको प्रोग्रामेटिक रूप से परिष्कृत Word टेम्प्लेट बनाने में मदद करते हैं जबकि कोड साफ़ और रखरखाव योग्य रहता है। कोडिंग का आनंद लें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करती हैं।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकृति बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में आकृतियों को डालें](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words के साथ Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}