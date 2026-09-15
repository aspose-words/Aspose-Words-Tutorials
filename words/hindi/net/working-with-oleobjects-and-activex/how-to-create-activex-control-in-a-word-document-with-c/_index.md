---
category: general
date: 2026-09-14
description: C# के साथ Word दस्तावेज़ में ActiveX नियंत्रण बनाएं। जानें कैसे ActiveX
  डालें, इंटरैक्टिव बटन जोड़ें, और प्रोग्रामेटिक रूप से .docx फ़ाइल जनरेट करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: hi
lastmod: 2026-09-14
og_description: C# का उपयोग करके वर्ड दस्तावेज़ में ActiveX नियंत्रण बनाएं। ActiveX
  सम्मिलित करने, इंटरैक्टिव बटन जोड़ने और फ़ाइल को सहेजने के लिए इस पूर्ण उदाहरण का
  पालन करें।
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: C# का उपयोग करके वर्ड में ActiveX कंट्रोल बनाएं – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: C# के साथ Word दस्तावेज़ में ActiveX नियंत्रण कैसे बनाएं
url: /hi/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word दस्तावेज़ में ActiveX नियंत्रण कैसे बनाएं

यदि आपको Microsoft Word फ़ाइल के भीतर **ActiveX नियंत्रण बनाना** है, तो यह गाइड एक पूर्ण, तैयार‑चलाने योग्य समाधान दिखाती है। आप देखेंगे कि कैसे ActiveX CommandButton डालें, उसकी गुण सेट करें, और केवल C# कोड का उपयोग करके परिणामी `.docx` फ़ाइल सहेजें।

Word दस्तावेज़ में एक इंटरैक्टिव बटन जोड़ना एक सामान्य आवश्यकता है जब आप चाहते हैं कि अंतिम‑उपयोगकर्ता दस्तावेज़ UI से सीधे मैक्रो या कस्टम लॉजिक को ट्रिगर कर सके। नीचे दिया गया उदाहरण **तीसरे‑पक्ष टूल्स** पर निर्भर हुए बिना **ActiveX डालने** का तरीका दर्शाता है, और यह **प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने** को भी कवर करता है।

इस ट्यूटोरियल के अंत तक आप **कोड से बटन बनाना**, उसका कैप्शन कस्टमाइज़ करना, और एक पोर्टेबल Word फ़ाइल उत्पन्न करना सीख जाएंगे जिसमें ActiveX नियंत्रण बना रहेगा।

## पूर्वापेक्षाएँ

- .NET 6.0 या बाद का (Aspose.Words for .NET लाइब्रेरी .NET Core और .NET Framework दोनों के साथ काम करती है)
- `Aspose.Words` NuGet पैकेज का रेफ़रेंस  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग का बुनियादी ज्ञान

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेस इम्पोर्ट करें

