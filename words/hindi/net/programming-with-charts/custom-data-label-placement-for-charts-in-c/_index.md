---
category: general
date: 2026-08-04
description: C# में चार्ट्स के लिए कस्टम डेटा‑लेबल प्लेसमेंट आपको चार्ट स्लाइस पर
  लेबल को केंद्रित करने की सुविधा देता है। Aspose.Words चार्ट API का उपयोग करके इस
  चरण‑दर‑चरण गाइड का पालन करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: hi
lastmod: 2026-08-04
og_description: C# में चार्ट्स के लिए कस्टम डेटा‑लेबल प्लेसमेंट आपको दिखाता है कि
  वर्ड चार्ट के प्रत्येक स्लाइस पर सभी डेटा लेबल को कैसे केंद्रित किया जाए। Aspose.Words
  के साथ चार्ट डेटा लेबल पोजिशनिंग में महारत हासिल करें।
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: C# में चार्ट्स के लिए कस्टम डेटा‑लेबल प्लेसमेंट – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: C# में चार्ट्स के लिए कस्टम डेटा‑लेबल प्लेसमेंट
url: /hi/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# में चार्ट्स के लिए कस्टम डेटा‑लेबल प्लेसमेंट

**Custom Data‑Label Placement for Charts** आपको Word दस्तावेज़ के भीतर चार्ट पर प्रत्येक लेबल के सटीक स्थान को नियंत्रित करने की सुविधा देता है। इस ट्यूटोरियल में आप सीखेंगे कि कैसे C# और Aspose.Words चार्ट API का उपयोग करके प्रत्येक स्लाइस पर सभी डेटा लेबल को केंद्रित किया जाए।

आपको एक पूर्ण, चलाने योग्य उदाहरण मिलेगा जो `.docx` फ़ाइल को लोड करता है, पहले चार्ट शेप तक पहुँचता है, प्रत्येक लेबल की `Position` को `Center` में बदलता है, और अपडेटेड दस्तावेज़ को सहेजता है। कोई बाहरी रेफ़रेंस आवश्यक नहीं—सिर्फ Aspose.Words for .NET लाइब्रेरी और एक बेसिक C# डेवलपमेंट एनवायरनमेंट।

**आप क्या सीखेंगे**

* वह Word दस्तावेज़ कैसे लोड करें जिसमें चार्ट हो।  
* Aspose.Words चार्ट API के साथ चार्ट शेप को कैसे खोजें।  
* चार्ट की प्रत्येक सीरीज़ में **डेटा लेबल पोजिशनिंग** कैसे लागू करें।  
* दस्तावेज़ को इस तरह सहेजें कि केंद्रित लेबल Word में दिखें।  

**पूर्वापेक्षाएँ**

