---
category: general
date: 2026-10-10
description: C# में Aspose.Words का उपयोग करके बटन का टेक्स्ट सेट करें और एक ActiveX
  बटन जोड़ें। जानें कैसे बटन डालें, बटन कंट्रोल बनाएं, और Word दस्तावेज़ में कैप्शन
  को कस्टमाइज़ करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: hi
lastmod: 2026-10-10
og_description: C# में Aspose.Words के साथ बटन का टेक्स्ट सेट करें और एक ActiveX बटन
  जोड़ें। बटन डालने, बटन कंट्रोल बनाने और उसके कैप्शन को कस्टमाइज़ करने के लिए इस
  चरण‑दर‑चरण गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: C# में बटन का टेक्स्ट सेट करें और ActiveX बटन जोड़ें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: बटन का टेक्स्ट सेट करें और C# में एक ActiveX बटन जोड़ें
url: /hi/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में बटन टेक्स्ट सेट करें और ActiveX बटन जोड़ें

यदि आपको Word दस्तावेज़ के अंदर एक ActiveX बटन पर **set button text** सेट करना है, तो यह गाइड आपको बिल्कुल बताता है कैसे। ट्यूटोरियल के अंत तक आप **insert button**, एक **button control** बना पाएँगे, और केवल कुछ ही C# कोड लाइनों से उसकी कैप्शन को कस्टमाइज़ कर सकेंगे।

ActiveX कंट्रोल्स के साथ काम करना आम है जब आप Word में इंटरैक्टिव फॉर्म बनाना चाहते हैं—चाहे वह कॉन्ट्रैक्ट टेम्पलेट हो, सर्वे हो, या आंतरिक टूल। इस उदाहरण में Aspose.Words for .NET का उपयोग किया गया है, एक लाइब्रेरी जो Microsoft Office स्थापित किए बिना Word फ़ाइलों को मैनीपुलेट करने देती है।

## Prerequisites

