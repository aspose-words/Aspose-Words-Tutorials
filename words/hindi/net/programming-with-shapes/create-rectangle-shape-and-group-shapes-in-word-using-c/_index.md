---
category: general
date: 2026-09-08
description: C# के साथ Word दस्तावेज़ में आयताकार आकार बनाएं। आकार का आकार सेट करना,
  कई आकारों को समूहित करना, और प्रोग्रामेटिक रूप से खाली Word दस्तावेज़ बनाना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: hi
lastmod: 2026-09-08
og_description: C# के साथ Word दस्तावेज़ में आयताकार आकार बनाएं। यह गाइड दिखाता है
  कि आकार का आकार कैसे सेट करें, कई आकारों को समूहित करें, और प्रोग्रामेटिक रूप से
  एक खाली Word दस्तावेज़ बनाएं।
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: C# का उपयोग करके Word में आयताकार आकार बनाएं और आकारों को समूहित करें
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# का उपयोग करके Word में आयताकार आकार बनाएं और आकारों को समूहित करें
url: /hi/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# का उपयोग करके Word में आयताकार आकार बनाएं और आकारों को समूहित करें

यदि आपको Word फ़ाइल के अंदर **create rectangle shape** है, तो यह ट्यूटोरियल आपको एक पूर्ण, तुरंत चलाने योग्य समाधान देता है। आप देखेंगे कि shape size कैसे सेट करें, कई shapes को समूहित करें, और शुरू से एक खाली Word दस्तावेज़ कैसे बनाएं—सभी Aspose.Words for .NET लाइब्रेरी के साथ।

प्रोग्रामेटिक रूप से Word दस्तावेज़ों के साथ काम करना अक्सर कई छोटे विवरणों को संभालने जैसा लगता है। इस गाइड के अंत तक आपके पास एक ही मेथड होगा जो एक `.docx` फ़ाइल उत्पन्न करता है जिसमें एक आयत और एक दीर्घवृत्त समूहित होते हैं, आगे के संपादन या प्रिंटिंग के लिए तैयार।

## आवश्यकताएँ

* .NET 6.0 या बाद का (कोड .NET Framework 4.6+ के साथ भी काम करता है)
* एक लाइसेंस प्राप्त **Aspose.Words for .NET** कॉपी (आप मुफ्त मूल्यांकन कुंजी का उपयोग कर सकते हैं)
* Visual Studio 2022 या Visual Studio Code जैसे IDE
* C# सिंटैक्स की बुनियादी परिचितता

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## चरण 1: एक खाली Word दस्तावेज़ बनाएं

पहला चरण एक खाली दस्तावेज़ बनाना है जो आकारों को होस्ट करेगा। यह *create blank word document* आवश्यकता को पूरा करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

एक खाली दस्तावेज़ बनाना आपको एक साफ़ कैनवास देता है। `Document` ऑब्जेक्ट पूरे `.docx` फ़ाइल का प्रतिनिधित्व करता है, और इसका `FirstSection.Body.FirstParagraph` नए नोड्स के लिए डिफ़ॉल्ट इंसर्शन पॉइंट है।

## चरण 2: आयताकार आकार बनाएं

अब आप आयत जोड़ सकते हैं। यहाँ **create rectangle shape** ऑपरेशन होता है।

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

आयाम सीधे सेट करने से **set shape size** कीवर्ड का उत्तर मिलता है। सभी size मान पॉइंट्स में व्यक्त किए जाते हैं, जो अंतिम दस्तावेज़ में आकार की उपस्थिति पर सटीक नियंत्रण प्रदान करता है।

## चरण 3: अतिरिक्त आकार बनाएं (दीर्घवृत्त)

एक सामान्य उपयोग केस कई आकारों को मिलाना है। यहाँ हम एक दीर्घवृत्त जोड़ते हैं जो बाद में उसी कंटेनर को साझा करेगा।

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

इस बिंदु पर दोनों आकार अभी भी स्वतंत्र हैं। अगला चरण दिखाता है कि **group multiple shapes** को एक साथ कैसे समूहित किया जाए।

## चरण 4: Word में आकारों को समूहित करें

आकारों को समूहित करने से आप उन्हें एक इकाई के रूप में स्थानांतरित, आकार बदल या फ़ॉर्मेट कर सकते हैं। यह **group shapes in word** और **group multiple shapes** आवश्यकताओं को पूरा करता है।

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

