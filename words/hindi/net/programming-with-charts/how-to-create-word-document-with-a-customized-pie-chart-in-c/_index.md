---
category: general
date: 2026-10-07
description: जानिए कैसे Aspose.Words का उपयोग करके C# में वर्ड दस्तावेज़ बनाएं और
  पाई चार्ट सम्मिलित करें। यह गाइड यह भी दिखाता है कि कस्टम चार्ट लेबल के साथ वर्ड
  फ़ाइल कैसे जेनरेट करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: hi
lastmod: 2026-10-07
og_description: C# में वर्ड दस्तावेज़ बनाएं और पाई चार्ट सम्मिलित करें। पूरी तरह से
  अनुकूलित चार्ट लेबल के साथ वर्ड फ़ाइल बनाने के लिए इस चरण‑दर‑चरण गाइड का पालन करें।
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: C# में कस्टमाइज़्ड पाई चार्ट के साथ एक Word दस्तावेज़ बनाएं
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: C# में कस्टमाइज़्ड पाई चार्ट के साथ वर्ड डॉक्यूमेंट कैसे बनाएं
url: /hi/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में कस्टमाइज़्ड पाई चार्ट के साथ वर्ड डॉक्यूमेंट कैसे बनाएं

यदि आपको प्रोग्रामेटिक रूप से **वर्ड डॉक्यूमेंट बनाना** है, तो यह ट्यूटोरियल दिखाता है कि **पाई चार्ट कैसे इन्सर्ट करें** और Aspose.Words for .NET का उपयोग करके उसके डेटा लेबल को कैसे कस्टमाइज़ करें। आप यह भी सीखेंगे कि **वर्ड फ़ाइल कैसे जेनरेट करें** जिसमें पूरी तरह स्टाइल किया गया चार्ट हो, प्रोजेक्ट सेटअप से लेकर अंतिम डॉक्यूमेंट को सेव करने तक की पूरी प्रक्रिया को कवर करते हुए।

यह गाइड प्रत्येक चरण को विस्तार से बताता है: चार्ट जोड़ना, लेबल पोज़िशन समायोजित करना, लीडर लाइन्स सक्षम करना, और अंत में परिणाम को `.docx` फ़ाइल के रूप में सेव करना। Aspose.Words लाइब्रेरी के अलावा कोई बाहरी टूल आवश्यक नहीं है, और पूर्ण सोर्स कोड प्रदान किया गया है ताकि आप इसे कॉपी‑पेस्ट करके तुरंत चला सकें।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

* .NET 6.0 SDK या बाद का संस्करण स्थापित हो  
* एक वैध Aspose.Words for .NET लाइसेंस (या फ्री इवैल्यूएशन की)  
* Visual Studio 2022 या Visual Studio Code जैसा IDE  

आपको अपने प्रोजेक्ट में निम्नलिखित NuGet पैकेज जोड़ने होंगे:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

ये पैकेज `Document`, `DocumentBuilder`, और चार्ट‑संबंधित क्लासेज़ को एक्सपोज़ करते हैं, जिनका उपयोग नीचे दिए गए उदाहरणों में किया गया है।

## Create word document and add a chart

पहला चरण **वर्ड डॉक्यूमेंट बनाना** है और एक `DocumentBuilder` प्राप्त करना है जो आपको कंटेंट इन्सर्ट करने की सुविधा देता है। बिल्डर एक कर्सर की तरह काम करता है जो डॉक्यूमेंट के भीतर स्थित होता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` ऑब्जेक्ट पूरे Word फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` ऐसे मेथड्स प्रदान करता है जैसे `InsertChart` जो ऑब्जेक्ट्स को सीधे डॉक्यूमेंट फ्लो में रखता है।

## Insert pie chart into the document

