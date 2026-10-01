---
category: general
date: 2026-09-30
description: C# के साथ Word में आकारों को समूहित करें – सीखें कैसे आकारों को समूहित
  करें, आयत और दीर्घवृत्त जोड़ें, और प्रोग्रामेटिकली Word दस्तावेज़ों में आयत आकार
  डालें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: hi
lastmod: 2026-09-30
og_description: C# और Aspose.Words का उपयोग करके Word में आकृतियों को समूहित करें।
  आयत जोड़ने, दीर्घवृत्त जोड़ने और प्रभावी ढंग से आकृतियों को समूहित करने के लिए इस
  पूर्ण गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: C# के साथ Word में आकारों को समूहित करें – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# और Aspose.Words का उपयोग करके Word में आकृतियों को समूहित कैसे करें
url: /hi/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word using C# and Aspose.Words

यदि आपको **Word में shapes को programmatically समूहित** करना है, तो यह गाइड आपको बिल्कुल वही दिखाएगा। आप देखेंगे कि कैसे एक rectangle जोड़ें, एक ellipse जोड़ें, और फिर उन्हें Aspose.Words लाइब्रेरी for .NET का उपयोग करके एक ही group shape में मिलाएँ।

Shapes के साथ काम करना रिपोर्ट, कॉन्ट्रैक्ट या मार्केटिंग सामग्री को स्वचालित रूप से जनरेट करने की सामान्य आवश्यकता है। इस ट्यूटोरियल के अंत तक आपके पास एक पुन: उपयोग योग्य C# मेथड होगा जो DOCX फ़ाइल को लोड करता है, एक rectangle और एक ellipse डालता है, उन्हें समूहित करता है, और परिणाम को सहेजता है—बिना Word को मैन्युअली खोले।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 SDK या बाद का संस्करण स्थापित  
* Visual Studio 2022 (Community edition भी चलेगा) जैसा विकास पर्यावरण  
* Aspose.Words for .NET लाइसेंस या एक मुफ्त evaluation कॉपी (API लाइसेंस के बिना भी काम करता है लेकिन watermark जोड़ता है)  

आपको एक स्रोत Word दस्तावेज़ (`input.docx`) भी चाहिए जो आप कोड से रेफ़र कर सकें। दस्तावेज़ खाली हो सकता है; ट्यूटोरियल shape हैंडलिंग पर केंद्रित है।

## Step 1: Create a new console project and add Aspose.Words

एक टर्मिनल या Visual Studio कमांड प्रॉम्प्ट खोलें और चलाएँ:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

यह एक नया console application **WordShapeDemo** बनाता है और `Aspose.Words` NuGet पैकेज जोड़ता है, जिसमें `Document` और `DocumentBuilder` क्लासेज़ होते हैं जो Word फ़ाइलों को हेरफेर करने के लिए उपयोग होते हैं।

## Step 2: Load or create a document

**Word में group shapes** के साथ काम करने का पहला कदम `Document` ऑब्जेक्ट प्राप्त करना है। आप या तो मौजूदा DOCX फ़ाइल लोड कर सकते हैं या एक खाली दस्तावेज़ से शुरू कर सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

`Document` क्लास पूरे Word फ़ाइल का प्रतिनिधित्व करता है। फ़ाइल लोड करने से आपके पास shapes डालने के लिए तैयार कैनवास मिल जाता है।

## Step 3: Begin a group shape

एक *group shape* आपको कई स्वतंत्र shapes को एक ही इकाई के रूप में ट्रीट करने देता है—एक साथ मूव या रिसाइज़ करने के लिए बिल्कुल उपयुक्त। समूह शुरू करने के लिए `DocumentBuilder` पर `StartGroupShape()` कॉल करें।

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

`StartGroupShape` कॉल करने से Aspose.Words को बताता है कि अगली सभी shape इन्सर्शन उसी logical group का हिस्सा हैं, जब तक आप `EndGroupShape` नहीं कॉल करते।

## Step 4: How to add rectangle shape in Word

अब समूह खुला है, एक rectangle डालें। `InsertShape` मेथड एक `ShapeType` enum लेता है, उसके बाद चौड़ाई और ऊँचाई (points में)।

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

rectangle समूह का पहला सदस्य बन जाता है। आप बाद में इसकी fill, outline या text को कस्टमाइज़ कर सकते हैं यदि आवश्यक हो।

## Step 5: How to add ellipse shape in Word

अगला, एक ellipse जोड़ें (जब चौड़ाई और ऊँचाई समान हों तो यह एक circle बनता है)। यह वही builder का उपयोग करके **ellipse जोड़ने** का प्रदर्शन करता है।

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

अब दोनों shapes समूह के भीतर एक ही coordinate space साझा करते हैं, जिससे उन्हें विज़ुअली अलाइन करना आसान हो जाता है।

## Step 6: Close the group shape definition

जब आप सभी इच्छित सदस्य जोड़ चुके हों, तो समूह को बंद करें। यह shapes के संग्रह को अंतिम रूप देता है ताकि Word उन्हें एक ऑब्जेक्ट के रूप में ट्रीट करे।

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

इस चरण के बाद दस्तावेज़ में एक ही grouped shape है जिसमें rectangle और ellipse दोनों शामिल हैं।

## Step 7: Save the modified document

