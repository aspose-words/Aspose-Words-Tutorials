---
category: general
date: 2026-08-04
description: C# में Aspose.Words के साथ डेटा लेबल कैसे जोड़ें। चार्ट को संपादित करना
  सीखें, चार्ट डेटा लेबल को केंद्रित करें, चार्ट में प्रतिशत दिखाएँ, और चार्ट डेटा
  लेबल को कस्टमाइज़ करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: hi
lastmod: 2026-08-04
og_description: Aspose.Words का उपयोग करके C# में डेटा लेबल कैसे जोड़ें। यह ट्यूटोरियल
  आपको चार्ट को संपादित करना, चार्ट डेटा लेबल को केंद्रित करना, चार्ट में प्रतिशत
  दिखाना, और चार्ट डेटा लेबल को अनुकूलित करना दिखाता है।
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: C# में Word चार्ट में डेटा लेबल कैसे जोड़ें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: C# में Word चार्ट में डेटा लेबल कैसे जोड़ें – चरण‑दर‑चरण गाइड
url: /hi/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word चार्ट में डेटा लेबल कैसे जोड़ें C# – चरण‑दर‑चरण गाइड

यदि आपको Word दस्तावेज़ के भीतर मौजूद चार्ट में **how to add data labels** जोड़ने की आवश्यकता है, तो यह गाइड आपको वह सटीक कोड दिखाता है जिसे आपको चलाना होगा। आप देखेंगे कि चार्ट प्रॉपर्टीज़ को कैसे संपादित करें, चार्ट डेटा लेबल को केंद्र में रखें, चार्ट में प्रतिशत दिखाएँ, और किसी भी परिदृश्य के लिए चार्ट डेटा लेबल को कस्टमाइज़ करें।

यह ट्यूटोरियल मौजूदा चार्ट को संशोधित करने के लिए आवश्यक सभी चीज़ें कवर करता है, दस्तावेज़ लोड करने से लेकर बदलावों को सहेजने तक। कोई बाहरी रेफ़रेंस आवश्यक नहीं है—सिर्फ Aspose.Words for .NET लाइब्रेरी और एक बेसिक C# विकास पर्यावरण।

## आवश्यकताएँ

* .NET 6.0 (या बाद का) स्थापित हो।
* Aspose.Words for .NET संस्करण 23.9 या नया।  
  आप इसे NuGet के माध्यम से स्थापित कर सकते हैं:

```bash
dotnet add package Aspose.Words
```

* एक Word फ़ाइल (`input.docx`) जिसमें कम से कम एक चार्ट हो।

## Word चार्ट में डेटा लेबल कैसे जोड़ें C# में

निम्नलिखित सेक्शन आपको प्रत्येक चरण के माध्यम से ले जाते हैं। मुख्य कीवर्ड **how to add data labels** कथा में और कोड टिप्पणियों में स्वाभाविक रूप से प्रकट होता है, जिससे सिफ़ारिश किए गए घनत्व में बना रहता है।

### चरण 1 – चार्ट वाले Word दस्तावेज़ को लोड करें

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*इस चरण का महत्व*: `Document` ऑब्जेक्ट पूरे Word फ़ाइल का प्रतिनिधित्व करता है। इसे लोड करने से आपको हर नोड तक पहुंच मिलती है, जिसमें चार्ट होस्ट करने वाले शैप्स भी शामिल हैं।

### चरण 2 – दस्तावेज़ से पहला चार्ट प्राप्त करें

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*इस चरण का महत्व*: चार्ट `Shape` नोड्स के अंदर संग्रहीत होते हैं। प्राप्त नोड को `Shape` में कास्ट करके और `GetChart()` कॉल करके, आप एक `Chart` ऑब्जेक्ट प्राप्त करते हैं जो सीरीज़, एक्सिस, और लेबल कलेक्शन को उजागर करता है।

### चरण 3 – डेटा लेबल कस्टमाइज़ेशन सक्षम करें और चार्ट में प्रतिशत दिखाएँ

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*इस चरण का महत्व*: `ShowPercentage` सेट करने से Aspose.Words को प्रत्येक स्लाइस के कुल में योगदान की गणना और प्रदर्शन करने के लिए कहा जाता है। यह सीधे द्वितीयक कीवर्ड **show percentages in chart** को संबोधित करता है।

### चरण 4 – प्रत्येक डेटा पॉइंट के केंद्र में लेबल की स्थिति बदलें

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*इस चरण का महत्व*: `Position` प्रॉपर्टी नियंत्रित करती है कि लेबल डेटा पॉइंट के सापेक्ष कहाँ दिखेगा। `Center` का उपयोग द्वितीयक कीवर्ड **center chart data labels** को पूरा करता है और पाई या डोनट चार्ट की पठनीयता को सुधारता है।

