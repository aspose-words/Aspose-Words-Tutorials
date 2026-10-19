---
title: Aspose.Words for .NET के साथ कॉलम चार्ट में प्लॉट एरिया बॉर्डर को छिपाएँ
weight: 410
limit:
description: Aspose.Words for .NET का उपयोग करके Word कॉलम चार्ट में चार्ट की प्लॉट एरिया बॉर्डर को छिपाना सीखें जबकि एक्सिस लाइनों को दिखाई रखें।
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET का उपयोग करके Word कॉलम चार्ट में चार्ट की प्लॉट
    एरिया बॉर्डर को छिपाना सीखें जबकि एक्सिस लाइनों को दिखाई रखें।
  headline: Aspose.Words for .NET के साथ कॉलम चार्ट में प्लॉट एरिया बॉर्डर को छिपाएँ
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके Word कॉलम चार्ट में चार्ट की प्लॉट
    एरिया बॉर्डर को छिपाना सीखें जबकि एक्सिस लाइनों को दिखाई रखें।
  name: Aspose.Words for .NET के साथ कॉलम चार्ट में प्लॉट एरिया बॉर्डर को छिपाएँ
  steps:
  - name: एक नया खाली Word दस्तावेज़ बनाएं और उसे संपादित करने के लिए एक DocumentBuilder
      बनाएं।
    text: एक नया खाली Word दस्तावेज़ बनाएं और उसे संपादित करने के लिए एक DocumentBuilder
      बनाएं।
  - name: दस्तावेज़ में 432×252 आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
    text: दस्तावेज़ में 432×252 आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
  - name: मौजूदा सभी सीरीज़ को साफ़ करें, तीन श्रेणी लेबल परिभाषित करें, और चार्ट
      में नमूना मानों के साथ एक सीरीज़ जोड़ें।
    text: मौजूदा सभी सीरीज़ को साफ़ करें, तीन श्रेणी लेबल परिभाषित करें, और चार्ट
      में नमूना मानों के साथ एक सीरीज़ जोड़ें।
  - name: प्लॉट एरिया की स्ट्रोक वेट को शून्य सेट करें, जिससे उसकी बॉर्डर हट जाए जबकि
      एक्सिस लाइनों को दिखाई दें।
    text: प्लॉट एरिया की स्ट्रोक वेट को शून्य सेट करें, जिससे उसकी बॉर्डर हट जाए जबकि
      एक्सिस लाइनों को दिखाई दें।
  - name: संशोधित दस्तावेज़ को .docx फ़ाइल में सहेजें।
    text: संशोधित दस्तावेज़ को .docx फ़ाइल में सहेजें।
  type: HowTo
