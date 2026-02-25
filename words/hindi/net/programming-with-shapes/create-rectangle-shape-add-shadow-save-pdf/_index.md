---
category: general
date: 2026-02-24
description: C# में Aspose.Words का उपयोग करके आयताकार आकार बनाएं, आकार में शैडो जोड़ें,
  और दस्तावेज़ को PDF के रूप में सहेजें। मिनटों में शैडो कैसे जोड़ें और PDF कैसे सहेजें,
  यह सीखें।
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: hi
og_description: Aspose.Words के साथ C# में आयताकार आकार बनाएं, फिर आकार में छाया जोड़ें
  और दस्तावेज़ को PDF के रूप में सहेजें – एक पूर्ण, चरण‑दर‑चरण मार्गदर्शिका।
og_title: आयताकार आकार बनाएं, छाया जोड़ें और PDF सहेजें
tags:
- Aspose.Words
- C#
- PDF generation
title: आयताकार आकार बनाएं, छाया जोड़ें और PDF सहेजें
url: /hi/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

? The instruction: translate all text content naturally to Hindi, keep technical terms in English. "create rectangle shape" is a phrase but could be considered technical. Might be okay to translate. But maybe better to keep as is? The original bold text includes "create rectangle shape". If we translate to Hindi inside bold, it's okay. Similarly "save document as PDF". Could keep as is. I think it's fine.

Now produce final content with all translations.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# आयताकार आकार बनाएं, शैडो जोड़ें और PDF सहेजें

क्या आपको कभी Word दस्तावेज़ में **आयताकार आकार बनाना** पड़ा है लेकिन साथ ही एक सुंदर ड्रॉप शैडो और PDF आउटपुट चाहिए था? आप अकेले नहीं हैं। कई रिपोर्टिंग या इनवॉइस‑जनरेशन प्रोजेक्ट्स में विज़ुअल पॉलिश—जैसे एक सूक्ष्म शैडो—“सिर्फ एक और फ़ाइल” और “प्रोफ़ेशनल‑ग्रेड दस्तावेज़” के बीच अंतर बनाता है।  

इस ट्यूटोरियल में हम ठीक यही करेंगे: **Aspose.Words for .NET** का उपयोग करके आयताकार आकार बनाना, आकार में शैडो जोड़ना, और अंत में **दस्तावेज़ को PDF के रूप में सहेजना**। अंत तक आपके पास एक तैयार‑चलाने योग्य C# कंसोल ऐप होगा जो शेडेड आयताकार के साथ PDF उत्पन्न करता है, और आप समझेंगे कि शैडो को कैसे ट्यून किया जाए या एक्सपोर्ट विकल्पों को कैसे बदला जाए।  

## आपको क्या चाहिए

- .NET 6 SDK (या कोई भी नवीनतम .NET संस्करण) – API .NET Framework 4.x पर भी समान रूप से काम करता है।  
- Aspose.Words for .NET NuGet पैकेज (`Aspose.Words`) – इसे `dotnet add package Aspose.Words` से स्थापित करें।  
- एक कोड एडिटर – Visual Studio, VS Code, या Rider पर्याप्त हैं।  

इस उदाहरण के लिए कोई अतिरिक्त लाइसेंसिंग कदम नहीं हैं; फ्री इवैल्यूएशन मोड PDF आउटपुट देखने के लिए पर्याप्त है।  

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेस इम्पोर्ट करें

सबसे पहले, चलिए एक कंसोल प्रोजेक्ट बनाते हैं और उन क्लासेज़ को इम्पोर्ट करते हैं जिनकी हमें आवश्यकता होगी।

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*क्यों यह महत्वपूर्ण है:* `Document` और `DocumentBuilder` हमें कैनवास देते हैं, जबकि `Shape` और `ShadowFormat` हमें आयताकार को ड्रॉ और स्टाइल करने देते हैं। इन्हें पहले इम्पोर्ट करने से बाद का कोड साफ़ रहता है।  

