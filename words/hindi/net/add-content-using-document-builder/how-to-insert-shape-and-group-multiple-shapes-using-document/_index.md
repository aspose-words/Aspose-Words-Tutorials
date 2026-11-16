---
category: general
date: 2026-11-15
description: Aspose.Words DocumentBuilder के साथ Word दस्तावेज़ में आकार कैसे डालें
  और कई आकारों को समूहित करें, सीखें। इसमें आयत आकार डालने और कई आकारों को डालने के
  उदाहरण शामिल हैं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: hi
lastmod: 2026-11-15
og_description: Aspose.Words का उपयोग करके Word फ़ाइल में आकार कैसे डालें। यह गाइड
  कई आकारों को समूहित करने, आयत आकार डालने, और कई आकारों को कुशलतापूर्वक जोड़ने को
  कवर करता है।
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: DocumentBuilder के साथ आकार कैसे डालें और कई आकारों को समूहित करें
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: C# में DocumentBuilder का उपयोग करके आकार कैसे डालें और कई आकारों को समूहित
  करें
url: /hi/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DocumentBuilder का उपयोग करके C# में शैप कैसे इन्सर्ट करें और कई शैप्स को ग्रुप करें

यदि आपको **शैप को इन्सर्ट करने** का तरीका Aspose.Words के साथ जानना है, तो यह गाइड आपको सटीक चरण दिखाता है। आप यह भी सीखेंगे कि **कई शैप्स को ग्रुप** कैसे करें ताकि वे एक ही ऑब्जेक्ट की तरह व्यवहार करें, और **रेक्टैंगल शैप** को अन्य ग्राफिक्स के साथ कैसे इन्सर्ट करें।

डॉक्यूमेंट ऑटोमेशन अक्सर कई ग्राफिक्स—चार्ट, लोगो, कॉल‑आउट—जोड़ने की आवश्यकता रखता है, जबकि उन्हें व्यवस्थित रखना जरूरी होता है। इस ट्यूटोरियल के अंत तक आप **कई शैप्स इन्सर्ट** कर सकेंगे, उन्हें एक ग्रुप में रख सकेंगे, और एक साफ़, पुन: उपयोग योग्य लेआउट सेव कर सकेंगे।

## प्रीरेक्विज़िट्स

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