एक नया कंसोल प्रोजेक्ट बनाएं (या कोड को किसी मौजूदा C# एप्लिकेशन में इंटीग्रेट करें)। आवश्यक नेमस्पेस इम्पोर्ट करें ताकि कंपाइलर Word‑प्रोसेसिंग क्लासेज़ को ढूँढ़ सके।

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **यह चरण क्यों महत्वपूर्ण है** – `Aspose.Words` API `Document`, `DocumentBuilder`, और `Forms2OleControl` क्लासेज़ प्रदान करती है जो आपको ऑब्जेक्ट स्तर पर Word फ़ाइलों को मैनीपुलेट करने देती हैं। इन रेफ़रेंसेज़ के बिना बाकी कोड कंपाइल नहीं होगा।

## चरण 2: नया Word दस्तावेज़ और DocumentBuilder बनाएं

`Document` ऑब्जेक्ट पूरे `.docx` पैकेज का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` कंटेंट डालने के लिए एक फ्लुएंट API प्रदान करता है।

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **व्याख्या** – एक नया `Document` इंस्टैंसिएट करने से आपको एक साफ़ कैनवास मिलता है। बिल्डर का कर्सर पहले सेक्शन की शुरुआत में स्थित होता है, जिससे अगला इन्सर्शन तुरंत संभव हो जाता है।

## चरण 3: ActiveX CommandButton डालें

`InsertForms2OleControl` का उपयोग करके एक विशिष्ट स्थान पर ActiveX नियंत्रण रखें। इस मेथड को नियंत्रण प्रकार और एक `RectangleF` चाहिए जो X/Y निर्देशांक और आकार (पॉइंट्स में) निर्धारित करता है।

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **यह क्यों काम करता है** – `OleControlType.CommandButton` API को बताता है कि एक मानक Windows CommandButton बनाना है। रेक्टेंगल बटन को पेज के टॉप‑लेफ़्ट कोने के सापेक्ष स्थित करता है, जिससे आप **इंटरैक्टिव बटन** ठीक उसी जगह जोड़ सकते हैं जहाँ आपको आवश्यकता है।

## चरण 4: बटन की गुण कॉन्फ़िगर करें

अब बटन का दिखने वाला टेक्स्ट (`Caption`) और उसका आंतरिक नाम (`Name`) सेट करें। ये गुण वही हैं जो उपयोगकर्ता देखते हैं और VBA कोड बाद में संदर्भित कर सकता है।

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **व्यावहारिक टिप** – `Name` दस्तावेज़ के भीतर यूनिक होना चाहिए; अन्यथा VBA मैक्रो गलत नियंत्रण को रेफ़र कर सकता है।

## चरण 5: दस्तावेज़ सहेजें

अंत में फ़ाइल को डिस्क पर लिखें। ActiveX नियंत्रण Word पैकेज के अंदर स्टोर होता है, इसलिए सहेजी गई फ़ाइल Microsoft Word में खोलने पर पूरी कार्यक्षमता रखेगी।

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **परिणाम** – `CommandButton.docx` को Word में खोलने पर “Click Me” लेबल वाला एक क्लिक करने योग्य CommandButton दिखेगा। नियंत्रण को Word UI (`Developer → Design Mode → Properties`) के माध्यम से मैक्रो से लिंक किया जा सकता है।

## पूर्ण स्रोत सूची

सभी चरणों को मिलाकर एक एकल, स्व-निहित प्रोग्राम बनता है जिसे आप कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### अपेक्षित आउटपुट

प्रोग्राम चलाने पर एक पुष्टि पंक्ति प्रिंट होती है:

```
Document saved to C:\Temp\CommandButton.docx
```

जब आप उत्पन्न फ़ाइल को Microsoft Word में खोलते हैं, तो आप निर्दिष्ट निर्देशांक पर एक **CommandButton** देखेंगे। डिज़ाइन मोड में बटन पर क्लिक करने से वह हाईलाइट होगा; रन मोड में यह किसी भी मानक ActiveX बटन की तरह व्यवहार करेगा।

## सामान्य विविधताएँ और किनारी मामलों

| परिदृश्य | समायोजन |
|----------|------------|
| **विभिन्न नियंत्रण प्रकार** | `OleControlType.CommandButton` को `OleControlType.CheckBox`, `OleControlType.OptionButton` आदि से बदलें |
| **एकाधिक बटन** | `InsertForms2OleControl` को बार‑बार कॉल करें, प्रत्येक नए बटन के लिए `RectangleF` निर्देशांक अपडेट करें |
| **डायनामिक साइजिंग** | पेज आकार (`builder.PageSetup.PageWidth`) के आधार पर रेक्टेंगल आयाम गणना करें |
| **स्ट्रीम में सहेजना** | जब आपको वेब API से फ़ाइल रिटर्न करनी हो, तो `document.Save(stream, SaveFormat.Docx)` उपयोग करें |
| **Word 97‑2003 फ़ॉर्मेट** | सहेजने के फ़ॉर्मेट को `SaveFormat.Doc` बदलें ताकि `.doc` फ़ाइल बने जिसमें अभी भी ActiveX नियंत्रण एम्बेड हो |

> **प्रो टिप:** हमेशा लक्ष्य Word संस्करण पर उत्पन्न दस्तावेज़ का परीक्षण करें, क्योंकि पुराने संस्करणों में सुरक्षा सेटिंग्स डिफ़ॉल्ट रूप से ActiveX नियंत्रणों को निष्क्रिय कर सकती हैं।

## अक्सर पूछे जाने वाले प्रश्न

**क्या यह .NET Core के साथ काम करता है?**  
हां। Aspose.Words लाइब्रेरी क्रॉस‑प्लेटफ़ॉर्म है और .NET Core तथा .NET 5/6+ के साथ पूरी तरह संगत है।

**क्या मैं बटन को प्रोग्रामेटिक रूप से मैक्रो असाइन कर सकता हूँ?**  
API सीधे VBA कोड एम्बेड नहीं करती। दस्तावेज़ जनरेट होने के बाद, Word में इसे खोलें, Developer टैब सक्षम करें, और एक मैक्रो रिकॉर्ड या लिखें जो `btnClick` को रेफ़र करे।

**अगर बटन नहीं दिख रहा है तो क्या करें?**  
सुनिश्चित करें कि Word में `Developer` टैब सक्षम है और दस्तावेज़ **Protected View** में नहीं खुला है। साथ ही जांचें कि रेक्टेंगल निर्देशांक पेज मार्जिन के भीतर हैं।

## निष्कर्ष

अब आप C# का उपयोग करके Word फ़ाइल के भीतर **ActiveX नियंत्रण बनाना** जानते हैं। इस ट्यूटोरियल ने **ActiveX डालना**, **इंटरैक्टिव बटन जोड़ना**, **शुरू से Word दस्तावेज़ बनाना**, और **कोड से बटन बनाना** जो सहेजने के बाद भी बना रहता है, को कवर किया है।

अब आप अतिरिक्त ActiveX प्रकारों का अन्वेषण कर सकते हैं, बटन को VBA मैक्रो से जोड़ सकते हैं, या इस लॉजिक को बड़े दस्तावेज़‑जनरेशन सर्विस में एम्बेड कर सकते हैं। विभिन्न आकार, स्थितियों और नियंत्रण गुणों के साथ प्रयोग करें ताकि आप अपने उपयोगकर्ता अनुभव को बिल्कुल वही बना सकें जिसकी आपको आवश्यकता है।

---


## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगा सकें।

- [नया Word दस्तावेज़ बनाएं](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Word दस्तावेज़ में VBA प्रोजेक्ट बनाएं](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Aspose.Words for .NET में Word दस्तावेज़ को स्टाइल करें](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}