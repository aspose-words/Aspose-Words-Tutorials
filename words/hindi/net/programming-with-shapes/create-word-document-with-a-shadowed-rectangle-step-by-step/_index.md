---
category: general
date: 2026-01-13
description: Aspose.Words का उपयोग करके वर्ड दस्तावेज़ बनाएं और सीखें कि कैसे आयताकार
  आकार डालें, छाया जोड़ें, और C# में आकार की छाया जोड़ें। पूर्ण उदाहरण शामिल है।
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: hi
og_description: Aspose.Words के साथ वर्ड दस्तावेज़ बनाएं, देखें कि आयताकार आकार कैसे
  डालें और छाया कैसे जोड़ें। पूर्ण C# उदाहरण का पालन करें।
og_title: छायांकित आयत के साथ वर्ड दस्तावेज़ बनाएं – पूर्ण ट्यूटोरियल
tags:
- Aspose.Words
- C#
- Document Automation
title: छाया वाले आयत के साथ वर्ड दस्तावेज़ बनाएं – चरण-दर-चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# शैडो वाले आयत के साथ Word Document बनाएं – चरण‑दर‑चरण गाइड

क्या आपको कभी **create word document** चाहिए था जिसमें एक सुंदर शेडेड आयत हो, लेकिन आप नहीं जानते थे कहाँ से शुरू करें? आप अकेले नहीं हैं—कई डेवलपर्स को Aspose.Words के साथ पहली बार काम करते समय यही समस्या आती है।  

इस ट्यूटोरियल में हम आपको प्रोग्रामेटिक रूप से **create word document** करने, **insert rectangle shape** करने, और **how to add shadow** दिखाने की पूरी प्रक्रिया बताएँगे, ताकि शैप वास्तव में उभरे। अंत तक आपके पास एक तैयार‑चलाने‑योग्य C# स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

## आप क्या सीखेंगे

- एक Word फ़ाइल में **how to insert shape** (आयत) डालने का सटीक कोड।  
- **add shape shadow** करने और उसकी उपस्थिति को नियंत्रित करने के लिए आवश्यक प्रॉपर्टीज़।  
- परिणाम को सेव करना और यह सत्यापित करना कि शैडो दिखाई दे रहा है।  
- कुछ व्यावहारिक टिप्स और एज‑केस नोट्स जो बाद में सिरदर्द बचाते हैं।

कोई बाहरी दस्तावेज़ आवश्यक नहीं—सब कुछ यहाँ है।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

1. **.NET 6.0** (या कोई भी हालिया .NET संस्करण) स्थापित।  
2. Aspose.Words for .NET का **license**, या परीक्षण के लिए मुफ्त इवैल्यूएशन मोड।  
3. एक विकास वातावरण—Visual Studio 2022 बहुत अच्छा है, लेकिन कोई भी एडिटर जो C# कंपाइल कर सके, चलेगा।

