---
category: general
date: 2026-06-02
description: C# का उपयोग करके Word दस्तावेज़ में चार्ट लेजेंड दिखाएँ। सीखें कैसे लेजेंड
  जोड़ें, प्रीसेट चार्ट स्टाइल लागू करें, और मिनटों में Word चार्ट विज़ुअल को कस्टमाइज़
  करें।
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: hi
og_description: Word दस्तावेज़ में तुरंत चार्ट लेजेंड दिखाएँ। यह गाइड आपको लेजेंड
  जोड़ने, प्रीसेट चार्ट स्टाइल लागू करने और किनारे के मामलों को संभालने के चरणों से
  परिचित कराता है।
og_title: Word में चार्ट लेजेंड दिखाएँ – पूर्ण C# ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: C# के साथ Word में चार्ट लेजेंड दिखाएँ – पूर्ण चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word में चार्ट लेजेंड दिखाएँ – पूर्ण चरण‑दर‑चरण गाइड

क्या आपने कभी सोचा है कि Word दस्तावेज़ में मौजूद चार्ट में **legend कैसे जोड़ें**? आप अकेले नहीं हैं। कई रिपोर्टों में, लेजेंड की कमी डेटा को रहस्यमय बनाती है, और इसे ठीक करना सिरदर्द नहीं होना चाहिए।  

इस ट्यूटोरियल में हम Aspose.Words for .NET का उपयोग करके Word फ़ाइल में **चार्ट लेजेंड दिखाएँगे**, एक प्रीसेट चार्ट स्टाइल लागू करेंगे, और सुनिश्चित करेंगे कि लेजेंड ठीक वहीँ दिखाई दे जहाँ आपको चाहिए। अंत तक आपके पास एक तैयार‑से‑चलाने वाला नमूना होगा जिसे आप किसी भी C# प्रोजेक्ट में डाल सकते हैं।

## इस गाइड में क्या कवर किया गया है

हम पूरी कार्यप्रवाह को चरण‑दर‑चरण देखेंगे:

1. मौजूदा *.docx* फ़ाइल लोड करें जिसमें पहले से ही एक चार्ट हो।  
2. पहला चार्ट प्राप्त करें (या कोई भी चार्ट जिसे आप लक्ष्य बनाते हैं)।  
3. **प्रीसेट चार्ट स्टाइल लागू करें** ताकि विज़ुअल को पेशेवर लुक मिले।  
4. **चार्ट लेजेंड दिखाएँ**, इसे दाएँ ओर रखें, और Waterfall चार्ट जैसे विशेष मामलों को संभालें।  
5. संशोधित दस्तावेज़ को सहेजें।

कोई बाहरी टूल नहीं, UI के साथ कोई मैन्युअल छेड़छाड़ नहीं—सिर्फ शुद्ध कोड। एकमात्र पूर्वशर्त Aspose.Words NuGet पैकेज (संस्करण 23.10 या बाद) का संदर्भ और C# की बुनियादी समझ है।

---

## Prerequisites

- .NET 6.0 या बाद (नमूना .NET Framework 4.7.2 के साथ भी काम करता है)।  
- Aspose.Words for .NET लाइब्रेरी स्थापित (`Install-Package Aspose.Words`)।  
- एक Word फ़ाइल (`input.docx`) जिसमें पहले से कम से कम एक चार्ट हो।  
- Visual Studio, Rider, या कोई भी IDE जो आप पसंद करते हैं।

---

## Step 1: Set Up the Project and Load the Document

First, create a console app (or integrate the code into an existing project). Add the `using` directives and load the `.docx` file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **क्यों महत्वपूर्ण है:** दस्तावेज़ को लोड करना आधार है। `Document` इंस्टेंस के बिना आप Aspose.Words द्वारा प्रदान किए गए चार्ट ऑब्जेक्ट्स तक नहीं पहुँच सकते।

---

## Step 2: Retrieve the Target Chart