- questions:
  - answer: '`Stroke` प्रॉपर्टी `Chart` ऑब्जेक्ट के समग्र फ़ॉर्मेट से संबंधित है,
      जो प्लॉट एरिया के चारों ओर आयताकार बॉर्डर बनाती है; एक्सिस लाइनों के लिए अलग
      `Axis` ऑब्जेक्ट होते हैं और वे चार्ट की `Stroke` सेटिंग्स से प्रभावित नहीं होते।'
    question: '`columnChart.Format.Stroke.Weight = 0` सेट करने से प्लॉट एरिया बॉर्डर
      क्यों हट जाता है जबकि एक्सिस लाइनों को दिखाई देना जारी रहता है?'
  - answer: नहीं, `Stroke` प्रॉपर्टी पूरे प्लॉट एरिया बॉर्डर को एकल आयत के रूप में
      नियंत्रित करती है, इसलिए भागिक बॉर्डर को Aspose.Words के माध्यम से छिपाया नहीं
      जा सकता; आपको कस्टम शैप्स ओवरले करना होगा या चार्ट को मैन्युअल रूप से संपादित
      करना होगा।
    question: क्या मैं प्लॉट एरिया बॉर्डर के केवल एक पक्ष (जैसे बायाँ पक्ष) को छिपा
      सकता हूँ जबकि बाकी तीन पक्ष दिखते रहें?
  - answer: हाँ, `Stroke` प्रॉपर्टी `ChartType` से स्वतंत्र है, इसलिए इसका `Weight`
      0 सेट करने से लाइन, पाई या किसी भी अन्य समर्थित चार्ट प्रकार के लिए प्लॉट एरिया
      बॉर्डर हट जाता है।
    question: यदि मैं चार्ट प्रकार को लाइन या पाई में बदलूँ, तो क्या `columnChart.Format.Stroke.Weight
      = 0` अभी भी प्लॉट एरिया बॉर्डर को छिपाएगा?
  - answer: कोई अतिरिक्त रिफ्रेश आवश्यक नहीं है; सीरीज़ को साफ़ करके नई जोड़ने से
      चार्ट आंतरिक रूप से अपडेट हो जाता है, और `wordDoc.Save(...)` वर्तमान स्थिति
      को .docx फ़ाइल में लिखता है।
    question: '`columnChart.Series.Clear()` कॉल करने के बाद, क्या मुझे दस्तावेज़ सहेजने
      से पहले चार्ट को रिफ्रेश करने की आवश्यकता है?'
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Word कॉलम चार्ट में प्लॉट बॉर्डर को छिपाएँ
og_description: Aspose.Words for .NET का उपयोग करके Word कॉलम चार्ट में प्लॉट एरिया बॉर्डर को हटाएँ जबकि एक्सिस लाइनों को दिखाई रखें।
og_image_alt: Aspose.Words for .NET का उपयोग करके एक Word दस्तावेज़ में कॉलम चार्ट दिखाने वाला गाइड, जहाँ प्लॉट एरिया बॉर्डर छिपा हुआ है लेकिन एक्सिस लाइनों को दिखाई देना जारी है।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET के साथ कॉलम चार्ट में प्लॉट एरिया बॉर्डर को छिपाएँ
इस ट्यूटोरियल में आप सीखेंगे कि कैसे एक Word दस्तावेज़ बनाएं, एक कॉलम चार्ट डालें, उसे नमूना डेटा से भरें, और फिर चार्ट की प्लॉट एरिया बॉर्डर को छिपाएं जबकि एक्सिस लाइनों को दिखाई रखें। चरण‑दर‑चरण कोड प्रत्येक ऑपरेशन को दर्शाता है और अंत में दस्तावेज़ को सहेजता है, ताकि आप तुरंत परिणाम देख सकें।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: `columnChart.Format.Stroke.Weight = 0` सेट करने से प्लॉट एरिया बॉर्डर क्यों हट जाता है जबकि एक्सिस लाइनों को दिखाई देना जारी रहता है?**  
A: `Stroke` प्रॉपर्टी `Chart` ऑब्जेक्ट के समग्र फ़ॉर्मेट से संबंधित है, जो प्लॉट एरिया के चारों ओर आयताकार बॉर्डर बनाती है; एक्सिस लाइनों के लिए अलग `Axis` ऑब्जेक्ट होते हैं और वे चार्ट की `Stroke` सेटिंग्स से प्रभावित नहीं होते।

**Q: क्या मैं प्लॉट एरिया बॉर्डर के केवल एक पक्ष (जैसे बायाँ पक्ष) को छिपा सकता हूँ जबकि बाकी तीन पक्ष दिखते रहें?**  
A: नहीं, `Stroke` प्रॉपर्टी पूरे प्लॉट एरिया बॉर्डर को एकल आयत के रूप में नियंत्रित करती है, इसलिए भागिक बॉर्डर को Aspose.Words के माध्यम से छिपाया नहीं जा सकता; आपको कस्टम शैप्स ओवरले करना होगा या चार्ट को मैन्युअल रूप से संपादित करना होगा।

**Q: यदि मैं चार्ट प्रकार को लाइन या पाई में बदलूँ, तो क्या `columnChart.Format.Stroke.Weight = 0` अभी भी प्लॉट एरिया बॉर्डर को छिपाएगा?**  
A: हाँ, `Stroke` प्रॉपर्टी `ChartType` से स्वतंत्र है, इसलिए इसका `Weight` 0 सेट करने से लाइन, पाई या किसी भी अन्य समर्थित चार्ट प्रकार के लिए प्लॉट एरिया बॉर्डर हट जाता है।

**Q: `columnChart.Series.Clear()` कॉल करने के बाद, क्या मुझे दस्तावेज़ सहेजने से पहले चार्ट को रिफ्रेश करने की आवश्यकता है?**  
A: कोई अतिरिक्त रिफ्रेश आवश्यक नहीं है; सीरीज़ को साफ़ करके नई जोड़ने से चार्ट आंतरिक रूप से अपडेट हो जाता है, और `wordDoc.Save(...)` वर्तमान स्थिति को .docx फ़ाइल में लिखता है।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}