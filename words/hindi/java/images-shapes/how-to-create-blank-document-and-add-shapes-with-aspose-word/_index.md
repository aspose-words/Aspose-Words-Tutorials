---
category: general
date: 2026-09-30
description: Aspose.Words का उपयोग करके C# में एक खाली दस्तावेज़ बनाएं और आयताकार
  आकार, दीर्घवृत्त, तथा कई आकारों को समूहित करें। सीखें कि आकार कैसे डालें और समूह
  कैसे बनाएं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: hi
lastmod: 2026-09-30
og_description: C# में एक खाली दस्तावेज़ बनाएं और Aspose.Words के साथ आकार सम्मिलित
  करना तथा कई आकारों को समूहित करना सीखें। चरण‑दर‑चरण ट्यूटोरियल का पालन करें।
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: C# में एक खाली दस्तावेज़ बनाएं और आकृतियों को समूहित करें – Aspose.Words
  गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: C# में Aspose.Words के साथ खाली दस्तावेज़ कैसे बनाएं और शैप्स जोड़ें
url: /hi/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words in C# के साथ खाली दस्तावेज़ कैसे बनाएं और आकार जोड़ें

यदि आपको **create blank document** बनाकर उसे ग्राफ़िक्स से भरना है, तो यह गाइड आपको बिल्कुल वही दिखाएगा। आप देखेंगे कि **insert rectangle shape** कैसे डालें, अन्य ड्राइंग ऑब्जेक्ट जोड़ें, और फिर **group multiple shapes** करके उन्हें एक इकाई की तरह व्यवहार कराएं।

आकारों के साथ काम करना अनुबंध, प्रमाणपत्र या कस्टम रिपोर्ट जनरेट करने के समय एक सामान्य आवश्यकता है। इस ट्यूटोरियल में आप पूरी वर्कफ़्लो सीखेंगे, दस्तावेज़ को इनिशियलाइज़ करने से लेकर अंतिम फ़ाइल को सेव करने तक, Aspose.Words API for .NET का उपयोग करके।

## आवश्यकताएँ

* .NET 6.0 (या बाद का) SDK स्थापित हो  
* एक वैध Aspose.Words for .NET लाइसेंस (इस उदाहरण के लिए फ्री ट्रायल काम करता है)  
* Visual Studio 2022 या Visual Studio Code जैसा IDE  

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## How to create blank document and work with shapes

