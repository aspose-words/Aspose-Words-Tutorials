---
title: Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में X अक्ष की ग्रिडलाइन को कस्टमाइज़ करें।
weight: 610
limit:
description: Aspose.Words for .NET के साथ Word कॉलम चार्ट में प्रमुख X‑अक्ष ग्रिडलाइन जोड़ना और उनका रंग‑कस्टमाइज़ करना सीखें।
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET के साथ Word कॉलम चार्ट में प्रमुख X‑अक्ष ग्रिडलाइन
    जोड़ना और उनका रंग‑कस्टमाइज़ करना सीखें।
  headline: Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में X अक्ष की ग्रिडलाइन
    को कस्टमाइज़ करें।
  type: TechArticle
- description: Aspose.Words for .NET के साथ Word कॉलम चार्ट में प्रमुख X‑अक्ष ग्रिडलाइन
    जोड़ना और उनका रंग‑कस्टमाइज़ करना सीखें।
  name: Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में X अक्ष की ग्रिडलाइन को
    कस्टमाइज़ करें।
  steps:
  - name: एक नया Word दस्तावेज़ बनाएं और उसे संपादित करने के लिए DocumentBuilder का
      उपयोग करें।
    text: एक नया Word दस्तावेज़ बनाएं और उसे संपादित करने के लिए DocumentBuilder का
      उपयोग करें।
  - name: दस्तावेज़ में 432×252 आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
    text: दस्तावेज़ में 432×252 आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
  - name: डिफ़ॉल्ट सीरीज़ को हटाएँ और तीन समूहों व मानों के साथ एक कस्टम सीरीज़ जोड़ें।
    text: डिफ़ॉल्ट सीरीज़ को हटाएँ और तीन समूहों व मानों के साथ एक कस्टम सीरीज़ जोड़ें।
  - name: चार्ट के प्राथमिक क्षैतिज (X) अक्ष का रेफ़रेंस प्राप्त करें।
    text: चार्ट के प्राथमिक क्षैतिज (X) अक्ष का रेफ़रेंस प्राप्त करें।
  - name: प्राथमिक X अक्ष पर प्रमुख ग्रिडलाइन के प्रदर्शन को सक्षम करें।
    text: प्राथमिक X अक्ष पर प्रमुख ग्रिडलाइन के प्रदर्शन को सक्षम करें।
  - name: ग्रिडलाइन का रंग नीला सेट करें और उनकी मोटाई 2 पॉइंट रखें।
    text: ग्रिडलाइन का रंग नीला सेट करें और उनकी मोटाई 2 पॉइंट रखें।
  - name: दस्तावेज़ को .docx फ़ाइल में सहेजें।
    text: दस्तावेज़ को .docx फ़ाइल में सहेजें।
  type: HowTo
- questions:
  - answer: 'उसी अक्ष प्रॉपर्टी को false सेट करें: `horizontalAxis.HasMajorGridlines
      = false;` यह X‑अक्ष की प्रमुख ग्रिडलाइन की दृश्यता को टॉगल करता है।'
    question: उन्हें सक्षम करने के बाद प्रमुख ग्रिडलाइन को फिर से कैसे छुपाऊँ?
  - answer: नहीं, `Format.Stroke` सेटिंग्स केवल उस अक्ष पर लागू होती हैं जिसे आप बदलते
      हैं; Y‑अक्ष की ग्रिडलाइन को स्टाइल करने के लिए आपको `chart.AxisY.Format.Stroke`
      को अलग से समायोजित करना होगा।
    question: क्या `horizontalAxis.Format.Stroke.Color` बदलने से Y‑अक्ष की ग्रिडलाइन
      भी प्रभावित होंगी?
  - answer: ग्रिडलाइन को पतला करने के लिए `horizontalAxis.Format.Stroke.Weight` का
      उपयोग करें और एक डबल वैल्यू (जैसे `0.5`) असाइन करें।
    question: कौन सी प्रॉपर्टी X‑अक्ष की प्रमुख ग्रिडलाइन की मोटाई को नियंत्रित करती
      है?
  - answer: हाँ, `horizontalAxis.Format.Stroke.DashStyle` को `DashStyle` एन्‍उम वैल्यू
      जैसे `DashStyle.Dash` या `DashStyle.Dot` पर सेट करें।
    question: क्या मैं X‑अक्ष की प्रमुख ग्रिडलाइन का डैश पैटर्न बदल सकता हूँ?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Word कॉलम चार्ट में X‑अक्ष की ग्रिडलाइन को स्टाइल करें।
og_description: Aspose.Words for .NET के साथ Word चार्ट के प्राथमिक X‑अक्ष ग्रिडलाइन को चालू करें और उनका रंग‑कस्टमाइज़ करें।
og_image_alt: Aspose.Words for .NET का उपयोग करके एक Word दस्तावेज़ जिसमें कॉलम चार्ट है, जहाँ प्राथमिक X‑अक्ष की प्रमुख ग्रिडलाइन को कस्टम रंग में हाइलाइट किया गया है, का गाइड।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके कॉलम चार्ट में X अक्ष की ग्रिडलाइन को कस्टमाइज़ करें।
इस ट्यूटोरियल में आप सीखेंगे कि कैसे एक Word दस्तावेज़ बनाएं, एक कॉलम चार्ट डालें, उसके डिफ़ॉल्ट डेटा को बदलें, और फिर प्राथमिक X अक्ष पर प्रमुख ग्रिडलाइन को सक्षम करें। आप यह भी देखेंगे कि ग्रिडलाइन की लाइन का रंग आपके डिज़ाइन के अनुसार कैसे बदलें। चरण‑दर‑चरण कोड का पालन करके X‑अक्ष की ग्रिडलाइन की दृश्यता और स्टाइलिंग पर सटीक नियंत्रण प्राप्त करें।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: उन्हें सक्षम करने के बाद प्रमुख ग्रिडलाइन को फिर से कैसे छुपाऊँ?**  
A: उसी अक्ष प्रॉपर्टी को false सेट करें: `horizontalAxis.HasMajorGridlines = false;` यह X‑अक्ष की प्रमुख ग्रिडलाइन की दृश्यता को टॉगल करता है।

**Q: क्या `horizontalAxis.Format.Stroke.Color` बदलने से Y‑अक्ष की ग्रिडलाइन भी प्रभावित होंगी?**  
A: नहीं, `Format.Stroke` सेटिंग्स केवल उस अक्ष पर लागू होती हैं जिसे आप बदलते हैं; Y‑अक्ष की ग्रिडलाइन को स्टाइल करने के लिए आपको `chart.AxisY.Format.Stroke` को अलग से समायोजित करना होगा।

**Q: कौन सी प्रॉपर्टी X‑अक्ष की प्रमुख ग्रिडलाइन की मोटाई को नियंत्रित करती है?**  
A: ग्रिडलाइन को पतला करने के लिए `horizontalAxis.Format.Stroke.Weight` का उपयोग करें और एक डबल वैल्यू (जैसे `0.5`) असाइन करें।

**Q: क्या मैं X‑अक्ष की प्रमुख ग्रिडलाइन का डैश पैटर्न बदल सकता हूँ?**  
A: हाँ, `horizontalAxis.Format.Stroke.DashStyle` को `DashStyle` एन्‍उम वैल्यू जैसे `DashStyle.Dash` या `DashStyle.Dot` पर सेट करें।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}