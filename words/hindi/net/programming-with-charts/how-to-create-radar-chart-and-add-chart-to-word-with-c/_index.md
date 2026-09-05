---
category: general
date: 2026-09-05
description: C# का उपयोग करके Word में रडार चार्ट बनाएं। एक खाली Word दस्तावेज़ बनाना,
  रडार चार्ट जोड़ना, चार्ट का आकार सेट करना और जल्दी से टिक मार्क्स सक्षम करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: hi
lastmod: 2026-09-05
og_description: C# का उपयोग करके Word में रडार चार्ट बनाएं। यह गाइड आपको दिखाता है
  कि कैसे एक खाली Word दस्तावेज़ बनाएं, रडार चार्ट जोड़ें, चार्ट का आकार सेट करें,
  और टिक मार्क्स सक्षम करें—सभी कुछ ही मिनटों में।
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Word में रडार चार्ट बनाएं – चरण‑दर‑चरण C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: C# के साथ रडार चार्ट कैसे बनाएं और चार्ट को Word में जोड़ें
url: /hi/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ रडार चार्ट कैसे बनाएं और Word में चार्ट जोड़ें

यदि आपको Word फ़ाइल के अंदर **रडार चार्ट बनाना** है, तो यह गाइड आपको पूरी प्रक्रिया के माध्यम से ले जाएगा। आप सीखेंगे कैसे **खाली Word दस्तावेज़ उत्पन्न करें**, रडार चार्ट डालें, **Word में चार्ट का आकार सेट करें**, और अक्ष ग्रेजुएशन सक्षम करें—सभी कुछ C# कोड की पंक्तियों के साथ।

रिपोर्ट में विज़ुअल डेटा जोड़ना एक सामान्य आवश्यकता है, और Aspose.Words का उपयोग इसे सरल बनाता है। नीचे दिए गए चरणों में हम यह भी कवर करते हैं कि कैसे **प्रोग्रामेटिक रूप से Word दस्तावेज़ों में चार्ट जोड़ें**, ताकि आप डैशबोर्ड, वित्तीय सारांश, या किसी भी डेटा‑ड्रिवन सामग्री को स्वचालित कर सकें।

## आवश्यकताएँ

