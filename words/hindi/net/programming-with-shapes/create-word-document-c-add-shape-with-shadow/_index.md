---
category: general
date: 2026-03-27
description: C# में Word दस्तावेज़ बनाएं और सीखें कि कैसे आकार जोड़ें, आकार पर छाया
  लागू करें, और छाया की दूरी सेट करें। Aspose.Words के लिए चरण‑दर‑चरण मार्गदर्शिका।
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: hi
og_description: C# में एक आयताकार आकार और कस्टम शैडो के साथ वर्ड दस्तावेज़ बनाएं।
  शैडो की दूरी और शैली सेट करने के लिए इस पूर्ण ट्यूटोरियल का पालन करें।
og_title: Word दस्तावेज़ बनाएं C# – छाया के साथ आकार जोड़ें
tags:
- Aspose.Words
- C#
- Document Automation
title: C# में वर्ड दस्तावेज़ बनाएं – शैडो के साथ आकार जोड़ें
url: /hi/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Document C# बनाएं – Shape में Shadow जोड़ें

क्या आपको कभी **create word document c#** बनाना पड़ा है जिसमें एक सुंदर स्टाइल्ड आयत हो? शायद आप एक रिपोर्ट टेम्प्लेट बना रहे हैं और लेआउट को पॉप करने के लिए एक सूक्ष्म ड्रॉप‑शैडो चाहते हैं। इस ट्यूटोरियल में हम ठीक वही करेंगे – कैसे shape जोड़ें, shape पर shadow लागू करें, और Aspose.Words का उपयोग करके shadow की दूरी को भी ट्यून करें।

हम एक खाली दस्तावेज़ से शुरू करेंगे, उसमें एक आयत डालेंगे, उसे एक प्रीसेट शैडो देंगे, और फ़ाइल को सेव करके समाप्त करेंगे। अंत तक आपके पास एक तैयार‑to‑use .docx होगा जिसे आप Word में खोल कर तुरंत प्रभाव देख सकते हैं। कोई बाहरी टूल नहीं, सिर्फ शुद्ध C# कोड।

## Prerequisites

- .NET 6 (या कोई भी नवीनतम .NET Framework) स्थापित हो।
- Visual Studio 2022 या VS Code के साथ C# एक्सटेंशन।
- Aspose.Words for .NET NuGet पैकेज (`Aspose.Words` संस्करण 23.12 या बाद का)।  
  आप इसे पैकेज मैनेजर कंसोल के माध्यम से जोड़ सकते हैं:

  ```powershell
  Install-Package Aspose.Words
  ```

बस इतना ही – कोई अतिरिक्त DLLs या COM इंटरऑप की आवश्यकता नहीं।

## चरण 1: नया Document और Builder प्रारंभ करें – *create word document c#* मूल बातें

सबसे पहले हमें एक `Document` ऑब्जेक्ट चाहिए जो Word फ़ाइल का प्रतिनिधित्व करता है और एक `DocumentBuilder` जिससे हम इसे संपादित कर सकें।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this step matters:** `Document` क्लास सभी Word भागों (पेज, स्टाइल, इमेज) का कंटेनर है। Builder एक हाई‑लेवल API है जो लो‑लेवल नोड मैनिपुलेशन को एब्स्ट्रैक्ट करता है, जिससे **create word document c#** XML से सीधे निपटे बिना आसान हो जाता है।

## चरण 2: Rectangle Shape डालें – *how to create rectangle*  

अब हम पृष्ठ पर एक आयत रखेंगे। आकार पॉइंट्स में व्यक्त किया जाता है (1 pt ≈ 1/72 इंच)।

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tip:** यदि आपको कोई अलग shape चाहिए, तो बस `ShapeType.Rectangle` को `ShapeType.Ellipse`, `ShapeType.Triangle` आदि से बदल दें। वही कोड **how to add shape** के किसी भी प्रकार के लिए काम करता है।

## चरण 3: Preset Shadow लागू करें और फाइन‑ट्यून करें – *apply shadow to shape*  

Aspose.Words कई प्रीसेट शैडो फॉर्मेट्स के साथ आता है। हम `Preset1` का उपयोग करेंगे और फिर दूरी, ब्लर, ट्रांसपेरेंसी, और रंग को कस्टमाइज़ करेंगे।

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Why customize the shadow?** `Distance` प्रॉपर्टी नियंत्रित करती है कि शैडो आयत से कितनी दूर बैठती है – इसे आप 3‑D रेंडरिंग में “लिफ्ट” की तरह समझ सकते हैं। `BlurRadius` किनारों को नरम करता है, जबकि `Transparency` आपको एक सूक्ष्म, प्रोफेशनल लुक देता है। यह **set shadow distance** की आवश्यकता को पूरा करता है और दिखाता है कि आप **apply shadow to shape** को लचीले तरीके से कैसे कर सकते हैं।

