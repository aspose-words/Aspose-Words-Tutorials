---
category: general
date: 2026-09-18
description: C# का उपयोग करके Word दस्तावेज़ में आयताकार आकार बनाएं। कई आकार जोड़ना,
  आकारों को समूह में जोड़ना, और Aspose.Words के साथ समूह आकार सम्मिलित करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: hi
lastmod: 2026-09-18
og_description: C# के साथ Word फ़ाइल में आयताकार आकार बनाएं। यह गाइड दिखाता है कि
  कैसे कई आकार जोड़ें, आकारों को एक समूह में जोड़ें, और Aspose.Words का उपयोग करके
  समूह आकार सम्मिलित करें।
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: C# में आयत आकार बनाएं और आकारों को समूहित करें
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: C# में आयत आकार बनाएं और कई आकारों को समूहित करें
url: /hi/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में आयताकार आकार बनाएं और कई आकारों को समूहित करें

यदि आपको Word दस्तावेज़ में **आयताकार आकार** बनाना है, तो यह ट्यूटोरियल एक पूर्ण समाधान दिखाता है। आप देखेंगे कि **कई आकार कैसे जोड़ें**, **आकारों को समूह में कैसे जोड़ें**, और **समूह आकार को कैसे सम्मिलित करें** Aspose.Words API for .NET का उपयोग करके।

आकारों के साथ काम करना रिपोर्ट, अनुबंध, या मार्केटिंग सामग्री को प्रोग्रामेटिक रूप से जनरेट करने की सामान्य आवश्यकता है। इस गाइड के अंत तक आपके पास एक चलाने योग्य C# कंसोल एप्लिकेशन होगा जो एक `.docx` फ़ाइल उत्पन्न करता है जिसमें एक आयत, एक दीर्घवृत्त, और दोनों आकारों को रखता हुआ एक समूह होता है।

एकमात्र आवश्यकताएँ हैं एक हालिया .NET SDK (6.0 या बाद का) और Aspose.Words for .NET की लाइसेंस प्राप्त कॉपी। अतिरिक्त कोई टूल आवश्यक नहीं है।

## Prerequisites

