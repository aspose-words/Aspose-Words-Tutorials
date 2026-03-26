---
category: general
date: 2026-03-25
description: C# में PDF दस्तावेज़ बनाएं और सीखें कि कैसे आयताकार आकार जोड़ें, भरने
  का रंग सेट करें, आकार का आकार समायोजित करें और कुछ ही चरणों में आकार की पारदर्शिता
  सेट करें।
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: hi
og_description: C# में PDF दस्तावेज़ बनाएं और देखें कि कैसे एक आयत जोड़ें, उसका भराव
  रंग, आकार और पारदर्शिता सेट करें ताकि परिष्कृत PDF आउटपुट प्राप्त हो सके।
og_title: आयताकार आकार के साथ PDF दस्तावेज़ बनाएं – C# ट्यूटोरियल
tags:
- C#
- PDF
- Aspose.Words
title: आयताकार आकार के साथ PDF दस्तावेज़ बनाएं – पूर्ण C# गाइड
url: /hi/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# आयत आकार के साथ PDF दस्तावेज़ बनाएं – पूर्ण C# गाइड

क्या आपको कभी **PDF दस्तावेज़** बनाना पड़ा है जिसमें एक कस्टम‑स्टाइल्ड आकार हो, लेकिन आप नहीं जानते थे कहाँ से शुरू करें? आप अकेले नहीं हैं। चाहे आप रिपोर्ट जेनरेटर बना रहे हों या मार्केटिंग फ़्लायर, प्रोग्रामेटिकली आयत बनाना, उसका भराव रंग सेट करना, आकार को समायोजित करना और यहाँ तक कि उसकी पारदर्शिता को नियंत्रित करना आपके PDFs को बहुत अधिक पेशेवर बना सकता है।

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑चलाने योग्य C# उदाहरण के माध्यम से **PDF दस्तावेज़ बनाना**, **आयत आकार जोड़ना**, **भराव रंग सेट करना**, **आकार का आकार निर्धारित करना**, और **आकार की पारदर्शिता सेट करना** (एक सूक्ष्म बाहरी छाया के लिए) दिखाएंगे। अंत में आपके पास एक एकल PDF फ़ाइल (`shadow.pdf`) होगी जिसे आप खोलकर परिणाम देख सकते हैं।

> **Pro tip:** वही तरीका अन्य आकार प्रकारों (ellipse, line, आदि) के साथ भी काम करता है—बस `ShapeType.RECTANGLE` को अपनी आवश्यकता के अनुसार बदल दें।

---

## आपको क्या चाहिए

| पूर्वापेक्षा | क्यों महत्वपूर्ण है |
|--------------|----------------|
| **.NET 6+** (या .NET Framework 4.6+) | Aspose.Words लाइब्रेरी आधुनिक रनटाइम को लक्षित करती है। |
| **Aspose.Words for .NET** NuGet पैकेज | `Document`, `Shape`, `ShadowEffect`, और संबंधित क्लासेस प्रदान करता है। |
| **एक C# IDE** (Visual Studio, Rider, VS Code) | सैंपल को डिबग और चलाना आसान बनाता है। |
| **बुनियादी C# ज्ञान** | आप सिंटैक्स को गहराई में जाए बिना समझ पाएँगे। |

आप लाइब्रेरी को कमांड लाइन से इस प्रकार इंस्टॉल कर सकते हैं:

```bash
dotnet add package Aspose.Words
```

बस इतना ही—कोई अतिरिक्त DLLs, कोई नेटिव डिपेंडेंसी नहीं। एक बार पैकेज स्थापित हो जाने पर, नीचे दिया गया कोड कम्पाइल और रन होगा।

---

## चरण‑दर‑चरण कार्यान्वयन

नीचे हम प्रक्रिया को पाँच तार्किक चरणों में विभाजित करते हैं। प्रत्येक चरण का स्पष्ट शीर्षक (ताकि AI मॉडल इसे इंडेक्स कर सके) और एक छोटा कोड ब्लॉक है जिसे आप सीधे कॉपी‑पेस्ट कर सकते हैं।

### ## 1. PDF दस्तावेज़ बनाएं और कैनवास तैयार करें

सबसे पहला काम `Document` का एक इंस्टेंस बनाना है। इसे एक खाली कैनवास समझें जो अंततः आपका PDF फ़ाइल बन जाएगा।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Why?** `Document` सभी सेक्शन, पैराग्राफ, और शैप्स को रखता है। एक साफ़ ऑब्जेक्ट से शुरू करने से पिछले रन से कोई छिपा हुआ आर्टिफैक्ट नहीं रहता।

### ## 2. आयत आकार जोड़ें – भराव रंग सेट करें और आकार निर्धारित करें

अब हम एक आयत बनाते हैं, उसे चमकीले पीले रंग से भरते हैं, और उसके आयाम निर्धारित करते हैं। यह **add rectangle shape**, **set fill color**, और **set shape size** को कवर करता है।

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Note:** चौड़ाई/ऊँचाई पॉइंट्स में मापी जाती है (1 पॉइंट = 1/72 इंच)। अपने लेआउट के अनुसार इन संख्याओं को समायोजित करें।

