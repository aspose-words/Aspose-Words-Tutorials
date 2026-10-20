---
title: Aspose.Words for .NET का उपयोग करके Word लाइन चार्ट्स में सेकेंडरी X‑अक्ष को फ़ॉर्मेट करें और डिस्प्ले यूनिट को हजारों पर सेट करें।
weight: 710
limit:
description: Aspose.Words for .NET का उपयोग करके एक Word लाइन चार्ट बनाएं, सेकेंडरी X‑अक्ष जोड़ें, उसकी डिस्प्ले यूनिट को हजारों पर सेट करें, और कस्टम न्यूमेरिक फ़ॉर्मेट लागू करें।
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET का उपयोग करके एक Word लाइन चार्ट बनाएं, सेकेंडरी
    X‑अक्ष जोड़ें, उसकी डिस्प्ले यूनिट को हजारों पर सेट करें, और कस्टम न्यूमेरिक फ़ॉर्मेट
    लागू करें।
  headline: Aspose.Words for .NET का उपयोग करके Word लाइन चार्ट्स में सेकेंडरी X‑अक्ष
    को फ़ॉर्मेट करें और डिस्प्ले यूनिट को हजारों पर सेट करें।
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके एक Word लाइन चार्ट बनाएं, सेकेंडरी
    X‑अक्ष जोड़ें, उसकी डिस्प्ले यूनिट को हजारों पर सेट करें, और कस्टम न्यूमेरिक फ़ॉर्मेट
    लागू करें।
  name: Aspose.Words for .NET का उपयोग करके Word लाइन चार्ट्स में सेकेंडरी X‑अक्ष
    को फ़ॉर्मेट करें और डिस्प्ले यूनिट को हजारों पर सेट करें।
  steps:
  - name: एक नया Document और DocumentBuilder बनाएं ताकि Word फ़ाइल बनाना शुरू किया
      जा सके।
    text: एक नया Document और DocumentBuilder बनाएं ताकि Word फ़ाइल बनाना शुरू किया
      जा सके।
  - name: दस्तावेज़ में 500×300 आकार का लाइन चार्ट डालें और Chart ऑब्जेक्ट प्राप्त
      करें।
    text: दस्तावेज़ में 500×300 आकार का लाइन चार्ट डालें और Chart ऑब्जेक्ट प्राप्त
      करें।
  - name: Aspose.Words द्वारा स्वचालित रूप से जोड़ी गई डिफ़ॉल्ट डेमो सीरीज़ को हटाएँ।
    text: Aspose.Words द्वारा स्वचालित रूप से जोड़ी गई डिफ़ॉल्ट डेमो सीरीज़ को हटाएँ।
  - name: X‑अक्ष के लिए उपयोग किए जाने वाले कैटेगरी लेबल्स की एक एरे परिभाषित करें।
    text: X‑अक्ष के लिए उपयोग किए जाने वाले कैटेगरी लेबल्स की एक एरे परिभाषित करें।
  - name: लेबल्स और वैल्यूज़ का उपयोग करके \"Main Data\" नाम की प्राइमरी डेटा सीरीज़
      जोड़ें।
    text: लेबल्स और वैल्यूज़ का उपयोग करके \"Main Data\" नाम की प्राइमरी डेटा सीरीज़
      जोड़ें।
  - name: Line प्रकार का एक सेकेंडरी सीरीज़ ग्रुप बनाएं और उसे सेकेंडरी एक्सिस ग्रुप
      को असाइन करें।
    text: Line प्रकार का एक सेकेंडरी सीरीज़ ग्रुप बनाएं और उसे सेकेंडरी एक्सिस ग्रुप
      को असाइन करें।
  - name: सेकेंडरी X‑अक्ष की डिस्प्ले यूनिट को हजारों पर सेट करें ताकि मान K में दिखें।
    text: सेकेंडरी X‑अक्ष की डिस्प्ले यूनिट को हजारों पर सेट करें ताकि मान K में दिखें।
  - name: सेकेंडरी X‑अक्ष के टिक लेबल्स पर कस्टम न्यूमेरिक फ़ॉर्मेट \"#,##0.0\" लागू
      करें।
    text: सेकेंडरी X‑अक्ष के टिक लेबल्स पर कस्टम न्यूमेरिक फ़ॉर्मेट \"#,##0.0\" लागू
      करें।
  - name: वैकल्पिक रूप से सेकेंडरी ग्रुप में एक सहायक डेटा सीरीज़ जोड़ें।
    text: वैकल्पिक रूप से सेकेंडरी ग्रुप में एक सहायक डेटा सीरीज़ जोड़ें।
  - name: दस्तावेज़ को .docx फ़ाइल के रूप में सहेजें।
    text: दस्तावेज़ को .docx फ़ाइल के रूप में सहेजें।
  type: HowTo
