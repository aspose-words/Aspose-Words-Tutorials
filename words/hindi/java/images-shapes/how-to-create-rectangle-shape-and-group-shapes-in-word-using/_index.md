---
category: general
date: 2026-11-18
description: C# के साथ Word दस्तावेज़ में आयताकार आकार कैसे बनाएं, सीखें। यह गाइड
  आकार का आकार निर्धारित करने, आकार की स्थिति सेट करने और Word में आकारों को समूहित
  करने को भी कवर करता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: hi
lastmod: 2026-11-18
og_description: C# का उपयोग करके Word फ़ाइल में आयताकार आकार बनाएं और आकार के आयाम
  सेट करना, आकार की स्थिति निर्धारित करना, तथा Word में आकारों को समूहित करना सीखें।
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: C# के साथ Word में आयताकार आकार बनाएं और आकारों को समूहित करें
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# का उपयोग करके Word में आयताकार आकार बनाना और आकारों को समूहित करना
url: /hi/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में C# का उपयोग करके आयताकार आकार बनाना और आकारों को समूहित करना

यदि आपको Word दस्तावेज़ में **आयताकार आकार बनाना** है, तो यह ट्यूटोरियल आपको एक पूर्ण, तैयार‑चलाने‑योग्य समाधान दिखाता है। आप देखेंगे कि आकार का आकार कैसे सेट करें, आकार की स्थिति कैसे सेट करें, और Word में आकारों को समूहित करें ताकि वे एकल वस्तु की तरह व्यवहार करें।

आकारों के साथ काम करना रिपोर्ट, चालान, या आरेखों को प्रोग्रामेटिक रूप से जनरेट करने में एक सामान्य आवश्यकता है। इस गाइड के अंत तक आप एक `.docx` फ़ाइल जनरेट करने में सक्षम होंगे जिसमें एक आयत, एक दीर्घवृत्त, और एक समूहित कंटेनर होगा—सभी Aspose.Words for .NET के साथ बनाए गए।

## आवश्यकताएँ

- .NET 6.0 SDK या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)
- एक कोड एडिटर या IDE (Visual Studio, VS Code, Rider, आदि)

अतिरिक्त कोई लाइब्रेरी आवश्यक नहीं है।

## Word में आयताकार आकार बनाना और आकारों को समूहित करना

मुख्य चरण इस प्रकार हैं:

1. **एक खाली दस्तावेज़ बनाएं** और एक `DocumentBuilder`।
2. **एक `GroupShape` डालें** जो व्यक्तिगत आकारों को रखेगा।
3. **एक आयताकार आकार बनाएं**, उसके आयाम सेट करें, और उसे समूह में जोड़ें।
4. **एक दीर्घवृत्त आकार बनाएं**, उसका आकार और स्थिति सेट करें, और उसे समूह में जोड़ें।
5. **दस्तावेज़ सहेजें**।

प्रत्येक चरण नीचे समझाया गया है, और संपूर्ण स्रोत कोड व्याख्या के बाद दिया गया है।

### चरण 1: दस्तावेज़ और बिल्डर को प्रारंभ करें

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` पूरे Word फ़ाइल को दर्शाता है, जबकि `DocumentBuilder` सामग्री डालने के लिए एक फ़्लुएंट API प्रदान करता है। किसी भी आकार को जोड़ने से पहले उनका प्रारंभ करना अनिवार्य है।

### चरण 2: एक समूह आकार डालें

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` एक कंटेनर की तरह काम करता है; सभी चाइल्ड आकार एक साथ चलते हैं। यह **Word में आकारों को समूहित करने** का अनुशंसित तरीका है जब आपको सामूहिक रूपांतरण (जैसे, स्थानांतरित करना, घुमाना, या हटाना) की आवश्यकता हो।

### चरण 3: आयत बनाएं और उसका आकार सेट करें

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

यहाँ हम `Width` और `Height` असाइन करके **आयताकार आकार बनाते** हैं और **आकार का आकार सेट करते** हैं। Aspose.Words में, आकार बिंदुओं में व्यक्त किए जाते हैं (1 pt ≈ 1/72 in)। आयामों को स्पष्ट रूप से सेट करने से आयत ठीक उसी तरह दिखाई देती है जैसा आप चाहते हैं।

### चरण 4: दीर्घवृत्त बनाएं, आयाम सेट करें, और उसकी स्थिति निर्धारित करें

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

दीर्घवृत्त के लिए **आकार के आयाम सेट करना** चौड़ाई और ऊँचाई दोनों के लिए समान है, जिससे एक पूर्ण वृत्त बनता है। `Left` प्रॉपर्टी **आकार की स्थिति सेट करना** दर्शाती है: दीर्घवृत्त समूह के मूल बिंदु से 120 pt दाईं ओर शुरू होता है, इसलिए यह आयत के साथ ओवरलैप नहीं करता।

### चरण 5: दस्तावेज़ सहेजें

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

सहेजने से Word फ़ाइल डिस्क पर लिखी जाती है। आप Microsoft Word में `GroupShape.docx` खोलकर यह सत्यापित कर सकते हैं कि आयत और दीर्घवृत्त सही ढंग से समूहित और स्थित हैं।

## आकार के आयाम और आकार सेट करना – गहरा विश्लेषण

