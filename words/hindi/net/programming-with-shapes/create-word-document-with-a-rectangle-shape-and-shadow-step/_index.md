---
category: general
date: 2026-03-01
description: Aspose.Words का उपयोग करके वर्ड दस्तावेज़ बनाएं और सीखें कि कैसे आयताकार
  आकार जोड़ें, कैसे छाया जोड़ें, कैसे पारदर्शिता सेट करें, और कैसे आकार बनाएं—सभी
  C# में।
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: hi
og_description: C# में Aspose.Words के साथ वर्ड दस्तावेज़ बनाएं। सीखें कि कैसे आयताकार
  आकार जोड़ें, बाहरी छाया लागू करें, और कुछ ही चरणों में पारदर्शिता सेट करें।
og_title: आयत आकार और छाया के साथ वर्ड दस्तावेज़ बनाएं – गाइड
tags:
- Aspose.Words
- C#
- Document Generation
title: आयत आकार और छाया के साथ वर्ड दस्तावेज़ बनाएं – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# एक आयताकार आकार और शैडो के साथ Word दस्तावेज़ बनाएं – चरण‑दर‑चरण मार्गदर्शिका

क्या आपको कभी **create word document** की आवश्यकता पड़ी है जिसमें एक कस्टम‑स्टाइल्ड आयत हो? शायद आप एक रिपोर्ट टेम्पलेट बना रहे हैं और लेआउट को आकर्षक बनाने के लिए एक सूक्ष्म ड्रॉप‑शैडो चाहते हैं। आप अकेले नहीं हैं—डेवलपर्स लगातार पूछते हैं, “प्रोग्रामेटिकली आयताकार आकार और शैडो कैसे जोड़ूँ?” अच्छी खबर यह है कि Aspose.Words के साथ आप इसे कुछ ही लाइनों में कर सकते हैं।

इस ट्यूटोरियल में हम पूरी प्रक्रिया को चरण‑दर‑चरण देखेंगे: एक खाली Word फ़ाइल बनाना, आयताकार आकार जोड़ना, और पारदर्शिता के साथ बाहरी शैडो कॉन्फ़िगर करना। अंत तक आपके पास एक तैयार‑उपयोग `Shadow.docx` होगा जिसे आप Word में खोलकर तुरंत प्रभाव देख सकते हैं। कोई बाहरी टूल नहीं, कोई जटिल XML नहीं—सिर्फ साफ़ C# कोड और स्पष्ट व्याख्याएँ।

## आप क्या सीखेंगे

- **How to create shape** ऑब्जेक्ट्स को Word दस्तावेज़ में Aspose.Words का उपयोग करके बनाना।
- **How to add rectangle shape** को पैराग्राफ में जोड़ना बिना मौजूदा सामग्री को बिगाड़े।
- **How to add shadow** (outer shadow) और उसके रंग, ऑफ़सेट, ब्लर, तथा पारदर्शिता को नियंत्रित करना।
- **How to set transparency** शैडो पर ताकि वह पेशेवर दिखे।
- टिप्स, संभावित समस्याएँ, और विविधताएँ जो आपको वास्तविक‑दुनिया के प्रोजेक्ट्स में चाहिए हो सकती हैं।

### पूर्वापेक्षाएँ

- .NET 6.0 या बाद वाला (API .NET Framework 4.6+ के साथ भी काम करता है)।
- NuGet (`Install-Package Aspose.Words`) के माध्यम से Aspose.Words for .NET स्थापित किया हुआ।
- C# सिंटैक्स की बुनियादी समझ—कुछ भी जटिल नहीं, बस सामान्य `using` स्टेटमेंट्स और ऑब्जेक्ट निर्माण।

> **Pro tip:** यदि आप Visual Studio का उपयोग कर रहे हैं, तो “nullable reference types” को सक्षम करें ताकि संभावित null‑reference बग्स को जल्दी पकड़ा जा सके।

## चरण 1 – एक खाली Word दस्तावेज़ बनाएं

`Document` क्लास से हम **create word document** शुरू करते हैं। इसे एक खाली कैनवास समझें; बाद में आप सेक्शन, पैराग्राफ, टेबल या शैप्स जोड़ सकते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

हमें एक नया `Document` इंस्टेंस क्यों चाहिए? क्योंकि हर शैप, पैराग्राफ, या स्टाइल एक दस्तावेज़ ऑब्जेक्ट मॉडल (DOM) के भीतर रहता है। एक साफ़ दस्तावेज़ से शुरू करने से यह सुनिश्चित होता है कि आप जो आयत जोड़ते हैं वह मौजूदा सामग्री में बाधा नहीं बनती।

