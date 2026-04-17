---
category: general
date: 2026-03-01
description: Aspose.Words का उपयोग करके PDF में जल्दी से आयत जोड़ें। शैप PDF डालना
  सीखें, PDF में ग्राफ़िक्स जोड़ें, और कस्टम शैडो के साथ प्रोग्रामेटिकली PDF दस्तावेज़
  बनाएं।
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: hi
og_description: Aspose.Words का उपयोग करके PDF में आयत जोड़ें। यह ट्यूटोरियल दिखाता
  है कि कैसे शैप PDF डालें, PDF में ग्राफ़िक्स जोड़ें, और C# में प्रोग्रामेटिकली PDF
  दस्तावेज़ बनाएं।
og_title: Aspose.Words के साथ PDF में आयत जोड़ें – पूर्ण गाइड
tags:
- pdf
- aspnet
- csharp
- graphics
title: Aspose.Words के साथ PDF में आयत जोड़ें – चरण‑दर‑चरण गाइड
url: /hi/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ PDF में आयत जोड़ें – पूर्ण गाइड

क्या आपको कभी **add rectangle to PDF** करने की ज़रूरत पड़ी है लेकिन यह नहीं पता था कि कौन सा API कॉल काम करेगा? आप अकेले नहीं हैं—डेवलपर्स लगातार पूछते रहते हैं, “मैं PDF में shape कैसे insert करूँ और फ़ाइल को हल्का रखूँ?” अच्छी खबर यह है कि Aspose.Words इसे बहुत आसान बनाता है। इस ट्यूटोरियल में हम पूरी प्रक्रिया को देखेंगे, प्रोग्रामेटिकली PDF दस्तावेज़ बनाने से लेकर आयत को शैडो के साथ स्टाइल करने तक।

हम कुछ अतिरिक्त चीज़ें भी जोड़ेंगे: आप सीखेंगे कि **add graphics to PDF** कैसे किया जाता है, **insert shape PDF** के सटीक कदम देखेंगे, और एक तैयार‑चलाने‑योग्य उदाहरण के साथ समाप्त करेंगे जो **creates PDF with shape** बनाता है। कोई बाहरी संदर्भ नहीं, सिर्फ एक स्व-समाहित समाधान जिसे आप आज ही कॉपी‑पेस्ट कर सकते हैं।

## आवश्यकताएँ

- .NET 6.0 या बाद का संस्करण (Aspose.Words .NET Standard 2.0+ के साथ काम करता है)
- एक वैध Aspose.Words for .NET लाइसेंस या अस्थायी इवैल्यूएशन कुंजी
- Visual Studio 2022 (या आपका पसंदीदा कोई भी IDE)
- बेसिक C# ज्ञान—कुछ विशेष नहीं, बस एक कंसोल ऐप चलाने की क्षमता

बस इतना ही। यदि आपके पास ये सब है, तो आप शुरू करने के लिए तैयार हैं।

## चरण 1: प्रोग्रामेटिकली PDF दस्तावेज़ बनाएं

जब आप **add rectangle to PDF** करना चाहते हैं, तो सबसे पहले एक खाली दस्तावेज़ बनाते हैं। `Document` क्लास को एक खाली कैनवास समझें; बाद में आप जो कुछ भी जोड़ेंगे वह इसके अंदर रहेगा।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

खाली दस्तावेज़ से शुरू क्यों करें? क्योंकि इससे आपको हर तत्व पर पूर्ण नियंत्रण मिलता है—बाद में छिपे हुए पेज हेडर या फुटर से जूझना नहीं पड़ता।

## चरण 2: shape PDF डालने के लिए DocumentBuilder को प्रारंभ करें

`DocumentBuilder` आपका ड्राइंग ब्रश है। यह टेक्स्ट, इमेज और, हमारे लिए सबसे महत्वपूर्ण, शैप्स को रखने में सक्षम है। इसके बिना आपको लो‑लेवल नोड ट्री को खुद ही मैनीपुलेट करना पड़ेगा—जो अधिकांश डेवलपर्स के लिए एक दुःस्वप्न है।

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ध्यान दें कि हमने अभी तक कोई पेज नहीं जोड़ा है। बिल्डर पहली बार कुछ डालते ही स्वचालित रूप से एक पेज बना देगा, जिससे कोड साफ़ रहता है।

## चरण 3: आयत आकार डालें – “add rectangle to PDF” का मूल

अब मज़ेदार हिस्सा आता है: आयत डालना। `InsertShape` मेथड कई `ShapeType` मानों को सपोर्ट करता है; हम `ShapeType.Rectangle` चुनेंगे और इसे 200 × 100 पॉइंट का आकार देंगे।

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

इस चरण पर PDF में पहले से ही एक साधारण आयत मौजूद है। यदि आप अभी फ़ाइल खोलते हैं, तो आपको पहला पेज के टॉप‑लेफ़्ट कोने में एक साधारण बॉक्स दिखाई देगा। यही **add graphics to PDF** की नींव है।

## चरण 4: आयत को स्टाइल करें – कस्टम शैडो जोड़ना

स्टाइल के बिना आयत बोरिंग होती है। चलिए इसे एक सूक्ष्म ड्रॉप शैडो देते हैं ताकि PDF रेंडर होने पर यह *पॉप* करे। `ShadowFormat` ऑब्जेक्ट ब्लर रेडियस से लेकर अपारदर्शिता तक सब नियंत्रित करता है।

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

शैडो क्यों जोड़ें? सौंदर्य वृद्धि के अलावा, शैडो ओवरलैपिंग ग्राफ़िक्स को अलग पहचानने में मदद करता है—जो आप **add graphics to PDF** अधिक जटिल रिपोर्टों में करते समय उपयोगी हो सकता है।

