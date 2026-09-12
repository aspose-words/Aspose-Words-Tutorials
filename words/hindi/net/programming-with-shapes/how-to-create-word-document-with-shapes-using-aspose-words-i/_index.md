---
category: general
date: 2026-09-11
description: Aspose.Words के साथ वर्ड दस्तावेज़ बनाना, आयताकार आकार जोड़ना और आकार
  के आयाम सेट करना सीखें। सटीक आकार निर्धारण के लिए चरण‑दर‑चरण C# गाइड।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: hi
lastmod: 2026-09-11
og_description: C# में Aspose.Words के साथ वर्ड दस्तावेज़ बनाएं। यह गाइड दिखाता है
  कि कैसे आयताकार आकार जोड़ें, आकार का आकार निर्धारित करें, और प्रोग्रामेटिक रूप से
  आकार के आयाम प्रबंधित करें।
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: आकारों के साथ वर्ड दस्तावेज़ बनाएं – Aspose.Words C# ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Aspose.Words का उपयोग करके C# में आकारों के साथ वर्ड दस्तावेज़ कैसे बनाएं
url: /hi/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words in C# का उपयोग करके शैप्स के साथ वर्ड डॉक्यूमेंट कैसे बनाएं

यदि आपको **वर्ड डॉक्यूमेंट बनाना** है जिसमें कस्टम ग्राफ़िक्स हों, तो आप इसे पूरी तरह कोड से कर सकते हैं। यह ट्यूटोरियल आपको एक Word फ़ाइल बनाने, एक रेक्टैंगल शैप जोड़ने, और शैप के हर आयाम को नियंत्रित करने के चरणों से परिचित कराएगा। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

आप सीखेंगे **रेक्टैंगल शैप जोड़ना**, **शैप का आकार सेट करना**, और **ग्रुप्ड कंटेनर के अंदर शैप के आयाम सेट करना**। उदाहरण Aspose.Words 13.9 का उपयोग करता है, लेकिन अवधारणाएँ बाद के संस्करणों पर भी लागू होती हैं। Aspose ड्रॉइंग API का कोई पूर्व अनुभव आवश्यक नहीं—सिर्फ बेसिक C# ज्ञान चाहिए।

## Prerequisites

