---
category: general
date: 2026-09-05
description: Aspose.Words का उपयोग करके C# में एक खाली Word दस्तावेज़ बनाना और एक
  आयताकार आकार जोड़ना सीखें, जिसे छिपाया जा सकता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: hi
lastmod: 2026-09-05
og_description: Aspose.Words का उपयोग करके खाली वर्ड दस्तावेज़ बनाना और छिपा हुआ आयताकार
  आकार सम्मिलित करना – C# डेवलपर्स के लिए चरण‑दर‑चरण गाइड।
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: एक खाली वर्ड दस्तावेज़ बनाएं जिसमें छिपा हुआ आयताकार आकार हो
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: एक खाली वर्ड दस्तावेज़ बनाएं और एक आयताकार आकार जोड़ें
url: /hi/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ब्लैंक वर्ड डॉक्यूमेंट बनाएं और एक आयताकार आकार जोड़ें

यदि आपको **खाली वर्ड दस्तावेज़** निर्माण की आवश्यकता है जिसमें ऐसा आकार भी हो जिसे आप लेआउट में दिखाई नहीं देना चाहते, तो यह गाइड Aspose.Words for .NET के साथ इसे ठीक‑ठीक कैसे करना है दिखाता है। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो एक नया दस्तावेज़ बनाता है, एक आयताकार आकार जोड़ता है, उस आकार को छिपाता है, और फ़ाइल को सहेजता है—कोई अतिरिक्त टूलिंग आवश्यक नहीं।

यह ट्यूटोरियल प्रोजेक्ट सेटअप से लेकर सामान्य समस्याओं के समाधान तक सब कुछ कवर करता है। अंत तक आप एक ऐसा Word फ़ाइल जेनरेट करने में सक्षम हो जाएंगे जो पाठक को खाली दिखता है, लेकिन फिर भी छिपा हुआ मेटाडेटा रखता है, जो वॉटरमार्क, कस्टम XML स्टोरेज, या लेआउट एंकर जैसी चीज़ों के लिए उपयोगी है।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

