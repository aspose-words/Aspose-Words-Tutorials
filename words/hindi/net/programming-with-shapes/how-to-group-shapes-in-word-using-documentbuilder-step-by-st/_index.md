---
category: general
date: 2026-09-08
description: DocumentBuilder के साथ Word में आकृतियों को समूहित करना सीखें, एक खाली
  Word दस्तावेज़ बनाएं, और केवल कुछ ही पंक्तियों के C# कोड में एक आयताकार आकृति डालें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: hi
lastmod: 2026-09-08
og_description: DocumentBuilder का उपयोग करके Word में आकृतियों को समूहित करें। यह
  ट्यूटोरियल दिखाता है कि कैसे एक खाली Word दस्तावेज़ बनाएं, एक आयताकार आकृति डालें,
  और आकृतियों को GroupShape में मिलाएँ।
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: DocumentBuilder के साथ Word में आकृतियों को समूहित करें – पूर्ण C# उदाहरण
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: DocumentBuilder का उपयोग करके Word में आकृतियों को समूहित करने की चरण‑दर‑चरण
  गाइड
url: /hi/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में DocumentBuilder का उपयोग करके आकृतियों को समूहित करने का तरीका – चरण‑दर‑चरण गाइड

यदि आपको प्रोग्रामेटिक रूप से **Word में आकृतियों को समूहित** करने की आवश्यकता है, तो यह ट्यूटोरियल C# में एक पूर्ण समाधान दिखाता है। आप देखेंगे कि **एक खाली Word दस्तावेज़ कैसे बनाएं**, **DocumentBuilder** का उपयोग कैसे करें, और **एक आयताकार आकृति सम्मिलित** करें, फिर उसे एक दीर्घवृत्त के साथ समूहित करें। परिणामस्वरूप एक एकल `GroupShape` मिलेगा जिसे आप एक ही वस्तु के रूप में स्थानांतरित, आकार बदल या शैलीबद्ध कर सकते हैं।

यह गाइड Aspose.Words for .NET लाइब्रेरी का उपयोग करके समूहित ग्राफ़िक्स के साथ Word दस्तावेज़ उत्पन्न करने के सभी आवश्यक पहलुओं को कवर करता है। लेख के अंत तक आपके पास एक चलाने योग्य प्रोजेक्ट होगा जो `GroupedShapes.docx` उत्पन्न करता है, जिसमें एक आयत और एक दीर्घवृत्त एक ही आकृति में मिलाए गए होते हैं।

## पूर्वापेक्षाएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.7.2+ के साथ भी काम करता है)
- Aspose.Words for .NET NuGet पैकेज (`Aspose.Words`) – संस्करण 23.12 या नया
- Visual Studio 2022 या Visual Studio Code जैसे C# IDE
- C# सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग का बुनियादी परिचय

> **प्रो टिप:** कमांड लाइन से NuGet पैकेज इंस्टॉल करें ताकि आपका प्रोजेक्ट साफ़ रहे:  
> `dotnet add package Aspose.Words --version 23.12.0`

## चरण 1: एक खाली Word दस्तावेज़ बनाएं

