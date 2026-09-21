---
category: general
date: 2026-09-21
description: C# का उपयोग करके Word लाइन चार्ट में सीरीज़ को फ़ॉर्मेट कैसे करें। Word
  दस्तावेज़ बनाना, लाइन चार्ट सम्मिलित करना, और कस्टम नंबर फ़ॉर्मेट लागू करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: hi
lastmod: 2026-09-21
og_description: C# का उपयोग करके Word लाइन चार्ट में सीरीज़ को फ़ॉर्मेट कैसे करें।
  यह ट्यूटोरियल आपको दिखाता है कि Word दस्तावेज़ कैसे बनाएं, लाइन चार्ट कैसे डालें,
  और कस्टम नंबर फ़ॉर्मेट कैसे लागू करें।
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: C# के साथ Word लाइन चार्ट में सीरीज़ को फ़ॉर्मेट कैसे करें – चरण‑दर‑चरण
  गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: C# के साथ Word लाइन चार्ट में सीरीज़ को कैसे फ़ॉर्मेट करें
url: /hi/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word लाइन चार्ट में सीरीज़ को फ़ॉर्मेट कैसे करें

यदि आपको Word लाइन चार्ट में **सीरीज़ को फ़ॉर्मेट** करने की आवश्यकता है, तो यह गाइड आपको एक पूर्ण, तुरंत चलाने योग्य समाधान प्रदान करता है। आप देखेंगे कि **Word दस्तावेज़ कैसे बनाएं**, **लाइन चार्ट कैसे डालें**, और Y‑मानों पर **कस्टम नंबर फ़ॉर्मेट कैसे लागू करें**—सब कुछ Aspose.Words for .NET के साथ।

चार्ट ऑब्जेक्ट मॉडल को समझने के बाद Word ऑटोमेशन सरल हो जाता है। इस ट्यूटोरियल के अंत तक आपके पास एक Word फ़ाइल होगी जिसमें एक लाइन चार्ट होगा और उसकी डेटा सीरीज़ दो दशमलव स्थान के साथ प्रतिशत के रूप में प्रदर्शित होगी।

## आप क्या हासिल करेंगे

* प्रोग्रामेटिकली एक खाली `.docx` फ़ाइल उत्पन्न करें।  
* आकार 400 × 300 पॉइंट्स वाला एक लाइन चार्ट जोड़ें।  
* चार्ट की पहली डेटा सीरीज़ तक पहुँचें।  
* फ़ॉर्मेट कोड `#,##0.00%` लागू करें ताकि Y‑मान प्रतिशत के रूप में दिखें।  

Aspose.Words NuGet पैकेज के अलावा कोई बाहरी टूल आवश्यक नहीं है।

## पूर्वापेक्षाएँ

