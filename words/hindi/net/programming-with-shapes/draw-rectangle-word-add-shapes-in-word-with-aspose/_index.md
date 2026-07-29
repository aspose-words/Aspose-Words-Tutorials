---
category: general
date: 2026-07-29
description: Aspose.Words का उपयोग करके आयताकार शब्द बनाएं। सीखें कि कैसे आयताकार
  आकृति जोड़ें, रेखा आकृति जोड़ें, और एक ही दस्तावेज़ में कई आकृतियों को प्रबंधित
  करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: hi
lastmod: 2026-07-29
og_description: Aspose.Words के साथ आयताकार शब्द बनाएं। इस चरण‑दर‑चरण गाइड का पालन
  करके आयताकार आकार जोड़ें, रेखा आकार जोड़ें, और कई आकारों के साथ शब्द को सहजता से
  संभालें।
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: वर्ड में आयत बनाएं – वर्ड में आकार जोड़ने में माहिर
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: वर्ड में आयत बनाएं – Aspose के साथ वर्ड में आकृतियाँ जोड़ें
url: /hi/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Word में Shapes जोड़ने की पूरी गाइड

क्या आप कभी सोचते रहे हैं कि **draw rectangle word** दस्तावेज़ बिना हर बार UI खोले कैसे बनाएं? आप अकेले नहीं हैं। कई डेवलपर्स को तुरंत Word फ़ाइलें जेनरेट करनी होती हैं, और सबसे आसान तरीका है कि एक लाइब्रेरी को यह काम करने दें। इस ट्यूटोरियल में हम आपको बिल्कुल दिखाएंगे **shapes कैसे जोड़ें**—विशेष रूप से एक rectangle और एक line—Aspose.Words for .NET का उपयोग करके, और हम *draw rectangle word* वाक्यांश पर ध्यान केंद्रित रखेंगे ताकि आप कभी खो न जाएँ।

इसे एक मिनी‑आर्ट स्टूडियो समझें जो आपके कोड के अंदर रहता है। अंत तक आप **add rectangle shape**, **add line shape**, और यहाँ तक कि उन्हें **multiple shapes word** समूहों में जोड़ सकेंगे। कोई UI नहीं, कोई मैन्युअल झंझट नहीं, सिर्फ साफ़, दोहराने योग्य C#।

## आप क्या सीखेंगे

- Aspose.Words के साथ नया Word दस्तावेज़ सेट अप करें।  
- **GroupShape** बनाएं जो कई ऑब्जेक्ट्स रख सके।  
- उस समूह के अंदर **add rectangle shape** और **add line shape** जोड़ें।  
- समूहित shapes को दस्तावेज़ बॉडी में डालें।  
- फ़ाइल को सेव करें और तुरंत परिणाम देखें।  

यदि आप बेसिक C# में सहज हैं और आपके पास Aspose.Words की कॉपी है, तो आप तैयार हैं। कोर लाइब्रेरी के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

> **Pro tip:** Aspose.Words .NET 6, .NET 7, और .NET Framework 4.6+ के साथ काम करता है। अपने प्रोजेक्ट से मेल खाने वाला runtime चुनें।

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – दस्तावेज़ सेट अप करना

draw rectangle word** करने से पहले हमें एक साफ़ कैनवास चाहिए। `Document` क्लास वही कैनवास है; `DocumentBuilder` हमारा ब्रश है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

ऊपर की दो लाइनों से हमें एक नई, मेमोरी में बनी `.docx` मिलती है। अभी तक कुछ भी डिस्क पर नहीं लिखा गया है, जिसका मतलब है कि हम फ़ाइल सिस्टम को गड़बड़ किए बिना प्रयोग कर सकते हैं।

## Shapes कैसे जोड़ें – GroupShape कंटेनर बनाना

जब आप चाहते हैं कि **multiple shapes word** एक इकाई की तरह व्यवहार करे—साथ में मूव हो, साथ में रोटेट हो—तो आप उन्हें `GroupShape` में रैप करते हैं। समूह को एक फ़ोल्डर समझें जो अन्य shapes रखता है।

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

समूह क्यों? क्योंकि बाद में आप **add rectangle shape** और **add line shape** जोड़कर उन्हें साथ में मूव करना चाह सकते हैं। समूह के बिना, आपको प्रत्येक shape को अलग‑अलग रीपोज़िशन करना पड़ेगा।

## add rectangle shape – समूह के अंदर Rectangle डालना

अब जब कंटेनर मौजूद है, चलिए **add rectangle shape** करते हैं। एक rectangle एक `Shape` है जिसका `ShapeType` `Rectangle` है।

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

`Left` और `Top` मान समूह के मूल बिंदु के सापेक्ष हैं, पेज के नहीं। इससे shapes को सटीक रूप से लाइन अप करना आसान हो जाता है। rectangle समूह के टॉप‑लेफ़्ट कोने के पास दिखाई देगा।

## add line shape – उसी समूह में Line जोड़ना

एक line बस एक और `Shape` है, लेकिन उसका `ShapeType` `Line` है। हम इसे rectangle के नीचे स्थित करेंगे।

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

क्योंकि line की ऊँचाई शून्य है, `Top` प्रॉपर्टी तय करती है कि line ऊर्ध्वाधर रूप से कहाँ स्थित है। `Width` नियंत्रित करता है कि line क्षैतिज रूप से कितनी लंबी होगी।

## multiple shapes word – समूह को दस्तावेज़ बॉडी में डालना

