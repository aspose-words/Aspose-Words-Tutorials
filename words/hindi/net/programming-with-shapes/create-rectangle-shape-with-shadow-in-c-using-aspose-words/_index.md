---
category: general
date: 2026-03-22
description: C# में आयताकार आकार बनाएं और Aspose.Words के साथ आकार पर शैडो जोड़ें।
  सीखें कि शैडो कैसे जोड़ें, आयत कैसे बनाएं, और शैडो गुण कैसे सेट करें।
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: hi
og_description: C# में आयताकार आकार बनाएं और Aspose.Words का उपयोग करके आकार में छाया
  जोड़ें। चरण‑दर‑चरण गाइड जिसमें छाया कैसे जोड़ें, आयत कैसे बनाएं, और छाया कैसे सेट
  करें, शामिल हैं।
og_title: C# में शैडो के साथ आयताकार आकार बनाएं – पूर्ण गाइड
tags:
- Aspose.Words
- C#
- Document Automation
title: Aspose.Words का उपयोग करके C# में शैडो के साथ आयताकार आकार बनाएं
url: /hi/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape with shadow in C# using Aspose.Words

क्या आपको कभी **Word दस्तावेज़ में rectangle shape** बनानी पड़ी और उसे subtle drop‑shadow देना नहीं आता था? आप अकेले नहीं हैं—कई डेवलपर्स को दस्तावेज़ ऑटोमेशन के साथ पहली बार काम करते समय यही समस्या आती है। इस गाइड में हम **shape में shadow जोड़ने** का पूरा तरीका Aspose.Words के साथ दिखाएंगे, और साथ ही “**how to add shadow**”, “**how to create rectangle**”, और “**how to set shadow**” के सवालों के जवाब भी देंगे।

हम एक साफ़‑सुथरा `Document` बनाएँगे, एक rectangle ड्रॉ करेंगे, उसका shadow चालू करेंगे, blur, distance, angle, और color को ट्यून करेंगे, और अंत में फ़ाइल सेव करेंगे। अंत तक आपके पास एक तैयार `.docx` होगा जिसमें ग्रे‑टोन वाला rectangle पेज के ऊपर तैरता हुआ दिखेगा। कोई रहस्य नहीं, बस सीधा‑सरल कोड जिसे आप किसी भी .NET प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* **Aspose.Words for .NET** (मार्च 2026 तक का नवीनतम संस्करण)। इसे आप NuGet से `Install-Package Aspose.Words` कमांड से प्राप्त कर सकते हैं।
* एक .NET डेवलपमेंट एनवायरनमेंट – Visual Studio, Rider, या यहाँ तक कि C# एक्सटेंशन वाला VS Code भी ठीक रहेगा।
* बेसिक C# ज्ञान – कुछ भी जटिल नहीं, बस एक console या WinForms ऐप बनाने की क्षमता।

बस इतना ही। कोई अतिरिक्त लाइब्रेरी नहीं, कोई छुपे हुए स्टेप नहीं। तैयार? चलिए शुरू करते हैं।

## Step 1: Initialize a new empty document

**rectangle shape** बनाने के लिए हमें पहले एक कंटेनर चाहिए – एक `Document` ऑब्जेक्ट – जो Word फ़ाइल को दर्शाता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

`Document` क्लास वह एंट्री पॉइंट है जहाँ से Aspose.Words की सारी कार्यक्षमता शुरू होती है। इसे एक खाली कैनवास की तरह समझें; इसके बिना आप कोई shape, table, या text नहीं जोड़ सकते।

## Step 2: Create the rectangle that will hold the shadow

अब हम **how to create rectangle** करेंगे, `Shape` को `Rectangle` टाइप के साथ इंस्टैंशिएट करके। हम इसका आकार पॉइंट्स में सेट करते हैं (1 point ≈ 1/72 इंच)।

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

200 × 100 पॉइंट क्यों? यह डेमो के लिए एक उचित आकार है – shadow को स्पष्ट रूप से देख सकें, लेकिन पेज को ओवरवेल्म न करे। अपनी लेआउट के अनुसार इन नंबरों को बदलने में संकोच न करें।

## Step 3: Enable the shadow effect and configure its appearance

यहाँ ट्यूटोरियल का मुख्य भाग है: **how to add shadow** और **how to set shadow** प्रॉपर्टीज़। Aspose.Words हर shape पर एक `Shadow` ऑब्जेक्ट प्रदान करता है, जिससे आप effect को टॉगल कर सकते हैं और विज़ुअल पैरामीटर्स को समायोजित कर सकते हैं।

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** किनारों को नरम करता है – बड़ी वैल्यू से shadow अधिक diffused दिखेगा।
* **Distance** shadow को rectangle से दूर धकेलता है।
* **Angle** यह तय करता है कि light कहाँ से आ रही है; 45° एक diagonal, natural‑look देता है।
* **Color** आपको कोई भी `System.Drawing.Color` चुनने देता है। Gray एक सुरक्षित डिफ़ॉल्ट है, लेकिन आप `Color.Black` से बोल्ड या `Color.LightGray` से subtle बना सकते हैं।

Pro tip: यदि आप `Enabled = false` सेट करते हैं, तो सभी अन्य shadow सेटिंग्स अनदेखी हो जाती हैं, इसलिए इस फ़्लैग को हमेशा दोबारा चेक करें।

