---
category: general
date: 2026-08-07
description: Aspose.Words का उपयोग करके C# में आयताकार आकार डालें और सीखें कि आकार
  को कैसे छुपाएँ, भरने का रंग कैसे सेट करें, और एक Word दस्तावेज़ में आयताकार आकार
  को प्रभावी ढंग से कैसे जोड़ें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: hi
lastmod: 2026-08-07
og_description: C# के साथ Word दस्तावेज़ में आयताकार आकार डालें। सीखें कि कैसे आकार
  को छिपाएँ, भरने का रंग सेट करें, और Aspose.Words का उपयोग करके आयताकार आकार जोड़ें।
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: C# में आयताकार आकार डालें – पूर्ण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: C# में Aspose.Words के साथ आयताकार आकार सम्मिलित करें – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Aspose.Words के साथ आयताकार आकार सम्मिलित करें – चरण‑दर‑चरण गाइड

यदि आपको C# से Word दस्तावेज़ में **आयताकार आकार** सम्मिलित करने की आवश्यकता है, तो यह गाइड आपको ठीक‑ठीक बताता है कि इसे कैसे किया जाए। आप देखेंगे कि भरने का रंग कैसे सेट करें, आकार को छुपाएँ ताकि वह अंतिम लेआउट में न दिखे, और फ़ाइल को सहेजें—सिर्फ कुछ पंक्तियों के कोड से।

आगे के अनुभागों में हम सभी आवश्यक बातों को कवर करेंगे: पूर्वापेक्षाएँ, पूर्ण कोड लिस्टिंग, प्रत्येक चरण की व्याख्याएँ, और सामान्य विविधताओं के लिए टिप्स जैसे आकार को फिर से दिखाना या अलग रंग का उपयोग करना। अंत तक आप किसी भी .docx फ़ाइल में प्रोग्रामेटिक रूप से **आयताकार आकार** जोड़ने में सक्षम होंगे।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* **Aspose.Words for .NET** (संस्करण 23.10 या बाद का)। आप इसे NuGet के माध्यम से स्थापित कर सकते हैं:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK या बाद का आपके मशीन पर स्थापित हो।
* C# और Visual Studio (या आपका पसंदीदा कोई भी IDE) की बुनियादी समझ।

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है—आकार‑से संबंधित API मुख्य Aspose.Words पैकेज का हिस्सा हैं।

## Insert rectangle shape with Aspose.Words

समाधान का मूल एक छोटा, स्वतंत्र प्रोग्राम है जो एक खाली दस्तावेज़ बनाता है, आयताकार आकार सम्मिलित करता है, उसका रंग सेट करता है, उसे छुपाता है, और फिर फ़ाइल को सहेजता है। नीचे पूर्ण स्रोत कोड है जिसमें इन‑लाइन टिप्पणीें हैं जो प्रत्येक पंक्ति के *क्यों* को समझाती हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### What each step does

