---
category: general
date: 2026-10-26
description: सी# में वर्ड दस्तावेज़ बनाना और प्रोग्रामेटिकली एक एक्टिवएक्स बटन जोड़ना
  सीखें। यह चरण‑दर‑चरण गाइड कमांड बटन डालने, डिजाइन समय पर उसे छिपाने, और फ़ाइल को
  सहेजने को कवर करता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: hi
lastmod: 2026-10-26
og_description: C# में Word दस्तावेज़ बनाएं और प्रोग्रामेटिकली एक ActiveX बटन जोड़ें।
  इस पूर्ण ट्यूटोरियल का पालन करें ताकि आप एक कमांड बटन एम्बेड कर सकें जो केवल रनटाइम
  पर दिखाई देता है।
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: ActiveX कमांड बटन के साथ C# में Word दस्तावेज़ बनाएं – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: ActiveX कमांड बटन के साथ C# में Word दस्तावेज़ कैसे बनाएं
url: /hi/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ ActiveX कमांड बटन वाला Word दस्तावेज़ कैसे बनाएं

यदि आपको **create Word document C#** की आवश्यकता है जिसमें एक इंटरैक्टिव बटन हो, तो यह गाइड आपको बिल्कुल वही दिखाता है। पहले दो वाक्यों के अंत तक आप समग्र दृष्टिकोण समझ जाएंगे, और अगले चरण आपको कोड की प्रत्येक पंक्ति के माध्यम से ले जाएंगे जो आपको लिखनी होगी।

आप सीखेंगे कि ActiveX बटन कैसे जोड़ें, डिज़ाइन के दौरान इसे छिपाएँ, और केवल उपयोगकर्ता फ़ाइल खोलने पर इसे दिखाई दें। ट्यूटोरियल सामान्य समस्याओं जैसे सुरक्षा चेतावनियों और संस्करण संगतता को भी कवर करता है, ताकि आप भरोसेमंद दस्तावेज़ वितरित कर सकें।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 या बाद का संस्करण स्थापित  
* **Aspose.Words for .NET** की लाइसेंस प्राप्त प्रति (नि:शुल्क ट्रायल प्रयोग के लिए काम करता है)  
* C# और Visual Studio (या कोई भी IDE जो .NET को सपोर्ट करता हो) की बुनियादी जानकारी  

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## Step 1: Create a Word document C# and initialize the DocumentBuilder

