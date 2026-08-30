---
category: general
date: 2026-08-04
description: Aspose.Words का उपयोग करके एक खाली वर्ड दस्तावेज़ बनाएं और कमांड बटन
  डालें। बटन का आकार सेट करना और C# में क्लिक करने योग्य बटन जोड़ना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: hi
lastmod: 2026-08-04
og_description: Aspose.Words के साथ एक खाली वर्ड दस्तावेज़ बनाएं और एक कमांड बटन डालें।
  यह गाइड दिखाता है कि बटन का आकार कैसे सेट करें, क्लिक करने योग्य बटन कैसे जोड़ें,
  और फ़ाइल को कैसे सहेजें।
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: खाली वर्ड दस्तावेज़ बनाएं और एक कमांड बटन जोड़ें – पूर्ण C# ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: कमांड बटन के साथ खाली वर्ड दस्तावेज़ बनाएं – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# कमांड बटन के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड

यदि आपको **खाली Word दस्तावेज़** बनाना है जिसमें एक इंटरैक्टिव बटन हो, तो यह ट्यूटोरियल Aspose.Words for .NET के साथ इसे कैसे करें, बिल्कुल दिखाता है। आप **कमांड बटन डालना**, उसकी उपस्थिति समायोजित करना, और उसे क्लिक करने योग्य बनाना सीखेंगे—सभी कुछ C# की कुछ लाइनों में।

यह गाइड प्रोजेक्ट सेटअप से लेकर अंतिम फ़ाइल को सहेजने तक सब कुछ कवर करता है, ताकि आप पूर्ण समाधान को अपने एप्लिकेशन में कॉपी‑पेस्ट कर सकें। साथ ही हम यह भी समझाएंगे कि **क्लिक करने योग्य बटन जोड़ना**, **बटन का आकार सेट करना**, और **कमांड बटन बनाना** प्रोग्रामेटिकली कैसे किया जाता है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो।
* Visual Studio 2022 (या कोई भी IDE जो .NET को सपोर्ट करता हो)।
* Aspose.Words for .NET NuGet पैकेज (`Aspose.Words` संस्करण 23.12 या नया)।
* C# और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी समझ।

कोई अतिरिक्त Office interop असेंबली की आवश्यकता नहीं है क्योंकि Aspose.Words Microsoft Word से पूरी तरह स्वतंत्र रूप से काम करता है।

## Step 1: Set up the .NET project

एक कंसोल एप्लिकेशन बनाएं जो Word ऑटोमेशन कोड को होस्ट करेगा।

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

यह कमांड `WordButtonDemo` नामक नया फ़ोल्डर बनाता है जिसमें चलाने योग्य `Program.cs` होता है और Aspose.Words लाइब्रेरी जोड़ता है।

## Step 2: Create blank word document

पहला कार्य **खाली Word दस्तावेज़ बनाना** है। Aspose.Words एक `Document` क्लास प्रदान करता है जो बॉक्स से बाहर एक खाली Word फ़ाइल का प्रतिनिधित्व करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

एक खाली दस्तावेज़ बनाने से आपको एक साफ़ कैनवास मिलता है जिस पर आप पैराग्राफ, टेबल या इस मामले में OLE कमांड बटन जोड़ सकते हैं।

## Step 3: Initialize DocumentBuilder

`DocumentBuilder` वह सहायक है जो आपको दस्तावेज़ में सामग्री डालने की अनुमति देता है। आपको इसे अभी बनाए गए दस्तावेज़ से जोड़ना होगा।

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

बिल्डर वर्तमान कर्सर स्थिति को बनाए रखता है, इसलिए कोई भी बाद का इन्सर्शन बिल्कुल वहीँ होगा जहाँ आप चाहते हैं।

## Step 4: Insert command button

अब हम **कमांड बटन डालते** हैं (एक OLE `Forms2OleControl`) दस्तावेज़ में। `InsertForms2OleControl` मेथड को तीन आर्ग्यूमेंट्स की आवश्यकता होती है:

1. OLE कंट्रोल का ProgID – मानक बटन के लिए `"CommandButton"`।
2. एक `Rectangle` जो **बटन का आकार सेट** करता है और उसकी स्थिति निर्धारित करता है।
3. वह कैप्शन जो बटन पर दिखेगा।

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

जब दस्तावेज़ Word में खोला जाता है, तो बटन किसी भी नेटिव फ़ॉर्म कंट्रोल की तरह व्यवहार करता है—आप इसे क्लिक कर सकते हैं, और Word संबंधित मैक्रो (यदि मौजूद हो) को फ़ायर करेगा। यह **क्लिक करने योग्य बटन जोड़ने** की आवश्यकता को पूरा करता है।

### Why use Forms2OleControl?

`Forms2OleControl` OLE ऑब्जेक्ट को सीधे DOCX फ़ाइल में एम्बेड करता है, जिससे कंट्रोल की प्रॉपर्टीज़ बिना Word Interop असेंबली की आवश्यकता के संरक्षित रहती हैं। यह **कमांड बटन बनाने** का सबसे भरोसेमंद तरीका है जो विभिन्न Word संस्करणों में काम करता है।

