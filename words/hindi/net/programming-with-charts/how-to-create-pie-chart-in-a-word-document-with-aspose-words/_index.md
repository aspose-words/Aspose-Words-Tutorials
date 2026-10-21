---
category: general
date: 2026-09-21
description: Aspose.Words का उपयोग करके पाई चार्ट बनाना और उसे Word में सम्मिलित करना,
  पाई चार्ट में डेटा लेबल जोड़ना, तथा पाई चार्ट पर प्रतिशत दिखाना, केवल कुछ ही चरणों
  में सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: hi
lastmod: 2026-09-21
og_description: Aspose.Words का उपयोग करके Word में पाई चार्ट बनाएं, चार्ट को Word
  में डालें, पाई चार्ट में डेटा लेबल जोड़ें, और पाई चार्ट पर प्रतिशत दिखाएं—सभी स्पष्ट
  कोड उदाहरणों के साथ।
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Aspose.Words के साथ Word में पाई चार्ट बनाएं – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Aspose.Words के साथ Word दस्तावेज़ में पाई चार्ट कैसे बनाएं
url: /hi/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ Word दस्तावेज़ में पाई चार्ट कैसे बनाएं

यदि आपको प्रोग्रामेटिक रूप से **पाई चार्ट बनाना** है, तो Aspose.Words इसे आसान बनाता है। इस ट्यूटोरियल में आप देखेंगे कि **Word में चार्ट कैसे डालें**, सीरीज़ को कॉन्फ़िगर करें, **पाई चार्ट में डेटा लेबल जोड़ें**, और अंत में **पाई चार्ट पर प्रतिशत दिखाएँ** ताकि विज़ुअल सटीक मान दर्शा सके। अंत तक आपके पास एक पूर्ण, चलाने योग्य उदाहरण होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

यह गाइड सभी आवश्यक चीज़ें कवर करता है: आवश्यक NuGet पैकेज, पूरा C# स्रोत, प्रत्येक API कॉल क्यों महत्वपूर्ण है इसका स्पष्टीकरण, और चार्ट को कस्टमाइज़ करने के टिप्स। कोई बाहरी दस्तावेज़ आवश्यक नहीं—सिर्फ कॉपी करें, चलाएँ, और अनुकूलित करें।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो।  
* Visual Studio 2022 (या कोई भी IDE जो .NET को सपोर्ट करता हो)।  
* Aspose.Words for .NET लाइसेंस (टेस्टिंग के लिए फ्री ट्रायल चलती है)।  
* C# और Word दस्तावेज़ संरचनाओं की बुनियादी समझ।

यदि ये सब आपके पास हैं, तो सीधे कोड की ओर बढ़ें।

## Step 1: Set up the project and import Aspose.Words

एक नया कंसोल प्रोजेक्ट बनाएं और Aspose.Words NuGet पैकेज जोड़ें:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

यह पैकेज `Aspose.Words.Drawing.Charts` नेमस्पेस शामिल करता है, जिसमें `Chart` और `ChartSeries` क्लासेज़ हैं जिन्हें हम उपयोग करेंगे।

> **Pro tip:** लाइसेंस फ़ाइल (`Aspose.Words.lic`) को प्रोजेक्ट रूट में रखें और स्टार्टअप पर लोड करें ताकि इवैल्यूएशन वॉटरमार्क न दिखें।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Step 2: Create a blank document and a DocumentBuilder

`Document` Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` कंटेंट डालने के लिए एक फ़्लुएंट API प्रदान करता है।

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder` वर्तमान इन्सर्शन पॉइंट को बनाए रखता है, जिससे चार्ट ठीक उसी स्थान पर आता है जहाँ आप चाहते हैं कि वह दस्तावेज़ प्रवाह में दिखे।

## Step 3: Insert a pie chart into the Word document

अब हम **Word में चार्ट डालते** हैं। `InsertChart` मेथड चार्ट प्रकार, चौड़ाई और ऊँचाई (पॉइंट्स में) लेता है।

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

इस चरण पर चार्ट में डिफ़ॉल्ट डेटा सीरीज़ होती है जिसमें प्लेसहोल्डर वैल्यूज़ (25, 25, 25, 25) होते हैं। आवश्यकता पड़ने पर आप इन्हें बाद में बदल सकते हैं।

## Step 4: Access the first series and customize data labels