## चरण 5: फ़ाइल सहेजें – “create PDF with shape” वर्कफ़्लो को पूरा करना

अंतिम लाइन सब कुछ डिस्क पर लिख देती है। Aspose.Words स्वचालित रूप से सही PDF संस्करण चुनता है और आवश्यक रिसोर्सेज एम्बेड करता है।

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

`ShapeWithShadow.pdf` खोलें और आप पृष्ठ पर गर्व से बैठी एक सुंदर शैडो वाली आयत देखेंगे। यही पूरा **create pdf document programmatically** फ्लो है, जो 30 लाइनों से कम कोड में समेटा गया है।

## पूर्ण कार्यशील उदाहरण – शुरू से अंत तक shape के साथ PDF बनाएं

नीचे वह पूरा प्रोग्राम है जिसे आप एक नए Console App प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी `using` स्टेटमेंट्स, `Main` मेथड, और भविष्य के संदर्भ के लिए एक छोटा कमेंट हेडर शामिल है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**अपेक्षित परिणाम:** एक सिंगल‑पेज PDF जहाँ 200 × 100‑पॉइंट की आयत टॉप‑लेफ़्ट कोने के पास स्थित है, और एक नरम, 45‑डिग्री शैडो से सजी हुई है। फ़ाइल को किसी भी PDF व्यूअर में खोलकर सत्यापित करें।

## सामान्य प्रश्न एवं किनारे के मामले

### क्या यह अन्य shape प्रकारों के साथ काम करता है?

बिल्कुल। `ShapeType.Rectangle` को `ShapeType.Ellipse`, `ShapeType.Triangle` या Aspose.Words द्वारा सपोर्ट किए गए 150+ विकल्पों में से किसी भी के साथ बदलें। वही `ShadowFormat` प्रॉपर्टीज़ लागू होती हैं।

### यदि मुझे आयत को किसी विशिष्ट पृष्ठ पर चाहिए तो क्या करें?

शेप डालने के बाद, आप `InsertShape` कॉल करने से पहले बिल्डर की `CurrentPage` प्रॉपर्टी को समायोजित करके आयत को किसी अन्य पेज पर ले जा सकते हैं। उदाहरण के लिए:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### क्या मैं आयत का fill color बदल सकता हूँ?

ज़रूर। `FillColor` प्रॉपर्टी का उपयोग करें:

```csharp
rect.FillColor = Color.LightBlue;
```

### यह फ़ाइल आकार को कैसे प्रभावित करता है?

एक साधारण शैप और शैडो जोड़ने से केवल कुछ किलोबाइट्स बढ़ते हैं। यदि आप कई ग्राफ़िक्स स्टैक करने लगते हैं, तो इमेज को कॉम्प्रेस करने या वेक्टर‑आधारित शैप्स उपयोग करने पर विचार करें ताकि PDF हल्का रहे।

### क्या उत्पादन के लिए लाइसेंस आवश्यक है?

Aspose.Words इवैल्यूएशन मोड में काम करता है, लेकिन आउटपुट PDF में वॉटरमार्क रहेगा। अनलिमिटेड उपयोग और वॉटरमार्क हटाने के लिए लाइसेंस खरीदें।

## टिप्स और ट्रिक्स (प्रो‑लेवल)

- **Batch insertion:** यदि आपको दर्जनों आयतें चाहिए, तो कोऑर्डिनेट्स के कलेक्शन पर लूप चलाएँ और वही `DocumentBuilder` पुनः उपयोग करें—परफ़ॉर्मेंस रैखिक रहता है।
- **Layering:** यदि आप चाहते हैं कि आयत टेक्स्ट के साथ फ्लो करे तो `rect.WrapType = WrapType.Inline` सेट करें, या टेक्स्ट को उसके चारों ओर लपेटने के लिए `WrapType.Square` उपयोग करें।
- **PDF/A compliance:** यदि आपको आर्काइव‑फ़्रेंडली PDF चाहिए तो सेव करने से पहले `doc.CompatibilityOptions.OptimizeForPdfA = true;` कॉल करें।

## दृश्य सारांश

![PDF में आयत जोड़ने का उदाहरण](https://example.com/rectangle-shadow.png "PDF में आयत जोड़ने का उदाहरण")

यह छवि अंतिम PDF लेआउट को दर्शाती है: एक साफ़ आयत जिसमें सूक्ष्म शैडो है, बिल्कुल वही जो हमारा कोड उत्पन्न करता है।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words का उपयोग करके **how to add rectangle to PDF** कैसे किया जाता है, **insert shape PDF** कैसे किया जाता है, और **add graphics to PDF** को कस्टम स्टाइलिंग के साथ कैसे लागू किया जाता है—साथ ही **creating PDF document programmatically** और एक **create PDF with shape** उदाहरण को कैसे पूरा किया जाता है जिसे आप कल फिर से उपयोग कर सकते हैं।  

अब आयत को किसी लोगो से बदलने की कोशिश करें, या कई शैप्स को मिलाकर एक साधारण डायग्राम बनाएं। आप टेक्स्ट रैपिंग, रोटेशन, या शैप के अंदर हाइपरलिंक एम्बेड करने को भी एक्सप्लोर कर सकते हैं। API इतनी समृद्ध है कि आप एक स्थैतिक PDF को इंटरैक्टिव, ग्राफ़िक्स‑रिच रिपोर्ट में बदल सकते हैं बिना C# छोड़े।

बिल्कुल प्रयोग करें, और यदि कोई समस्या आती है तो नीचे टिप्पणी छोड़ें। Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}