---
category: general
date: 2026-10-04
description: C# का उपयोग करके Word में आकृतियों को समूहित करना सीखें। यह गाइड दिखाता
  है कि आयताकार आकृति कैसे डालें, कई आकृतियों को समूहित करें, और प्रोग्रामेटिक रूप
  से एक खाली Word फ़ाइल बनाएं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: hi
lastmod: 2026-10-04
og_description: C# का उपयोग करके Word में आकारों को समूहित करें। आयताकार आकार डालने,
  कई आकारों को समूहित करने और DocumentBuilder के साथ एक खाली Word फ़ाइल बनाने के लिए
  इस चरण‑दर‑चरण गाइड का पालन करें।
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: C# के साथ Word में आकृतियों को समूहित करें – पूर्ण DocumentBuilder ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: C# और DocumentBuilder का उपयोग करके Word में आकृतियों को कैसे समूहित करें
url: /hi/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में C# और DocumentBuilder के साथ शैप्स को समूहित कैसे करें

यदि आपको C# एप्लिकेशन से Word में **शैप्स को समूहित** करने की आवश्यकता है, तो यह ट्यूटोरियल आपको ठीक-ठीक दिखाएगा कि इसे कैसे किया जाए। आप देखेंगे कि *रेक्टैंगल शैप कैसे डालें*, कई ड्रॉइंग को एक समूह में कैसे मिलाएँ, और अंत में **एक खाली Word फ़ाइल बनाएँ** जिसमें समूहित ऑब्जेक्ट्स हों।

शैप्स के साथ काम करना रिपोर्ट, इनवॉइस, या कस्टम टेम्प्लेट्स को प्रोग्रामेटिकली जनरेट करने की एक सामान्य आवश्यकता है। इस गाइड के अंत तक आपके पास एक पुन: उपयोग योग्य कोड स्निपेट होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं जो Aspose.Words को रेफ़र करता है।

## आप क्या सीखेंगे

- शुरू से एक खाली Word दस्तावेज़ बनाएँ।  
- `DocumentBuilder` का उपयोग करके एक रेक्टैंगल शैप और एक एलिप्स डालें।  
- **कई शैप्स को समूहित** करें `GroupShape` में।  
- हाइरार्की बनाने के लिए **append child to group** का उपयोग करें।  
- फ़ाइल को डिस्क पर सहेजें और परिणाम सत्यापित करें।

Aspose.Words का पूर्व अनुभव आवश्यक नहीं है, लेकिन आपके पास C# और .NET विकास की बुनियादी समझ होनी चाहिए।

## पूर्वापेक्षाएँ

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 या बाद का | C# कोड के लिए रनटाइम प्रदान करता है। |
| Aspose.Words for .NET (नवीनतम संस्करण) | `Document`, `DocumentBuilder`, और शैप क्लासेज़ प्रदान करता है। |
| Visual Studio 2022 (या VS Code) जैसे IDE | सैंपल को कंपाइल और रन करना आसान बनाता है। |
| आपके मशीन पर किसी फ़ोल्डर में लिखने की अनुमति | `doc.save` कॉल के लिए आवश्यक है। |

NuGet के माध्यम से Aspose.Words स्थापित करें:

```bash
dotnet add package Aspose.Words
```

---

## Word में शैप्स को समूहित करना – चरण‑दर‑चरण गाइड

नीचे पूरा, चलाने योग्य प्रोग्राम दिया गया है। प्रत्येक सेक्शन को विस्तार से समझाया गया है ताकि आप समझ सकें कि कोड इस तरह क्यों लिखा गया है, न कि केवल **क्या** यह करता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### प्रत्येक चरण का महत्व क्यों है

1. **एक खाली Word फ़ाइल बनाएँ** – एक साफ़ दस्तावेज़ से शुरू करने से यह सुनिश्चित होता है कि कोई छिपा हुआ फॉर्मेटिंग शैप की पोजीशन में बाधा न डाले।  
2. **DocumentBuilder को इनिशियलाइज़ करें** – `DocumentBuilder` लो‑लेवल नोड मैनिपुलेशन को एब्स्ट्रैक्ट करता है, जिससे आप लेआउट पर ध्यान केंद्रित कर सकते हैं।  
3. **व्यक्तिगत शैप्स डालें** – समूह बनाने से पहले आपको अलग-अलग ऑब्जेक्ट्स (`insert rectangle shape` और एक एलिप्स) चाहिए। `Left` और `Top` को समायोजित करने से वे साइड‑बाय‑साइड दिखेंगे।  
4. **कई शैप्स को समूहित करें** – `GroupShape` बनाकर और **append child to group** का उपयोग करके, आप दो स्वतंत्र ड्रॉइंग्स को एक लॉजिकल यूनिट में बदलते हैं। समूह को मूव या रिसाइज़ करने से दोनों चाइल्ड एक साथ प्रभावित होंगे।  
5. **दस्तावेज़ सहेजें** – अंतिम फ़ाइल, `GroupedShapes.docx`, को Microsoft Word में खोलकर यह सत्यापित किया जा सकता है कि रेक्टैंगल और एलिप्स वास्तव में समूहित हैं (एक को चुनें, और दोनों साथ में मूव होते हैं)।