- questions:
  - answer: नहीं – `AxisX` सेटिंग्स `ChartSeriesGroup` की होती हैं, इसलिए आप `secondaryGroup.AxisX.DisplayUnit.Unit`
      और `secondaryGroup.AxisX.NumberFormat.FormatCode` को सीरीज़ जोड़ने से पहले या
      बाद में सेट कर सकते हैं; कॉन्फ़िगरेशन दोनों ही मामलों में ग्रुप के अक्ष पर लागू
      होगा।
    question: क्या मुझे सेकेंडरी X‑अक्ष पर डिस्प्ले यूनिट और नंबर फ़ॉर्मेट सेट करने
      से पहले सेकेंडरी सीरीज़ जोड़नी पड़ती है?
  - answer: हाँ – किसी भी `AxisBuiltInUnit` वैल्यू को असाइन करें, उदाहरण के लिए `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` ताकि अक्ष के मान हजारों के बजाय मिलियन्स में दिखें।
    question: क्या मैं सेकेंडरी X‑अक्ष के लिए मिलियन्स जैसी कोई अलग बिल्ट‑इन यूनिट
      उपयोग कर सकता हूँ?
  - answer: नहीं – फ़ॉर्मेट कोड केवल उस अक्ष पर लागू होता है जिसे आप संशोधित करते
      हैं (`secondaryGroup.AxisX.NumberFormat.FormatCode`), इसलिए प्राइमरी X‑अक्ष
      अपनी डिफ़ॉल्ट फ़ॉर्मेटिंग रखता है।
    question: क्या कस्टम फ़ॉर्मेट \"#,##0.0\" प्राइमरी X‑अक्ष के लेबल्स को प्रभावित
      करेगा?
  - answer: चार्ट में आपके द्वारा जोड़ी गई सीरीज़ के साथ डिफ़ॉल्ट डेमो सीरीज़ भी शामिल
      हो जाएगी, जिससे अतिरिक्त लाइन्स और असंगत कैटेगरी हो सकते हैं; कलेक्शन को साफ़
      करने से केवल आपका इच्छित डेटा ही दिखेगा।
    question: यदि मैं `lineChart.Series.Clear();` के साथ डेमो सीरीज़ को साफ़ करना
      भूल जाऊँ तो क्या होगा?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: सेकेंडरी X‑अक्ष को फ़ॉर्मेट करें और यूनिट को हजारों पर सेट करें
og_description: Word लाइन चार्ट में सेकेंडरी X‑अक्ष जोड़ें और उसके लेबल्स को कस्टम पैटर्न के साथ हजारों में फ़ॉर्मेट करें।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word लाइन चार्ट में सेकेंडरी X‑अक्ष जोड़ने और उसके लेबल्स को हजारों में डिस्प्ले यूनिट के साथ फ़ॉर्मेट करने का गाइड।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word लाइन चार्ट्स में सेकेंडरी X‑अक्ष को फ़ॉर्मेट करें और डिस्प्ले यूनिट को हजारों पर सेट करें।
यह ट्यूटोरियल आपको एक लाइन चार्ट वाला Word दस्तावेज़ बनाने, सेकेंडरी X‑अक्ष जोड़ने, और उस अक्ष को हजारों में मान दिखाने के लिए कॉन्फ़िगर करने की प्रक्रिया से गुज़राता है। आप सीखेंगे कि सेकेंडरी अक्ष लेबल्स पर कस्टम न्यूमेरिक फ़ॉर्मेट कैसे लागू किया जाए, जिससे डेटा प्रस्तुति पर सटीक नियंत्रण मिल सके। अपने Word रिपोर्ट्स में मल्टी‑अक्सिस चार्ट्स की पठनीयता बढ़ाने के लिए चरणों का पालन करें।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: क्या मुझे सेकेंडरी X‑अक्ष पर डिस्प्ले यूनिट और नंबर फ़ॉर्मेट सेट करने से पहले सेकेंडरी सीरीज़ जोड़नी पड़ती है?**  
A: नहीं – `AxisX` सेटिंग्स `ChartSeriesGroup` की होती हैं, इसलिए आप `secondaryGroup.AxisX.DisplayUnit.Unit` और `secondaryGroup.AxisX.NumberFormat.FormatCode` को सीरीज़ जोड़ने से पहले या बाद में सेट कर सकते हैं; कॉन्फ़िगरेशन दोनों ही मामलों में ग्रुप के अक्ष पर लागू होगा।

**Q: क्या मैं सेकेंडरी X‑अक्ष के लिए मिलियन्स जैसी कोई अलग बिल्ट‑इन यूनिट उपयोग कर सकता हूँ?**  
A: हाँ – किसी भी `AxisBuiltInUnit` वैल्यू को असाइन करें, उदाहरण के लिए `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` ताकि अक्ष के मान हजारों के बजाय मिलियन्स में दिखें।

**Q: क्या कस्टम फ़ॉर्मेट \"#,##0.0\" प्राइमरी X‑अक्ष के लेबल्स को प्रभावित करेगा?**  
A: नहीं – फ़ॉर्मेट कोड केवल उस अक्ष पर लागू होता है जिसे आप संशोधित करते हैं (`secondaryGroup.AxisX.NumberFormat.FormatCode`), इसलिए प्राइमरी X‑अक्ष अपनी डिफ़ॉल्ट फ़ॉर्मेटिंग रखता है।

**Q: यदि मैं `lineChart.Series.Clear();` के साथ डेमो सीरीज़ को साफ़ करना भूल जाऊँ तो क्या होगा?**  
A: चार्ट में आपके द्वारा जोड़ी गई सीरीज़ के साथ डिफ़ॉल्ट डेमो सीरीज़ भी शामिल हो जाएगी, जिससे अतिरिक्त लाइन्स और असंगत कैटेगरी हो सकते हैं; कलेक्शन को साफ़ करने से केवल आपका इच्छित डेटा ही दिखेगा।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}