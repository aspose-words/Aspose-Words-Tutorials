---
category: general
date: 2026-10-26
description: Aspose.Words का उपयोग करके C# में साधारण टेक्स्ट कंटेंट कंट्रोल कैसे
  डालें, सीखें। StructuredDocumentTag, शीर्षक और टैग आईडी को कवर करने वाला चरण‑दर‑चरण
  गाइड।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: hi
lastmod: 2026-10-26
og_description: Aspose.Words का उपयोग करके C# में प्लेन टेक्स्ट कंटेंट कंट्रोल डालें।
  शीर्षक, टैग आईडी जोड़ने और रूप को अनुकूलित करने के लिए इस गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: C# के साथ Word में सादा पाठ कंटेंट कंट्रोल डालें – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# के साथ Word दस्तावेज़ में प्लेन टेक्स्ट कंटेंट कंट्रोल कैसे डालें
url: /hi/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word दस्तावेज़ में प्लेन टेक्स्ट कंटेंट कंट्रोल डालें

यदि आपको Word फ़ाइल में **plain text content control** डालने की आवश्यकता है, तो यह ट्यूटोरियल Aspose.Words for .NET का उपयोग करके इसे बिल्कुल कैसे करना है दिखाता है। चाहे आप एक दस्तावेज़‑जनरेशन सेवा बना रहे हों या फ़ॉर्म निर्माण को स्वचालित कर रहे हों, नीचे दिए गए चरण आपको एक पुन: उपयोग योग्य, संपादन योग्य क्षेत्र जोड़ने की अनुमति देते हैं जिसे अंतिम उपयोगकर्ता भर सकते हैं।

आप सीखेंगे कि कैसे `Document` बनाएं, `DocumentBuilder` का उपयोग करके एक plain‑text Structured Document Tag (SDT) रखें, एक उपयोगकर्ता‑मित्र शीर्षक सेट करें, और एक अनूठा टैग पहचानकर्ता असाइन करें। गाइड सामान्य विविधताओं को भी समझाता है—जैसे दिखावट बदलना या कंट्रोल को नेस्ट करना—ताकि आप समाधान को किसी भी प्रोजेक्ट में अनुकूलित कर सकें।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- .NET 6.0 या बाद का संस्करण (कोड .NET Framework 4.6+ के साथ भी काम करता है)
- एक वैध Aspose.Words for .NET लाइसेंस (या एक मुफ्त इवैल्यूएशन की)
- Visual Studio 2022 या कोई भी C#‑संगत IDE
- C# सिंटैक्स की बुनियादी समझ

> **Pro tip:** यदि आप मुफ्त इवैल्यूएशन का उपयोग कर रहे हैं, तो याद रखें कि आउटपुट दस्तावेज़ में एक वॉटरमार्क होगा। लाइसेंस्ड संस्करण इसे स्वचालित रूप से हटा देता है।

## Aspose.Words का उपयोग करके प्लेन टेक्स्ट कंटेंट कंट्रोल कैसे डालें

समाधान का मूल तीन‑स्टेप प्रक्रिया है:

1. **`Document` और `DocumentBuilder` बनाएं।**  
2. **डिफ़ॉल्ट दिखावट के साथ एक प्लेन‑टेक्स्ट Structured Document Tag (SDT) डालें।**  
3. **SDT को एक शीर्षक और टैग पहचानकर्ता असाइन करें।**  

प्रत्येक चरण नीचे विस्तृत है, साथ में पूर्ण, चलाने योग्य कोड।

### चरण 1: दस्तावेज़ और बिल्डर को इनिशियलाइज़ करें

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` पूरे Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` ऐसी मेथड्स प्रदान करता है जैसे `InsertParagraph`, `InsertImage`, और, इस ट्यूटोरियल के लिए महत्वपूर्ण, `InsertStructuredDocumentTag`। इन्हें पहले इनिशियलाइज़ करने से आपको **plain text content control** रखने के लिए एक कैनवास मिल जाता है।

