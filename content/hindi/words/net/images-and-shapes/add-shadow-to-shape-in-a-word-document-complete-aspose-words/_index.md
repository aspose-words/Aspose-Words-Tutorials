---
category: general
date: 2025-12-08
description: Aspose.Words के साथ शीघ्रता से आकार में छाया जोड़ें। Aspose का उपयोग
  करके Word दस्तावेज़ बनाना, आकार में छाया जोड़ना, और C# में छाया की पारदर्शिता लागू
  करना सीखें।
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: hi
og_description: Aspose.Words का उपयोग करके Word फ़ाइल में आकार पर छाया जोड़ें। यह
  चरण‑दर‑चरण गाइड दिखाता है कि दस्तावेज़ कैसे बनाएं, आकार जोड़ें, और छाया की पारदर्शिता
  कैसे लागू करें।
og_title: आकार में छाया जोड़ें – Aspose.Words C# ट्यूटोरियल
tags:
- Aspose.Words
- C#
- Word Automation
title: Word दस्तावेज़ में आकृति पर छाया जोड़ें – पूर्ण Aspose.Words गाइड
url: /hindi/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# आकार में छाया जोड़ें – पूर्ण Aspose.Words गाइड

क्या आपको कभी Word फ़ाइल में **add shadow to shape** जोड़ने की ज़रूरत पड़ी है लेकिन कौन से API कॉल्स उपयोग करने हैं, इस बात को लेकर अनिश्चित रहे हैं? आप अकेले नहीं हैं। कई डेवलपर्स पहली बार जब एक आयत या किसी भी ड्राइंग एलिमेंट को उचित ड्रॉप‑शैडो देने की कोशिश करते हैं, तो वे अटक जाते हैं, विशेषकर जब वे Aspose.Words for .NET के साथ काम कर रहे होते हैं।

इस ट्यूटोरियल में हम आपको वह सब कुछ बताएँगे जो आपको जानना आवश्यक है: **creating a Word document using Aspose** से लेकर शैडो को कॉन्फ़िगर करने, उसके ब्लर, दूरी, कोण, और यहाँ तक कि **applying shadow transparency** तक। अंत तक आपके पास एक तैयार‑चलाने योग्य C# प्रोग्राम होगा जो एक `.docx` फ़ाइल बनाता है जिसमें एक सुंदर शेडेड आयत होती है—Word में मैन्युअल हस्तक्षेप की आवश्यकता नहीं।

---

## आप क्या सीखेंगे

- Visual Studio में Aspose.Words प्रोजेक्ट सेट अप करने का तरीका।  
- **create Word document using Aspose** और एक shape डालने के सटीक कदम।  
- **How to add shape shadow** ब्लर, दूरी, कोण, और ट्रांसपेरेंसी पर पूर्ण नियंत्रण के साथ।  
- सामान्य समस्याओं (जैसे, लाइसेंस गायब होना, गलत यूनिट) को हल करने के टिप्स।  
- एक पूर्ण, कॉपी‑एंड‑पेस्ट कोड सैंपल जिसे आप आज ही चला सकते हैं।

> **Prerequisites:** .NET 6+ (या .NET Framework 4.7.2+), एक वैध Aspose.Words लाइसेंस (या फ्री ट्रायल), और C# की बुनियादी परिचितता।

## चरण 1 – अपना प्रोजेक्ट सेट अप करें और Aspose.Words जोड़ें

सबसे पहले, Visual Studio खोलें, एक नया **Console App (.NET Core)** बनाएं, और Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** यदि आपके पास लाइसेंस फ़ाइल (`Aspose.Words.lic`) है, तो उसे प्रोजेक्ट रूट में कॉपी करें और स्टार्टअप पर लोड करें। इससे फ्री इवैल्यूएशन मोड में दिखाई देने वाला वाटरमार्क हट जाता है।

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

## चरण 2 – एक नया खाली दस्तावेज़ बनाएं

अब हम वास्तव में **create Word document using Aspose** करेंगे। यह ऑब्जेक्ट हमारे shape के लिए कैनवास के रूप में काम करेगा।

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

`Document` क्लास बाकी सब चीज़ों—पैराग्राफ, सेक्शन, और बेशक, ड्राइंग ऑब्जेक्ट्स—के लिए एंट्री पॉइंट है।

## चरण 3 – एक आयताकार Shape डालें

डॉक्यूमेंट तैयार होने पर, हम एक shape जोड़ सकते हैं। यहाँ हम एक साधारण आयत चुनते हैं, लेकिन वही लॉजिक सर्कल, लाइन, या कस्टम पॉलीगॉन के लिए भी काम करता है।

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Why a shape?** Aspose.Words में एक `Shape` ऑब्जेक्ट टेक्स्ट, इमेजेज़ रख सकता है, या सिर्फ एक सजावटी तत्व के रूप में कार्य कर सकता है। एक shape में शैडो जोड़ना picture frame को मैनिपुलेट करने से बहुत आसान है।

## चरण 4 – शैडो कॉन्फ़िगर करें (Add Shadow to Shape)

यह ट्यूटोरियल का मुख्य भाग है—**how to add shape shadow** और उसकी उपस्थिति को बारीकी से ट्यून करना। `ShadowFormat` प्रॉपर्टी आपको पूर्ण नियंत्रण देती है।

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### प्रत्येक प्रॉपर्टी क्या करती है

