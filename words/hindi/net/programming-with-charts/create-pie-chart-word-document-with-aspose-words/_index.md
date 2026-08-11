---
category: general
date: 2026-08-10
description: Aspose.Words का उपयोग करके पाई चार्ट वाला Word दस्तावेज़ बनाएं। चार्ट
  कैसे डालें, पाई चार्ट के रंग कैसे अनुकूलित करें, और C# में पाई स्लाइस का रंग कैसे
  बदलें, सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: hi
lastmod: 2026-08-10
og_description: Aspose.Words के साथ पाई चार्ट वाला Word दस्तावेज़ बनाएं। यह गाइड बताता
  है कि कैसे चार्ट डालें, पाई चार्ट के रंग को कस्टमाइज़ करें, और C# एप्लिकेशन में
  पाई स्लाइस का रंग बदलें।
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: पाई चार्ट वर्ड दस्तावेज़ बनाएं – Aspose.Words गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Aspose.Words के साथ पाई चार्ट वाला Word दस्तावेज़ बनाएं
url: /hi/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ पाई चार्ट वाला Word दस्तावेज़ बनाएं

यदि आपको प्रोग्रामेटिकली **पाई चार्ट वाला Word दस्तावेज़ बनाना** है, तो यह ट्यूटोरियल आपको बिल्कुल वही दिखाएगा। हम एक चार्ट डालने, **पाई चार्ट के रंगों को कस्टमाइज़ करने**, और Aspose.Words for .NET का उपयोग करके **पाई स्लाइस का रंग बदलने** की प्रक्रिया को चरण-दर-चरण बताएँगे।

आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जिसे आप Visual Studio में कॉपी कर सकते हैं, चलाएँ, और तुरंत उत्पन्न *.docx* फ़ाइल खोलकर स्टाइल किए गए पाई चार्ट की जाँच कर सकते हैं। कोई बाहरी दस्तावेज़ीकरण आवश्यक नहीं है—आपको जो कुछ भी चाहिए वह इस गाइड में ही है।

## आवश्यकताएँ

