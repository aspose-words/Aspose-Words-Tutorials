---
category: general
date: 2026-08-10
description: Aspose.Words का उपयोग करके प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं,
  सीखें कि वर्ड में कई शैप्स को कैसे समूहित किया जाए, वर्ड में आयत जोड़ें, और C# में
  एक समूह शैप बनाएं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: hi
lastmod: 2026-08-10
og_description: Aspose.Words के साथ प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाएं। यह गाइड
  आपको दिखाता है कि कैसे कई शैप्स को समूहित करें, वर्ड में आयत जोड़ें, और प्लेन‑टेक्स्ट
  कंटेंट कंट्रोल एम्बेड करें, सब कुछ C# में।
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं – C# में आकारों को समूहित करें
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं और C# में आकृतियों को समूहित करें
url: /hi/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाएं और C# में शैप्स को समूहित करें

यदि आपको **create word document programmatically** की आवश्यकता है, तो यह ट्यूटोरियल आपको Aspose.Words के साथ एक DOCX फ़ाइल बनाने और **group multiple shapes word** को एक साथ समूहित करने का तरीका दिखाता है। हम **add rectangle to word** और **how to create group shape** को भी कवर करेंगे, जिसमें एक आयत और एक दीर्घवृत्त दोनों शामिल हैं, साथ ही उपयोगकर्ता इनपुट के लिए एक plain‑text StructuredDocumentTag भी होगा।

आपको एक तैयार‑से‑उपयोग Word फ़ाइल मिलेगी जिसमें समूहित आयत‑दीर्घवृत्त शैप और एक कंटेंट कंट्रोल होगा जहाँ उपयोगकर्ता नाम टाइप कर सकेगा। कोड चलने के बाद Word में कोई मैन्युअल संपादन आवश्यक नहीं है।

## आपको क्या चाहिए

- .NET 6.0 या बाद का (उदाहरण .NET 6 को लक्षित करता है, लेकिन कोई भी हालिया .NET संस्करण काम करेगा)
- Aspose.Words for .NET लाइसेंस (टेस्टिंग के लिए फ्री ट्रायल काम करता है)
- Visual Studio 2022 या कोई भी C# IDE जो आप पसंद करते हैं
- C# सिंटैक्स की बुनियादी परिचितता

## प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाना – समग्र कार्यप्रवाह

प्रक्रिया तीन तार्किक चरणों में विभाजित है:

1. **Initialize** एक `Document` और एक `DocumentBuilder` – किसी भी Word फ़ाइल के निर्माण की नींव।
2. **Build a group shape** जो एक आयत और एक दीर्घवृत्त रखता है – **group multiple shapes word** और **how to create group shape** को दर्शाता है।
3. **Insert a StructuredDocumentTag (SDT)** – एक plain‑text कंटेंट कंट्रोल जो अंतिम उपयोगकर्ताओं को डेटा भरने देता है, समग्र दस्तावेज़ लेआउट के हिस्से के रूप में **add rectangle to word** को दर्शाता है।

