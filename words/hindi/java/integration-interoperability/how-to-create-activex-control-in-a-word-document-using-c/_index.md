---
category: general
date: 2026-08-20
description: ActiveX नियंत्रण बनाना, बटन का आकार सेट करना, और Word में बटन जोड़ना
  सीखें, एक पूर्ण C# उदाहरण के साथ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: hi
lastmod: 2026-08-20
og_description: C# के साथ एक Word फ़ाइल में ActiveX नियंत्रण बनाएं। यह ट्यूटोरियल
  दिखाता है कि बटन का आकार कैसे सेट करें, बटन को Word में कैसे जोड़ें, और एक क्लिक
  करने योग्य बटन कैसे बनाएं।
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Word में एक ActiveX नियंत्रण बनाएं – चरण‑दर‑चरण C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: C# का उपयोग करके वर्ड दस्तावेज़ में ActiveX नियंत्रण कैसे बनाएं
url: /hi/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# का उपयोग करके Word दस्तावेज़ में ActiveX कंट्रोल कैसे बनाएं

यदि आपको Microsoft Word फ़ाइल के भीतर **ActiveX कंट्रोल** बनाना है, तो यह गाइड आपको ठीक‑ठीक बताता है कि कैसे करना है। आप देखेंगे कि **Word में बटन कैसे जोड़ें**, बटन के आयाम कैसे सेट करें, और कंट्रोल को क्लिक‑योग्य कैसे बनाएं—सभी एक छोटे, स्वतंत्र C# प्रोग्राम के साथ।

इस ट्यूटोरियल में आप:

* यह समझेंगे कि इंटरैक्टिव Word दस्तावेज़ों के लिए ActiveX कंट्रोल क्यों उपयोगी है।  
* **बटन का आकार सेट** करने और कैप्शन असाइन करने के लिए आवश्यक कोड सीखेंगे।  
* यह देखेंगे कि **क्लिक‑योग्य बटन** कैसे बनाएं जिसे बाद में मैक्रो या बाहरी लॉजिक से जोड़ा जा सके।  

ये चरण Aspose.Words .NET 23.12 या बाद के संस्करण के साथ काम करते हैं और केवल एक .NET डेवलपमेंट एनवायरनमेंट की आवश्यकता होती है।

> **Prerequisite** – आपके पास एक वैध Aspose.Words लाइसेंस है (या आप एवाल्यूएशन संस्करण उपयोग कर रहे हैं) और Visual Studio 2022 या कोई भी C# IDE।

---

## Word दस्तावेज़ में ActiveX कंट्रोल कैसे बनाएं

पहला कदम एक खाली `Document` और एक `DocumentBuilder` को इंस्टैंशिएट करना है। बिल्डर ऑब्जेक्ट्स जैसे ActiveX कंट्रोल को इन्सर्ट करने के लिए हाई‑लेवल API प्रदान करता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

`InsertActiveXButton` मेथड (अगले भाग में परिभाषित) **बटन को इन्सर्ट करने** और उसे कॉन्फ़िगर करने की लॉजिक रखता है।

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

प्रोग्राम चलाने पर **ActiveXButton.docx** बनता है। Word में फ़ाइल खोलने पर **Submit** लेबल वाला बटन दिखाई देगा। कंट्रोल पूरी तरह कार्यात्मक है—इस पर क्लिक करने से मानक `CommandButton_Click` इवेंट उठता है, जिसे आप बाद में VBA मैक्रो से बाइंड कर सकते हैं।

### क्यों यह काम करता है

* `InsertForms2OleControl` Word को बताता है कि वह **CommandButton** प्रकार का OLE ऑब्जेक्ट एम्बेड करे, जो क्लासिक ActiveX बटन क्लास है।  
* चौड़ाई और ऊँचाई के आर्ग्यूमेंट सीधे **बटन का आकार सेट** करते हैं; Word इन मानों को पॉइंट्स (1 pt ≈ 1/72 in) से ट्रांसलेट करता है।  
* कंट्रोल का नाम (`Name = "btnSubmit"`) रखने से VBA से (`ActiveDocument.InlineShapes("btnSubmit")`) उसे ढूँढना आसान हो जाता है।  

---

## बटन का आकार और कैप्शन सेट करें

यदि आपको अलग दिखावट चाहिए, तो `InsertForms2OleControl` कॉल में संख्यात्मक आर्ग्यूमेंट्स को समायोजित करें। मेथड सिग्नेचर है:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – ActiveX क्लास का प्रोग्रामेटिक आइडेंटिफ़ायर (`"CommandButton"` मानक बटन के लिए)।  
* **width / height** – पॉइंट्स में आकार। 2 cm चौड़े बटन के लिए `width = 56.7` उपयोग करें (2 cm ≈ 56.7 pt)।  

इन्सर्ट करने के बाद आप कैप्शन भी बदल सकते हैं:

```csharp
commandButton.Caption = "Send Request";
```

कैप्शन बदलने से आकार नहीं बदलता, लेकिन उपयोगकर्ता को दिखने वाला टेक्स्ट बदल जाता है।

