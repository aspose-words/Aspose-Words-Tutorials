---
category: general
date: 2026-08-10
description: Aspose.Words का उपयोग करके प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाएं, फिर
  एक ActiveX कंट्रोल वर्ड बटन जोड़ें। कुछ ही मिनटों में ActiveX कमांड बटन डालें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: hi
lastmod: 2026-08-10
og_description: Aspose.Words का उपयोग करके प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाएं, फिर
  एक ActiveX नियंत्रण वर्ड बटन जोड़ें। जानें कि कैसे जल्दी से ActiveX कमांड बटन डालें।
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं – C# में एक ActiveX बटन जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं और एक्टिवएक्स बटन जोड़ें
url: /hi/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं और ActiveX बटन जोड़ें

यदि आपको **create word document programmatically** है, तो यह गाइड Aspose.Words for .NET के साथ पूरी प्रक्रिया को समझाता है। आप यह भी सीखेंगे कि **add activex control word** तत्व और **insert activex command button** ऑब्जेक्ट्स को एक ही, स्वतंत्र उदाहरण में सम्मिलित किया जाए।

कोड से Word फ़ाइलें जनरेट करने से Microsoft Word खोलने के मैनुअल कदम हट जाते हैं, जिससे आप रिपोर्ट, इनवॉइस, या डेटा‑ड्रिवन कॉन्ट्रैक्ट्स को स्वचालित रूप से बना सकते हैं। इस ट्यूटोरियल के अंत तक आपके पास एक तैयार‑चलाने योग्य C# कंसोल ऐप होगा जो एक इंटरैक्टिव ActiveX CommandButton वाला `.docx` फ़ाइल उत्पन्न करता है।

## पूर्वापेक्षाएँ

* .NET 6.0 SDK या बाद का संस्करण (कोड .NET Framework 4.6+ के साथ भी काम करता है)
* Visual Studio 2022 या कोई भी IDE जो .NET विकास को सपोर्ट करता है
* एक वैध Aspose.Words for .NET लाइसेंस (आप परीक्षण के लिए मुफ्त इवैल्यूएशन कुंजी का उपयोग कर सकते हैं)
* C# सिंटैक्स और COM/ActiveX कंट्रोल्स की अवधारणा की बुनियादी समझ

> **Pro tip:** यदि आप जनरेट किए गए दस्तावेज़ को उन उपयोगकर्ताओं को वितरित करने की योजना बना रहे हैं जिनके पास Word स्थापित नहीं है, तो ActiveX कंट्रोल की रनटाइम फ़ाइलें `.docx` के साथ एम्बेड करें या एक मैक्रो‑सक्षम टेम्पलेट प्रदान करें।

## प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाना – प्रारंभिक सेटअप

पहले, अपने प्रोजेक्ट में Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

फिर एक नया कंसोल प्रोजेक्ट बनाएं (यदि आपके पास पहले से नहीं है):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

जनरेट की गई `Program.cs` फ़ाइल खोलें – हम इसकी सामग्री को नीचे दिए गए पूर्ण समाधान से बदल देंगे।

## चरण 1: नेमस्पेस इम्पोर्ट करें और लाइसेंस कॉन्फ़िगर करें

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*यह क्यों महत्वपूर्ण है*: `Aspose.Words.Drawing` को इम्पोर्ट करने से आपको `Forms2OleControl` तक पहुंच मिलती है, जो Word दस्तावेज़ में ActiveX कंट्रोल का प्रतिनिधित्व करने वाली क्लास है। लाइसेंस को जल्दी सेट करने से प्रोडक्शन में रनटाइम चेतावनियों से बचा जा सकता है।

## चरण 2: एक खाली दस्तावेज़ और DocumentBuilder बनाएं

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` ऑब्जेक्ट `.docx` फ़ाइल का इन‑मेमोरी प्रतिनिधित्व है। `DocumentBuilder` एक कर्सर की तरह काम करता है जिसे आप दस्तावेज़ में तत्व सम्मिलित करने के लिए घुमाते हैं।

## चरण 3: ActiveX CommandButton कंट्रोल सम्मिलित करें

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` एक OLE ऑब्जेक्ट बनाता है जिसे Word ActiveX कंट्रोल के रूप में मानता है। कोऑर्डिनेट सिस्टम पॉइंट्स (1 पॉइंट = 1/72 इंच) का उपयोग करता है, जो Word के लेआउट इंजन से मेल खाता है।

## चरण 4: बटन का कैप्शन और वैकल्पिक प्रॉपर्टीज़ सेट करें

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

`Caption` प्रॉपर्टी सेट करना बटन को लेबल करने का सबसे सामान्य तरीका है। यदि आपको बटन को VBA मैक्रो चलाना है, तो मैक्रो नाम को `OnAction` में असाइन करें। यह ट्यूटोरियल विज़ुअल भाग पर केंद्रित है; मैक्रो इंटीग्रेशन “अगले कदम” सेक्शन में कवर किया गया है।

## चरण 5: दस्तावेज़ सहेजें

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

जब आप प्रोग्राम चलाएंगे, तो आपको एक कंसोल संदेश दिखाई देगा जो पुष्टि करेगा कि `ActiveX_CommandButton.docx` डिस्क पर लिखी गई है।

### पूरा स्रोत कोड (कॉपी‑पेस्ट तैयार)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

स्निपेट चलाने से एक Word फ़ाइल बनती है जिसमें एक क्लिक करने योग्य **ActiveX command button** होता है। फ़ाइल को Microsoft Word में खोलें, **Design Mode** (Developer टैब → Design Mode) पर स्विच करें, और आप बटन को ठीक उसी जगह पर रेंडर होते देखेंगे जहाँ आपने रखा था।

## चरण 6: परिणाम सत्यापित करें

1. `ActiveX_CommandButton.docx` को Microsoft Word में खोलें।
2. यदि **Developer** टैब दिखाई नहीं देता है तो उसे सक्षम करें (`File → Options → Customize Ribbon → check Developer`)।
3. **Design Mode** पर क्लिक करें। बटन को “Submit” लेबल के साथ दिखना चाहिए।
4. यदि आपने `OnAction` मैक्रो जोड़ा है, तो Design Mode बंद होने पर बटन पर क्लिक करके मैक्रो को ट्रिगर करें।

यदि बटन नहीं दिखता है, तो सुनिश्चित करें कि Word की सुरक्षा सेटिंग्स ActiveX कंट्रोल्स की अनुमति देती हैं (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`)।

## आम प्रश्न और किनारे के मामलों

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं अन्य ActiveX प्रकार सम्मिलित कर सकता हूँ?** | हाँ। `Forms2OleControlType` एन्‍युम में `CheckBox`, `OptionButton`, `ComboBox` आदि शामिल हैं। `CommandButton` को इच्छित एन्‍युम वैल्यू से बदलें। |

## अगले क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके वर्ड दस्तावेज़ में ग्रुप शेप बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words का उपयोग करके हेडर और फुटर के साथ वर्ड दस्तावेज़ बनाएं](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words का उपयोग करके वर्ड दस्तावेज़ में इनलाइन इमेज डालें](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}