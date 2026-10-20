---
title: Aspose.Words for .NET का उपयोग करके Hyperlink Comment जोड़ें और PDF Annotation के रूप में निर्यात करें।
weight: 110
limit:
description: Aspose.Words for .NET के साथ Word फ़ाइल में हाइपरलिंक टिप्पणी जोड़ना और उसे PDF एनोटेशन के रूप में निर्यात करना सीखें।
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET के साथ Word फ़ाइल में हाइपरलिंक टिप्पणी जोड़ना
    और उसे PDF एनोटेशन के रूप में निर्यात करना सीखें।
  headline: Aspose.Words for .NET का उपयोग करके Hyperlink Comment जोड़ें और PDF Annotation
    के रूप में निर्यात करें।
  type: TechArticle
- description: Aspose.Words for .NET के साथ Word फ़ाइल में हाइपरलिंक टिप्पणी जोड़ना
    और उसे PDF एनोटेशन के रूप में निर्यात करना सीखें।
  name: Aspose.Words for .NET का उपयोग करके Hyperlink Comment जोड़ें और PDF Annotation
    के रूप में निर्यात करें।
  steps:
  - name: एक नया खाली Document ऑब्जेक्ट और इसे काम में लेने के लिए एक DocumentBuilder
      बनाएं।
    text: एक नया खाली Document ऑब्जेक्ट और इसे काम में लेने के लिए एक DocumentBuilder
      बनाएं।
  - name: एक पंक्ति दृश्यमान टेक्स्ट लिखें जो आने वाली टिप्पणी को होस्ट करेगा।
    text: एक पंक्ति दृश्यमान टेक्स्ट लिखें जो आने वाली टिप्पणी को होस्ट करेगा।
  - name: Jane Doe द्वारा लिखी गई एक Comment बनाएं और इसे दस्तावेज़ के पहले पैराग्राफ
      से संलग्न करें।
    text: Jane Doe द्वारा लिखी गई एक Comment बनाएं और इसे दस्तावेज़ के पहले पैराग्राफ
      से संलग्न करें।
  - name: टिप्पणी के भीतर, एक पैराग्राफ जोड़ें और Aspose.Words Library वेबसाइट का
      नीला, रेखांकित हाइपरलिंक डालें।
    text: टिप्पणी के भीतर, एक पैराग्राफ जोड़ें और Aspose.Words Library वेबसाइट का
      नीला, रेखांकित हाइपरलिंक डालें।
  - name: दस्तावेज़ को इस प्रकार कॉन्फ़िगर करें कि टिप्पणियों को PDF एनोटेशन के रूप
      में रेंडर किया जाए और लेआउट को रीफ़्रेश करें।
    text: दस्तावेज़ को इस प्रकार कॉन्फ़िगर करें कि टिप्पणियों को PDF एनोटेशन के रूप
      में रेंडर किया जाए और लेआउट को रीफ़्रेश करें।
  - name: जेनरेट किए गए PDF को संग्रहीत करने के लिए वर्तमान डायरेक्टरी में एक "Output"
      फ़ोल्डर बनाएं।
    text: जेनरेट किए गए PDF को संग्रहीत करने के लिए वर्तमान डायरेक्टरी में एक "Output"
      फ़ोल्डर बनाएं।
  - name: PdfSaveOptions का उपयोग करके तैयार दस्तावेज़ को PDF फ़ाइल के रूप में सहेजें।
    text: PdfSaveOptions का उपयोग करके तैयार दस्तावेज़ को PDF फ़ाइल के रूप में सहेजें।
  - name: जाँचें कि PDF फ़ाइल मौजूद है और डेटा रखती है, फिर परिणाम को कंसोल पर आउटपुट
      करें।
    text: जाँचें कि PDF फ़ाइल मौजूद है और डेटा रखती है, फिर परिणाम को कंसोल पर आउटपुट
      करें।
  type: HowTo
