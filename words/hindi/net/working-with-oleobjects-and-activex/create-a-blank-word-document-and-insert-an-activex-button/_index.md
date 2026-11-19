---
category: general
date: 2026-11-18
description: एक खाली Word दस्तावेज़ बनाएं और C# के साथ एक ActiveX बटन डालें। नियंत्रण
  जोड़ना, बटन का कैप्शन सेट करना, और फ़ाइल को सहेजना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: hi
lastmod: 2026-11-18
og_description: C# का उपयोग करके एक खाली Word दस्तावेज़ बनाएं और उसमें एक ActiveX
  बटन डालें। नियंत्रण जोड़ने, बटन कैप्शन सेट करने और परिणाम को सहेजने के लिए इस पूर्ण
  ट्यूटोरियल का पालन करें।
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: एक खाली Word दस्तावेज़ बनाएं और ActiveX बटन डालें – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: एक खाली Word दस्तावेज़ बनाएं और एक ActiveX बटन सम्मिलित करें
url: /hi/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# एक खाली Word दस्तावेज़ बनाएं और एक ActiveX बटन डालें

यदि आपको **एक खाली Word दस्तावेज़** बनाना है और उसके भीतर एक इंटरैक्टिव ActiveX बटन रखना है, तो यह गाइड आपको Aspose.Words for .NET के साथ इसे बिल्कुल कैसे करना है दिखाएगा। आप पूर्ण कोड देखेंगे, समझेंगे कि प्रत्येक पंक्ति क्यों महत्वपूर्ण है, और सीखेंगे कि **बटन कैप्शन सेट** कैसे करें ताकि नियंत्रण उपयोगकर्ता इंटरैक्शन के लिए तैयार दिखे।

मुख्य लक्ष्य के अलावा, हम **ActiveX डालने के तरीके** को कवर करेंगे, **Word फ़ाइल में नियंत्रण जोड़ने के चरण** और कस्टम कैप्शन के साथ **ActiveX बटन डालने** की बारीकियों को समझेंगे। अंत तक आपके पास किसी भी दस्तावेज़‑ऑटोमेशन परिदृश्य के लिए एक पुन: उपयोग योग्य पैटर्न होगा जिसमें एम्बेडेड UI तत्वों की आवश्यकता होती है।

## What you’ll learn

* प्रोग्रामेटिक रूप से **एक खाली Word दस्तावेज़ बनाना**।  
* **ActiveX बटन डालने** के लिए आवश्यक सटीक API कॉल्स और उसकी प्रॉपर्टीज़ को कॉन्फ़िगर करना।  
* **बटन कैप्शन सेट** करना ताकि नियंत्रण वांछित टेक्स्ट दिखाए।  
* फ़ाइल को अपनी पसंद के स्थान पर सहेजने और सामान्य समस्याओं को संभालने के टिप्स।

### Prerequisites

* .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.6+ के साथ भी काम करता है)।  
* Aspose.Words for .NET स्थापित (`Install-Package Aspose.Words`)।  
* C# और Visual Studio या किसी भी .NET‑compatible IDE की बुनियादी परिचितता।

---

## Create a blank Word document with Aspose.Words