### प्रो टिप

यदि आप स्क्वायर बटन चाहते हैं, तो दोनों आयामों को समान मान दें:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Word में बटन जोड़ें और उसे क्लिक‑योग्य बनाएं

ऊपर दिया गया कोड पहले ही **Word में बटन जोड़ता** है। बटन को कोई कार्रवाई करने के लिए, आपको एक VBA मैक्रो लिखना होगा जो `Click` इवेंट को हैंडल करे। नीचे एक न्यूनतम मैक्रो है जिसे आप Word VBA एडिटर (`Alt+F11` → Insert → Module) में पेस्ट कर सकते हैं:

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

क्योंकि कंट्रोल का नाम `btnSubmit` है, Word स्वचालित रूप से `Click` इवेंट को `btnSubmit_Click` से मैप कर देता है। यह बाहरी लाइब्रेरीज़ के बिना **क्लिक‑योग्य बटन** फ़ंक्शनैलिटी बनाने का मानक तरीका है।

> **Note:** Word में मैक्रो सुरक्षा सेटिंग्स ActiveX कंट्रोल को ब्लॉक कर सकती हैं। सुनिश्चित करें कि दस्तावेज़ के लिए “Enable all macros” या “Enable VBA macros” चुना गया है, या प्रोडक्शन उपयोग के लिए मैक्रो को डिजिटल साइन करें।

---

## सामान्य प्रश्न: बटन कैसे इन्सर्ट करें और ट्रबलशूटिंग

### 1. यदि बटन सेव करने के बाद नहीं दिखता तो क्या करें?

* जाँचें कि आपका Aspose.Words संस्करण `InsertForms2OleControl` को सपोर्ट करता है या नहीं। 22.5 से पहले के संस्करण इस फीचर को नहीं रखते।  
* सुनिश्चित करें कि टार्गेट फ़ाइल फ़ॉर्मेट `.docx` या `.doc` है। पुराने फ़ॉर्मेट जैसे `.rtf` ActiveX ऑब्जेक्ट्स को स्टोर नहीं कर सकते।

### 2. क्या मैं बटन को किसी विशिष्ट बुकमार्क पर इन्सर्ट कर सकता हूँ?

हाँ। `InsertForms2OleControl` कॉल करने से पहले बिल्डर को बुकमार्क पर ले जाएँ:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. **बटन का आकार** टेक्स्ट की लंबाई के आधार पर डायनामिक कैसे सेट करें?

`Graphics.MeasureString` मेथड (`System.Drawing` से) का उपयोग करके आवश्यक चौड़ाई निकालें और पिक्सेल को पॉइंट्स में बदलें (`points = pixels * 72 / DPI`)। फिर इस गणना किए गए मान को `InsertForms2OleControl` को पास करें।

### 4. क्या लूप में कई बटन जोड़ना संभव है?

बिल्कुल। इन्सर्शन लॉजिक को `for` लूप में रखें और प्रत्येक इटरेशन के लिए `Left` और `Top` प्रॉपर्टीज़ को समायोजित करें:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## अपेक्षित आउटपुट

जब आप प्रोग्राम चलाते हैं और **ActiveXButton.docx** खोलते हैं:

* पहले पेज के टॉप‑लेफ़्ट के पास एक ही **Submit** बटन दिखाई देगा।  
* बटन का आकार आपके द्वारा दिए गए आयामों (`100 pt × 30 pt`) के बराबर होगा।  
* यदि आपने VBA मैक्रो जोड़ा है, तो बटन पर क्लिक करने से एक मैसेज बॉक्स दिखेगा: “You clicked the Submit button!”।

आपने अब सफलतापूर्वक **ActiveX कंट्रोल बनाना**, **बटन का आकार सेट करना**, और **Word में बटन जोड़ना** सीख लिया है, साथ ही भविष्य के ऑटोमेशन कार्यों के लिए **बटन इन्सर्ट करना** और **क्लिक‑योग्य बटन बनाना** भी समझ लिया है।

---

## निष्कर्ष

इस ट्यूटोरियल में आपने C# के साथ Word दस्तावेज़ में **ActiveX कंट्रोल** कैसे बनाएं, यह सीखा। चरणों का पालन करके आप **बटन का आकार सेट** कर सकते हैं, कंट्रोल को एक अर्थपूर्ण नाम दे सकते हैं, और **Word में बटन जोड़** सकते हैं ताकि वह **क्लिक‑योग्य बटन** बन जाए और VBA मैक्रो से जुड़ सके।  

अब आप आगे खोज सकते हैं:

* VBA के बजाय .NET COM ऐड‑इन से बटन को बाइंड करना।  
* `CheckBox` या `ComboBox` जैसे अन्य ActiveX क्लासेज़ का उपयोग करना।  
* कई कंट्रोल्स के साथ पूर्ण फ़ॉर्म्स को ऑटोमेट करना।

विभिन्न आकारों के साथ प्रयोग करने में संकोच न करें।

## आप आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकें।

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}