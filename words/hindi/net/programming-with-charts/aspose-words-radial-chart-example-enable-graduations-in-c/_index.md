---
category: general
date: 2026-10-13
description: Aspose.Words रेडियल चार्ट का उदाहरण जो C# और Aspose.Words 24.9+ का उपयोग
  करके रेडियल चार्ट पर ग्रेडुएशन सक्षम करने का तरीका दिखाता है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: hi
lastmod: 2026-10-13
og_description: Aspose.Words रेडियल चार्ट उदाहरण जो C# और नवीनतम 24.9+ लाइब्रेरी के
  साथ रेडियल चार्ट पर ग्रेजुएशन सक्षम करने को दर्शाता है।
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words रेडियल चार्ट उदाहरण – C# में ग्रेडुएशन सक्षम करें
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words रेडियल चार्ट उदाहरण: C# में ग्रेजुएशन सक्षम करें'
url: /hi/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words रेडियल चार्ट उदाहरण: C# में ग्रेजुएशन्स सक्षम करें

यदि आप एक **aspose.words radial chart example** की तलाश में हैं, तो आप सही जगह पर आए हैं। यह ट्यूटोरियल आपको Aspose.Words for .NET API का उपयोग करके रेडियल चार्ट के लिए ग्रेजुएशन्स को चालू करने के सटीक चरणों के माध्यम से ले जाता है।

रेडियल चार्ट चक्रीय डेटा जैसे समय‑के‑दिन के मेट्रिक्स या मौसमी रुझानों को विज़ुअलाइज़ करने के लिए उपयोगी होते हैं। डिफ़ॉल्ट रूप से ग्रेजुएशन्स (वृत्ताकार अक्ष के चारों ओर के टिक मार्क) छिपे होते हैं, जिससे चार्ट पढ़ना कठिन हो सकता है। उन्हें सक्षम करना एक एकल‑लाइन परिवर्तन है, लेकिन आपको सही ऑब्जेक्ट मॉडल और वह संस्करण जानना होगा जो इस सुविधा का समर्थन करता है।

इस गाइड में आप सीखेंगे कि कैसे:

* वह वर्ड दस्तावेज़ लोड करें जिसमें पहले से ही एक रेडियल चार्ट हो।  
* Aspose.Words चार्ट API के माध्यम से चार्ट शेप तक पहुंचें।  
* **graduations visibility** को चालू करें (उपलब्ध **Aspose.Words version 24.9** से)।  
* संशोधित दस्तावेज़ को सहेजें और परिणाम की पुष्टि करें।

पूरा, चलाने योग्य कोड शामिल है, इसलिए आप इसे नई कंसोल प्रोजेक्ट में कॉपी‑पेस्ट करके तुरंत प्रभाव देख सकते हैं।

