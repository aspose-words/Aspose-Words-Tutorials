---
category: general
date: 2026-09-05
description: Aspose.Words C# का उपयोग करके Word दस्तावेज़ बनाएं और सीखें कि ActiveX
  कमांड बटन कैसे डालें, बटन का आकार कैसे सेट करें, और इंटरैक्टिव बटन कार्यक्षमता कैसे
  जोड़ें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: hi
lastmod: 2026-09-05
og_description: C# में Word दस्तावेज़ बनाएं और एक ActiveX कमांड बटन डालें। यह ट्यूटोरियल
  दिखाता है कि बटन का आकार कैसे सेट करें और इंटरैक्टिव बटन सुविधाएँ कैसे जोड़ें।
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: C# में ActiveX कमांड बटन के साथ Word दस्तावेज़ बनाएं – चरण-दर-चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: C# में ActiveX कमांड बटन के साथ Word दस्तावेज़ कैसे बनाएं
url: /hi/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में ActiveX कमांड बटन के साथ Word दस्तावेज़ कैसे बनाएं

यदि आपको प्रोग्रामेटिक रूप से **Word दस्तावेज़** बनाना है और एक क्लिक करने योग्य UI तत्व एम्बेड करना है, तो यह गाइड आपको बिल्कुल बताता है कैसे। Aspose.Words for .NET का उपयोग करके आप **Word दस्तावेज़** बना सकते हैं, **कमांड बटन जोड़ सकते हैं**, और उसकी उपस्थिति को नियंत्रित कर सकते हैं—बिना Microsoft Word खोले।

आप सीखेंगे **ActiveX** नियंत्रण कैसे डालें, **बटन का आकार सेट करें**, और बटन को एक इंटरैक्टिव UI घटक की तरह व्यवहार कराएं। COM या VBA का कोई पूर्व अनुभव आवश्यक नहीं है; केवल एक .NET विकास वातावरण और Aspose.Words लाइब्रेरी चाहिए।

## आप क्या हासिल करेंगे

* **Create a Word document** को C# से शुरू से बनाएं।
* **Insert an ActiveX command button** (क्लासिक “Click Me” नियंत्रण)।
* **Set the button size** और स्थिति को सटीक रूप से सेट करें।
* वैकल्पिक रूप से सरल **interactive button** लॉजिक जोड़ें (जैसे, एक macro placeholder)।
* फ़ाइल को `.docx` के रूप में सहेजें जिसे Microsoft Word या किसी भी संगत व्यूअर में खोला जा सकता है।

### आवश्यकताएँ