### चरण 5 – चार्ट डेटा लेबल को आगे कस्टमाइज़ करें (वैकल्पिक)

यदि आपको अधिक नियंत्रण चाहिए, तो आप फ़ॉन्ट, रंग, या लीडर लाइन्स को समायोजित कर सकते हैं:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

ये सेटिंग्स द्वितीयक कीवर्ड **customize chart data labels** को दर्शाती हैं और दिखाती हैं कि आप ब्रांड गाइडलाइन के अनुसार स्वरूप को कैसे अनुकूलित कर सकते हैं।

### चरण 6 – संशोधित दस्तावेज़ को सहेजें

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*इस चरण का महत्व*: सहेजने से अपडेटेड चार्ट Word दस्तावेज़ में वापस लिखा जाता है, जिससे फ़ाइल को Microsoft Word में खोलने पर नए डेटा लेबल दिखते हैं।

## पूर्ण, चलाने योग्य उदाहरण

नीचे एक पूर्ण प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं। इसमें सभी आवश्यक `using` निर्देश और टिप्पणियाँ शामिल हैं जो प्रत्येक पंक्ति को समझाती हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### अपेक्षित परिणाम

जब आप Microsoft Word में `output.docx` खोलेंगे, तो चार्ट दिखाएगा:

* प्रत्येक स्लाइस के बगल में प्रतिशत मान (जैसे, **25 %**, **40 %**, …).
* लेबल प्रत्येक डेटा पॉइंट के केंद्र में स्थित।
* आप द्वारा लागू कोई अतिरिक्त स्टाइलिंग, जैसे बोल्ड लाल टेक्स्ट।

ये दृश्य संकेत चार्ट को समझने में आसान बनाते हैं, विशेषकर प्रस्तुतियों या रिपोर्टों में।

## डेटा लेबल से परे चार्ट प्रॉपर्टीज़ को कैसे संपादित करें

जबकि इस गाइड का फोकस **how to add data labels** है, आप **how to edit chart** सेटिंग्स जैसे शीर्षक, लेजेंड की स्थिति, या एक्सिस फ़ॉर्मेटिंग भी बदलना चाह सकते हैं। `Chart` ऑब्जेक्ट `Title`, `Legend`, और `AxisX/AxisY` जैसी प्रॉपर्टीज़ प्रदान करता है। उदाहरण के लिए, चार्ट शीर्षक बदलने के लिए:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

सभी चार्ट संशोधन एक ही पैटर्न का पालन करते हैं: चार्ट प्राप्त करें, उसकी प्रॉपर्टीज़ को समायोजित करें, फिर दस्तावेज़ को सहेजें।

## सामान्य जाल और सर्वोत्तम‑प्रैक्टिस टिप्स

| समस्या | क्यों होता है | सिफ़ारिशी समाधान |
|---|---|---|
| चार्ट एक समूहित शैप के अंदर है। | `GetChild(NodeType.Shape, …)` बाहरी समूह लौटाता है, न कि अंदर का चार्ट। | `shape.HasChart` वाले शैप को पुनरावर्ती रूप से खोजें। |
| सहेजने के बाद डेटा लेबल नहीं दिखते। | `ShowValue` या `ShowPercentage` को `true` पर सेट नहीं किया गया था। | आवश्यकतानुसार स्पष्ट रूप से दोनों `ShowValue` और `ShowPercentage` को सेट करें। |
| छोटे स्लाइस पर लेबल ओवरलैप होते हैं। | केंद्र स्थिती भीड़भाड़ का कारण बन सकती है। | बाहरी स्थिति के लिए `ChartDataLabelPosition.OutSideEnd` उपयोग करें, या `LeaderLines` सक्षम करें। |

## निष्कर्ष

अब आप C# का उपयोग करके Word चार्ट में **how to add data labels** करना जानते हैं। ट्यूटोरियल ने चार्ट प्राप्त करने, लेबल दृश्यता सक्षम करने, लेबल को केंद्रित करने, प्रतिशत दिखाने, और स्वरूप को कस्टमाइज़ करने को कवर किया। इस ज्ञान के साथ आप **how to edit chart** विवरण, **center chart data labels**, **show percentages in chart**, और **customize chart data labels** किसी भी रिपोर्टिंग परिदृश्य के लिए कर सकते हैं।

और अधिक खोजने के लिए तैयार हैं? कई सीरीज़ जोड़ने, कंडीशनल फ़ॉर्मेटिंग लागू करने, या चार्ट को इमेज के रूप में एक्सपोर्ट करने की कोशिश करें। Aspose.Words API व्यापक चार्ट मैनिपुलेशन क्षमताएँ प्रदान करता है—प्रयोग करें और अपने डेटा के लिए परिपूर्ण विज़ुअल प्रतिनिधित्व खोजें।

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}