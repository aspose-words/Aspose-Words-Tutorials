---
category: general
date: 2026-10-07
description: Aspose.Words C# के साथ Word दस्तावेज़ में OLE कमांड बटन कैसे डालें, सीखें।
  DocumentBuilder, प्रॉपर्टीज़ और फ़ाइल को सहेजने को कवर करने वाली चरण‑दर‑चरण गाइड।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: hi
lastmod: 2026-10-07
og_description: C# का उपयोग करके Word दस्तावेज़ में OLE कमांड बटन डालें। इस संक्षिप्त
  ट्यूटोरियल का पालन करके Aspose.Words के साथ एक कार्यात्मक CommandButton जोड़ें,
  कॉन्फ़िगर करें और सहेजें।
og_image_alt: Insert OLE command button example in Word document
og_title: C# के साथ Word में OLE कमांड बटन डालें – पूर्ण Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: C# का उपयोग करके Word दस्तावेज़ में OLE कमांड बटन कैसे डालें
url: /hi/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# का उपयोग करके Word दस्तावेज़ में OLE command button कैसे डालें

यदि आपको प्रोग्रामेटिक रूप से Word फ़ाइल में **insert OLE command button** डालना है, तो यह गाइड आपको Aspose.Words for .NET के साथ यह कैसे करना है, बिल्कुल दिखाता है। चाहे आप फ़ॉर्म‑भरा रिपोर्ट बना रहे हों या ऐसे टेम्प्लेट को ऑटोमेट कर रहे हों जिसमें उपयोगकर्ता इंटरैक्शन की आवश्यकता हो, नीचे दिए गए चरण आपको एक पूर्ण, चलाने योग्य समाधान प्रदान करते हैं।

आप सीखेंगे कि कैसे एक खाली दस्तावेज़ बनाएं, `DocumentBuilder` का उपयोग करके `Forms2OleControl` रखें, बटन का कैप्शन और नाम सेट करें, और अंत में `.docx` को सहेजें। Aspose.Words लाइब्रेरी के अलावा कोई बाहरी टूल आवश्यक नहीं है।

## आवश्यकताएँ