पहला चरण एक खाली `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट एक Word फ़ाइल का प्रतिनिधित्व करता है जिसमें तब तक कोई सामग्री नहीं होती जब तक हम कुछ नहीं जोड़ते।

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Why this matters*: एक खाली `Document` आपको एक साफ़ कैनवास देता है। आप बाद में पैराग्राफ, टेबल या नियंत्रण जोड़ सकते हैं बिना मौजूदा फ़ॉर्मेटिंग की चिंता किए।

---

## Initialise a DocumentBuilder to work with the document

`DocumentBuilder` एक हेल्पर क्लास है जो आपको वर्तमान कर्सर स्थिति पर सामग्री डालने देती है। यह स्वचालित रूप से ट्रैक करता है कि आप दस्तावेज़ में कहाँ हैं।

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: `DocumentBuilder` के बिना आपको लो‑लेवल नोड ट्री को मैन्युअली मैनीपुलेट करना पड़ेगा। बिल्डर टेक्स्ट, इमेज और ActiveX नियंत्रणों को डालने को सरल बनाता है।

---

## How to insert an ActiveX button (insert activex button)

अब हम `InsertForms2OleControl` का उपयोग करके एक ActiveX नियंत्रण एम्बेड करते हैं। इस मेथड को तीन आर्ग्यूमेंट्स की आवश्यकता होती है:

1. नियंत्रण का प्रकार (`OleControlType.CommandButton`)।  
2. नियंत्रण का एक आंतरिक नाम (VBA या मैक्रो कोड द्वारा उपयोग किया जाता है)।  
3. एक `RectangleF` जो पेज पर स्थिति और आकार को परिभाषित करता है।

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Why this matters*: यह **Word दस्तावेज़ में activex डालने** का मूल भाग है। रेक्टैंगल के कॉर्डिनेट्स पॉइंट्स में व्यक्त होते हैं (1 पॉइंट = 1/72 इंच)। बटन को जहाँ चाहिए वहाँ रखने के लिए इन्हें समायोजित करें।

### Tip

यदि आपको बटन को किसी विशिष्ट पेज पर दिखाना है, तो पहले बिल्डर का कर्सर मूव करें:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## How to set button caption (set button caption)

नियंत्रण रखने के बाद, आप उसकी प्रॉपर्टीज़ को संशोधित कर सकते हैं। सबसे दृश्यमान प्रॉपर्टी `Caption` है, जो बटन पर दिखाए जाने वाले टेक्स्ट को निर्धारित करती है।

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Why this matters*: उपयोगकर्ता कैप्शन देखते हैं, आंतरिक नाम नहीं। इसे बदलने से बटन अंतिम दस्तावेज़ में अर्थपूर्ण बन जाता है।

---

## Save the document containing the button

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप कोई भी समर्थित फ़ॉर्मेट (`.docx`, `.pdf`, आदि) चुन सकते हैं। यहाँ हम इसे Word दस्तावेज़ के रूप में सहेजते हैं।

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Why this matters*: फ़ाइल को स्थायी रूप से सहेजने से आप इसे Microsoft Word में खोलकर बटन का परीक्षण कर सकते हैं। जब दस्तावेज़ खोला जाएगा, बटन “Press” कैप्शन के साथ दिखाई देगा।

### Expected result

`with_button.docx` को Word में खोलने पर एक खाली पेज दिखता है जिसमें एक आयताकार बटन **Press** लेबल के साथ होता है। बटन पर क्लिक करने से डिफ़ॉल्ट रूप से कुछ नहीं होता क्योंकि कोई VBA मैक्रो जुड़ा नहीं है, लेकिन नियंत्रण पूरी तरह कार्यात्मक है और बाद में कोड से जोड़ा जा सकता है।

---

## How to add control to a specific paragraph (how to add control)

कभी-कभी आप बटन को किसी विशेष पैराग्राफ के अंदर चाहते हैं, उदाहरण के लिए कुछ निर्देशात्मक टेक्स्ट के बाद। नियंत्रण डालने से पहले बिल्डर को पोज़िशन करने के लिए `MoveTo` का उपयोग करें।

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Why this matters*: यह पैटर्न संदर्भ में **नियंत्रण जोड़ने** का तरीका दर्शाता है, जिससे दस्तावेज़ लेआउट तार्किक बना रहता है।

---

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| बटन पेज के बाहर दिखता है | रेक्टैंगल कॉर्डिनेट्स पेज मार्जिन के बाहर हैं | पेज डाइमेंशन प्राप्त करने और सुरक्षित `RectangleF` गणना करने के लिए `builder.PageSetup` का उपयोग करें। |
| कैप्शन नहीं दिख रहा | `Caption` को नियंत्रण के पूरी तरह इनिशियलाइज़ होने से पहले सेट किया गया | `Caption` को `InsertForms2OleControl` कॉल के **बाद** सेट करें, जैसा कि चरण 4 में दिखाया गया है। |
| दस्तावेज़ बटन के बिना सहेजा जाता है | इन्सर्शन के बाद बिल्डर का कर्सर मूव किया गया बिना बदलाव कमिट किए | बिल्डर को उसी पेज पर रखें या सहेजने से पहले `builder.Document.UpdatePageLayout()` कॉल करें। |

---

## Full, runnable example

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं। यह एक खाली Word फ़ाइल बनाता है, एक ActiveX बटन डालता है, उसका कैप्शन सेट करता है, और परिणाम सहेजता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output**: प्रोग्राम चलाने के बाद, Microsoft Word में `C:\Temp\with_button.docx` खोलें। आपको एक पेज दिखेगा जिसमें टेक्स्ट “Below is an ActiveX button created programmatically:” होगा, उसके बाद **Press** लेबल वाला बटन होगा।

---

## Conclusion

अब आप जानते हैं कि Aspose.Words for .NET का उपयोग करके **एक खाली Word दस्तावेज़ बनाना**, **ActiveX बटन डालना**, **बटन कैप्शन सेट करना**, और **परिणाम सहेजना** कैसे है। वही पैटर्न `OleControlType` बदलकर अन्य ActiveX नियंत्रणों (चेकबॉक्स, लिस्ट बॉक्स आदि) पर भी लागू किया जा सकता है।  

अगला, आप VBA के साथ **ActiveX बटन इवेंट्स डालने** या मौजूदा दस्तावेज़ों में **नियंत्रण जोड़ने** का पता लगा सकते हैं जिनमें पहले से सामग्री है। दोनों विषय यहाँ कवर किए गए अवधारणाओं पर सीधे आधारित हैं।

कोडिंग का आनंद लें, और विभिन्न आकार, स्थितियों और कैप्शन के साथ प्रयोग करने में संकोच न करें ताकि आपके एप्लिकेशन की UI आवश्यकताओं के अनुरूप हो सके!

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करती हैं।

- [C# के साथ ActiveX कमांड बटन वाला Word दस्तावेज़ कैसे बनाएं](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Aspose.Words के साथ Word दस्तावेज़ में ActiveX बटन कैसे जोड़ें](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}