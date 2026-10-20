---
category: general
date: 2026-08-04
description: Word में प्रोग्रामेटिकली docx फ़ाइल सहेजें, साथ ही आयताकार आकार जोड़ें
  और आकारों को समूहित करें। आकार के आयाम सेट करना और प्रोग्रामेटिकली टेक्स्टबॉक्स
  बनाना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: hi
lastmod: 2026-08-04
og_description: C# का उपयोग करके docx फ़ाइल सहेजें, जिसमें आयताकार आकार जोड़ना, Word
  में आकारों को समूहित करना, आकार के आयाम सेट करना, और प्रोग्रामेटिकली टेक्स्टबॉक्स
  बनाना शामिल है।
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Word में समूहित आकृतियों के साथ docx फ़ाइल सहेजें – C# चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# का उपयोग करके Word में समूहित आकारों के साथ docx फ़ाइल सहेजें
url: /hi/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# का उपयोग करके Word में समूहित आकारों के साथ docx फ़ाइल सहेजें

यदि आपको कई आकारों को एक साथ व्यवस्थित करके **docx फ़ाइल सहेजने** की आवश्यकता है, तो यह गाइड आपको C# के साथ यह करने का तरीका दिखाता है। आप सीखेंगे कि कैसे **आयत आकार जोड़ें**, Word दस्तावेज़ में कई आकारों को समूहित करें, **आकार के आयाम सेट करें**, और **प्रोग्रामेटिक रूप से टेक्स्टबॉक्स बनाएं**। यह समाधान नवीनतम Aspose.Words for .NET के साथ काम करता है और .NET 6 या बाद के संस्करण पर चलता है।

ट्यूटोरियल प्रत्येक चरण को दर्शाता है, प्रोजेक्ट सेटअप से लेकर अंतिम `doc.Save` कॉल तक। अंत तक आपके पास एक पुन: उपयोग योग्य कोड स्निपेट होगा जिसे आप किसी भी कंसोल या ASP.NET प्रोजेक्ट में पेस्ट कर सकते हैं। कोई बाहरी स्क्रिप्ट या DOCX फ़ाइल का मैनुअल संपादन आवश्यक नहीं है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6 SDK (या नया) स्थापित।
* **Aspose.Words for .NET** का वैध लाइसेंस (टेस्टिंग के लिए फ्री ट्रायल काम करता है)।
* Visual Studio 2022, VS Code, या कोई भी IDE जो .NET प्रोजेक्ट बना सके।

कोड केवल Aspose.Words नेमस्पेस का उपयोग करता है, इसलिए अतिरिक्त NuGet पैकेज की आवश्यकता नहीं है।

## Save docx file with grouped shapes in Word

समाधान का मूल भाग एक `GroupShape` बनाना है जिसमें आयत और टेक्स्टबॉक्स दोनों हों, फिर इस समूह को दस्तावेज़ में डालें और `doc.Save` कॉल करें। नीचे के अनुभाग प्रक्रिया को छोटे‑छोटे हिस्सों में विभाजित करते हैं।

### 1. Create a new document and a builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*इस चरण का महत्व* – एक नया `Document` ऑब्जेक्ट एक खाली *.docx* फ़ाइल का प्रतिनिधित्व करता है। `DocumentBuilder` उच्च‑स्तरीय मेथड्स जैसे `InsertNode` प्रदान करता है, जिसका उपयोग हम समूह आकार रखने के लिए करेंगे।

### 2. Add rectangle shape to a group

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*इस चरण का महत्व* – **add rectangle shape** ऑपरेशन यह दर्शाता है कि कैसे सटीक आकार और स्थिति के साथ एक दृश्य तत्व परिभाषित किया जाए। आयत `group` के भीतर रहती है, इसलिए बाद में समूह को ले जाने पर आयत स्वचालित रूप से साथ चलती है।

### 3. Group shapes in Word document

`GroupShape` क्लास कई ड्राइंग ऑब्जेक्ट्स को एकत्रित करती है। समूह बनाना उपयोगी है जब आप कई ऑब्जेक्ट्स को एक इकाई के रूप में संभालना चाहते हैं (जैसे, साथ‑साथ ले जाना, घुमाना या कॉपी करना)।

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*हम समूह क्यों बनाते हैं* – समूह बनाना लेआउट जटिलता को कम करता है। प्रत्येक आकार को अलग‑अलग पेज पर पोज़िशन करने के बजाय, आप समूह के `Left`, `Top`, `Width`, और `Height` को एक बार समायोजित करते हैं।

### 4. Set shape dimensions for precise layout