### चरण 2: प्लेन‑टेक्स्ट कंटेंट कंट्रोल (SDT) डालें

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` Aspose.Words को बताता है कि वह एक **plain text content control** बनाए, जो उपयोगकर्ताओं द्वारा संपादित किया जा सकने वाला साधारण टेक्स्ट बॉक्स जैसा व्यवहार करता है। `SdtAppearance.Default` कंट्रोल को हल्के बैकग्राउंड के साथ रेंडर करता है, जिससे दस्तावेज़ में यह स्पष्ट हो जाता है कि वह क्षेत्र संपादन योग्य है।

> **`SdtAppearance.Default` क्यों उपयोग करें?**  
> डिफ़ॉल्ट दिखावट Word के सभी संस्करणों में सबसे सार्वभौमिक संगत शैली है। यदि आपको बॉर्डर‑लेस लुक चाहिए, तो बाद में `SdtAppearance.Hidden` में बदल सकते हैं।

### चरण 3: शीर्षक और टैग पहचानकर्ता सेट करें

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) Word के *Content Controls* पैन में दिखता है, जिससे अंतिम उपयोगकर्ता फ़ील्ड के उद्देश्य को समझते हैं।  
- **Tag** (`sdt.Tag`) एक डेवलपर‑उन्मुख पहचानकर्ता है जिसे आप बाद में `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` के ज़रिए क्वेरी कर सकते हैं।  
- **PlaceholderName** ग्रे‑आउट गाइडेंस टेक्स्ट प्रदान करता है, जिससे उपयोगकर्ता अनुभव बेहतर होता है।

ऊपर दिया गया पूर्ण कोड स्निपेट एक स्व-निहित प्रोग्राम बनाता है जिसे आप कंपाइल और रन कर सकते हैं। निष्पादन के बाद, `output.docx` में एक ही प्लेन‑टेक्स्ट कंटेंट कंट्रोल होगा जिसका शीर्षक *MyTag* और टैग *TagId* होगा।

![Diagram showing insert plain text content control in a Word document](image.png){alt="Word दस्तावेज़ में प्लेन टेक्स्ट कंटेंट कंट्रोल डालने का आरेख"}

## StructuredDocumentTag (SDT) और उसकी प्रॉपर्टीज़ को समझना

एक **Structured Document Tag** (SDT) Word कंटेंट कंट्रोल्स के लिए आधारभूत ऑब्जेक्ट मॉडल है। प्लेन टेक्स्ट कंट्रोल डालने के लिए सबसे प्रासंगिक प्रॉपर्टीज़ हैं:

| प्रॉपर्टी | उद्देश्य | सामान्य मान |
|----------|----------|------------|
| `SdtType` | कंट्रोल का प्रकार निर्धारित करता है (plain text, rich text, picture, आदि) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | कंट्रोल की दृश्य शैली | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | *Content Controls* पैन में दिखने वाला मानव‑पठनीय नाम | कोई भी छोटा स्ट्रिंग |
| `Tag` | कोड में उपयोग होने वाला मशीन‑पठनीय पहचानकर्ता | अल्फ़ान्यूमेरिक स्ट्रिंग |
| `PlaceholderName` | कंट्रोल खाली होने पर दिखने वाला टेक्स्ट | कस्टम हिन्ट टेक्स्ट |

जब आप `SdtType.PlainText` सेट करते हैं, तो Word सामग्री को केवल साधारण अक्षरों तक सीमित कर देता है, जिससे रिच फ़ॉर्मेटिंग नहीं हो पाती। यह कंट्रोल *Name*, *Email*, या *Phone Number* जैसे सरल फ़ॉर्म फ़ील्ड्स के लिए आदर्श है।

### आपको जो विविधताएँ चाहिए हो सकती हैं

| परिदृश्य | कोड परिवर्तन |
|----------|--------------|
| **कोई दृश्य शेडिंग नहीं** (बॉर्डर‑लेस) | `Default` के बजाय `SdtAppearance.Hidden` उपयोग करें। |
| **रीड‑ओनली फ़ील्ड** | डालने के बाद `sdt.LockContentControl = true` सेट करें। |
| **डेटा से पहले‑भरण** | टैग बनाने के बाद `sdt.Text = "John Doe";` सेट करें। |
| **टेबल में कई कंट्रोल** | `InsertStructuredDocumentTag` कॉल से पहले `builder.InsertCell();` का उपयोग करके SDT को टेबल सेल के अंदर डालें। |

## सामान्य गड़बड़ियाँ और उनका समाधान

1. **शीर्षक सेट करना भूल जाना** – Word कंट्रोल बना देगा, लेकिन उपयोगकर्ता *Content Controls* पैन में कोई अर्थपूर्ण विवरण नहीं देख पाएंगे। हमेशा `sdt.Title` असाइन करें।  
2. **गलत `SdtType` का उपयोग** – यदि आपको plain text चाहिए लेकिन आप गलती से `RichText` चुन लेते हैं, तो कंट्रोल फ़ॉर्मेटिंग की अनुमति देगा, जिससे डाउनस्ट्रीम प्रोसेसिंग टूट सकती है। enum वैल्यू को दोबारा जांचें।  
3. **रीड‑ओनली फ़ोल्डर में सेव करना** – `doc.Save` कॉल `UnauthorizedAccessException` फेंकेगा। सुनिश्चित करें कि लक्ष्य डायरेक्टरी लिखने योग्य हो या परीक्षण के लिए `Path.GetTempPath()` उपयोग करें।  
4. **लाइसेंस लागू नहीं किया** – वैध लाइसेंस के बिना आउटपुट दस्तावेज़ में इवैल्यूएशन वॉटरमार्क रहेगा। अपने प्रोग्राम की शुरुआत में लाइसेंस लागू करें:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है, जिसे आप नई कंसोल प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**अपेक्षित आउटपुट:** `output.docx` को Microsoft Word में खोलने पर एक पंक्ति टेक्स्ट *“Please fill in the following field:”* के बाद एक हल्के‑ग्रे बॉक्स्ड क्षेत्र दिखेगा जिसका लेबल *MyTag* होगा। प्लेसहोल्डर *Enter your text here* हल्के ग्रे में दिखेगा जब तक उपयोगकर्ता टाइप नहीं करता।

## निष्कर्ष

अब आप जानते हैं कि **plain text content control** को Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कैसे डालें। ट्यूटोरियल ने `Document` को इनिशियलाइज़ करना, `PlainText` प्रकार का `StructuredDocumentTag` डालना, और उसके शीर्षक, टैग, तथा प्लेसहोल्डर को कस्टमाइज़ करना कवर किया। `SdtAppearance` विकल्पों और सामान्य गड़बड़ियों को समझकर आप फ़ॉर्म, टेम्प्लेट, और स्वचालित रिपोर्ट्स बना सकते हैं जो संपादन योग्य कंट्रोल्स पर निर्भर होते हैं।

### आगे क्या सीखें?

- `RichText` या `ComboBox` जैसे अन्य SDT प्रकारों की खोज करें जो ड्रॉपडाउन प्रदान करते हैं।  
- टेबल्स के अंदर कई कंट्रोल्स को मिलाएँ या `RepeatingSection` का उपयोग करके उन्हें दोहराएँ।  
- `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` का उपयोग करके कंट्रोल वैल्यूज़ को प्रोग्रामेटिक रूप से पढ़ें या बदलें।

इन विविधताओं के साथ प्रयोग करने में संकोच न करें, और इस पैटर्न को अपने बड़े दस्तावेज़‑जनरेशन पाइपलाइन में इंटीग्रेट करें। हैप्पी कोडिंग!

## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [How to create content control in C# with Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}