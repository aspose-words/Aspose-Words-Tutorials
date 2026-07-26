---
category: general
date: 2026-07-26
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में पाई चार्ट डालें। कुछ ही
  चरणों में चार्ट जोड़ना, स्लाइस को एक्सप्लोड करना और प्रतिशत दिखाना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: hi
lastmod: 2026-07-26
og_description: Aspose.Words के साथ Word फ़ाइल में पाई चार्ट डालें। इस गाइड का पालन
  करके जानें कि चार्ट कैसे जोड़ें, स्लाइस को कैसे एक्सप्लोड करें, और प्रतिशत जल्दी
  से कैसे दिखाएँ।
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Word में पाई चार्ट डालें – चरण-दर-चरण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Aspose.Words के साथ Word में पाई चार्ट डालें – पूर्ण गाइड
url: /hi/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ Word में पाई चार्ट डालें – पूर्ण गाइड

क्या आपको कभी Word रिपोर्ट में **पाई चार्ट डालने** की ज़रूरत पड़ी है लेकिन शुरुआत नहीं पता थी? आप अकेले नहीं हैं। कई बिज़नेस ऐप्स में पाई चार्ट का विज़ुअल इम्पैक्ट डेटा को तुरंत समझने योग्य बनाता है, और Aspose.Words कुछ ही कोड लाइनों से इसे संभव बनाता है।

इस ट्यूटोरियल में हम **Word में चार्ट जोड़ने**, ज़ोर देने के लिए स्लाइस को एक्सप्लोड करने, और डेटा लेबल पर प्रतिशत दिखाने के सटीक चरणों को देखेंगे। अंत तक आपके पास एक तैयार‑चलाने‑योग्य उदाहरण होगा जिसे आप किसी भी .NET प्रोजेक्ट में डाल सकते हैं।

---

## आवश्यकताएँ

- .NET 6.0 या बाद का संस्करण (कोड .NET Core और .NET Framework दोनों में काम करता है)
- Aspose.Words for .NET NuGet पैकेज स्थापित हो  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# सिंटैक्स की बुनियादी समझ – कोई विशेष ज्ञान आवश्यक नहीं
- आपका पसंदीदा IDE (Visual Studio, Rider, या VS Code)

बस इतना ही। चलिए काम शुरू करते हैं।

---

## Word दस्तावेज़ में पाई चार्ट डालें

पहले हमें एक नया `Document` ऑब्जेक्ट और एक `DocumentBuilder` चाहिए। बिल्डर को ऐसे समझें जैसे वह पेन हो जो सीधे Word कैनवास पर लिखता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` पूरे .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` हमें चार्ट, टेबल और टेक्स्ट जैसे तत्वों को डालने के लिए एक सुविधाजनक API देता है। यह हर **how to add chart** ऑपरेशन की नींव है।

---

## Word में चार्ट कैसे जोड़ें

अब हमारे पास बिल्डर है, हम वास्तव में **पाई चार्ट डाल सकते** हैं। `insertChart` मेथड चार्ट का प्रकार और पॉइंट्स में वांछित आयाम लेता है (1 पॉइंट = 1/72 इंच)।

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tip:** अगर आपको अलग आकार चाहिए, तो केवल चौड़ाई और ऊँचाई मानों को बदलें। चार्ट स्वचालित रूप से पेज मार्जिन में फिट होने के लिए स्केल हो जाएगा।

---

## जोर देने के लिए स्लाइस को एक्सप्लोड कैसे करें

एक सामान्य विज़ुअल ट्यून यह है कि स्लाइस को “एक्सप्लोड” किया जाए ताकि वह सर्कल से बाहर निकले। इससे पाठक की नजर सबसे महत्वपूर्ण हिस्से की ओर आकर्षित होती है।

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Why explode a slice?** जब आप किसी विशेष श्रेणी—जैसे वित्तीय रिपोर्ट में “Q1 revenue”—को हाइलाइट करना चाहते हैं, तो स्लाइस को एक्सप्लोड करने से वह तुरंत दिखाई देता है, बिना अतिरिक्त टेक्स्ट के।

---

## डेटा लेबल पर प्रतिशत कैसे दिखाएँ