### अपेक्षित आउटपुट

Open `GroupedShapes.docx` in Microsoft Word:

- आपको एक रेक्टैंगल और एक एलिप्स एक-दूसरे के बगल में दिखाई देंगे।  
- किसी भी शैप को चुनने से दोनों हाइलाइट हो जाएंगे, जिससे पुष्टि होगी कि वे एक ही समूह के हैं।  
- समूह को एकल ऑब्जेक्ट की तरह ड्रैग, रिसाइज़ या फॉर्मेट किया जा सकता है।

![Word दस्तावेज़ में समूहित रेक्टैंगल और एलिप्स का चित्र](https://example.com/grouped-shapes.png){: .center-image alt="Word दस्तावेज़ में समूहित रेक्टैंगल और एलिप्स का चित्र"}

*स्क्रीनशॉट अंतिम समूहित शैप्स को दर्शाता है।*

---

## रेक्टैंगल शैप डालें – आकार और शैली को अनुकूलित करना

यदि आपको एक विशिष्ट फ़िल रंग या बॉर्डर वाला रेक्टैंगल चाहिए, तो डालने के बाद `Shape` ऑब्जेक्ट को संशोधित करें:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

ये प्रॉपर्टीज़ `Shape` क्लास का हिस्सा हैं, और ये किसी भी शैप प्रकार के लिए काम करती हैं, केवल रेक्टैंगल के लिए नहीं। **append child to group** करने से पहले शैली को समायोजित करने से समूह आपके सेट किए गए विज़ुअल प्रॉपर्टीज़ को इनहेरिट करता है।

---

## कई शैप्स को समूहित करें – दो से अधिक ऑब्जेक्ट्स को संभालना

उदाहरण में एक रेक्टैंगल और एक एलिप्स को समूहित किया गया है, लेकिन आप किसी भी संख्या में शैप्स जोड़ सकते हैं:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Pro tip:** एक जटिल समूह बनाने के बाद, आप उसकी लेआउट को लॉक कर सकते हैं ताकि आकस्मिक बदलावों से बचा जा सके:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – क्रम महत्वपूर्ण है

`AppendChild` को कॉल करने का क्रम Z‑order निर्धारित करता है (कौन सा शैप ऊपर दिखेगा)। इस उदाहरण में, पहले रेक्टैंगल जोड़ा जाता है, फिर एलिप्स, इसलिए यदि वे इंटरसेक्ट करते हैं तो एलिप्स रेक्टैंगल के ऊपर ओवरले करेगा। क्रम बदलना इतना ही सरल है जितना `RemoveChild` को कॉल करके फिर से जोड़ना:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## खाली Word फ़ाइल बनाएं – पुन: उपयोग योग्य हेल्पर मेथड

यदि आपके एप्लिकेशन को अक्सर एक नया दस्तावेज़ चाहिए, तो निर्माण लॉजिक को एन्कैप्सुलेट करें:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

आप फिर मुख्य प्रोग्राम में `new Document()` लाइन को `CreateBlankWordFile()` से बदल सकते हैं। यह **create blank word file** अवधारणा को पुन: उपयोग योग्य तरीके से दर्शाता है।

---

## सामान्य समस्याएँ और उन्हें कैसे टालें

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| शैप्स ऑफ‑पेज दिखते हैं | डिफ़ॉल्ट `Left`/`Top` मान 0 होते हैं, जिससे शैप मार्जिन पर रख दिया जाता है। | डालने के बाद `Left` और `Top` को स्पष्ट रूप से सेट करें। |
| समूह का फॉर्मेटिंग खो जाता है | समूह में जोड़ने के बाद किसी चाइल्ड शैप को बदलने से समूह का लेआउट टूट सकता है। | सभी विज़ुअल प्रॉपर्टीज़ **AppendChild** कॉल करने से **पहले** लागू करें। |
| सहेजी गई फ़ाइल खाली है | `DocumentBuilder` का उपयोग कभी नोड जोड़ने के लिए नहीं किया गया, या `doc.Save` किसी अलग `Document` इंस्टेंस पर कॉल किया गया। | सुनिश्चित करें कि आप वही `Document` सहेज रहे हैं जिसे आपने बनाया था। |
| Word में संगतता चेतावनियाँ | नए शैप फीचर्स का उपयोग जो समर्थित नहीं हैं |  |

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में ग्रुप शैप बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में शैप्स डालें](/words/english/net/working-with-shapes/insert-shape/)
- [C# का उपयोग करके Word में रेक्टैंगल शैप बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}