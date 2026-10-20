---
title: Aspose.Words for .NET का उपयोग करके Word में चार्ट शीर्षक अपडेट करें और लेजेंड की दृश्यता टॉगल करें
weight: 810
limit:
description: Aspose.Words for .NET के साथ Word दस्तावेज़ में चार्ट शीर्षक बदलना और लेजेंड की दृश्यता नियंत्रित करना सीखें।
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET के साथ Word दस्तावेज़ में चार्ट शीर्षक बदलना
    और लेजेंड की दृश्यता नियंत्रित करना सीखें।
  headline: Aspose.Words for .NET का उपयोग करके Word में चार्ट शीर्षक अपडेट करें और
    लेजेंड की दृश्यता टॉगल करें
  type: TechArticle
- description: Aspose.Words for .NET के साथ Word दस्तावेज़ में चार्ट शीर्षक बदलना
    और लेजेंड की दृश्यता नियंत्रित करना सीखें।
  name: Aspose.Words for .NET का उपयोग करके Word में चार्ट शीर्षक अपडेट करें और लेजेंड
    की दृश्यता टॉगल करें
  steps:
  - name: उपयोगकर्ता‑द्वारा प्रदान किया गया चार्ट शीर्षक और यह निर्धारित करें कि लेजेंड
      दिखाया जाना चाहिए या नहीं।
    text: उपयोगकर्ता‑द्वारा प्रदान किया गया चार्ट शीर्षक और यह निर्धारित करें कि लेजेंड
      दिखाया जाना चाहिए या नहीं।
  - name: एक नया Word दस्तावेज़ और सामग्री जोड़ने के लिए DocumentBuilder बनाएं।
    text: एक नया Word दस्तावेज़ और सामग्री जोड़ने के लिए DocumentBuilder बनाएं।
  - name: दस्तावेज़ में 432 × 252 pt आकार का कॉलम चार्ट सम्मिलित करें और सत्यापित
      करें कि शेप में वास्तव में एक चार्ट मौजूद है।
    text: दस्तावेज़ में 432 × 252 pt आकार का कॉलम चार्ट सम्मिलित करें और सत्यापित
      करें कि शेप में वास्तव में एक चार्ट मौजूद है।
  - name: चार्ट ऑब्जेक्ट प्राप्त करें, उसका शीर्षक टेक्स्ट उपयोगकर्ता के मान पर सेट
      करें, और सुनिश्चित करें कि शीर्षक प्रदर्शित हो।
    text: चार्ट ऑब्जेक्ट प्राप्त करें, उसका शीर्षक टेक्स्ट उपयोगकर्ता के मान पर सेट
      करें, और सुनिश्चित करें कि शीर्षक प्रदर्शित हो।
  - name: 'लेजेंड को कॉन्फ़िगर करें: यदि अनुरोध किया गया हो तो इसे दाएँ दिखाएँ, अन्यथा
      छिपाएँ, और इसे प्लॉट एरिया के ऊपर ओवरले करने की अनुमति दें।'
    text: 'लेजेंड को कॉन्फ़िगर करें: यदि अनुरोध किया गया हो तो इसे दाएँ दिखाएँ, अन्यथा
      छिपाएँ, और इसे प्लॉट एरिया के ऊपर ओवरले करने की अनुमति दें।'
  - name: संशोधित दस्तावेज़ को डिस्क पर CustomChart.docx के रूप में सहेजें।
    text: संशोधित दस्तावेज़ को डिस्क पर CustomChart.docx के रूप में सहेजें।
  type: HowTo
