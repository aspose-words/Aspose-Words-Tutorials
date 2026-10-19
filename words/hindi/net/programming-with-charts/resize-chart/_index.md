---
title: Aspose.Words for .NET का उपयोग करके Word में पेज साइज बदलते समय चार्ट को अनुपातिक रूप से री-साइज़ करें
weight: 210
limit:
description: Aspose.Words for .NET का उपयोग करके दस्तावेज़ को A4 में बदलते समय Word कॉलम चार्ट को ऑटो‑री-साइज़ करना सीखें।
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET का उपयोग करके दस्तावेज़ को A4 में बदलते समय Word
    कॉलम चार्ट को ऑटो‑री-साइज़ करना सीखें।
  headline: Aspose.Words for .NET का उपयोग करके Word में पेज साइज बदलते समय चार्ट
    को अनुपातिक रूप से री-साइज़ करें
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके दस्तावेज़ को A4 में बदलते समय Word
    कॉलम चार्ट को ऑटो‑री-साइज़ करना सीखें।
  name: Aspose.Words for .NET का उपयोग करके Word में पेज साइज बदलते समय चार्ट को अनुपातिक
    रूप से री-साइज़ करें
  steps:
  - name: एक नया Document ऑब्जेक्ट और उसे संपादित करने के लिए DocumentBuilder बनाएं।
    text: एक नया Document ऑब्जेक्ट और उसे संपादित करने के लिए DocumentBuilder बनाएं।
  - name: 432×252 पॉइंट्स आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
    text: 432×252 पॉइंट्स आकार का कॉलम चार्ट डालें और उसका Chart ऑब्जेक्ट प्राप्त
      करें।
  - name: चार्ट का शीर्षक टेक्स्ट "Quarterly Revenue" सेट करें और इसे दृश्यमान बनाएं।
    text: चार्ट का शीर्षक टेक्स्ट "Quarterly Revenue" सेट करें और इसे दृश्यमान बनाएं।
  - name: दस्तावेज़ को फ़ाइल में सहेजें जिससे मूल चार्ट आकार दिखे।
    text: दस्तावेज़ को फ़ाइल में सहेजें जिससे मूल चार्ट आकार दिखे।
  - name: दस्तावेज़ का पेपर साइज A4 में बदलें और लेआउट को रिफ्रेश करें।
    text: दस्तावेज़ का पेपर साइज A4 में बदलें और लेआउट को रिफ्रेश करें।
  - name: पेज की चौड़ाई का 80 % बराबर नया चार्ट चौड़ाई गणना करें, जबकि मूल आस्पेक्ट
      रेशियो को बरकरार रखें।
    text: पेज की चौड़ाई का 80 % बराबर नया चार्ट चौड़ाई गणना करें, जबकि मूल आस्पेक्ट
      रेशियो को बरकरार रखें।
  - name: यदि शेप में चार्ट है, तो गणना की गई चौड़ाई और ऊँचाई लागू करके उसे री-साइज़
      करें।
    text: यदि शेप में चार्ट है, तो गणना की गई चौड़ाई और ऊँचाई लागू करके उसे री-साइज़
      करें।
  - name: चार्ट को री-साइज़ करने के बाद दस्तावेज़ को सहेजें ताकि नया पेज आकार प्रतिबिंबित
      हो।
    text: चार्ट को री-साइज़ करने के बाद दस्तावेज़ को सहेजें ताकि नया पेज आकार प्रतिबिंबित
      हो।
  type: HowTo
