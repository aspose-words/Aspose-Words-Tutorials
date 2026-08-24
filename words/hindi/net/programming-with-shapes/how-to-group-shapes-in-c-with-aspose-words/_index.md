---
category: general
date: 2026-08-23
description: Aspose.Words का उपयोग करके C# में आकृतियों को समूहित करना सीखें। यह गाइड
  यह भी बताता है कि आयताकार आकृति कैसे डालें और जटिल दस्तावेज़ों के लिए शब्द में आकृतियों
  को कैसे जोड़ें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: hi
lastmod: 2026-08-23
og_description: C# में Aspose.Words के साथ शैप्स को कैसे ग्रुप करें। आयताकार शैप डालने,
  शब्द में शैप्स जोड़ने, और कई शैप्स को प्रभावी ढंग से ग्रुप करने के लिए इस पूर्ण
  ट्यूटोरियल का पालन करें।
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: C# में आकृतियों को समूहित करने का तरीका – चरण-दर-चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Aspose.Words के साथ C# में आकृतियों को कैसे समूहित करें
url: /hi/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में Aspose.Words के साथ आकृतियों को समूहित कैसे करें

यदि आपको प्रोग्रामेटिक रूप से Word दस्तावेज़ में **how to group shapes** करने की आवश्यकता है, तो यह ट्यूटोरियल Aspose.Words for .NET का उपयोग करके सटीक चरण दिखाता है। चाहे आप रिपोर्ट जेनरेटर, टेम्पलेट इंजन, या डायग्रामिंग टूल बना रहे हों, आप सीखेंगे कि कैसे एक समूह शुरू करें, एक आयत आकृति डालें, और कोड से बाहर निकले बिना शब्द‑स्तर की सामग्री के साथ आकृतियों को जोड़ें।

आप यह भी देखेंगे कि कैसे **group multiple shapes** को एक साथ समूहित किया जाए, जो तब आवश्यक होता है जब आप वस्तुओं के संग्रह को एक इकाई के रूप में स्थानांतरित, घुमाना या शैलीबद्ध करना चाहते हैं। नीचे दिया गया उदाहरण नवीनतम Aspose.Words 24.x रिलीज़ के साथ काम करता है और केवल .NET 6 या बाद का संस्करण आवश्यक है।

## पूर्वापेक्षाएँ

- .NET 6 SDK (या कोई भी .NET संस्करण जो Aspose.Words द्वारा समर्थित है)
- Visual Studio 2022 या VS Code
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)
- C# और Aspose.Words ऑब्जेक्ट मॉडल की बुनियादी परिचितता

> **Pro tip:** परीक्षण के दौरान वॉटरमार्क सीमाओं से बचने के लिए Aspose का मुफ्त मूल्यांकन लाइसेंस उपयोग करें।

## Aspose.Words के साथ आकृतियों को समूहित करने का तरीका

नीचे एक पूर्ण, चलाने योग्य प्रोग्राम दिया गया है जो **how to start group** को प्रदर्शित करता है, एक आयत जोड़ता है, और समूह को समाप्त करता है। कोड आपके द्वारा प्रदान किए गए स्निपेट के समान तार्किक प्रवाह का अनुसरण करता है, लेकिन इसमें संदर्भ, त्रुटि संभालना, और स्पष्टता के लिए टिप्पणियाँ जोड़ी गई हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### प्रत्येक चरण का महत्व क्यों है

| चरण | उद्देश्य | यह कीवर्ड से कैसे संबंधित है |
|------|---------|--------------------------------|
| **Create a new blank document** | आकृति संचालन के लिए एक साफ़ कैनवास प्रदान करता है। | बाद में **add shapes word** के लिए मंच तैयार करता है। |
| **Initialize DocumentBuilder** | बिल्डर ऑब्जेक्ट्स डालने के लिए मुख्य API है। | **how to start group** करने से पहले आवश्यक है। |
| **StartGroupShape** | एक तार्किक कंटेनर शुरू करता है; सभी बाद की आकृतियाँ इस समूह की सदस्य बनती हैं। | सीधे **how to start group** का उत्तर देता है। |
| **InsertShape** (rectangle, ellipse, text) | समूह के भीतर व्यक्तिगत आकृतियों को रखता है। आयत कॉल **insert rectangle shape** को संतुष्ट करता है; टेक्स्ट आकृति **add shapes word** को संतुष्ट करती है। | **group multiple shapes** को दर्शाता है। |
| **EndGroupShape** | समूह को अंतिम रूप देता है ताकि आप इसे एक इकाई के रूप में स्थानांतरित या शैलीबद्ध कर सकें। | **how to group shapes** कार्यप्रवाह को पूरा करता है। |

## आयत आकृति डालना – गहन विश्लेषण

`InsertShape` मेथड एक `ShapeType` enum, चौड़ाई, और ऊँचाई स्वीकार करता है। कस्टम स्टाइलिंग के साथ **insert rectangle shape** करने के लिए, आप उदाहरण को विस्तारित कर सकते हैं:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Why style it?** स्टाइलिंग सुनिश्चित करती है कि समूह को बाद में पुनःस्थापित करने पर आयत प्रमुख दिखे। यह यह भी दर्शाता है कि आकृति गुण *समूह बंद होने से पहले* सेट किए जा सकते हैं।

## Word‑स्तर की आकृतियों को जोड़ना (add shapes word)

