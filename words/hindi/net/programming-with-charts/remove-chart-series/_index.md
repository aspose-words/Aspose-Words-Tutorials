---
title: Aspose.Words for .NET का उपयोग करके Word Document से एक Chart Series हटाएँ
weight: 510
limit:
description: Aspose.Words for .NET के साथ Word दस्तावेज़ में एक कॉलम चार्ट से विशिष्ट डेटा सीरीज़ को हटाना सीखें।
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET के साथ Word दस्तावेज़ में एक कॉलम चार्ट से विशिष्ट
    डेटा सीरीज़ को हटाना सीखें।
  headline: Aspose.Words for .NET का उपयोग करके Word Document से एक Chart Series हटाएँ
  type: TechArticle
- description: Aspose.Words for .NET के साथ Word दस्तावेज़ में एक कॉलम चार्ट से विशिष्ट
    डेटा सीरीज़ को हटाना सीखें।
  name: Aspose.Words for .NET का उपयोग करके Word Document से एक Chart Series हटाएँ
  steps:
  - name: एक नया Word Document बनाएं और उससे जुड़ा एक DocumentBuilder बनाएं।
    text: एक नया Word Document बनाएं और उससे जुड़ा एक DocumentBuilder बनाएं।
  - name: 432×252 पॉइंट्स आकार का एक कॉलम चार्ट सम्मिलित करें और आगे की हेरफेर के
      लिए Chart ऑब्जेक्ट प्राप्त करें।
    text: 432×252 पॉइंट्स आकार का एक कॉलम चार्ट सम्मिलित करें और आगे की हेरफेर के
      लिए Chart ऑब्जेक्ट प्राप्त करें।
  - name: हटाई जाने वाली सीरीज़ का शून्य‑आधारित इंडेक्स निर्धारित करें (दूसरी सीरीज़)।
    text: हटाई जाने वाली सीरीज़ का शून्य‑आधारित इंडेक्स निर्धारित करें (दूसरी सीरीज़)।
  - name: यदि इंडेक्स वैध है, तो चार्ट की Series कलेक्शन पर RemoveAt कॉल करके उस सीरीज़
      को हटाएँ।
    text: यदि इंडेक्स वैध है, तो चार्ट की Series कलेक्शन पर RemoveAt कॉल करके उस सीरीज़
      को हटाएँ।
  - name: अपडेटेड दस्तावेज़ को .docx फ़ाइल में सहेजें।
    text: अपडेटेड दस्तावेज़ को .docx फ़ाइल में सहेजें।
  type: HowTo
- questions:
  - answer: '`if` जांच (`targetSeriesIdx < columnChart.Series.Count`) विफल होगी, इसलिए
      `RemoveAt` कभी कॉल नहीं होगा और चार्ट अपरिवर्तित रहेगा।'
    question: यदि मैं चार्ट में सीरीज़ की संख्या के बराबर इंडेक्स पास करता हूँ तो
      क्या होता है?
  - answer: हाँ, `columnChart.Series.RemoveAt` के बाद लेजेंड को पुनः उत्पन्न किया
      जाता है ताकि शेष सीरीज़ को दर्शाया जा सके, इसलिए हटाई गई प्रविष्टि लेजेंड से
      गायब हो जाती है।
    question: क्या सीरीज़ हटाने से चार्ट लेजेंड स्वचालित रूप से अपडेट हो जाता है?
  - answer: कोड किसी भी चार्ट प्रकार के लिए काम करता है जो `Series` कलेक्शन को सपोर्ट
      करता है; बस चार्ट सम्मिलित करते समय `ChartType.Column` को इच्छित प्रकार में
      बदल दें।
    question: क्या मैं वही कोड लाइन या पाई चार्ट से सीरीज़ हटाने के लिए उपयोग कर सकता
      हूँ?
  - answer: शून्य सीरीज़ वाला चार्ट अभी भी एक वैध `Shape` है और सहेजा जाएगा, लेकिन
      परिणामी दस्तावेज़ में यह खाली दिखाई देगा।
    question: यदि मैं चार्ट में केवल एक ही सीरीज़ हटाता हूँ, तो क्या चार्ट अभी भी
      सही ढंग से सहेजा जाएगा?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Word दस्तावेज़ में एक Chart Series हटाएँ
og_description: Aspose.Words for .NET का उपयोग करके Word चार्ट से डेटा सीरीज़ हटाने के लिए चरण‑दर‑चरण गाइड।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कॉलम चार्ट से विशिष्ट डेटा सीरीज़ को हटाने का तरीका दर्शाने वाला गाइड।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word Document से एक Chart Series हटाएँ
यह ट्यूटोरियल दिखाता है कि कैसे एक Word दस्तावेज़ बनाएं, DocumentBuilder से एक कॉलम चार्ट जोड़ें, और फिर ChartSeriesCollection.RemoveAt मेथड का उपयोग करके उस चार्ट से एक विशिष्ट डेटा सीरीज़ हटाएँ। अंत में आपके पास एक सहेजा हुआ दस्तावेज़ होगा जिसमें अनचाही सीरीज़ हटाई गई होगी, जिससे आपको .NET कोड से सीधे चार्ट सामग्री पर सटीक नियंत्रण मिलेगा।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: यदि मैं चार्ट में सीरीज़ की संख्या के बराबर इंडेक्स पास करता हूँ तो क्या होता है?**  
A: `if` जांच (`targetSeriesIdx < columnChart.Series.Count`) विफल होगी, इसलिए `RemoveAt` कभी कॉल नहीं होगा और चार्ट अपरिवर्तित रहेगा।

**Q: क्या सीरीज़ हटाने से चार्ट लेजेंड स्वचालित रूप से अपडेट हो जाता है?**  
A: हाँ, `columnChart.Series.RemoveAt` के बाद लेजेंड को पुनः उत्पन्न किया जाता है ताकि शेष सीरीज़ को दर्शाया जा सके, इसलिए हटाई गई प्रविष्टि लेजेंड से गायब हो जाती है।

**Q: क्या मैं वही कोड लाइन या पाई चार्ट से सीरीज़ हटाने के लिए उपयोग कर सकता हूँ?**  
A: कोड किसी भी चार्ट प्रकार के लिए काम करता है जो `Series` कलेक्शन को सपोर्ट करता है; बस चार्ट सम्मिलित करते समय `ChartType.Column` को इच्छित प्रकार में बदल दें।

**Q: यदि मैं चार्ट में केवल एक ही सीरीज़ हटाता हूँ, तो क्या चार्ट अभी भी सही ढंग से सहेजा जाएगा?**  
A: शून्य सीरीज़ वाला चार्ट अभी भी एक वैध `Shape` है और सहेजा जाएगा, लेकिन परिणामी दस्तावेज़ में यह खाली दिखाई देगा।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}