- questions:
  - answer: '`InsertHyperlink` का तीसरा पैरामीटर यह निर्धारित करता है कि लिंक को फ़ील्ड
      के रूप में माना जाए या नहीं; इसे `false` सेट करने पर एक साधारण हाइपरलिंक डाला
      जाता है जो PDF एनोटेशन में फ़ील्ड कोड की आवश्यकता के बिना काम करता है।'
    question: '`InsertHyperlink` में तीसरा तर्क (`false`) क्या नियंत्रित करता है?'
  - answer: '`Save` कॉल करने से पहले `myDocument.LayoutOptions.CommentDisplayMode`
      को `CommentDisplayMode.ShowInBalloons` सेट करें; तब PDF में टिप्पणी एक सामान्य
      Word टिप्पणी के रूप में होगी, न कि एनोटेशन के रूप में।'
    question: मैं टिप्पणी को PDF एनोटेशन के बजाय Word दस्तावेज़ में बॉलून के रूप में
      कैसे दिखा सकता हूँ?
  - answer: हाँ—आपके द्वारा पैराग्राफ में जोड़ी गई प्रत्येक `Comment` अपना स्वयं का
      `InsertHyperlink` कॉल रख सकती है, और सभी हाइपरलिंक दस्तावेज़ सहेजते समय अलग-अलग
      PDF एनोटेशन के रूप में संरक्षित रहेंगे।
    question: यदि मैं एक से अधिक टिप्पणी जोड़ूँ, तो क्या प्रत्येक हाइपरलिंक निर्यात
      किए गए PDF में काम करेगा?
  - answer: जेनरेट किए गए PDF को खोलें, टिप्पणी एनोटेशन (आमतौर पर नोट आइकन के रूप
      में दिखता है) को खोजें, उसे क्लिक करके टिप्पणी टेक्स्ट दिखाएँ, और फिर नीले रेखांकित
      लिंक को क्लिक करें; यह वेब ब्राउज़र में लक्ष्य URL खोलना चाहिए।
    question: PDF जेनरेट होने के बाद टिप्पणी के भीतर का हाइपरलिंक वास्तव में काम करता
      है या नहीं, मैं कैसे सत्यापित करूँ?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: हाइपरलिंक टिप्पणी डालें और PDF में निर्यात करें
og_description: Word टिप्पणी में क्लिक करने योग्य लिंक एम्बेड करना और उसे PDF एनोटेशन में बदलना सीखें।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में क्लिक करने योग्य हाइपरलिंक वाली टिप्पणी जोड़ने और उसे PDF एनोटेशन के रूप में निर्यात करने का गाइड।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Hyperlink Comment जोड़ें और PDF Annotation के रूप में निर्यात करें।
इस ट्यूटोरियल में आप देखेंगे कि कैसे एक Word दस्तावेज़ बनाया जाए, एक टिप्पणी डालें जिसमें बाहरी वेबसाइट के लिए क्लिक करने योग्य हाइपरलिंक हो, उस टिप्पणी को PDF एनोटेशन के रूप में दिखाने के लिए कॉन्फ़िगर करें, दस्तावेज़ को PDF में निर्यात करें, और परिणामी PDF फ़ाइल को सत्यापित करें। चरण‑दर‑चरण कोड आपको समृद्ध, लिंक‑सक्षम टिप्पणियाँ जोड़ने और उन्हें PDF में परिवर्तित करते समय संरक्षित रखने की अनुमति देता है, जिससे पाठकों के साथ इंटरैक्टिव नोट्स साझा करना आसान हो जाता है।

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: `InsertHyperlink` में तीसरा तर्क (`false`) क्या नियंत्रित करता है?**  
A: `InsertHyperlink` का तीसरा पैरामीटर यह निर्धारित करता है कि लिंक को फ़ील्ड के रूप में माना जाए या नहीं; इसे `false` सेट करने पर एक साधारण हाइपरलिंक डाला जाता है जो PDF एनोटेशन में फ़ील्ड कोड की आवश्यकता के बिना काम करता है।

**Q: मैं टिप्पणी को PDF एनोटेशन के बजाय Word दस्तावेज़ में बॉलून के रूप में कैसे दिखा सकता हूँ?**  
A: `Save` कॉल करने से पहले `myDocument.LayoutOptions.CommentDisplayMode` को `CommentDisplayMode.ShowInBalloons` सेट करें; तब PDF में टिप्पणी एक सामान्य Word टिप्पणी के रूप में होगी, न कि एनोटेशन के रूप में।

**Q: यदि मैं एक से अधिक टिप्पणी जोड़ूँ, तो क्या प्रत्येक हाइपरलिंक निर्यात किए गए PDF में काम करेगा?**  
A: हाँ—आपके द्वारा पैराग्राफ में जोड़ी गई प्रत्येक `Comment` अपना स्वयं का `InsertHyperlink` कॉल रख सकती है, और सभी हाइपरलिंक दस्तावेज़ सहेजते समय अलग-अलग PDF एनोटेशन के रूप में संरक्षित रहेंगे।

**Q: PDF जेनरेट होने के बाद टिप्पणी के भीतर का हाइपरलिंक वास्तव में काम करता है या नहीं, मैं कैसे सत्यापित करूँ?**  
A: जेनरेट किए गए PDF को खोलें, टिप्पणी एनोटेशन (आमतौर पर नोट आइकन के रूप में दिखता है) को खोजें, उसे क्लिक करके टिप्पणी टेक्स्ट दिखाएँ, और फिर नीले रेखांकित लिंक को क्लिक करें; यह वेब ब्राउज़र में लक्ष्य URL खोलना चाहिए।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}