`GroupShape.Bounds` प्रॉपर्टी चाइल्ड आकारों के लिए कोऑर्डिनेट सिस्टम निर्धारित करती है। आयत और दीर्घवृत्त को एक ही `GroupShape` के अंदर रखकर, आप बाद में उन्हें एक ही कॉल से साथ में स्थानांतरित या घुमा सकते हैं।

## चरण 5: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल में वह समूहित आकार होंगे जो आपने अभी बनाए हैं।

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

प्रोग्राम चलाने के बाद, Microsoft Word में `GroupedShapes.docx` खोलें। आपको एक आयत और एक दीर्घवृत्त एक साथ समूहित दिखना चाहिए; एक आकार का चयन करने से दूसरा भी चयनित हो जाता है, जिससे समूह बनना सफल हुआ यह पुष्टि होती है।

## पूर्ण स्रोत कोड

निम्नलिखित पूर्ण प्रोग्राम को एक नए console‑app प्रोजेक्ट में कॉपी करें और चलाएँ। कोई अतिरिक्त कोड आवश्यक नहीं है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### अपेक्षित आउटपुट

प्रोग्राम चलाने से `GroupedShapes.docx` बनता है। Word में फ़ाइल खोलने पर दिखता है:

* **rectangle** (100 pt × 50 pt) नीले बॉर्डर और हल्के‑ग्रे फ़िल के साथ।
* **ellipse** (80 pt × 80 pt) गहरे‑हरा बॉर्डर और हल्के‑पीले फ़िल के साथ।
* दोनों आकार एक ही समूह में हैं, इसलिए एक को ले जाने से दूसरा भी साथ में चलता है।

## सामान्य प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं समूह में दो से अधिक आकार जोड़ सकता हूँ?** | हाँ। अतिरिक्त `Shape` ऑब्जेक्ट बनाएं और प्रत्येक के लिए `group.AppendChild(yourShape)` कॉल करें। |
| **यदि मुझे समूह को घुमाना हो तो क्या करें?** | `group.RotationAngle = 45;` (डिग्री) सेट करें। सभी चाइल्ड आकार एक साथ घुमते हैं। |
| **क्या दस्तावेज़ सहेजने के बाद आकारों को समूहित करना संभव है?** | आपको सहेजने से पहले दस्तावेज़ संरचना को संशोधित करना होगा; अन्यथा आपको फ़ाइल लोड करनी होगी, आकारों को ढूँढ़ना होगा, और समूह को पुनः बनाना होगा। |
| **क्या मुझे किसी ऑब्जेक्ट को डिस्पोज़ करना चाहिए?** | Aspose.Words अपने संसाधनों का प्रबंधन करता है, लेकिन यदि आप मैन्युअल रूप से स्ट्रीम खोलते हैं तो `FileStream` ऑब्जेक्ट को डिस्पोज़ करना चाहिए। |
| **क्या कोड .doc (बाइनरी) फ़ॉर्मेट के साथ काम करेगा?** | हाँ, `doc.Save("output.doc")` बदलें। समूह बनावट समान रहती है। |

## निष्कर्ष

अब आप जानते हैं कि C# का उपयोग करके Word फ़ाइल के अंदर **create rectangle shape**, **set shape size**, और **group multiple shapes** कैसे करें। यह तरीका आपको प्रोग्रामेटिक रूप से जटिल डायग्राम, वॉटरमार्क, या टेम्पलेट‑आधारित रिपोर्ट बिना मैन्युअल संपादन के बनाने देता है।

### अगले कदम

* **group shapes in word** को और अधिक एक्सप्लोर करें, उसी समूह में टेक्स्ट बॉक्स या इमेज जोड़कर।
* `SetShapeSize` पैटर्न का उपयोग करके पेज लेआउट के आधार पर डायमेंशन डायनामिकली कैलकुलेट करें।
* इस तकनीक को मेल‑मर्ज फ़ील्ड्स के साथ मिलाकर बड़े पैमाने पर व्यक्तिगत दस्तावेज़ जनरेट करें।

विभिन्न आकार प्रकार, रंग, और समूह ट्रांसफ़ॉर्मेशन के साथ प्रयोग करने में संकोच न करें। कोडिंग का आनंद लें!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [छाया वाले आयताकार आकार के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [छाया वाले आयत के साथ Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}