---
category: general
date: 2026-09-08
description: C# का उपयोग करके खाली Word दस्तावेज़ बनाना, आयताकार आकार डालना और कई
  आकारों को समूहित करना सीखें। इस चरण‑दर‑चरण गाइड का पालन करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: hi
lastmod: 2026-09-08
og_description: खाली Word दस्तावेज़ बनाएं, आयताकार आकार डालें और C# में कई आकारों
  को समूहित करें। यह ट्यूटोरियल आपको पूरी प्रक्रिया के माध्यम से ले जाता है।
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: C# में समूहित आकारों के साथ खाली Word दस्तावेज़ बनाएं
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: ग्रुप किए गए आकारों के साथ खाली वर्ड दस्तावेज़ कैसे बनाएं
url: /hi/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# समूहित आकारों के साथ खाली Word दस्तावेज़ कैसे बनाएं

यदि आपको कस्टम ग्राफिक्स वाला **खाली Word दस्तावेज़** बनाना है, तो यह गाइड आपको ठीक-ठीक दिखाएगा। आप **आयत आकार डालना**, **एकाधिक आकारों को समूहित करना**, और **समूह में आकार जोड़ना** सीखेंगे Aspose.Words for .NET का उपयोग करके।

एक खाली दस्तावेज़ आपको एक साफ़ कैनवास देता है, और आकारों को समूहित करने से आप उन्हें एक इकाई के रूप में ले जा सकते हैं, आकार बदल सकते हैं या घुमा सकते हैं। यह ट्यूटोरियल हर चरण को कवर करता है—दस्तावेज़ को इनिशियलाइज़ करने से लेकर अंतिम फ़ाइल को सेव करने तक—ताकि आप कोड को अपने प्रोजेक्ट में कॉपी कर तुरंत परिणाम देख सकें।

## आपको क्या चाहिए

* .NET 6.0 या बाद का (कोड .NET Framework 4.6+ के साथ भी काम करता है)
* एक वैध Aspose.Words for .NET लाइसेंस (फ़्री इवैल्यूएशन परीक्षण के लिए काम करता है)
* Visual Studio 2022 या Visual Studio Code जैसे IDE
* C# सिंटैक्स की बुनियादी समझ

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## खाली Word दस्तावेज़ कैसे बनाएं

पहला कदम `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट एक खाली `.docx` फ़ाइल का प्रतिनिधित्व करता है जिसे आप `DocumentBuilder` से एडिट कर सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` कंस्ट्रक्टर मेमोरी में **खाली Word दस्तावेज़** बनाता है। `DocumentBuilder` टेक्स्ट, इमेज और ड्रॉइंग ऑब्जेक्ट्स डालने के लिए एक फ़्लुएंट API प्रदान करता है।

## दस्तावेज़ में आयत आकार डालें

अब, एक आयत आकार जोड़ें। यह आयत बाद में बनाने वाले समूह का पहला चाइल्ड होगा।

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

`InsertShape` को `ShapeType.Rectangle` के साथ कॉल करने से **आयत आकार** वर्तमान कर्सर पोजीशन पर डालता है। चौड़ाई और ऊँचाई पॉइंट्स में व्यक्त की जाती हैं (1 pt ≈ 1/72 in)।

## कई आकारों को साथ में समूहित करें

`GroupShape` एक कंटेनर की तरह काम करता है। समूह के अंदर के सभी चाइल्ड आकार एक साथ मूव और ट्रांसफ़ॉर्म होते हैं। पहले समूह बनाएं, फिर हमने अभी बनाया हुआ आयत जोड़ें।

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

`InsertGroupShape` मेथड बिल्डर के कर्सर पर एक खाली समूह रखता है। आयत को एप्पेंड करके हम **एकाधिक आकारों को समूहित** करते हैं—आयत समूह के इंटरनल नोड कलेक्शन का हिस्सा बन जाता है।

## समूह में आकार जोड़ें और फ़ाइल सहेजें

अब दूसरा आकार—एक एलिप्स—जोड़ें ताकि दिखाया जा सके कि कई ऑब्जेक्ट्स एक ही कंटेनर साझा कर सकते हैं। उसके बाद दस्तावेज़ को सेव करें।

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`InsertShape` कॉल **समूह में आकार जोड़ता** है जब आप रिटर्न किए गए `Shape` को `GroupShape` में एप्पेंड करते हैं। `Document` को सेव करने से एक `.docx` फ़ाइल बनती है जिसे आप Microsoft Word, LibreOffice या किसी भी संगत व्यूअर में खोल सकते हैं।