* .NET 6.0 SDK या बाद का संस्करण।  
* Visual Studio 2022 (या कोई भी C# IDE)।  
* Aspose.Words for .NET 23.10 या नया – `dotnet add package Aspose.Words` के माध्यम से इंस्टॉल करें।  

कोड Windows, Linux, और macOS पर काम करता है क्योंकि Aspose.Words प्लेटफ़ॉर्म‑अज्ञेय है।

## Aspose.Words के साथ Word दस्तावेज़ बनाएं

पहला कदम `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट मेमोरी में पूरे Word फ़ाइल का प्रतिनिधित्व करता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*क्यों यह महत्वपूर्ण है*: `Document` सभी Word‑प्रोसेसिंग ऑपरेशनों का एंट्री पॉइंट है। इसके बिना आप पैराग्राफ, टेबल या चार्ट नहीं जोड़ सकते।

## दस्तावेज़ में लाइन चार्ट डालें

`DocumentBuilder` `Document` में कंटेंट लिखता है। `InsertChart` को कॉल करने से वर्तमान पृष्ठ पर एक चार्ट शैप बनता है।

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*क्यों यह महत्वपूर्ण है*: `InsertChart` एक `Chart` ऑब्जेक्ट लौटाता है जो आपको सीरीज़, एक्सिस और फ़ॉर्मेटिंग पर पूर्ण नियंत्रण देता है। आकार पैरामीटर पॉइंट्स में व्यक्त होते हैं (1 point = 1/72 inch)।

## पहली डेटा सीरीज़ तक पहुँचें

हर चार्ट में एक या अधिक `ChartSeries` होते हैं। पहली सीरीज़ इंडेक्स 0 पर होती है।

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*क्यों यह महत्वपूर्ण है*: `ChartSeries` ऑब्जेक्ट एक लाइन चार्ट में एक लाइन के Y‑मान, X‑मान और फ़ॉर्मेटिंग विकल्प रखता है। इस ऑब्जेक्ट को संशोधित करने से डेटा का दृश्य प्रतिनिधित्व बदलता है।

## सीरीज़ पर कस्टम नंबर फ़ॉर्मेट लागू करें

`FormatCode` प्रॉपर्टी यह नियंत्रित करती है कि संख्यात्मक मान कैसे दिखाए जाएँ। इसे `#,##0.00%` सेट करने से Word मानों को दो दशमलव स्थान के साथ प्रतिशत के रूप में दर्शाता है।

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*क्यों यह महत्वपूर्ण है*: कस्टम फ़ॉर्मेट के बिना, Word कच्चे दशमलव संख्याएँ दिखाता है (जैसे `0.15`)। फ़ॉर्मेट कोड उन्हें `15.00%` में बदल देता है, जो अक्सर व्यावसायिक रिपोर्टों की आवश्यकता होती है।

## दस्तावेज़ को सहेजें और परिणाम सत्यापित करें

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

जब आप Microsoft Word में `FormattedSeriesLineChart.docx` खोलते हैं, तो आपको एक लाइन चार्ट दिखाई देगा जहाँ Y‑अक्ष के लेबल `15.00%`, `30.00%`, `45.00%`, और `60.00%` पढ़ते हैं। चार्ट का आकार `InsertChart` में दिए गए आयामों से मेल खाता है।

### अपेक्षित आउटपुट स्क्रीनशॉट

> *छवि: एक Word दस्तावेज़ पृष्ठ जिसमें प्रतिशत‑फ़ॉर्मेटेड Y‑अक्ष मानों के साथ लाइन चार्ट दिखाया गया है।*  
> *(Alt text: एक Word दस्तावेज़ का स्क्रीनशॉट जिसमें प्रतिशत‑फ़ॉर्मेटेड Y‑अक्ष मानों के साथ लाइन चार्ट दिखाया गया है)*

## सामान्य विविधताएँ और किनारी मामलों

| स्थिति | समायोजन |
|-----------|------------|
| **एकाधिक सीरीज़** | `chart.Series` के माध्यम से लूप करें और प्रत्येक सीरीज़ के लिए `FormatCode` सेट करें। |
| **विभिन्न चार्ट प्रकार** | `ChartType.Line` को `ChartType.Column`, `ChartType.Pie` आदि से बदलें। |
| **स्थानीय‑विशिष्ट विभाजक** | `CultureInfo`‑सचेत फ़ॉर्मेट स्ट्रिंग्स का उपयोग करें, उदाहरण के लिए फ्रेंच स्थानीयकरण के लिए `"# ##0,00 %"`। |
| **डायनामिक डेटा स्रोत** | फ़ॉर्मेट लागू करने से पहले डेटाबेस या CSV फ़ाइल से `series.YValues` को भरें। |

**Pro tip:** हमेशा फ़ॉर्मेट **बाद में** लागू करें जब आपने Y‑मान जोड़ दिए हों। पहले फ़ॉर्मेट बदलना और फिर मान जोड़ना भी काम करता है, लेकिन बाद में लागू करने से सुनिश्चित होता है कि फ़ॉर्मेट अंतिम डेटा सेट पर लागू हो।

## सारांश

अब आप जानते हैं **how to format series** को C# का उपयोग करके Word लाइन चार्ट में कैसे फ़ॉर्मेट किया जाए। ट्यूटोरियल ने कवर किया:

* Word दस्तावेज़ बनाना (`create word document`)।  
* लाइन चार्ट डालना (`insert line chart`, `add chart to word`)।  
* चार्ट की पहली सीरीज़ तक पहुँचना।  
* कस्टम नंबर फ़ॉर्मेट (`apply custom number format`) लागू करना ताकि प्रतिशत दिखे।

## अगले कदम

* विभिन्न `ChartType` मानों के साथ प्रयोग करें ताकि देखें कि अन्य विज़ुअलाइज़ेशन कैसे व्यवहार करते हैं।  
* `chart.Title`, `chart.AxisX.Title`, और `chart.AxisY.Title` का उपयोग करके शीर्षक, एक्सिस लेबल, और लेजेंड जोड़ें।  
* चार्ट को इमेज (`chart.Save` के साथ `SaveFormat.Png`) के रूप में एक्सपोर्ट करें ताकि वेब रिपोर्टों में उपयोग किया जा सके।

इस पैटर्न को डैशबोर्ड, वित्तीय रिपोर्ट, या किसी भी दस्तावेज़ के लिए अनुकूलित करने में संकोच न करें जिसे प्रोग्रामेटिक चार्टिंग की आवश्यकता है। कोडिंग का आनंद लें!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं ताकि आप अतिरिक्त API फीचर्स में निपुण हो सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Aspose.Words for .NET का उपयोग करके Word में लाइन चार्ट बनाएं](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Word दस्तावेज़ में कॉलम चार्ट डालें](/words/english/net/programming-with-charts/insert-column-chart/)
- [Word दस्तावेज़ में एरिया चार्ट डालें | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}