समूह और उसके चाइल्ड आकार दोनों को स्पष्ट आयामों की आवश्यकता होती है; अन्यथा Word डिफ़ॉल्ट आकार लागू करता है जो आपके डिज़ाइन से मेल नहीं खा सकता।

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*हम आयाम क्यों सेट करते हैं* – सटीक माप यह सुनिश्चित करता है कि आयत और टेक्स्टबॉक्स अनजाने में ओवरलैप न हों और अंतिम **save docx file** इच्छित लेआउट से मेल खाए।

### 5. Create textbox programmatically inside the group

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*इस चरण का महत्व* – **create textbox programmatically** भाग दिखाता है कि कैसे एक आकार के भीतर रिच टेक्स्ट एम्बेड किया जाए। `Paragraph` और `Run` का उपयोग करने से बाद में फ़ॉर्मेटिंग पर पूर्ण नियंत्रण मिलता है।

### 6. Insert group shape and **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*इस अंतिम चरण का महत्व* – `InsertNode` कॉल समूहित आकारों को बिल्डर के कर्सर की वर्तमान स्थिति पर रखता है। `doc.Save` मेथड **save docx file** ऑपरेशन करता है, जिससे एक पूर्ण‑फ़ीचर Word दस्तावेज़ डिस्क पर लिखा जाता है।

> **Result:** Microsoft Word में *GroupShape.docx* खोलने पर बाएँ तरफ एक आयत और दाएँ तरफ एक टेक्स्टबॉक्स दिखता है, दोनों एक ही समूह में लॉक होते हैं। आप समूह को एक इकाई के रूप में ले जा सकते हैं, आकार बदल सकते हैं, या अतिरिक्त फ़ॉर्मेटिंग लागू कर सकते हैं।

## Full, runnable example

नीचे दिया गया कोड एक नए कंसोल प्रोजेक्ट (`dotnet new console`) में कॉपी करें और `dotnet run` चलाएँ। प्रोग्राम प्रोजेक्ट की आउटपुट फ़ोल्डर में `GroupShape.docx` बनाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Expected output

* आउटपुट डायरेक्टरी में **GroupShape.docx** नाम की फ़ाइल बनती है।
* फ़ाइल खोलने पर बाएँ तरफ एक आयताकार आकार और दाएँ तरफ “Grouped text” वाला टेक्स्टबॉक्स दिखता है, दोनों एक साथ लॉक होते हैं।
* किसी भी आकार का चयन करने पर पूरी समूह मूव होती है, जिससे **group shapes word** कार्यक्षमता सही ढंग से काम कर रही है, यह पुष्टि होती है।

## Common variations and edge cases

| Situation | Recommendation |
|-----------|----------------|
| दो से अधिक आकारों की आवश्यकता | `builder.InsertNode` कॉल करने से पहले अतिरिक्त `Shape` ऑब्जेक्ट्स को `group` में जोड़ें। |
| समूह को किसी विशिष्ट पेज पर दिखाना चाहते हैं | बिल्डर का कर्सर `builder.MoveToDocumentEnd()` या `builder.MoveToPage(pageNumber)` से ले जाएँ। |
| अलग इकाइयाँ चाहिए (जैसे, सेंटीमीटर) | इंच को पॉइंट में बदलने के लिए `ConvertUtil.InchToPoint(1.0)` उपयोग करें, जो Word अपेक्षित इकाई है। |
| टेक्स्टबॉक्स को टेक्स्ट रैप चाहिए | टेक्स्टबॉक्स बनाने के बाद `textBox.TextBoxWrap = TextBoxWrapType.Square` सेट करें। |
| पुराने .NET Framework संस्करणों के साथ काम कर रहे हैं | वही API .NET Framework 4.7+ के साथ काम करती है, बस सही Aspose.Words संस्करण को रेफ़रेंस करें। |

**Pro tip:** सभी चाइल्ड आकार जोड़ने के *बाद* समूह की `Width` और `Height` सेट करें। इससे समूह पूरी तरह से अपनी सामग्री को घेर लेता है और Word में दस्तावेज़ खोलते समय क्लिपिंग से बचता है।

## Conclusion

आप अब जानते हैं कि **save docx file** कैसे करें जबकि **add rectangle shape**, **group shapes word**, **set shape dimensions**, और **create textbox programmatically** को Aspose.Words for .NET का उपयोग करके लागू किया जाए। पूरा उदाहरण एक साफ़, दोहराने योग्य पैटर्न दर्शाता है जिसे आप अधिक जटिल लेआउट, जैसे चार्ट या इमेज, के लिए अनुकूलित कर सकते हैं।

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर में महारत हासिल कर सकते हैं और अपने प्रोजेक्ट में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर कर सकते हैं।

- [C# का उपयोग करके Word में आयत आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow ट्यूटोरियल – C# में Word आकार में शैडो जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}