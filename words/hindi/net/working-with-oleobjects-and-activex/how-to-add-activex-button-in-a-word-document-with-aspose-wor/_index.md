---
category: general
date: 2026-08-14
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में ActiveX बटन कैसे जोड़ें
  – एक खाली Word दस्तावेज़ बनाना और प्रोग्रामेटिक रूप से ActiveX बटन सम्मिलित करना
  सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: hi
lastmod: 2026-08-14
og_description: Aspose.Words के साथ Word दस्तावेज़ में ActiveX बटन कैसे जोड़ें। यह
  ट्यूटोरियल दिखाता है कि खाली Word दस्तावेज़ कैसे बनाएं, ActiveX बटन कैसे डालें,
  और परिणाम को कैसे सहेजें।
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Word में ActiveX बटन कैसे जोड़ें – Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Aspose.Words के साथ Word दस्तावेज़ में ActiveX बटन कैसे जोड़ें
url: /hi/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ Word दस्तावेज़ में ActiveX बटन कैसे जोड़ें

यदि आपको उत्पन्न किए गए Word फ़ाइल में **how to add ActiveX** नियंत्रण जोड़ने की आवश्यकता है, तो यह गाइड आपको सटीक चरण दिखाता है। आप प्रोग्रामेटिक रूप से **insert ActiveX button** सीखेंगे, **create empty Word document** से शुरू करके और अंत में एक सहेजी गई फ़ाइल होगी जिसे Microsoft Word में खोला जा सकता है।

VBA कोड चलाने या मैक्रो ट्रिगर करने वाला बटन जोड़ना स्वचालित रिपोर्ट जेनरेटर, फॉर्म टेम्पलेट या इंटरैक्टिव कॉन्ट्रैक्ट्स के लिए सामान्य आवश्यकता है। Aspose.Words for .NET का उपयोग करके आप Office लॉन्च किए बिना दस्तावेज़ बना सकते हैं, जिससे प्रक्रिया तेज़ और सर्वर‑फ़्रेंडली रहती है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 (या बाद का) SDK स्थापित हो।
* Visual Studio 2022 या कोई भी C#‑संगत IDE।
* Aspose.Words for .NET NuGet पैकेज (`Aspose.Words` संस्करण 24.9 या नया)।  
  इसे इस तरह स्थापित करें:
  ```bash
  dotnet add package Aspose.Words
  ```
* यदि आप ActiveX बटन का परीक्षण करने की योजना बना रहे हैं तो Windows वातावरण आवश्यक है, क्योंकि ActiveX नियंत्रणों को Microsoft Word के Windows संस्करण की आवश्यकता होती है।

## Step 1: Create an empty Word document

पहला कार्य है मेमोरी में **create empty Word document** बनाना। इस उद्देश्य के लिए Aspose.Words `Document` क्लास प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` पूरे .docx फ़ाइल का प्रतिनिधित्व करता है। इस बिंदु पर दस्तावेज़ में कोई पृष्ठ नहीं होते, लेकिन आप तुरंत सामग्री जोड़ना शुरू कर सकते हैं।

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` एक सहायक है जो आपको दस्तावेज़ में टेक्स्ट, इमेज और अन्य ऑब्जेक्ट डालने की सुविधा देता है। यह उसी `Document` इंस्टेंस पर काम करता है जिसे आपने अभी बनाया है।

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

बिल्डर एक कर्सर पोज़िशन बनाए रखता है; इस पंक्ति के बाद आप जो भी डालते हैं वह पहले पृष्ठ की शुरुआत में दिखाई देगा।

## Step 3: Insert an ActiveX CommandButton control

Aspose.Words `InsertForms2OleControl` मेथड को उजागर करता है जिससे आप लेगेसी फ़ॉर्म नियंत्रण, जिसमें ActiveX भी शामिल है, जोड़ सकते हैं। इस मेथड को नियंत्रण का प्रकार और उसका आकार पॉइंट्स में चाहिए होता है।

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

वापसी में मिलने वाला `Forms2OleControl` ऑब्जेक्ट आपको नियंत्रण के नाम और कैप्शन जैसी प्रॉपर्टीज़ कॉन्फ़िगर करने देता है।

## Step 4: Configure the button’s properties

एक सार्थक `Name` सेट करने से बाद में आप VBA कोड से इस नियंत्रण को रेफ़र कर सकते हैं। `Caption` वह टेक्स्ट है जो उपयोगकर्ता बटन पर देखता है।

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** नाम को छोटा और अल्फ़ान्यूमेरिक रखें; Word उन नामों को अस्वीकार कर देगा जिनमें स्पेस या विशेष अक्षर हों।