* .NET 6.0 या बाद का संस्करण स्थापित  
* Visual Studio 2022 (या कोई भी C# IDE)  
* Aspose.Words for .NET लाइसेंस या फ्री इवैल्यूएशन की  
* C# और Aspose.Words `DocumentBuilder` क्लास की बेसिक समझ  

आपको किसी अन्य थर्ड‑पार्टी लाइब्रेरी की जरूरत नहीं है; सभी आवश्यक चीज़ें Aspose.Words में ही शामिल हैं।

## Step 1: NuGet के माध्यम से Aspose.Words इंस्टॉल करें

Visual Studio में अपना प्रोजेक्ट खोलें और Package Manager Console में निम्न कमांड चलाएँ:

```powershell
Install-Package Aspose.Words
```

यह पैकेज `DocumentBuilder`, `Shape`, और `GroupShape` क्लासेज़ को शामिल करता है, जो इस ट्यूटोरियल में उपयोग होते हैं।

## Step 2: DocumentBuilder इंस्टेंस बनाएं – **शैप इन्सर्ट करने** की नींव

कोड की पहली कार्रवाई `DocumentBuilder` बनाना है। यह ऑब्जेक्ट आपको डॉक्यूमेंट ट्री तक सीधा एक्सेस देता है, जिससे आप शैप्स को ठीक उसी जगह रख सकते हैं जहाँ आप चाहते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*क्यों महत्वपूर्ण है*: `DocumentBuilder` एक कर्सर (इन्सर्शन पॉइंट) बनाए रखता है। हर बाद के `Insert...` कॉल इस कर्सर का उपयोग करते हैं, इसलिए हम बाद में इसे `GroupShape` के अंदर ले जाकर सभी शैप्स को एक साथ रखते हैं।

## Step 3: **रेक्टैंगल शैप** इन्सर्ट करें – पहला ग्राफिक

रेक्टैंगल अक्सर टेबल, इमेज या कॉल‑आउट के प्लेसहोल्डर के रूप में उपयोग होता है। `InsertShape` को `ShapeType.Rectangle` के साथ उपयोग करें और चौड़ाई व ऊँचाई पॉइंट्स में निर्दिष्ट करें (1 pt ≈ 1/72 in)।

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

रेक्टैंगल वर्तमान कर्सर लोकेशन पर दिखाई देगा। आप बाद में इसकी फ़िल, लाइन स्टाइल या टेक्स्ट को कस्टमाइज़ कर सकते हैं।

## Step 4: दूसरा शैप इन्सर्ट करें – विज़ुअल वैरायटी के लिए एलिप्स

एक से अधिक शैप इन्सर्ट करने से **कई शैप्स इन्सर्ट** करने का प्रदर्शन होता है। एलिप्स रेक्टैंगल के बाद डॉक्यूमेंट फ्लो में आएगा।

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

अब डॉक्यूमेंट में दो स्वतंत्र शैप्स हैं। यदि आप कर्सर को मूव करें या टेक्स्ट जोड़ें, तो शैप्स अपनी इन्सर्शन पॉइंट पर ही रहेंगे।

## Step 5: **कई शैप्स को ग्रुप** करें ताकि वे एक इकाई बनें

ग्रुपिंग आवश्यक है जब आपको कई ग्राफिक्स को एक साथ मूव, रोटेट या फॉर्मेट करना हो। नीचे दिया गया कोड `GroupShape` बनाता है, बिल्डर का कर्सर उसके अंदर ले जाता है, और फिर वही शैप्स फिर से इन्सर्ट करता है—इस बार वे ग्रुप के चाइल्ड बन जाते हैं।

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### ग्रुप क्यों उपयोग करें?

* **सिंगल‑पॉइंट ट्रांसफ़ॉर्मेशन** – एक कॉल से पूरे ग्रुप को रोटेट या रिसाइज़ करें।  
* **लॉजिकल ऑर्गनाइज़ेशन** – Word डॉक्यूमेंट ट्री ग्रुपिंग को दर्शाता है, जिससे बाद में एडिट करना आसान हो जाता है।  
* **कंसिस्टेंट लेआउट** – ग्रुप को मूव करने से उसके चाइल्ड की रिलेटिव पोजीशन बनी रहती है।

### और शैप्स जोड़ें – ग्रुप के अंदर **कई शैप्स इन्सर्ट** को विस्तारित करें

जब तक कर्सर `GroupShape` के अंदर रहता है, आप `InsertShape` को बार‑बार कॉल कर सकते हैं। उदाहरण के लिए, एक ट्रायएंगल जोड़ने के लिए:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

हर कॉल ग्रुप कॉन्टेक्स्ट को सम्मानित करती है, इसलिए ट्रायएंगल स्वचालित रूप से उसी ग्रुप सेट का हिस्सा बन जाता है।

## Step 6: डॉक्यूमेंट को सेव करें और परिणाम जांचें

सभी शैप्स इन्सर्ट करने के बाद, डॉक्यूमेंट को `.docx` फ़ाइल में सेव करें। Microsoft Word (या कोई भी कम्पैटिबल व्यूअर) में फ़ाइल खोलने पर दो अलग‑अलग शैप्स के बाद एक ग्रुपेड सेट दिखना चाहिए, जिसमें वही रेक्टैंगल, एलिप्स और ट्रायएंगल हों।

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### अपेक्षित आउटपुट

* **पहले दो शैप्स** – रेक्टैंगल और एलिप्स जो पेज पर स्वतंत्र रूप से रखे गए हैं।  
* **ग्रुपेड ब्लॉक** – रेक्टैंगल, एलिप्स और ट्रायएंगल जो Word में किसी भी शैप को क्लिक करने पर साथ‑साथ मूव होते हैं।

आप ग्रुपिंग को टेस्ट कर सकते हैं किसी भी शैप को सिलेक्ट करके; Word पूरी कलेक्शन को हाईलाइट करेगा, जिससे पुष्टि होगी कि **कई शैप्स को ग्रुप** करने का ऑपरेशन सफल रहा।

## Common pitfalls and pro tips

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Shapes appear outside the intended page | The builder’s cursor was not moved into the `GroupShape` before inserting. | Always call `builder.MoveTo(group)` **before** any `InsertShape` calls that belong to the group. |
| Group disappears after saving | The group was inserted without being added to the document’s node collection. | Use `builder.InsertNode(group)` immediately after creating the `GroupShape`. |
| Unexpected size because of document DPI | Aspose.Words uses points; if you think in pixels you may get mismatched dimensions. | Convert pixels to points (`points = pixels * 72 / 96`) or work directly in points. |
| Shapes overlap unintentionally | No explicit positioning was set; Word places them sequentially. | Set `Shape.Left` and `Shape.Top` after insertion to control exact placement. |

**Pro tip:** ग्रुपिंग के बाद आप ग्रुप की `Shapes` कलेक्शन (`group.Shapes`) को प्राप्त कर सकते हैं, जिससे आप इटरेट, रिनेम या बल्क फॉर्मेटिंग लागू कर सकते हैं।

## Step 7: उदाहरण को विस्तारित करें – आगे क्या करें?

अब जब आप **शैप इन्सर्ट करने**, **रेक्टैंगल शैप इन्सर्ट करने**, और **कई शैप्स को ग्रुप** करने के बारे में जानते हैं, तो आप आगे खोज सकते हैं:

* **ग्रुपेड शैप्स को एनिमेट** – ग्रुप पर रोटेशन या फ्लिप प्रॉपर्टीज़ सेट करें।  
* **स्टाइल्स अप्लाई करें** – `Shape.FillColor`, `Shape.LineFormat`, या `Shape.TextBox` का उपयोग करके लेबल जोड़ें।  
* **PDF में एक्सपोर्ट** – वही ग्रुपेड लेआउट `doc.Save("output.pdf")` कॉल करने पर सही रेंडर होगा।  

इन सभी एक्सटेंशन में वही `DocumentBuilder` वर्कफ़्लो दोहराया जाता है, जिससे आपका कोड साफ़ और मेंटेनेबल रहता है।

## निष्कर्ष

इस ट्यूटोरियल ने Aspose.Words के साथ Word डॉक्यूमेंट में **शैप इन्सर्ट करने**, **रेक्टैंगल शैप इन्सर्ट करने**, और **कई शैप्स को ग्रुप** करने का तरीका दिखाया, ताकि वे एक ही ऑब्जेक्ट की तरह व्यवहार करें। चरण‑दर‑चरण कोड का पालन करके आप भरोसेमंद रूप से **कई शैप्स इन्सर्ट**, उन्हें ग्रुप में व्यवस्थित, और प्रोग्रामेटिकली प्रोफेशनल‑ग्रेड डॉक्यूमेंट बना सकते हैं।

विभिन्न शैप टाइप्स, रंग, और ग्रुप ट्रांसफ़ॉर्मेशन के साथ प्रयोग करने में संकोच न करें। जब तैयार हों, तो इस पैटर्न को बड़े रिपोर्टिंग या टेम्प्लेटिंग सॉल्यूशन्स में इंटीग्रेट करें ताकि जटिल डॉक्यूमेंट लेआउट्स को ऑटोमेट किया जा सके। Happy coding!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}