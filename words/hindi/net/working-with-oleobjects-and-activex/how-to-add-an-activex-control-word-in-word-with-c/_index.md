---
category: general
date: 2026-09-30
description: C# का उपयोग करके Word दस्तावेज़ में एक ActiveX कंट्रोल शब्द जोड़ें। जानें
  कि ActiveX बटन कैसे डालें, कमांड बटन कैसे जोड़ें, और उसे क्लिक करने योग्य बनाएं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: hi
lastmod: 2026-09-30
og_description: C# के साथ Word दस्तावेज़ में एक ActiveX नियंत्रण शब्द जोड़ें। इस पूर्ण
  गाइड का पालन करके ActiveX बटन डालें, एक कमांड बटन जोड़ें, और इसे क्लिक करने योग्य
  बनाएं।
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Word दस्तावेज़ों में ActiveX नियंत्रण शब्द जोड़ें – चरण‑दर‑चरण C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: C# का उपयोग करके Word में ActiveX कंट्रोल शब्द कैसे जोड़ें
url: /hi/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word में ActiveX कंट्रोल शब्द कैसे जोड़ें

यदि आपको Microsoft Word फ़ाइल के भीतर एक **ActiveX control word** एम्बेड करने की आवश्यकता है, तो यह गाइड आपको बिल्कुल बताता है कि इसे कैसे किया जाए। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो एक क्लिक करने योग्य बटन डालता है, दस्तावेज़ को सहेजता है, और नवीनतम Aspose.Words for .NET के साथ काम करता है।

ActiveX कंट्रोल शब्द जोड़ने से आप इंटरैक्टिव फ़ॉर्म, कस्टम डायलॉग या सरल UI तत्व बना सकते हैं जो मूल Word कंट्रोल की तरह व्यवहार करते हैं। चाहे आप उपयोगकर्ता इंटरैक्शन की आवश्यकता वाले अनुबंध टेम्पलेट बना रहे हों या रिपोर्ट में “Run” बटन चाहिए, नीचे दिए गए चरण सभी आवश्यक चीज़ें कवर करते हैं।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