## चरण 2: इच्छित आयामों के साथ **आयताकार आकार बनाएं**

अब हम वास्तव में एक खाली दस्तावेज़ बनाते हैं और उसमें आयताकार डालते हैं। देखें कि `InsertShape` मेथड एक `Shape` ऑब्जेक्ट लौटाता है जिसे हम तुरंत स्टाइल कर सकते हैं।

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*व्याख्या*: आकार पॉइंट्स में व्यक्त किया जाता है (1 pt = 1/72 in)। अपने लेआउट के अनुसार संख्याओं को समायोजित करें। हम आकार को हल्के‑नीले रंग से भरते हैं ताकि शैडो स्पष्ट दिखे।  

## चरण 3: **आकार में शैडो जोड़ें** – प्रभाव को बारीकी से समायोजित करें

शैडो केवल “ऑन/ऑफ़” नहीं है। आप इसके रंग, ब्लर, दूरी, दिशा, और यहाँ तक कि ट्रांसपेरेंसी को भी नियंत्रित कर सकते हैं। यहाँ एक व्यावहारिक कॉन्फ़िगरेशन है जो अधिकांश रिपोर्ट्स के लिए अच्छा काम करता है।

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*आप इन मानों को क्यों बदल सकते हैं:*  
- **BlurRadius** – सपनीला प्रभाव के लिए बढ़ाएँ, तेज़ किनारा के लिए घटाएँ।  
- **Direction** – 0° दाएँ की ओर, 90° नीचे, 180° बाएँ, आदि। अपने पेज लेआउट के अनुसार घुमाएँ।  
- **Transparency** – ठोस शैडो के लिए `0` सेट करें, आधा‑ट्रांसपेरेंट के लिए `0.5` आदि।  

### शैडो कैसे जोड़ें – वैकल्पिक तरीके

यदि आपको **मल्टी‑लेयर शैडो** चाहिए (जैसे, एक गहरा बाहरी शैडो और एक हल्का आंतरिक शैडो), तो आप दूसरा आकार बना सकते हैं, उसे ऑफ़सेट कर सकते हैं, और अलग `ShadowFormat` सेट कर सकते हैं। या, तेज़ “नो‑ब्लर” लुक के लिए, `BlurRadius = 0` सेट करें।  

## चरण 4: **दस्तावेज़ को PDF के रूप में सहेजें** – अंतिम एक्सपोर्ट

आयताकार और उसका शैडो तैयार होने के बाद, अंतिम चरण फ़ाइल को PDF के रूप में लिखना है। Aspose.Words आंतरिक रूप से रूपांतरण संभालता है; आपको बस इच्छित फ़ॉर्मेट के साथ `Save` कॉल करना है।

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*टिप्पणी*: यदि आपको PDF अनुपालन (PDF/A, PDF/X) नियंत्रित करना है या फ़ॉन्ट एम्बेड करना है, तो एक ओवरलोड का उपयोग करें:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

यही **PDF कैसे सहेजें** का सारांश है।  

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम है जिसे आप `Program.cs` में कॉपी‑पेस्ट कर सकते हैं। यह जैसा है वैसा ही कम्पाइल और रन करता है (सिर्फ यह सुनिश्चित करें कि आउटपुट फ़ोल्डर मौजूद है)।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### अपेक्षित परिणाम

जनरेट किए गए `ShadowRectangle.pdf` को खोलें। आपको एक पेज पर हल्के‑नीले आयताकार, 45° नीचे‑दाएँ ऑफ़सेट वाला नरम ग्रे शैडो, और साफ़ किनारे दिखेंगे। PDF किसी भी आधुनिक रीडर (Adobe Acrobat, Edge, Chrome) में देखी जा सकती है।

![PDF में शैडो के साथ आयताकार आकार बनाएं](/images/shadow-rectangle.png "शैडो के साथ आयताकार आकार बनाएं")

