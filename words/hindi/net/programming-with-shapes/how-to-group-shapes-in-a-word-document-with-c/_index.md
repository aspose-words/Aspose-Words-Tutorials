---
category: general
date: 2026-08-14
description: C# का उपयोग करके Word दस्तावेज़ में आकारों को समूहित कैसे करें। Word
  दस्तावेज़ बनाना सीखें, आयताकार आकार डालें, Word में आकारों को समूहित करें, और दस्तावेज़
  को docx के रूप में सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: hi
lastmod: 2026-08-14
og_description: C# का उपयोग करके Word दस्तावेज़ में आकृतियों को कैसे समूहित करें।
  इस पूर्ण ट्यूटोरियल का पालन करके Word फ़ाइल बनाएं, आयताकार आकृति डालें, Word में
  आकृतियों को समूहित करें, और परिणाम को docx के रूप में सहेजें।
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: C# के साथ Word दस्तावेज़ में आकृतियों को समूहित करने का चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: C# के साथ Word दस्तावेज़ में आकृतियों को कैसे समूहित करें
url: /hi/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word दस्तावेज़ में आकृतियों को समूहित कैसे करें

यदि आपको Word दस्तावेज़ में **आकृतियों को समूहित करने** की आवश्यकता है, तो यह गाइड C# और Aspose.Words लाइब्रेरी का उपयोग करके सटीक चरण दिखाता है। आप देखेंगे कि कैसे Word दस्तावेज़ बनाएं, आयताकार आकृति डालें, Word में आकृतियों को समूहित करें, और अंत में **दस्तावेज़ को docx के रूप में सहेजें**—सभी एक ही चलाने योग्य प्रोग्राम में।

आकृतियों को बनाना और उनका संचालन करना रिपोर्ट, अनुबंध, या मार्केटिंग ब्रोशर को प्रोग्रामेटिक रूप से जेनरेट करने की सामान्य आवश्यकता है। इस ट्यूटोरियल के अंत तक आपके पास एक पुन: उपयोग योग्य कोड स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित हों:

- .NET 6.0 या बाद का संस्करण स्थापित हो  
- Visual Studio 2022 (या कोई भी IDE जो .NET को सपोर्ट करता हो)  
- Aspose.Words for .NET लाइसेंस (या फ्री ट्रायल)  
- C# सिंटैक्स की बुनियादी समझ  

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## Word दस्तावेज़ में आकृतियों को समूहित करने का तरीका

समाधान का मूल पाँच‑कदम प्रक्रिया है। प्रत्येक कदम को विस्तार से समझाया गया है, और लेख के अंत में पूरा स्रोत कोड दिया गया है।

### चरण 1: नया खाली दस्तावेज़ बनाएं