* .NET 6.0 SDK या बाद का संस्करण (कोड .NET Framework 4.8 के साथ भी काम करता है)
* Visual Studio 2022 (या कोई भी IDE जो C# को सपोर्ट करता हो)
* Aspose.Words for .NET स्थापित (`dotnet add package Aspose.Words`)
* C# और Word दस्तावेज़ संरचना की बुनियादी समझ

> **Pro tip:** `InsertForms2OleControl` मेथड केवल लेगेसी “Forms 2.0” कंट्रोल्स के साथ काम करता है, जो Word फ़ॉर्म फ़ील्ड्स के लिए उपयोग किए जाने वाले ActiveX कंट्रोल्स हैं। यदि आप नए Office संस्करणों को टार्गेट कर रहे हैं, तो भी कंट्रोल डेस्कटॉप क्लाइंट में सही ढंग से रेंडर होगा।

## Step 1: Set up the project and import namespaces

एक नया कंसोल प्रोजेक्ट बनाएं और आवश्यक `using` स्टेटमेंट्स जोड़ें। इससे कंपाइलर `Document`, `DocumentBuilder`, और `OleControlType` क्लासेज़ को ढूँढ़ सकेगा।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

`Aspose.Words` नेमस्पेस Word प्रोसेसिंग के लिए हाई‑लेवल API प्रदान करता है, जबकि `Aspose.Words.Drawing` में `OleControlType` एनेमरेशन होता है जो ActiveX कंट्रोल के प्रकार को निर्दिष्ट करने के लिए आवश्यक है।

## Step 2: Load the source Word document

आपको उस Word फ़ाइल से शुरू करना होगा जिसे आप संशोधित करना चाहते हैं। नीचे दिया गया कोड `input.docx` को उस फ़ोल्डर से लोड करता है जिसे आप निर्दिष्ट करते हैं।

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

यदि फ़ाइल मौजूद नहीं है, तो Aspose.Words `FileNotFoundException` फेंकेगा। यदि आपको सुगम त्रुटि हैंडलिंग चाहिए तो कॉल को `try/catch` ब्लॉक में रैप करें।

## Step 3: Create a DocumentBuilder to edit the document

`DocumentBuilder` टेक्स्ट, इमेज और कंट्रोल्स डालने का मुख्य साधन है। यह एक कर्सर बनाए रखता है जो अगले एलिमेंट के स्थान को दर्शाता है।

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

डिफ़ॉल्ट रूप से, बिल्डर का कर्सर पहले सेक्शन की शुरुआत में स्थित होता है। आप इसे `MoveToDocumentEnd()` या `MoveToParagraph(index)` जैसी मेथड्स से कहीं और ले जा सकते हैं।

## Step 4: Insert an ActiveX CommandButton control

अब ट्यूटोरियल का मुख्य भाग: **ActiveX कंट्रोल शब्द** को क्लिक करने योग्य बटन के रूप में डालना। `InsertForms2OleControl` मेथड दो आर्ग्यूमेंट लेता है—कंट्रोल का प्रकार और कंट्रोल के लिए कैप्शन (या नाम)।

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **`OleControlType.CommandButton` क्यों उपयोग करें?**  
  यह Word को क्लासिक Forms 2.0 कमांड बटन बनाने के लिए बताता है, जो कैप्शन दिखाता है और बाद में मैक्रो या VBA स्क्रिप्ट से जोड़ा जा सकता है।

* **कैप्शन क्या करता है?**  
  स्ट्रिंग `"ClickMe"` बटन का दृश्यमान टेक्स्ट बन जाता है। आप इसे अपनी UI के अनुसार किसी भी चीज़ में बदल सकते हैं।

### Inserting the button at a specific location

यदि आपको बटन किसी विशेष पैराग्राफ के बाद चाहिए, तो पहले बिल्डर को मूव करें:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Step 5: Save the modified document

कंट्रोल डालने के बाद, बदलावों को नई फ़ाइल (या मूल फ़ाइल को ओवरराइट) में सहेजें।

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

जब आप `output.docx` को डेस्कटॉप संस्करण के Word में खोलेंगे, तो आपको **ClickMe** (या आपके द्वारा उपयोग किए गए कैप्शन के अनुसार **Submit**) लेबल वाला बटन दिखाई देगा। डिज़ाइन मोड में बटन पर क्लिक करने से डिफ़ॉल्ट रूप से कुछ नहीं होता; आप बाद में Word के “Developer” टैब से मैक्रो असाइन कर सकते हैं।

## Full, runnable example

नीचे एक स्वतंत्र प्रोग्राम दिया गया है जो पूरे वर्कफ़्लो को दर्शाता है। इसे नए कंसोल ऐप के `Program.cs` में कॉपी करें और चलाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Expected output

* कंसोल सफल संदेश के साथ आउटपुट पाथ प्रिंट करेगा।
* `output.docx` खोलने पर बिल्डर द्वारा डाले गए स्थान पर **ClickMe** बटन दिखेगा।
* बटन को चयनित, आकार बदल सकते हैं, या Word के **Developer → Design Mode** के माध्यम से मैक्रो असाइन कर सकते हैं।

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| **हेडर/फ़ूटर में ActiveX बटन कैसे डालें?** | `InsertForms2OleControl` कॉल करने से पहले `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` के साथ बिल्डर को हेडर/फ़ूटर पर ले जाएँ। |
| **अगर बटन की जगह चेकबॉक्स चाहिए तो?** | `OleControlType.CheckBox` उपयोग करें और `"Agree"` जैसा कैप्शन दें। |
| **क्या बटन Word Online में काम करेगा?** | नहीं। Word Online लेगेसी Forms 2.0 ActiveX कंट्रोल्स को सपोर्ट नहीं करता। बटन केवल डेस्कटॉप क्लाइंट में रेंडर होता है। |
| **क्या बटन का आकार प्रोग्रामेटिकली सेट कर सकते हैं?** | डालने के बाद `builder.CurrentParagraph.Runs[0].GetShape()` से `Shape` ऑब्जेक्ट प्राप्त करें और `Width`/`Height` को समायोजित करें। |
| **कोड से मैक्रो असाइन करने का कोई तरीका है?** | Aspose.Words मैक्रो एडिटिंग को एक्सपोज़ नहीं करता। आपको दस्तावेज़ को Word में खोलकर मैन्युअली मैक्रो जोड़ना होगा या Office Interop API का उपयोग करना होगा। |

## Tips for production use

* **हार्ड‑कोडेड पाथ से बचें** – `Path.Combine` और कॉन्फ़िगरेशन फ़ाइलों का उपयोग करें।
* **`Document` को डिस्पोज़ करें** – बड़े फ़ाइलों के साथ काम करते समय मेमोरी को तुरंत मुक्त करने के लिए इसे `using` स्टेटमेंट में रखें।
* **आउटपुट वैलिडेट करें** – प्रोग्रामेटिकली जांचें कि दस्तावेज़ में `OleControl` प्रकार का शैप मौजूद है या नहीं, `doc.GetChildNodes(NodeType.Shape, true)` को इटररेट करके।
* **सुरक्षा नोट** – ActiveX कंट्रोल क्लाइंट मशीन पर कोड चला सकते हैं। केवल भरोसेमंद उपयोगकर्ताओं को ही दस्तावेज़ वितरित करें और डिजिटल सिग्नेचर पर विचार करें।

## Conclusion

आप अब जानते हैं कि C# का उपयोग करके Word दस्तावेज़ में **ActiveX control word** कैसे जोड़ें। दस्तावेज़ लोड करके, `DocumentBuilder` बनाकर, `InsertForms2OleControl` से कमांड बटन डालकर, और फ़ाइल सहेजकर आप इंटरैक्टिव Word फ़ॉर्म्स को ऑटोमेट कर सकते हैं। अन्य `OleControlType` मानों के साथ प्रयोग करें, कंट्रोल्स को हेडर या टेबल में रखें, और मैक्रो के साथ मिलाकर अधिक समृद्ध उपयोगकर्ता अनुभव बनाएं।

---

*अगले कदम*: अन्य प्रकार के **ActiveX कंट्रोल** कैसे डालें, VBA के माध्यम से **कमांड बटन** इवेंट हैंडलर कैसे जोड़ें, और क्रॉस‑प्लेटफ़ॉर्म संगतता के लिए **ActiveX बटन डालने** की सर्वोत्तम प्रैक्टिसेज़ पढ़ें।

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}