* .NET 6.0 SDK या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
* Visual Studio 2022 (या कोई भी IDE जो C# को सपोर्ट करता हो)
* एक सक्रिय **Aspose.Words** NuGet लाइसेंस (टेस्टिंग के लिए फ्री ट्रायल काम करता है)
* C# और डॉक्यूमेंट नोड्स के कॉन्सेप्ट की बेसिक समझ

आप लाइब्रेरी को निम्नलिखित CLI कमांड से इंस्टॉल कर सकते हैं:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** अपने Aspose.Words संस्करण को हमेशा अपडेट रखें; इस ट्यूटोरियल में उपयोग किया गया API संस्करण 23.10 तक स्थिर है।

## Aspose.Words के साथ ब्लैंक वर्ड डॉक्यूमेंट कैसे बनाएं

पहला कदम `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। एक नया `Document` एक खाली **खाली वर्ड दस्तावेज़** दर्शाता है—कोई पैराग्राफ नहीं, कोई सेक्शन नहीं, सिर्फ फ़ाइल कंटेनर।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Why this matters:** एक साफ़ दस्तावेज़ से शुरू करने से यह सुनिश्चित होता है कि बाद में आप जो छिपा हुआ आकार जोड़ेंगे वह मौजूदा कंटेंट या स्टाइल्स में बाधा न डाले।

## दस्तावेज़ में आयताकार आकार जोड़ें

अब हम एक आयताकार आकार बनाते हैं। Aspose.Words में एक shape एक नोड होता है जिसे दस्तावेज़ ट्री में कहीं भी रखा जा सकता है, और इसे आकार, फ़िल, लाइन स्टाइल और विज़िबिलिटी के साथ कॉन्फ़िगर किया जा सकता है।

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

ऊपर दिया गया कोड एक दृश्यमान आयत बनाता है। इस बिंदु पर आप इसे `builder.InsertNode(rectangle)` से दस्तावेज़ में डाल सकते थे। हालांकि, क्योंकि हम चाहते हैं कि आकार छिपा रहे, हम इन्सर्शन से पहले उसकी `Hidden` प्रॉपर्टी को समायोजित करेंगे।

## Word दस्तावेज़ में आकार को छिपाने का तरीका

Word shape नोड्स के लिए एक `Hidden` एट्रिब्यूट प्रदान करता है। जब इसे `true` पर सेट किया जाता है, तो आकार पेज लेआउट में नहीं दिखता, लेकिन यह दस्तावेज़ के XML का हिस्सा बना रहता है। यह **how to hide shape** आवश्यकता का मूल है।

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Explanation:** `Hidden = true` सेट करने से shape के XML में `<w:hide>` एट्रिब्यूट जुड़ जाता है। Word प्रोसेसर रेंडरिंग के दौरान इस आकार को अनदेखा करता है, फिर भी इसे प्रोग्रामेटिकली या Word के XML व्यू से एक्सेस किया जा सकता है।

## छिपे हुए आकार को खाली दस्तावेज़ में इन्सर्ट करें

अब हम छिपे हुए आयत को दस्तावेज़ ट्री में रखेंगे। क्योंकि दस्तावेज़ अभी भी खाली है, आकार मुख्य स्टोरी का पहला नोड बन जाता है।

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

यदि आप परिणामी फ़ाइल को Microsoft Word में खोलते हैं, तो आपको एक दिखने में खाली पेज मिलेगा। आकार मौजूद है, लेकिन वह अदृश्य है।

## दस्तावेज़ को सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप कोई भी समर्थित फ़ॉर्मेट (`.docx`, `.pdf`, `.odt`, आदि) चुन सकते हैं। इस ट्यूटोरियल के लिए हम आधुनिक DOCX फ़ॉर्मेट का उपयोग करेंगे।

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### अपेक्षित परिणाम

`HiddenRectangle.docx` को Word में खोलें:

* दस्तावेज़ खाली दिखता है (कोई दृश्यमान आकार या टेक्स्ट नहीं)।
* यदि आप फ़ाइल को **Open XML SDK** या **Word XML Viewer** जैसे टूल से जांचते हैं, तो आपको `<w:pict>` एलिमेंट मिलेगा जिसमें `hidden` एट्रिब्यूट के साथ आयत शामिल है।

![छिपे हुए आयताकार आकार के साथ खाली वर्ड दस्तावेज़](image.png){: .align-center alt="छिपे हुए आयताकार आकार के साथ खाली वर्ड दस्तावेज़"}

## पूर्ण, चलाने योग्य उदाहरण

नीचे वह पूरा प्रोग्राम है जिसे आप कॉन्सोल एप्लिकेशन में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी आवश्यक `using` निर्देश, एरर हैंडलिंग, और कमेंट्स शामिल हैं।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

प्रोग्राम चलाएँ (`dotnet run`) और आउटपुट फ़ाइल की पुष्टि करें। कंसोल सहेजने के स्थान को पुष्टि करेगा।

## सामान्य प्रश्न और एज केस

### क्या मैं एक साथ कई आकारों को छिपा सकता हूँ?

हाँ। प्रत्येक आकार बनाएं, `Hidden = true` सेट करें, और उन्हें क्रमशः इन्सर्ट करें। छिपा हुआ फ़्लैग नोड स्तर पर काम करता है, इसलिए एक ही दस्तावेज़ में छिपे और दृश्यमान दोनों आकारों को मिलाना समर्थित है।

### यदि मुझे आकार को केवल प्रिंट व्यू में छिपाना हो तो क्या करें?

Word **display** और **print** विज़िबिलिटी को `DisplayWhen` प्रॉपर्टी के माध्यम से अलग करता है। Aspose.Words इस फ़्लैग के लिए सीधे API नहीं देता, लेकिन आप नीचे दिखाए अनुसार मूल XML को संशोधित कर सकते हैं:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

इसे केवल तब उपयोग करें जब आपको प्रिंट‑केवल विज़िबिलिटी चाहिए।

### क्या छिपा हुआ आकार फ़ाइल आकार को प्रभावित करता है?

एक छिपा हुआ आकार वही XML पेलोड जोड़ता है जैसा एक दृश्यमान आकार करता है, इसलिए फ़ाइल आकार में वृद्धि समान रहती है। हालांकि, क्योंकि आकार  

## आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण, चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}