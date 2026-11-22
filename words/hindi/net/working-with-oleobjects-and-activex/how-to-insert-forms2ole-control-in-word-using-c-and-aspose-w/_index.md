---
category: general
date: 2026-11-22
description: C# के साथ Word में Forms2Ole नियंत्रण डालना सीखें। यह चरण‑दर‑चरण गाइड
  DocumentBuilder, कमांड बटन की स्थिति और .docx फ़ाइल को सहेजने को कवर करता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: hi
lastmod: 2026-11-22
og_description: C# के साथ Word में Forms2Ole नियंत्रण डालें। Aspose.Words और DocumentBuilder
  का उपयोग करके कमांड बटन जोड़ने के लिए इस गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: C# के साथ Word में Forms2Ole नियंत्रण डालें – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# और Aspose.Words का उपयोग करके Word में Forms2Ole कंट्रोल कैसे डालें
url: /hi/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# और Aspose.Words का उपयोग करके Word में Forms2Ole कंट्रोल कैसे डालें

यदि आपको Word में **Forms2Ole कंट्रोल डालना** है, तो यह ट्यूटोरियल आपको C# के साथ इसे कैसे करना है दिखाता है। चाहे आप एक भरने योग्य टेम्पलेट बना रहे हों या फॉर्म निर्माण को स्वचालित कर रहे हों, नीचे दिया गया समाधान आपको प्रोग्रामेटिकली एक कमांड बटन जोड़ने की अनुमति देता है।

आप सीखेंगे कि कैसे एक खाली दस्तावेज़ बनाएं, नियंत्रण रखने के लिए `DocumentBuilder` का उपयोग करें, और परिणाम को `.docx` के रूप में सहेजें। गाइड सामान्य समस्याओं को भी कवर करता है, जैसे कि निर्देशांक प्रणाली और पुराने Word संस्करणों के साथ संगतता।

## आवश्यकताएँ

* .NET 6.0 या बाद का (कोड .NET Framework 4.6+ के साथ भी काम करता है)
* Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`)
* C# और Word ऑब्जेक्ट मॉडल की बुनियादी समझ
* Visual Studio या VS Code जैसे IDE

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेस इम्पोर्ट करें

एक नया कंसोल एप्लिकेशन बनाएं और Aspose.Words पैकेज जोड़ें:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

`Program.cs` में आवश्यक नेमस्पेस इम्पोर्ट करें:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **प्रो टिप:** `Forms2OleControl` API के पूर्ण समर्थन के लिए नवीनतम Aspose.Words संस्करण का उपयोग करें।

## चरण 2: एक खाली दस्तावेज़ बनाएं और DocumentBuilder को इनिशियलाइज़ करें

`Document` क्लास Word फ़ाइल का प्रतिनिधित्व करती है, जबकि `DocumentBuilder` सामग्री डालने के लिए मेथड प्रदान करता है।

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` एक कर्सर की तरह काम करता है; इस लाइन के बाद आप दस्तावेज़ में कहीं भी तत्व रखना शुरू कर सकते हैं।

## चरण 3: बटन की स्थिति और आकार निर्धारित करें

