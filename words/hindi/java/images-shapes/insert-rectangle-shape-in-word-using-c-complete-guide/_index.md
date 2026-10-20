---
category: general
date: 2026-08-04
description: C# के साथ Word दस्तावेज़ में आयताकार आकार डालें। Word में आकारों को समूहित
  करना सीखें, दस्तावेज़ को docx के रूप में सहेजें, और उन्नत लेआउट के लिए DocumentBuilder
  का उपयोग करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: hi
lastmod: 2026-08-04
og_description: C# का उपयोग करके Word फ़ाइल में आयताकार आकार डालें और फिर उन्नत लेआउट
  के लिए आकारों को समूहित करें। यह ट्यूटोरियल दस्तावेज़ को docx के रूप में सहेजने
  और DocumentBuilder का कुशलतापूर्वक उपयोग करने को भी कवर करता है।
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Word में आयताकार आकार डालें – C# चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# का उपयोग करके Word में आयताकार आकार डालें – पूर्ण गाइड
url: /hi/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में C# का उपयोग करके आयताकार आकार डालें – पूर्ण गाइड

यदि आपको C# का उपयोग करके Word दस्तावेज़ में **आयताकार आकार डालना** है, तो यह ट्यूटोरियल आपको बिल्कुल वही दिखाता है। आप सीखेंगे **Word में आकारों को समूहित करने** का तरीका, **दस्तावेज़ को docx के रूप में सहेजना**, और **Builder का उपयोग** कैसे करें ताकि कोड साफ़ और रखरखाव योग्य हो।

आकारों के साथ काम करना रिपोर्ट, प्रमाणपत्र, या कस्टम लेआउट को प्रोग्रामेटिकली जनरेट करने की एक सामान्य आवश्यकता है। इस गाइड के अंत तक आपके पास एक पूरी तरह चलने योग्य उदाहरण होगा जो एक आयत बनाता है, एक दीर्घवृत्त जोड़ता है, उन्हें समूहित करता है, और परिणाम को DOCX फ़ाइल के रूप में सहेजता है।

## आवश्यकताएँ

