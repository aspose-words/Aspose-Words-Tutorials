---
category: general
date: 2026-09-21
description: Aspose.Words और C# के साथ Word दस्तावेज़ में ActiveX कमांड बटन बनाना
  सीखें। चरण‑दर‑चरण मार्गदर्शिका में सम्मिलन, स्थिति निर्धारण और सहेजना शामिल है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: hi
lastmod: 2026-09-21
og_description: C# और Aspose.Words का उपयोग करके Word दस्तावेज़ में ActiveX कमांड
  बटन बनाएं। इस पूर्ण ट्यूटोरियल का पालन करके बटन को प्रोग्रामेटिकली सम्मिलित, स्थित
  और सहेजें।
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: C# के साथ Word में ActiveX कमांड बटन बनाएं – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: C# का उपयोग करके Word में ActiveX कमांड बटन कैसे बनाएं
url: /hi/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# का उपयोग करके Word में ActiveX कमांड बटन कैसे बनाएं

यदि आपको Word फ़ाइल के भीतर **ActiveX कमांड बटन बनाएं** की आवश्यकता है, तो यह गाइड आपको सटीक चरण दिखाता है। Aspose.Words for .NET का उपयोग करके आप बटन को पूरी तरह से C# कोड से जोड़ सकते हैं, उसकी स्थिति निर्धारित कर सकते हैं, और कॉन्फ़िगर कर सकते हैं।

ActiveX बटन का प्रोग्रामेटिक इन्सर्शन मैन्युअल UI कार्य को समाप्त करता है और फॉर्म, रिपोर्ट, या इंटरैक्टिव टेम्प्लेट के लिए स्वचालित दस्तावेज़ निर्माण को सक्षम बनाता है। इस ट्यूटोरियल में आप **DocumentBuilder**, **InsertForms2OleControl** मेथड, और संबंधित प्रॉपर्टीज़ का उपयोग करके पूरी तरह कार्यात्मक बटन बनाना सीखेंगे।

## आपको क्या चाहिए

* .NET 6.0 SDK या बाद का संस्करण (कोड .NET Framework 4.7+ के साथ भी काम करता है)
* Aspose.Words for .NET (NuGet पैकेज `Aspose.Words`)
* Visual Studio 2022 या VS Code जैसा IDE
* C# और Word दस्तावेज़ अवधारणाओं का बुनियादी ज्ञान

Microsoft Word पर निर्भरता नहीं है, इसलिए अतिरिक्त Office इंस्टॉलेशन की आवश्यकता नहीं है क्योंकि Aspose.Words स्वतंत्र रूप से काम करता है।

## चरण 1: C# प्रोजेक्ट सेट अप करें

एक नया कंसोल प्रोजेक्ट बनाएं और Aspose.Words पैकेज जोड़ें।

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

`Aspose.Words` लाइब्रेरी **DocumentBuilder** क्लास प्रदान करती है जिसका उपयोग हम दस्तावेज़ को संशोधित करने के लिए करेंगे।

## चरण 2: दस्तावेज़ और बिल्डर को इनिशियलाइज़ करें

पहला कोड ब्लॉक एक खाली दस्तावेज़ और एक `DocumentBuilder` इंस्टेंस बनाता है। यह ऑब्जेक्ट सभी Word‑प्रोसेसिंग ऑपरेशनों का एंट्री पॉइंट है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**यह क्यों महत्वपूर्ण है:** `DocumentBuilder` वर्तमान कर्सर पोजीशन को बनाए रखता है, इसलिए उसके बाद की कोई भी इन्सर्शन ठीक उसी जगह पर दिखाई देगी जहाँ आप कर्सर रखते हैं।

## चरण 3: ActiveX कमांड बटन इन्सर्ट करें

**InsertForms2OleControl** मेथड अनुरोधित प्रकार का ActiveX कंट्रोल बनाता है। यहाँ हम `CommandButton` का अनुरोध करते हैं और उसके आकार को पॉइंट्स में निर्दिष्ट करते हैं (200 × 30 pt)।

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**व्याख्या:**  
* `OleControlType.CommandButton` Aspose.Words को बताता है कि बटन बनाना है, न कि कोई अन्य कंट्रोल टाइप।  
* यह मेथड एक `Forms2OleControl` ऑब्जेक्ट रिटर्न करता है, जो पोजीशनिंग और प्रॉपर्टी फ़ील्ड्स को एक्सपोज़ करता है।

## चरण 4: बटन को पोजीशन करें और उसकी प्रॉपर्टीज़ सेट करें

