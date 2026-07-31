---
category: general
date: 2026-07-29
description: Aspose.Words का उपयोग करके वर्ड दस्तावेज़ में कमांड बटन जोड़ें। कुछ आसान
  चरणों में ActiveX नियंत्रण गुण सेट करना और कमांड बटन का कैप्शन सेट करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: hi
lastmod: 2026-07-29
og_description: Aspose.Words के साथ वर्ड दस्तावेज़ में कमांड बटन जोड़ें। यह ट्यूटोरियल
  दिखाता है कि कैसे एक्टिवएक्स कंट्रोल प्रॉपर्टीज़ सेट करें और कमांड बटन का कैप्शन
  जल्दी से सेट करें।
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Word दस्तावेज़ में कमांड बटन जोड़ें – Aspose.Words चरण-दर-चरण
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Aspose.Words के साथ Word दस्तावेज़ में कमांड बटन जोड़ें – पूर्ण गाइड
url: /hi/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में कमांड बटन जोड़ें – पूर्ण प्रोग्रामिंग मार्गदर्शिका

क्या आपको कभी **add command button to word document** जोड़ने की ज़रूरत पड़ी है लेकिन यह नहीं पता था कि कौन से API कॉल्स इस्तेमाल करें? आप अकेले नहीं हैं; कई डेवलपर्स को पहली बार DOCX फ़ाइल में इंटरैक्टिव कंट्रोल एम्बेड करने की कोशिश में यही समस्या आती है। अच्छी ख़बर यह है कि Aspose.Words इसे आश्चर्यजनक रूप से आसान बनाता है। इस गाइड में हम CommandButton ActiveX कंट्रोल बनाना, **set activex control properties** सेट करना, और **set command button caption** सेट करना—सभी साफ़ C# कोड के साथ जो आप अभी कॉपी‑पेस्ट कर सकते हैं—पर चर्चा करेंगे।

इस ट्यूटोरियल के अंत तक आपके पास एक पूरी तरह कार्यशील Word फ़ाइल होगी जिसमें एक क्लिक करने योग्य “Submit” बटन होगा, जिसे Microsoft Word में खोला जा सकता है। कोई बाहरी VBA स्क्रिप्ट नहीं, कोई मैन्युअल UI हस्तक्षेप नहीं—सिर्फ शुद्ध प्रोग्रामेटिक कंट्रोल।

## आप क्या सीखेंगे

* एक खाली Word दस्तावेज़ और एक `DocumentBuilder` कैसे बनाएं।
* Aspose.Words का उपयोग करके **add command button to word document** जोड़ने के लिए सटीक मेथड कॉल।
* आकार, स्थिति और नाम जैसी **set activex control properties** करने के तरीके।
* **set command button caption** करने की सही तकनीक ताकि बटन पर ठीक वही लिखा हो जो आप चाहते हैं।
* विभिन्न बटन प्रकार, DPI स्केलिंग, और Word संस्करण संगतता जैसे किनारे के मामलों को संभालने के टिप्स।

