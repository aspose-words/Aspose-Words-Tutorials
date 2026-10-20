---
category: general
date: 2026-03-30
description: C# का उपयोग करके Word आकृति पर शैडो सेट करना सीखें। यह गाइड दिखाता है
  कि कैसे आकृति में शैडो जोड़ें, आकृति की पारदर्शिता समायोजित करें, और आयताकार शैडो
  जोड़ें।
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: hi
og_description: C# में Word के आकार पर शैडो कैसे सेट करें? आकार पर शैडो जोड़ने, आकार
  की पारदर्शिता समायोजित करने और आयताकार शैडो जोड़ने के लिए इस चरण‑दर‑चरण गाइड का
  पालन करें।
og_title: Word आकृति पर शैडो कैसे सेट करें – C# ट्यूटोरियल
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Word Shape पर छाया कैसे सेट करें – C# ट्यूटोरियल
url: /hi/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Set Shadow on a Word Shape – C# Tutorial

क्या आपने कभी **शैडो सेट करने** के बारे में सोचा है किसी Word दस्तावेज़ में शैप पर बिना UI के झंझट के? आप अकेले नहीं हैं। कई रिपोर्ट या मार्केटिंग डेक में एक सूक्ष्म ड्रॉप‑शैडो एक आयत को उभार देता है, और इसे प्रोग्रामेटिकली करना घंटों बचा सकता है।

इस गाइड में हम एक पूर्ण, तैयार‑चलाने‑योग्य उदाहरण के माध्यम से चलेंगे जो न केवल **शैडो सेट करने** को दिखाता है, बल्कि **add shape shadow**, **adjust shape transparency**, और यहाँ तक कि **add rectangle shadow** को भी कवर करता है उन क्लासिक कॉल‑आउट बॉक्सों के लिए। अंत तक आपके पास एक Word फ़ाइल (`output.docx`) होगी जो परिष्कृत दिखेगी, और आप समझेंगे कि प्रत्येक प्रॉपर्टी क्यों महत्वपूर्ण है।

## Prerequisites

- .NET 6+ (या .NET Framework 4.7.2) के साथ एक C# कंपाइलर  
- Aspose.Words for .NET NuGet पैकेज (`Install-Package Aspose.Words`)  
- C# और Word के ऑब्जेक्ट मॉडल की बुनियादी समझ  

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं—सभी चीज़ें Aspose.Words के भीतर रहती हैं।

---

## How to Set Shadow on a Word Shape in C#

नीचे पूरा स्रोत फ़ाइल दिया गया है। इसे `Program.cs` के रूप में सेव करें और अपने IDE या `dotnet run` से चलाएँ। कोड एक मौजूदा `.docx` को लोड करता है, पहला शैप (डिफ़ॉल्ट रूप से एक आयत) खोजता है, उसकी शैडो को चालू करता है, कुछ दृश्य पैरामीटर समायोजित करता है, और परिणाम को सेव करता है।

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **What you’ll see** – आयत अब एक काली ड्रॉप‑शैडो के साथ है जो 30 % पारदर्शी है, 5 pt दाएँ और नीचे शिफ्ट हुई है, और हल्का ब्लर है। `output.docx` को Word में खोलकर पुष्टि करें।

## Adjust Shape Transparency – Why It Matters

पारदर्शिता केवल एक सौंदर्यात्मक नॉब नहीं है; यह पठनीयता को प्रभावित करती है। 0.0 मान शैडो को पूरी तरह अपारदर्शी बनाता है, जबकि 1.0 इसे पूरी तरह छिपा देता है। ऊपर के स्निपेट में हमने `0.3` का उपयोग किया है ताकि एक सूक्ष्म प्रभाव प्राप्त हो जो हल्के और गहरे दोनों बैकग्राउंड पर काम करे। प्रयोग करने में संकोच न करें:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

ध्यान रखें, **adjust shape transparency** को शैप के फ़िल कलर पर भी लागू किया जा सकता है यदि आपको स्वयं आयत को अर्ध‑पारदर्शी बनाना हो।

## Add Shape Shadow to Different Objects

हमारा कोड `Shape` ऑब्जेक्ट को टार्गेट करता है, लेकिन वही `ShadowFormat` प्रॉपर्टी **Image**, **Chart**, और यहाँ तक कि **TextBox** ऑब्जेक्ट्स पर भी मौजूद हैं। यहाँ एक त्वरित पैटर्न है जिसे आप कॉपी‑पेस्ट कर सकते हैं:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

