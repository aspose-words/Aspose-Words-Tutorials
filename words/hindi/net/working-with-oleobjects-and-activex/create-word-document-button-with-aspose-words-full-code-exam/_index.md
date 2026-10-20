---
category: general
date: 2026-07-23
description: Aspose.Words का उपयोग करके वर्ड दस्तावेज़ बटन बनाएं – .docx फ़ाइल में
  ActiveX CommandButton डालने के लिए चरण‑दर‑चरण मार्गदर्शिका।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: hi
lastmod: 2026-07-23
og_description: 'Aspose.Words के साथ वर्ड दस्तावेज़ बटन बनाएं: मिनटों में वर्ड फ़ाइल
  में एक ActiveX CommandButton को एम्बेड करना सीखें।'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: वर्ड दस्तावेज़ बनाने का बटन – Aspose.Words पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Aspose.Words के साथ वर्ड दस्तावेज़ बनाने का बटन – पूर्ण कोड उदाहरण
url: /hi/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ Word दस्तावेज़ बटन बनाना – पूर्ण प्रोग्रामिंग गाइड

क्या आपको **Word दस्तावेज़ बटन बनाना** की ज़रूरत रही है लेकिन सही API नहीं मिल पाई? आप अकेले नहीं हैं—ज्यादातर डेवलपर्स को .docx फ़ाइल में इंटरैक्टिव कंट्रोल एम्बेड करने पर दिक्कत आती है। अच्छी खबर? Aspose.Words for .NET की मदद से आप कुछ ही लाइनों के कोड से Word दस्तावेज़ में पूरी तरह कार्यशील ActiveX CommandButton डाल सकते हैं।

इस ट्यूटोरियल में हम पूरी प्रक्रिया को चरण‑दर‑चरण देखेंगे: प्रोजेक्ट सेट‑अप, `DocumentBuilder` का इनिशियलाइज़ेशन, `InsertForms2OleControl` से बटन इन्सर्ट करना, और अंत में फ़ाइल को ऐसे सेव करना कि Word कंट्रोल को पहचान ले। अंत तक आपके पास एक तैयार‑to‑use Word फ़ाइल होगी जिसमें क्लिक करने योग्य बटन होगा—बिना किसी COM इंटरऑप जिम्नास्टिक के।

## आपको क्या चाहिए

शुरू करने से पहले सुनिश्चित करें कि आपके पास ये प्री‑रिक्विज़िट्स हैं:

- **.NET 6.0** या उसके बाद का संस्करण (कोड .NET Framework 4.6+ के साथ भी काम करता है)।  
- **Aspose.Words for .NET** NuGet पैकेज (वर्ज़न 23.9 या नया)।  
- C# की बुनियादी समझ (हम सिंटैक्स को शुरुआती‑फ़्रेंडली रखेंगे)।  
- Visual Studio 2022 या आपका पसंदीदा कोई भी IDE।

बस इतना ही—कोई अतिरिक्त COM रेफ़रेंस नहीं, कोई Office इंटरऑप नहीं, सिर्फ़ शुद्ध मैनेज्ड कोड।

---

## चरण 1: Aspose.Words को **Word दस्तावेज़ बटन बनाने** के लिए सेट‑अप करें

सबसे पहले, अपने प्रोजेक्ट में Aspose.Words पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

या, यदि आप Visual Studio NuGet UI इस्तेमाल कर रहे हैं, तो “Aspose.Words” सर्च करें और **Install** पर क्लिक करें। यह एक लाइन आपको `Document`, `DocumentBuilder`, और `InsertForms2OleControl` मेथड तक पहुंच देती है, जिसकी हमें आगे ज़रूरत पड़ेगी।

> **Pro tip:** अपने NuGet पैकेज हमेशा अपडेट रखें; नए रिलीज़ अक्सर ActiveX हैंडलिंग के बग फ़िक्स़ लेकर आते हैं।

---

## चरण 2: **DocumentBuilder** को **ActiveX CommandButton** के लिए इनिशियलाइज़ करें

अब हम एक नया Word दस्तावेज़ बनाते हैं और `DocumentBuilder` को स्पिन‑अप करते हैं। `DocumentBuilder` को आप कैनवास पर कंटेंट ड्रॉ करने वाले पेंटब्रश की तरह समझ सकते हैं।

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

ध्यान दें कि हमने `System.Drawing` इम्पोर्ट किया है—`Rectangle` स्ट्रक्चर बटन की लोकेशन और साइज निर्धारित करता है। यही वह जगह है जहाँ **ActiveX CommandButton** रहेगा।

---

## चरण 3: **InsertForms2OleControl** से **CommandButton** जोड़ें

ट्यूटोरियल का मुख्य भाग: बटन को इन्सर्ट करना। `InsertForms2OleControl` मेथड तीन आर्ग्यूमेंट लेता है—कंट्रोल टाइप, एक `Rectangle`, और वैकल्पिक नाम। हम `OleControlType.CommandButton` का उपयोग करके वही कंट्रोल निर्दिष्ट करेंगे जिसे हम चाहते हैं।

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

यह एक कॉल बहुत कुछ करती है:

1. **Creates** एक OLE ऑब्जेक्ट Word फ़ाइल के अंदर।  
2. **Registers** इसे ActiveX CommandButton के रूप में, जिसे Word एक क्लिक‑योग्य UI एलिमेंट के रूप में रेंडर करेगा।  
3. **Positions** इसे उस rectangle के अनुसार जहाँ हमने इसे दिया है।

