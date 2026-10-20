---
category: general
date: 2026-10-20
description: Aspose.Words का उपयोग करके Word दस्तावेज़ में पाई चार्ट बनाएं – चरण‑दर‑चरण
  गाइड जो दिखाता है कि रंग कैसे सेट करें, स्लाइस को एक्सप्लोड करें, और Word दस्तावेज़
  को सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: hi
lastmod: 2026-10-20
og_description: Aspose.Words के साथ Word दस्तावेज़ में पाई चार्ट बनाएं। रंग सेट करना,
  स्लाइस को एक्सप्लोड करना, और एक ही चलाने योग्य उदाहरण में Word दस्तावेज़ को सहेजना
  सीखें।
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Word दस्तावेज़ में पाई चार्ट बनाएं – पूर्ण C# गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Aspose.Words के साथ Word दस्तावेज़ में पाई चार्ट कैसे बनाएं
url: /hi/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ Word दस्तावेज़ में पाई चार्ट कैसे बनाएं

यदि आपको Word फ़ाइल के अंदर **पाई चार्ट बनाना** है, तो यह गाइड आपको ठीक‑ठीक बताता है कि कैसे करना है। आप देखेंगे कि कैसे कस्टम रंग सेट किया जाए, ज़ोर देने के लिए स्लाइस को एक्सप्लोड किया जाए, और अंत में **Word दस्तावेज़ को सहेजा** जाए जिसमें चार्ट एम्बेड हो।

प्रोग्रामेटिक रूप से चार्ट बनाना Word खोलने, चार्ट डालने और उसकी उपस्थिति को मैन्युअली समायोजित करने वाले चरणों को समाप्त कर देता है। इस ट्यूटोरियल के अंत तक आपके पास एक पूर्ण, चलने योग्य C# कंसोल एप्लिकेशन होगा जो पाई चार्ट बनाता है, उसे कस्टमाइज़ करता है, और परिणाम को डिस्क पर लिखता है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* .NET 6.0 SDK या बाद का संस्करण स्थापित  
* एक वैध Aspose.Words for .NET लाइसेंस (या एक मुफ्त इवैल्यूएशन की)  
* Visual Studio 2022 या VS Code जैसे IDE  

`Aspose.Words` के अलावा कोई अतिरिक्त NuGet पैकेज आवश्यक नहीं है।

## Word दस्तावेज़ में पाई चार्ट कैसे बनाएं

पहला कदम `Document` और `DocumentBuilder` को इंस्टैंशिएट करना है। बिल्डर आपको हाई‑लेवल Word फीचर्स तक पहुँच देता है, जिसमें चार्ट इन्सर्शन भी शामिल है।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

इस बिंदु पर दस्तावेज़ में पहले से ही एक बेसिक पाई चार्ट मौजूद है। अगले सेक्शन में **स्लाइस को एक्सप्लोड कैसे करें**, **रंग कैसे सेट करें**, और **Word दस्तावेज़ को कैसे सहेजें** बताया गया है।

## ज़ोर देने के लिए स्लाइस को एक्सप्लोड कैसे करें

एक स्लाइस को एक्सप्लोड करने से वह पाई के बाकी हिस्सों से अलग हो जाता है, जिससे पाठक का ध्यान उस पर जाता है। Aspose.Words API आपको पॉइंट्स में एक्सप्लोजन दूरी निर्दिष्ट करने की अनुमति देता है।

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

स्लाइस को क्यों एक्सप्लोड करें? उन रिपोर्टों में जो किसी विशेष श्रेणी—जैसे “सबसे अधिक बिकने वाला प्रोडक्ट”—को उजागर करती हैं, दृश्य विभाजन डेटा पॉइंट को तुरंत पहचानने योग्य बनाता है।

## चार्ट स्लाइस पर रंग कैसे सेट करें

कस्टम रंग ब्रांड संगति और पठनीयता को बढ़ाते हैं। आप किसी भी `System.Drawing.Color` को एक विशिष्ट डेटा पॉइंट पर असाइन कर सकते हैं।

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

आप केवल प्री‑डिफाइंड रंगों तक सीमित नहीं हैं; आप सटीक शेड्स के लिए `Color.FromArgb` वैल्यू बना सकते हैं।

## चार्ट के साथ Word दस्तावेज़ कैसे सहेजें

एक बार चार्ट आपकी इच्छानुसार दिखने लगे, फ़ाइल को सहेजना सीधा है। `Document.Save` मेथड उस फॉर्मेट में दस्तावेज़ लिखता है जिसे आप निर्दिष्ट करते हैं—यहाँ हम डिफ़ॉल्ट `.docx` का उपयोग कर रहे हैं।

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

प्रोग्राम चलाने पर `PieChart.docx` बनता है। Microsoft Word में फ़ाइल खोलने पर एक पाई चार्ट दिखेगा जहाँ पहली स्लाइस एक्सप्लोड की गई है और लाल रंग से भरी हुई है, बिल्कुल कोड में निर्दिष्ट अनुसार।

### अपेक्षित परिणाम

* `C:\Temp` में **PieChart.docx** नामक Word फ़ाइल।  
* दस्तावेज़ में एक ही पाई चार्ट है, जिसका आकार 400 × 300 पॉइंट्स है।  
* स्लाइस 0 को 20 पॉइंट्स से ऑफ़सेट किया गया है और लाल रंग से भरा गया है, जबकि अन्य स्लाइस डिफ़ॉल्ट रंग रखते हैं।  