नीचे पूर्ण, चलाने योग्य कोड दिया गया है, जिसके बाद चरण‑दर‑चरण विवरण है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### चरण 1 – दस्तावेज़ और बिल्डर को Initialize करें
`Document` ऑब्जेक्ट पूरे DOCX फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` सामग्री जोड़ने के लिए एक सुविधाजनक API प्रदान करता है। इन्हें Initialize करना पहला आवश्यक कदम है जब भी आप **create word document programmatically** करते हैं।

> **Pro tip:** यदि आप एक ही दस्तावेज़ को कई ऑपरेशनों में पुन: उपयोग करने की योजना बनाते हैं, तो अनावश्यक ऑब्जेक्ट निर्माण से बचने के लिए एक ही `DocumentBuilder` इंस्टेंस रखें।

### चरण 2 – एक group shape कंटेनर बनाएं
`ShapeType.Group` वाला एक `Shape` एक कैनवास के रूप में कार्य करता है जो अन्य शैप्स को रख सकता है। `Width` और `Height` सेट करने से समूह के लिए बाउंडिंग बॉक्स परिभाषित होता है। यह Aspose.Words में **how to create group shape** का मुख्य भाग है।

> **Edge case:** यदि समूह की चौड़ाई उसके बच्चों की संयुक्त चौड़ाई से छोटी है, तो बच्चे क्लिप हो जाएंगे। हमेशा समूह को इतना बड़ा बनाएं कि वह प्रत्येक चाइल्ड शैप को समाहित कर सके।

### चरण 3 – Word में एक आयत जोड़ें
`ShapeType.Rectangle` के साथ एक आयत बनाई जाती है। इसके `Left` और `Top` प्रॉपर्टीज़ इसे समूह के मूल बिंदु के सापेक्ष स्थित करती हैं। यह चरण **add rectangle to word** को दर्शाता है और दिखाता है कि आप सटीक प्लेसमेंट को कैसे नियंत्रित कर सकते हैं।

> **Common mistake:** `Left`/`Top` सेट करना भूल जाने पर आयत समूह के डिफ़ॉल्ट मूल (0,0) पर दिखाई देती है, जिससे अन्य बच्चों के साथ ओवरलैप हो सकता है।

### चरण 4 – समूह में एक दीर्घवृत्त (सर्कल) जोड़ें
एक दीर्घवृत्त को आयत की तरह ही जोड़ा जाता है, लेकिन `ShapeType.Ellipse` के साथ। `Left = 210` इसे आयत के दाईं ओर ले जाता है, जिससे एक ही समूह के भीतर दो दृश्य रूप से अलग शैप्स बनते हैं।

> **Why use a group?** समूह बनाकर आप बाद में दोनों शैप्स को एक ही ऑपरेशन से मूव, रोटेट या रिसाइज़ कर सकते हैं, जिससे उनका सापेक्ष लेआउट बना रहता है।

### चरण 5 – पूर्ण समूह शैप को दस्तावेज़ में Insert करें
`builder.InsertNode(groupShape)` पूरे समूह को वर्तमान कर्सर स्थान पर रखता है। चूंकि समूह में पहले से ही उसके बच्चे शामिल हैं, आपको आयत या दीर्घवृत्त के लिए अतिरिक्त Insert कॉल की आवश्यकता नहीं है।

### चरण 6 – एक plain‑text StructuredDocumentTag (SDT) बनाएं
एक StructuredDocumentTag एक कंटेंट कंट्रोल है जिसे अंतिम उपयोगकर्ता दस्तावेज़ को Word में खोलने पर भर सकते हैं। `Title = "CustomerName"` सेट करने से कंट्रोल को एक अर्थपूर्ण पहचानकर्ता मिलता है, जो बाद में डेटा एक्सट्रैक्शन के लिए उपयोगी है।

> **Why a plain‑text SDT?** यह इनपुट को केवल plain text तक सीमित करता है, जिससे आकस्मिक फॉर्मेटिंग से बचा जा सके जो डाउनस्ट्रीम प्रोसेसिंग को तोड़ सकती है।

### चरण 7 – दस्तावेज़ को Save करें
`doc.Save("GroupAndSDT.docx")` फ़ाइल को डिस्क पर लिखता है। परिणामी DOCX में समूहित शैप्स और SDT होते हैं। Microsoft Word में फ़ाइल खोलने पर एक आयत को एक सर्कल के बगल में दिखेगा, दोनों को एक ही ऑब्जेक्ट के रूप में चयनित किया जा सकता है, उसके बाद “Enter name here …” प्लेसहोल्डर दिखेगा।

#### अपेक्षित आउटपुट
- निष्पादन फ़ोल्डर में **GroupAndSDT.docx** नामक फ़ाइल।
- Word में: एक समूहित शैप (आयत + दीर्घवृत्त) जिसे आप एक इकाई के रूप में मूव कर सकते हैं।
- समूह के ठीक नीचे, एक ग्रे‑शेडेड कंटेंट कंट्रोल जो उपयोगकर्ता को नाम टाइप करने के लिए प्रेरित करता है।

## अतिरिक्त विविधताएँ और सर्वोत्तम प्रथाएँ

### विभिन्न शैप प्रकारों का उपयोग
आप `ShapeType.Rectangle` या `ShapeType.Ellipse` को किसी भी अन्य `ShapeType` (जैसे, `ShapeType.Polygon`, `ShapeType.Line`) से बदल सकते हैं। समूह बनाने की लॉजिक समान रहती है।

### फ़िल रंग और बॉर्डर सेट करना
फ़िल और स्ट्रोक जोड़ने से दृश्य अंतर बेहतर होता है, विशेष रूप से जब दस्तावेज़ को गैर‑तकनीकी हितधारकों के साथ साझा किया जाता है।

```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

### पूरे समूह को घुमाना
समूह को घुमाना प्रत्येक बच्चे को अलग‑अलग घुमाने की तुलना में अधिक कुशल है।

```csharp
groupShape.Rotation = 45; // rotates both shapes together
```

### PDF में निर्यात करना
यदि आपको PDF संस्करण चाहिए, तो बस कॉल करें:

```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```

## सामान्य समस्याएँ और उन्हें कैसे टालें

| लक्षण | कारण | समाधान |
|---------|-------|


## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करती हैं।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह शैप बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [C# का उपयोग करके Word में आयत शैप बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [छाया वाली आयत शैप के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}