* .NET 6.0 SDK या बाद का स्थापित हो  
* एक वैध Aspose.Words for .NET लाइसेंस (या अस्थायी मूल्यांकन कुंजी)  
* Visual Studio 2022 (या कोई भी C# IDE)  

कोड केवल `Aspose.Words` और `Aspose.Words.Drawing.Charts` नेमस्पेसेस का उपयोग करता है, इसलिए Aspose.Words लाइब्रेरी के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## पाई चार्ट वाला Word दस्तावेज़ बनाएं – पूर्ण उदाहरण

निम्नलिखित C# प्रोग्राम एक नया Word दस्तावेज़ बनाता है, पाई चार्ट डालता है, पहले दो स्लाइस को स्टाइल करता है, और फ़ाइल को सहेजता है। प्रत्येक चरण का विस्तृत विवरण दिया गया है।

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### प्रत्येक चरण की व्याख्या

| Step | यह क्या करता है | क्यों महत्वपूर्ण है |
|------|----------------|-------------------|
| **1** | एक नया `Document` और एक `DocumentBuilder` बनाता है। | `DocumentBuilder` Word फ़ाइल में सामग्री, जैसे चार्ट, डालने के लिए सहज (fluent) मेथड्स प्रदान करता है। |
| **2** | `InsertChart` को `ChartType.Pie` और एक निश्चित आकार के साथ कॉल करता है। | `InsertChart` **चार्ट डालने का तरीका** मेथड है; चौड़ाई/ऊँचाई निर्दिष्ट करने से चार्ट पृष्ठ पर ठीक से फिट हो जाता है। |
| **3** | तीन श्रेणियों और संख्यात्मक मानों के साथ एक डेटा सीरीज़ जोड़ता है। | डेटा के बिना पाई चार्ट अदृश्य रहता है; इसे भरने से स्टाइलिंग चरण प्रदर्शित होते हैं। |
| **4** | पहले पॉइंट पर `Explosion` सेट करता है। | स्लाइस को एक्सप्लोड करने से किसी विशेष भाग का ध्यान आकर्षित होता है—मुख्य डेटा को हाइलाइट करने में उपयोगी। |
| **5** | पहले दो पॉइंट्स के लिए `ForeColor` सेट करता है। | यह **पाई चार्ट के रंगों को कस्टमाइज़ करने** का मुख्य भाग है; आप कोई भी `System.Drawing.Color` उपयोग कर सकते हैं। |
| **6** | अतिरिक्त स्लाइस के लिए **पाई स्लाइस का रंग बदलने** का तरीका दिखाता है। | दिखाता है कि स्टाइलिंग केवल पहले दो स्लाइस तक सीमित नहीं है; आप प्रत्येक स्लाइस को अलग-अलग रंग सकते हैं। |
| **7** | दस्तावेज़ को `PieChartStyled.docx` के रूप में सहेजता है। | अंतिम आउटपुट को Microsoft Word, Google Docs, या किसी भी संगत व्यूअर में खोला जा सकता है। |

#### अपेक्षित आउटपुट

`PieChartStyled.docx` खोलने पर 400 × 300 pt पाई चार्ट वाला एक पृष्ठ दिखता है:

* Slice 1 (orange) बाहर की ओर एक्सप्लोड किया गया है।  
* Slice 2 (green) एक्सप्लोडेड स्लाइस के बगल में दिखता है।  
* Slice 3 (steel‑blue) शेष भाग को भरता है।

चार्ट डेटा मानों (30, 45, 25) और आपके द्वारा परिभाषित कस्टम रंगों को दर्शाता है।

## पाई को स्टाइल करने के तरीके – अतिरिक्त टिप्स

* **थीम रंगों का उपयोग करें** – `Color.Orange` को हार्ड‑कोड करने के बजाय, आप दस्तावेज़ थीम से रंग ले सकते हैं:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **डेटा लेबल जोड़ें** – यदि आप चार्ट पर प्रतिशत दिखाना चाहते हैं:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **डायनामिक रूप से आकार बदलें** – पेज मार्जिन के आधार पर चार्ट का आकार गणना करें:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

ये विविधताएँ **पाई को स्टाइल करने के तरीके** की लचीलापन को बुनियादी उदाहरण से परे दर्शाती हैं।

## सामान्य प्रश्नों के उत्तर

**प्रश्न: क्या यह .NET Core के साथ काम करता है?**  
**उत्तर:** हाँ। Aspose.Words for .NET .NET Core, .NET 5, .NET 6, और बाद के संस्करणों के साथ संगत है। बस वही NuGet पैकेज रेफ़रेंस करें।

**प्रश्न: यदि मुझे पाई के बजाय डोनट चार्ट चाहिए तो?**  
**उत्तर:** `ChartType.Pie` को `ChartType.Doughnut` से बदलें। वही स्टाइलिंग API (`Explosion`, `ForeColor`) लागू होते हैं।

**प्रश्न: क्या मैं चार्ट को मौजूदा दस्तावेज़ में डाल सकता हूँ?**  
**उत्तर:** मौजूदा फ़ाइल को `new Document("Existing.docx")` से खोलें, उस दस्तावेज़ के लिए `DocumentBuilder` बनाएं, और इच्छित कर्सर स्थिति पर `InsertChart` कॉल करें।

**प्रश्न: मैं बड़े डेटा सेट को कैसे संभालूँ?**  
**उत्तर:** पाई चार्ट सीमित संख्या में श्रेणियों (आमतौर पर < 10) के लिए सबसे उपयुक्त होते हैं। कई श्रेणियों के लिए, बार या कॉलम चार्ट पर विचार करें।

## पूर्ण स्रोत कोड सारांश

नीचे एक ब्लॉक में पूरा प्रोग्राम दिया गया है, जिससे आप आसानी से कॉपी‑पेस्ट कर सकें:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

इस कोड को चलाने से पहले वर्णित स्टाइल किए गए पाई चार्ट वाला Word दस्तावेज़ बनता है।

## निष्कर्ष

अब आप Aspose.Words का उपयोग करके **पाई चार्ट वाला Word** दस्तावेज़ **बनाना**, **पाई चार्ट के रंगों को कस्टमाइज़ करना**, और प्रोग्रामेटिकली **पाई स्लाइस का रंग बदलना** जानते हैं। इस गाइड में चार्ट डालना, डेटा भरना, स्लाइस को एक्सप्लोड करना, कस्टम रंग लागू करना, और परिणाम सहेजना शामिल था।  

अब आप पाई के अलावा अन्य **चार्ट डालने के तरीके**, लेजेंड जोड़ना, या कई चार्ट वाले मल्टी‑पेज रिपोर्ट बनाना जैसे संबंधित विषयों का पता लगा सकते हैं। अपनी रिपोर्टिंग आवश्यकताओं के अनुसार विभिन्न रंग योजनाओं और डेटा सेट के साथ प्रयोग करें।

कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन तरीकों का अन्वेषण करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके Word में कॉलम चार्ट डालें](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET | Word दस्तावेज़ में एरिया चार्ट डालें](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET का उपयोग करके Word में स्कैटर चार्ट बनाएं](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}