---
category: general
date: 2026-09-21
description: Aspose.Words for C# का उपयोग करके Word में आकृतियों को समूहित करना सीखें।
  यह चरण‑दर‑चरण मार्गदर्शिका समूहित आकृतियों को बनाने, स्थित करने और सहेजने को कवर
  करती है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: hi
lastmod: 2026-09-21
og_description: Aspose.Words for C# का उपयोग करके Word में आकारों को समूहित करें।
  इस संक्षिप्त ट्यूटोरियल का पालन करके प्रोग्रामेटिकली समूहित आकार बनाएं, उनका स्थान
  निर्धारित करें, और उन्हें सहेजें।
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Aspose.Words के साथ Word में आकारों को समूहित करें – पूर्ण C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words for C# के साथ Word में आकृतियों को कैसे समूहित करें
url: /hi/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for C# के साथ Word में आकृतियों को समूहित करने का तरीका

यदि आपको प्रोग्रामेटिक रूप से **Word में आकृतियों को समूहित** करने की आवश्यकता है, तो Aspose.Words इसे सरल बनाता है। यह ट्यूटोरियल दिखाता है कि दो आयताकार आकृतियों को कैसे बनाएं, उन्हें एक‑दूसरे के बगल में रखें, उन्हें `GroupShape` में मिलाएँ, और परिणाम को DOCX फ़ाइल के रूप में सहेजें।

