---
category: general
date: 2026-09-21
description: Aspose.Words का उपयोग करके एक खाली Word दस्तावेज़ बनाएं, आकार सेट करें,
  स्थिति सेट करें, रंग सेट करें, और एक ही चरण में docx फ़ाइल को सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: hi
lastmod: 2026-09-21
og_description: एक खाली Word दस्तावेज़ बनाएं, आकार सेट करें, स्थिति सेट करें, रंग
  सेट करें, और मिनटों में Aspose.Words के साथ docx फ़ाइल सहेजें।
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: एक खाली Word दस्तावेज़ बनाएं और रंगीन आकार जोड़ें – Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Aspose.Words के साथ एक खाली Word दस्तावेज़ बनाएं और रंगीन आकार जोड़ें
url: /hi/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ एक खाली Word दस्तावेज़ बनाएं और रंगीन आकार जोड़ें

यदि आपको प्रोग्रामेटिक रूप से **एक खाली Word दस्तावेज़ बनाना** है, तो यह गाइड Aspose.Words के साथ यह दिखाता है। आप सीखेंगे कि कैसे **आकार का आकार सेट करें**, **आकार की स्थिति सेट करें**, **आकार का रंग सेट करें**, और अंत में **docx फ़ाइल को सहेजें** बिना अपने IDE से निकले।

C# में Word फ़ाइलों के साथ काम करना अक्सर लो‑लेवल OpenXML कॉल्स को संभालने जैसा होता है, लेकिन Aspose.Words जटिलता को सरल बनाता है। इस ट्यूटोरियल के अंत तक आपके पास एक पूरी तरह कार्यशील `.docx` होगा जिसमें दो रंगीन आयतों से बना एक समूहित आकार होगा—रिपोर्ट, प्रमाणपत्र, या कस्टम टेम्प्लेट्स के लिए एकदम उपयुक्त।

## आवश्यकताएँ

- .NET 6.0 या बाद का (कोड .NET Framework 4.7+ के साथ भी काम करता है)
- Aspose.Words for .NET 23.9 या नया (NuGet के माध्यम से इंस्टॉल करें: `Install-Package Aspose.Words`)
- C# और Visual Studio (या कोई भी C# एडिटर) की बुनियादी जानकारी

कोई मौजूदा Word फ़ाइल आवश्यक नहीं है; ट्यूटोरियल **एक खाली Word दस्तावेज़ बनाकर** शुरू होता है।

## Aspose.Words के साथ एक खाली Word दस्तावेज़ बनाएं

पहला कदम `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट मेमोरी में एक खाली Word फ़ाइल का प्रतिनिधित्व करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` शुरू में खाली होता है, जो कि **एक खाली Word दस्तावेज़ बनाने** के लिए बिल्कुल सही है। `builder` बाद में वर्तमान कर्सर स्थान पर आकार समूह डालने के लिए उपयोग किया जाएगा।

## आकार का आकार सेट करें और GroupShape बनाएं

`GroupShape` एक कंटेनर की तरह काम करता है जो कई व्यक्तिगत आकारों को रख सकता है। पहले, कंटेनर के कुल आयाम निर्धारित करें।

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

यहाँ हम समूह के लिए **आकार का आकार सेट** करते हैं (300 × 200)। वही प्रॉपर्टी नाम (`Width`, `Height`) प्रत्येक चाइल्ड आकार के लिए उपयोग होते हैं, जिससे आपको हर तत्व पर सूक्ष्म नियंत्रण मिलता है।

## पहला आयत जोड़ें और आकार का रंग सेट करें

अब समूह में एक आयत जोड़ें और उसे बैकग्राउंड रंग दें।

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

`FillColor` प्रॉपर्टी **आकार का रंग सेट** करती है। `System.Drawing.Color` का उपयोग करके आप कोई भी प्री‑डिफाइंड या कस्टम ARGB मान चुन सकते हैं।

## दूसरा आयत जोड़ें, उसका आकार, स्थिति और रंग सेट करें

दूसरा आयत दिखाता है कि कैसे **आकार की स्थिति सेट** करें समूह के सापेक्ष और उसका रंग कैसे बदलें।

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

चूंकि समूह की चौड़ाई 300 पॉइंट है, दो 120‑पॉइंट आयतें 30‑पॉइंट गैप के साथ आराम से फिट होती हैं। यदि आपको अलग लेआउट चाहिए तो `Left` और `Top` को समायोजित करें।

## GroupShape को दस्तावेज़ में डालें