आप Word में चार्ट का चयन करके और स्लाइस प्रॉपर्टीज़ की जांच करके एक्सप्लोजन और रंग की पुष्टि कर सकते हैं।

## प्रो टिप्स और सामान्य गलतियां

* **प्रो टिप:** यदि आपको चार्ट शीर्षक या लेजेंड बदलना है, तो सहेजने से पहले `pieChart.Title.Text` और `pieChart.Legend` प्रॉपर्टीज़ का उपयोग करें।  
* **सावधान रहें:** डिफ़ॉल्ट डेटा पॉइंट्स को साफ़ करना भूलने से अतिरिक्त, अनचाहे स्लाइस बन सकते हैं। अपना डेटा जोड़ने से पहले हमेशा `Series[0].DataPoints.Clear()` कॉल करें।  
* **परफ़ॉर्मेंस टिप:** बड़े दस्तावेज़ों के लिए, कई बिल्डर बनाने के बजाय एक ही `DocumentBuilder` इंस्टेंस को पुन: उपयोग करें; इससे मेमोरी ओवरहेड कम होता है।

## Aspose.Words का उपयोग करके चार्ट कैसे बनाएं (अतिरिक्त संदर्भ)

`InsertChart` मेथड पाई चार्ट के अलावा कई चार्ट प्रकारों का समर्थन करता है, जैसे कॉलम, लाइन, और एरिया चार्ट। किसी अलग प्रकार पर स्विच करने के लिए `ChartType.Pie` को इच्छित enum वैल्यू, उदाहरण के लिए `ChartType.Column`, से बदलें। कस्टमाइज़ेशन के बाकी चरण (स्लाइस एक्सप्लोड करना, रंग सेट करना) समान पैटर्न का पालन करते हैं, हालांकि सभी चार्ट प्रकार “एक्सप्लोजन” प्रॉपर्टी नहीं दिखाते।

## अन्य चार्ट प्रकारों में स्लाइस को एक्सप्लोड कैसे करें

केवल पाई‑टाइप चार्ट `SetExplosion` मेथड को एक्सपोज़ करते हैं। यदि आप इसे बार चार्ट पर कॉल करने की कोशिश करते हैं, तो API `ArgumentException` फेंकेगा। ऐसे मामलों में, किसी विशेष बार को उजागर करने के लिए डेटा लेबल या कॉलआउट का उपयोग करने पर विचार करें।

## एकल स्लाइस के बजाय पूरी सीरीज़ पर रंग कैसे सेट करें

यदि आप चाहते हैं कि सीरीज़ की हर स्लाइस एक ही रंग साझा करे, तो डेटा पॉइंट्स पर लूप करें:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

यह तरीका तब उपयोगी होता है जब आपको कई चार्ट्स में एक समान रंग योजना चाहिए।

## Word दस्तावेज़ को अन्य फ़ॉर्मैट में कैसे सहेजें

Aspose.Words PDF, HTML, और कई अन्य फ़ॉर्मैट में एक्सपोर्ट कर सकता है। `Save` में फ़ाइल एक्सटेंशन बदलें और वैकल्पिक रूप से एक `SaveOptions` ऑब्जेक्ट पास करें:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

चार्ट रेंडरिंग इंजन स्वचालित रूप से चार्ट को लक्ष्य फ़ॉर्मैट में बदल देता है, रंग और एक्सप्लोजन सेटिंग्स को संरक्षित रखते हुए।

## निष्कर्ष

अब आप जानते हैं कि **Word दस्तावेज़ में पाई चार्ट कैसे बनाएं**, उसकी उपस्थिति को **स्लाइस को एक्सप्लोड** करके और **रंग सेट** करके कस्टमाइज़ करें, और अंत में **चार्ट एम्बेडेड Word दस्तावेज़ को सहेजें**। यह एंड‑टू‑एंड उदाहरण आपको रिपोर्ट जनरेशन, डैशबोर्ड, या किसी भी ऐसे परिदृश्य के लिए एक ठोस आधार देता है जहाँ विज़ुअल डेटा को प्रोग्रामेटिक रूप से इन्सर्ट करने की आवश्यकता होती है।

### अगले कदम

* अन्य चार्ट प्रकारों (`ChartType.Column`, `ChartType.Line`) का अन्वेषण करें ताकि आपका रिपोर्टिंग टूलकिट विस्तृत हो।  
* एक ही दस्तावेज़ में कई चार्ट जोड़ें ताकि व्यापक डैशबोर्ड बनाए जा सकें।  
* `ChartDataLabel` के साथ प्रयोग करें ताकि प्रतिशत या मान सीधे स्लाइस पर दिखाए जा सकें।  

कोड को अपने डेटा स्रोतों के अनुसार अनुकूलित करने में संकोच न करें—चाहे आप डेटाबेस, API, या CSV फ़ाइल से मान निकालें, वही Aspose.Words वर्कफ़्लो लागू होता है। चार्टिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [C# में Aspose.Words के साथ पाई चार्ट स्लाइस को एक्सप्लोड करें – पूर्ण गाइड](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम कॉलम चार्ट डालें](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में चार्ट सीरीज़ डेटा अपडेट करें](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}