जब आप प्रोग्रामेटिक रूप से **Word दस्तावेज़ बनाना** चाहते हैं, तो पहला काम `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट मेमोरी में पूरे .docx फ़ाइल का प्रतिनिधित्व करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**यह क्यों महत्वपूर्ण है:** `DocumentBuilder` एक हाई‑लेवल हेल्पर है जो आपको टेक्स्ट, टेबल और आकृतियों को मैन्युअल रूप से नोड ट्री को हैंडल किए बिना डालने की सुविधा देता है।

### चरण 2: आयताकार आकृति डालें

**आयताकार आकृति डालने** के प्रदर्शन के लिए हम `InsertShape` मेथड का उपयोग करते हैं। यह आयत समूह का पहला सदस्य होगा।

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**यह क्यों महत्वपूर्ण है:** आकृतियों की स्थिति इन्सर्शन पॉइंट के सापेक्ष निर्धारित होती है। फ़िल रंग सेट करने से आप उत्पन्न दस्तावेज़ खोलने पर आकृति को स्पष्ट रूप से देख सकते हैं।

### चरण 3: दीर्घवृत्त आकृति डालें

अब हम **दीर्घवृत्त आकृति डालते** हैं (API इसे `Ellipse` कहता है)। यह समूह का दूसरा सदस्य होगा।

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**यह क्यों महत्वपूर्ण है:** आयत के तुरंत बाद दीर्घवृत्त डालने से दोनों आकृतियाँ एक ही पैराग्राफ में आ जाती हैं, जिससे बाद में समूह बनाना आसान हो जाता है।

### चरण 4: आयत और दीर्घवृत्त को समूहित करें

अब हम मुख्य प्रश्न **Word दस्तावेज़ में आकृतियों को समूहित कैसे करें** का उत्तर देते हैं। Aspose.Words `AppendGroupShape` प्रदान करता है जिससे आप एक समूह कंटेनर बनाते हैं, और फिर उस कंटेनर पर `Group()` कॉल करते हैं।

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**यह क्यों महत्वपूर्ण है:** समूहित होने के बाद, `groupedShape` पर किया गया कोई भी ट्रांसफ़ॉर्मेशन (स्थानांतरित करना, आकार बदलना, घुमाना) स्वचालित रूप से आयत और दीर्घवृत्त दोनों पर लागू होता है। यह जेनरेटेड दस्तावेज़ों में लेआउट स्थिरता बनाए रखने के लिए आवश्यक है।

### चरण 5: दस्तावेज़ को DOCX फ़ाइल के रूप में सहेजें

अंतिम कदम **दस्तावेज़ को docx के रूप में सहेजना** है। आप कोई भी पाथ चुन सकते हैं; उदाहरण में प्लेसहोल्डर `"YOUR_DIRECTORY"` का उपयोग किया गया है जिसे आपको वास्तविक फ़ोल्डर से बदलना चाहिए।

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**यह क्यों महत्वपूर्ण है:** DOCX के रूप में सहेजने से समूह मेटाडेटा संरक्षित रहता है, इसलिए जब आप फ़ाइल को Microsoft Word में खोलते हैं तो आयत और दीर्घवृत्त एक ही ऑब्जेक्ट के रूप में दिखेंगे।

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जो सभी पाँच चरणों को मिलाता है। इसे एक नए कंसोल प्रोजेक्ट में कॉपी करें, Aspose.Words NuGet पैकेज रिस्टोर करें, और चलाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### अपेक्षित आउटपुट

जब आप `groupedShapes.docx` को Microsoft Word में खोलते हैं, तो आपको एक हल्के‑नीले रंग की आयत और एक हल्के‑कोरल रंग की दीर्घवृत्त एक साथ लॉक हुए दिखेंगे। किसी भी आकृति पर क्लिक करने से दोनों चयनित हो जाएँगे, जिससे आप उन्हें एक ही इकाई के रूप में मूव या रिसाइज़ कर सकते हैं।

## सामान्य प्रश्न और किनारे के मामलों

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं दो से अधिक आकृतियों को समूहित कर सकता हूँ?** | हाँ। `AppendGroupShape` में किसी भी संख्या में `Shape` ऑब्जेक्ट पास कर सकते हैं। यह मेथड एक एरे स्वीकार करता है, इसलिए आप कलेक्शन को डायनामिक रूप से बना सकते हैं। |
| **यदि समूह को टेबल सेल में एंकर करना हो तो क्या करें?** | आकृतियों को सेल के पैराग्राफ के अंदर डालें, फिर उस पैराग्राफ पर `AppendGroupShape` कॉल करें। समूह सेल की एंकरिंग को विरासत में ले लेगा। |
| **क्या समूह बनाना अंतर्निहित XML को प्रभावित करता है?** | Aspose.Words `<w:grpSp>` एलिमेंट लिखता है जिसमें चाइल्ड आकृतियाँ होती हैं। Word इसे समूह के रूप में पहचानता है और सापेक्ष स्थिति को संरक्षित रखता है। |
| **बाद में समूह को कैसे अनग्रुप करूँ?** | `groupedShape.Ungroup()` कॉल करें; यह मेथड व्यक्तिगत आकृतियों को वापस देता है ताकि आप उन्हें अलग‑अलग मैनीपुलेट कर सकें। |
| **बहुत सारी आकृतियों को समूहित करने पर प्रदर्शन पर असर पड़ता है?** | स्वयं समूह बनाना महँगा नहीं है, लेकिन बहुत बड़े समूह (सैकड़ों आकृतियों) रेंडरिंग और फ़ाइल आकार को बढ़ा सकते हैं। यदि आकार समस्या बनता है तो इमेज को फ्लैटन करने पर विचार करें। |

## प्रो टिप्स

- **स्पष्ट स्थितियाँ सेट करें** (`Left`, `Top`) यदि आपको समूह बनाने से पहले सटीक संरेखण चाहिए।  
- **`Shape.WrapType = WrapType.Inline`** का उपयोग करें जब आप चाहते हैं कि समूह पैराग्राफ एलिमेंट की तरह व्यवहार करे, न कि फ़्लोटिंग ऑब्जेक्ट।  
- **समूह पर लाइन स्टाइल लागू करें** (`groupedShape.LineFormat`) ताकि पूरी कलेक्शन को बॉर्डर मिल सके।  
- **समूह को पुन: उपयोग करें**: `Group()` कॉल करने के बाद, आप `groupedShape` को क्लोन कर सकते हैं और क्लोन को दस्तावेज़ में कहीं और इन्सर्ट कर सकते हैं।

## अगले कदम

अब जब आप **Word दस्तावेज़ में आकृतियों को समूहित करने** का तरीका जानते हैं, तो आप संबंधित विषयों का अन्वेषण कर सकते हैं, जैसे:

- **कस्टम टेक्स्ट या इमेज के साथ आयताकार आकृति डालें**।  
- **नेस्टेड समूह** (समूह के भीतर समूह) बनाकर जटिल डायग्राम बनाएं।  
- **दस्तावेज़ को PDF के रूप में एक्सपोर्ट करें** जबकि आकृति समूह को संरक्षित रखें (`doc.Save("output.pdf", SaveFormat.Pdf)`)।  

इनमें से प्रत्येक यहाँ कवर किए गए मूल सिद्धांतों पर आधारित है, इसलिए आप अपने Word ऑटोमेशन टूलकिट को आगे बढ़ाने के लिए तैयार हैं।

## निष्कर्ष

इस ट्यूटोरियल ने C# का उपयोग करके Word दस्तावेज़ में **आकृतियों को समूहित करने** का प्रदर्शन किया। आपने **Word दस्तावेज़ बनाना**, **आयताकार आकृति डालना**, **Word में आकृतियों को समूहित करना**, और अंत में **दस्तावेज़ को docx के रूप में सहेजना** सीखा। पूर्ण, चलाने योग्य उदाहरण और व्यावहारिक टिप्स के साथ, आप किसी भी दस्तावेज़‑जनरेशन वर्कफ़्लो में आकृति समूह को एकीकृत कर सकते हैं। हैप्पी कोडिंग!

## आगे क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकते हैं और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकते हैं।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकृति बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में आकृतियों को डालें](/words/english/net/working-with-shapes/insert-shape/)
- [C# – चरण‑दर‑चरण गाइड के साथ Word में आयताकार आकृति बनाएं](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}