पहला चरण `Document` ऑब्जेक्ट और `DocumentBuilder` को इंस्टैंशिएट करना है। `Document` पूरे .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` सामग्री जोड़ने के लिए फ़्लुएंट मेथड्स प्रदान करता है।

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** बिना `DocumentBuilder` के आपको OpenXML DOM को मैन्युअल रूप से मैनीपुलेट करना पड़ेगा, जो त्रुटिप्रवण और पढ़ने में कठिन होता है। बिल्डर इन विवरणों को एब्स्ट्रैक्ट करता है और एक सही‑फ़ॉर्मेटेड Word फ़ाइल सुनिश्चित करता है।

## Step 2: How to add ActiveX button – insert a CommandButton control

अब हम एक **CommandButton ActiveX control** को एक विशिष्ट स्थान पर डालते हैं। आयत (rectangle) बटन की स्थिति (X, Y) और आकार (चौड़ाई, ऊँचाई) को पॉइंट्स में परिभाषित करती है।

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Why this matters:** `InsertForms2OleControl` वह एकमात्र Aspose.Words मेथड है जो वास्तविक ActiveX OLE ऑब्जेक्ट बनाता है। `Forms2OleControlType.CommandButton` एन्‍उम वैल्यू Word को बताती है कि वह एक क्लिक‑योग्य बटन एम्बेड करे, न कि सामान्य OLE कंटेनर।

## Step 3: Programmatically add command button – hide it until runtime

Word डिफ़ॉल्ट रूप से किसी भी इन्सर्टेड शेप को विज़िबल मानता है। टेम्पलेट डिज़ाइन करते समय बटन को अदृश्य रखने के लिए, बिल्डर द्वारा अभी‑ही बनाए गए शेप पर `Hidden` प्रॉपर्टी सेट करें।

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Why this matters:** `Hidden = true` सेट करने से बटन डिज़ाइन व्यू में अव्यवस्था नहीं बनाता। जब दस्तावेज़ Word में खुलता है, तो रन‑टाइम वातावरण स्वचालित रूप से कंट्रोल को दिखा देता है, जिससे इच्छित यूज़र एक्सपीरियंस बना रहता है।

## Step 4: Save the file – create command button word document

अंत में, दस्तावेज़ को डिस्क पर लिखें। ऐसा पाथ चुनें जहाँ आपका एप्लिकेशन लिख सके, और आधुनिक संगतता सुनिश्चित करने के लिए `.docx` एक्सटेंशन उपयोग करें।

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Why this matters:** `.docx` के रूप में सेव करने से एम्बेडेड ActiveX कंट्रोल Office Open XML मानक के अनुरूप रहता है, जिसे Word 2007 और बाद के संस्करण सपोर्ट करते हैं। यदि आपको लेगेसी `.doc` की जरूरत है, तो एक्सटेंशन बदलें और `SaveFormat.Doc` उपयोग करें।

## Full working example

सब कुछ मिलाकर, यहाँ पूरा प्रोग्राम है जिसे आप कॉपी, पेस्ट और रन कर सकते हैं:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Expected output:** प्रोग्राम चलाने के बाद, `C:\Temp\ActiveX.docx` को Microsoft Word में खोलें। आपको एक खाली दस्तावेज़ दिखेगा; डिज़ाइन मोड में बटन दिखाई नहीं देगा। फ़ील्ड कोड टॉगल करने के लिए **Alt + F9** दबाएँ, फिर बटन के क्षेत्र पर क्लिक करें—Word ActiveX कंट्रोल रेंडर करेगा, और आप उसके साथ इंटरैक्ट कर सकते हैं (जैसे, प्रॉपर्टीज़ देखने के लिए डबल‑क्लिक)।

## Edge cases and best‑practice tips

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **User disables ActiveX** | Word सुरक्षा चेतावनी दिखा सकता है या कंट्रोल को ब्लॉक कर सकता है। | उपयोगकर्ताओं को Trust Center में “ActiveX controls” को सक्षम करने के निर्देश दें, या मैक्रो‑साइन्ड वैकल्पिक समाधान प्रदान करें। |
| **Document opened in Word Online** | Word Online ActiveX को सपोर्ट नहीं करता; बटन हट जाएगा। | क्लाउड संगतता के लिए फॉलबैक हाइपरलिंक या कंटेंट कंट्रोल उपयोग करें। |
| **Different DPI settings** | हाई‑DPI डिस्प्ले पर आयत का आकार बड़ा या छोटा दिख सकता है। | डिफ़ॉल्ट `GraphicsUnit.Point` उपयोग करें और सामान्य DPI सेटिंग्स (96 dpi, 120 dpi) पर टेस्ट करें। |
| **Multiple buttons** | `GetChildNodes(NodeType.Shape, true)[0]` कॉल केवल पहला शेप रिट्रीव करता है। | `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` पर लूप करें और आप जो भी शेप जोड़ें, उसके लिए `Hidden` सेट करें। |
| **Legacy .doc format** | `.doc` में सेव करने पर कुछ ActiveX प्रॉपर्टीज़ खो सकती हैं। | जब तक कोई सख्त लेगेसी आवश्यकता न हो, `.docx` को प्राथमिकता दें। |

**Pro tip:** बटन डालने के बाद, आप Word UI के माध्यम से उसके `OnAction` प्रॉपर्टी को मैक्रो असाइन कर सकते हैं। इससे आप अतिरिक्त C# कोड लिखे बिना कस्टम क्लिक बिहेवियर परिभाषित कर सकते हैं।

## Frequently asked questions

* **Does this work with .NET Core?**  
  हाँ। Aspose.Words for .NET पूरी तरह से .NET 5, .NET 6 और बाद के संस्करणों के साथ संगत है। वही NuGet पैकेज रेफ़रेंस करें।

* **Can I change the button caption after the document is generated?**  
  `InsertForms2OleControl` में सेट किया गया कैप्शन डिफ़ॉल्ट डिज़ाइन‑टाइम टेक्स्ट बन जाता है। उपयोगकर्ता इसे Word में एडिट कर सकते हैं, लेकिन आप `Shape.OleFormat` API के माध्यम से OLE ऑब्जेक्ट की प्रॉपर्टीज़ एक्सेस करके प्रोग्रामेटिकली भी अपडेट कर सकते हैं।

* **What if I need a different size for the button?**  
  `RectangleF` मानों को समायोजित करें। पहले दो पैरामीटर X‑ और Y‑कोऑर्डिनेट्स हैं; अंतिम दो चौड़ाई और ऊँचाई पॉइंट्स में हैं (1 pt = 1/72 इंच)।

## Conclusion

अब आप **create Word document C#** और **programmatically add command button** को Aspose.Words की मदद से कर सकते हैं। ट्यूटोरियल ने दस्तावेज़ इनिशियलाइज़ेशन, ActiveX बटन इन्सर्शन, रन‑टाइम तक छुपाने, और अंतिम फ़ाइल को सेव करने को कवर किया। इन बिल्डिंग ब्लॉक्स के साथ आप किसी भी Word टेम्पलेट में इंटरैक्टिव कंट्रोल एम्बेड कर सकते हैं।

अगला कदम: **how to add ActiveX button** इवेंट हैंडलिंग, **create command button word** स्टाइलिंग VBA के साथ, और **programmatically add command button** को मौजूदा दस्तावेज़ों में जोड़ना। चेकबॉक्स, कॉम्बो बॉक्स, या कस्टम OLE ऑब्जेक्ट्स के लिए भी वही चरण अपनाएँ—बस `Forms2OleControlType` एन्‍उम वैल्यू बदलें।

प्रयोग शुरू करें: कैप्शन बदलें, पोज़िशन एडजस्ट करें, या कई कंट्रोल्स को चेन करें। जितना अधिक आप प्रैक्टिस करेंगे, उतनी ही सहजता से आप C# से रिच, इंटरैक्टिव Word दस्तावेज़ डिलीवर कर पाएँगे। Happy coding!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}