## चरण 2 – आयताकार आकार को परिभाषित करें

अब हम **how to create shape** एक आयत बनाते हैं। `Shape` कन्स्ट्रक्टर ओनिंग डॉक्यूमेंट और शैप टाइप लेता है। हम इसकी चौड़ाई और ऊँचाई पॉइंट्स में सेट करते हैं (1 pt ≈ 1/72 in)।

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

आप सोच सकते हैं, “क्या मैं पॉइंट्स की जगह सेंटीमीटर इस्तेमाल कर सकता हूँ?” API केवल पॉइंट्स स्वीकार करता है, लेकिन आप इसे बदल सकते हैं: `points = centimeters * 28.35`। यह छोटा परिवर्तन तब उपयोगी होता है जब आप शैप्स को पेज मार्जिन के अनुसार संरेखित कर रहे हों।

## चरण 3 – बाहरी शैडो जोड़ें और पारदर्शिता सेट करें

यहीं पर जादू होता है: **how to add shadow** और **how to set transparency** उस शैडो पर। `ShadowFormat` प्रॉपर्टी आपको पूरी नियंत्रण देती है।

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**इन सेटिंग्स का कारण?**  
- **Transparency** पेज की नीचे की बनावट को दिखने देता है, जिससे शैडो बहुत भारी न लगे।  
- **OffsetX/Y** यह भ्रम पैदा करता है कि शैप पेज से उठी हुई है।  
- **BlurRadius** किनारों को नरम करता है—इसके बिना शैडो एक कठोर आयत होगी, जो अस्वाभाविक दिखेगी।

यदि आपको अधिक नाटकीय प्रभाव चाहिए, तो `OffsetX/Y` को 10 करें और `BlurRadius` को 8 तक बढ़ाएँ। इसके विपरीत, सूक्ष्म संकेत के लिए उन्हें क्रमशः 2 और 2 रखें।

## चरण 4 – दस्तावेज़ में शैप डालें

अब हम **add rectangle shape** को दस्तावेज़ के पहले पैराग्राफ में जोड़ते हैं। यदि दस्तावेज़ में कोई सामग्री नहीं है, तो `FirstParagraph` आपके लिए स्वचालित रूप से बन जाता है।

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

यदि आप शैप को किसी विशिष्ट टेबल सेल या बाद के पैराग्राफ में चाहते हैं तो क्या? बस उस नोड को खोजें (`doc.GetChild(NodeType.Paragraph, index, true)`) और उस पर `AppendChild` कॉल करें। यदि आपको कई कॉपी चाहिए तो वही शैप ऑब्जेक्ट क्लोन किया जा सकता है।

## चरण 5 – दस्तावेज़ को सहेजें

अंत में, हम डिस्क पर **create word document** फ़ाइल बनाते हैं। ऐसा पाथ उपयोग करें जो आपके वातावरण के अनुकूल हो; उदाहरण में एक प्लेसहोल्डर उपयोग किया गया है।

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

जब आप Microsoft Word में `Shadow.docx` खोलते हैं, तो आपको नीचे‑दाएँ ओर ऑफ़सेट वाला एक हल्का‑ग्रे आयत और नरम बाहरी शैडो दिखेगा। शैडो की 30 % पारदर्शिता सुनिश्चित करती है कि वह पेज पर हावी न हो।

---

![शैडो वाले आयताकार आकार के साथ Word दस्तावेज़ बनाएं](image.png "शैडो वाले आयताकार आकार के साथ Word दस्तावेज़ बनाएं")

*छवि वैकल्पिक पाठ: शैडो वाले आयताकार आकार के साथ Word दस्तावेज़ बनाएं*

## पूर्ण, तैयार‑चलाने योग्य कोड

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी‑पेस्ट करके कंसोल ऐप में उपयोग कर सकते हैं। कोई हिस्सा नहीं छूटा, कोई “अधिक जानकारी के लिए दस्तावेज़ देखें” नहीं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### अपेक्षित परिणाम

- लक्ष्य फ़ोल्डर में **Shadow.docx** नाम की फ़ाइल दिखाई देती है।
- इसे Word में खोलने पर एक आयत (200 × 100 pt) के साथ डार्क‑ग्रे बाहरी शैडो दिखता है।
- शैडो क्षैतिज और ऊर्ध्वाधर रूप से 5 pt ऑफ़सेट है, ब्लर किया गया है, और 30 % पारदर्शी है।