* .NET 6.0 (या बाद का) स्थापित हो।  
* Visual Studio 2022 (या कोई भी C# IDE)।  
* `Aspose.Words` NuGet पैकेज का रेफ़रेंस।  
* एक Word फ़ाइल (`Chart.docx`) जिसमें कम से कम एक चार्ट हो।

---

## कस्टम डेटा‑लेबल प्लेसमेंट फॉर चार्ट्स – चरण 1: दस्तावेज़ लोड करना

पहला कदम वह Word फ़ाइल खोलना है जिसमें चार्ट मौजूद है। `Document` Aspose.Words के साथ किसी भी मैनिपुलेशन का एंट्री पॉइंट है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*इस चरण का महत्व*: दस्तावेज़ लोड किए बिना आप चार्ट ऑब्जेक्ट तक नहीं पहुँच सकते। वैधता सुनिश्चित करती है कि यदि फ़ाइल में चार्ट नहीं है तो आपको स्पष्ट त्रुटि मिले, जिससे बाद में null‑reference से बचा जा सके।

---

## Aspose.Words चार्ट API का उपयोग करके चार्ट शेप्स तक पहुँचना

Aspose.Words एक चार्ट को `Shape` के अंदर नेस्टेड `Chart` ऑब्जेक्ट के रूप में मानता है। आप इसे उपयुक्त चाइल्ड नोड को कास्ट करके प्राप्त करते हैं।

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*इस चरण का महत्व*: सीधे `Chart` तक पहुँचने से आपको सीरीज़, डेटा पॉइंट और लेबल प्रॉपर्टीज़ पर पूर्ण नियंत्रण मिलता है। यदि शेप चार्ट नहीं है, तो कोड प्रारंभिक रूप से एक सूचनात्मक संदेश के साथ समाप्त हो जाता है।

---

## C# में चार्ट डेटा लेबल पोजिशनिंग सेट करना

अब प्रत्येक सीरीज़ और प्रत्येक डेटा लेबल के माध्यम से इटररेट करें, `Position` को `Center` सेट करें। यह **Custom Data‑Label Placement for Charts** का मुख्य भाग है।

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**प्रो टिप**: यदि आपको अलग प्लेसमेंट चाहिए (जैसे कॉलम चार्ट के लिए `InsideEnd`), तो एनेम वैल्यू को उसी अनुसार बदलें। `ChartDataLabelPosition` एनेम Word द्वारा समर्थित सभी मानक पोजिशन को कवर करता है।

*इस चरण का महत्व*: `label.Position` को बदलने से अंतर्निहित OOXML प्रतिनिधित्व अपडेट होता है, इसलिए दस्तावेज़ Microsoft Word में खोलने पर लेबल केंद्रित दिखेगा।

---

## अपडेटेड लेबल्स के साथ Word दस्तावेज़ सहेजना

चार्ट में बदलाव करने के बाद, परिवर्तन को फ़ाइल में वापस लिखें। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई कॉपी बना सकते हैं।

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*इस चरण का महत्व*: सहेजने से अपडेटेड OOXML डिस्क पर लिख जाता है। `ChartLabelsCentered.docx` को Word में खोलने पर प्रत्येक स्लाइस लेबल केंद्रित दिखेगा, जिससे **Custom Data‑Label Placement for Charts** सफल हुआ यह पुष्टि होगी।

---

## एज केस और वैरिएशन

| स्थिति | कैसे निपटें |
|-----------|---------------|
| **एक ही दस्तावेज़ में कई चार्ट** | `doc.GetChildNodes(NodeType.Shape, true)` पर लूप करें और प्रत्येक शेप के लिए `shape.HasChart` जाँचें। |
| **विभिन्न चार्ट प्रकार** (pie, doughnut, bar) | `ChartDataLabelPosition.Center` पाई‑टाइप चार्ट्स के लिए काम करता है। बार/कॉलम चार्ट्स के लिए आप `InsideEnd` या `OutsideEnd` पसंद कर सकते हैं। |
| **लेबल टेक्स्ट को फॉर्मेट करना है** | `label.TextProperties` तक पहुँचकर फ़ॉन्ट साइज, रंग या बोल्डनेस सेट करें। |
| **.NET Core पर चलाना** | सुनिश्चित करें कि आप Aspose.Words का .NET Standard संस्करण रेफ़रेंस कर रहे हैं; API समान है। |

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कंसोल एप्लिकेशन में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी आवश्यक `using` निर्देश और एरर हैंडलिंग शामिल है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**अपेक्षित परिणाम**: `ChartLabelsCentered.docx` को Microsoft Word में खोलें। चार्ट की प्रत्येक स्लाइस अब अपना डेटा लेबल सीधे स्लाइस के केंद्र में दिखाएगी, जिससे दृश्य अधिक साफ़ दिखेगा।

---

## निष्कर्ष

अब आपके पास C# में **Custom Data‑Label Placement for Charts** का पूर्ण समाधान है। दस्तावेज़ लोड करके, Aspose.Words चार्ट API के माध्यम से चार्ट तक पहुँचकर, प्रत्येक लेबल के लिए `ChartDataLabelPosition.Center` सेट करके, और फ़ाइल को सहेजकर आप किसी भी Word‑आधारित चार्ट के लिए लेबल पोजिशनिंग को ऑटोमेट कर सकते हैं।

आगे, `InsideEnd` या `OutsideEnd` जैसे अन्य **chart data label positioning** विकल्पों को एक्सप्लोर करें, या **C# chart manipulation** के साथ रंग बदलना, लेजेंड जोड़ना, या शून्य से चार्ट जनरेट करना आज़माएँ। ये एक्सटेंशन यहाँ कवर की गई तकनीकों पर सीधे आधारित हैं और आपके Word दस्तावेज़ चार्ट ऑटोमेशन कौशल को विस्तारित करेंगे। Happy coding!

## अगला क्या सीखें?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकते हैं और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकते हैं।

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}