- questions:
  - answer: जब `displayLegend` `true` होता है, तो कोड `chartLegend.Position` को `LegendPosition.Right`
      सेट करता है, जिससे लेजेंड प्लॉट एरिया के दाएँ पक्ष पर दिखाई देता है; `Overlay`
      प्रॉपर्टी `true` ही रहती है, इसलिए लेजेंड चार्ट के ऊपर ओवरलैप करके स्थान बचा
      सकता है।
    question: '`displayLegend` को `true` सेट करने से उत्पन्न चार्ट में क्या परिवर्तन
      होता है?'
  - answer: '`chartTitle.Text` असाइन करने के बाद `chartTitle.Show = false` सेट करें
      (या बस `Show` को `true` सेट करना छोड़ दें); इससे शीर्षक Word दस्तावेज़ में रेंडर
      नहीं होगा।'
    question: यदि उपयोगकर्ता कोई शीर्षक प्रदान नहीं करता है तो मैं चार्ट शीर्षक को
      कैसे छिपा सकता हूँ?
  - answer: हाँ—`InsertChart` एक `Shape` लौटाता है जिसमें चार्ट होना चाहिए, लेकिन
      `HasChart` की जाँच करने से यह सुनिश्चित होता है कि शेप वास्तव में एक `Chart`
      ऑब्जेक्ट रखता है; अन्यथा कोड `InvalidOperationException` फेंकेगा।
    question: '`InsertChart` कॉल करने के बाद `chartContainer.HasChart` की जाँच करना
      आवश्यक है क्या?'
  - answer: बिल्कुल; `LegendPosition` एन्‍युम से कोई भी मान (जैसे `LegendPosition.Top`,
      `LegendPosition.Bottom`, `LegendPosition.Left`) `chartLegend.Position` को असाइन
      करके लेजेंड को आवश्यकतानुसार पुनः स्थित कर सकते हैं।
    question: क्या मैं लेजेंड को दाएँ पक्ष के अलावा किसी अन्य स्थान पर रख सकता हूँ?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Word में चार्ट शीर्षक और लेजेंड बदलें
og_description: Aspose.Words for .NET के साथ Word दस्तावेज़ में कस्टम चार्ट शीर्षक सेट करना और लेजेंड डिस्प्ले को नियंत्रित करना सीखें।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में चार्ट शीर्षक अपडेट करने और लेजेंड टॉगल करने वाला कोड दिखाने वाला गाइड
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word में चार्ट शीर्षक अपडेट करें और लेजेंड की दृश्यता टॉगल करें
यह ट्यूटोरियल दिखाता है कि Aspose.Words for .NET के साथ Word दस्तावेज़ के भीतर एक चार्ट को प्रोग्रामेटिक रूप से कैसे संशोधित किया जाए। आप सीखेंगे कि कॉलम चार्ट कैसे सम्मिलित करें, उसका शीर्षक उपयोगकर्ता द्वारा प्रदान किए गए टेक्स्ट से बदलें, और उपयोगकर्ता की प्राथमिकताओं के आधार पर लेजेंड की दृश्यता और ओवरले को नियंत्रित करें। ये कदम आपको मैन्युअल संपादन के बिना डायनामिक रूप से चार्ट प्रस्तुति को अनुकूलित करने की अनुमति देते हैं।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: `displayLegend` को `true` सेट करने से उत्पन्न चार्ट में क्या परिवर्तन होता है?**  
A: जब `displayLegend` `true` होता है, तो कोड `chartLegend.Position` को `LegendPosition.Right` सेट करता है, जिससे लेजेंड प्लॉट एरिया के दाएँ पक्ष पर दिखाई देता है; `Overlay` प्रॉपर्टी `true` ही रहती है, इसलिए लेजेंड चार्ट के ऊपर ओवरलैप करके स्थान बचा सकता है।

**Q: यदि उपयोगकर्ता कोई शीर्षक प्रदान नहीं करता है तो मैं चार्ट शीर्षक को कैसे छिपा सकता हूँ?**  
A: `chartTitle.Text` असाइन करने के बाद `chartTitle.Show = false` सेट करें (या बस `Show` को `true` सेट करना छोड़ दें); इससे शीर्षक Word दस्तावेज़ में रेंडर नहीं होगा।

**Q: `InsertChart` कॉल करने के बाद `chartContainer.HasChart` की जाँच करना आवश्यक है क्या?**  
A: हाँ—`InsertChart` एक `Shape` लौटाता है जिसमें चार्ट होना चाहिए, लेकिन `HasChart` की जाँच करने से यह सुनिश्चित होता है कि शेप वास्तव में एक `Chart` ऑब्जेक्ट रखता है; अन्यथा कोड `InvalidOperationException` फेंकेगा।

**Q: क्या मैं लेजेंड को दाएँ पक्ष के अलावा किसी अन्य स्थान पर रख सकता हूँ?**  
A: बिल्कुल; `LegendPosition` एन्‍युम से कोई भी मान (जैसे `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) `chartLegend.Position` को असाइन करके लेजेंड को आवश्यकतानुसार पुनः स्थित कर सकते हैं।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}