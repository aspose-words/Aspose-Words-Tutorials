---
title: Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में समान डेटा लेबल सेट करें
weight: 110
limit:
description: Aspose.Words for .NET के साथ Word कॉलम चार्ट बनाना सीखें और सभी सीरीज़ पर समान डेटा‑लेबल फ़ॉन्ट आकार और रंग लागू करें।
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET के साथ Word कॉलम चार्ट बनाना सीखें और सभी सीरीज़
    पर समान डेटा‑लेबल फ़ॉन्ट आकार और रंग लागू करें।
  headline: Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में समान डेटा लेबल सेट
    करें
  type: TechArticle
- description: Aspose.Words for .NET के साथ Word कॉलम चार्ट बनाना सीखें और सभी सीरीज़
    पर समान डेटा‑लेबल फ़ॉन्ट आकार और रंग लागू करें।
  name: Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में समान डेटा लेबल सेट करें
  steps:
  - name: एक नया खाली Word दस्तावेज़ बनाएं और उसे संपादित करने के लिए DocumentBuilder
      का उपयोग करें।
    text: एक नया खाली Word दस्तावेज़ बनाएं और उसे संपादित करने के लिए DocumentBuilder
      का उपयोग करें।
  - name: दस्तावेज़ में 500×300 आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
    text: दस्तावेज़ में 500×300 आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
  - name: Aspose.Words द्वारा नए चार्ट में जोड़ी गई डिफ़ॉल्ट सैंपल सीरीज़ को हटाएँ।
    text: Aspose.Words द्वारा नए चार्ट में जोड़ी गई डिफ़ॉल्ट सैंपल सीरीज़ को हटाएँ।
  - name: श्रेणी लेबल निर्धारित करें और दो डेटा सीरीज़ (Item Alpha और Item Beta) उनके
      मानों के साथ चार्ट में जोड़ें।
    text: श्रेणी लेबल निर्धारित करें और दो डेटा सीरीज़ (Item Alpha और Item Beta) उनके
      मानों के साथ चार्ट में जोड़ें।
  - name: बेसलाइन फ़ॉन्ट आकार और रंग सेट करें जो सभी डेटा लेबल पर लागू होगा।
    text: बेसलाइन फ़ॉन्ट आकार और रंग सेट करें जो सभी डेटा लेबल पर लागू होगा।
  - name: प्रत्येक सीरीज़ के लिए डेटा लेबल सक्षम करें, संख्यात्मक मान दिखाएँ, और पूर्वनिर्धारित
      फ़ॉन्ट आकार और रंग लागू करें।
    text: प्रत्येक सीरीज़ के लिए डेटा लेबल सक्षम करें, संख्यात्मक मान दिखाएँ, और पूर्वनिर्धारित
      फ़ॉन्ट आकार और रंग लागू करें।
  - name: दस्तावेज़ को .docx फ़ाइल के रूप में सहेजें।
    text: दस्तावेज़ को .docx फ़ाइल के रूप में सहेजें।
  type: HowTo
- questions:
  - answer: '`InsertChart` एक डिफ़ॉल्ट सैंपल सीरीज़ के साथ चार्ट बनाता है; इसे साफ़
      करने से वह प्लेसहोल्डर हट जाता है जिससे चार्ट केवल उन सीरीज़ को दिखाता है जिन्हें
      आप जोड़ते हैं (`Item Alpha` और `Item Beta`)।'
    question: '`chart.Series.Clear()` को अपने स्वयं के सीरीज़ जोड़ने से पहले क्यों
      कॉल करना आवश्यक है?'
  - answer: '`Color.White` को किसी भी `System.Drawing.Color` मान से बदलें, उदाहरण
      के लिए `Color.Black` या `Color.FromArgb(255, 30, 144, 255)`; नया रंग लूप के
      भीतर `series.DataLabels.Font.Color` के माध्यम से लागू किया जाता है।'
    question: डेटा‑लेबल का रंग सफ़ेद के अलावा कुछ और कैसे बदलें?
  - answer: डेटा लेबल छिप जाएंगे, इसलिए आपके द्वारा लागू फ़ॉन्ट सेटिंग्स अदृश्य हो
      जाएँगी; लेबल (और उनकी स्टाइलिंग) को दिखाने के लिए आपको `HasDataLabels` को `true`
      रखना होगा।
    question: फ़ॉन्ट आकार और रंग कॉन्फ़िगर करने के बाद यदि मैं `series.HasDataLabels
      = false` सेट करूँ तो क्या होगा?
  - answer: हाँ—प्रत्येक `ChartSeries` का अपना `DataLabels` ऑब्जेक्ट होता है, इसलिए
      प्रारंभिक लूप के बाद जोड़ी गई किसी भी सीरीज़ को भी `HasDataLabels`, `ShowValue`
      और फ़ॉन्ट प्रॉपर्टीज़ सेट करनी होंगी, या तो फिर से लूप करके या स्टाइलिंग को
      हेल्पर मेथड में निकालकर।
    question: यदि मैं बाद में कोड में एक और सीरीज़ जोड़ूँ तो क्या मुझे फिर से सभी
      सीरीज़ पर लूप करना पड़ेगा?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Word चार्ट पर समान डेटा लेबल लागू करें
