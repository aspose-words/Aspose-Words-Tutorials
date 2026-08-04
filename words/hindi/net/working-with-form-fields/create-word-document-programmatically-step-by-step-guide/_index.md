---
category: general
date: 2026-08-04
description: C# का उपयोग करके प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाएं। सिर्फ कुछ ही
  चरणों में Aspose.Words के साथ प्रोग्रामेटिकली कमांड बटन जोड़ना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: hi
lastmod: 2026-08-04
og_description: Aspose.Words के साथ प्रोग्रामेटिकली वर्ड दस्तावेज़ बनाएं। यह गाइड
  दिखाता है कि प्रोग्रामेटिकली कमांड बटन कैसे जोड़ें, उसे कॉन्फ़िगर करें, और फ़ाइल
  को सहेजें।
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं – पूर्ण C# ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं – पूर्ण C# ट्यूटोरियल

यदि आपको **create word document programmatically** करने की आवश्यकता है, तो यह गाइड आपको Aspose.Words for .NET के साथ यह बिल्कुल कैसे करना है दिखाता है। केवल कुछ ही C# लाइनों में आप एक खाली `.docx` फ़ाइल बना सकते हैं, **programmatically add command button** नियंत्रण जोड़ सकते हैं, उनकी प्रॉपर्टीज़ सेट कर सकते हैं, और परिणाम को सहेज सकते हैं।  

नीचे दिए गए चरण प्रोजेक्ट सेटअप से लेकर एज केस को संभालने तक सब कुछ कवर करते हैं, ताकि आप कोड को अपनी एप्लिकेशन में कॉपी करके बिना किसी संशोधन के चला सकें।

## आप क्या हासिल करेंगे

* स्मृति में पूरी तरह से एक नया Word दस्तावेज़ इनिशियलाइज़ करें।  
* **Programmatically add command button** OLE नियंत्रण को किसी भी स्थान और आकार में जोड़ें।  
* बटन का कैप्शन, आंतरिक नाम, और अन्य OLE प्रॉपर्टीज़ कॉन्फ़िगर करें।  
* जेनरेटेड दस्तावेज़ को डिस्क या स्ट्रीम में आगे की प्रोसेसिंग के लिए सहेजें।  

### आवश्यकताएँ

* .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.6+ के साथ भी काम करता है)।  
* एक वैध Aspose.Words for .NET लाइसेंस (या मुफ्त इवैल्यूएशन)।  
* C# और Visual Studio (या आपके पसंदीदा किसी भी IDE) की बुनियादी परिचितता।  

> **उपयोगी टिप:** यदि आप लाइसेंस के बिना सैंपल चलाते हैं, तो Aspose.Words पहले पृष्ठ पर एक छोटा इवैल्यूएशन वॉटरमार्क जोड़ देगा।

## चरण 1: प्रोजेक्ट सेट अप करें और आवश्यक नेमस्पेसेस इम्पोर्ट करें

एक नया Console App बनाएं (या मौजूदा सर्विस में इंटीग्रेट करें) और Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

फिर अपने `.cs` फ़ाइल के शीर्ष पर आवश्यक नेमस्पेसेस शामिल करें:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

ये इम्पोर्ट्स आपको `Document`, `DocumentBuilder`, `Forms2OleControl`, और पोजिशनिंग के लिए उपयोग किए जाने वाले `RectangleF` स्ट्रक्ट तक पहुंच प्रदान करते हैं।

## चरण 2: एक नया Word दस्तावेज़ इनिशियलाइज़ करें

किसी भी **create word document programmatically** वर्कफ़्लो में पहला ऑपरेशन `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट केवल मेमोरी में रहता है जब तक आप इसे स्पष्ट रूप से सहेजते नहीं।

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` एक कर्सर की तरह काम करता है जो ट्रैक करता है कि अगला एलिमेंट कहाँ रखा जाएगा। इसका उपयोग कोड को संक्षिप्त रखता है और उसी तरह दर्शाता है जैसे आप सीधे Word में टाइप करेंगे।

## चरण 3: एक command button OLE नियंत्रण डालें

Aspose.Words `InsertForms2OleControl` मेथड प्रदान करता है जो OLE ऑब्जेक्ट जैसे command buttons, check boxes, या combo boxes को एम्बेड करता है। इस मेथड को तीन आर्ग्युमेंट्स की आवश्यकता होती है:

1. `ControlType` enum मान (यहाँ `CommandButton`)।  
2. एक `RectangleF` जो नियंत्रण की X‑Y स्थिति और चौड़ाई‑ऊँचाई को परिभाषित करता है (पॉइंट्स में मापा जाता है, जहाँ 72 pt = 1 inch)।  
3. वैकल्पिक रूप से, अतिरिक्त OLE प्रॉपर्टीज़ (बेसिक बटन के लिए आवश्यक नहीं)।

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **यह क्यों काम करता है:** `InsertForms2OleControl` दस्तावेज़ में एक OLE कंटेनर बनाता है और एक `Forms2OleControl` रैपर रिटर्न करता है। यह रैपर आपको नीचे के OLE ऑब्जेक्ट (वास्तविक बटन) को बिना लो‑लेवल COM इंटरऑप से निपटे मैनीपुलेट करने देता है।

## चरण 4: बटन का कैप्शन और आंतरिक नाम कॉन्फ़िगर करें

इन्सर्शन के बाद, आमतौर पर आप बटन को एक यूज़र‑विज़िबल लेबल और एक आंतरिक पहचानकर्ता देना चाहते हैं जिसे आपका मैक्रो या ऐड‑इन बाद में रेफ़र कर सके।

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