बस इतना ही। `Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## चरण 1 – प्रोजेक्ट सेट अप करें और Aspose.Words को रेफ़रेंस करें

पहले, एक नया कंसोल ऐप बनाएं और Aspose.Words पैकेज जोड़ें:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** यदि आप फ्री ट्रायल उपयोग कर रहे हैं, तो `License.SetLicense` को अपने लाइसेंस फ़ाइल के साथ कॉल करना याद रखें; अन्यथा लाइब्रेरी वॉटरमार्क जोड़ देगी।

## चरण 2 – Document Builder को इनिशियलाइज़ करें

अब हम वास्तविक **create word document** प्रक्रिया शुरू करेंगे। `Document` क्लास हमें एक खाली कैनवास देती है, और `DocumentBuilder` उस पर पेंट करने की सुविधा देता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

हमें बिल्डर की जरूरत क्यों है? यह लो‑लेवल OpenXML विवरणों को एब्स्ट्रैक्ट करता है, ताकि आप *क्या* करना चाहते हैं उस पर ध्यान दे सकें, न कि *कैसे* फ़ाइल संरचित है। यही **how to insert shape** को जल्दी करने का मूल है।

## चरण 3 – आयत (Rectangle) Shape डालें

अब हम वास्तव में **insert rectangle shape** करेंगे। आयत का आकार 150 × 100 पॉइंट होगा (लगभग 2 इंच × 1.3 इंच)।

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

`InsertShape` मेथड एक `Shape` ऑब्जेक्ट रिटर्न करता है, जिसे हम आगे कस्टमाइज़ कर सकते हैं। इस चरण पर आयत सिर्फ एक सॉलिड सफ़ेद बॉक्स है—अभी तक कोई शैडो नहीं।

## चरण 4 – शैडो कैसे जोड़ें (Add Shape Shadow)

एक शैडो जोड़ना बहुत आसान है जब आप जानते हैं किन प्रॉपर्टीज़ को बदलना है। `ShadowFormat` ऑब्जेक्ट विज़िबिलिटी, कलर, ब्लर, ऑफ़सेट, और साइज को नियंत्रित करता है।

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

यह ब्लॉक **how to add shadow** को साधारण अंग्रेज़ी में समझाता है: इसे ऑन करें, रंग चुनें, ट्रांसपैरेंसी, ऑफ़सेट, ब्लर, और साइज को ट्यून करें। आप इन नंबरों के साथ प्रयोग करके भारी ड्रॉप‑शैडो या हल्की फुसफुसाती शैडो बना सकते हैं।

### सामान्य वैरिएशन

- **विभिन्न रंग:** क्लासिक ड्रॉप शैडो के लिए `Color.Black` उपयोग करें, या स्टाइलिश इफ़ेक्ट के लिए `Color.BlueViolet`।  
- **शून्य ब्लर:** `BlurRadius = 0` सेट करने से तेज़, स्पष्ट किनारा मिलेगा।  
- **बड़े ऑफ़सेट:** `OffsetX`/`OffsetY` को बढ़ाकर शैडो को आकार से दूर धकेलें।

## चरण 5 – दस्तावेज़ को सेव करें और सत्यापित करें

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल एक सामान्य `.docx` होगी जिसे कोई भी आधुनिक वर्ड प्रोसेसर खोल सकता है।

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

परिणामस्वरूप *ShadowRectangle.docx* को Microsoft Word में खोलें। आपको एक आयत के साथ नरम ग्रे शैडो नीचे‑दाएँ तरफ़ ऑफ़सेटेड दिखेगा—बिल्कुल वही जो कोड ने निर्दिष्ट किया था।

> **Expected output:** एक सिंगल‑पेज Word फ़ाइल जिसमें 150 × 100‑पॉइंट आयत हो, 30 % ट्रांसपेरेंट ग्रे शैडो हो, 5 pts ऑफ़सेट, 4 pts ब्लर, और आकार 75 % हो।

## पूर्ण कार्यशील उदाहरण

सब कुछ मिलाकर, यहाँ पूरा, तैयार‑चलाने‑योग्य प्रोग्राम है:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

प्रोग्राम चलाएँ (`dotnet run`) आपको एक नया Word फ़ाइल मिलेगा जिसमें सुंदर शैडो वाला आयत होगा—रिपोर्ट, सर्टिफ़िकेट, या किसी भी विज़ुअल क्यू के लिए परफ़ेक्ट।

## अक्सर पूछे जाने वाले प्रश्न (FAQs)

**Q: क्या मैं अन्य शैप (ellipse, star) डाल सकता हूँ और वही शैडो कोड उपयोग कर सकता हूँ?**  
A: बिल्कुल। `InsertShape` मेथड किसी भी `ShapeType` एन्‍यूम वैल्यू को स्वीकार करता है। एक बार आपके पास `Shape` इंस्टेंस हो, `ShadowFormat` प्रॉपर्टीज़ समान रूप से काम करती हैं, इसलिए **how to add shadow** शैप‑निर्भर नहीं है।

**Q: अगर मुझे शैडो दोनों तरफ चाहिए तो?**  
A: Aspose.Words प्रति शैप केवल एक ड्रॉप शैडो सपोर्ट करता है। डबल‑साइड इफ़ेक्ट सिम्युलेट करने के लिए शैप को डुप्लिकेट करें, प्रत्येक कॉपी को अलग‑अलग ऑफ़सेट दें, और एक की `ShadowFormat.Visible` को `false` रखें जबकि दूसरे की शैडो को विज़िबल रखें।

**Q: क्या यह .NET Framework 4.8 पर काम करता है?**  
A: हाँ। API संस्करण‑निर्पेक्ष है; बस अपने टार्गेट फ्रेमवर्क के लिए उपयुक्त Aspose.Words DLL रेफ़रेंस करें।

## टिप्स & पिटफ़ॉल्स

- **`Visible = true` सेट करना न भूलें**—अन्यथा शैडो प्रॉपर्टीज़ इग्नोर हो जाएँगी।  
- **ट्रांसपैरेंसी वैल्यू 0.0 (ऑपेक) से 1.0 (पूरी तरह ट्रांसपेरेंट) तक होती है।** आम गलती `30` के बजाय `0.3` उपयोग करना है।  
- **रीड‑ओनली फ़ोल्डर में सेव करने से एक्सेप्शन फेंकेगा।** सुनिश्चित करें कि आउटपुट डायरेक्टरी राइटेबल है।

## अगले कदम

अब जब आप **how to insert shape**, **add shape shadow**, और Aspose.Words के साथ **create word document** करना जानते हैं, तो आप आगे देख सकते हैं:

- आयत के अंदर **टेक्स्ट जोड़ना** `builder.InsertParagraph()` का उपयोग करके शैप डालने से पहले।  
- अधिक रिच विज़ुअल स्टाइलिंग के लिए **gradient fills** या **patterned borders** लागू करना।  
- कई पेज़ जेनरेट करना, प्रत्येक में अलग‑शेडेड शैप, ताकि डायनामिक रिपोर्ट बन सके।

बिना हिचकिचाहट प्रयोग करें—शैडो का रंग, ब्लर, या साइज बदलने से आपके दस्तावेज़ का लुक काफी बदल सकता है।

---

*प्रोडक्शन में डालने के लिए तैयार? कोड को पकड़ें, पैरामीटर बदलें, और देखें कि आपके Word फ़ाइल सेकंडों में प्रोफेशनल लुक पा रहे हैं।*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}