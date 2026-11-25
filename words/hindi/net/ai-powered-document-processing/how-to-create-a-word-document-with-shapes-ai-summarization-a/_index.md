---
category: general
date: 2026-11-25
description: Word दस्तावेज़ बनाना, आयताकार आकार जोड़ना, AI के साथ दस्तावेज़ का सारांश
  बनाना, AI का उपयोग करके पाठ का अनुवाद करना, और Aspose.Words का उपयोग करके दस्तावेज़
  को DOCX के रूप में सहेजना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: hi
lastmod: 2026-11-25
og_description: एक Word दस्तावेज़ बनाएं, आयताकार आकार जोड़ें, AI से दस्तावेज़ का सारांश
  बनाएं, AI से टेक्स्ट का अनुवाद करें, और दस्तावेज़ को DOCX के रूप में सहेजें—सभी
  एक ही C# ट्यूटोरियल में।
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: C# में आकृतियों, AI सारांश और अनुवाद के साथ एक Word दस्तावेज़ बनाएं
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: C# में आकार, AI सारांश और अनुवाद के साथ Word दस्तावेज़ कैसे बनाएं
url: /hi/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में आकार, AI सारांश और अनुवाद के साथ Word दस्तावेज़ कैसे बनाएं

यदि आपको प्रोग्रामेटिकली **Word दस्तावेज़ बनाना** है, तो यह गाइड आपको बिल्कुल दिखाएगा कि कैसे। Aspose.Words for .NET का उपयोग करके आप **add rectangle shape**, AI सेवा को बुलाकर **summarize document with AI**, पैराग्राफ को **translate text using AI**, और अंत में **save document as DOCX** सीखेंगे।

बहुत से डेवलपर्स को डॉक्यूमेंट ऑटोमेशन और आधुनिक AI सुविधाओं को एक साथ जोड़ने में कठिनाई होती है। इस ट्यूटोरियल के अंत तक आपके पास एक एकल, स्वतंत्र C# प्रोजेक्ट होगा जो पूरी तरह फॉर्मेटेड *.docx* फ़ाइल बनाता है, जिसमें एक विज़ुअल आकार, AI‑जनित सारांश, और बहुभाषी सामग्री शामिल होगी।

## आवश्यकताएँ