शुरू करने से पहले, सुनिश्चित करें कि आपके पास है:

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो  
* Visual Studio 2022 (या कोई भी IDE जो C# को सपोर्ट करता हो)  
* Aspose.Words for .NET लाइसेंस (सीखने के लिए मुफ्त इवैल्यूएशन काम करता है)  

आपको `Aspose.Words` NuGet पैकेज का रेफ़रेंस भी चाहिए:

```bash
dotnet add package Aspose.Words
```

## Word दस्तावेज़ में बटन कैसे डालें

पहला कदम है एक नया `Document` और एक `DocumentBuilder` बनाना। बिल्डर कंटेंट जोड़ने का एंट्री पॉइंट है, जिसमें ActiveX कंट्रोल्स भी शामिल हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `Document` पूरे .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` `InsertParagraph` और `InsertFormField` जैसे हाई‑लेवल मेथड्स प्रदान करता है। एक साफ़ दस्तावेज़ से शुरू करने से बटन ठीक उसी जगह पर दिखाई देगा जहाँ आप चाहते हैं।

## Forms2OleControl के साथ बटन कंट्रोल बनाएं

अब हम वास्तविक बटन कंट्रोल बनाते हैं। `Forms2OleControl` वह क्लास है जिसे Aspose.Words सभी ActiveX ऑब्जेक्ट्स के लिए उपयोग करता है, और `COMMANDBUTTON` टाइप Word में एक क्लिक करने योग्य बटन के रूप में रेंडर होता है।

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Explanation:**  
* `InsertForms2OleControl` कंट्रोल को बिल्कुल वही कोऑर्डिनेट्स पर रखता है जो आप प्रदान करते हैं।  
* आकार पॉइंट्स में परिभाषित होता है (1 पॉइंट = 1/72 इंच)। इन संख्याओं को अपने लेआउट के अनुसार समायोजित करें।

## ActiveX कंट्रोल जोड़ें और इसे एक अनूठा नाम दें

हर ActiveX ऑब्जेक्ट का एक विशिष्ट नाम होना चाहिए ताकि आप बाद में (उदाहरण के लिए VBA में इवेंट्स हैंडल करते समय) उसे रेफ़र कर सकें।

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tip:** नाम में स्पेस या विशेष अक्षर न रखें; Word नाम को अपने आंतरिक फ़ॉर्म मॉडल में एक पहचानकर्ता के रूप में मानता है।

## ActiveX बटन पर बटन टेक्स्ट (कैप्शन) सेट करें

यहाँ वह जगह है जहाँ मुख्य कीवर्ड **set button text** काम आता है। `Caption` प्रॉपर्टी वह लेबल परिभाषित करती है जो उपयोगकर्ता बटन पर देखते हैं।

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

आप दस्तावेज़ सहेजने से पहले कभी भी कैप्शन बदल सकते हैं। यदि बाद में UI को लोकलाइज़ करना हो, तो बस `SetCaption` को एक अलग स्ट्रिंग के साथ फिर से कॉल करें।

## दस्तावेज़ सहेजें और परिणाम सत्यापित करें

अंत में, दस्तावेज़ को डिस्क पर लिखें। Microsoft Word में फ़ाइल खोलने पर बटन कस्टम कैप्शन के साथ दिखेगा।

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Expected output:** जब आप *ActiveXButton.docx* को Word में खोलेंगे, तो आप एक बटन देखेंगे जो निर्दिष्ट कोऑर्डिनेट्स पर स्थित है, लेबल **Click Me** के साथ। बटन पर क्लिक करने से डिफ़ॉल्ट Word कमांड बटन व्यवहार ट्रिगर होगा (जिसे आप बाद में VBA से कस्टमाइज़ कर सकते हैं)।

![बटन टेक्स्ट सेट करने का उदाहरण](https://example.com/activex-button.png){alt="बटन टेक्स्ट सेट करने का उदाहरण"}

## ActiveX बटन जोड़ें और इवेंट्स को हैंडल करें (वैकल्पिक)

यदि आपको बटन को कस्टम एक्शन करवाना है, तो आप एक VBA मैक्रो जोड़ सकते हैं जो `Click` इवेंट पर प्रतिक्रिया देता है। मैक्रो को प्रोग्रामेटिकली इंजेक्ट किया जा सकता है, लेकिन यह ट्यूटोरियल के दायरे से बाहर है। महत्वपूर्ण बात यह है कि बटन पहले से मौजूद है और उसकी कैप्शन सेट है—किसी भी इवेंट हैंडलिंग के लिए तैयार।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| बटन गलत संरेखित दिखाई देता है | निर्देशांक पॉइंट्स में हैं, पिक्सेल में नहीं | पिक्सेल मान को पॉइंट्स में बदलें (`points = pixels * 72 / DPI`) |
| सहेजने के बाद कैप्शन नहीं बदलता | `SetCaption` को `Save` के बाद कॉल किया गया | हमेशा `doc.Save` कॉल करने से **पहले** कैप्शन सेट करें |
| पुराने Word संस्करणों में कंट्रोल दिखाई नहीं देता | कुछ पुराने Word बिल्ड्स में पूर्ण ActiveX समर्थन नहीं होता | लक्षित Word संस्करण पर परीक्षण करें; फॉलबैक के रूप में `CheckBox` या `DropDownList` उपयोग करने पर विचार करें |
| आउटपुट में लाइसेंस चेतावनी | इवैल्यूएशन लाइसेंस समाप्त हो जाता है | वैध Aspose.Words लाइसेंस लागू करें: `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और रन कर सकते हैं। इसमें सभी आवश्यक `using` निर्देश शामिल हैं और दस्तावेज़ निर्माण से लेकर सहेजने तक का पूरा वर्कफ़्लो दर्शाया गया है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

प्रोग्राम को `dotnet run` के साथ चलाएँ। निष्पादन के बाद *ActiveXButton.docx* खोलें ताकि पुष्टि हो सके कि बटन की कैप्शन **Click Me** पढ़ती है।

## आपने क्या सीखा, उसका सारांश

* आपने Aspose.Words का उपयोग करके ActiveX बटन पर **set button text** कैसे सेट करें, सीखा।  
* आपने **how to insert button**, **create button control**, और **add activex control** को Word दस्तावेज़ में जोड़ने के सटीक चरण देखे।  
* अब आपके पास एक पुन: उपयोग योग्य कोड स्निपेट है जिसे आप किसी भी फॉर्म‑आधारित Word ऑटोमेशन प्रोजेक्ट के लिए अनुकूलित कर सकते हैं।

## अगले कदम

* `Forms2OleControlType` के अन्य मान जैसे `CHECKBOX` या `LISTBOX` का अन्वेषण करें ताकि अधिक समृद्ध फॉर्म बना सकें।  
* बटन को VBA मैक्रो के साथ मिलाकर गणना या डेटा वैधता कर सकते हैं।  
* दस्तावेज़ भरने के बाद उपयोगकर्ता इनपुट पढ़ने के लिए Aspose.Words का `FormField` API उपयोग करें।

डिज़ाइन आवश्यकताओं के अनुसार आकार, स्थिति और कैप्शन के साथ प्रयोग करने में संकोच न करें। यदि आपको कोई समस्या आती है, तो Aspose.Words दस्तावेज़ीकरण में प्रत्येक क्लास के लिए विस्तृत रेफ़रेंसेज़ उपलब्ध हैं।

Happy coding!


## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच का अन्वेषण कर सकें।

- [Aspose.Words के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Aspose.Words के साथ Word में Shape में शैडो जोड़ें – चरण‑दर‑चरण](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के फुटर में पेज नंबर जोड़ें](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}