## Step 5: Save the document

अंत में, दस्तावेज़ को डिस्क पर लिखें। आधुनिक Word फ़ाइलों के लिए `.docx` एक्सटेंशन उपयोग करें; ActiveX बटन `.doc` फ़ाइलों में भी समान रूप से काम करता है, लेकिन नए प्रोजेक्ट्स के लिए `.docx` प्राथमिक फ़ॉर्मेट है।

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

जब आप `ActiveXButton.docx` को Microsoft Word में खोलेंगे, तो आपको एक क्लिक करने योग्य **Submit** बटन दिखाई देगा। यदि आप मैक्रो सक्षम करते हैं, तो आप `btnSubmit_Click` पर VBA कोड संलग्न कर सकते हैं और बटन क्लिक होने पर वह चलाया जा सकता है।

## Full, runnable example

सभी हिस्सों को मिलाकर आपको एक स्व-निहित प्रोग्राम मिलता है जिसे आप कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output** – प्रोग्राम चलाने के बाद, कंसोल सहेजे गए स्थान को प्रिंट करता है, और Word में उत्पन्न फ़ाइल खोलने पर पहली पृष्ठ के शीर्ष पर **Submit** लेबल वाला बटन दिखता है।

## Handling common questions and edge cases

### Does the button work in all Word versions?

ActiveX नियंत्रण Windows पर डेस्कटॉप संस्करण के Word में समर्थित हैं। वे Word Online, macOS के Word या मोबाइल क्लाइंट्स में रेंडर नहीं होते। यदि आपको क्रॉस‑प्लेटफ़ॉर्म इंटरैक्टिविटी चाहिए, तो कंटेंट कंट्रोल या HTML‑आधारित समाधान पर विचार करें।

### What if I need a different size or position?

`InsertForms2OleControl` नियंत्रण को वर्तमान बिल्डर कर्सर पर रखता है। इसे स्थानांतरित करने के लिए, डालने से पहले `builder.MoveTo` से कर्सर समायोजित करें, या निर्माण के बाद नियंत्रण की `Left` और `Top` प्रॉपर्टीज़ बदलें:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Can I add other ActiveX types?

हाँ। `Forms2OleControlType` एनेमरेशन में `CheckBox`, `OptionButton`, `ListBox` आदि शामिल हैं। `CommandButton` को इच्छित एनेम मान से बदलें और प्रॉपर्टीज़ उसी अनुसार समायोजित करें।

### Is a macro required for the button to do something?

बटन स्वयं कुछ नहीं करता जब तक आप VBA कोड नहीं जोड़ते। Word में **Alt+F11** दबाकर VBA एडिटर खोलें, `btnSubmit_Click` खोजें और वांछित लॉजिक लिखें। यदि आप **SaveFormat.Doc** (legacy `.doc`) फ़ॉर्मेट का उपयोग करते हैं तो उत्पन्न दस्तावेज़ VBA प्रोजेक्ट रखेगा, लेकिन `.docx` फ़ाइलें VBA मैक्रो संग्रहीत नहीं कर सकतीं। एम्बेडेड VBA चाहिए तो `.doc` फ़ॉर्मेट उपयोग करें।

## Conclusion

अब आप Aspose.Words का उपयोग करके Word फ़ाइल में **how to add ActiveX** नियंत्रण जोड़ना जानते हैं। **create empty Word document** बनाकर, `DocumentBuilder` को प्रारंभ करके, **insert ActiveX button**, उसकी प्रॉपर्टीज़ कॉन्फ़िगर करके और फ़ाइल सहेजकर, आप सीधे अपने .NET कोड से इंटरैक्टिव Word टेम्पलेट बना सकते हैं।

अगले चरण में **insert ActiveX button** इवेंट हैंडलिंग, टेबल या इमेज के लिए **create word document aspose**, और एंटरप्राइज़ डिप्लॉयमेंट के लिए मैक्रो‑एनेबल्ड दस्तावेज़ को सुरक्षित करने जैसे संबंधित विषयों का अन्वेषण करें। विभिन्न नियंत्रण प्रकारों और लेआउट विकल्पों के साथ प्रयोग करें ताकि उपयोगकर्ता अनुभव को अपने एप्लिकेशन की जरूरतों के अनुसार अनुकूलित किया जा सके।

कोडिंग का आनंद लें!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगा सकें।

- [Aspose.Words का उपयोग करके हेडर और फुटर के साथ Word दस्तावेज़ बनाएं](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में ग्रुप शेप बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words का उपयोग करके टेबल के साथ Word दस्तावेज़ बनाएं](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}