| प्रॉपर्टी | प्रभाव | सामान्य मान |
|----------|--------|----------------|
| **Visible** | शैडो को ऑन/ऑफ़ करता है। | `true` / `false` |
| **Blur** | शैडो के किनारों को नरम करता है। | `0` (hard) to `10` (very soft) |
| **Distance** | शैडो को shape से दूर ले जाता है। | `1`–`5` points is common |
| **Angle** | ऑफ़सेट की दिशा को नियंत्रित करता है। | `0`–`360` degrees |
| **Transparency** | शैडो को आंशिक रूप से पारदर्शी बनाता है। | `0` (opaque) to `1` (invisible) |

> **Edge case:** यदि आप `Transparency` को `1` सेट करते हैं, तो शैडो पूरी तरह गायब हो जाता है—प्रोग्रामेटिक रूप से इसे टॉगल करने के लिए उपयोगी।

## चरण 5 – Shape को दस्तावेज़ में जोड़ें

अब हम shape को दस्तावेज़ के बॉडी के पहले पैराग्राफ से जोड़ते हैं। यदि कोई पैराग्राफ नहीं है तो Aspose स्वचालित रूप से एक पैराग्राफ बना देता है।

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

यदि आपके दस्तावेज़ में पहले से सामग्री है, तो आप `InsertAfter` या `InsertBefore` का उपयोग करके shape को किसी भी नोड पर डाल सकते हैं।

## चरण 6 – दस्तावेज़ को सेव करें

अंत में, फ़ाइल को डिस्क पर लिखें। आप कोई भी समर्थित फ़ॉर्मेट (`.docx`, `.pdf`, `.odt`, आदि) चुन सकते हैं, लेकिन इस ट्यूटोरियल के लिए हम मूल Word फ़ॉर्मेट ही उपयोग करेंगे।

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

परिणामी `ShadowedShape.docx` को Microsoft Word में खोलें, और आपको एक आयत दिखेगी जिसमें एक नरम, 45‑डिग्री शैडो है जो 30 % पारदर्शी है—बिल्कुल वही जो हमने कॉन्फ़िगर किया था।

## पूर्ण कार्यशील उदाहरण

नीचे **complete, copy‑and‑paste ready** प्रोग्राम है जो ऊपर बताए सभी चरणों को सम्मिलित करता है। इसे `Program.cs` के रूप में सेव करें और `dotnet run` से चलाएँ।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Expected output:** `ShadowedShape.docx` नाम की फ़ाइल जिसमें एक ही आयत है जिसमें 45° के कोण पर एक सूक्ष्म, अर्ध‑पारदर्शी ड्रॉप शैडो है।

## विविधताएँ और उन्नत टिप्स

### शैडो रंग बदलना

डिफ़ॉल्ट रूप से शैडो shape के फ़िल रंग को विरासत में लेता है, लेकिन आप एक कस्टम रंग सेट कर सकते हैं:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### विभिन्न शैडो वाले कई Shapes

यदि आपको कई shapes चाहिए, तो बस निर्माण और कॉन्फ़िगरेशन चरणों को दोहराएँ। यदि आप बाद में उन्हें रेफ़र करने की योजना बनाते हैं तो प्रत्येक shape को एक अनूठा नाम देना याद रखें।

### शैडो संरक्षित रखते हुए PDF में एक्सपोर्ट करना

PDF में सेव करते समय Aspose.Words शैडो इफ़ेक्ट्स को संरक्षित रखता है:

```csharp
doc.Save("ShadowedShape.pdf");
```

### सामान्य समस्याएँ

| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| शैडो दिखाई नहीं दे रहा | `ShadowFormat.Visible` left as `false` | Set to `true`. |
| शैडो बहुत कठोर दिख रहा है | `Blur` set to `0` | Increase `Blur` to 3–6. |
| PDF में शैडो गायब हो जाता है | पुराना Aspose.Words संस्करण (< 22.9) उपयोग करना | Upgrade to the latest library. |

## निष्कर्ष

हमने Aspose.Words का उपयोग करके **how to add shadow to shape** को कवर किया है, दस्तावेज़ को इनिशियलाइज़ करने से लेकर ब्लर, दूरी, कोण, और **applying shadow transparency** को बारीकी से ट्यून करने तक। पूर्ण उदाहरण एक साफ़, प्रोडक्शन‑रेडी अप्रोच दिखाता है जिसे आप किसी भी shape या दस्तावेज़ लेआउट में अनुकूलित कर सकते हैं।

यदि आपके पास **create word document using aspose** के बारे में अधिक जटिल परिदृश्यों—जैसे शैडो वाले टेबल या डायनामिक डेटा‑ड्रिवेन shapes—के बारे में प्रश्न हैं, तो नीचे टिप्पणी छोड़ें या Aspose.Words इमेज हैंडलिंग और पैराग्राफ फ़ॉर्मेटिंग पर संबंधित ट्यूटोरियल देखें।

कोडिंग का आनंद लें, और अपने Word दस्तावेज़ों को वह अतिरिक्त विज़ुअल पॉलिश देने का मज़ा उठाएँ! 

--- 

![add shadow to shape example](shadowed_shape.png "add shadow to shape example")

{{< layout-end >}}

{{< layout-end >}}