> **Prerequisite:** Visual Studio (या कोई भी C# IDE) जिसमें Aspose.Words for .NET स्थापित हो (NuGet पैकेज `Aspose.Words`)। पहले से ActiveX का कोई अनुभव आवश्यक नहीं है।

---

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेसेस इम्पोर्ट करें

**add command button to word document** जोड़ने से पहले हमें एक C# प्रोजेक्ट चाहिए जो Aspose.Words को रेफ़रेंस करे। एक नया .NET कंसोल ऐप बनाएं, फिर NuGet पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

अब आवश्यक नेमस्पेसेस को अपने सोर्स फ़ाइल में लाएँ:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

ये तीन `using` निर्देश आपको `Document`, `DocumentBuilder`, और `Forms2OleControl` क्लासेज़ तक पहुँच देते हैं जो ActiveX इन्सर्शन को सक्षम बनाते हैं।

*Pro tip:* यदि आप Visual Studio का उपयोग कर रहे हैं, तो IDE क्लास नाम टाइप करने पर इन्हें स्वचालित रूप से जोड़ने का सुझाव देगा।

---

## चरण 2: एक खाली दस्तावेज़ और बिल्डर बनाएं

एक नया `Document` ऑब्जेक्ट एक खाली Word फ़ाइल का प्रतिनिधित्व करता है। `DocumentBuilder` हमारा उपयोगी “पेन” है जो हमें ड्रॉ करने, टेक्स्ट इन्सर्ट करने, और—सबसे महत्वपूर्ण—ActiveX कंट्रोल्स रखने की अनुमति देता है।

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

इस चरण पर दस्तावेज़ सिर्फ एक खाली कैनवास है—जैसे एक साफ़ कागज़ की शीट जो आपके कमांड बटन की प्रतीक्षा कर रही है।

---

## चरण 3: CommandButton ActiveX कंट्रोल इन्सर्ट करें

अब हम अंततः **add command button to word document** जोड़ते हैं। Aspose.Words `InsertForms2OleControl` मेथड प्रदान करता है, जो कंट्रोल प्रकार और आयाम लेता है। हम `Forms2OleControlType.CommandButton` का उपयोग करेंगे और इसे 150 पॉइंट चौड़ाई और 30 पॉइंट ऊँचाई देंगे।

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

यह मेथड एक `Forms2OleControl` इंस्टेंस लौटाता है, जिसका उपयोग हम अगले चरण में **set activex control properties** करने के लिए करेंगे।

---

## चरण 4: कंट्रोल कॉन्फ़िगर करें – नाम, कैप्शन, और पोज़िशन

### कैप्शन सेट करना

कैप्शन वह टेक्स्ट है जो बटन पर दिखता है। **set command button caption** करने के लिए, बस `Caption` प्रॉपर्टी में एक स्ट्रिंग असाइन करें:

```csharp
commandButton.Caption = "Submit";
```

आप `"Submit"` को किसी भी चीज़ में बदल सकते हैं—“Save”, “Export”, “Launch”, आदि—और Word वही टेक्स्ट दिखाएगा।

### कंट्रोल का नाम देना

कंट्रोल को एक सार्थक नाम देना बाद में (जैसे Word मैक्रोज़ ऑटोमेट करते समय) रेफ़रेंस करना आसान बनाता है। हम `Name` प्रॉपर्टी सेट करेंगे:

```csharp
commandButton.Name = "btnSubmit";
```

### पेज पर पोज़िशनिंग

Word लेआउट के लिए पॉइंट्स (इंच का 1/72) का उपयोग करता है। बटन को जहाँ चाहिए वहाँ रखने के लिए `Left` और `Top` प्रॉपर्टीज़ को समायोजित करें:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

यदि आपको बटन को किसी पैराग्राफ़ के सापेक्ष संरेखित करना है, तो पहले बिल्डर का कर्सर ले जाएँ, फिर कंट्रोल इन्सर्ट करें; कोऑर्डिनेट्स उस स्थान के सापेक्ष होंगे।

*Edge case:* हाई‑DPI मॉनीटर पर विज़ुअल साइज Word में थोड़ा अलग दिख सकता है। डिवाइसों में बटन का फिजिकल साइज स्थिर रखने के लिए आप टार्गेट DPI (आमतौर पर Word के लिए 96 DPI) के आधार पर पॉइंट्स की गणना कर सकते हैं।

---

## चरण 5: दस्तावेज़ को सेव करें

बटन पूरी तरह कॉन्फ़िगर हो जाने के बाद फ़ाइल को सेव करना एक‑लाइनर है:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

परिणामी `CommandButton.docx` में एक पूरी तरह कार्यशील ActiveX बटन होगा। इसे Microsoft Word में खोलें, और आपको वह “Submit” बटन ठीक उसी स्थान पर दिखेगा जहाँ आपने रखा था।

### अपेक्षित परिणाम

1. Word दस्तावेज़ एक पेज के साथ खुलता है।
2. एक आयताकार बटन जिसका लेबल **Submit** है, निर्दिष्ट कोऑर्डिनेट्स पर दिखाई देता है।
3. यदि आप बटन पर राइट‑क्लिक करके **Properties** चुनते हैं, तो आपको `btnSubmit` नाम और अन्य सेट की गई प्रॉपर्टीज़ दिखेंगी।

---

## चरण 6: उन्नत वैरिएशन और सामान्य pitfalls

### अन्य ActiveX प्रकार इन्सर्ट करना

`InsertForms2OleControl` मेथड केवल कमांड बटन तक सीमित नहीं है। आप चेक बॉक्स, ऑप्शन बटन, या कस्टम ActiveX ऑब्जेक्ट्स भी एम्बेड कर सकते हैं:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

उसी **set activex control properties** पैटर्न को लागू करें—सिर्फ टाइप एन्नुम को बदलें।

### Word संस्करणों को संभालना

पुराने Word संस्करण (pre‑2007) बाइनरी `.doc` फ़ॉर्मेट का उपयोग करते हैं, जहाँ ActiveX कंट्रोल्स अलग तरीके से स्टोर होते हैं। Aspose.Words `.doc` के रूप में सेव करते समय कंट्रोल को ऑटोमैटिकली कन्वर्ट कर देता है, लेकिन कुछ प्रॉपर्टीज़ (जैसे सटीक पोज़िशनिंग) शिफ्ट हो सकती हैं। यदि आप लेगेसी फ़ॉर्मेट टार्गेट कर रहे हैं, तो विशेष Word संस्करण में आउटपुट का परीक्षण करें।

### सुरक्षा सेटिंग्स

Word उन मशीनों पर जहाँ मैक्रो सुरक्षा कड़ी है, ActiveX कंट्रोल्स को डिसेबल कर सकता है। “Security Warning” डायलॉग से बचने के लिए विचार करें:

* दस्तावेज़ को भरोसेमंद सर्टिफ़िकेट से साइन करें।
* उपयोगकर्ताओं को उस फ़ाइल लोकेशन के लिए ActiveX कंटेंट एनेबल करने के निर्देश दें।
* यदि सुरक्षा चिंता है तो मैक्रो‑फ्री विकल्प (जैसे प्लेन कंटेंट कंट्रोल्स) का उपयोग करें।

---

## चरण 7: पूर्ण कार्यशील उदाहरण

नीचे पूरा, तैयार‑चलाने‑योग्य प्रोग्राम है जिसमें हमने चर्चा किए सभी चरण शामिल हैं। इसे अपने `Program.cs` में कॉपी करें, आउटपुट पाथ आवश्यकतानुसार बदलें, और **Run** दबाएँ।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**यह कोड क्या करता है:**

* एक नई दस्तावेज़ से शुरू करता है।
* एक कमांड बटन इन्सर्ट करता है, **set activex control properties** सेट करता है, और **set command button caption** सेट करता है।
* एक संक्षिप्त व्याख्यात्मक पैराग्राफ जोड़ता है।
* फ़ाइल को `CommandButton.docx` के रूप में सेव करता है।

प्रोग्राम चलाएँ, जेनरेटेड फ़ाइल खोलें, और आप बटन को व्याख्यात्मक टेक्स्ट के नीचे स्थित देखेंगे।

---

## निष्कर्ष

हमने दिखाया कि कैसे Aspose.Words का उपयोग करके **add command button to word document** किया जाता है, कैसे **set activex control properties** सेट किए जाते हैं, और कैसे **set command button caption** सेट किया जाता है—सभी एक संक्षिप्त, प्रोडक्शन‑रेडी C# स्निपेट में। यह तरीका स्केलेबल है: कंट्रोल टाइप बदलें, डाइमेंशन समायोजित करें, या डेटा सोर्स पर लूप करके स्वचालित रूप से दर्जनों बटन एम्बेड करें।

आगे बढ़ना चाहते हैं? कोशिश करें:

* बटन को ऐसे मैक्रो से बाइंड करें जो डेटा एक्सपोर्ट ट्रिगर करे।
* `Picture` प्रॉपर्टी का उपयोग करके बटन के अंदर इमेज या कस्टम आइकन जोड़ें।
* कई ActiveX कंट्रोल्स (टेक्स्ट बॉक्स, कॉम्बो बॉक्स आदि) के साथ पूर्ण फ़ॉर्म बनाएं।

प्रयोग ही Word ऑटोमेशन में महारत हासिल करने का सबसे अच्छा तरीका है। यदि आप किसी समस्या में फँसते हैं, तो DPI गणनाओं और Word सुरक्षा सेटिंग्स को दोबारा चेक करें। कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा अधिक इंटरैक्टिव रहें!

## आप आगे क्या सीख सकते हैं?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}