इसलिए चाहे आप **add shape shadow** को किसी लोगो या सजावटी आइकन पर लगाएँ, तरीका समान रहता है।

## How to Add Shadow to Any Shape – Edge Cases

1. **Shape without a bounding box** – कुछ Word शैप (जैसे फ्री‑फ़ॉर्म स्क्रिबल) शैडो को सपोर्ट नहीं करते। `ShadowFormat.Visible` सेट करने की कोशिश करने पर चुपचाप विफल हो जाएगा। यदि सुरक्षा चाहिए तो `shape.IsShadowSupported` जांचें।  
2. **Older Word versions** – शैडो प्रॉपर्टी Word 2007+ की सुविधाओं से मैप होती हैं। यदि आपको Word 2003 सपोर्ट करना है, तो फ़ाइल खोलने पर शैडो को नजरअंदाज़ किया जाएगा।  
3. **Multiple shadows** – Aspose.Words वर्तमान में प्रति शैप केवल एक शैडो को सपोर्ट करता है। यदि आपको डबल‑लेयर प्रभाव चाहिए, तो शैप को डुप्लिकेट करें, उसे ऑफ़सेट करें, और अलग शैडो सेटिंग्स लागू करें।

## Add Rectangle Shadow – A Real‑World Use Case

कल्पना करें आप एक तिमाही रिपोर्ट बना रहे हैं और प्रत्येक सेक्शन हेडर एक रंगीन आयत है। **add rectangle shadow** जोड़ने से पेज को “कार्ड‑जैसा” लुक मिलता है। कदम बेस उदाहरण के समान हैं; बस यह सुनिश्चित करें कि आप जिस शैप को टार्गेट कर रहे हैं वह वास्तव में आयत है (`shape.ShapeType == ShapeType.Rectangle`)। यदि आपको शून्य से आयत बनानी है, तो नीचे का स्निपेट देखें:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

इस अतिरिक्त के साथ पूरा प्रोग्राम चलाने पर आपको एक नई आयत मिलेगी जिसमें पहले से ही इच्छित **add rectangle shadow** प्रभाव होगा।

---

![Word shape with shadow](placeholder-image.png){alt="Word में शैप पर शैडो सेट करने का तरीका"}

*चित्र: शैडो सेटिंग्स लागू करने के बाद आयत।*

## Quick Recap (Bullet‑Point Cheat Sheet)

- **Load** दस्तावेज़ को `new Document(path)` से लोड करें।  
- **Locate** शैप को `doc.GetChild(NodeType.Shape, index, true)` से खोजें।  
- **Enable** शैडो: `shape.ShadowFormat.Visible = true;`।  
- **Set color** किसी भी `System.Drawing.Color` से।  
- **Adjust transparency** (`0.0–1.0`) से अपारदर्शिता नियंत्रित करें।  
- **OffsetX / OffsetY** शैडो को क्षैतिज/ऊर्ध्वाधर रूप से (पॉइंट्स) ले जाएँ।  
- **BlurRadius** किनारा को नरम करता है—ज्यादा मान = धुंधला शैडो।  
- **Save** फ़ाइल को सेव करें और Word में खोलकर परिणाम देखें।

## What to Try Next?

- **Dynamic colors** – शैडो रंग को थीम या उपयोगकर्ता इनपुट से प्राप्त करें।  
- **Conditional shadows** – शैडो तभी लागू करें जब शैप की चौड़ाई एक निश्चित थ्रेशहोल्ड से अधिक हो।  
- **Batch processing** – दस्तावेज़ में सभी शैप्स पर लूप चलाएँ और **add shape shadow** को स्वचालित रूप से लागू करें।  

यदि आपने इस ट्यूटोरियल को फॉलो किया, तो अब आप जानते हैं **how to set shadow**, कैसे **adjust shape transparency**, और कैसे **add rectangle shadow** करके अपने दस्तावेज़ को प्रोफ़ेशनल लुक दें। प्रयोग करें, चीज़ें तोड़ें, फिर ठीक करें—कोडिंग सबसे अच्छा शिक्षक है।

---

*हैप्पी कोडिंग! यदि यह ट्यूटोरियल आपके काम आया, तो एक टिप्पणी छोड़ें या अपने शैडो ट्रिक्स शेयर करें। जितना हम एक‑दूसरे से सीखेंगे, हमारे Word डॉक्यूमेंट उतने ही सुंदर बनेंगे।*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}