अब जब बिल्डर तैयार है, आप **पाई चार्ट इन्सर्ट** कर सकते हैं और उसका आकार निर्धारित कर सकते हैं। चार्ट बिल्डर की वर्तमान पोज़िशन पर जोड़ा जाता है।

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` एक `Chart` ऑब्जेक्ट रिटर्न करता है जिसे आप आगे मैनिपुलेट कर सकते हैं। सैंपल डेटा चार तिमाही बिक्री को दर्शाने वाले चार स्लाइस बनाता है।

## Customize pie chart data labels

चार्ट को अधिक पठनीय बनाने के लिए, अक्सर आपको **पाई चार्ट** के लेबल को कस्टमाइज़ करना पड़ता है—स्लाइस के बाहर पोज़िशन करना और लीडर लाइन्स दिखाना। यही वह जगह है जहाँ `ChartDataLabelCollection` काम आता है।

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

`Position` को `OutsideEnd` सेट करने से प्रत्येक लेबल स्लाइस के किनारे के बाहर चला जाता है, जबकि `ShowLeaderLines` एक लाइन ड्रॉ करता है जो लेबल को उसके स्लाइस से जोड़ती है। वैकल्पिक फ़्लैग्स `ShowValue` और `ShowPercentage` पाठकों को दोनों—कच्चे नंबर और प्रतिशत—प्रदान करते हैं।

**Pro tip:** यदि आपको लेबल फ़ॉन्ट फॉर्मेट करना है, तो `dataLabels.Font` का उपयोग करके साइज, रंग और स्टाइल सेट करें। इससे चार्ट आपके कॉरपोरेट ब्रांडिंग के साथ मेल खाता है।

## Save and generate word file

चार्ट पूरी तरह कॉन्फ़िगर हो जाने के बाद, आप `Document` इंस्टेंस को डिस्क पर सेव करके **वर्ड फ़ाइल जेनरेट** कर सकते हैं। अधिकतम कम्पैटिबिलिटी के लिए `.docx` फ़ॉर्मेट चुनें।

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

जब आप `CustomPieChart.docx` खोलेंगे, तो आपको चार स्लाइस वाला पाई चार्ट दिखेगा, प्रत्येक लेबल स्लाइस के बाहर होगा, लीडर लाइन्स से जुड़ा होगा, और दोनों वैल्यू व प्रतिशत प्रदर्शित करेगा।

![C# से बनाए गए कस्टमाइज़्ड पाई चार्ट वाला वर्ड डॉक्यूमेंट का स्क्रीनशॉट](image-placeholder.png)

*यह इमेज **वर्ड डॉक्यूमेंट बनाना** ट्यूटोरियल के अंतिम परिणाम को दर्शाती है।*

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | Add additional `ChartSeries` objects to `pieChart.Series`. Each series can have its own `DataLabels` collection for independent styling. |
| **Different chart size** | Change the width and height parameters in `InsertChart(width, height)`. Values are in points (1 pt ≈ 1/72 in). |
| **Chart title** | Use `pieChart.Title.Text = "Quarterly Sales"` to add a descriptive title. |
| **Export to PDF** | Call `document.Save("Report.pdf", SaveFormat.Pdf);` after the chart is built. |
| **License handling** | Place your license file (`Aspose.Words.lic`) in the application folder and load it with `new License().SetLicense("Aspose.Words.lic");` before creating the document. |

इन वैरिएशन्स के माध्यम से आप कई वास्तविक‑दुनिया परिदृश्यों में **पाई चार्ट कैसे जोड़ें** सवाल का उत्तर दे सकते हैं, साधारण रिपोर्ट से लेकर जटिल डैशबोर्ड तक।

## Conclusion

अब आप जानते हैं कि **वर्ड डॉक्यूमेंट कैसे बनाएं**, **पाई चार्ट कैसे इन्सर्ट करें**, और Aspose.Words for .NET का उपयोग करके **पाई चार्ट लेबल्स को कैसे कस्टमाइज़ करें**। पूरा उदाहरण एक साफ़ वर्कफ़्लो दर्शाता है: डॉक्यूमेंट इनिशियलाइज़ करना, चार्ट जोड़ना, डेटा‑लेबल पोज़िशनिंग समायोजित करना, लीडर लाइन्स सक्षम करना, और अंत में **वर्ड फ़ाइल जेनरेट** करना जिसे कोई भी शेयर कर सकता है।

इस ट्यूटोरियल को विभिन्न चार्ट टाइप्स (`ChartType.Column`, `ChartType.Line`) के साथ प्रयोग करके या कस्टम कलर पैलेट्स लागू करके अपने ब्रांड के अनुरूप बनाकर विस्तारित करें। यदि आपको कोई समस्या आती है, तो Aspose.Words डॉक्यूमेंटेशन देखें या “पाई चार्ट कैसे जोड़ें” जैसे संबंधित टॉपिक्स को एक्सप्लोर करें, जिसमें मल्टीपल सीरीज़ और डायनामिक डेटा सोर्सेज़ शामिल हैं।

Happy coding, and feel free to share your results or ask follow‑up questions in the comments!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}