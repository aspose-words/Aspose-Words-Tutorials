---
category: general
date: 2026-08-07
description: C# में जल्दी से पाई चार्ट बनाएं। पाई चार्ट कैसे डालें, डेटा लेबल पाई
  कैसे जोड़ें, प्रतिशत चार्ट कैसे दिखाएं, और चार्ट डेटा लेबल को कस्टमाइज़ करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: hi
lastmod: 2026-08-07
og_description: Aspose.Words के साथ C# में पाई चार्ट वर्ड बनाएं। यह ट्यूटोरियल दिखाता
  है कि पाई चार्ट कैसे डालें, डेटा लेबल पाई जोड़ें, और चार्ट डेटा लेबल को कस्टमाइज़
  करते हुए प्रतिशत चार्ट कैसे दिखाएँ।
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: C# में पाई चार्ट शब्द बनाएं – पूर्ण ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: C# में पाई चार्ट शब्द बनाएं – चरण‑दर‑चरण मार्गदर्शिका
url: /hi/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create pie chart word in C# – step‑by‑step guide

यदि आपको C# में **create pie chart word** दस्तावेज़ बनाने की आवश्यकता है, तो यह गाइड एक पूर्ण, तैयार‑चलाने योग्य समाधान प्रदान करता है। आप देखेंगे कि **insert pie chart**, **add data labels pie**, और **show percentage chart** कैसे किया जाता है तथा **customize chart data labels** को कैसे अनुकूलित किया जाता है ताकि एक पेशेवर लुक प्राप्त हो सके।

प्रोग्रामेटिक रूप से चार्ट बनाना आपको मैन्युअल संपादन से बचाता है, विशेषकर जब रिपोर्ट या डैशबोर्ड को स्वचालित रूप से उत्पन्न करना हो। नीचे दिए गए सेक्शन में आप Aspose.Words for .NET का उपयोग करके Word फ़ाइल में पूरी तरह लेबल किया हुआ पाई चार्ट एम्बेड करने के लिए आवश्यक सभी चीज़ें सीखेंगे।

## Prerequisites and setup

शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो।  
* एक वैध Aspose.Words for .NET लाइसेंस (या अस्थायी इवैल्यूएशन की)।  
* Visual Studio 2022 (या कोई भी IDE जो C# को सपोर्ट करता हो)।  

अपने प्रोजेक्ट में Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** यदि आप कई चार्ट जनरेट करने की योजना बना रहे हैं, तो बेहतर प्रदर्शन के लिए **Free‑Form Drawing** मोड (`DocumentBuilder.UseFreeFormDrawing = true`) सक्षम करें।

## Create pie chart word with Aspose.Words

पहला मुख्य कदम एक खाली Word दस्तावेज़ और एक `DocumentBuilder` बनाना है। यह ऑब्जेक्ट सभी बाद के इन्सर्शन को नियंत्रित करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: `Document` पूरे `.docx` फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` पैराग्राफ, टेबल और चार्ट जोड़ने के लिए एक फ़्लुएंट API प्रदान करता है। एक साफ़ दस्तावेज़ से शुरू करने से कोई छिपा फ़ॉर्मेटिंग चार्ट लेआउट में बाधा नहीं बनता।

## Insert pie chart into the document

अब हम इच्छित आकार का पाई चार्ट रखेंगे। `InsertChart` मेथड एक `Chart` ऑब्जेक्ट लौटाता है जिसे हम आगे कॉन्फ़िगर कर सकते हैं।

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Why this matters*: `ChartType.Pie` फ़्लैग Aspose.Words को एक गोलाकार चार्ट जनरेट करने के लिए बताता है। चौड़ाई (`400`) और ऊँचाई (`300`) पॉइंट्स में निर्दिष्ट हैं, जिससे आपको विज़ुअल फुटप्रिंट पर सटीक नियंत्रण मिलता है।

## Populate the chart with data

पाई चार्ट को कम से कम एक सीरीज़ के संख्यात्मक मानों की आवश्यकता होती है। यहाँ हम तीन श्रेणियाँ जोड़ते हैं: “Apples”, “Bananas”, और “Cherries”।

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Why this matters*: प्रत्येक `AddCategory` कॉल एक स्लाइस बनाती है। संख्यात्मक मान स्लाइस का आकार निर्धारित करता है, जबकि लेबल श्रेणी का नाम बन जाता है जब डेटा लेबल सक्रिय होते हैं।

## Add data labels pie and show percentage chart

चार्ट को जानकारीपूर्ण बनाने के लिए हम डेटा लेबल सक्षम करते हैं, उन्हें स्लाइस के बाहर स्थित करते हैं, और Aspose.Words को दोनों श्रेणी नाम और प्रतिशत दिखाने के लिए कहते हैं।

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Why this matters*: `Position` को `OutsideEnd` सेट करने से पठनीयता बेहतर होती है, विशेषकर जब स्लाइस छोटे हों। `ShowCategoryName` और `ShowPercentage` को सक्षम करने से **show percentage chart** की आवश्यकता पूरी होती है और **add data labels pie** लक्ष्य भी प्राप्त होता है।

## Customize chart data labels further (optional)

आप फ़ॉन्ट बदलना, लीडर लाइन जोड़ना, या लेजेंड को छिपाना चाह सकते हैं। नीचे दिया गया स्निपेट सामान्य कस्टमाइज़ेशन दिखाता है:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Why this matters*: लेबल की उपस्थिति को अनुकूलित करने से चार्ट आपके दस्तावेज़ की शैली गाइड से मेल खाता है। लेजेंड हटाने से दृश्य अव्यवस्था कम होती है जब डेटा लेबल पहले से ही वही जानकारी प्रदान कर रहे हों।

## Save the document with the customized chart

अंत में, दस्तावेज़ को डिस्क पर लिखें। ऐसा पथ चुनें जहाँ आपके पास लिखने की अनुमति हो।

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

जब आप Microsoft Word में `ChartWithCustomLabels.docx` खोलेंगे, तो आपको एक पाई चार्ट दिखाई देगा जहाँ प्रत्येक स्लाइस को उसकी श्रेणी नाम और प्रतिशत के साथ लेबल किया गया है, स्लाइस के बाहर स्थित है, और कस्टम फ़ॉन्ट सेटिंग्स के साथ स्टाइल किया गया है।

### Expected output

| स्लाइस   | मान | प्रतिशत | Word में दिखाया गया लेबल |
|---------|-----|----------|--------------------------|
| Apples  | 40  | 40 %     | Apples – 40 %            |
| Bananas | 35  | 35 %     | Bananas – 35 %           |
| Cherries| 25  | 25 %     | Cherries – 25 %          |

चार्ट नीचे दी गई चित्रण जैसा दिखना चाहिए:

![Word document displaying a pie chart with percentage labels outside each slice](pie-chart-word.png "Create pie chart word example")

*Image alt text includes the primary keyword for SEO.*

## Handling multiple series and edge cases

बुनियादी उदाहरण एक ही सीरीज़ का उपयोग करता है, जो पाई चार्ट के लिए सामान्य है। यदि आपको कई सीरीज़ (जैसे दो वर्षों की तुलना) दिखानी हैं, तो आपको:

1. प्रत्येक अतिरिक्त सीरीज़ के लिए `chart.Series.Add()` कॉल करना होगा।  
2. सुनिश्चित करें कि प्रत्येक सीरीज़ समान श्रेणियों का उपयोग करे; अन्यथा Aspose.Words `ArgumentException` फेंकेगा।  
3. वैकल्पिक रूप से, स्लाइस को अलग पहचान देने के लिए `labels.ShowSeriesName = true` सेट करें।

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

जब कई सीरीज़ मौजूद हों, तो चार्ट स्वचालित रूप से **clustered pie** (जिसे “pie of pies” भी कहा जाता है) के रूप में रेंडर होता है। आउटपुट की जाँच करें कि लेबल पठनीय रहें।

## Common pitfalls and how to avoid them

| समस्या | कारण | समाधान |
|--------|------|--------|
| लेबल स्लाइस के ऊपर ओवरलैप हो रहे हैं | चार्ट क्षेत्र छोटा है या श्रेणियों की संख्या अधिक है | चार्ट के आयाम बढ़ाएँ (`InsertChart(width, height)`) या `Position` को `InsideEnd` बदलें। |
| प्रतिशत 100 % नहीं बनते | डेटा में राउंडिंग त्रुटियाँ | `labels.ShowPercentage = true` उपयोग करें (Aspose.Words स्वतः सामान्यीकरण करता है)। |
| Word में चार्ट खाली दिख रहा है | लाइसेंस नहीं है या इवैल्यूएशन टाइमआउट | दस्तावेज़ बनाने से पहले वैध Aspose.Words लाइसेंस लोड करें। |
| फ़ॉन्ट रंग Word थीम से अलग हैं | कोड में कस्टम फ़ॉन्ट सेट किया गया है | कस्टम फ़ॉन्ट सेटिंग हटाएँ या Word की थीम रंगों से मेल रखें (`System.Drawing.Color.Black`)। |

## Full source code (runnable)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

प्रोग्राम चलाने पर `ChartWithCustomLabels.docx` उत्पन्न होगा, जिसमें **create pie chart word** उदाहरण शामिल है जो ट्यूटोरियल में सूचीबद्ध सभी आवश्यकताओं को पूरा करता है।

## Conclusion

अब आप Aspose.Words का उपयोग करके C# में **create pie chart word** दस्तावेज़ बनाने में सक्षम हैं। इस गाइड में पाई चार्ट इन्सर्ट करना, **add data labels pie**, **show percentage chart**, और **customize chart data labels** को कवर किया गया है ताकि एक पेशेवर, डेटा‑ड्रिवन Word फ़ाइल तैयार की जा सके।  

अब आप संबंधित विषयों जैसे मौजूदा पैराग्राफ़ में **insert pie chart**, **bar** या **line** चार्ट जनरेट करना, या विभिन्न डेटा सेट के साथ रिपोर्टों का बैच निर्माण स्वचालित करना, का अन्वेषण कर सकते हैं। विभिन्न लेबल पोज़िशन, फ़ॉन्ट स्टाइल, और मल्टी‑सीरीज़ कॉन्फ़िगरेशन के साथ प्रयोग करें ताकि आउटपुट को अपनी रिपोर्टिंग जरूरतों के अनुसार ट्यून किया जा सके।

Happy charting!

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}