- **बिंदु बनाम इंच**: 72 pt = 1 in। यदि आप इंच पसंद करते हैं, तो 72 से गुणा करें (उदा., 2.5 in के लिए `2.5 * 72`)।
- **स्वचालित स्केलिंग**: यदि आप `Width` या `Height` छोड़ देते हैं, तो आकार अपना डिफ़ॉल्ट आकार उपयोग करता है। लेआउट आश्चर्य से बचने के लिए स्पष्ट रूप से **आकार का आकार सेट करें**।
- **आस्पेक्ट रेशियो**: `Ellipse` जैसे आकारों के लिए, `Width` और `Height` को समान रखने से वृत्ताकार रूप बना रहता है।

## Word में आकार की स्थिति निर्धारित करना

`Left` और `Top` प्रॉपर्टी आकार के कंटेनर (समूह या पृष्ठ) के अंदर ऑफ़सेट को नियंत्रित करती हैं। सकारात्मक मान आकार को दाएँ/नीचे ले जाते हैं; नकारात्मक मान इसे बाएँ/ऊपर शिफ्ट करते हैं। समूह बनाते समय, स्थितियां समूह के मूल बिंदु के सापेक्ष होती हैं, जो लेआउट गणनाओं को सरल बनाती हैं।

## Aspose.Words का उपयोग करके Word में आकारों को समूहित करना

समूह बनाना आवश्यक है जब आप कई आकारों को एक इकाई के रूप में कार्य करना चाहते हैं। `GroupShape` ऑब्जेक्ट:

- `AppendChild` का समर्थन करता है ताकि कोई भी `Shape` (आयत, दीर्घवृत्त, छवि, आदि) जोड़ा जा सके।
- एक ही कॉल से पूरे समूह को स्थानांतरित, घुमा या हटाने की अनुमति देता है।
- चाइल्ड आकारों की स्थितियों को समूह के सापेक्ष रखता है, जिससे जटिल आरेखों को प्रबंधित करना आसान हो जाता है।

**प्रो टिप:** सभी चाइल्ड आकार जोड़ने के बाद, आप समूह के `Width`, `Height`, `Left`, और `Top` को समायोजित करके पूरी संग्रह को एक ही चरण में पुनः स्थित कर सकते हैं।

## पूर्ण चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और चलाने के लिए उपयोग कर सकते हैं। इसमें सभी `using` निर्देश, एक `Main` मेथड, और टिप्पणियां शामिल हैं जो प्रत्येक पंक्ति को समझाती हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**अपेक्षित आउटपुट:** प्रोग्राम चलाने के बाद, `GroupShape.docx` निष्पादन फ़ोल्डर में दिखाई देता है। इसे Word में खोलने पर बाएँ ओर एक आयत (100 pt × 50 pt) और दाएँ ओर 120 pt स्थित एक दीर्घवृत्त (80 pt × 80 pt) दिखता है, दोनों एक ही समूहित वस्तु के भीतर।

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="C# द्वारा निर्मित समूहित आयत और दीर्घवृत्त आकार दिखाते हुए Word दस्तावेज़ का स्क्रीनशॉट" }

*ऊपर की छवि अंतिम परिणाम को दर्शाती है; आयत और दीर्घवृत्त को एक समूह के रूप में चयन किया जा सकता है।*

## सामान्य प्रश्न और किनारे के मामलों

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं दो से अधिक आकार जोड़ सकता हूँ?** | हाँ। प्रत्येक अतिरिक्त आकार के लिए `group.AppendChild(yourShape)` कॉल करें। |
| **यदि मुझे समूह को घुमाना हो तो क्या करें?** | सभी चाइल्ड जोड़ने के बाद `group.RotationAngle = 45;` (डिग्री) का उपयोग करें। |
| **मैं समूह का बैकग्राउंड रंग कैसे बदलूँ?** | `group.FillColor = System.Drawing.Color.LightGray;` सेट करें। |
| **क्या यह .doc फ़ाइलों के साथ काम करेगा?** | Aspose.Words `.doc` और `.docx` दोनों को सपोर्ट करता है। वही कोड काम करता है; केवल `Save` में फ़ाइल एक्सटेंशन बदलें। |
| **क्या कई आकारों को समूहित करने से मेमोरी पर प्रभाव पड़ेगा?** | समूह बनाना स्वयं में न्यूनतम ओवरहेड जोड़ता है। मुख्य चिंता कुल आकारों की संख्या है; बड़े दस्तावेज़ों के लिए इसे उचित रखें। |

## निष्कर्ष

इस ट्यूटोरियल में आपने C# का उपयोग करके Word फ़ाइल में **आयताकार आकार बनाना**, **आकार का आकार सेट करना**, **आकार के आयाम सेट करना**, **आकार की स्थिति सेट करना**, और अंत में Aspose.Words के साथ **Word में आकारों को समूहित करना** सीखा। पूर्ण उदाहरण एक साफ़, रखरखाव योग्य दृष्टिकोण दर्शाता है जिसे आप अधिक जटिल आरेख, चार्ट, या कस्टम ग्राफिक्स में विस्तारित कर सकते हैं।

अगले चरण में, आप निम्नलिखित का अन्वेषण कर सकते हैं:

- आकारों के भीतर टेक्स्ट जोड़ना (`Shape.TextPath.Text = "Hello"`).
- `GroupShape` में छवियां डालना।
- समूहित आकारों को PDF में निर्यात करना `doc.Save("output.pdf")` के साथ।

विभिन्न आकारों, स्थितियों, और अतिरिक्त आकार प्रकारों के साथ प्रयोग करने में संकोच न करें ताकि आपके प्रोजेक्ट की आवश्यकताओं को पूरा किया जा सके। कोडिंग का आनंद लें!

## आप आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाना](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}