पाई चार्ट में आमतौर पर एक ही सीरीज़ होती है। **पाई चार्ट में डेटा लेबल जोड़ने** के लिए, हम इसे प्राप्त करते हैं और प्रतिशत डिस्प्ले को सक्षम करते हैं।

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Why we set `ShowPercentage`:** यह फ़्लैग Aspose.Words को प्रत्येक स्लाइस के योगदान की गणना करके उसे प्रतिशत के रूप में रेंडर करने को कहता है। `Position` प्रॉपर्टी सुनिश्चित करती है कि लेबल स्लाइस के ऊपर ओवरलैप न करे, जिससे पठनीयता बढ़ती है—विशेषकर जब स्लाइस छोटे हों।

## Step 5: (Optional) Replace the placeholder data

यदि आप विशिष्ट मान चाहते हैं, तो डिफ़ॉल्ट पॉइंट्स को बदलें:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

प्रदर्शित प्रतिशत स्वचालित रूप से नए मानों के अनुसार समायोजित हो जाएंगे।

## Step 6: Save the document

अंत में, दस्तावेज़ को डिस्क पर लिखें। एक्सटेंशन फ़ॉर्मेट तय करता है; `.docx` एक आधुनिक Word फ़ाइल बनाता है।

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

प्रोग्राम चलाने पर आउटपुट फ़ोल्डर में **PieChart.docx** नाम की फ़ाइल बनती है। इसे Microsoft Word में खोलने पर प्रत्येक स्लाइस के प्रतिशत लेबल के साथ पाई चार्ट दिखेगा, लेबल स्लाइस के बाहर स्थित होगा।

### Expected output

जनरेटेड दस्तावेज़ खोलने पर आपको दिखना चाहिए:

* एकल पाई चार्ट, आकार 400 × 300 pt।  
* चार स्लाइस (या जितने पॉइंट्स आपने जोड़े)।  
* “40 %”, “30 %” आदि जैसे प्रतिशत लेबल, प्रत्येक स्लाइस के बाहर प्रदर्शित।

यदि लेबल स्लाइस के अंदर दिख रहे हों, तो सुनिश्चित करें कि `ChartDataLabelPosition.OutsideEnd` सही ढंग से सेट किया गया है।

## Step 7: Common variations and edge cases

### Adding a title to the chart

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Changing slice colors

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Handling an empty series

यदि आपका डेटा स्रोत खाली हो सकता है, तो `IndexOutOfRangeException` से बचने के लिए गार्ड लगाएँ:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exporting to PDF instead of Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

चार्ट रेंडरिंग लॉजिक वही रहता है; Aspose.Words स्वचालित रूप से Word लेआउट को PDF में बदल देता है।

## Full source listing

नीचे पूरा, तैयार‑चलाने‑योग्य प्रोग्राम दिया गया है। इसे `Program.cs` में कॉपी करें और `dotnet run` चलाएँ।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusion

अब आप जानते हैं कि Aspose.Words का उपयोग करके Word फ़ाइल में **पाई चार्ट कैसे बनाएं**, **Word में चार्ट कैसे डालें**, **पाई चार्ट में डेटा लेबल कैसे जोड़ें**, और **पाई चार्ट पर प्रतिशत कैसे दिखाएँ**। यह उदाहरण पूर्ण वर्कफ़्लो दर्शाता है—प्रोजेक्ट सेटअप से लेकर अंतिम दस्तावेज़ तक—ताकि आप इसे डैशबोर्ड, रिपोर्ट या स्वचालित इनवॉइस जनरेशन के लिए अनुकूलित कर सकें।  

अगले चरण में, **चार्ट में प्रतिशत कैसे दिखाएँ** जैसी संबंधित विषयों का अन्वेषण करें, चार्ट रंग कस्टमाइज़ करें, या वितरण के लिए Word दस्तावेज़ को PDF में बदलें। विभिन्न चार्ट प्रकार (Bar, Line) को उसी `InsertChart` मेथड से आज़माएँ और अपनी ऑटोमेशन क्षमताओं को विस्तृत करें।

Happy charting!

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर्स में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Word में Aspose.Words for .NET का उपयोग करके कॉलम चार्ट डालें](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET का उपयोग करके Word स्कैटर चार्ट बनाएं](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Word दस्तावेज़ में एरिया चार्ट डालें | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}