Word निर्देशांक को पॉइंट्स में मापता है (1 pt ≈ 1/72 in)। `System.Drawing` से `Rectangle` स्ट्रक्ट नियंत्रण की सीमाओं को वर्णित करता है।

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` नियंत्रण को वर्तमान पृष्ठ के टॉप‑लेफ़्ट कोने में रखता है।
* बटन को कहीं और ले जाने के लिए `x` और `y` समायोजित करें (उदाहरण: `new Rectangle(150, 200, 100, 30)`).

## चरण 4: Forms2Ole कमांड बटन डालें

अब `InsertForms2OleControl` का उपयोग करके नियंत्रण जोड़ें। इस मेथड को नियंत्रण प्रकार, एक नाम, और ऊपर परिभाषित सीमाओं की आवश्यकता होती है।

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

वापसी में मिला `Forms2OleControl` ऑब्जेक्ट आपको `Enabled`, `Visible` जैसी प्रॉपर्टीज़ बदलने या बाद में मैक्रो नाम संलग्न करने की अनुमति देता है।

### Forms2Ole का उपयोग क्यों करें?

* **Legacy compatibility** – Forms2Ole कंट्रोल Word 97‑2003 (`.doc`) और नए `.docx` फ़ाइलों में काम करते हैं।
* **Macro support** – वे VBA मैक्रो को ट्रिगर कर सकते हैं, जिससे वे इंटरैक्टिव टेम्पलेट्स के लिए आदर्श होते हैं।
* **Precise placement** – कंटेंट कंट्रोल्स के विपरीत, आप सटीक निर्देशांक नियंत्रित कर सकते हैं।

## चरण 5: दस्तावेज़ सहेजें

अंत में, फ़ाइल को डिस्क पर लिखें। ऐसा फ़ोल्डर चुनें जहाँ आपके पास लिखने की अनुमति हो।

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`output.docx` को Microsoft Word में खोलें। आपको पहले पृष्ठ के टॉप‑लेफ़्ट कोने में **ClickMe** लेबल वाला बटन दिखाई देगा। Word में इसे क्लिक करने से कुछ नहीं होगा जब तक आप मैक्रो असाइन नहीं करते, लेकिन नियंत्रण पूरी तरह कार्यात्मक है।

## सामान्य किनारे मामलों को संभालना

| Situation | How to address it |
|-----------|-------------------|
| **बटन पृष्ठ से बाहर दिख रहा है** | जाँचें कि `Rectangle` निर्देशांक पृष्ठ मार्जिन के भीतर हैं। सुरक्षित सीमाएँ गणना करने के लिए `builder.PageSetup.PageWidth` और `PageHeight` का उपयोग करें। |
| **पुराने Word संस्करणों में नियंत्रण दिखाई नहीं देता** | दस्तावेज़ को `.doc` के रूप में सहेजें (`doc.Save("output.doc", SaveFormat.Doc)`) ताकि Word 97‑2003 के साथ Forms2Ole संगतता सुनिश्चित हो सके। |
| **कैप्शन बदलने की आवश्यकता** | डालने के बाद, `commandButton.Caption = "Submit";` सेट करें। |
| **मैक्रो असाइन करें** | `commandButton.MacroName = "MyMacro"` सेट करें; मैक्रो दस्तावेज़ के VBA प्रोजेक्ट में मौजूद होना चाहिए। |
| **एकाधिक बटन** | विभिन्न `Rectangle` मानों और अद्वितीय नामों के साथ चरण 4 दोहराएँ। |

## पूर्ण, चलाने योग्य उदाहरण

सब कुछ मिलाकर, यहाँ एक स्व-निहित प्रोग्राम है जिसे आप कॉपी, पेस्ट और चलाने के लिए उपयोग कर सकते हैं:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**अपेक्षित आउटपुट:** प्रोग्राम चलाने के बाद, `output.docx` Word में खुलता है जिसमें शीर्ष‑बाएँ कोने में *Click Me!* लेबल वाला क्लिक करने योग्य बटन होता है।

## निष्कर्ष

अब आप जानते हैं कि C# और Aspose.Words का उपयोग करके **Word में Forms2Ole कंट्रोल कैसे डालें**। प्रक्रिया में `Document` बनाना, `Rectangle` की स्थिति निर्धारित करना, और `DocumentBuilder` के माध्यम से `InsertForms2OleControl` को कॉल करना शामिल है। पूर्ण कोड नमूना और किनारे मामलों के मार्गदर्शन के साथ, आप किसी भी स्वचालित Word वर्कफ़्लो में कमांड बटन को एकीकृत कर सकते हैं।

### अगले कदम

* `CheckBox` या `OptionButton` जैसे अन्य `ControlType` मानों का अन्वेषण करें।
* इंटरैक्टिव फॉर्म्स के लिए Forms2Ole कंट्रोल को VBA मैक्रो के साथ संयोजित करें।
* विशिष्ट पैराग्राफ़ या टेबल पर बटन रखने के लिए `DocumentBuilder.MoveTo` का उपयोग करें।
* उन्नत प्रॉपर्टी सेटिंग्स के लिए Aspose.Words की **Forms2Ole** डॉक्यूमेंटेशन देखें।

कोडिंग का आनंद लें, और C# और Aspose.Words के साथ अधिक समृद्ध Word दस्तावेज़ बनाते रहें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [C# का उपयोग करके Word दस्तावेज़ में OLE कमांड बटन कैसे डालें](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Aspose.Words के साथ Word में ActiveX कंट्रोल कैसे जोड़ें – चरण‑दर‑चरण गाइड](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Aspose.Words के साथ Word दस्तावेज़ में कमांड बटन जोड़ें – पूर्ण गाइड](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}