og_description: Aspose.Words for .NET के साथ जल्दी से प्रत्येक चार्ट लेबल को समान फ़ॉन्ट आकार और रंग दें।
og_image_alt: एक गाइड जो दिखाता है कि Aspose.Words for .NET का उपयोग करके बनाए गए Word दस्तावेज़ में कॉलम चार्ट है जहाँ सभी डेटा लेबल समान फ़ॉन्ट आकार और रंग साझा करते हैं।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में समान डेटा लेबल सेट करें
यह ट्यूटोरियल दिखाता है कि कैसे Word दस्तावेज़ जनरेट करें, एक कॉलम चार्ट डालें, और Aspose.Words for .NET के साथ कस्टम डेटा सीरीज़ जोड़ें। फिर यह डिफ़ॉल्ट डेटा‑लेबल फ़ॉन्ट आकार और रंग निर्धारित करता है ताकि चार्ट की प्रत्येक सीरीज़ समान लेबल दिखाए। एक ही शैली लागू करके आप पूरे चार्ट में सुसंगत दृश्य रूप सुनिश्चित कर सकते हैं।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: `chart.Series.Clear()` को अपने स्वयं के सीरीज़ जोड़ने से पहले क्यों कॉल करना आवश्यक है?**  
A: `InsertChart` एक डिफ़ॉल्ट सैंपल सीरीज़ के साथ चार्ट बनाता है; इसे साफ़ करने से वह प्लेसहोल्डर हट जाता है जिससे चार्ट केवल उन सीरीज़ को दिखाता है जिन्हें आप जोड़ते हैं (`Item Alpha` और `Item Beta`)।

**Q: डेटा‑लेबल का रंग सफ़ेद के अलावा कुछ और कैसे बदलें?**  
A: `Color.White` को किसी भी `System.Drawing.Color` मान से बदलें, उदाहरण के लिए `Color.Black` या `Color.FromArgb(255, 30, 144, 255)`; नया रंग लूप के भीतर `series.DataLabels.Font.Color` के माध्यम से लागू किया जाता है।

**Q: फ़ॉन्ट आकार और रंग कॉन्फ़िगर करने के बाद यदि मैं `series.HasDataLabels = false` सेट करूँ तो क्या होगा?**  
A: डेटा लेबल छिप जाएंगे, इसलिए आपके द्वारा लागू फ़ॉन्ट सेटिंग्स अदृश्य हो जाएँगी; लेबल (और उनकी स्टाइलिंग) को दिखाने के लिए आपको `HasDataLabels` को `true` रखना होगा।

**Q: यदि मैं बाद में कोड में एक और सीरीज़ जोड़ूँ तो क्या मुझे फिर से सभी सीरीज़ पर लूप करना पड़ेगा?**  
A: हाँ—प्रत्येक `ChartSeries` का अपना `DataLabels` ऑब्जेक्ट होता है, इसलिए प्रारंभिक लूप के बाद जोड़ी गई किसी भी सीरीज़ को भी `HasDataLabels`, `ShowValue` और फ़ॉन्ट प्रॉपर्टीज़ सेट करनी होंगी, या तो फिर से लूप करके या स्टाइलिंग को हेल्पर मेथड में निकालकर।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}