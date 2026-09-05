---
category: general
date: 2026-09-05
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में आयताकार आकार बनाएं, फिर
  एलीप्स शब्द सम्मिलित करना और Word में आकारों को समूहित करना सीखें ताकि अधिक समृद्ध
  लेआउट प्राप्त हो सके।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: hi
lastmod: 2026-09-05
og_description: Aspose.Words के साथ Word दस्तावेज़ में आयताकार आकार बनाएं, फिर जटिल
  लेआउट के लिए Word में दीर्घवृत्त शब्द सम्मिलित करने और आकारों को समूहित करने का
  तरीका देखें।
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Word में आयताकार आकार बनाएं और आकारों को समूहित करें – Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words के साथ Word में आयताकार आकार कैसे बनाएं और आकारों को समूहित करें
url: /hi/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ Word में आयताकार आकार बनाना और आकारों को समूहित करना

यदि आपको Word दस्तावेज़ में **आयताकार आकार** बनाना है, तो यह गाइड Aspose.Words for .NET के साथ सटीक चरण दिखाता है। आप यह भी देखेंगे कि Word में एलिप्स कैसे डालें, आकारों को समूहित करें, और परिणाम को DOCX फ़ाइल के रूप में सहेजें। यह समाधान किसी भी .NET 6+ प्रोजेक्ट में काम करता है और सर्वर पर Microsoft Office स्थापित होने की आवश्यकता नहीं है।

यह ट्यूटोरियल प्रोजेक्ट सेटअप से लेकर सामान्य लेआउट समस्याओं को संभालने तक सब कुछ कवर करता है, ताकि आप कोड को कॉपी करके तुरंत चला सकें।

## आवश्यकताएँ

* .NET 6 SDK या बाद का संस्करण स्थापित हो  
* एक NuGet‑संगत IDE (Visual Studio, Rider, या VS Code)  
* Aspose.Words for .NET लाइसेंस (या एक अस्थायी इवैल्यूएशन कुंजी)  
* C# और Word दस्तावेज़ संरचना का बुनियादी ज्ञान  

ये आइटम कोड को कम्पाइल करने और आकारों को सही ढंग से रेंडर करने में मदद करते हैं।

## चरण 1: प्रोजेक्ट सेट अप करें और Aspose.Words जोड़ें

एक नया कंसोल प्रोजेक्ट बनाएं और Aspose.Words पैकेज जोड़ें:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

यह पैकेज `Document`, `DocumentBuilder`, `Shape`, और `GroupShape` क्लासेज़ प्रदान करता है जो इस ट्यूटोरियल में पूरे समय उपयोग होते हैं।

## चरण 2: ब्लैंक दस्तावेज़ और बिल्डर इनिशियलाइज़ करें

