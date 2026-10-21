---
category: general
date: 2026-10-13
description: C# का उपयोग करके Word दस्तावेज़ में चार्ट लेबल को प्रोग्रामेटिकली समायोजित
  करना सीखें। यह गाइड Aspose.Words चार्ट मैनिपुलेशन और लेबल एलाइनमेंट को कवर करता
  है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: hi
lastmod: 2026-10-13
og_description: C# का उपयोग करके Word दस्तावेज़ में चार्ट लेबल्स को प्रोग्रामेटिकली
  समायोजित करें। लेबल की स्थिति, संरेखण और अन्य चीज़ों को बदलने के लिए इस पूर्ण ट्यूटोरियल
  का पालन करें।
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: वर्ड में चार्ट लेबल्स को प्रोग्रामेटिकली समायोजित करें – C# चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: C# के साथ Word दस्तावेज़ में चार्ट लेबल्स को प्रोग्रामेटिकली समायोजित करें
url: /hi/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# के साथ Word दस्तावेज़ में चार्ट लेबल को प्रोग्रामेटिकली समायोजित करें

यदि आपको Word दस्तावेज़ में **चार्ट लेबल को प्रोग्रामेटिकली समायोजित** करने की आवश्यकता है, तो यह गाइड आपको C# के साथ इसे बिल्कुल कैसे करना है दिखाता है। चाहे आप रिपोर्ट बना रहे हों, डैशबोर्ड को स्वचालित कर रहे हों, या टेम्प्लेट को कस्टमाइज़ कर रहे हों, आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो .docx फ़ाइल के भीतर एक चार्ट के लेबल प्लेसमेंट और अलाइनमेंट को बदलता है।

आप यह भी सीखेंगे कि **Aspose.Words चार्ट मैनिपुलेशन** तकनीकों का उपयोग कैसे करें, कई सीरीज़ को संभालें, और **C# चार्ट डेटा लेबल** ऑब्जेक्ट्स के साथ काम करते समय सामान्य समस्याओं से कैसे बचें।

## पूर्वापेक्षाएँ