## चरण 4: Document को Save करें – *create word document c#* Completion

अंत में, दस्तावेज़ को डिस्क पर लिखें। पथ को उस फ़ोल्डर में बदलें जहाँ आपके पास लिखने की अनुमति हो।

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

परिणामस्वरूप फ़ाइल को Microsoft Word में खोलें, और आपको एक हल्के‑नीले रंग की आयत के साथ एक नरम ग्रे शैडो 5 pt द्वारा ऑफ़सेटेड दिखेगा। यह दृश्य प्रमाण है कि आपने सफलतापूर्वक **create word document c#** एक स्टाइल्ड shape के साथ किया है।

![Shadowed Shape के साथ Word Document C# बनाएं](shadow-example.png){: .img alt="create word document c# उदाहरण जिसमें आयत और छाया दिखती है"}

## Optional Variations & Edge Cases

| परिदृश्य | क्या बदलें | क्यों महत्वपूर्ण है |
|----------|------------|--------------------|
| **विभिन्न shadow शैली** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | अतिरिक्त कोड के बिना आपको अधिक नाटकीय लुक देता है। |
| **कोई preset नहीं – कस्टम shadow** | `Format` को हटाएँ और `OffsetX`, `OffsetY` को मैन्युअल रूप से सेट करें। | दिशा और गहराई पर पूर्ण नियंत्रण। |
| **Multiple shapes** | सेव करने से पहले `builder.InsertShape` को फिर से कॉल करें। | आइकॉन, लोगो आदि के साथ जटिल टेम्प्लेट्स के लिए उपयोगी। |
| **पुरानी Aspose संस्करणों के साथ संगतता** | `ShadowEffect` क्लास का उपयोग करें (v20.x में उपलब्ध)। | सुनिश्चित करता है कि आपका कोड लेगेसी प्रोजेक्ट्स पर चले। |
| **Saving as PDF** | `document.Save("ShadowShape.pdf");` | PDF आउटपुट में भी समान shadow रेंडरिंग दिखती है। |

> **Common question:** *What if the shadow doesn’t appear in Word?*  
> सुनिश्चित करें कि आप Aspose.Words का नवीनतम संस्करण (≥ 22.9) उपयोग कर रहे हैं। पुराने रिलीज़ में शैडो सपोर्ट सीमित था। साथ ही यह भी जाँचें कि दस्तावेज़ नवीनतम Word संस्करण (2016+) में खुला है।

## Full Working Example

नीचे पूरा, कॉपी‑पेस्ट‑रेडी प्रोग्राम दिया गया है। इसमें सभी `using` निर्देश, टिप्पणी, और त्रुटि संभालना शामिल है ताकि अनुभव सुगम रहे।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

प्रोग्राम चलाएँ, `C:\Temp\ShadowShape.docx` पर जाएँ, और आपको वही आयत दिखेगी जिसमें हमने ठीक वही शैडो कॉन्फ़िगर किया था।

## Recap & Next Steps

- अब आप जानते हैं कि **create word document c#** कैसे करें, आयत डालें, और कस्टम **set shadow distance** के साथ **apply shadow to shape** कैसे करें।  
- यह उदाहरण Aspose.Words का उपयोग करता है, जो OpenXML जटिलताओं को छुपाता है और Word संस्करणों में सुसंगत रेंडरिंग की गारंटी देता है।  
- आगे बढ़ना चाहते हैं? कई shapes को मिलाएँ, आयत के अंदर टेक्स्ट जोड़ें, या वही दस्तावेज़ PDF के रूप में एक्सपोर्ट करें ताकि आप देख सकें कि shadow कैसे ट्रांसलेट होता है।

### Related Topics You Might Explore

- **How to add shape** को हेडर/फूटर में ब्रांडिंग के लिए जोड़ें।  
- प्रोग्रामेटिकली चार्ट और टेबल डालने के लिए **Aspose.Words** का उपयोग।  
- वेक्टर shapes के बजाय चित्रों पर **shadow effects** को कस्टमाइज़ करना।  
- इनवॉइस या प्रमाणपत्रों के लिए बड़े पैमाने पर दस्तावेज़ जनरेशन को ऑटोमेट करना।

बिना झिझक प्रयोग करें, कोड को तोड़ें, फिर फिर से बनाएं – यही अवधारणाओं को जल्दी से अंदरूनी बनाने का सबसे तेज़ तरीका है। अगर कोई समस्या आती है, तो नीचे टिप्पणी छोड़ें या आधिकारिक Aspose.Words दस्तावेज़ में गहरी API जानकारी देखें।

Happy coding, and enjoy making your Word files look a little more polished!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}