हमारे पास एक समूह है जिसमें अब **add rectangle shape** और **add line shape** हैं। अंतिम कदम है इसे पूरी तरह से दस्तावेज़ में डालना।

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` समूह को ठीक उसी जगह रखता है जहाँ `DocumentBuilder` वर्तमान में स्थित है। यदि आपको इसे किसी विशेष पैराग्राफ में चाहिए, तो पहले `builder.MoveToParagraph(index)` से बिल्डर को मूव करें।

## परिणाम को सेव करना – draw rectangle word आउटपुट देखना

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

जनरेट की गई फ़ाइल को Microsoft Word में खोलें और आपको एक समूह दिखाई देगा जिसमें rectangle और line दोनों हैं। आप समूह पर क्लिक कर सकते हैं, उसे ड्रैग कर सकते हैं, या आकार बदल भी सकते हैं—सभी shapes साथ में मूव होते हैं। यही है **multiple shapes word** की शक्ति।

### अपेक्षित आउटपुट

- एक `.docx` फ़ाइल जिसका नाम `GroupShape.docx` है।  
- एक पेज जिसमें टॉप‑लेफ़्ट कोने के पास एक समूहित rectangle (120 × 80 pt) है।  
- एक क्षैतिज line (150 pt लंबी) जो rectangle के ठीक नीचे स्थित है।  
- दोनों shapes को एक ही ऑब्जेक्ट के रूप में चयनित किया जा सकता है।

यदि आप समूह पर डबल‑क्लिक करेंगे, तो Word आपको प्रत्येक shape को अलग‑अलग एडिट करने देगा—बारीकी से ट्यून करने के लिए परफेक्ट।

## सामान्य प्रश्न और किनारे के मामलों

**अगर मुझे दो से अधिक shapes चाहिए तो?**  
बस प्रत्येक अतिरिक्त ऑब्जेक्ट के लिए `group.AppendChild(yourShape)` कॉल करते रहें। समूह किसी भी संख्या में shapes रख सकता है, जिससे यह जटिल डायग्राम के लिए आदर्श है।

**क्या मैं rectangle का fill color बदल सकता हूँ?**  
बिल्कुल। rectangle बनाते समय, `rectangle.FillColor = System.Drawing.Color.LightBlue;` सेट करें। यह किसी भी shape के लिए काम करता है जो fill को सपोर्ट करता है।

**क्या line के लिए `Height = 0` सेट करना आवश्यक है?**  
हां, एक सीधी क्षैतिज line के लिए ऊँचाई शून्य होनी चाहिए। एक लंबवत line के लिए, `Width = 0` सेट करें और `Height` को सकारात्मक मान दें।

**क्या यह .doc फ़ाइलों (Word 97‑2003) के साथ काम करेगा?**  
Aspose.Words पुराने `.doc` फॉर्मेट में सेव कर सकता है, लेकिन कुछ आधुनिक shape फीचर सीमित हो सकते हैं। पूर्ण फ़िडेलिटी के लिए `.docx` का उपयोग करें।

**पूरे समूह को कैसे घुमाएँ?**  
इसे डालने से पहले आप `group.Rotation = 45;` (डिग्री) सेट कर सकते हैं। यह रोटेशन प्रत्येक चाइल्ड shape पर लागू होता है।

## सारांश – Word में प्रोग्रामेटिकली Shapes कैसे जोड़ें

- **draw rectangle word** `Document` और `DocumentBuilder` बनाकर शुरू होता है।  
- **multiple shapes word** रखने के लिए **GroupShape** बनाएं।  
- **add rectangle shape** और **add line shape** को समूह में जोड़ें।  
- `builder.InsertNode` से समूह को बॉडी में डालें।  
- फ़ाइल को सेव करें और विज़ुअल परिणाम की जाँच के लिए खोलें।  

यही पूरा वर्कफ़्लो है, जो एक ही आसान‑पढ़ने योग्य कोड लिस्टिंग में संकलित है।

## अगले कदम और संबंधित विषय

अब जब आप **shapes कैसे जोड़ें** जानते हैं, तो निम्नलिखित का अन्वेषण करें:

- गोल कोनों के साथ **add rectangle shape** (`ShapeType.Rectangle` + `CornerRadius`)।  
- विभिन्न dash पैटर्न के साथ lines को स्टाइल करना (`line.LineFormat.DashStyle`)।  
- रिपोर्ट को समृद्ध बनाने के लिए shapes के साथ images एम्बेड करना।  
- **multiple shapes word** का उपयोग करके फ्लोचार्ट या सरल UML डायग्राम बनाना।  

इनमें से प्रत्येक विषय यहाँ स्थापित बुनियाद पर स्वाभाविक रूप से बनता है, और सभी shapes बनाना, उन्हें कॉन्फ़िगर करना, और आवश्यकता पड़ने पर समूहित करना जैसी समान पैटर्न का पालन करते हैं।

कोडिंग का आनंद लें! यदि आपको कोई अजीब समस्या मिले या आपके पास कोई शानदार उपयोग‑केस हो, तो नीचे टिप्पणी छोड़ें। आपका फीडबैक हम सभी को **draw rectangle word** और उससे आगे की कला में निपुण बनने में मदद करता है।

## अब आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर में निपुण बनने और अपने प्रोजेक्ट में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [C# का उपयोग करके Word में rectangle shape बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words के साथ Word में rectangle shape बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में Shapes डालें](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}