- .NET 6.0 या बाद का संस्करण स्थापित हो  
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)  
- Visual Studio 2022 जैसे IDE (कोई भी C# सपोर्ट करने वाला एडिटर चलेगा)  

इन टूल्स के तैयार होने से आप कोड को तुरंत चलाकर अतिरिक्त कॉन्फ़िगरेशन की जरूरत नहीं पड़ेगी।

## Step 1: Initialize the document and builder – create word document basics

पहला ऑपरेशन `Document` ऑब्जेक्ट और `DocumentBuilder` को इंस्टैंशिएट करना है। `Document` फ़ाइल को दर्शाता है, जबकि `DocumentBuilder` कंटेंट इन्सर्ट करने के लिए एक फ़्लुएंट API प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
डॉक्यूमेंट को पहले बनाकर आप एक साफ़ कैनवास प्राप्त करते हैं। बिल्डर का कर्सर पहले पैराग्राफ पर शुरू होता है, जहाँ हम बाद में **create shapes in word** करेंगे।

## Step 2: Build a GroupShape to hold multiple graphics

`GroupShape` एक कंटेनर की तरह काम करता है; आप पूरे ग्रुप को एक ही यूनिट के रूप में मूव, रोटेट या रिसाइज़ कर सकते हैं। यहाँ हम कंटेनर की चौड़ाई और ऊँचाई पॉइंट्स में निर्धारित करते हैं (1 pt ≈ 1/72 in)।

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Why this matters:**  
शैप्स को ग्रुप करने से लेआउट मैनेजमेंट सरल हो जाता है। यदि बाद में आप और शैप्स (जैसे सर्कल या टेक्स्ट बॉक्स) जोड़ते हैं, तो वे ग्रुप की पोज़िशन और स्केलिंग को इनहेरिट करेंगे।

## Step 3: Create a rectangle shape and configure its dimensions

अब हम वास्तविक रेक्टैंगल जोड़ते हैं। `Shape` कंस्ट्रक्टर को डॉक्यूमेंट रेफ़रेंस और शैप टाइप चाहिए। निर्माण के बाद हम स्पष्ट रूप से **set shape size** और **set shape dimensions** करते हैं।

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Why this matters:**  
चौड़ाई, ऊँचाई, लेफ़्ट और टॉप सेट करने से आपको शैप पर पिक्सेल‑परफेक्ट कंट्रोल मिलता है। यह तब आवश्यक होता है जब डॉक्यूमेंट को किसी डिज़ाइन स्पेसिफिकेशन या प्रिंटेड फ़ॉर्म से मिलाना हो।

## Step 4: Assemble the group by appending the rectangle

रेक्टैंगल को `GroupShape` में अपेंड करने से वह एक चाइल्ड नोड बन जाता है। आप डॉक्यूमेंट में ग्रुप इन्सर्ट करने से पहले जितनी भी चाइल्ड्स चाहिए, जोड़ सकते हैं।

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:** यदि आप दूसरा शैप जोड़ना चाहते हैं, तो उसे भी उसी तरह बनाएं और `group.AppendChild(secondShape)` कॉल करें। सभी चाइल्ड्स ग्रुप के कोऑर्डिनेट सिस्टम को शेयर करते हैं।

## Step 5: Insert the grouped shape into the document and save

ग्रुप पूरी तरह बन जाने के बाद, हम इसे वर्तमान पैराग्राफ में रखते हैं। बिल्डर की `CurrentParagraph` प्रॉपर्टी सीधे अंडरलाईंग नोड ट्री तक पहुंच देती है।

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Why this matters:**  
ग्रुप को पैराग्राफ में अपेंड करने से शैप टेक्स्ट फ्लो के साथ इनलाइन दिखता है। डॉक्यूमेंट को सेव करना **create word document** ऑपरेशन को फाइनल करता है।

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different page orientation** | `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` को ग्रुप बनाने से पहले सेट करें। |
| **Multiple rectangles** | अतिरिक्त `Shape` ऑब्जेक्ट बनाएं और प्रत्येक के लिए `group.AppendChild(newRect)` कॉल करें। |
| **Dynamic size based on content** | इमेज डाइमेंशन या टेक्स्ट मेट्रिक्स से चौड़ाई/ऊँचाई गणना करें, फिर `rectangle.Width` / `rectangle.Height` को असाइन करें। |
| **Export to PDF** | `doc.Save` के बाद `doc.Save("GroupShape.pdf", SaveFormat.Pdf);` कॉल करें। |
| **Compatibility with older Word versions** | Word 97‑2003 संगतता के लिए `SaveFormat.Doc` का उपयोग करके सेव करें, `Docx` की बजाय। |

ये वैरिएशन्स दर्शाते हैं कि कैसे समान कोर लॉजिक को विभिन्न वास्तविक‑विश्व आवश्यकताओं के अनुसार अनुकूलित किया जा सकता है।

## Full, runnable example

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी‑पेस्ट करके चला सकते हैं। इसमें सभी `using` डायरेक्टिव्स, `Main` एंट्री पॉइंट, और प्रत्येक लाइन को समझाने वाले कमेंट्स शामिल हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Expected output:**  
जब आप *GroupShape.docx* खोलेंगे, तो पहले पेज पर ग्रे‑बॉर्डर वाला रेक्टैंगल दिखेगा जो बाएँ/ऊपर मार्जिन से 50 pt की दूरी पर स्थित है, और रेक्टैंगल स्वयं ग्रुप के अंदर 10 pt की ऑफ़सेट पर है। आयाम कोड में सेट किए गए मानों से मेल खाते हैं।

## Conclusion

अब आप जानते हैं कैसे **create word document**, **add rectangle shape**, और Aspose.Words का उपयोग करके सटीक रूप से **set shape size** तथा **set shape dimensions** कर सकते हैं। ग्रुप्ड‑शैप अप्रोच आपके लेआउट को लचीला रखता है और भविष्य में अतिरिक्त ग्राफ़िक्स या टेक्स्ट बॉक्स जैसी एक्सटेंशन के लिए तैयार करता है।

अगले चरण में, **create shapes in word** जैसे सर्कल, एरो या कस्टम SVG पाथ्स के लिए टॉपिक्स एक्सप्लोर करें, और सीखें कैसे **set shape fill color** या **apply rotation** किया जाता है। विभिन्न मापों के साथ प्रयोग करें ताकि आप देख सकें Word पॉइंट्स बनाम सेंटीमीटर को कैसे रेंडर करता है, और इस कोड को बड़े डॉक्यूमेंट‑जनरेशन पाइपलाइन में इंटीग्रेट करें।

Happy coding, and feel free to adapt this pattern to any automated reporting or form‑filling scenario you encounter!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}