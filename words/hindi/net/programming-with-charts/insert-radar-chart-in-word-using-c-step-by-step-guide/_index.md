---
category: general
date: 2026-09-14
description: C# के साथ Word में रडार चार्ट डालें। जानें कि चार्ट शीर्षक कैसे सेट करें,
  कई श्रृंखलाएँ कैसे जोड़ें, और कुछ ही पंक्तियों में प्रोग्रामेटिक रूप से चार्ट बनाएं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: hi
lastmod: 2026-09-14
og_description: C# का उपयोग करके Word में रडार चार्ट डालें। यह ट्यूटोरियल दिखाता है
  कि चार्ट शीर्षक कैसे सेट करें, कई श्रृंखलाएँ कैसे जोड़ें, और प्रोग्रामेटिक रूप से
  चार्ट कैसे बनाएं।
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: C# के साथ Word में रडार चार्ट डालें – त्वरित प्रोग्रामिंग गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: C# का उपयोग करके Word में रडार चार्ट डालें – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert radar chart in Word using C# – step‑by‑step guide

यदि आपको **Word दस्तावेज़ में radar chart** डालना है, तो यह गाइड आपको C# के साथ प्रोग्रामेटिक रूप से इसे करने का तरीका दिखाएगा। आप यह भी सीखेंगे कि **चार्ट का शीर्षक कैसे सेट करें**, **multiple series radar chart** कैसे जोड़ें, और अपने IDE से बाहर निकले बिना फ़ाइल को कैसे सहेजें।

यह ट्यूटोरियल प्रोजेक्ट सेटअप से लेकर अंतिम `doc.Save` कॉल तक सब कुछ कवर करता है, इसलिए आप पूरा उदाहरण कॉपी‑पेस्ट करके तुरंत चला सकते हैं। किसी बाहरी दस्तावेज़ की आवश्यकता नहीं है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6 (या बाद का) स्थापित हो।
* एक वैध Aspose.Words for .NET लाइसेंस (या अस्थायी एवाल्यूएशन की)।
* Visual Studio 2022 या कोई भी पसंदीदा C# IDE।

> **Pro tip:** यदि आप फ्री ट्रायल का उपयोग कर रहे हैं, तो पहले `Document` बनाते समय लाइसेंस सेट करना न भूलें, ताकि एवाल्यूएशन वॉटरमार्क न दिखे।

## Step 1: Insert radar chart into a Word document

पहला कार्य है नया `Document` और `DocumentBuilder` बनाना। बिल्डर आपको दस्तावेज़ की सामग्री तक पहुंच देता है और **radar chart** को ठीक उसी जगह रखने की अनुमति देता है जहाँ आपको ज़रूरत है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Why this step matters:* `InsertChart` एक चार्ट ऑब्जेक्ट बनाता है जिसे आप दस्तावेज़ सहेजने से पहले पूरी तरह कॉन्फ़िगर कर सकते हैं। `ChartType.Radar` का उपयोग करने से Word कॉलम या लाइन चार्ट के बजाय रेडियल चार्ट रेंडर करता है।

## Step 2: Set chart title and axis graduations

बिना शीर्षक वाला चार्ट भ्रमित कर सकता है। यहाँ हम **चार्ट का शीर्षक** “Sales Radar” सेट करते हैं और दोनों अक्षों पर graduations सक्षम करते हैं (Aspose.Words 24.9 से उपलब्ध)।

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Why this step matters:* शीर्षक पाठकों को संदर्भ देता है, और graduations स्केल पर प्रत्येक डेटा पॉइंट कहाँ आता है यह दिखाकर पठनीयता बढ़ाते हैं।

## Step 3: Create multiple series for radar chart

एक **multiple series radar chart** आपको विभिन्न अवधियों की तुलना एक साथ करने देता है। नीचे हम दो सीरीज़—Q1 और Q2—प्रत्येक में तीन डेटा पॉइंट्स के साथ जोड़ते हैं।

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Why this step matters:* कई सीरीज़ जोड़ने से दिखता है कि कैसे एक ही रडार पर विभिन्न डेटा सेट्स की तुलना की जा सकती है, जो बिक्री, प्रदर्शन या सर्वे परिणामों के लिए सामान्य आवश्यकता है।