* .NET 6.0 या बाद का संस्करण स्थापित हो  
* Aspose.Words for .NET लाइसेंस (या फ्री ट्रायल) – यह लाइब्रेरी इस ट्यूटोरियल में उपयोग किए गए `Document`, `DocumentBuilder`, और चार्ट API प्रदान करती है  
* Visual Studio 2022 (या कोई भी C# IDE)  

> **Pro tip:** यदि आप परीक्षण कर रहे हैं, तो Aspose.Words DLL को अपने प्रोजेक्ट के `bin` फ़ोल्डर में रखें और इसे NuGet के माध्यम से रेफ़रेंस करें (`Install-Package Aspose.Words`).

## Word दस्तावेज़ में रडार चार्ट कैसे बनाएं

पहला कदम **खाली Word दस्तावेज़ उत्पन्न करना** है जो चार्ट को होस्ट करेगा। यह आपको एक साफ़ कैनवास देता है और किसी भी सामग्री को जोड़ने से पहले दस्तावेज़ के मेटाडेटा को नियंत्रित करने की अनुमति देता है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*क्यों यह महत्वपूर्ण है:* एक खाली `Document` ऑब्जेक्ट यह सुनिश्चित करता है कि कोई छिपी हुई स्टाइल या सेक्शन चार्ट लेआउट में बाधा न डालें। यह आपको बाद में दस्तावेज़ गुण (लेखक, शीर्षक) सेट करने की भी अनुमति देता है यदि आवश्यक हो।

## Aspose.Words का उपयोग करके Word में चार्ट कैसे जोड़ें

अगला, एक `DocumentBuilder` बनाएं। बिल्डर वह मुख्य उपकरण है जो आपको दस्तावेज़ में टेक्स्ट, इमेज और चार्ट सम्मिलित करने देता है।

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

अब आप सीधे कर्सर की स्थिति पर **रडार चार्ट जोड़ सकते हैं**। `InsertChart` मेथड एक `ChartType` एन्नुम, चौड़ाई, और ऊँचाई (पॉइंट्स में) स्वीकार करता है।

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*क्यों 400 × 300?* ये आयाम एक मानक A4 पेज पर स्पष्ट, पढ़ने योग्य चार्ट प्रदान करते हैं। यदि आपके लेआउट को अलग अनुपात चाहिए तो आप बाद में **Word में चार्ट का आकार सेट करें** चरण के साथ आकार समायोजित कर सकते हैं।

## Word में चार्ट का आकार सेट करना

यदि आपको सम्मिलन के बाद आकार को बारीकी से समायोजित करने की आवश्यकता है, तो आप चार्ट के `Width` और `Height` प्रॉपर्टीज़ को संशोधित कर सकते हैं। यह तब उपयोगी होता है जब आसपास का टेक्स्ट या पेज मार्जिन अलग दृश्य संतुलन निर्धारित करता है।

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Note:** `InsertChart` ओवरलोड पहले से ही आकार सेट करता है, इसलिए ऊपर दिया गया कोड वैकल्पिक है और पूर्णता के लिए दिखाया गया है।

## रेडियल एक्सिस पर टिक मार्क्स सक्षम करें

एक रडार चार्ट सबसे उपयोगी तब होता है जब रेडियल एक्सिस स्पष्ट ग्रेजुएशन दिखाता है। निम्न सेटिंग्स टिक मार्क्स को चालू करती हैं और अंतराल को 30 डिग्री पर सेट करती हैं, जो सामान्य कंपास‑स्टाइल रडार डिस्प्ले के अनुरूप है।

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*क्यों यह महत्वपूर्ण है:* ग्रेजुएशन पाठकों को प्रत्येक कोण पर मानों का अनुमान लगाने में मदद करते हैं, जिससे उन स्टेकहोल्डर्स के लिए पठनीयता बढ़ती है जो डेटा से परिचित नहीं हैं।

## चार्ट वाले दस्तावेज़ को सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। आप कोई भी फ़ोल्डर चुन सकते हैं; बस यह सुनिश्चित करें कि पाथ मौजूद हो।

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

जब आप Microsoft Word में `RadialChart.docx` खोलेंगे, तो आपको पेज के केंद्र में पूरी तरह से रेंडर किया गया रडार चार्ट दिखेगा, जैसा कि निर्दिष्ट आकार में है, और हर 30 डिग्री पर टिक मार्क्स होंगे।

### अपेक्षित आउटपुट

* `.docx` फ़ाइल जिसका नाम **RadialChart.docx** है  
* पहला पेज 400 × 300 पॉइंट्स आकार के रडार चार्ट को शामिल करता है  
* X‑axis (radial axis) पर 0°, 30°, 60°, …, 330° पर टिक मार्क्स दिखते हैं  

अब आप `radarChart.Series` तक पहुंच कर प्लेसहोल्डर डेटा सीरीज़ को अपने मानों से बदल सकते हैं – लेकिन यह इस बुनियादी **add radar chart** ट्यूटोरियल के दायरे से बाहर है।

## सामान्य विविधताएँ और किनारे के मामले

| Scenario | Adjustment |
|----------|------------|
| **विभिन्न चार्ट प्रकार** | Replace `ChartType.Radar` को `ChartType.Column`, `ChartType.Pie`, आदि से बदलें। |
| **एकाधिक चार्ट** | `InsertChart` को बार‑बार कॉल करें; प्रत्येक कॉल नया चार्ट पिछले वाले के बाद स्थित करता है। |
| **बड़े डेटा सेट** | बहुत सारे पॉइंट्स भरने के लिए `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` का उपयोग करें। |
| **PDF के रूप में सहेजना** | चार्ट जोड़ने के बाद `document.Save("RadialChart.pdf", SaveFormat.Pdf);` कॉल करें। |
| **.NET Core पर चलाना** | सुनिश्चित करें कि आप `Aspose.Words.NETCore` पैकेज को रेफ़रेंस करें; API उपयोग समान है। |

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी‑पेस्ट करके एक कंसोल एप्लिकेशन में उपयोग कर सकते हैं। इसमें सभी चरण, वैकल्पिक आकार समायोजन, और स्पष्टता के लिए टिप्पणियाँ शामिल हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

प्रोग्राम चलाएँ, उत्पन्न फ़ाइल खोलें, और आप रडार चार्ट को ठीक वैसा ही देखेंगे जैसा वर्णित है।

## निष्कर्ष

अब आप जानते हैं कि C# का उपयोग करके **रडार चार्ट कैसे बनाएं** और **Word दस्तावेज़ों में चार्ट कैसे जोड़ें**। ट्यूटोरियल ने **खाली Word दस्तावेज़** उत्पन्न करने, रडार चार्ट डालने, **Word में चार्ट का आकार सेट करने**, और अक्ष ग्रेजुएशन सक्षम करने को कवर किया। इस आधार के साथ आप समाधान को कई चार्ट, कस्टम डेटा सीरीज़, या PDF में निर्यात करने तक विस्तारित कर सकते हैं।

### अगले कदम

* `ChartType` के साथ अन्य चार्ट प्रकारों का अन्वेषण करें (जैसे, `Bar`, `Line`) – संबंधित उदाहरणों के लिए **add radar chart** कीवर्ड देखें।

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Word दस्तावेज़ में स्कैटर चार्ट डालें](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Aspose.Words for .NET का उपयोग करके Word में कॉलम चार्ट डालें](/words/english/net/working-with-charts/insert-column-chart/)
- [Word दस्तावेज़ में चार्ट एक्सिस छुपाएँ](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}