`Document` ऑब्जेक्ट पूरे Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` आपको प्रोग्रामेटिक रूप से कंटेंट डालने की अनुमति देता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

पहले दस्तावेज़ बनाना सुनिश्चित करता है कि सभी बाद के आकार संचालन के पास एक वैध कंटेनर हो।

## चरण 3: **आयताकार आकार** बनाएं और उसके आयाम सेट करें

आयत सबसे सामान्य कंटेनर है टेक्स्ट या इमेज के लिए। आप इसका आकार पॉइंट्स में परिभाषित करते हैं (1 pt ≈ 1/72 इंच)।

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

इस चरण का महत्व: `Shape` क्लास ज्योमेट्री, फ़िल, और लाइन प्रॉपर्टीज़ को समेटे हुए है। इन्सर्शन से पहले `Width` और `Height` सेट करने से आकार अपेक्षित आकार में दिखाई देता है।

## चरण 4: **Ellipse शब्द कैसे डालें** – एक एलिप्स आकार जोड़ें

एलिप्स को आइकन, मार्कर, या सजावटी तत्वों के लिए उपयोग किया जा सकता है। कोड आयत निर्माण को प्रतिबिंबित करता है, केवल `ShapeType` बदलता है।

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

`FillColor` और `Line.Color` प्रॉपर्टीज़ दिखाती हैं कि बाहरी इमेज के बिना उपस्थिति को कैसे कस्टमाइज़ किया जाए।

## चरण 5: **Word में आकारों को समूहित करें** – आयताकार और एलिप्स को मिलाएं

समूह बनाना आपको कई आकारों को एक इकाई के रूप में मूव, रिसाइज़ या रोटेट करने देता है। यह तब आवश्यक होता है जब आपको एक संयुक्त ग्राफिक (जैसे लेबल वाला आइकन) चाहिए।

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

जब आप `AppendChild` कॉल करते हैं, तो मूल आकार मुख्य दस्तावेज़ प्रवाह से हट जाते हैं और `GroupShape` के चाइल्ड बन जाते हैं। समूह एकल आकार की तरह व्यवहार करता है, जिससे बाद के लेआउट समायोजन सरल हो जाते हैं।

## चरण 6: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप कोई भी समर्थित फ़ॉर्मेट (`.docx`, `.pdf`, `.html`, आदि) चुन सकते हैं। इस ट्यूटोरियल के लिए हम मूल Word फ़ॉर्मेट रखते हैं।

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

प्रोग्राम चलाने के बाद, *GroupShape.docx* को Microsoft Word में खोलें। आपको एक आयत और एक एलिप्स समूहित हुए दिखेंगे, जो आपने निर्दिष्ट कोऑर्डिनेट्स पर स्थित हैं।

## सामान्य विविधताएँ और किनारे के मामले

| स्थिति | क्या बदलें | कारण |
|-----------|----------------|--------|
| **विभिन्न आकार इकाइयाँ** | इंच के लिए `ConvertUtil.InchToPoint(2.5)` या मिलीमीटर के लिए `ConvertUtil.MillimeterToPoint(30)` का उपयोग करें। | जब आप गैर‑पॉइंट मापों के साथ काम करते हैं तो कोड पढ़ने योग्य रहता है। |
| **आयत के अंदर टेक्स्ट जोड़ना** | `Paragraph` नोड बनाएं, उसकी `Text` प्रॉपर्टी सेट करें, और `AppendChild` के माध्यम से इसे `rectangleShape` में जोड़ें। | अलग टेक्स्ट बॉक्स के बिना आकार को लेबल करने की अनुमति देता है। |
| **समूह को घुमाना** | `groupShape.Rotation = 45;` (डिग्री) सेट करें। | तिरछे बैज या वॉटरमार्क बनाने में उपयोगी। |
| **PDF के रूप में सहेजना** | `doc.Save("GroupShape.pdf");` को कॉल करें। | Aspose.Words PDF आउटपुट के लिए वेक्टर आकारों को स्वचालित रूप से रास्टराइज़ करता है। |
| **एकाधिक समूह** | अतिरिक्त `GroupShape` इंस्टेंस बनाएं और अपेंड/इंसर्ट चरणों को दोहराएं। | कई स्वतंत्र संयोजनों के साथ जटिल पेज लेआउट सक्षम करता है। |

### प्रो टिप

हमेशा आकार **समूह बनाने से पहले** जोड़ें। यदि आप किसी ऐसे आकार को समूहित करने की कोशिश करते हैं जो पहले से किसी अन्य समूह का हिस्सा है, तो Aspose.Words `ArgumentException` फेंकता है। समूह को एक ही मेथड में बनाना इस रनटाइम त्रुटि से बचाता है।

### ध्यान रखें

* **कोऑर्डिनेट सिस्टम** – `Left` और `Top` पेज के बाएँ और ऊपर के मार्जिन से मापे जाते हैं, दस्तावेज़ किनारे से नहीं। इसको समझने में गलती करने से आकार पेज के बाहर जा सकते हैं।  
* **लाइसेंसिंग** – वैध लाइसेंस के बिना, सहेजा गया दस्तावेज़ “Aspose.Words for .NET Evaluation” वॉटरमार्क दिखाएगा। कोड में जल्दी लाइसेंस लागू करें (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) ताकि यह न हो।

## पूर्ण स्रोत कोड (चलाने योग्य)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

इस प्रोग्राम को चलाने से *GroupShape.docx* बनता है जिसमें समूहित आकार ठीक उसी तरह होते हैं जैसा वर्णित है।

## निष्कर्ष

आप अब जानते हैं कि Aspose.Words का उपयोग करके **आयताकार आकार** कैसे बनाएं, **Ellipse शब्द कैसे डालें**, और **Word में आकारों को समूहित करें**। पूरा उदाहरण पूर्ण वर्कफ़्लो दर्शाता है—दस्तावेज़ इनिशियलाइज़ करने से लेकर अंतिम फ़ाइल सहेजने तक—ताकि आप आकार हैंडलिंग को किसी भी स्वचालित रिपोर्टिंग या दस्तावेज़‑जनरेशन समाधान में एकीकृत कर सकें।

### आगे क्या?

* अधिक जटिल ज्यामिति जैसे `Polygon` या `Freeform` के लिए **aspose.words create shapes** का अन्वेषण करें।  
* समूहित आकारों को **content controls** के साथ मिलाकर डायनामिक टेम्प्लेट बनाएं।  
* DOCX को PDF या HTML में बदलें ताकि देखें कि वेक्टर आकार विभिन्न फ़ॉर्मेट में कैसे रेंडर होते हैं।  

विभिन्न आकार, रंग और रोटेशन के साथ प्रयोग करने में संकोच न करें। जब आप आकार समूह बनाने में निपुण हो जाएंगे, तो आप सीधे Word दस्तावेज़ों में जटिल डायग्राम, बैज और कस्टम UI एलिमेंट बना सकते हैं।

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच का अन्वेषण कर सकें।

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}