समूह पूरी तरह कॉन्फ़िगर हो जाने के बाद, इसे वर्तमान कर्सर स्थान पर रखें।

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` आकार को सीधे दस्तावेज़ के बॉडी में लिखता है, जिससे पहले परिभाषित **सेट आकार स्थिति** ठीक वैसी ही बनी रहती है।

## docx फ़ाइल सहेजें

अंतिम कदम दस्तावेज़ को डिस्क पर सहेजना है। यह **docx फ़ाइल सहेजें** ऑपरेशन को दर्शाता है।

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

प्रोग्राम चलाने के बाद, Microsoft Word में `GroupShape.docx` खोलें। आपको एक खाली पेज दिखेगा जिसमें दो रंगीन आयतों वाला एक समूहित आकार साइड‑बाय‑साइड स्थित होगा।

### अपेक्षित आउटपुट

- एक सिंगल‑पेज `.docx` फ़ाइल।
- पेज में एक समूहित आकार है जो बाएँ और ऊपर के मार्जिन से 100 पॉइंट दूर स्थित है।
- समूह के भीतर, एक हल्का‑नीला आयत बाएँ ओर है, और एक हल्का‑कोरल आयत दाएँ ओर है, प्रत्येक का आकार 120 × 80 पॉइंट है।

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी‑पेस्ट करके एक कंसोल एप्लिकेशन में उपयोग कर सकते हैं। अतिरिक्त फ़ाइलों की आवश्यकता नहीं है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

इस प्रोग्राम को चलाने से पहले वर्णित वही दस्तावेज़ बनता है, जो चारों उद्देश्यों को पूरा करता है: **एक खाली Word दस्तावेज़ बनाना**, **आकार का आकार सेट करना**, **आकार की स्थिति सेट करना**, **आकार का रंग सेट करना**, और **docx फ़ाइल सहेजना**।

## सामान्य विविधताएँ और किनारे के मामलों

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **विभिन्न आकार प्रकार** | Replace `ShapeType.Rectangle` with `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. | बिना बाहरी इमेज़ के अधिक जटिल ग्राफ़िक्स बनाने की अनुमति देता है। |
| **डायनामिक आयाम** | Compute `Width` and `Height` from user input or configuration files. | समाधान को कई दस्तावेज़ टेम्प्लेट्स में पुन: उपयोग योग्य बनाता है। |
| **PDF के रूप में सहेजना** | Call `document.Save("output.pdf", SaveFormat.Pdf);` | यदि प्राप्तकर्ताओं को गैर‑संपादन योग्य फ़ॉर्मेट चाहिए, तो PDF एक सुरक्षित विकल्प है। |
| **आकार के अंदर टेक्स्ट जोड़ना** | Create a `TextBox` shape and set `TextBox.Text`. | लेबल वाले बैज या कॉलआउट बनाने के लिए उपयोगी। |
| **एक पेज पर कई समूह** | Repeat steps 2‑5 with different `Left`/`Top` values. | डैशबोर्ड या मल्टी‑सेक्शन लेआउट बनाने में सक्षम बनाता है। |

### प्रो टिप

जब आपको आकारों को सटीक रूप से संरेखित करने की आवश्यकता हो, तो समूह डालने से पहले `ShapeBase.WrapType = WrapType.Inline` प्रॉपर्टी का उपयोग करें। यह समूह को पैराग्राफ की तरह व्यवहार करने के लिए मजबूर करता है, जिससे उसके आसपास अनपेक्षित टेक्स्ट फ्लो नहीं होता।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words के साथ **एक खाली Word दस्तावेज़ कैसे बनाएं**, **आकार का आकार सेट करें**, **आकार की स्थिति सेट करें**, **आकार का रंग सेट करें**, और **docx फ़ाइल सहेजें**। पूरा उदाहरण किसी भी Word ऑटोमेशन प्रोजेक्ट में समूहित ग्राफ़िक्स जोड़ने के लिए एक साफ़, पुन: उपयोग योग्य पैटर्न दर्शाता है।

अब आप आगे खोज सकते हैं:

- उसी `GroupShape` में अधिक आकार या इमेज़ जोड़ना (**आकार का आकार**, **आकार का रंग** विविधताएँ)।
- सजावटी प्रभावों के लिए आयतों को घुमाने हेतु `ShapeBase.Rotation` का उपयोग करना।
- वितरण को विस्तृत करने के लिए उसी दस्तावेज़ को PDF या HTML के रूप में एक्सपोर्ट करना (**docx फ़ाइल सहेजें** विकल्प)।

विभिन्न रंगों, आकारों और लेआउट लॉजिक के साथ प्रयोग करने में संकोच न करें ताकि आपके विशिष्ट रिपोर्टिंग या टेम्प्लेटिंग आवश्यकताओं के अनुरूप हो सके। कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करती हैं।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [C# का उपयोग करके Word में आयत आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words आकार शैडो ट्यूटोरियल – C# में Word आकार में शैडो जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}