- .NET 6.0 SDK या बाद का संस्करण स्थापित हो  
- Visual Studio 2022 (या कोई भी C# IDE)  
- Aspose.Words for .NET लाइसेंस (या एक मुफ्त इवैल्यूएशन की)  
- AI सारांश और अनुवाद कॉल के लिए इंटरनेट कनेक्शन  

`Aspose.Words` और `Aspose.Words.AI` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## चरण 1: प्रोजेक्ट सेट अप करें और आवश्यक पैकेज जोड़ें

एक नया कंसोल प्रोजेक्ट बनाएं और Aspose.Words लाइब्रेरीज़ को जोड़ें।

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** यदि आप इवैल्यूएशन मोड का उपयोग करने की योजना बना रहे हैं, तो `Main` में शुरुआती चरण में `Aspose.Words.License.SetLicense("Aspose.Words.lic");` कॉल करें ताकि वॉटरमार्क न आएँ।

## चरण 2: डॉक्यूमेंट को इनिशियलाइज़ करें – **create word document** का मूल

कोड की पहली कार्यात्मक पंक्ति एक नया **Word दस्तावेज़** ऑब्जेक्ट बनाती है। यह ऑब्जेक्ट सभी बाद की ऑपरेशन्स के लिए कैनवास है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` टेक्स्ट, आकार और कंट्रोल्स को मैन्युअल रूप से लो‑लेवल नोड ट्रीज़ को संभाले बिना सम्मिलित करना आसान बनाता है।

## चरण 3: डॉक्यूमेंट में **Add rectangle shape** जोड़ें

एक rectangle shape को विज़ुअल प्लेसहोल्डर, लेबल बैकग्राउंड, या साधारण ग्राफ़िक के रूप में उपयोग किया जा सकता है। हम पहले एक `GroupShape` बनाते हैं, फिर उसके अंदर एक `Rectangle` डालते हैं।

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

यह rectangle 100 पॉइंट चौड़ा और 50 पॉइंट ऊँचा है। क्योंकि यह एक `GroupShape` के अंदर रहता है, आप बाद में अधिक तत्व (जैसे टेक्स्ट बॉक्स) जोड़ सकते हैं बिना लेआउट टकराव की चिंता किए।

## चरण 4: एक plain‑text StructuredDocumentTag (SDT) डालें

StructuredDocumentTag ऑब्जेक्ट्स कंटेंट कंट्रोल्स के लिए उपयोगी होते हैं जिन्हें बाद में डेटा स्रोतों से बाइंड किया जा सकता है।

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

`true` फ़्लैग टैग को **repeating** कंट्रोल के रूप में चिह्नित करता है, जो टेम्प्लेट्स के लिए उपयोगी है।

## चरण 5: एक ActiveX CommandButton कंट्रोल जोड़ें (वैकल्पिक UI)

यदि उत्पन्न दस्तावेज़ ऐसे वातावरण में उपयोग होगा जो ActiveX को सपोर्ट करता है, तो आप एक बटन एम्बेड कर सकते हैं।

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

यह चरण वैकल्पिक है; यदि आपका लक्षित दर्शक विंडोज़ वातावरण में दस्तावेज़ के साथ कभी इंटरैक्ट नहीं करता, तो आप इसे हटा सकते हैं।

## चरण 6: **Summarize document with AI** करें

Aspose.Words.AI बड़े‑भाषा‑मॉडल सेवाओं के चारों ओर एक सुविधाजनक रैपर प्रदान करता है। यहाँ हम OpenAI बैकएंड के साथ `DocumentSummarizer.Summarize` को कॉल करते हैं।

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

यह मेथड वर्तमान नोड ट्री का विश्लेषण करता है, सबसे प्रासंगिक वाक्यों को निकालता है, और एक संक्षिप्त पैराग्राफ लौटाता है। यह **summarize document with AI** कार्यक्षमता का मूल है।

## चरण 7: **Translate text using AI** करें

अब हम दिखाते हैं कि कैसे एक नमूना स्ट्रिंग को अंग्रेज़ी से फ़्रेंच में अनुवादित किया जाए। `Translator.Translate` मेथड आंतरिक रूप से एक Google AI मॉडल को कॉल करता है।

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

आप `Language.French` को किसी भी समर्थित भाषा enum मान से बदल सकते हैं, जिससे ऑन‑द‑फ्लाई बहुभाषी दस्तावेज़ निर्माण संभव हो जाता है।

## चरण 8: **Save document as DOCX** करें

अंत में, संपादित दस्तावेज़ को डिस्क पर सहेजें। जब आप `.docx` एक्सटेंशन निर्दिष्ट करते हैं, तो `Save` मेथड स्वचालित रूप से एक *.docx* फ़ाइल लिखता है।

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

फ़ाइल `Result.docx` अब इसमें शामिल है:

- एक group shape के अंदर rectangle shape  
- एक plain‑text कंटेंट कंट्रोल (SDT)  
- एक ActiveX CommandButton (यदि आपने चरण 5 रखा है)  
- एक AI‑जनित सारांश पैराग्राफ  
- “Hello world” का फ़्रेंच अनुवाद

आप Microsoft Word में फ़ाइल खोलकर प्रत्येक तत्व की पुष्टि कर सकते हैं।

## पूर्ण स्रोत कोड

नीचे पूरा, तैयार‑चलाने‑योग्य प्रोग्राम दिया गया है। इसे `Program.cs` में कॉपी करें और `dotnet run` चलाएँ।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### अपेक्षित आउटपुट

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

जब आप `Result.docx` खोलेंगे, तो आपको शीर्ष के पास rectangle shape, SDT प्लेसहोल्डर, बटन, सारांश पैराग्राफ, और फ़्रेंच अनुवाद plain text के रूप में सम्मिलित दिखेगा।

## निष्कर्ष

अब आप जानते हैं कि कैसे **शुरू से एक Word दस्तावेज़ बनाएं**, **rectangle shape जोड़ें**, **AI के साथ दस्तावेज़ का सारांश बनाएं**, **AI के साथ टेक्स्ट अनुवाद करें**, और **डॉक्यूमेंट को DOCX के रूप में सहेजें**—सभी कुछ संक्षिप्त C# लाइनों से। यह पैटर्न स्केलेबल है: आप हार्ड‑कोडेड स्ट्रिंग्स को डायनामिक डेटा से बदल सकते हैं, अधिक आकार या चार्ट जोड़ सकते हैं, और `SummarizerOptions` या `Translator` पैरामीटर को समायोजित करके AI प्रदाता बदल सकते हैं।

### आगे क्या?

- **add rectangle shape** के विभिन्न रूपों का अन्वेषण करें: भरने का रंग, लाइन स्टाइल बदलें, या आकार के अंदर टेक्स्ट जोड़ें।  
- बड़े दस्तावेज़ों पर **summarize document with AI** का उपयोग करके स्वचालित रूप से एग्जीक्यूटिव सारांश बनाएं।  
- **translate text using AI** को विस्तारित करके पूरे पैराग्राफ या टेबल को बैच‑प्रोसेस करें और बहुभाषी रिपोर्ट बनाएं।  
- Aspose.Words चार्टिंग APIs को मिलाकर AI‑जनित अंतर्दृष्टियों के साथ डेटा विज़ुअलाइज़ेशन एम्बेड करें।  

बिना झिझक प्रयोग करें, और अपने परिणाम कमेंट्स में या GitHub पर साझा करें। कोडिंग का आनंद लें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट‑संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच खोजने में मदद करती हैं।

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}