| चरण | कारण |
|------|--------|
| **नया दस्तावेज़ बनाएं** | एक साफ़ कैनवास प्रदान करता है; आप `new Document(path)` में फ़ाइल पथ पास करके मौजूदा .docx भी लोड कर सकते हैं। |
| **DocumentBuilder को इनिशियलाइज़ करें** | `DocumentBuilder` एक उच्च‑स्तरीय सहायक है जो आपको टेक्स्ट, टेबल और आकार सम्मिलित करने देता है बिना लो‑लेवल नोड ट्री को संभाले। |
| **आयताकार आकार सम्मिलित करें** | `InsertShape` मेथड एक `Shape` ऑब्जेक्ट लौटाता है जिसे आप आगे कस्टमाइज़ कर सकते हैं (आकार, स्थिति, बॉर्डर आदि)। |
| **भरण रंग सेट करें** | `FillColor` प्रॉपर्टी अंदरूनी रंग को नियंत्रित करती है; आप कोई भी `Color` वैल्यू उपयोग कर सकते हैं (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)` आदि)। |
| **आकार को छुपाएँ** | `Hidden = true` Word को लेआउट के दौरान आकार को अनदेखा करने को बताता है जबकि वह दस्तावेज़ के XML में बना रहता है। यह अदृश्य ऑब्जेक्ट्स को स्टोर करने का मानक तरीका है। |
| **दस्तावेज़ सहेजें** | परिवर्तन को .docx फ़ाइल में स्थायी बनाता है। सहेजी गई फ़ाइल में छुपा हुआ आयताकार आकार होगा। |

## How to set fill color for a shape

भरण रंग बदलना इतना सरल है कि आप `System.Drawing.Color` को `FillColor` प्रॉपर्टी को असाइन कर दें। यदि आपको कस्टम शेड चाहिए, तो `Color.FromArgb` का उपयोग करें:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Why this matters*: भरण रंग आकार के XML (`<w:fill>` एट्रिब्यूट) में संग्रहीत होता है। जब आकार छुपा होता है, तब भी रंग मौजूद रहता है, जो डाउनस्ट्रीम प्रोसेसिंग (जैसे रंग कोड के आधार पर मेटाडेटा निकालना) के लिए उपयोगी हो सकता है।

## How to hide shape in the final document

`Hidden` फ़्लैग `Shape` क्लास की एक बूलियन प्रॉपर्टी है। इसे `true` सेट करने से सुनिश्चित होता है कि आकार Word लेआउट इंजन द्वारा अनदेखा किया जाए।

```csharp
rectangleShape.Hidden = true;
```

**सामान्य समस्याएँ**

* **Hidden vs. Visible** – यदि बाद में आपको आकार को दिखाना हो, तो बस `Hidden = false` सेट कर दें।
* **Compatibility** – Word के पुराने संस्करण (pre‑2007) छुपे हुए ड्रॉइंग ऑब्जेक्ट्स को अलग तरह से संभाल सकते हैं। Aspose.Words उपयुक्त OOXML एलेमेंट में फ़्लैग संग्रहीत करके संगतता बनाए रखता है।

## How to insert shape programmatically

हालाँकि उदाहरण में आयताकार आकार उपयोग किया गया है, वही `InsertShape` मेथड कई अन्य आकारों (ellipse, triangle, line आदि) के लिए भी काम करता है। पहला आर्ग्यूमेंट एक `ShapeType` enum वैल्यू होता है:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tip**: यदि आपको पृष्ठ पर किसी विशिष्ट स्थान पर आकार रखना है, तो `InsertShape` कॉल करने से पहले `builder.MoveTo` का उपयोग करके इंसर्शन पॉइंट सेट करें।

## Add rectangle shape to an existing document

अक्सर आप टेम्पलेट को बढ़ा रहे होते हैं, न कि शून्य से शुरू। चरण 1 को इस तरह बदलें:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

सभी बाद के चरण समान रहते हैं, और आयताकार आकार उस स्थान पर जोड़ा जाएगा जहाँ बिल्डर का कर्सर स्थित है (आमतौर पर डिफ़ॉल्ट रूप से दस्तावेज़ के अंत में)।

## Handling edge cases and variations

### 1. Making the shape visible again

यदि आपके वर्कफ़्लो के बाद के हिस्से में छुपे हुए आयताकार आकार को दिखाने की आवश्यकता हो, तो आप फ़्लैग को टॉगल कर सकते हैं:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Adding a border (stroke)

एक छुपा हुआ आकार तब भी दिखाई देने वाला बॉर्डर रख सकता है जब आप उसे दिखाने का निर्णय लेते हैं। `LineColor` और `LineWidth` प्रॉपर्टी सेट करें:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Positioning the rectangle absolutely

सटीक लेआउट नियंत्रण के लिए, आकार के `WrapType` को `WrapType.Inline` (डिफ़ॉल्ट) या `WrapType.TopBottom` में बदलें और `Left`/`Top` प्रॉपर्टी को समायोजित करें:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Using a different measurement unit

Aspose.Words पॉइंट्स में काम करता है (1 pt = 1/72 इंच)। यदि आप सेंटीमीटर पसंद करते हैं, तो पहले रूपांतरण करें:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Complete runnable example

नीचे *पूरा* प्रोग्राम है जिसे आप कॉपी, पेस्ट और चलाकर देख सकते हैं। इसमें सभी आवश्यक `using` निर्देश शामिल हैं और ऐसे एब्सोल्यूट पाथ्स हैं जिन्हें आपको अपने वातावरण के अनुसार समायोजित करना होगा।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected result**: फ़ाइल `HiddenRectangleShape.docx` Microsoft Word में *कोई दिखाई देने वाला आकार* नहीं दिखाते हुए खुलती है, लेकिन छुपा हुआ आयताकार आकार दस्तावेज़ XML में मौजूद होता है। आप इसकी उपस्थिति की पुष्टि .docx को ज़िप आर्काइव के रूप में खोलकर `word/document.xml` में `<w:shape>` एलेमेंट को `w:fill="yellow"` और `w:hidden="true"` एट्रिब्यूट्स के साथ देख कर कर सकते हैं।

## Conclusion

आप अब जानते हैं कि C# और Aspose.Words का उपयोग करके Word दस्तावेज़ में **आयताकार आकार** कैसे **सम्मिलित** करें, **भरण रंग** कैसे **सेट** करें, और **आकार को छुपाएँ** ताकि वह अंतिम लेआउट में अदृश्य रहे। यही पैटर्न अन्य आकार प्रकारों, कस्टम रंगों और मौजूदा टेम्पलेट्स के लिए भी काम करता है। बॉर्डर, एब्सोल्यूट पोजिशनिंग और विभिन्न माप इकाइयों के साथ प्रयोग करें ताकि आकार को अपनी सटीक आवश्यकताओं के अनुसार ढाल सकें।

### Next steps

* तालिकाओं या हेडर/फ़ूटर के भीतर **आकार सम्मिलित करने** की खोज करें ताकि वॉटरमार्क बन सकें।
* **आयताकार आकार जोड़ने** को कंटेंट कंट्रोल्स के साथ मिलाकर डायनामिक प्लेसहोल्डर बनाएं।
* उन्नत सुविधाओं जैसे रोटेशन, ग्रेडिएंट फ़िल्स, और SVG इम्पोर्ट के लिए Aspose.Words की **shape manipulation** API की समीक्षा करें।

कोड को अपने प्रोजेक्ट में अनुकूलित करने में संकोच न करें, और टिप्पणी में हमें बताएं कि आप अगले कौन सी shape‑related चुनौती हल कर रहे हैं!

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं ताकि आप अतिरिक्त API फीचर्स में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}