- questions:
  - answer: हाँ। `docBuilder.PageSetup.PaperSize` बदलने से मौजूदा शेप्स स्वचालित रूप
      से समायोजित नहीं होते, इसलिए आपको जैसा दिखाया गया है वैसा `chartContainer.Width`
      और `Height` को स्वयं पुनः गणना करके असाइन करना होगा।
    question: क्या दस्तावेज़ के पेपर साइज बदलने के बाद मुझे चार्ट को मैन्युअल रूप
      से री-साइज़ करना चाहिए?
  - answer: यह `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      को स्टोर करता है और नई चौड़ाई निर्धारित करने के बाद `newChartHeight = newChartWidth
      * originalAspectRatio` की गणना करता है।
    question: कोड री-साइज़ करते समय चार्ट के मूल चौड़ाई‑से‑ऊँचाई अनुपात को कैसे बनाए
      रखता है?
  - answer: '`UpdatePageLayout()` लेआउट इंजन को पेज डाइमेंशन पुनः‑मूल्यांकन करने के
      लिए मजबूर करता है, जिससे `docBuilder.PageSetup.PageWidth` चार्ट आकार पुनः‑गणना
      से पहले नई A4 चौड़ाई को दर्शाता है।'
    question: '`myDoc.UpdatePageLayout()` को पेपर साइज A4 सेट करने के बाद क्यों कॉल
      किया जाता है?'
  - answer: '`if (chartContainer.HasChart)` गार्ड कोड को तब `Width` और `Height` असाइन
      करने से रोकता है जब कोई चार्ट मौजूद नहीं होता, जिससे रन‑टाइम एक्सेप्शन से बचा
      जा सके।'
    question: यदि डाले गए शेप में वास्तव में चार्ट नहीं है तो क्या होता है?
  - answer: बिल्कुल—`0.8` मल्टिप्लायर को अपनी पसंद के किसी भी अनुपात से बदल दें; बाकी
      री‑साइज़ लॉजिक अभी भी मूल आस्पेक्ट रेशियो को बरकरार रखेगा।
    question: क्या मैं 80 % स्केलिंग फैक्टर को किसी अन्य मान में बदल सकता हूँ?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: A4 में स्विच करने पर Word चार्ट को री-साइज़ करें
og_description: दस्तावेज़ को A4 में बदलने के बाद इसे ऑटो‑री-साइज़ करके अपने चार्ट को अनुपातिक रखें।
og_image_alt: Aspose.Words for .NET का उपयोग करके A4‑साइज़ Word दस्तावेज़ में फिट होने के लिए स्वचालित रूप से री-साइज़ किए गए कॉलम चार्ट की स्क्रीनशॉट
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word में पेज साइज बदलते समय चार्ट को अनुपातिक रूप से री-साइज़ करें
यह ट्यूटोरियल दिखाता है कि कैसे एक कॉलम चार्ट को Word दस्तावेज़ में डालें, दस्तावेज़ का पेज साइज A4 में बदलें, और चार्ट को स्वचालित रूप से री-साइज़ किया जाए ताकि वह नई पेज चौड़ाई के अनुपात में बना रहे। चरणों का पालन करने पर आप देखेंगे कि चार्ट अपने आयामों को मैन्युअल स्केलिंग के बिना समायोजित करता है, जिससे विभिन्न पेज फ़ॉर्मेट्स में एकसमान लेआउट सुनिश्चित होता है।

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: क्या दस्तावेज़ के पेपर साइज बदलने के बाद मुझे चार्ट को मैन्युअल रूप से री-साइज़ करना चाहिए?**  
A: हाँ। `docBuilder.PageSetup.PaperSize` बदलने से मौजूदा शेप्स स्वचालित रूप से समायोजित नहीं होते, इसलिए आपको जैसा दिखाया गया है वैसा `chartContainer.Width` और `Height` को स्वयं पुनः गणना करके असाइन करना होगा।

**Q: कोड री-साइज़ करते समय चार्ट के मूल चौड़ाई‑से‑ऊँचाई अनुपात को कैसे बनाए रखता है?**  
A: यह `originalAspectRatio = chartContainer.Height / chartContainer.Width` को स्टोर करता है और नई चौड़ाई निर्धारित करने के बाद `newChartHeight = newChartWidth * originalAspectRatio` की गणना करता है।

**Q: `myDoc.UpdatePageLayout()` को पेपर साइज A4 सेट करने के बाद क्यों कॉल किया जाता है?**  
A: `UpdatePageLayout()` लेआउट इंजन को पेज डाइमेंशन पुनः‑मूल्यांकन करने के लिए मजबूर करता है, जिससे `docBuilder.PageSetup.PageWidth` चार्ट आकार पुनः‑गणना से पहले नई A4 चौड़ाई को दर्शाता है।

**Q: यदि डाले गए शेप में वास्तव में चार्ट नहीं है तो क्या होता है?**  
A: `if (chartContainer.HasChart)` गार्ड कोड को तब `Width` और `Height` असाइन करने से रोकता है जब कोई चार्ट मौजूद नहीं होता, जिससे रन‑टाइम एक्सेप्शन से बचा जा सके।

**Q: क्या मैं 80 % स्केलिंग फैक्टर को किसी अन्य मान में बदल सकता हूँ?**  
A: बिल्कुल—`0.8` मल्टिप्लायर को अपनी पसंद के किसी भी अनुपात से बदल दें; बाकी री‑साइज़ लॉजिक अभी भी मूल आस्पेक्ट रेशियो को बरकरार रखेगा।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}