यदि आपको किसी आकृति के भीतर सीधे टेक्स्ट एम्बेड करना है—जिसे आमतौर पर “WordArt” या “text box” कहा जाता है—तो `ShapeType.TextPlainText` का उपयोग करें। डालने के बाद, आप `DocumentBuilder.Writeln` या आकृति की `TextBox` प्रॉपर्टी तक पहुँच कर टेक्स्ट लिख सकते हैं:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

यह **add shapes word** कीवर्ड को संतुष्ट करता है और दिखाता है कि टेक्स्ट समूह के साथ कैसे यात्रा कर सकता है।

## कई आकृतियों को समूहित करना – व्यावहारिक परिदृश्य

जब आप **group multiple shapes** करते हैं, तो आप उन्हें पोजिशनिंग, रोटेशन, या स्केलिंग के लिए एकल ऑब्जेक्ट की तरह व्यवहार कर सकते हैं। उदाहरण के लिए, समूह बंद होने के बाद आप पूरे समूह को स्थानांतरित कर सकते हैं:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

या समूह को घुमा सकते हैं:

```csharp
group.Rotation = 45; // degrees
```

ये संचालन केवल इसलिए संभव हैं क्योंकि आकृतियों का समान पैरेंट समूह है।

## किनारे के मामलों को संभालना

1. **Nested groups** – Aspose.Words समूहों के भीतर समूहों की अनुमति देता है। नेस्टेड समूह बनाने के लिए, आंतरिक समूह के लिए `EndGroupShape` कॉल करने से पहले `StartGroupShape` फिर से कॉल करें।
2. **Empty groups** – यदि आप समूह शुरू करते हैं लेकिन कभी आकृति नहीं डालते, तो भी `EndGroupShape` एक खाली कंटेनर बनाएगा। यह हानिरहित है लेकिन फ़ाइल आकार थोड़ा बढ़ा सकता है।
3. **Compatibility** – उत्पन्न DOCX Word 2010 और बाद के संस्करणों के साथ काम करता है। पुराने संस्करण समूहिंग मेटाडेटा को अनदेखा कर सकते हैं, इसलिए हमेशा लक्ष्य Word संस्करण के साथ परीक्षण करें।

## संदर्भ के लिए पूर्ण स्रोत फ़ाइल

निम्नलिखित को एक .NET कंसोल प्रोजेक्ट में `Program.cs` के रूप में सहेजें। कोड बिना किसी संशोधन के संकलित और चलाया जा सकता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### अपेक्षित आउटपुट

Opening `GroupedShapes.docx` in Microsoft Word will show:

- एक हल्के‑कोरल रंग की आयत, एक दीर्घवृत्त, और एक टेक्स्ट बॉक्स—सभी दृश्य रूप से एक साथ बंधे हुए।
- समूह के किसी भी भाग का चयन करने से पूरी समूह का चयन हो जाता है (एकल बाउंडिंग बॉक्स दिखाई देता है)।
- समूह को स्थानांतरित या घुमाने से सभी तीन आकृतियाँ साथ में चलती हैं।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं दस्तावेज़ में पहले से मौजूद आकृतियों को समूहित कर सकता हूँ?**  
A: हाँ। मौजूदा `Shape` ऑब्जेक्ट्स को प्राप्त करें, `builder.StartGroupShape()` कॉल करें, उन्हें `builder.InsertShape(existingShape)` के साथ पुनः‑डालें, फिर `EndGroupShape()` कॉल करें।

**Q: क्या समूह बनाना अंतर्निहित XML को प्रभावित करता है?**  
A: Aspose.Words एक `<w:grpSp>` तत्व जोड़ता है जिसमें प्रत्येक आकृति का `<w:sp>` नोड शामिल होता है। यह Office Open XML विनिर्देशन के साथ पूरी तरह संगत है।

**Q: यदि बाद में मुझे समूह को अलग (ungroup) करना पड़े तो?**  
A: कोई सीधा “ungroup” API नहीं है, लेकिन आप समूह की चाइल्ड आकृतियों (`group.GroupShape.Children`) पर इटररेट कर सकते हैं और उन्हें दस्तावेज़ बॉडी में कॉपी कर सकते हैं।

## अगले कदम

अब जब आप **how to group shapes** जानते हैं, तो इन संबंधित विषयों का अन्वेषण करें:

- **Apply complex formatting to grouped shapes** – ग्रेडिएंट फ़िल्स, शैडो इफ़ेक्ट्स, और लाइन स्टाइल सेट करना सीखें।
- **Export grouped shapes as images** – समूह को रास्टराइज़ करने के लिए `Shape.GetShapeRenderer().Save(...)` का उपयोग करें।
- **Create dynamic diagrams** – डेटा‑ड्रिवेन पोजिशनिंग को समूह के साथ मिलाकर स्वचालित रूप से फ्लोचार्ट बनाएं।

इनमें से प्रत्येक इस मार्गदर्शिका में कवर किए गए मूलभूत सिद्धांतों पर आधारित है और आपको अधिक समृद्ध, इंटरैक्टिव Word दस्तावेज़ बनाने में मदद करेगा।

---

*हैप्पी कोडिंग! यदि आपको यह गाइड उपयोगी लगा, तो इसे टीममेट्स के साथ साझा करें या उस रिपॉज़िटरी को स्टार दें जिसमें नमूना प्रोजेक्ट है।*

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}