---
category: general
date: 2026-09-05
description: सीखें कि समूह आकार वाली docx कैसे बनाएं, ActiveX कमांड बटन डालें, और
  एक पूर्ण C# उदाहरण के साथ Markdown को Word दस्तावेज़ में लोड करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: hi
lastmod: 2026-09-05
og_description: C# का उपयोग करके समूह आकार वाली docx फ़ाइल बनाएं, ActiveX कमांड बटन
  डालें, और Markdown को Word दस्तावेज़ में लोड करें। इस चरण‑दर‑चरण ट्यूटोरियल का पालन
  करें।
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: समूह आकार docx बनाएं और ActiveX नियंत्रण एम्बेड करें – C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: C# में समूह आकार docx कैसे बनाएं और इंटरैक्टिव नियंत्रण जोड़ें
url: /hi/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में समूह आकार (group shape) docx बनाना और इंटरैक्टिव कंट्रोल जोड़ना

यदि आपको **group shape docx** फ़ाइलें प्रोग्रामेटिकली बनानी हैं, तो यह गाइड आपको ठीक‑ठीक दिखाएगा। आप यह भी देखेंगे कि **ActiveX command button** कंट्रोल कैसे **डालें** और **Markdown को Word दस्तावेज़ में** कैसे लोड करें बिना underline फ़ॉर्मेटिंग खोए। ट्यूटोरियल के अंत तक आपके पास एक पूरी तरह कार्यशील `.docx` होगा जिसमें वेक्टर ग्राफ़िक्स, इंटरैक्टिव UI एलिमेंट्स, और markdown‑आधारित कंटेंट सम्मिलित होंगे।

यह ट्यूटोरियल मानता है कि आपके पास एक बेसिक C# डेवलपमेंट एनवायरनमेंट और Aspose.Words for .NET लाइब्रेरी इंस्टॉल है। कोई बाहरी टूल्स आवश्यक नहीं—सब कुछ एक सामान्य .NET कंसोल या डेस्कटॉप एप्लिकेशन के भीतर चलता है।

## Prerequisites

- .NET 6.0 SDK या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
- Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`)
- एक वैध X.509 प्रमाणपत्र (`.pfx`) यदि आप साइनिंग स्टेप टेस्ट करना चाहते हैं
- एक इमेज फ़ाइल (जैसे `logo.png`) और एक markdown फ़ाइल (`sample.md`) जिसे आप किसी ज्ञात फ़ोल्डर में रखें

> **Pro tip:** सभी इनपुट फ़ाइलों को एक ही *resources* फ़ोल्डर में रखें ताकि रिलेटिव पाथ्स सरल हो जाएँ।

## Step 1: Set up the project and import namespaces

एक नया कंसोल प्रोजेक्ट बनाएँ और आवश्यक `using` निर्देश जोड़ें। यह ब्लॉक यह भी दर्शाता है कि बाद में आप किस तरह Aspose.Words क्लासेज़ को रेफ़र करेंगे।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using` स्टेटमेंट्स आपको `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl`, और अन्य टाइप्स तक सीधे पहुँच प्रदान करते हैं जो पूरे ट्यूटोरियल में उपयोग होते हैं।

## Step 2: **Create group shape docx** – add a grouped shape with child elements

एक *group shape* आपको कई ड्रॉइंग ऑब्जेक्ट्स को एक इकाई के रूप में ट्रीट करने देता है। यह संबंधित ग्राफ़िक्स को एक साथ मूव या रिसाइज़ करने में उपयोगी है।

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Why a group shape?**  
ग्रुपिंग से रेक्टैंगल और एलिप्स दोनों एक साथ अलाइन रहते हैं जब उपयोगकर्ता उन्हें Word में ड्रैग करता है। यह बाद में सामान्य बॉर्डर लागू करने या पूरे ग्राफ़िक को प्रोग्रामेटिकली मूव करने जैसे ऑपरेशन्स को भी सरल बनाता है।

## Step 3: Insert a plain‑text content control (placeholder for user input)

Content controls उपयोगकर्ताओं को टेक्स्ट टाइप करने के लिए एक स्ट्रक्चर्ड एरिया देते हैं। प्लेसहोल्डर टेक्स्ट तब गायब हो जाता है जब उपयोगकर्ता टाइप करना शुरू करता है।

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

`PlaceholderName` प्रॉपर्टी वह लाइट‑ग्रे क्यू दिखाती है जो Word में दिखाई देती है। उपयोगकर्ता इसे अपने टेक्स्ट से बदल सकते हैं, और अंडरलाइनिंग XML वैध बनी रहती है।

## Step 4: **Insert ActiveX command button** – add interactive UI to the document

ActiveX कंट्रोल्स अभी भी आधुनिक Word फ़ाइलों में सपोर्टेड हैं और मैक्रो या एक्सटर्नल ऑटोमेशन को ट्रिगर कर सकते हैं। नीचे हम एक *command button* जोड़ते हैं और उसका कैप्शन सेट करते हैं।

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**When to use an ActiveX button?**  
यदि आप दस्तावेज़ को कॉरपोरेट वातावरण में वितरित करते हैं जहाँ VBA मैक्रो पर निर्भरता है, तो ActiveX बटन एक मैक्रो या एक्सटर्नल एप्लिकेशन लॉन्च कर सकता है। शुद्ध HTML‑आधारित इंटरैक्टिविटी के लिए, *content controls* के साथ *Office.js* उपयोग करने पर विचार करें।

