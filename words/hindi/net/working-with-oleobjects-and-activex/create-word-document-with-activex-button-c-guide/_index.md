---
category: general
date: 2026-07-19
description: Aspose.Words C# का उपयोग करके Word दस्तावेज़ बनाएं और सीखें कि कैसे ActiveX
  कमांड बटन जोड़ें, बटन का आकार सेट करें, और प्रोग्रामेटिकली बटन डालें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: hi
lastmod: 2026-07-19
og_description: Aspose.Words C# के साथ Word दस्तावेज़ बनाएं और सेकंडों में एक ActiveX
  कमांड बटन एम्बेड करें। बटन का आकार सेट करने और बटन को आसानी से डालने के लिए चरण‑दर‑चरण
  गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: ActiveX बटन के साथ Word दस्तावेज़ बनाएं – C# ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: ActiveX बटन के साथ Word दस्तावेज़ बनाएं – C# गाइड
url: /hi/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX बटन के साथ Word दस्तावेज़ बनाएं – पूर्ण C# गाइड

क्या आपने कभी सोचा है कि **Word दस्तावेज़** बनाते समय एक कार्यात्मक ActiveX बटन कैसे जोड़ें? शायद आप एक रिपोर्ट को ऑटोमेट कर रहे हैं और फ़ाइल के भीतर एक क्लिक करने योग्य “Approve” कंट्रोल चाहिए। इस ट्यूटोरियल में हम ठीक वही करेंगे—Aspose.Words for .NET का उपयोग करके एक ActiveX कमांड बटन जोड़ेंगे, उसका आकार सेट करेंगे, और उसे जहाँ चाहिए वहाँ डालेंगे।  

यदि आप कभी खुद से *how to add activex* कंट्रोल्स को बिना Word को मैन्युअली खोले जोड़ने के बारे में सोचते रहे हैं, तो आप सही जगह पर हैं। अंत तक आपके पास एक चलाने योग्य उदाहरण, प्रत्येक चरण की स्पष्ट व्याख्या, और सामान्य समस्याओं को संभालने के टिप्स होंगे।

## आप क्या सीखेंगे

- C# प्रोजेक्ट में Aspose.Words को कैसे सेटअप करें  
- **Word दस्तावेज़** बनाने और ActiveX कमांड बटन एम्बेड करने के लिए सटीक कोड  
- **बटन का आकार सेट करने** और उसकी कैप्शन व नाम को कस्टमाइज़ करने के तरीके  
- **कमांड बटन डालने** की सही विधि और दस्तावेज़ में **बटन कैसे डालें** किसी भी स्थान पर  
- एज‑केस विचार (Word संस्करण, प्लेटफ़ॉर्म सीमाएँ, सुरक्षा चेतावनियाँ)

### पूर्वापेक्षाएँ

- .NET 6.0 या बाद का (कोड .NET Framework 4.7+ पर भी काम करता है)।  
- एक वैध Aspose.Words for .NET लाइसेंस (या एक मुफ्त इवैल्यूएशन की)।  
- Visual Studio 2022 (या कोई भी पसंदीदा IDE)।  
- C# और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी समझ।

कोई अन्य थर्ड‑पार्टी लाइब्रेरी आवश्यक नहीं है।

---

## चरण 1: Word दस्तावेज़ बनाएं – प्रोजेक्ट सेटअप