अंत में, बदलावों को डिस्क पर लिखें। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई फ़ाइल बना सकते हैं।

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

प्रोग्राम चलाने पर `output.docx` बनता है। Microsoft Word में फ़ाइल खोलें, shape को सेलेक्ट करें, और आप देखेंगे कि rectangle और ellipse एक साथ मूव होते हैं—जिससे **Word में group shapes** ऑपरेशन सफल होने का प्रमाण मिलता है।

### Expected result

* Word फ़ाइल में एक ही grouped ऑब्जेक्ट है।  
* समूह को सेलेक्ट करने पर आप rectangle और ellipse दोनों को एक साथ ड्रैग, रिसाइज़ या रोटेट कर सकते हैं।  
* Word के साथ कोई मैनुअल इंटरैक्शन आवश्यक नहीं; सब कुछ C# कोड द्वारा किया जाता है।

![Grouped shapes in Word document](grouped-shapes.png "Word दस्तावेज़ में एक समूहित rectangle और ellipse shape का स्क्रीनशॉट")

*Image alt text: “Word दस्तावेज़ में एक समूहित rectangle और ellipse shape का स्क्रीनशॉट”* (छवि alt‑text आवश्यकता को पूरा करता है)।

## Why grouping shapes matters

Shapes को समूहित करना केवल दृश्य सुविधा नहीं है। यह आपको सक्षम बनाता है:

* **लेआउट की स्थिरता बनाए रखें** – समूह को मूव करने से रिलेटिव पोज़िशन बरकरार रहती है।  
* **एक बार में ट्रांसफ़ॉर्मेशन लागू करें** – प्रत्येक shape को अलग‑अलग रोटेट या स्केल करने की बजाय पूरे समूह को रोटेट या स्केल करें।  
* **डाउनस्ट्रीम प्रोसेसिंग को सरल बनाएं** – जब अन्य टूल DOCX पढ़ते हैं, तो उन्हें एक ही composite shape दिखता है, जिससे जटिलता कम होती है।

यदि आपको भविष्य में उसी logical unit में और shapes (जैसे line या text box) जोड़ने की जरूरत पड़े, तो बस `EndGroupShape` से पहले फिर से `InsertShape` कॉल करें।

## Common variations and edge cases

| Situation | How to handle it |
|-----------|-----------------|
| **Different units** – you have measurements in centimeters | `InsertShape` कॉल करने से पहले सेंटीमीटर को points में बदलें (`1 cm ≈ 28.35 pt`)। |
| **Adding a text label** – you want a caption inside the group | rectangle और ellipse के बाद `ShapeType.TextBox` इन्सर्ट करें, फिर उसकी `Text` प्रॉपर्टी सेट करें। |
| **Applying a fill color** – you need a blue rectangle | `InsertShape` के बाद, `builder.CurrentParagraph.Runs[0].Font` के माध्यम से आखिरी shape प्राप्त करें और `shape.FillColor = System.Drawing.Color.Blue;` सेट करें। |
| **Using a different document format** – you target `.doc` instead of `.docx` | वही कोड काम करता है; केवल `Save` कॉल में फ़ाइल एक्सटेंशन बदलें। Aspose.Words स्वचालित रूप से फ़ॉर्मेट संभालता है। |

## Pro tips

* **Builder को पुन: उपयोग करें** – आप एक ही दस्तावेज़ में कई समूह शुरू और समाप्त कर सकते हैं; बस `EndGroupShape` के बाद फिर से `StartGroupShape` कॉल करें।  
* **Performance** – एक ही `StartGroupShape/EndGroupShape` ब्लॉक के भीतर बैच में shape इन्सर्शन करना, समूह के बाहर व्यक्तिगत रूप से इन्सर्ट करने से तेज़ होता है।  
* **Licensing** – evaluation लाइसेंस पहले पृष्ठ पर watermark जोड़ता है। प्रोडक्शन में इसे हटाने के लिए उचित लाइसेंस इंस्टॉल करें।

## Conclusion

अब आप जानते हैं कि C# के साथ **Word में shapes को समूहित** कैसे करें, **rectangle कैसे जोड़ें**, **ellipse कैसे जोड़ें**, और Aspose.Words का उपयोग करके Word दस्तावेज़ों में **rectangle shape कैसे इन्सर्ट करें**। पूरा, चलाने योग्य उदाहरण प्रोजेक्ट सेटअप से लेकर अंतिम फ़ाइल सहेजने तक हर कदम को दर्शाता है।

अब आप अतिरिक्त shape प्रकारों का अन्वेषण कर सकते हैं, स्टाइलिंग लागू कर सकते हैं, या समूहित shapes को टेबल और इमेज़ के साथ मिलाकर परिष्कृत, programmatically जनरेटेड दस्तावेज़ बना सकते हैं।

---

**Next steps**

* **समूहित shapes को rotate करना सीखें**: समूह बंद करने के बाद `Shape.RotationAngle` का उपयोग करें।  
* **rectangle और ellipse के लिए fill और outline कस्टमाइज़ेशन** का अन्वेषण करें।  
* इस लॉजिक को ASP.NET Core API में इंटीग्रेट करें ताकि ऑन‑डिमांड रिपोर्ट जनरेट हो सके।  

Happy coding!


## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}