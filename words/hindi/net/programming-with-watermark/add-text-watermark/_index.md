---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में लाल तिरछा टेक्स्ट वॉटरमार्क जोड़ें
weight: 110
limit:
description: Aspose.Words for .NET का उपयोग करके बैच में उत्पन्न प्रत्येक Word फ़ाइल पर स्वचालित रूप से लाल तिरछा टेक्स्ट वॉटरमार्क लागू करें।
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET का उपयोग करके बैच में उत्पन्न प्रत्येक Word फ़ाइल
    पर स्वचालित रूप से लाल तिरछा टेक्स्ट वॉटरमार्क लागू करें।
  headline: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में लाल तिरछा टेक्स्ट
    वॉटरमार्क जोड़ें
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके बैच में उत्पन्न प्रत्येक Word फ़ाइल
    पर स्वचालित रूप से लाल तिरछा टेक्स्ट वॉटरमार्क लागू करें।
  name: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में लाल तिरछा टेक्स्ट
    वॉटरमार्क जोड़ें
  steps:
  - name: '"GeneratedReports" फ़ोल्डर बनाएं जहाँ आउटपुट फ़ाइलें सहेजी जाएँगी।'
    text: '"GeneratedReports" फ़ोल्डर बनाएं जहाँ आउटपुट फ़ाइलें सहेजी जाएँगी।'
  - name: एक लूप शुरू करें जो तीन अलग-अलग दस्तावेज़ उत्पन्न करेगा।
    text: एक लूप शुरू करें जो तीन अलग-अलग दस्तावेज़ उत्पन्न करेगा।
  - name: एक नया खाली Word दस्तावेज़ ऑब्जेक्ट बनाएं।
    text: एक नया खाली Word दस्तावेज़ ऑब्जेक्ट बनाएं।
  - name: DocumentBuilder का उपयोग करके दस्तावेज़ में एक शीर्षक पंक्ति और विवरण लिखें।
    text: DocumentBuilder का उपयोग करके दस्तावेज़ में एक शीर्षक पंक्ति और विवरण लिखें।
  - name: वॉटरमार्क की उपस्थिति निर्धारित करें, जिसमें फ़ॉन्ट, आकार, रंग और तिरछा
      लेआउट शामिल हैं।
    text: वॉटरमार्क की उपस्थिति निर्धारित करें, जिसमें फ़ॉन्ट, आकार, रंग और तिरछा
      लेआउट शामिल हैं।
  - name: कॉन्फ़िगर किए गए लाल तिरछे वॉटरमार्क को टेक्स्ट "PROTECTED" के साथ दस्तावेज़
      पर लागू करें।
    text: कॉन्फ़िगर किए गए लाल तिरछे वॉटरमार्क को टेक्स्ट "PROTECTED" के साथ दस्तावेज़
      पर लागू करें।
  - name: वॉटरमार्कयुक्त दस्तावेज़ को एक अनूठे फ़ाइलनाम के साथ "GeneratedReports"
      फ़ोल्डर में सहेजें।
    text: वॉटरमार्कयुक्त दस्तावेज़ को एक अनूठे फ़ाइलनाम के साथ "GeneratedReports"
      फ़ोल्डर में सहेजें।
  - name: वर्तमान दस्तावेज़ को प्रोसेस करने के बाद लूप को बंद करें।
    text: वर्तमान दस्तावेज़ को प्रोसेस करने के बाद लूप को बंद करें।
  type: HowTo