अधिकांश पाई चार्ट बेहतर दिखते हैं जब प्रत्येक स्लाइस अपना प्रतिशत दिखाता है। Aspose.Words हमें यह एक ही प्रॉपर्टी से ऑन करने देता है।

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Quick note:** `ShowPercentage` फ़्लैग सीरीज़ के सभी पॉइंट्स पर लागू होता है, इसलिए आपको इसे प्रत्येक स्लाइस के लिए अलग से सेट करने की जरूरत नहीं है।

---

## चार्ट वाले दस्तावेज़ को सहेजें

आखिर में, हम दस्तावेज़ को डिस्क पर लिखते हैं। कोई भी फ़ोल्डर चुनें; बस यह सुनिश्चित करें कि पाथ मौजूद हो।

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

जब आप `PieChart.docx` को Microsoft Word में खोलेंगे, तो आपको एक पूरी तरह से रेंडर किया गया पाई चार्ट दिखेगा जिसमें पहला स्लाइस एक्सप्लोड किया गया है और प्रतिशत प्रदर्शित हैं—बिल्कुल वही जो आप एक परिष्कृत बिज़नेस रिपोर्ट से उम्मीद करेंगे।

---

## पूरा कार्यशील उदाहरण

नीचे पूरा, कॉपी‑एंड‑पेस्ट‑तैयार प्रोग्राम दिया गया है। इसे एक कंसोल ऐप के रूप में चलाएँ और आउटपुट फ़ाइल की जाँच करें।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected result:** जेनरेट किए गए `PieChart.docx` को खोलें। आपको “Sales Q1” शीर्षक वाला तीन‑स्लाइस पाई चार्ट दिखेगा, जिसमें पहला स्लाइस बाहर निकला हुआ है और प्रत्येक स्लाइस पर क्रमशः “30 %”, “45 %”, और “25 %” लिखा होगा। विज़ुअल डेटा के साथ पूरी तरह मेल खाता है।

---

## सामान्य प्रश्न और किनारे के मामले

- **What if I need more than one series?**  
  बस अतिरिक्त `ChartSeries` ऑब्जेक्ट्स को `chart.Series` में जोड़ें। प्रत्येक सीरीज़ का अपना डेटा सेट, रंग और एक्सप्लोड सेटिंग्स हो सकती हैं।

- **Can I change the chart’s colors?**  
  हाँ। प्रत्येक `ChartPoint` में `Format.Fill.ForeColor` प्रॉपर्टी होती है जिसे आप किसी भी `System.Drawing.Color` पर सेट कर सकते हैं।

- **What about different chart types?**  
  `ChartType` एन्नुम में बार, लाइन, डोनट और कई अन्य प्रकार शामिल हैं। अपनी जरूरत के अनुसार `ChartType.Pie` को किसी अन्य प्रकार से बदलें।

- **Is the chart editable in Word after insertion?**  
  बिल्कुल। Word चार्ट को एक नेटिव Office चार्ट मानता है, इसलिए उपयोगकर्ता इसे डबल‑क्लिक करके बिल्ट‑इन चार्ट एडिटर खोल सकते हैं।

---

## निष्कर्ष

अब आप बिल्कुल जानते हैं कि Aspose.Words का उपयोग करके Word दस्तावेज़ में **पाई चार्ट कैसे डालें**, **Word में चार्ट कैसे जोड़ें**, **स्लाइस को एक्सप्लोड कैसे करें**, और **डेटा लेबल पर प्रतिशत कैसे दिखाएँ**। ऊपर दिया गया पूरा उदाहरण चलाने के लिए तैयार है, और आप इसे कस्टम डेटा, स्टाइलिंग या अतिरिक्त सीरीज़ के साथ विस्तारित कर सकते हैं।

अगला कदम तैयार है? पाई को डोनट चार्ट में बदलें, या विभिन्न डेटा सेटों के साथ स्वचालित रूप से कई रिपोर्ट जनरेट करें। यदि आप अन्य विज़ुअलाइज़ेशन में रुचि रखते हैं, तो **how to add chart** के लिए बार और लाइन ग्राफ़ गाइड देखें, या गहरी कस्टमाइज़ेशन के लिए **add chart to word** API रेफ़रेंस देखें।

हैप्पी कोडिंग, और आपके दस्तावेज़ हमेशा एक परिपूर्ण स्लाइस की तरह स्पष्ट रहें!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}