इन्सर्शन के बाद आप बटन को पेज पर किसी भी स्थान पर ले जा सकते हैं और उसे प्रोग्रामेटिक नाम तथा दृश्यमान कैप्शन दे सकते हैं।

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**प्रो टिप:** कॉऑर्डिनेट सिस्टम पेज के टॉप‑लेफ़्ट कोने से शुरू होता है। बटन को अन्य फॉर्म फ़ील्ड्स के साथ संरेखित करने के लिए `Left` और `Top` को समायोजित करें।

## चरण 5: दस्तावेज़ को सेव करें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल में ActiveX बटन होगा, जिसे Microsoft Word में खोलने पर बटन इंटरैक्टिव बन जाएगा।

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

जब आप Word में `ActiveXCommandButton.docx` खोलेंगे, तो आपको निर्दिष्ट स्थान पर **Submit** लेबल वाला बटन दिखाई देगा। Word में इसे क्लिक करने से डिफ़ॉल्ट कमांड‑बटन व्यवहार ट्रिगर होगा (जिसे आप बाद में VBA या Word ऐड‑इन्स से कस्टमाइज़ कर सकते हैं)।

## पूर्ण, रन करने योग्य उदाहरण

सभी भागों को मिलाकर एक स्व-निहित प्रोग्राम बनता है जिसे आप कॉपी, पेस्ट और रन कर सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**अपेक्षित आउटपुट:** कंसोल पर *“Document created successfully.”* प्रदर्शित होगा और फ़ोल्डर में `ActiveXCommandButton.docx` मौजूद होगा। Microsoft Word में फ़ाइल खोलने पर बाएँ मार्जिन से 100 pt और पेज के टॉप से 150 pt पर स्थित क्लिक करने योग्य **Submit** बटन दिखेगा।

## सामान्य समस्याएँ और उनका समाधान

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| बटन पृष्ठ से बाहर दिखाई देता है | `Left`/`Top` मान पेज के आयामों से अधिक हैं | `doc.FirstSection.PageSetup.PageWidth` और `PageHeight` का उपयोग करके सुरक्षित कॉऑर्डिनेट्स की गणना करें |
| बटन Word में दिखाई नहीं देता | दस्तावेज़ ऐसे फ़ॉर्मेट में सेव हुआ है जो ActiveX कंट्रोल्स को हटाता है (जैसे `.txt`) | हमेशा `.docx` या `.doc` के रूप में सेव करें |
| रनटाइम त्रुटि `ArgumentOutOfRangeException` | चौड़ाई या ऊँचाई शून्य या नकारात्मक सेट की गई है | `InsertForms2OleControl` को पास किए गए आकार के आर्ग्युमेंट्स को सकारात्मक संख्या रखें |

## समाधान का विस्तार

आप बटन को अतिरिक्त प्रॉपर्टीज़ जैसे `Enabled`, `Visible` सेट करके या VBA के माध्यम से मैक्रो अटैच करके और अधिक कस्टमाइज़ कर सकते हैं। **Forms2OleControl** क्लास आपको अन्य ActiveX कंट्रोल्स जैसे चेक बॉक्स (`OleControlType.CheckBox`) या कॉम्बो बॉक्स (`OleControlType.ComboBox`) इन्सर्ट करने की भी सुविधा देती है।

यदि आपको लूप में कई बटन जनरेट करने हैं, तो इन्सर्शन लॉजिक को एक हेल्पर मेथड में एन्कैप्सुलेट करें:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## निष्कर्ष

अब आप C# और Aspose.Words का उपयोग करके Word दस्तावेज़ में **ActiveX कमांड बटन बनाना** जानते हैं। ट्यूटोरियल ने प्रोजेक्ट सेटअप, `InsertForms2OleControl` से बटन इन्सर्ट करना, उसे पोजीशन करना, और अंतिम फ़ाइल को सेव करना कवर किया। इस आधार के साथ आप जटिल फॉर्म्स को ऑटोमेट कर सकते हैं, इंटरैक्टिव कंट्रोल्स एम्बेड कर सकते हैं, और Word दस्तावेज़ों को बड़े .NET सॉल्यूशन्स में इंटीग्रेट कर सकते हैं।

अगला, **Aspose.Words ActiveX** फॉर्म फ़ील्ड्स, **C# DocumentBuilder** एडवांस्ड स्टाइलिंग, या चेक बॉक्स और ड्रॉप‑डाउन लिस्ट के लिए **Word में ActiveX कंट्रोल** प्रोग्रामेटिकली जोड़ने जैसे संबंधित विषयों का अन्वेषण करें। विभिन्न कॉऑर्डिनेट्स और साइजेज़ के साथ प्रयोग करें ताकि आपका लेआउट ठीक फिट हो सके। Happy coding!

## आप आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स इस गाइड में प्रदर्शित तकनीकों पर आधारित निकटतम संबंधित विषयों को कवर करते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}