आप एक पूर्ण, चलाने योग्य उदाहरण, प्रत्येक चरण के महत्व की व्याख्याएँ, और ओवरलैपिंग आकृतियों या डायनामिक साइजिंग जैसे सामान्य किनारे के मामलों को संभालने के टिप्स देखेंगे। इस गाइड के अंत तक आप किसी भी Word ऑटोमेशन प्रोजेक्ट में आकृति समूह बनाना एकीकृत कर सकते हैं।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 (या बाद का) स्थापित – Aspose.Words .NET Standard 2.0+, .NET Core, और .NET Framework को सपोर्ट करता है।
* एक वैध Aspose.Words for .NET लाइसेंस (या अस्थायी एवाल्यूएशन कुंजी) – लाइसेंस के बिना लाइब्रेरी काम करती है लेकिन वॉटरमार्क जोड़ती है।
* Visual Studio 2022 (या कोई भी C# IDE) ताकि आप सैंपल को कंपाइल और रन कर सकें।

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## Aspose.Words का उपयोग करके Word में आकृतियों को समूहित करने का तरीका

समाधान का मूल भाग एक **`GroupShape`** ऑब्जेक्ट है जो व्यक्तिगत आकृतियों के लिए कंटेनर के रूप में कार्य करता है। नीचे हम प्रक्रिया को स्पष्ट चरणों में विभाजित करते हैं।

### Step 1: Create a blank document and a `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step?*  
`Document` पूरे DOCX फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` फ़्लुएंट मेथड्स (जैसे `InsertShape`) प्रदान करता है जो स्वचालित रूप से नए तत्वों को वर्तमान कर्सर स्थिति पर रखता है।

### Step 2: Insert the first rectangle shape

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

`InsertShape` कॉल आकृति को दस्तावेज़ में जोड़ती है और एक `Shape` ऑब्जेक्ट लौटाती है जिसे आप आगे कॉन्फ़िगर कर सकते हैं (रंग, बॉर्डर आदि)। आकार पॉइंट्स में व्यक्त किया जाता है (1 pt ≈ 1/72 in)।

### Step 3: Insert the second rectangle and offset it

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

`Left` सेट करने से आकृति पेज मार्जिन के सापेक्ष स्थित होती है। ऑफ़सेट पहली आकृति की चौड़ाई (100 pt) से बड़ा होना चाहिए ताकि ओवरलैप न हो; हम 120 pt का उपयोग करते हैं जिससे एक छोटा गैप बनता है।

### Step 4: Create a `GroupShape` large enough for both rectangles

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` को मालिक `Document` और कंटेनर के आयाम चाहिए होते हैं। कंटेनर की चौड़ाई सबसे दूर स्थित आकृति के दाएँ किनारे से अधिक होनी चाहिए; अन्यथा दूसरी आकृति क्लिप हो जाएगी।

### Step 5: Append the individual shapes to the group

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

ऐपेंड करने से आकृतियों को समूह की आंतरिक कलेक्शन में ले जाया जाता है। इस कॉल के बाद आकृतियाँ दस्तावेज़ ट्री में स्वतंत्र ऑब्जेक्ट नहीं रहतीं—वे समूह की सदस्य बन जाती हैं।

### Step 6: Insert the grouped shape back into the document

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` पूरी `GroupShape` को उस स्थान पर रखता है जहाँ कर्सर वर्तमान में स्थित है। यदि आपको समूह को किसी विशिष्ट पैराग्राफ में चाहिए, तो पहले बिल्डर को उस पैराग्राफ पर ले जाएँ।

### Step 7: Save the document

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

परिणामी फ़ाइल में दो आयतें एक ही ऑब्जेक्ट की तरह व्यवहार करती हैं—आप उन्हें Microsoft Word में साथ‑साथ मूव, रिसाइज़ या डिलीट कर सकते हैं।

## Full source code

सभी चरणों को मिलाकर एक स्व-निहित प्रोग्राम बनता है:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Expected output:** Microsoft Word में *GroupedShapes.docx* खोलने पर दो आयतें बगल‑बगल दिखेंगी, जिन्हें एक ही चयन योग्य ऑब्जेक्ट के रूप में माना जाएगा। समूह को ड्रैग करने से दोनों आयतें साथ‑साथ मूव होंगी।

## Common variations and edge cases

| Situation | Recommended adjustment |
|-----------|------------------------|
| **More than two shapes** | अतिरिक्त `Shape` ऑब्जेक्ट बनाएँ, उन्हें उचित रूप से स्थित करें, और प्रत्येक को उसी `GroupShape` में जोड़ें। |
| **Dynamic size** | चाइल्ड आकृतियों के अधिकतम `Right` और `Bottom` मानों के आधार पर समूह की चौड़ाई/ऊँचाई की गणना करें। |
| **Different shape types** | `ShapeType.Ellipse`, `ShapeType.Triangle` आदि को भी उसी तरह इन्सर्ट किया जा सकता है; समूह कंटेनर प्रकार की परवाह नहीं करता। |
| **Rotated shapes** | `shape.Rotation = 45;` को ऐपेंड करने से पहले सेट करें; रोटेशन समूह के भीतर संरक्षित रहता है। |
| **Saving as PDF** | `doc.Save("GroupedShapes.pdf");` कॉल करें – समूह PDF रेंडरिंग में बरकरार रहता है। |

**Pro tip:** समूह बनाने के बाद भी आप `group.GetChildNodes(NodeType.Shape, true)` के माध्यम से व्यक्तिगत आकृतियों को संशोधित कर सकते हैं। यह तब उपयोगी होता है जब आप किसी एक आयत का फ़िल रंग बदलना चाहते हैं बिना समूह को तोड़े।

## How to verify the grouping programmatically

यदि आपको यह पुष्टि करनी है कि आकृतियाँ सही ढंग से समूहित हुई हैं (जैसे यूनिट टेस्ट में), तो दस्तावेज़ नोड हायरार्की को देखें:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

आउटपुट इस प्रकार होना चाहिए:

```
Number of groups: 1
Children in first group: 2
```

यह पुष्टि करता है कि **Word में समूहित आकृतियाँ** अपेक्षित रूप से बनाई गई हैं।

## Conclusion

अब आप जानते हैं कि Aspose.Words for C# के साथ **Word में आकृतियों को समूहित** कैसे किया जाता है। प्रक्रिया में व्यक्तिगत आकृतियों का निर्माण, उनका स्थान निर्धारण, उन्हें `GroupShape` में लपेटना, और समूह को दस्तावेज़ में पुनः सम्मिलित करना शामिल है। ऊपर दिया गया पूर्ण उदाहरण आपको किसी भी संख्या में आकृतियों, विभिन्न प्रकारों, या यहाँ तक कि टेक्स्ट बॉक्स और इमेज़ के साथ संयोजन करने की अनुमति देता है।

अगला, संबंधित विषयों का अन्वेषण करें जैसे **Aspose.Words shape grouping**, **C# Word shape manipulation**, और **DocumentBuilder insert shape** ताकि आप अधिक उन्नत दस्तावेज़ ऑटोमेशन परिदृश्यों को लागू कर सकें। डायनामिक साइजिंग, कंडीशनल ग्रुपिंग, और PDF में एक्सपोर्ट करने के साथ प्रयोग करें ताकि Aspose.Words की शक्ति का पूर्ण लाभ उठा सकें।

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को खोज सकें।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में आकृतियों को सम्मिलित करें](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words के साथ Word में आयताकार आकृति बनाएं – चरण-दर-चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words आकृति छाया ट्यूटोरियल – C# में Word आकृति में छाया जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}