**कमांड बटन डालने** से पहले हमें काम करने के लिए एक खाली Word फ़ाइल चाहिए। यह चरण Aspose.Words का उपयोग करके क्लासिक “create word document” पैटर्न भी दिखाता है।

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **यह क्यों महत्वपूर्ण है:** `Document` पूरे .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` वर्तमान कर्सर स्थिति को ट्रैक करता है। सभी बाद के इंसर्ट (हमारे ActiveX कंट्रोल सहित) इस बिल्डर के सापेक्ष होते हैं।

---

## चरण 2: ActiveX जोड़ें – कमांड बटन कंट्रोल बनाएं

अब दस्तावेज़ मौजूद है, चलिए **how to add activex** भाग को संभालते हैं। Aspose.Words `Forms2OleControl` क्लास को ActiveX ऑब्जेक्ट्स के लिए एक्सपोज़ करता है। यहाँ हम एक कमांड बटन बनाएँगे और उसकी प्रॉपर्टीज़ कॉन्फ़िगर करेंगे, जिसमें **बटन का आकार सेट करना** भी शामिल है।

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **प्रो टिप:** आकार पॉइंट्स में मापा जाता है (1 पॉइंट = 1/72 इंच)। अपने लेआउट के अनुसार मान समायोजित करें; एक सामान्य टूलबार बटन के लिए 120 × 30 अच्छा काम करता है।

---

## चरण 3: कमांड बटन डालें – **Insert Command Button** का मूल

कंट्रोल तैयार है, अब हम **insert command button** को बिल्डर की वर्तमान लोकेशन पर दस्तावेज़ में डालते हैं। आप बिल्डर को कहीं भी (जैसे किसी पैराग्राफ के बाद) ले जा सकते हैं इससे पहले कि आप इस मेथड को कॉल करें।

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

यदि आपको किसी विशिष्ट बुकमार्क पर **how to insert button** चाहिए, तो पहले बिल्डर को वहाँ ले जाएँ:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **पर्दे के पीछे क्या होता है?** Aspose.Words आवश्यक OLE ऑब्जेक्ट स्ट्रीम्स को .docx पैकेज में लिखता है, ताकि Word बटन को बिना किसी अतिरिक्त मैक्रो के रेंडर कर सके।

---

## चरण 4: दस्तावेज़ सहेजें – **Create Word Document** चक्र को समाप्त करना

अंतिम चरण सीधा है: फ़ाइल को डिस्क पर सहेजें। यह **create word document** का राउंड‑ट्रिप पूरा करता है, ActiveX एम्बेड करता है, और सहेजता है।

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

परिणामी फ़ाइल को Microsoft Word (केवल Windows) में खोलें। आपको “Click Me” लेबल वाला एक क्लिक करने योग्य बटन दिखेगा। इसे क्लिक करने पर CommandButton की डिफ़ॉल्ट Action ट्रिगर होगी—जब तक आप VBA कोड नहीं जोड़ते, कुछ नहीं होगा, लेकिन कंट्रोल पूरी तरह कार्यात्मक है।

> **अपेक्षित आउटपुट:** एक .docx फ़ाइल जिसमें एक पृष्ठ, बटन इन्सर्शन पॉइंट पर केंद्रित, आकार 120 × 30 pt, कैप्शन “Click Me” के साथ।  
> ![ActiveX बटन Word दस्तावेज़ में डाला गया है](placeholder-image.png)  
> *Image alt text:* **C# का उपयोग करके Word दस्तावेज़ में डाला गया ActiveX बटन** (matches `og_image_alt`)।

---

## चरण 5: एज केस, सुरक्षा, और सर्वोत्तम प्रथाएँ

### प्लेटफ़ॉर्म सीमाएँ
- ActiveX कंट्रोल्स केवल Windows संस्करण के Word में चलते हैं। यदि आपका ऑडियंस macOS या Word Online उपयोग करता है, तो बटन एक स्थैतिक इमेज के रूप में दिखेगा।
- कुछ कॉरपोरेट वातावरण सुरक्षा कारणों से ActiveX को डिसेबल कर देते हैं; आपको दस्तावेज़ को साइन करना पड़ सकता है या उपयोगकर्ताओं को कंटेंट एनेबल करने के लिए सूचित करना पड़ सकता है।

### VBA इंटरैक्शन (वैकल्पिक)
यदि आप बटन को मैक्रो चलाने देना चाहते हैं, तो सहेजने के बाद दस्तावेज़ में एक VBA प्रोजेक्ट जोड़ना होगा। Aspose.Words स्वचालित रूप से VBA कोड जेनरेट नहीं करता, लेकिन आप `Document.VbaProject` API का उपयोग करके इसे इंजेक्ट कर सकते हैं।

### नाम टकराव
हर कंट्रोल को एक अनूठा `Name` दें। समान नाम दोहराने से Word कंट्रोल को रिज़ॉल्व करने की कोशिश में रन‑टाइम एरर हो सकते हैं।

### प्रदर्शन टिप
जब कई कंट्रोल्स डाल रहे हों, तो एक ही `DocumentBuilder` इंस्टेंस को पुनः उपयोग करें और लूप के अंदर `doc.Save` कॉल करने से बचें। इंसर्ट्स को बैच में करें और अंत में एक बार सहेजें।

---

## पूर्ण कार्यशील उदाहरण

सब कुछ एक साथ मिलाकर, यहाँ एक पूर्ण, कॉपी‑एंड‑पेस्ट‑रेडी प्रोग्राम है:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

प्रोग्राम चलाएँ, सहेजी गई फ़ाइल खोलें, और आपको बिल्डर की पोज़िशन पर बटन बिल्कुल वही दिखेगा।

---

## निष्कर्ष

हमने अभी **Word दस्तावेज़** को शून्य से बनाया, `Forms2OleControl` को कॉन्फ़िगर करके **how to add activex** सीखा, **बटन का आकार सेट करने** की प्रॉपर्टीज़ को समझा, और सही तरीके से **कमांड बटन डालने** तथा **बटन कैसे डालें** किसी भी स्थान पर दिखाया।  

एक ही कोड सैंपल से अब आपके पास इंटरैक्टिव फ़ॉर्म्स वाले टेम्पलेट्स, उपयोगकर्ता स्वीकृति वाले कॉन्ट्रैक्ट्स, या रिपोर्ट में कुछ उपयोगी कंट्रोल्स जोड़ने के लिए मजबूत नींव है।

### आगे क्या सीखें?

- **बटन को स्टाइल करें** – फ़ॉन्ट, रंग बदलें, या इमेज बैकग्राउंड जोड़ें।  
- **VBA मैक्रो अटैच करें** – बटन को कैलकुलेशन या बाहरी प्रोग्राम लॉन्च करने दें।  
- **अन्य कंट्रोल्स के साथ मिलाएँ** – चेकबॉक्स, लिस्ट बॉक्स, या एम्बेडेड Excel शीट्स।  

प्रयोग करने में संकोच न करें, और यदि कोई समस्या आती है तो नीचे टिप्पणी करें। कोडिंग का आनंद लें, और Aspose.Words के साथ Word ऑटोमेशन का मज़ा उठाएँ!

## आगे आप क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकते हैं और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकते हैं।

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}