---
category: general
date: 2026-10-20
description: Aspose.Words for C# का उपयोग करके नई `Hidden` प्रॉप के साथ एक आकार को
  छिपाएँ/दिखाएँ। सीखें कि कैसे आकार की दृश्यता को टॉगल करें, किनारे के मामलों को संभालें,
  और परिणाम को सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: hi
lastmod: 2026-10-20
og_description: Aspose.Words for C# का उपयोग करके नए `Hidden` प्रॉप के साथ एक आकार
  को छिपाएँ/दिखाएँ। आकार की दृश्यता टॉगल करने में निपुण बनें और सामान्य गलतियों से
  बचें।
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Aspose.Words (C#) में नए `Hidden` प्रॉप का उपयोग करके एक आकार को छिपाएँ/दिखाएँ
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words for C# में नए `Hidden` प्रॉप के साथ एक आकार को छुपाएँ/दिखाएँ
url: /hi/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for C# में नए `Hidden` प्रॉप के साथ Shape को Hide/Show करना

यदि आपको Word दस्तावेज़ में नए `Hidden` प्रॉप के साथ **Shape को Hide/Show** करने की आवश्यकता है, तो यह गाइड आपको Aspose.Words for .NET के साथ इसे बिल्कुल कैसे करना है दिखाता है। चाहे आप रिपोर्ट बना रहे हों, टेम्प्लेट बना रहे हों, या आयातित दस्तावेज़ों को साफ़ कर रहे हों, प्रोग्रामेटिक रूप से shape की दृश्यता को नियंत्रित करने से मैन्युअल संपादन से बचा जा सकता है।

इस ट्यूटोरियल में आप सीखेंगे कि कैसे एक दस्तावेज़ लोड करें, एक shape खोजें, `Hidden` प्रॉपर्टी को टॉगल करें, और संशोधित फ़ाइल को सहेजें। चरणों में कई shape को संभालने और inline बनाम floating ग्राफ़िक्स को प्रबंधित करने जैसी सामान्य विविधताएँ भी शामिल हैं।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

* .NET 6.0 (या बाद का) स्थापित – Aspose.Words .NET Standard 2.0 और .NET Core को सपोर्ट करता है।
* **Aspose.Words for .NET** की लाइसेंस प्राप्त कॉपी (नि:शुल्क ट्रायल खोज के लिए काम करता है)।
* Visual Studio 2022 या Visual Studio Code जैसे IDE।
* एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक shape हो (जैसे चित्र, SmartArt, या drawing canvas)।

## Step 1: Load the Word document

पहला ऑपरेशन एक `Document` ऑब्जेक्ट बनाना है जो डिस्क पर मौजूद .docx फ़ाइल का प्रतिनिधित्व करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this step matters*: `Document` सभी Aspose.Words ऑपरेशनों का एंट्री पॉइंट है। फ़ाइल को मेमोरी में लोड करने से आपको उसके नोड ट्री तक पूरी पहुंच मिलती है, जिसमें shapes भी शामिल हैं।

## Step 2: Retrieve the target shape

विज़िबिलिटी टॉगल करने के लिए आपको shape नोड का रेफ़रेंस प्राप्त करना होगा। नीचे दिया गया उदाहरण दस्तावेज़ में पहला shape प्राप्त करता है, लेकिन आप नाम, प्रकार, या इंडेक्स के आधार पर shape खोजने के लिए लॉजिक को अनुकूलित कर सकते हैं।

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Why this step matters*: `GetChild` के साथ `true` एक डीप सर्च करता है, जिससे आप tables या headers के अंदर नेस्टेड shapes भी पा लेते हैं। `null` की जाँच करने से `NullReferenceException` से बचा जा सकता है जब दस्तावेज़ में कोई shape न हो।

## Step 3: Hide the shape with the `Hidden` property

Aspose.Words ने `Hidden` प्रॉपर्टी पेश की है जिससे यह नियंत्रित किया जा सकता है कि shape रेंडर या प्रिंट हो या नहीं। इसे `true` सेट करने से shape छिप जाता है; `false` सेट करने से shape फिर से दिखाई देता है।

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

यदि आपको पहले छिपाए गए shape को **show** करना है, तो बस `false` असाइन करें:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Why this step matters*: `Hidden` प्रॉपर्टी floating और inline दोनों shapes के लिए काम करती है, और यह Word के मूल “Hidden” फ़ॉर्मेटिंग के साथ इंटीग्रेट होती है। यह तरीका shape को हटाने की तुलना में अधिक भरोसेमंद है क्योंकि नोड दस्तावेज़ ट्री में बना रहता है, लेआउट और रेफ़रेंसेज़ संरक्षित रहती हैं।

## Step 4: Save the modified document

विज़िबिलिटी समायोजित करने के बाद, बदलावों को नई फ़ाइल में (या इच्छानुसार मूल फ़ाइल को ओवरराइट) लिखें।

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Why this step matters*: `Save` इन‑मेरी नोड ट्री को .docx पैकेज में सीरियलाइज़ करता है जिसे Word खोल सकता है। hidden फ़्लैग स्थायी रहता है, इसलिए Microsoft Word में फ़ाइल खोलने पर shape `Hidden` सेटिंग के अनुसार दिखेगा या नहीं।

## Full, runnable example

सभी चरणों को मिलाकर आपको एक स्व-निहित प्रोग्राम मिलता है जिसे आप कॉपी, कंपाइल और रन कर सकते हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Expected output** when you run the program:

```
Document saved. Shape hidden = True
```

`ShapeHidden.docx` को Microsoft Word में खोलने पर लक्ष्य shape के बिना दस्तावेज़ दिखेगा। यदि आप `shape.Hidden = false;` को सहेजने से पहले सेट करते हैं, तो shape फिर से प्रकट हो जाएगा।

## Handling multiple shapes

उपरोक्त उदाहरण एकल shape के लिए काम करता है। वास्तविक दुनिया के दस्तावेज़ों में अक्सर कई ग्राफ़िक्स होते हैं। सभी उन shapes को छिपाने या दिखाने के लिए जो किसी शर्त को पूरा करती हैं (जैसे विशिष्ट नाम या प्रकार) एक लूप का उपयोग करें।

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tip*: `ShapeType` द्वारा फ़िल्टर करने से अनजाने में decorative तत्वों जैसे text boxes या SmartArt को छिपाने से बचा जा सकता है।

## Edge cases and best practices

| Situation | Recommended handling |
|-----------|----------------------|
| **Shape is inside a header/footer** | पहले header/footer नोड प्राप्त करें, फिर उस sub‑document पर `GetChild(NodeType.Shape, …)` कॉल करें। |
| **Document contains no shapes** | `GetChild` के बाद हमेशा `null` की जाँच करें या `doc.GetChildNodes(NodeType.Shape, true).Count` को सत्यापित करें। |
| **You need to preserve the hidden flag across different Word versions** | `Hidden` प्रॉपर्टी shape के XML में `<w:hidden/>` के रूप में संग्रहीत होती है, जो Word 2007 और बाद के संस्करणों द्वारा समर्थित है। |
| **Performance with large documents** | `doc.GetChildNodes(NodeType.Shape, true)` को एक बार कॉल करें और संग्रह को पुन: उपयोग करें, बजाय बार‑बार `GetChild` कॉल करने के। |

## Pro tip: Combine `Hidden` with `WrapType`

जब कोई shape छिपा होता है, तब तक Word उस स्थान को रिज़र्व करता है जब तक आप उसकी wrapping व्यवहार नहीं बदलते। `WrapType = WrapType.None` सेट करने से प्लेसहोल्डर एरिया हट जाता है।

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

यह लेआउट को ऐसे संकुचित करता है जैसे shape कभी मौजूद ही न रहा हो, जो साफ़ रिपोर्ट जनरेट करने में उपयोगी है।

## Conclusion

अब आप Aspose.Words for C# में नए `Hidden` प्रॉप का उपयोग करके **Shape को Hide/Show** करना जानते हैं। समाधान में दस्तावेज़ लोड करना, shape ढूँढ़ना, `Hidden` प्रॉपर्टी टॉगल करना, और परिवर्तन को सहेजना शामिल है। सर्वोत्तम प्रैक्टिस टिप्स—null की जाँच, कई shapes को संभालना, और wrap सेटिंग्स को समायोजित करना—का पालन करके आप किसी भी Word ऑटोमेशन परिदृश्य में shape की दृश्यता को भरोसेमंद रूप से नियंत्रित कर सकते हैं।

आगे क्या सीखें?

* **Hide/Show multiple shapes** based on custom metadata (uses the “programmatically hide shape” technique).
* **Combine `Hidden` with conditional content** using Aspose.Words fields for dynamic report generation.
* **Explore other node properties**, such as `Visible` for chart objects or `IsDeleted` for paragraph-level control.

Happy coding, and enjoy the fine‑grained control that Aspose.Words provides for Word document shape visibility!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}