* .NET 6.0 या बाद का संस्करण स्थापित हो  
* Visual Studio 2022 (या कोई भी IDE जो C# का समर्थन करता हो)  
* **Aspose.Words for .NET** लाइब्रेरी (NuGet के माध्यम से उपलब्ध)  

आप निम्नलिखित कमांड से लाइब्रेरी जोड़ सकते हैं:

```bash
dotnet add package Aspose.Words
```

## DocumentBuilder के साथ आयताकार आकार डालें

पहला कदम एक नया `Document` और एक `DocumentBuilder` बनाना है। Builder आपको सामग्री, जिसमें आकार भी शामिल हैं, डालने के लिए एक फ्लुएंट API प्रदान करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` इंस्टेंस वह मुख्य ऑब्जेक्ट है जिसका उपयोग आप **आयताकार आकार डालने** और अन्य तत्वों के लिए करेंगे। यह दस्तावेज़ के भीतर वर्तमान कर्सर स्थिति को ट्रैक करता है, इसलिए कोई भी डालना ठीक उसी जगह पर होता है जहाँ आपको चाहिए।

## आयताकार आकार कैसे डालें

Builder तैयार होने पर, `InsertShape` को कॉल करें। आप `ShapeType`, चौड़ाई, और ऊँचाई पॉइंट्स में निर्दिष्ट करते हैं (1 pt ≈ 1/72 in)।

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*क्यों यह महत्वपूर्ण है*: `FillColor` और `StrokeColor` सेट करने से आयत दृश्य रूप से अलग दिखता है, जो बाद में इसे अन्य आकारों के साथ समूहित करने में मदद करता है।

## Word में आकारों को समूहित कैसे करें

आकारों को समूहित करने से आप कई वस्तुओं को एक इकाई के रूप में ले जा सकते हैं, घुमा सकते हैं, या फॉर्मेट कर सकते हैं। आयत डालने के बाद, एक और आकार (इस उदाहरण में एक दीर्घवृत्त) जोड़ें और फिर एक `GroupShape` बनाएं।

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

`InsertGroupShape` कॉल एक प्लेसहोल्डर बनाता है जो किसी भी संख्या में चाइल्ड आकारों को रख सकता है। आयत और दीर्घवृत्त को जोड़कर, आप प्रभावी रूप से **Word में आकारों को समूहित** करते हैं। समूह एक एकल आकार की तरह व्यवहार करता है—आप इसे पुनः स्थित कर सकते हैं, बॉर्डर लागू कर सकते हैं, या आकार बदल सकते हैं बिना प्रत्येक चाइल्ड के आंतरिक लेआउट को प्रभावित किए।

### प्रो टिप

समूह बनाने के बाद, आप समूह की स्थिति को पृष्ठ के सापेक्ष बदल सकते हैं:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## दस्तावेज़ को docx के रूप में सहेजें

एक बार आकार व्यवस्थित हो जाने के बाद, आपको फ़ाइल को स्थायी रूप से सहेजना होगा। `Document.Save` मेथड फ़ाइल एक्सटेंशन से स्वचालित रूप से फ़ॉर्मेट निर्धारित करता है। **दस्तावेज़ को docx के रूप में सहेजने** के लिए, ऐसे पथ को पास करें जो `.docx` पर समाप्त हो।

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

प्रोग्राम चलाने से `output.docx` बनता है। फ़ाइल को Microsoft Word में खोलें, और आपको एक हल्के‑नीले रंग का आयत और हल्के‑कोरल रंग का दीर्घवृत्त एक साथ समूहित दिखेगा। आप समूह पर क्लिक करके उसे एकल वस्तु की तरह ले जा सकते हैं।

## DocumentBuilder का प्रभावी उपयोग कैसे करें

`DocumentBuilder` केवल आकार डालने वाला नहीं है; यह टेक्स्ट, टेबल, हेडर और फुटर को भी संभालता है। जब आप आकार निर्माण को टेक्स्ट के साथ मिलाते हैं, तो यदि आपको कहीं और सामग्री डालनी हो तो कर्सर को रीसेट करना याद रखें:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Builder की स्थिति को स्पष्ट रखकर आकस्मिक ओवरराइट से बचा जा सकता है और कोड को बनाए रखना आसान हो जाता है।

## किनारे के मामलों और विविधताएँ

| स्थिति | अनुशंसित दृष्टिकोण |
|-----------|----------------------|
| **दो से अधिक आकार** | प्रत्येक आकार को Insert करें, फिर सहेजने से पहले प्रत्येक आकार के लिए `AppendChild` कॉल करें। |
| **नेस्टेड समूह** | एक समूह बनाएं, आकार जोड़ें, फिर उस समूह को दूसरे `GroupShape` में Insert करें। |
| **विभिन्न माप इकाइयाँ** | यदि आपके पास पिक्सेल में आयाम हैं तो `builder.ConvertPixelsToPoints` उपयोग करें। |
| **पुराने Word संस्करणों के साथ संगतता** | एक्सटेंशन बदलकर `.doc` के रूप में सहेजें; अधिकांश आकार सुविधाएँ अभी भी काम करती हैं। |

## पूर्ण कार्यशील उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप नई कंसोल प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं। अतिरिक्त स्निपेट्स की आवश्यकता नहीं है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**अपेक्षित परिणाम**: `output.docx` खोलने पर एक हल्के‑नीले रंग का आयत और हल्के‑कोरल रंग का दीर्घवृत्त एक साथ समूहित दिखता है, जो बाएँ मार्जिन से 150 pt और शीर्ष से 100 pt की दूरी पर स्थित है। कैप्शन समूह के नीचे दिखाई देता है।

## निष्कर्ष

अब आप जानते हैं कि C# का उपयोग करके Word फ़ाइल में **आयताकार आकार कैसे डालें**, **Word में आकारों को कैसे समूहित करें**, और Aspose.Words `DocumentBuilder` के साथ **दस्तावेज़ को docx के रूप में कैसे सहेजें**। इन चरणों में महारत हासिल करके आप जटिल लेआउट—प्रमाणपत्र, रिपोर्ट, या कस्टम फ़ॉर्म—पूरी तरह कोड के माध्यम से बना सकते हैं।

अगला, संबंधित विषयों जैसे **टेक्स्ट बॉक्स जोड़ना**, **टेबल के साथ काम करना**, या **PDF में निर्यात करना** का अन्वेषण करें। इनमें से प्रत्येक वही `DocumentBuilder` मूलभूत सिद्धांतों पर आधारित है जिसे आपने अभी अभ्यास किया है।

क्या आप अपने Word दस्तावेज़ों को स्वचालित करने के लिए तैयार हैं? उदाहरण को अधिक आकारों के साथ विस्तारित करने, ग्रेडिएंट लागू करने, या डेटा पर लूप करके एक ही रन में पूर्ण रिपोर्ट उत्पन्न करने का प्रयास करें। कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में आकार डालें](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words के साथ Word में आयताकार आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}