पहला कदम `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट मेमोरी में Word फ़ाइल का प्रतिनिधित्व करता है और आपको `DocumentBuilder` तक पहुंच देता है, जो कंटेंट डालने का मुख्य टूल है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**क्यों यह महत्वपूर्ण है:** एक खाली दस्तावेज़ आपको एक साफ़ कैनवास देता है। `DocumentBuilder` वर्तमान इंसर्शन पॉइंट को बनाए रखता है, इसलिए आप जो भी आकार जोड़ते हैं वह स्वचालित रूप से उचित पृष्ठ पर रख दिया जाता है।

## Insert rectangle shape and other shapes

अब हम एक आयत और एक अंडाकार जोड़ते हैं। दोनों कॉल्स एक ही `InsertShape` मेथड का उपयोग करती हैं, जो Aspose.Words में **how to insert shapes** का अनुशंसित तरीका है।

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*`InsertShape` मेथड आकार को वर्तमान कर्सर स्थान पर स्वचालित रूप से रखता है.* यदि आपको सटीक प्लेसमेंट चाहिए, तो इंसर्शन के बाद `Shape.Left` और `Shape.Top` को समायोजित कर सकते हैं।

## Group multiple shapes into a single object

अब हम आयत और अंडाकार को एक तार्किक इकाई में मिलाते हैं। ग्रुपिंग तब उपयोगी होती है जब आप कई आकारों को एक साथ मूव या रिसाइज़ करना चाहते हैं।

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**यह कैसे काम करता है:** `InsertGroupShape` एक कंटेनर बनाता है जो किसी भी अन्य `Shape` की तरह व्यवहार करता है। `AppendChild` को कॉल करके आप मौजूदा आकारों को कंटेनर में ले जाते हैं, जो उनके रिलेटिव कोऑर्डिनेट्स को स्वचालित रूप से अपडेट करता है।

### व्यावहारिक टिप

यदि बाद में आपको दो से अधिक आकारों के लिए प्रोग्रामेटिक रूप से **how to create group** बनाना हो, तो प्रत्येक अतिरिक्त `Shape` इंस्टेंस के लिए `AppendChild` दोहराएँ। समूह में कोई भी संख्या में ड्राइंग ऑब्जेक्ट्स हो सकते हैं, जिसमें चित्र, टेक्स्ट बॉक्स, या यहाँ तक कि अन्य समूह भी शामिल हैं।

## Full example – how to insert shapes and save the document

नीचे पूरा, चलाने योग्य प्रोग्राम दिया गया है जो अब तक चर्चा किए गए सभी चरणों को दर्शाता है। कोड चलाने पर `ShapesDemo.docx` फ़ाइल बनती है जिसमें एक आयत, एक अंडाकार, और एक ग्रुप्ड आकार शामिल है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**अपेक्षित आउटपुट:** Microsoft Word में `ShapesDemo.docx` खोलने पर एक ही पृष्ठ पर नीली आयत, हरी अंडाकार, और एक ग्रे बॉर्डर दिखेगा जो समूह को दर्शाता है। समूह को मूव करने से दोनों आकार एक साथ चलते हैं, जिससे **group multiple shapes** ऑपरेशन सफल हुआ यह पुष्टि होती है।

## Common questions and edge‑case handling

| प्रश्न | उत्तर |
|----------|--------|
| *यदि मुझे आकार किसी विशिष्ट पृष्ठ पर चाहिए तो क्या करें?* | आकार डालने से पहले `builder.MoveToDocumentEnd();` कॉल करें, या किसी विशेष सेक्शन को टार्गेट करने के लिए `builder.MoveToSection(sectionIndex);` उपयोग करें। |
| *क्या मैं ग्रुप्ड आकार के अंदर टेक्स्ट जोड़ सकता हूँ?* | हाँ। `ShapeType.TextBox` प्रकार का `Shape` बनाएं, उसका टेक्स्ट कॉन्फ़िगर करें, और फिर उसे `GroupShape` में `AppendChild` करें। |
| *क्या आकार के आयाम पॉइंट्स में हैं या पिक्सेल में?* | Aspose.Words **points** (1 pt = 1/72 inch) का उपयोग करता है। यह प्रिंटर और डिस्प्ले पर सुसंगत साइजिंग सुनिश्चित करता है। |
| *ग्रुप की रोटेशन कैसे बदलें?* | `groupShape.RotationAngle = 45;` (डिग्री) सेट करें। सभी चाइल्ड आकार समूह के मूल बिंदु के चारों ओर घुमेंगे। |

## निष्कर्ष

आप अब जानते हैं कि **create blank document**, **insert rectangle shape**, **how to insert shapes** जैसे एलिप्स, और **group multiple shapes** को एकल ऑब्जेक्ट में कैसे बनाएं, Aspose.Words for .NET का उपयोग करके। पूर्ण कोड उदाहरण अनुशंसित दृष्टिकोण को दर्शाता है, और ऊपर दी गई टिप्स आपको समाधान को अधिक जटिल परिदृश्यों जैसे टेक्स्ट बॉक्स जोड़ना या समूह को घुमाना आदि में अनुकूलित करने में मदद करती हैं।

और अधिक खोजने के लिए तैयार हैं? समूह में एक चित्र आकार जोड़ें, विभिन्न फ़िल रंगों के साथ प्रयोग करें, या एक मल्टी‑पेज रिपोर्ट जनरेट करें जहाँ प्रत्येक पृष्ठ में अपना ग्रुप्ड डायग्राम हो। वही सिद्धांत लागू होते हैं, इसलिए आप इस पैटर्न को किसी भी दस्तावेज़‑ऑटोमेशन प्रोजेक्ट में स्केल कर सकते हैं।

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच खोजने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में आकार डालें](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}