## Step 4: Insert the shape into the document body

rectangle तैयार है और उसका shadow कॉन्फ़िगर हो गया है, अब हमें इसे दस्तावेज़ में रखना है। सबसे आसान तरीका है इसे पहले सेक्शन के पहले पैराग्राफ में append करना।

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

यदि आपके दस्तावेज़ में पहले से टेक्स्ट है, तो आप किसी विशेष `Paragraph` या यहाँ तक कि `Table` सेल को ढूँढ कर shape वहाँ insert कर सकते हैं। `AppendChild` मेथड बहुमुखी है – यह किसी भी `Node` टाइप के साथ काम करता है।

## Step 5: Save the document and verify the result

अंत में, हम फ़ाइल को डिस्क पर लिखते हैं। पाथ को अपनी पसंद के अनुसार बदलें; फ़ोल्डर मौजूद होना चाहिए, नहीं तो आपको exception मिलेगा।

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

परिणामी `ShadowedRectangle.docx` को Microsoft Word (या LibreOffice) में खोलें और आपको एक ग्रे rectangle के साथ एक crisp, diagonal shadow नीचे‑दाएँ की ओर तैरते हुए दिखना चाहिए। यदि shadow बहुत हल्का लगता है, तो `BlurRadius` या `Distance` बढ़ाएँ और कोड को फिर से चलाएँ – प्रयोग ही मज़ा है।

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Create rectangle shape with shadow example"}

### Expected output

* एक single‑page Word दस्तावेज़।
* 200 × 100‑point ग्रे rectangle जो पेज के top‑left पर स्थित है।
* 8 pixels की ऑफ़सेट पर 45° एंगल वाला subtle ग्रे shadow, 5 pixels blur के साथ।

## How to add shadow to shape – deeper dive

आप सोच सकते हैं, *“क्या मैं shadow को animate कर सकता हूँ या उसे user input के आधार पर बदल सकता हूँ?”* जबकि Aspose.Words स्वयं animation को सपोर्ट नहीं करता, आप shadow प्रॉपर्टीज़ को प्रोग्रामेटिकली बदल सकते हैं और विभिन्न लुक्स के साथ कई संस्करण बना सकते हैं। उदाहरण के लिए, रंगों के एक कलेक्शन पर लूप चलाएँ:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

यह छोटा स्निपेट **how to set shadow** को डायनामिकली दिखाता है—थीम्ड रिपोर्ट्स जनरेट करने के लिए बेहतरीन।

## How to create rectangle – alternative shapes

यदि आपको rounded rectangle चाहिए, तो बस `ShapeType` बदलें:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

या, एक perfect square के लिए, `Width` को `Height` के बराबर सेट करें। वही shadow प्रॉपर्टीज़ लागू होती हैं, इसलिए आप किसी भी shape के लिए **how to add shadow** पहले से ही कवर कर चुके हैं।

## Common pitfalls and troubleshooting

| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| Shadow दिखाई नहीं देता | `Shadow.Enabled` को `false` रखा गया | `rectangleShape.Shadow.Enabled = true;` सेट करें |
| Shadow बहुत तेज़ दिख रहा है | `BlurRadius` 0 पर सेट है | `BlurRadius` को कम से कम 3 तक बढ़ाएँ |
| Save करने पर `FileNotFoundException` मिल रहा है | Destination फ़ोल्डर मौजूद नहीं है | पहले फ़ोल्डर बनाएँ या वैध पाथ उपयोग करें |
| Shape दिखाई नहीं दे रहा | Width/Height 0 पर सेट है | सुनिश्चित करें दोनों डाइमेंशन > 0 हों |

इन मुद्दों पर नज़र रखें तो “मेरी shape क्यों नहीं दिख रही?” जैसी क्लासिक समस्या से बच सकते हैं।

## Recap – what we’ve accomplished

* **Create rectangle shape** को एक नए Word दस्तावेज़ में Aspose.Words के साथ बनाया।  
* **Add shadow to shape** को `Shadow.Enabled` फ़्लैग टॉगल करके और blur, distance, angle, और color को ट्यून करके लागू किया।  
* **how to add shadow**, **how to create rectangle**, और **how to set shadow** को एक साफ़, पुन: उपयोग योग्य कोड स्निपेट में दर्शाया।  
* एक पूर्ण, ready‑to‑run उदाहरण प्रदान किया जिसे आप किसी भी C# प्रोजेक्ट में पेस्ट कर सकते हैं।

## What’s next?

अब जब आप बुनियादी बातों में निपुण हो गए हैं, तो आगे देखें:

* **How to add shadow to images** – वही `Shadow` API `ShapeType.Image` के साथ काम करता है।
* **Combining multiple shapes** – Word में सीधे flowcharts या infographics बनाएँ।
* **Exporting to PDF** – shadows जोड़ने के बाद `document.Save("output.pdf")` कॉल करके printable संस्करण बनाएँ।

विभिन्न colors, angles, या यहाँ तक कि gradient fills के साथ प्रयोग करने में संकोच न करें। API इतना लचीला है कि आप बिना Word खोले ही प्रोफ़ेशनल‑लुकिंग दस्तावेज़ बना सकते हैं।

---

Happy coding! यदि आपको कोई समस्या आती है, तो नीचे कमेंट करें या Aspose.Words फ़ोरम देखें – कम्युनिटी जल्दी मदद करती है।

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}