## सामान्य प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं शैडो का रंग अपने ब्रांड के अनुसार बदल सकता हूँ?** | बिल्कुल—सिर्फ `System.Drawing.Color.DarkGray` को अपनी पसंद के किसी भी `Color` से बदल दें, उदाहरण के लिए नीले एक्सेंट के लिए `Color.FromArgb(255, 0, 120, 215)`। |
| **अगर मुझे बाहरी के बजाय आंतरिक शैडो चाहिए तो क्या करें?** | `ShadowFormat.Style = ShadowStyle.InnerShadow` सेट करें। बाकी प्रॉपर्टीज़ वही व्यवहार करती हैं। |
| **क्या पुरानी Word संस्करणों में पारदर्शिता समर्थित है?** | हां। Aspose.Words उपयुक्त XML लिखता है जिसे Word 2007+ समझता है। पुराने संस्करण पारदर्शिता मान को नजरअंदाज कर सकते हैं लेकिन फिर भी शैडो दिखाएंगे। |
| **क्या मैं विभिन्न शैडो वाले कई शैप्स जोड़ सकता हूँ?** | बिल्कुल—सिर्फ नए `Shape` इंस्टेंस बनाएं, प्रत्येक शैडो को स्वतंत्र रूप से कॉन्फ़िगर करें, और उन्हें इच्छित नोड्स में जोड़ें। |
| **सैकड़ों शैप्स के प्रदर्शन के बारे में क्या?** | बहुत सारे शैप्स बनाने से मेमोरी उपयोग बढ़ सकता है। एक ही `Document` इंस्टेंस को पुन: उपयोग करें और लूप में शैप्स जोड़ें; यदि मेमोरी दबाव हो तो अस्थायी ऑब्जेक्ट्स को डिस्पोज़ करें। |

## वास्तविक‑दुनिया के प्रोजेक्ट्स के लिए टिप्स

- **Batch generation:** कई उपयोगकर्ताओं के लिए रिपोर्ट जनरेट करते समय, एक ही `Document` टेम्पलेट को इंस्टैंशिएट करें और प्रत्येक इटरेशन के लिए क्लोन करें। शैप्स जोड़ने से पहले प्लेसहोल्डर्स को बदलें।
- **Dynamic sizing:** पेज डाइमेंशन (`document.FirstSection.PageSetup.PageWidth`) का उपयोग करके शैप का आकार पेज के सापेक्ष गणना करें, जिससे विभिन्न कागज आकारों में लेआउट सुसंगत रहे।
- **Testing:** शैडो पैरामीटर में बदलाव के बाद हमेशा उत्पन्न `.docx` को Word में खोलें। विज़ुअल फीडबैक संख्या अनुमान लगाने से तेज़ है।

## अगले कदम

अब जब आप **how to add rectangle shape**, **how to add shadow**, और **how to set transparency** जानते हैं, तो निम्नलिखित को एक्सप्लोर करने पर विचार करें:

- शैप्स में **gradient fills** जोड़ना (`Shape.FillFormat`)।
- वॉटरमार्क प्रभाव के लिए शैप्स के अंदर **pictures** एम्बेड करना।
- ग्रिड में कई शैडो वाले शैप्स को संरेखित करने के लिए **tables** का उपयोग करना।
- शैडो को संरक्षित रखते हुए उसी दस्तावेज़ को PDF में एक्सपोर्ट करना (`document.Save("output.pdf")`)।

इनमें से प्रत्येक समान मूल अवधारणाओं पर आधारित है, इसलिए आप कोड को विस्तारित करने में सहज महसूस करेंगे।

---

### पुनरावलोकन

हमने Aspose.Words के साथ **create word document** शुरू किया, फिर **how to create shape** एक आयत लागू की, **how to add shadow** लागू किया, **how to set transparency** को समायोजित किया, और परिणाम सहेजा। पूरी प्रक्रिया एक संक्षिप्त, पुन: उपयोग योग्य पैटर्न में फिट होती है जिसे आप किसी भी ऑटोमेशन परिदृश्य में अनुकूलित कर सकते हैं।

बिना झिझक प्रयोग करें—रंग बदलें, ऑफ़सेट के साथ खेलें, या कई शैप्स को एक साथ स्टैक करें। यदि कोई समस्या आती है, तो ऊपर के सेक्शन को फिर से देखें; वे तेज़ संदर्भ के लिए डिज़ाइन किए गए हैं। कोडिंग का आनंद लें, और आपके दस्तावेज़ हमेशा परिपूर्ण दिखें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}