## Step 5: Insert a hidden image (e.g., a logo) for branding or later script access

हिडन शैप्स प्रिंटेड दस्तावेज़ में नहीं दिखते लेकिन XML में रहते हैं, जिससे आप उन्हें बाद में प्रोग्रामेटिकली रिट्रीव कर सकते हैं।

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Step 6: **Load markdown into a Word document** while preserving underline formatting

Aspose.Words सीधे Markdown इम्पोर्ट कर सकता है। `ImportUnderlineFormatting` को एनेबल करने से markdown अंडरलाइन (`<u>` या `__text__`) Word अंडरलाइन स्टाइल में बदल जाते हैं, न कि साधारण टेक्स्ट में।

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Edge case:** यदि markdown फ़ाइल में टेबल्स हैं, तो वे स्वचालित रूप से Word टेबल्स में बदल जाते हैं। यदि आपको कस्टम टेबल स्टाइलिंग चाहिए, तो इन्सर्शन के बाद `DocumentBuilder` से लागू करें।

## Step 7: Sign the document with XAdES‑EPES (optional security step)

डिजिटल सिग्नेचर दस्तावेज़ की इंटेग्रिटी सुनिश्चित करता है। नीचे दिया गया कोड **create group shape docx** फ़ाइल को XAdES‑EPES प्रोफ़ाइल का उपयोग करके साइन करता है।

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** प्रमाणपत्र पासवर्ड को सोर्स कंट्रोल से बाहर रखें। प्रोडक्शन में एनवायरनमेंट वेरिएबल्स या सिक्योर वॉल्ट का उपयोग करें।

## Full runnable example

सभी स्टेप्स को मिलाकर एक सिंगल, सेल्फ‑कंटेन्ड प्रोग्राम बनता है। फ़ाइल को `Program.cs` के रूप में सेव करें और कमांड लाइन से चलाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

प्रोग्राम चलाने से `CompleteGroupShape.docx` जनरेट होगा जिसमें शामिल हैं:

- एक ग्रुप्ड रेक्टैंगल + एलिप्स (मुख्य **create group shape docx**)
- प्लेन‑टेक्स्ट कंटेंट कंट्रोल जिसमें प्लेसहोल्डर टेक्स्ट है
- **insert ActiveX command button** जिसका लेबल “Click Me” है
- एक हिडन लोगो इमेज
- अंडरलाइन फ़ॉर्मेटिंग सुरक्षित रखी गई Markdown कंटेंट
- XAdES‑EPES डिजिटल सिग्नेचर (यदि प्रमाणपत्र उपलब्ध हो)

## Common questions and troubleshooting

| Question | Answer |
|---|---|
| **Will the ActiveX button work on macOS Word?** | macOS Word ActiveX कंट्रोल्स को सपोर्ट नहीं करता। बटन एक स्थैतिक इमेज के रूप में दिखेगा। क्रॉस‑प्लेटफ़ॉर्म इंटरैक्टिविटी के लिए Office.js के साथ कंटेंट कंट्रोल्स उपयोग करें। |
| **What if the markdown file contains custom CSS?** | Aspose.Words CSS को इग्नोर करता है; केवल स्टैंडर्ड markdown सिंटैक्स प्रोसेस होता है। CSS‑स्टाइल्ड एलिमेंट्स को इम्पोर्ट के बाद मैन्युअली Word स्टाइल्स में बदलें। |
| **Can I add more shapes to the same group later?** | हाँ। `GroupShape` को उसके नाम या इंडेक्स से रिट्रीव करें, फिर `AppendChild(newShape)` कॉल करें। संशोधन के बाद दस्तावेज़ को फिर से सेव करना याद रखें। |
| **How do I change the signature algorithm?** | `signature.SignatureAlgorithm` को `Sign` कॉल करने से पहले सेट करें। डिफ़ॉल्ट SHA‑256 है, जो अधिकांश कंप्लायंस आवश्यकताओं को पूरा करता है। |
| **Is the hidden image visible in the Word UI?** | नहीं, लेकिन इसे Word विकल्पों में *Show hidden text* टॉगल करके दिखाया जा सकता है। यह लेआउट को गंदा किए बिना मेटाडेटा स्टोर करने में उपयोगी है। |

## Next steps

अब जब आप **create group shape docx**, **insert ActiveX command button**, और **load markdown into a Word document** कर सकते हैं, तो आप आगे खोज सकते हैं:

- **Embedding VBA macros** जो ActiveX बटन क्लिक पर रिएक्ट करते हैं।
- **Applying custom styles** markdown‑जनरेटेड पैराग्राफ़्स पर।
- **Generating PDFs** उसी दस्तावेज़ से `doc.Save("output.pdf", SaveFormat.Pdf)` का उपयोग करके।
- **Automating batch processing** कई markdown फ़ाइलों को एक ही कंपाइल्ड रिपोर्ट में बदलना।

इन एक्सटेंशन से आप पूरी तरह ऑटोमेटेड डॉक्यूमेंट पाइपलाइन बना सकते हैं जो रिच ग्राफ़िक्स, इंटरैक्टिव कंट्रोल्स, और markdown‑आधारित ऑथरिंग को C# से जोड़ते हैं।

---

*Happy coding! If you found this tutorial

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create markdown from word – Complete C# Guide](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}