### अपेक्षित परिणाम

जब आप *GroupShapeDemo.docx* खोलेंगे, तो आपको एक खाली पेज दिखेगा जिसमें एक समूहित ऑब्जेक्ट होगा, जिसमें हल्के‑नीले रंग की आयत और गुलाबी एलिप्स शामिल है। समूह को सिलेक्ट करने से आप दोनों आकारों को साथ में मूव कर सकते हैं, जिससे पुष्टि होती है कि **एकाधिक आकारों को समूहित** करना सफल रहा।

## GroupShape का उपयोग क्यों करें?

* **एटॉमिक ट्रांसफ़ॉर्मेशन** – समूह को स्केल, रोटेट या मूव करने से सभी चाइल्ड समान रूप से प्रभावित होते हैं।
* **लॉजिकल ऑर्गेनाइज़ेशन** – संबंधित ग्राफिक्स को साथ रखता है, जिससे दस्तावेज़ की संरचना को बनाए रखना आसान हो जाता है।
* **परफ़ॉर्मेंस** – कई स्वतंत्र आकारों को संभालने की तुलना में एक ही कंटेनर को रेंडर करना अक्सर तेज़ होता है।

यदि बाद में आपको किसी एकल चाइल्ड को मॉडिफ़ाई करना हो, तो आप उसे `group.ChildNodes` से इंडेक्स या उसके `Name` प्रॉपर्टी द्वारा प्राप्त कर सकते हैं।

## सामान्य विविधताएँ और किनारी मामलों

| Scenario                                 | How to adapt the code                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **विभिन्न आकार प्रकार**                | Replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other `ShapeType` |
| **आकार के अंदर टेक्स्ट जोड़ना**           | Use `Shape.TextPath.Text = "Hello"` after inserting the shape                    |
| **घूर्णन कोण सेट करना**                 | `group.Rotation = 45;` (degrees)                                                 |
| **DOCX के बजाय PDF के रूप में सहेजना**    | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **समूह पर बॉर्डर लागू करना**             | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## प्रो टिप्स

* **अपने आकारों को नाम दें** – `rectangle.Name = "MyRect";` बाद में उन्हें ढूँढ़ना आसान बनाता है।
* **रिलेटिव पोजिशनिंग का उपयोग करें** – यदि आप चाहते हैं कि समूह पेज मार्जिन से एंकर रहे, तो `group.RelativeHorizontalPosition` को `RelativeHorizontalPosition.Page` सेट करें।
* **रिसोर्सेज़ डिस्पोज़ करें** – बड़े एप्लिकेशन में काम करते समय `Document` को `using` ब्लॉक में रैप करें ताकि अनमैनेज्ड मेमोरी तुरंत मुक्त हो सके।

## त्वरित कॉपी‑पेस्ट के लिए पूर्ण स्रोत कोड

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

कोड को एक नए कंसोल प्रोजेक्ट में कॉपी करें, `Aspose.Words` NuGet पैकेज को रिस्टोर करें, और रन करें। आउटपुट फ़ाइल प्रोजेक्ट की `bin/Debug/net6.0` (या समकक्ष) फ़ोल्डर में दिखाई देगी।

## अगले कदम

अब जब आप **खाली Word दस्तावेज़ बना सकते हैं**, **आयत आकार डाल सकते हैं**, और **एकाधिक आकारों को समूहित** कर सकते हैं, तो आप आगे खोज सकते हैं:

* समूह के अंदर **टेक्स्ट बॉक्स** जोड़ना ताकि लेबल्ड डायग्राम बन सकें।
* `doc.Save("image.png", SaveFormat.Png)` के साथ समूहित ग्राफिक को इमेज में एक्सपोर्ट करना।
* रिपोर्ट्स के लिए टेबल्स के साथ समूहों को कॉम्बाइन करना ताकि रिच़ फॉर्मेटेड रिपोर्ट्स बन सकें।

विभिन्न आकार प्रॉपर्टीज़, समूह हायरार्की, और एक्सपोर्ट फ़ॉर्मेट्स के साथ प्रयोग करें ताकि Aspose.Words की ड्रॉइंग क्षमताओं का पूरा लाभ उठा सकें।

--- 

*याद रखें*: आकारों को समूहित करना आपके Word दस्तावेज़ों को व्यवस्थित रखने और कोड को मेंटेनेबल रखने का एक शक्तिशाली तरीका है। हैप्पी कोडिंग!

## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक रिसोर्स में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [C# का उपयोग करके Word में आयत आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में आकार डालें](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}