![Aspose.Words रेडियल चार्ट उदाहरण ग्रेजुएशन्स के साथ](https://example.com/images/radial-chart-graduations.png "Aspose.Words रेडियल चार्ट उदाहरण जिसमें ग्रेजुएशन्स सक्षम दिखाए गए हैं")

## आवश्यकताएँ

शुरू करने से पहले, सुनिश्चित करें कि आपके पास है:

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 or later | Aspose.Words for .NET 24.9+ .NET Standard 2.0 को टारगेट करता है और .NET 6+ पर काम करता है। |
| Aspose.Words for .NET **24.9** or newer | `IsGraduationsVisible` प्रॉपर्टी संस्करण 24.9 में पेश की गई थी। पुराने रिलीज़ में `MissingMemberException` फेंका जाएगा। |
| A Word document (`RadialChart.docx`) that contains a radial chart | यह उदाहरण मौजूदा चार्ट को संशोधित करता है; शून्य से एक बनाना एक अलग विषय है। |
| A C# IDE (Visual Studio, Rider, VS Code) | कोई भी IDE जो .NET प्रोजेक्ट्स को कंपाइल कर सके, काम करेगा। |
| NuGet package `Aspose.Words` | इंस्टॉल करें `dotnet add package Aspose.Words --version 24.9.0` (या बाद का संस्करण) के माध्यम से। |

> **Pro tip:** यदि आप 24.9 में अपग्रेड नहीं कर सकते, तो आप अभी भी अन्य चार्ट प्रॉपर्टीज़ को संशोधित कर सकते हैं, लेकिन ग्रेजुएशन्स छिपे रहेंगे क्योंकि API ने वह फ़्लैग उजागर नहीं किया है।

## Aspose.Words रेडियल चार्ट उदाहरण – चरण‑दर‑चरण गाइड

निम्नलिखित सेक्शन प्रक्रिया को अलग‑अलग, आसानी‑से‑फ़ॉलो करने योग्य चरणों में विभाजित करते हैं। प्रत्येक चरण में आपको आवश्यक सटीक कोड और यह समझाने के लिए एक छोटा विवरण शामिल है कि *क्यों* वह चरण मौजूद है।

### चरण 1: वह दस्तावेज़ लोड करें जिसमें रेडियल चार्ट हो

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Why this matters:**  
`Document` **Aspose.Words चार्ट API** का प्रवेश बिंदु है। यह DOCX फ़ाइल को मेमोरी में लोड करता है, जिससे आपको हर नोड—पैराग्राफ़, टेबल, और चार्ट शेप्स—तक पहुंच मिलती है। यदि फ़ाइल नहीं मिलती, तो `Document` `FileNotFoundException` फेंकेगा, जिसे प्रोडक्शन कोड में हैंडल करना चाहिए।

### चरण 2: दस्तावेज़ से पहला चार्ट शेप प्राप्त करें

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Why this matters:**  
चार्ट `Shape` नोड्स के रूप में संग्रहीत होते हैं। `GetChild` मेथड `NodeType.Shape` के साथ DOM को ट्रैवर्स करता है और पहला मिलते‑जुलते शेप को लौटाता है। `Chart` में कास्ट करने से आपको `RadialChart` जैसे चार्ट‑विशिष्ट प्रॉपर्टीज़ मिलती हैं। null‑चेक यह सुनिश्चित करता है कि यदि दस्तावेज़ में चार्ट नहीं है तो स्पष्ट त्रुटि मिले, जो टेम्प्लेट पुन: उपयोग करते समय एक सामान्य एज केस है।

### चरण 3: रेडियल चार्ट पर ग्रेजुएशन्स सक्षम करें

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Why this matters:**  
`IsGraduationsVisible` वृत्ताकार अक्ष के चारों ओर के टिक मार्क को नियंत्रित करता है। इसे `true` सेट करने पर चार्ट ग्रेजुएशन्स दिखाता है, जिससे दर्शकों को मानों को सटीक रूप से मापने में आसानी होती है। यह प्रॉपर्टी `RadialChart` के तहत आती है, जो `Chart` का एक सब‑टाइप है। यदि आप इसे गैर‑रेडियल चार्ट (जैसे बार चार्ट) पर उपयोग करने की कोशिश करते हैं, तो `RadialChart` प्रॉपर्टी `null` होगी, इसलिए अधिक जटिल परिदृश्यों में पहले चार्ट प्रकार की जाँच करनी चाहिए।

#### गैर‑रेडियल चार्ट्स को संभालना (वैकल्पिक)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

यह गार्ड कोड को मजबूत बनाता है जब स्रोत दस्तावेज़ में विभिन्न प्रकार के चार्ट हो सकते हैं।

### चरण 4: संशोधित दस्तावेज़ को सहेजें

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Why this matters:**  
`Save` को कॉल करने से इन‑मेमोरी DOM को .docx फ़ाइल में लिखा जाता है, जिससे आपने चार्ट में किया गया परिवर्तन स्थायी हो जाता है। आउटपुट फ़ाइल को Microsoft Word, LibreOffice, या किसी भी DOCX‑सपोर्टिंग व्यूअर में खोला जा सकता है। आप वृत्ताकार अक्ष के चारों ओर दृश्यमान ग्रेजुएशन्स के साथ रेडियल चार्ट देखेंगे।

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप .NET कंसोल प्रोजेक्ट की `Program.cs` में पेस्ट कर सकते हैं।

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### अपेक्षित आउटपुट

जब आप Word में `RadialChart_Graduations.docx` खोलते हैं, तो रेडियल चार्ट वृत्ताकार अक्ष के चारों ओर टिक मार्क (ग्रेजुएशन्स) दिखाएगा, जैसा कि पहले दिखाए गए स्क्रीनशॉट में है। चार्ट के बाकी हिस्से (डेटा सीरीज़, लेजेंड, टाइटल) अपरिवर्तित रहेंगे।

## सामान्य विविधताएँ और किनारे के मामले

| Situation | Solution |
|-----------|----------|
| **पुराना Aspose.Words संस्करण (< 24.9)** | नवीनतम NuGet पैकेज में अपग्रेड करें। `IsGraduationsVisible` प्रॉपर्टी पहले के रिलीज़ में मौजूद नहीं है। |
| **एक ही दस्तावेज़ में कई चार्ट** | उपयुक्त `index` के साथ `doc.GetChild(NodeType.Shape, index, true)` का उपयोग करें या `doc.GetChildNodes(NodeType.Shape, true)` पर इटररेट करके `ChartType.Radial` द्वारा फ़िल्टर करें। |
| **प्रोग्रामेटिकली बनाया गया चार्ट** | `DocumentBuilder` का उपयोग करके एक चार्ट डालें, फिर `RadialChart.IsGraduationsVisible` सेट करें। |

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके वर्ड दस्तावेज़ में चार्ट सीरीज़ डेटा अपडेट करें](/words/english/net/programming-with-charts/modify-chart-series/)
- [Aspose.Words for .NET का उपयोग करके वर्ड दस्तावेज़ से एक चार्ट सीरीज़ हटाएँ](/words/english/net/programming-with-charts/remove-chart-series/)
- [Aspose.Words for .NET के साथ कॉलम चार्ट में प्लॉट एरिया बॉर्डर छिपाएँ](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}