### ## 3. बाहरी छाया लागू करें और आकार की पारदर्शिता सेट करें

छायाएँ गहराई जोड़ती हैं, और उनकी अपारदर्शिता को नियंत्रित करना **set shape transparency** का सार है। नीचे हम 30 % पारदर्शिता के साथ एक ग्रे बाहरी छाया कॉन्फ़िगर करते हैं।

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Why set transparency?** 30 % पारदर्शी छाया सूक्ष्म दिखती है, जिससे आयत पृष्ठ पर “समतल” नहीं लगती।

### ## 4. दस्तावेज़ बॉडी में आकार डालें

अब हम आयत को दस्तावेज़ के पहले सेक्शन के पहले पैराग्राफ में रखते हैं। यह चरण सब कुछ आपस में जोड़ता है।

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Edge case:** यदि आपको आकार नई पेज पर चाहिए, तो शैप जोड़ने से पहले `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` जोड़ें।

### ## 5. दस्तावेज़ को PDF फ़ाइल के रूप में सहेजें

अंत में, हम इन‑मेमोरी संरचना को एक वास्तविक PDF फ़ाइल में लिखते हैं। फ़ाइल आपके द्वारा निर्दिष्ट फ़ोल्डर में लिखी जाएगी।

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

जब आप प्रोग्राम चलाते हैं, तो `shadow.pdf` नाम की फ़ाइल बनती है। इसे खोलने पर एक पीला आयत दिखेगा जिसके नीचे 4 पॉइंट्स की ऑफ़सेट वाली हल्की ग्रे छाया होगी—बिल्कुल वही जो कोड ने वर्णित किया था।

> **Expected output:** एक सिंगल‑पेज PDF जहाँ आयत पेज के ऊपर‑बाएँ कोने के पास स्थित है, पीले रंग से भरी हुई, आकार 200 × 100 पॉइंट्स, और अर्द्ध‑पारदर्शी बाहरी छाया के साथ।

---

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

नीचे पूरा स्रोत फ़ाइल दिया गया है, जिसे आप नई कंसोल प्रोजेक्ट में डाल सकते हैं।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tip:** `YOUR_DIRECTORY` को एक पूर्ण पाथ जैसे `C:\Temp` या रिलेटिव पाथ जैसे `.\output` से बदलें। प्रोग्राम फ़ोल्डर नहीं होने पर उसे बना देगा।

---

## अक्सर पूछे जाने वाले प्रश्न (FAQ)

**प्रश्न: क्या मैं आयत की पेज पर स्थिति बदल सकता हूँ?**  
उत्तर: बिल्कुल। शैप को पैराग्राफ में जोड़ने से पहले `rectangle.Left` और `rectangle.Top` (दोनों पॉइंट्स में) सेट करें।

**प्रश्न: यदि मुझे छाया के बजाय भराव को पारदर्शी चाहिए तो क्या करें?**  
उत्तर: `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` उपयोग करें – पहला आर्ग्यूमेंट अल्फा चैनल (0‑255) है, जहाँ 128 लगभग 50 % पारदर्शिता देता है।

**प्रश्न: क्या यह .NET Core के साथ काम करता है?**  
उत्तर: हाँ। Aspose.Words .NET Standard 2.0+ को सपोर्ट करता है, इसलिए आप वही कोड .NET 6, .NET 7, या .NET Framework 4.6+ पर चला सकते हैं।

**प्रश्न: मैं कई शैप्स कैसे जोड़ सकता हूँ?**  
उत्तर: प्रत्येक शैप के लिए चरण 2‑4 दोहराएँ, संभवतः उन्हें विभिन्न पैराग्राफ या सेक्शन में डालें।

---

## निष्कर्ष

हमने अभी **PDF दस्तावेज़** शून्य से **बनाया**, **आयत आकार जोड़ा**, **भराव रंग सेट किया**, **आकार निर्धारित किया**, और **आकार की पारदर्शिता** को समायोजित करके एक परिष्कृत छाया प्रभाव प्राप्त किया। सैंपल कोड स्वतंत्र है, एक मिनट से कम समय में चलता है, और अधिक जटिल PDF लेआउट्स के लिए आवश्यक मुख्य अवधारणाओं को दर्शाता है।

अगली चुनौती के लिए तैयार हैं? आयत को गोल‑कोने वाले आकार से बदलें, शैप के अंदर एक इमेज एम्बेड करें, या स्वचालित रूप से टेबल ऑफ़ कंटेंट्स जेनरेट करें। वही API आपको टेक्स्ट, इमेज, और वेक्टर को लेयर करने की अनुमति देती है—तो संभावनाएँ अनंत हैं।

यदि आपको यह गाइड उपयोगी लगा, तो GitHub पर स्टार दें, टीम के साथ शेयर करें, या अपनी खुद की वैरिएशन के साथ कमेंट छोड़ें। Happy coding! 

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "स्क्रीनशॉट जिसमें पीला आयत और ग्रे बाहरी छाया के साथ निर्मित PDF दिखाया गया है")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}