यदि आपको बटन का कैप्शन या अन्य प्रॉपर्टीज़ बदलनी हैं, तो इन्सर्शन के बाद `OleFormat` तक पहुंच कर कर सकते हैं। अधिकांश मामलों में डिफ़ॉल्ट कैप्शन (“CommandButton1”) पर्याप्त रहता है।

---

## चरण 4: **CommandButton** वाला Word दस्तावेज़ सेव करें

सेव करना बहुत आसान है—सिर्फ़ उस फ़ोल्डर का पाथ दें जहाँ आपके पास लिखने की अनुमति है। फ़ाइल एक्सटेंशन `.docx` होना चाहिए ताकि बटन राउंड‑ट्रिप में बना रहे।

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

जब आप `CommandButton.docx` को Microsoft Word में खोलेंगे, तो आपको पहले पेज के टॉप‑लेफ़्ट कॉर्नर पर एक छोटा बटन दिखेगा। डिफ़ॉल्ट रूप से क्लिक करने पर कुछ नहीं होता (उसके लिए VBA चाहिए), लेकिन कंट्रोल पूरी तरह कार्यशील है और बाद में कनेक्ट किया जा सकता है।

> **Why this works:** Aspose.Words OLE स्ट्रीम को सीधे DOCX पैकेज में लिखता है, जिससे Word को रन‑टाइम पर कंट्रोल जेनरेट करने की ज़रूरत नहीं पड़ती। इस कारण बटन ठीक उसी जगह पर दिखता है जहाँ आपने रखा था।

---

## चरण 5: Word में बटन की जाँच करें

जनरेटेड फ़ाइल खोलें:

1. Microsoft Word लॉन्च करें।  
2. **File → Open** पर जाएँ और `CommandButton.docx` चुनें।  
3. आपको “CommandButton1” लेबल वाला एक आयताकार बटन दिखना चाहिए।  

यदि बटन नहीं दिख रहा है, तो **Design Mode** को एनेबल करें (Developer → Design Mode)। यह ActiveX कंट्रोल की विज़ुअल रिप्रेज़ेंटेशन को टॉगल करता है।

---

## चरण 6: उन्नत विकल्प – **ActiveX CommandButton** को कस्टमाइज़ करें

नीचे कुछ त्वरित ट्यून‑अप दिए गए हैं जो आपके काम आ सकते हैं:

| लक्ष्य | कोड स्निपेट |
|------|--------------|
| कैप्शन बदलें | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| मैक्रो नाम सेट करें (Word मैक्रो सपोर्ट आवश्यक) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| इन्सर्शन के बाद साइज बदलें | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

ये स्निपेट्स `InsertForms2OleControl` की लचीलापन दर्शाते हैं। आप `OleControlType` एन्नुम को बदलकर `CheckBox` या `ListBox` जैसे अन्य ActiveX कंट्रोल भी एम्बेड कर सकते हैं।

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा, कॉपी‑पेस्ट‑रेडी प्रोग्राम है जो **शुरू से Word दस्तावेज़ बटन बनाता** है:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**प्रोग्राम चलाने पर अपेक्षित आउटपुट:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

परिणामस्वरूप फ़ाइल खोलें और आप बटन को ठीक उसी जगह देखेंगे जहाँ कोड ने रखा था।

---

## सामान्य गलतियाँ और उनका समाधान

- **`System.Drawing` रेफ़रेंस मिसिंग** – `Rectangle` स्ट्रक्चर वहीं रहता है; बिना इस रेफ़रेंस के कंपाइलर एरर देगा।  
- **पुराना Aspose.Words वर्ज़न** – शुरुआती रिलीज़ में `InsertForms2OleControl` पूरी तरह सपोर्ट नहीं करता था। नवीनतम स्थिर पैकेज पर अपग्रेड करें।  
- **`.doc` के बजाय `.docx` में सेव करना** – पुराने बाइनरी फ़ॉर्मेट में OLE स्ट्रीम हट जाता है, जिससे बटन गायब हो जाता है।  
- **हेडलेस सर्वर पर Word न इंस्टॉल होना** – बटन फ़ाइल में रहेगा, लेकिन आप बिना Word के प्रीव्यू नहीं देख पाएँगे। यह ऑटोमेटेड जेनरेशन पाइपलाइन के लिए ठीक है।

---

## अगले कदम – **Word दस्तावेज़ बटन बनाने** वर्कफ़्लो को विस्तारित करें

अब जब आप बेसिक समझ गए हैं, तो इन उन्नत विचारों पर विचार करें:

- बटन से **VBA मैक्रो** अटैच करें ताकि कस्टम बिज़नेस लॉजिक चल सके।  
- लूप में **कई बटन** जेनरेट करें ताकि डायनामिक फ़ॉर्म बन सकें।  
- **Aspose.PDF** के साथ मिलाकर वही दस्तावेज़ PDF में एक्सपोर्ट करें; बटन PDF में स्थिर इमेज बन जाएगा।  
- **


## आगे आप क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स संबंधित विषयों को कवर करते हैं और इस गाइड में दिखाए गए तकनीकों को आगे बढ़ाते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर्स को मास्टर कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}