Charts are stored as nodes inside the document tree. The `GetChild` method performs a deep search, letting us fetch the first chart regardless of where it sits (header, body, footer, etc.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **टिप:** यदि आपके पास कई चार्ट हैं, तो इंडेक्स `0` को `1`, `2`, … में बदलें या `doc.GetChildNodes(NodeType.Chart, true)` के माध्यम से इटररेट करें।

---

## Step 3: Apply a Preset Visual Style

A good-looking chart often starts with a style. Aspose.Words ships with dozens of built‑in styles; `ChartStyle.Style12` is a clean, modern option.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **कैसे काम करता है:** `Style` प्रॉपर्टी UI में दिखने वाले बिल्ट‑इन Word चार्ट स्टाइल्स से मैप होती है। प्रीसेट चुनने से आपको रंग, फ़ॉन्ट और मार्कर मैन्युअली सेट करने की ज़रूरत नहीं पड़ती।

---

## Step 4: Enable the Legend and Position It

Now for the star of the show—**show chart legend**. We turn the legend on, then dock it to the right side of the chart.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **दाएँ क्यों?** लेजेंड को दाएँ रखने से डेटा क्षेत्र चौड़ा रहता है, जो बार या कॉलम चार्ट के लिए विशेष रूप से उपयोगी है।

---

## Step 5: Handle Waterfall Charts (Special Case)

Waterfall charts behave a bit differently; the legend can be hidden by default. The following guard clause ensures the legend is visible when the chart type is Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **एज केस नोट:** कुछ पुराने Word संस्करण Waterfall चार्ट के लिए `HasLegend` को अनदेखा करते हैं, इसलिए स्पष्ट रूप से `Legend.Show` सेट करने से दृश्यता सुनिश्चित होती है।

---

## Step 6: Save the Modified Document

Finally, write the changes back to disk. You can overwrite the original file or create a new one.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

कार्यक्रम चलाने पर `output.docx` बन जाएगा जिसमें दाएँ ओर एक दृश्यमान लेजेंड होगा, `Style12` से स्टाइल किया हुआ। परिणाम सत्यापित करने के लिए फ़ाइल को Word में खोलें।

---

## Full Working Example (All Steps Combined)

Below is the complete, ready‑to‑run code. Copy‑paste it into `Program.cs` (or any C# file) and adjust the file paths.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**अपेक्षित आउटपुट:** `output.docx` खोलने पर मूल चार्ट दाएँ‑साइड लेजेंड के साथ दिखता है, आधुनिक `Style12` से स्टाइल किया हुआ। सभी डेटा सीरीज़ स्पष्ट रूप से लेबल्ड हैं, जिससे चार्ट तुरंत समझ में आता है।

---

## Frequently Asked Questions (FAQ)

### How to add legend to a specific chart (not the first one)?

Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based position of your target chart, or loop through all chart nodes:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Can I place the legend at the bottom instead of the right?

Absolutely. Just change the `LegendPosition` enum:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### What if the chart already has a legend but I want to hide it?

Set `HasLegend` to `false`:

```csharp
chart.HasLegend = false;
```

### Does this work with Word 2010, 2016, and later?

Yes. Aspose.Words abstracts the underlying Word version, so the same code works across all modern .docx files.

---

## Pro Tips & Common Pitfalls

- **प्रो टिप:** स्टाइल लागू करने के बाद भी आप `Chart.Series` कलेक्शन के माध्यम से व्यक्तिगत तत्वों (रंग, डेटा लेबल) को समायोजित कर सकते हैं। स्टाइल आपको एक ठोस बेसलाइन देता है।  
- **ध्यान रखें:** यदि चार्ट टेबल सेल के अंदर है, तो लेजेंड संकुचित दिख सकता है। लेजेंड को पोजिशन करने से पहले चार्ट का आकार (`chart.Width`, `chart.Height`) बढ़ाने पर विचार करें।  
- **परफॉर्मेंस नोट:** बड़े दस्तावेज़ (सैकड़ों MB) लोड करने से मेमोरी‑इंटेंसिव हो सकता है। यदि आपको केवल चार्ट मैनिपुलेशन चाहिए तो `LoadOptions` के साथ `LoadFormat.Docx` उपयोग करें ताकि ओवरहेड कम हो।

---

## Next Steps

अब जब आप Word में **legend कैसे जोड़ें** और **प्रीसेट चार्ट स्टाइल लागू करें** जानते हैं, तो आप निम्नलिखित का अन्वेषण कर सकते हैं:

- **कस्टम चार्ट रंग** (`chart.Series[i].Format.Fill.ForeColor`)।  
- **डेटा लेबल फ़ॉर्मेटिंग** (`chart.Series[i].HasDataLabel = true`)।  
- **चार्ट को इमेज के रूप में एक्सपोर्ट करना** (`chart.ToImage()`), जो अन्यत्र एम्बेड करने में उपयोगी है।  

इनमें से प्रत्येक विषय समान ऑब्जेक्ट मॉडल पर आधारित है, इसलिए सीखने की प्रक्रिया सहज होगी।

---

## Conclusion

हमने अभी-अभी C# का उपयोग करके Word दस्तावेज़ में **चार्ट लेजेंड दिखाने** के लिए एक साफ़, एंड‑टू‑एंड समाधान प्रदर्शित किया है। दस्तावेज़ लोड करके, चार्ट प्राप्त करके, प्रीसेट स्टाइल लागू करके, लेजेंड सक्षम करके और Waterfall की विशेषताओं को संभालकर, आपको एक पॉलिश्ड चार्ट मिलता है जो किसी भी बिज़नेस रिपोर्ट के लिए तैयार है।  

बिना झिझक अन्य `ChartStyle` मानों या लेजेंड पोजिशन के साथ प्रयोग करें—आपके डेटा विज़ुअलाइज़ेशन को सर्वश्रेष्ठ प्रस्तुति का हक़ है। यदि कोई समस्या आती है, तो नीचे टिप्पणी छोड़ें; हैप्पी कोडिंग!

---

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}