* .NET 6.0 या बाद का (कोड .NET Framework 4.7+ के साथ भी काम करता है)  
* एक वैध Aspose.Words for .NET लाइसेंस या मुफ्त इवैल्यूएशन कुंजी  
* Visual Studio 2022 (या कोई भी C# IDE जो आप पसंद करें)  
* C# सिंटैक्स और Word OLE अवधारणाओं की बुनियादी परिचितता  

> **Pro tip:** यदि आप मुफ्त इवैल्यूएशन का उपयोग कर रहे हैं, तो उत्पन्न दस्तावेज़ में एक छोटा वॉटरमार्क होगा। लाइसेंस प्राप्त संस्करण इसे स्वचालित रूप से हटा देता है।

## चरण 1: Aspose.Words स्थापित करें

NuGet के माध्यम से अपने प्रोजेक्ट में Aspose.Words पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

इस पैकेज में OLE कंट्रोल्स के लिए आवश्यक `Aspose.Words.Drawing` और `Aspose.Words.Drawing.Ole` नेमस्पेस शामिल हैं।

## चरण 2: DocumentBuilder के साथ OLE command button डालें

ट्यूटोरियल का मुख्य भाग `InsertForms2OleControl` मेथड है। यह एक विशिष्ट स्थान और आकार पर **Forms2 OLE CommandButton** बनाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### क्यों यह काम करता है

* `DocumentBuilder` प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने के लिए मुख्य API है।  
* `InsertForms2OleControl` Aspose.Words को एक **Forms2 OLE control** एम्बेड करने के लिए कहता है, जो लेगेसी Word फ़ॉर्म तकनीक है जो कमांड बटन, चेक बॉक्स आदि का समर्थन करती है।  
* `OleControlType.CommandButton` enum मान यह निर्दिष्ट करता है कि डाला गया कंट्रोल एक **command button** है—वही प्रकार जिसे आपने **insert OLE command button** करने के लिए माँगा था।  
* `Rectangle` दृश्य स्थान निर्धारित करता है। अपने लेआउट के अनुसार X/Y निर्देशांक या चौड़ाई/ऊँचाई को समायोजित करें।

## चरण 3: दस्तावेज़ सहेजें

बटन को कॉन्फ़िगर करने के बाद, दस्तावेज़ को डिस्क पर लिखें। आप Aspose.Words द्वारा समर्थित कोई भी फ़ॉर्मेट चुन सकते हैं (`.docx`, `.pdf`, `.odt`, …)। इस ट्यूटोरियल के लिए हम इसे Word दस्तावेज़ के रूप में सहेजेंगे।

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

जब आप Microsoft Word में `CommandButton.docx` खोलेंगे, तो आपको **Click Me** लेबल वाला एक क्लिक करने योग्य बटन दिखाई देगा। Word में इसे दबाने से डिफ़ॉल्ट “Run Macro” डायलॉग खुलता है क्योंकि बटन एक OLE फ़ॉर्म कंट्रोल है; आप बाद में आवश्यकता अनुसार एक मैक्रो या VBA कोड संलग्न कर सकते हैं।

## चरण 4: परिणाम सत्यापित करें (अपेक्षित आउटपुट)

जनरेटेड फ़ाइल खोलें:

1. बटन आपके द्वारा निर्दिष्ट निर्देशांक पर दिखाई देता है (पृष्ठ के बाएँ और ऊपर से लगभग 1.4 इंच)।  
2. कैप्शन **Click Me** पढ़ता है।  
3. नाम प्रॉपर्टी (`cmdSubmit`) Word के **Developer → Properties** पैन में दिखाई देती है, जो VBA से कंट्रोल को रेफ़र करने पर उपयोगी होती है।  

![Word दस्तावेज़ में Insert OLE command button उदाहरण](insert-ole-button.png)

*Image alt text*: **Word दस्तावेज़ में Insert OLE command button उदाहरण** (पहुँचयोग्यता और SEO के लिए प्राथमिक कीवर्ड शामिल है)।

## किनारे के मामलों और सामान्य प्रश्न

### 1. यदि बटन वह स्थान नहीं दिखाता जहाँ मैं अपेक्षा करता हूँ तो क्या करें?

* Word पिक्सेल के बजाय पॉइंट्स का उपयोग करता है। स्क्रीन पिक्सेल को पॉइंट्स में बदलें (`points = pixels * 72 / DPI`)।  
* सुनिश्चित करें कि Rectangle पेज मार्जिन से नहीं टकराता; अन्यथा Word कंट्रोल को शिफ्ट कर सकता है।

### 2. क्या मैं बटन को मौजूदा दस्तावेज़ में डाल सकता हूँ?

हां। `new Document("Existing.docx")` से दस्तावेज़ लोड करें और वही `DocumentBuilder` वर्कफ़्लो उपयोग करें। बस `InsertForms2OleControl` कॉल करने से पहले बिल्डर का कर्सर स्थानांतरित करना याद रखें (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, आदि)।

### 3. बटन से मैक्रो कैसे संलग्न करें?

Aspose.Words VBA कोड नहीं बनाता, लेकिन आप दस्तावेज़ जनरेट होने के बाद एक मैक्रो एम्बेड कर सकते हैं:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. क्या यह .NET Core पर Linux के साथ काम करता है?

OLE कंट्रोल एक Windows‑विशिष्ट फीचर है क्योंकि यह COM पर निर्भर करता है। Linux पर बटन डाला जाएगा, लेकिन यह इंटरैक्टिव व्यवहार के बिना एक स्थैतिक चित्र के रूप में दिखेगा। क्रॉस‑प्लेटफ़ॉर्म इंटरैक्टिव फ़ॉर्म्स के लिए, कंटेंट कंट्रोल्स (`StructuredDocumentTag`) का उपयोग करने पर विचार करें।

### 5. यदि मुझे अलग आकार या कई बटन चाहिए तो क्या करें?

अतिरिक्त `Rectangle` ऑब्जेक्ट्स को अद्वितीय निर्देशांक के साथ बनाएं और `InsertForms2OleControl` कॉल को दोहराएं। प्रत्येक बटन का अपना `Caption` और `Name` हो सकता है।

## पूर्ण कार्यशील उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉन्सोल एप्लिकेशन में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी आवश्यक `using` निर्देश, त्रुटि संभालना, और टिप्पणी शामिल हैं।

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

प्रोग्राम चलाएँ, जनरेटेड `CommandButton.docx` खोलें, और आपको **Click Me** बटन दिखाई देगा जो आगे की कस्टमाइज़ेशन के लिए तैयार है।

## निष्कर्ष

अब आप जानते हैं कि C# और Aspose.Words का उपयोग करके Word दस्तावेज़ में **insert OLE command button** कैसे डालें। ट्यूटोरियल ने निम्नलिखित को कवर किया:

* Aspose.Words पैकेज स्थापित करना  
* `OleControlType.CommandButton` के साथ `DocumentBuilder.InsertForms2OleControl` का उपयोग  
* बटन प्रॉपर्टीज़ सेट करना (`Caption`, `Name`)  
* आउटपुट को सहेजना और सत्यापित करना  

यहां से आप चेक बॉक्स, कॉम्बो बॉक्स, या पूरे Excel वर्कशीट एम्बेड करने के लिए **Aspose.Words OLE control** जैसे संबंधित विषयों का अन्वेषण कर सकते हैं। आप बड़े टेम्प्लेट्स में **Word OLE command button** ऑटोमेशन का प्रयोग भी कर सकते हैं, या बेहतर क्रॉस‑प्लेटफ़ॉर्म समर्थन के लिए OLE कंट्रोल्स को आधुनिक **content controls** से बदल सकते हैं।

बिना संकोच rectangle मानों को अनुकूलित करें, कई बटन जोड़ें, या अपनी एप्लिकेशन की जरूरतों के अनुसार VBA मैक्रो संलग्न करें। कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स इस गाइड में प्रदर्शित तकनीकों पर आधारित निकट संबंधित विषयों को कवर करते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में माहिर बनने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [Word दस्तावेज़ में Ole ऑब्जेक्ट डालें](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Word दस्तावेज़ में Ole ऑब्जेक्ट को आइकन के रूप में डालें](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Ole पैकेज के साथ Word में Ole ऑब्जेक्ट डालें](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}