*(इमेज़ का alt टेक्स्ट मुख्य कीवर्ड को SEO के लिए शामिल करता है।)*  

## सामान्य प्रश्न और किनारे‑के‑केस हैंडलिंग

**यदि PDF में शैडो गायब हो जाए तो क्या करें?**  
सुनिश्चित करें कि आप Aspose.Words का नवीनतम संस्करण (≥23.3) उपयोग कर रहे हैं। पुराने बिल्ड्स में एक बग था जहाँ कुछ शैडो प्रॉपर्टीज़ PDF रूपांतरण के दौरान अनदेखी हो जाती थीं।  

**क्या मैं शैडो का रंग अपने ब्रांड के अनुसार बदल सकता हूँ?**  
बिल्कुल—सिर्फ `System.Drawing.Color.Gray` को अपनी पसंद के किसी भी `Color` से बदल दें, जैसे `Color.FromArgb(128, 0, 0, 255)` से एक अर्ध‑पारदर्शी नीला।  

**मैं अन्य आकारों (एलिप्स, स्टार, आदि) में शैडो कैसे जोड़ूँ?**  
एक ही `ShadowFormat` किसी भी `Shape` ऑब्जेक्ट के लिए काम करता है। आकार बनाने के बाद, उसका `ShadowFormat` प्राप्त करें और प्रॉपर्टीज़ सेट करें।  

**DPI या स्केलिंग समस्याओं के बारे में क्या?**  
PDF रेंडरिंग आकार के पॉइंट साइज का सम्मान करती है। यदि आपको उच्च‑रिज़ॉल्यूशन आउटपुट चाहिए (प्रिंटिंग के लिए), तो आकार के आयामों को उसी अनुसार समायोजित करें या `PdfSaveOptions.ImageResolution` सेट करें।  

**क्या मैं अन्य फ़ॉर्मेट्स, जैसे PNG, में एक्सपोर्ट कर सकता हूँ?**  
हां—सिर्फ `document.Save("output.png", SaveFormat.Png)` कॉल करें। शैडो समान तरीके से रेंडर होगा।  

## प्रो टिप्स और बेस्ट प्रैक्टिसेज़

- **बिल्डर को पुनः उपयोग करें**: यदि आप कई आकार जोड़ रहे हैं, तो एक ही `DocumentBuilder` इंस्टेंस रखें; कई बनाने की तुलना में यह सस्ता पड़ता है।  
- **बैच सेविंग**: लूप में कई PDFs जनरेट करते समय, `PdfSaveOptions` ऑब्जेक्ट को पुनः उपयोग करें ताकि बार‑बार अलोकेशन से बचा जा सके।  
- **टेस्टिंग**: सहेजने के बाद हमेशा PDF खोलें ताकि यह पुष्टि हो सके कि शैडो अपेक्षित रूप से दिख रहा है। कुछ PDF व्यूअर्स शैडो को थोड़ा अलग रेंडर करते हैं; Adobe Acrobat सबसे भरोसेमंद रेफ़रेंस है।  
- **परफ़ॉर्मेंस**: बड़े दस्तावेज़ों के लिए, यदि आवश्यक न हो तो `builder.PageSetup.DifferentFirstPageHeaderFooter = false` सेट करके `DocumentBuilder.InsertShape` की ऑटोमैटिक पेज ब्रेक्स को डिसेबल करें।  

## निष्कर्ष

हमने Aspose.Words for .NET का उपयोग करके **आयताकार आकार बनाना**, **आकार में शैडो जोड़ना**, और **दस्तावेज़ को PDF के रूप में सहेजना** के लिए सभी आवश्यक चीज़ें कवर कर ली हैं। कोड कॉम्पैक्ट है, अवधारणाएँ समझाई गई हैं, और अब आपके पास अन्य आकारों, शैडो स्टाइल्स, और एक्सपोर्ट विकल्पों के साथ प्रयोग करने की ठोस नींव है।  

अगला कदम? आयताकार को गोल‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}