- .NET 6.0 SDK या नया  
- Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`)  
- C# सिंटैक्स का बुनियादी परिचय  

आप पैकेज को निम्नलिखित कमांड से इंस्टॉल कर सकते हैं:

```bash
dotnet add package Aspose.Words
```

## Step 1: Create rectangle shape with Aspose.Words

पहला चरण `Rectangle` प्रकार का एक `Shape` ऑब्जेक्ट बनाना है। यह ऑब्जेक्ट दस्तावेज़ में दिखाई देने वाले दृश्य आयत का प्रतिनिधित्व करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**यह क्यों महत्वपूर्ण है:** `ShapeType.Rectangle` Aspose.Words को एक ज्यामितीय आयत रेंडर करने के लिए बताता है। `Width` और `Height` सेट करने से उसका आकार पॉइंट्स में निर्धारित होता है (1 पॉइंट = 1/72 इंच)। फ़िल और स्ट्रोक रंग जोड़ने से आकार अतिरिक्त स्टाइलिंग के बिना दिखाई देता है।

## Step 2: Add multiple shapes to the document

आयत के बाद, आप किसी भी संख्या में अतिरिक्त आकार बना सकते हैं। इस उदाहरण में हम एक दीर्घवृत्त जोड़ते हैं ताकि **कई आकार जोड़ना** कैसे काम करता है दिखाया जा सके।

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**यह क्यों महत्वपूर्ण है:** प्रत्येक `new Shape` कॉल एक स्वतंत्र ड्राइंग ऑब्जेक्ट बनाता है। उन्हें क्रमशः सम्मिलित करने से आप आकारों का एक संग्रह बनाते हैं जिसे बाद में समूहित या व्यक्तिगत रूप से स्थित किया जा सकता है।

## Step 3: Add shapes to group

आकारों को समूहित करने से लेआउट प्रबंधन सरल हो जाता है क्योंकि समूह एकल नोड की तरह व्यवहार करता है। यह चरण दिखाता है कि `GroupShape` का उपयोग करके **आकारों को समूह में जोड़ना** कैसे किया जाता है।

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**यह क्यों महत्वपूर्ण है:** `GroupShape` एक कंटेनर की तरह कार्य करता है। जब आप समूह को स्थानांतरित, घुमाते या आकार बदलते हैं, तो सभी चाइल्ड आकार स्वचालित रूप से अनुसरण करते हैं। बाउंडिंग बॉक्स (200 × 200 पॉइंट) चाइल्ड आकारों के लिए समन्वय स्थान निर्धारित करता है।

## Step 4: Insert group shape into the document

अब जब समूह में आयत और दीर्घवृत्त दोनों हैं, तो आपको इच्छित स्थान पर **समूह आकार सम्मिलित** करना होगा। बिल्डर पहले ही खाली समूह रख चुका है, लेकिन आप आवश्यकता पड़ने पर इसे कहीं और भी सम्मिलित कर सकते हैं।

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**यह क्यों महत्वपूर्ण है:** `Left` और `Top` को समायोजित करने से पूरे समूह को पृष्ठ के भीतर ले जाया जाता है। दस्तावेज़ को सहेजने से आकार पदानुक्रम `.docx` फ़ाइल में लिखा जाता है जिसे Microsoft Word, LibreOffice, या किसी भी संगत व्यूअर में खोला जा सकता है।

## Complete runnable example

नीचे पूरा प्रोग्राम दिया गया है जो सभी चरणों को संयोजित करता है। कोड को एक नए कंसोल प्रोजेक्ट में कॉपी करें और `GroupShapeExample.docx` उत्पन्न करने के लिए चलाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**अपेक्षित आउटपुट:**  
`GroupShapeExample.docx` खोलने पर एकल समूह दिखेगा जिसमें हल्के‑नीले रंग का आयत और हल्के‑कोरल रंग का दीर्घवृत्त होगा, दोनों 200 × 200 पॉइंट कंटेनर के भीतर स्थित हैं। समूह को Word में एक वस्तु के रूप में चयन किया जा सकता है, जिससे पुष्टि होती है कि **आकारों को समूह में जोड़ना** सफल रहा।

## Common variations and edge cases

| Situation | Recommended adjustment |
|-----------|------------------------|
| विभिन्न आकार प्रकार (जैसे `ShapeType.Line`) | इच्छित `ShapeType` के साथ आकार बनाएं और उसकी ज्यामिति अनुसार सेट करें। |
| आकार को घुमाने की आवश्यकता | समूह में जोड़ने से पहले `shape.Rotation = 45;` (डिग्री) उपयोग करें। |
| कई समूहों वाले बड़े दस्तावेज़ | एक ही `DocumentBuilder` इंस्टेंस को पुनः उपयोग करें; प्रत्येक समूह के लिए नया बिल्डर बनाने से बचें ताकि मेमोरी ओवरहेड कम हो। |
| DOCX के बजाय PDF में सहेजना | समूह सम्मिलित करने के बाद `doc.Save("output.pdf", SaveFormat.Pdf);` कॉल करें। |

**Pro tip:** जब आपको सटीक प्लेसमेंट चाहिए तो समूह के लिए स्पष्ट `Left` और `Top` मान हमेशा सेट करें। यदि आप इन्हें छोड़ देते हैं, तो समूह बिल्डर के वर्तमान कर्सर पोजीशन को विरासत में लेता है, जिससे अप्रत्याशित लेआउट परिणाम मिल सकते हैं।

## Conclusion

अब आप जानते हैं कि C# में Word दस्तावेज़ के लिए **आयताकार आकार बनाना**, **कई आकार जोड़ना**, **आकारों को समूह में जोड़ना**, और **समूह आकार सम्मिलित करना** कैसे किया जाता है। पूरा उदाहरण दस्तावेज़ निर्माण से लेकर अंतिम फ़ाइल सहेजने तक का पूर्ण वर्कफ़्लो दर्शाता है।  

अगला, संबंधित विषयों का अन्वेषण करें जैसे **पाठ के सापेक्ष आकारों की स्थिति**, **टेक्स्ट रैपिंग लागू करना**, और **समूहित आकारों को PDF में निर्यात करना**। ये विस्तार आपको Aspose.Words के साथ परिष्कृत, प्रोग्रामेटिक दस्तावेज़ लेआउट बनाने में मदद करेंगे।

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करेंगे।

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}