पहला कार्य `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है, जो एक खाली Word फ़ाइल का प्रतिनिधित्व करता है, और `DocumentBuilder` जो आपको सामग्री जोड़ने की अनुमति देता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**यह क्यों महत्वपूर्ण है:** `Document` फ़ाइल कंटेनर प्रदान करता है, जबकि `DocumentBuilder` टेक्स्ट, इमेज और आकृतियों को सम्मिलित करने के लिए एक फ़्लुएंट API देता है। `DocumentBuilder` के बिना आपको दस्तावेज़ के नोड ट्री को मैन्युअल रूप से बदलना पड़ेगा, जो त्रुटिप्रवण है।

## चरण 2: एक आयताकार आकृति सम्मिलित करें

आयत अक्सर डायग्राम के निर्माण ब्लॉक के रूप में उपयोग होती है। `InsertShape` को `ShapeType.Rectangle` के साथ उपयोग करें और चौड़ाई व ऊँचाई पॉइंट्स में निर्दिष्ट करें (1 pt ≈ 1/72 in)।

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**यह क्यों महत्वपूर्ण है:** `Left` और `Top` सेट करने से आयत पृष्ठ पर सटीक रूप से स्थित होती है, जो बाद में अन्य आकृतियों के साथ समूहित करने के लिए आवश्यक है। `InsertShape` मेथड स्वचालित रूप से आकृति को वर्तमान पैराग्राफ में जोड़ देता है।

## चरण 3: एक दीर्घवृत्त आकृति सम्मिलित करें

अब एक दीर्घवृत्त जोड़ें जो आयत के बगल में स्थित होगा।

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**यह क्यों महत्वपूर्ण है:** अलग `ShapeType` का उपयोग यह दर्शाता है कि समान `DocumentBuilder` API विभिन्न ग्राफ़िक्स बना सकती है। दीर्घवृत्त को इस तरह स्थित करें कि वह आयत के साथ ओवरलैप हो, जिससे समूहित प्रभाव स्पष्ट हो।

## चरण 4: दो आकृतियों को समूहित करें

`GroupShape` एक कंटेनर की तरह कार्य करता है। आयत और दीर्घवृत्त को बच्चों के रूप में जोड़ने से वे एक ही ऑब्जेक्ट बन जाते हैं।

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**यह क्यों महत्वपूर्ण है:** `Bounds` प्रॉपर्टी Word को बताती है कि समूह पृष्ठ पर कहाँ स्थित है। बच्चों को जोड़ने से आप उनकी व्यक्तिगत फ़ॉर्मेटिंग को बरकरार रखते हुए सामूहिक परिवर्तन (स्थानांतरित, घुमाना, आकार बदलना) सक्षम करते हैं।

## चरण 5: दस्तावेज़ को सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप पथ को अपनी पसंद के किसी भी फ़ोल्डर में बदल सकते हैं।

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

जब आप `GroupedShapes.docx` को Microsoft Word में खोलेंगे, तो आपको एक आयत और एक दीर्घवृत्त एक साथ समूहित दिखेगा। समूह का चयन करने से दोनों आकृतियाँ हाइलाइट होंगी, जिससे आप उन्हें एक इकाई के रूप में ड्रैग या री‑साइज़ कर सकते हैं।

### अपेक्षित आउटपुट

- एक Word फ़ाइल जिसका नाम **GroupedShapes.docx** है
- पहले पृष्ठ पर **आयत** (100 pt × 50 pt) स्थित (50, 50) पर मौजूद है
- **दीर्घवृत्त** (80 pt × 80 pt) स्थित (200, 70) पर
- दोनों आकृतियाँ **GroupShape** का हिस्सा हैं, जिसकी बाउंडिंग बॉक्स 300 pt × 200 pt है

## सामान्य विविधताएँ और किनारे के मामले

| परिदृश्य | समायोजन |
|----------|------------|
| **विभिन्न पृष्ठ आकार** | `document.Sections[0].PageSetup.PageWidth` और `PageHeight` को आकृतियों को सम्मिलित करने से पहले सेट करें। |
| **दो से अधिक आकृतियाँ** | अतिरिक्त `Shape` ऑब्जेक्ट बनाएं और प्रत्येक के लिए `groupShape.AppendChild(newShape)` कॉल करें। |
| **भरण रंग लागू करें** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **समूह को घुमाएँ** | `groupShape.Rotation = 45;` (डिग्री) |
| **PDF में निर्यात करें** | DOCX सहेजने के बाद `document.Save("GroupedShapes.pdf");` कॉल करें। |

## पूर्ण स्रोत कोड (चलाने के लिए तैयार)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

कोड को एक नए कंसोल प्रोजेक्ट में कॉपी करें, Aspose.Words NuGet पैकेज को रिस्टोर करें, और चलाएँ। कंसोल फ़ाइल स्थान की पुष्टि करेगा, और फ़ाइल खोलने पर समूहित ग्राफ़िक्स दिखेंगे।

## निष्कर्ष

अब आप Aspose.Words `DocumentBuilder` के साथ **Word में आकृतियों को समूहित** करने का तरीका जानते हैं। ट्यूटोरियल ने **एक खाली Word दस्तावेज़ बनाना**, **आयताकार आकृति सम्मिलित करना**, दीर्घवृत्त जोड़ना, और उन्हें `GroupShape` में मिलाना दिखाया। इस बुनियाद के साथ आप सीधे C# से अधिक समृद्ध डायग्राम, फ्लोचार्ट या कस्टम ग्राफ़िक्स बना सकते हैं।

### आगे क्या?

- **DocumentBuilder** का उपयोग तालिकाओं, हेडर और फुटर के लिए कैसे करें, इसका अन्वेषण करें।
- एनोटेटेड डायग्राम के लिए टेक्स्ट बॉक्स के साथ **insert rectangle shape Word** तकनीकों को संयोजित करें।
- **create blank word doc** को स्वचालित रिपोर्ट जनरेशन के लिए टेम्पलेट के रूप में उपयोग करें।

रंगों, ग्रेडिएंट्स और अतिरिक्त आकृतियों के साथ प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकृति बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में आकृतियाँ सम्मिलित करें](/words/english/net/working-with-shapes/insert-shape/)
- [C# का उपयोग करके Word में आयताकार आकृति बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}