- questions:
  - answer: IsSemitrasparent निर्धारित करता है कि वॉटरमार्क आंशिक अपारदर्शिता के साथ
      रेंडर किया जाए या नहीं; इसे **true** सेट करने से टेक्स्ट अर्द्ध‑पारदर्शी हो
      जाता है जिससे नीचे की सामग्री अधिक पढ़ने योग्य रहती है।
    question: '**IsSemitrasparent** विकल्प क्या नियंत्रित करता है और इसे **true**
      सेट करने का क्या प्रभाव पड़ता है?'
  - answer: हाँ—**document.Watermark.SetText** को कॉल करने से पहले **TextWatermarkOptions**
      में **Layout** प्रॉपर्टी को **WatermarkLayout.Horizontal** सेट करें।
    question: क्या मैं वॉटरमार्क की दिशा को तिरछी के बजाय क्षैतिज में बदल सकता हूँ?
  - answer: यह स्निपेट एक नया **Document** इंस्टेंस बनाता है, लेकिन आप किसी भी मौजूदा
      फ़ाइल को (उदाहरण के लिए, `new Document("Existing.docx")`) खोल सकते हैं और फिर
      **document.Watermark.SetText** को कॉल करके वही वॉटरमार्क लागू कर सकते हैं।
    question: क्या यह कोड मौजूदा Word फ़ाइल में वॉटरमार्क जोड़ता है, या केवल नए बनाए
      गए दस्तावेज़ों में?
  - answer: '**TextWatermarkOptions** की **Color** प्रॉपर्टी को **Color.FromArgb(red,
      green, blue)** के साथ कस्टम रंग असाइन करें, उदाहरण के लिए बैंगनी के लिए `Color
      = Color.FromArgb(128, 0, 128)`।'
    question: पूर्वनिर्धारित **Color.Red** के बजाय वॉटरमार्क के लिए कस्टम RGB रंग
      कैसे उपयोग करूँ?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Word डॉक्युमेंट्स में लाल तिरछा टेक्स्ट वॉटरमार्क जोड़ें
og_description: देखें कि Aspose.Words के साथ बैच में प्रत्येक Word दस्तावेज़ पर लाल तिरछा वॉटरमार्क कैसे ऑटो‑ऐप्लाई किया जाता है।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में लाल तिरछा टेक्स्ट वॉटरमार्क कैसे जोड़ें, यह दर्शाने वाला गाइड
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में लाल तिरछा टेक्स्ट वॉटरमार्क जोड़ें
यह ट्यूटोरियल दिखाता है कि बैच रिपोर्ट जनरेशन के दौरान बनाए गए प्रत्येक Word दस्तावेज़ में स्वचालित रूप से लाल तिरछा टेक्स्ट वॉटरमार्क कैसे एम्बेड किया जाए। Aspose.Words for .NET के Document और DocumentBuilder क्लासों का उपयोग करके, वॉटरमार्क को प्रोग्रामेटिक रूप से फ़ाइलों के निर्मित होने पर लागू किया जाता है, जिससे प्रत्येक दस्तावेज़ में समान ब्रांडिंग या गोपनीयता नोटिस बिना मैन्युअल प्रयास के शामिल हो जाता है।

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: **IsSemitrasparent** विकल्प क्या नियंत्रित करता है और इसे **true** सेट करने का क्या प्रभाव पड़ता है?**  
A: IsSemitrasparent निर्धारित करता है कि वॉटरमार्क आंशिक अपारदर्शिता के साथ रेंडर किया जाए या नहीं; इसे **true** सेट करने से टेक्स्ट अर्द्ध‑पारदर्शी हो जाता है जिससे नीचे की सामग्री अधिक पढ़ने योग्य रहती है।

**Q: क्या मैं वॉटरमार्क की दिशा को तिरछी के बजाय क्षैतिज में बदल सकता हूँ?**  
A: हाँ—**document.Watermark.SetText** को कॉल करने से पहले **TextWatermarkOptions** में **Layout** प्रॉपर्टी को **WatermarkLayout.Horizontal** सेट करें।

**Q: क्या यह कोड मौजूदा Word फ़ाइल में वॉटरमार्क जोड़ता है, या केवल नए बनाए गए दस्तावेज़ों में?**  
A: यह स्निपेट एक नया **Document** इंस्टेंस बनाता है, लेकिन आप किसी भी मौजूदा फ़ाइल को (उदाहरण के लिए, `new Document("Existing.docx")`) खोल सकते हैं और फिर **document.Watermark.SetText** को कॉल करके वही वॉटरमार्क लागू कर सकते हैं।

**Q: पूर्वनिर्धारित **Color.Red** के बजाय वॉटरमार्क के लिए कस्टम RGB रंग कैसे उपयोग करूँ?**  
A: **TextWatermarkOptions** की **Color** प्रॉपर्टी को **Color.FromArgb(red, green, blue)** के साथ कस्टम रंग असाइन करें, उदाहरण के लिए बैंगनी के लिए `Color = Color.FromArgb(128, 0, 128)`।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}