| आवश्यकता | कारण |
|-------------|--------|
| .NET 6.0 या बाद में | C# कोड के लिए रनटाइम प्रदान करता है। |
| Aspose.Words for .NET (नवीनतम संस्करण) | उदाहरण में उपयोग किए गए `Document`, `DocumentBuilder`, और `Forms2OleControl` APIs प्रदान करता है। |
| Visual Studio 2022 (या कोई भी C# IDE) | नमूना को संकलित और चलाना आसान बनाता है। |
| बुनियादी C# ज्ञान | कोड प्रवाह को समझने के लिए आवश्यक है। |

> **Pro tip:** यदि आप Aspose.Words का ट्रायल संस्करण उपयोग कर रहे हैं, तो कोड चलाने से पहले लाइसेंस सेट करना सुनिश्चित करें ताकि मूल्यांकन वॉटरमार्क से बचा जा सके।

## Word दस्तावेज़ बनाने की प्रक्रिया – समग्र कार्यप्रवाह

प्रक्रिया चार तार्किक चरणों में विभाजित है:

1. **Initialize a new document** और एक `DocumentBuilder` को संपादन के लिए प्रारंभ करें।  
2. `InsertForms2OleControl` का उपयोग करके **Insert an ActiveX command button** डालें।  
3. **Configure the button** – कैप्शन, आकार, और स्थिति।  
4. दस्तावेज़ को डिस्क पर **Save** करें।

![Word document with an ActiveX button](/images/activex-button.png "Screenshot of a Word document that contains an ActiveX command button created with C#")

## ActiveX कमांड बटन कैसे डालें

**how to insert activex** भाग `InsertForms2OleControl` मेथड से शुरू होता है। यह मेथड एक COM‑आधारित नियंत्रण बनाता है जिसे Word एक ActiveX ऑब्जेक्ट के रूप में मानता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Why this works:** `OleControlType.CommandButton` Aspose.Words को क्लासिक VB‑स्टाइल बटन बनाने के लिए बताता है। आकार और स्थान पॉइंट्स में व्यक्त किए जाते हैं (1 पॉइंट = 1/72 इंच), जो लेआउट पर सटीक नियंत्रण देता है।

## कमांड बटन जोड़ें और बटन का आकार सेट करें

नियंत्रण डालने के बाद आप उसकी दृश्य गुणों को समायोजित कर सकते हैं। **add command button** चरण **set button size** को भी कवर करता है।

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explanation:**  

* `Caption` बटन पर प्रदर्शित लेबल है।  
* `Width` और `Height` आपको प्रारंभिक सम्मिलन के बाद **set button size** करने देते हैं—जब आकार रनटाइम डेटा पर निर्भर करता है तो उपयोगी।  
* `Left` और `Top` दस्तावेज़ को पुनः बनाने के बिना नियंत्रण को पुनः स्थित करते हैं।

> **Common pitfall:** पिक्सेल के बजाय पॉइंट्स का उपयोग करना भूल जाने से बटन बहुत छोटा या बहुत बड़ा दिखाई देगा। यदि आप स्क्रीन माप से शुरू करते हैं तो हमेशा पिक्सेल मान (`px * 72 / DPI`) को परिवर्तित करें।

## इंटरैक्टिव बटन जोड़ें (वैकल्पिक)

एक ActiveX बटन क्लिक करने पर एक macro चला सकता है, लेकिन C# से VBA कोड एम्बेड करना शुद्ध Aspose.Words कार्यप्रवाह के दायरे से बाहर है। इसके बजाय, आप एक placeholder प्रॉपर्टी जोड़ सकते हैं जिसे Word macro नाम के रूप में पहचान लेगा।

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

जब उपयोगकर्ता उत्पन्न `.docx` को Word में खोलता है, बटन पर क्लिक करने से `MyMacroName` चलाने का प्रयास होगा। यदि macro मौजूद नहीं है, तो Word उपयोगकर्ता को इसे बनाने के लिए प्रॉम्प्ट करेगा।

**Why you might use this:** उन कॉरपोरेट फॉर्म्स के लिए जहाँ macro फ़ील्ड भरता है, C# कोड को केवल बटन रखना होता है; macro लॉजिक दस्तावेज़ के VBA प्रोजेक्ट में रहता है।

## दस्तावेज़ सहेजें और परिणाम सत्यापित करें

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Expected output:** Microsoft Word में `CommandButton.docx` खोलने पर **Click Me** लेबल वाला बटन दिखेगा जो बाएँ मार्जिन से 100 pts और शीर्ष से 120 pts पर स्थित है। बटन का आकार **200 pts × 80 pts** है। बटन पर क्लिक करने से macro placeholder चलाया जाएगा (यदि मौजूद है)।

## पूर्ण कार्यशील उदाहरण

नीचे पूर्ण, चलाने योग्य प्रोग्राम है जो सब कुछ एक साथ रखता है। इसे एक नए Console App प्रोजेक्ट में कॉपी करें, Aspose.Words NuGet पैकेज जोड़ें, और चलाएँ।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

प्रोग्राम चलाएँ, फिर उत्पन्न फ़ाइल खोलें। आपको **interactive button** आगे की कस्टमाइज़ेशन के लिए तैयार दिखेगा।

## अक्सर पूछे जाने वाले प्रश्न

| प्रश्न | उत्तर |
|----------|--------|
| **क्या यह .NET Core के साथ काम करता है?** | हाँ। Aspose.Words .NET Standard को सपोर्ट करता है, इसलिए वही कोड .NET 5/6/7 पर चलता है। |
| **क्या मैं अन्य ActiveX नियंत्रण (जैसे, CheckBox) उपयोग कर सकता हूँ?** | बिल्कुल। `OleControlType.CommandButton` को `OleControlType.CheckBox`, `OleControlType.OptionButton` आदि से बदलें। |
| **यदि मुझे लैंडस्केप पेज पर बड़ा बटन चाहिए तो क्या करें?** | `Width`, `Height`, `Left`, और `Top` प्रॉपर्टीज़ को अनुपातिक रूप से समायोजित करें। याद रखें कि पॉइंट्स पेज की अभिविन्यास के बावजूद समान रहते हैं। |
| **क्या बटन को क्लिक करने योग्य बनाने के लिए macro आवश्यक है?** | नहीं। बटन UI तत्व के रूप में पूरी तरह कार्यशील है; macro केवल क्लिक करने पर कस्टम व्यवहार जोड़ता है। |

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words के साथ **Word दस्तावेज़** कैसे **create** करें, **command button** कैसे **add** करें, **button size** कैसे **set** करें, और वैकल्पिक रूप से बटन को macro से लिंक करके **add interactive button** व्यवहार प्राप्त करें। यह तरीका आपको फॉर्म निर्माण को स्वचालित करने, डायनेमिक रिपोर्ट जनरेट करने, या सीधे C# से Word‑आधारित UI प्रोटोटाइप बनाने की अनुमति देता है।

अगला, आप निम्नलिखित विषयों का अन्वेषण कर सकते हैं:

* सर्वे फॉर्म्स के लिए **ActiveX चेक बॉक्स कैसे डालें**।  
* `DocumentBuilder` का उपयोग करके बटन के आसपास **रिच टेक्स्ट कंटेंट कैसे जोड़ें**।  
* बटन को कार्यशील रखते हुए **दस्तावेज़ को कैसे सुरक्षित करें**।  

विभिन्न नियंत्रण प्रकारों, आकारों, और macro नामों के साथ प्रयोग करने में संकोच न करें ताकि आपका विशिष्ट परिदृश्य फिट हो सके। कोडिंग का आनंद लें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for .NET के साथ Word दस्तावेज़ बनाएं](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words का उपयोग करके Word दस्तावेज़ में इनलाइन इमेज डालें](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Aspose.Words का उपयोग करके टेबल के साथ Word दस्तावेज़ बनाएं](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}