## Step 5: Customize the button (optional)

आप **बटन का आकार सेट** अधिक सटीक रूप से करना चाह सकते हैं या फ़ॉन्ट, बैकग्राउंड कलर जैसी अतिरिक्त प्रॉपर्टीज़ बदलना चाह सकते हैं। Aspose.Words अंतर्निहित OLE ऑब्जेक्ट को एक्सपोज़ करता है, जिससे आगे की ट्यूनिंग संभव होती है।

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

यदि आपको अलग आकार चाहिए, तो Step 4 में `Rectangle` मानों को समायोजित करें। निर्देशांक पॉइंट्स में मापे जाते हैं (1 pt = 1/72 इंच), इसलिए `120` लगभग 1.67 इंच की चौड़ाई के बराबर है।

## Step 6: Save the document

अंत में, दस्तावेज़ को डिस्क पर लिखें। परिणामी फ़ाइल में एक **खाली Word दस्तावेज़** होगा जिसमें पूरी तरह कार्यशील कमांड बटन होगा।

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

जब आप `CommandButtonDemo.docx` को Microsoft Word में खोलेंगे, तो आपको “Click Me” लेबल वाला बटन दिखेगा। बटन पर क्लिक करने से डिफ़ॉल्ट मैक्रो डायलॉग प्रदर्शित होगा, जब तक आप कोई कस्टम मैक्रो नहीं जोड़ते।

## Complete source code

नीचे पूरा प्रोग्राम है जिसे आप `Program.cs` में कॉपी कर सकते हैं। इसमें ऊपर वर्णित सभी चरण शामिल हैं और बिना किसी संशोधन के कम्पाइल हो जाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Expected result

प्रोग्राम चलाने पर `CommandButtonDemo.docx` बनता है। फ़ाइल को Word में खोलने पर दिखेगा:

* एक पेज जिसमें **Click Me** लेबल वाला बटन हो।
* बटन **बटन का आकार सेट** (120 × 30 पॉइंट) को सम्मानित करता है।
* बटन पर क्लिक करने से Word का डिफ़ॉल्ट कमांड‑बटन व्यवहार ट्रिगर होता है, जिससे **क्लिक करने योग्य बटन जोड़ने** की प्रक्रिया सफल साबित होती है।

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Does this work with .doc files?** | हाँ। `doc.Save("file.doc")` में फ़ाइल एक्सटेंशन बदल दें। OLE कंट्रोल लेगेसी बाइनरी फ़ॉर्मेट में भी संग्रहीत होता है। |
| **What if I need multiple buttons?** | `InsertForms2OleControl` को बार‑बार कॉल करें, प्रत्येक नए बटन के लिए `Rectangle` को समायोजित करें ताकि ओवरलैप न हो। |
| **Can I attach a macro to the button?** | बटन स्वयं में मैक्रो कोड नहीं होता। आपको दस्तावेज़ में VBA मैक्रो मैन्युअली या `Document` ऑब्जेक्ट की `Modules` कलेक्शन के माध्यम से जोड़ना होगा। |
| **Is the button visible in PDF export?** | जब आप Aspose.Words का उपयोग करके DOCX को PDF में एक्सपोर्ट करते हैं, तो बटन एक स्थैतिक इमेज के रूप में रेंडर होता है, न कि इंटरैक्टिव कंट्रोल के रूप में। |
| **What versions of Word are supported?** | OLE कमांड बटन Word 2007 और उसके बाद के संस्करणों में काम करता है, क्योंकि यह मानक Forms2.0 स्पेसिफिकेशन का पालन करता है। |

## Conclusion

अब आप **खाली Word दस्तावेज़ बनाना**, **कमांड बटन डालना**, **क्लिक करने योग्य बटन जोड़ना**, और **बटन का आकार सेट** करना Aspose.Words for .NET का उपयोग करके जानते हैं। पूरा उदाहरण **कमांड बटन बनाने** की पूरी वर्कफ़्लो को शुरुआत से अंत तक दर्शाता है, जिससे आप अधिक उन्नत Word ऑटोमेशन कार्यों के लिए एक ठोस नींव प्राप्त कर सकते हैं।

## Next steps

* `InsertForms2OleControl` में ProgID बदलकर अन्य OLE कंट्रोल्स (जैसे `CheckBox`, `ListBox`) का अन्वेषण करें।
* बटन को VBA मैक्रो के साथ जोड़ें ताकि उपयोगकर्ता के क्लिक करने पर कस्टम एक्शन निष्पादित हो सके।
* बटन डालने से पहले `DocumentBuilder` का उपयोग करके टेबल, इमेज या फुटनोट जैसी अतिरिक्त सामग्री जोड़ें।
* अपने दस्तावेज़ के लेआउट आवश्यकताओं के अनुसार **बटन का आकार सेट** मानों के साथ प्रयोग करें।

Happy coding, and enjoy building richer Word documents with interactive controls!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}