* .NET 6.0 (या बाद का) स्थापित हो  
* Visual Studio 2022 (या कोई भी C# IDE)  
* The **Aspose.Words for .NET** NuGet पैकेज (`Install-Package Aspose.Words`)  
* एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक चार्ट हो  

ये आइटम्स **Word दस्तावेज़ चार्ट उदाहरण** को संशोधित करने के लिए आवश्यक हैं।

## चरण 1: प्रोजेक्ट सेट अप करें और नेमस्पेस इम्पोर्ट करें

एक नया कंसोल प्रोजेक्ट बनाएं और आवश्यक `using` निर्देश जोड़ें। यह **चार्ट लेबल को प्रोग्रामेटिकली समायोजित** करने के लिए वातावरण तैयार करता है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*इस चरण का कारण?*  
डॉक्यूमेंट लोड करने से आपको आंतरिक **Word दस्तावेज़ चार्ट उदाहरण** ट्री तक पहुंच मिलती है, जहाँ चार्ट को shape नोड्स के रूप में संग्रहीत किया जाता है।

## चरण 2: पहला चार्ट शेप खोजें

चार्ट को `Shape` नोड्स के रूप में संग्रहीत किया जाता है। नीचे दिया गया कोड दस्तावेज़ में पहला चार्ट प्राप्त करता है, जो हमारे लेबल समायोजन का लक्ष्य है।

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*इस चरण का कारण?*  
`GetChild` मेथड पुनरावर्ती रूप से (`true`) खोज करता है और `Shape` प्रकार का पहला नोड लौटाता है। `Chart` में कास्ट करने से हम चार्ट‑विशिष्ट API के साथ काम कर सकते हैं।

## चरण 3: वह डेटा लेबल एक्सेस करें जिसे आप संशोधित करना चाहते हैं

एक चार्ट में प्रत्येक सीरीज़ के पास डेटा लेबल्स का एक संग्रह होता है। एक साधारण चार्ट के लिए, पहला लेबल अक्सर पर्याप्त होता है। नीचे दिया गया कोड दिखाता है कि इसे कैसे पहुंचा जाए।

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*इस चरण का कारण?*  
`ChartSeries` बिंदुओं की एक श्रृंखला को दर्शाता है। `DataLabelCollection` उस श्रृंखला के लेबल्स को रखता है, जिससे प्लेसमेंट और अलाइनमेंट पर सटीक नियंत्रण मिलता है।

## चरण 4: लेबल प्लेसमेंट और अलाइनमेंट बदलें

अब हम **चार्ट लेबल को प्रोग्रामेटिकली समायोजित** करते हैं, पोजीशन, हॉरिज़ॉन्टल अलाइनमेंट, और वर्टिकल अलाइनमेंट सेट करके। ये प्रॉपर्टीज़ Word UI में दिखने वाले विकल्पों के अनुरूप हैं।

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*इन सेटिंग्स का कारण?*  

* `OutsideEnd` लेबल को प्रत्येक बार या कॉलम के अंत के ठीक बाहर रखता है, जिससे पठनीयता बढ़ती है।  
* `HorizontalAlignment.Center` टेक्स्ट को बिंदु के ऊपर केंद्रित रखता है, जबकि `VerticalAlignment.Top` लेबल के शीर्ष किनारे को डेटा पॉइंट के साथ संरेखित करता है, जिससे अन्य तत्वों के साथ ओवरलैप नहीं होता।

### प्रो टिप
यदि किसी चार्ट में कई सीरीज़ हैं, तो `chart.Series` पर लूप करें और प्रत्येक `DataLabelCollection` पर समान सेटिंग्स लागू करें। इससे पूरे चार्ट में एक समान लुक सुनिश्चित होता है।

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## चरण 5: संशोधित दस्तावेज़ को सहेजें

लेबल्स को समायोजित करने के बाद, बदलावों को नई फ़ाइल में सहेजें। यह **चार्ट लेबल पोजीशन संशोधित** प्रक्रिया को पूरा करता है।

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

जब आप `output.docx` खोलेंगे, तो आप देखेंगे कि प्रत्येक चार्ट लेबल अपने डेटा पॉइंट के बाहर अंत में चला गया है, हॉरिज़ॉन्टली केंद्रित और वर्टिकली टॉप पर अलाइन किया गया है।

## किनारे के मामलों और विविधताएँ

| स्थिति | ध्यान देने योग्य बातें | सिफारिश किया गया तरीका |
|-----------|-------------------|----------------------|
| **Multiple charts** एक ही दस्तावेज़ में | `GetChild` केवल पहला चार्ट लौटाता है। | सभी चार्ट शेप्स पर इटरेट करने के लिए `doc.GetChildNodes(NodeType.Shape, true)` का उपयोग करें। |
| **Series without data labels** | `DataLabelCollection` खाली हो सकता है। | कलेक्शन एक्सेस करने से पहले `series.HasDataLabels` जांचें। |
| **Different chart types** (pie, line, scatter) | सभी `DataLabelPosition` मान वैध नहीं होते। | ऐसे चार्ट्स के लिए `DataLabelPosition.Auto` का उपयोग करें जो स्वचालित रूप से सबसे अच्छा प्लेसमेंट तय करते हैं। |
| **Localization** | अलाइनमेंट कॉन्स्टेंट्स भाषा‑निर्पेक्ष हैं, लेकिन रेंडर किया गया टेक्स्ट RTL समर्थन की आवश्यकता हो सकती है। | यदि आपको RTL भाषाओं की आवश्यकता है तो `dataLabel.TextDirection` सेट करें। |

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप कॉपी, पेस्ट और रन कर सकते हैं। `YOUR_DIRECTORY` को वास्तविक फ़ोल्डर पाथ से बदलें।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**अपेक्षित परिणाम:** `output.docx` खोलने पर प्रत्येक चार्ट लेबल डेटा पॉइंट के बाहर स्थित, हॉरिज़ॉन्टली केंद्रित और टॉप पर अलाइन दिखता है—बिल्कुल वही प्रभाव जो आपने **चार्ट लेबल को प्रोग्रामेटिकली समायोजित** किया था।

## निष्कर्ष

अब आप जानते हैं कि C# का उपयोग करके Word दस्तावेज़ में **चार्ट लेबल को प्रोग्रामेटिकली समायोजित** कैसे किया जाता है। ट्यूटोरियल ने कवर किया:

* **Aspose.Words चार्ट मैनिपुलेशन** के साथ दस्तावेज़ लोड करना  
* **C# चार्ट डेटा लेबल** तक पहुँच  
* **modify chart label position** और अलाइनमेंट बदलना  
* फ़ाइल को सहेजना और सामान्य किनारे के मामलों को संभालना  

अब आप अधिक उन्नत परिदृश्यों का अन्वेषण कर सकते हैं, जैसे लेबल फ़ॉन्ट को कस्टमाइज़ करना, कंडीशनल फॉर्मेटिंग जोड़ना, या बैच प्रोसेस में कई चार्ट्स को अपडेट करना। विभिन्न `DataLabelPosition` विकल्पों के साथ प्रयोग करें ताकि वह शैली मिल सके जो आपके रिपोर्ट्स के लिए सबसे उपयुक्त हो।

*क्या आप अपने ऑटोमेटेड रिपोर्टिंग पाइपलाइन को बेहतर बनाना चाहते हैं? लेबल्स में कस्टम नंबर फ़ॉर्मेट जोड़ने या चार्ट को इमेज के रूप में एक्सपोर्ट करके PDFs में उपयोग करने की कोशिश करें।*

## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर करने में मदद करेंगे।

- [Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में समान डेटा लेबल सेट करें](/words/english/net/programming-with-charts/uniform-data-labels/)
- [चार्ट में डेटा लेबल के लिए डिफ़ॉल्ट विकल्प सेट करें](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में चार्ट सीरीज़ डेटा अपडेट करें](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}