## Step 4: Save the Word document programmatically

अंत में, आप **चार्ट को प्रोग्रामेटिक रूप से बनाते** हैं और दस्तावेज़ को डिस्क पर सहेजते हैं। `Save` मेथड एक `.docx` फ़ाइल लिखता है जिसे Microsoft Word में खोला जा सकता है।

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

जब आप `RadialGraduations.docx` खोलेंगे, तो आपको “Sales Radar” शीर्षक वाला radar chart दिखेगा, जिसमें दो सीरीज़ (Q1 और Q2) महीने Jan‑Mar के खिलाफ प्लॉटेड होंगी।

### Expected output

![Word में रडार चार्ट](https://example.com/radar-chart.png){: .align-center alt="Word दस्तावेज़ जिसमें दो डेटा सीरीज़ वाला radar chart दिखाया गया है"}

स्क्रीनशॉट (या वास्तविक फ़ाइल) पुष्टि करता है कि चार्ट सफलतापूर्वक डाला गया, शीर्षक दिया गया, और सही ढंग से डेटा से भर दिया गया है।

## Full, runnable example

सब कुछ एक साथ रखने पर, यहाँ एक स्वतंत्र प्रोग्राम है जिसे आप कंपाइल और रन कर सकते हैं:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

प्रोग्राम चलाएँ, जेनरेटेड फ़ाइल खोलें, और **insert radar chart** ऑपरेशन सफल हुआ या नहीं, यह सत्यापित करें।

## Common questions & edge cases

| Question | Answer |
|----------|--------|
| **Can I change the chart type after insertion?** | हाँ। `InsertChart` के बाद, `chart.Type` को नया `ChartType` असाइन करें। हालांकि, शुरू से सही प्रकार चुनना अधिक कुशल है। |
| **What if I need more than two series?** | प्रत्येक अतिरिक्त सीरीज़ के लिए `chart.Series.Add` कॉल करें। चार्ट स्वचालित रूप से लेजेंड और रंग समायोजित कर लेगा। |
| **How do I customize colors or markers?** | `chart.Series[i].Format.Fill.ForeColor` से फ़िल रंग बदलें और `chart.Series[i].Marker` से मार्कर स्टाइल सेट करें। |
| **Is the API compatible with .NET Framework?** | वही कोड .NET Framework 4.7+ के साथ काम करता है; केवल उपयुक्त Aspose.Words DLL रेफ़रेंस करें। |
| **What if I’m using an older Aspose.Words version?** | Graduations (`HasGraduations`) 24.9 में पेश किए गए थे। पुराने संस्करणों में आप `chart.AxisX.MajorGridLines` और `chart.AxisY.MajorGridLines` का उपयोग करके मैन्युअली ग्रिड लाइन्स जोड़ सकते हैं। |

## Conclusion

अब आप जानते हैं कि **C# का उपयोग करके Word दस्तावेज़ में radar chart कैसे डालें**, **चार्ट का शीर्षक सेट करें**, **multiple series radar chart जोड़ें**, और **चार्ट को प्रोग्रामेटिक रूप से बनाएं**। यह एंड‑टू‑एंड समाधान रिपोर्टिंग, डैशबोर्ड या किसी भी ऐसी स्थिति को स्वचालित करता है जहाँ श्रेणियों की दृश्य तुलना आवश्यक है।

अगला, **चार्ट रंगों को कस्टमाइज़ करना**, **चार्ट को इमेज के रूप में एक्सपोर्ट करना**, या **PDF फ़ाइलों में चार्ट एम्बेड करना** जैसे विषयों का अन्वेषण करें। विभिन्न डेटा सेट्स के साथ प्रयोग करें और देखें कि radar visualization कैसे अनुकूलित होती है।

Happy coding!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को आज़मा सकें।

- [Aspose.Words for .NET का उपयोग करके Word में कॉलम चार्ट डालें](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET का उपयोग करके Word में बबल चार्ट डालें](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Aspose.Words for .NET के साथ Word दस्तावेज़ में एरिया चार्ट डालें](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}