- `Caption` वह टेक्स्ट है जो Word UI में बटन पर दिखता है।  
- `Name` वह प्रोग्रामेटिक पहचानकर्ता है जिसका उपयोग VBA या बाहरी ऑटोमेशन स्क्रिप्ट्स करते हैं।

### वैकल्पिक: बटन को एक मैक्रो असाइन करें

यदि आप बटन क्लिक होने पर VBA मैक्रो चलाने की योजना बनाते हैं, तो आप मैक्रो का नाम अटैच कर सकते हैं:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **विशेष मामला:** जब लक्ष्य दस्तावेज़ ऐसे मशीन पर खोला जाएगा जिसमें मैक्रो नहीं है, तो Word एक सुरक्षा चेतावनी दिखाएगा। हमेशा अपने मैक्रो को साइन करें या उपयोगकर्ताओं को आवश्यक सेटिंग्स के बारे में सूचित करें।

## चरण 5: दस्तावेज़ सहेजें

आप फ़ाइल को डिस्क, `MemoryStream`, या सीधे वेब API में रिस्पॉन्स ऑब्जेक्ट में लिख सकते हैं। एक कंसोल डेमो के लिए सबसे सरल तरीका है इसे लोकल फ़ोल्डर में सहेजना:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

परिणामी `.docx` Microsoft Word में खुलता है जिसमें एक कार्यात्मक command button होता है जो “Click Me” दिखाता है। बटन पर क्लिक करने से असाइन किया गया मैक्रो (यदि कोई हो) ट्रिगर होगा या सिर्फ एक डिफ़ॉल्ट संदेश दिखाएगा।

## पूर्ण कार्यशील उदाहरण

`Program.cs` में नीचे दिया गया प्रोग्राम कॉपी करें और चलाएँ। यह पूरे **create word document programmatically** फ्लो को दिखाता है, जिसमें एरर हैंडलिंग भी शामिल है।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**अपेक्षित परिणाम:** Word में `CommandButton.docx` खोलने पर “Click Me” लेबल वाला बटन दिखता है। बटन पर होवर करने से प्रॉपर्टीज़ पेन में नाम `cmdClickMe` दिखता है।

## सामान्य प्रश्न और ट्रबलशूटिंग

| Question | Answer |
|----------|--------|
| *क्या मैं बटन को मौजूदा दस्तावेज़ में जोड़ सकता हूँ?* | हां। फ़ाइल को `new Document("Existing.docx")` से लोड करें, फिर वही `InsertForms2OleControl` कॉल उपयोग करें। |
| *`RectangleF` कौन सी इकाइयाँ उपयोग करता है?* | पॉइंट्स (1 inch = 72 pt). बटन को सटीक रूप से पोजिशन करने के लिए मान समायोजित करें। |
| *क्या बटन Word for Mac पर काम करेगा?* | OLE नियंत्रण केवल Windows Word में समर्थित हैं। Mac पर बटन एक स्थिर इमेज के रूप में दिखता है। |
| *क्या उत्पादन उपयोग के लिए लाइसेंस चाहिए?* | एक कमर्शियल लाइसेंस इवैल्यूएशन वॉटरमार्क हटाता है और पूरी कार्यक्षमता अनलॉक करता है। |
| *इन्सर्शन के बाद बटन का आकार कैसे बदलें?* | `commandButton.Width` और `commandButton.Height` को संशोधित करें या नए `RectangleF` के साथ पुनः‑इन्सर्ट करें। |

## समाधान का विस्तार

अब जब आप जानते हैं कि **programmatically add command button** नियंत्रण कैसे जोड़ें, तो आप इन संबंधित विषयों का अन्वेषण कर सकते हैं:

* **Insert other form controls** – `ControlType.CheckBox`, `ControlType.OptionButton` आदि का उपयोग करें। (द्वितीयक कीवर्ड *Aspose.Words InsertForms2OleControl* को कवर करता है)।  
* **Populate the document with dynamic data** – डेटाबेस से डेटा को टेबल या मेल‑मर्ज फ़ील्ड्स में मर्ज करें।  
* **Export to PDF** – बटन जोड़ने के बाद, `doc.Save("output.pdf", SaveFormat.Pdf)` कॉल करके PDF संस्करण बनाएं (संबंधित *C# Word automation*).

## निष्कर्ष

अब आपके पास Aspose.Words for .NET का उपयोग करके **create word document programmatically** और **programmatically add command button** के लिए एक पूर्ण, प्रोडक्शन‑रेडी पैटर्न है। ट्यूटोरियल ने प्रोजेक्ट सेटअप, दस्तावेज़ इनिशियलाइज़ेशन, OLE बटन इन्सर्शन, प्रॉपर्टी कॉन्फ़िगरेशन, और फ़ाइल सहेजने को कवर किया। आप कोड को अन्य फ़ॉर्म कंट्रोल्स जोड़ने, मैक्रो अटैच करने, या लॉजिक को वेब सर्विसेज या बैकग्राउंड जॉब्स में इंटीग्रेट करने के लिए स्वतंत्र हैं।

कोडिंग का आनंद लें, और Word दस्तावेज़ों को ऑटोमेट करने का मज़ा उठाएँ!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words के साथ Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Aspose.Words का उपयोग करके तालिका के साथ Word दस्तावेज़ बनाएं](/words/english/net/add-content-using-document-builder/build-table/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में ग्रुप शेप बनाएं](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}