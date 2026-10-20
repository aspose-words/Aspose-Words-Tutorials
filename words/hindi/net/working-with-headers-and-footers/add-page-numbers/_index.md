---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के फुटर में पेज नंबर जोड़ें।
weight: 210
limit:
description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के प्राइमरी फुटर में स्वचालित रूप से अपडेट होने वाले पेज नंबर जोड़ें।
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के प्राइमरी फुटर
    में स्वचालित रूप से अपडेट होने वाले पेज नंबर जोड़ें।
  headline: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के फुटर में पेज नंबर
    जोड़ें।
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के प्राइमरी फुटर
    में स्वचालित रूप से अपडेट होने वाले पेज नंबर जोड़ें।
  name: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के फुटर में पेज नंबर जोड़ें।
  steps:
  - name: एक नया Document ऑब्जेक्ट बनाएं और उससे जुड़ा एक DocumentBuilder बनाएं।
    text: एक नया Document ऑब्जेक्ट बनाएं और उससे जुड़ा एक DocumentBuilder बनाएं।
  - name: बिल्डर का कर्सर पहले सेक्शन के प्राइमरी फुटर पर ले जाएँ।
    text: बिल्डर का कर्सर पहले सेक्शन के प्राइमरी फुटर पर ले जाएँ।
  - name: पैराग्राफ की अलाइनमेंट को सेंटर सेट करें ताकि फुटर टेक्स्ट केंद्रित हो जाए।
    text: पैराग्राफ की अलाइनमेंट को सेंटर सेट करें ताकि फुटर टेक्स्ट केंद्रित हो जाए।
  - name: '"Page " लेबल लिखें और एक PAGE फ़ील्ड डालें जो वर्तमान पेज नंबर दिखाए।'
    text: '"Page " लेबल लिखें और एक PAGE फ़ील्ड डालें जो वर्तमान पेज नंबर दिखाए।'
  - name: '" of " लिखें और एक NUMPAGES फ़ील्ड डालें जो कुल पेज संख्या दिखाए।'
    text: '" of " लिखें और एक NUMPAGES फ़ील्ड डालें जो कुल पेज संख्या दिखाए।'
  - name: दस्तावेज़ को .docx फ़ाइल में सहेजें।
    text: दस्तावेज़ को .docx फ़ाइल में सहेजें।
  type: HowTo
- questions:
  - answer: नहीं। `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` बिल्डर को केवल
      *पहले* सेक्शन के प्राइमरी फुटर पर ले जाता है, इसलिए फ़ील्ड केवल वहीं डाले जाते
      हैं।
    question: यदि दस्तावेज़ में एक से अधिक सेक्शन हैं, तो क्या यह कोड हर सेक्शन के
      फुटर में पेज नंबर जोड़ देगा?
  - answer: फ़ील्ड लिखने से पहले `builder.ParagraphFormat.Alignment` को किसी अन्य
      `ParagraphAlignment` मान (जैसे, `ParagraphAlignment.Right`) पर सेट करें।
    question: मैं फुटर में पेज‑नंबर पैराग्राफ की अलाइनमेंट कैसे बदल सकता हूँ?
  - answer: '`InsertField` फ़ील्ड कोड और एक वैकल्पिक फ़ील्ड परिणाम लेता है; `null`
      पास करने से Aspose.Words को रनटाइम पर Word को परिणाम गणना करने के लिए कहा जाता
      है।'
    question: '`InsertField(\"PAGE\", null)` में `null` आर्ग्यूमेंट क्या दर्शाता है?'
  - answer: हाँ—फ़ील्ड डालने से पहले `HeaderFooterType.FooterPrimary` को `HeaderFooterType.HeaderPrimary`
      (या किसी अन्य हेडर टाइप) से बदलें।
    question: क्या मैं वही "Page X of Y" फ़ील्ड फुटर की बजाय हेडर में रख सकता हूँ?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Word फुटर में स्वचालित पेज नंबर डालें
og_description: Aspose.Words for .NET के साथ Word फुटर में लाइव पेज नंबर जोड़ने के लिए चरण‑दर‑चरण कोड।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के फुटर में स्वचालित पेज नंबर कैसे जोड़ें, यह दर्शाने वाला गाइड।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ के फुटर में पेज नंबर जोड़ें।
यह ट्यूटोरियल दिखाता है कि Aspose.Words Document और DocumentBuilder का उपयोग करके Word दस्तावेज़ के प्राइमरी फुटर में स्वचालित रूप से अपडेट होने वाले पेज नंबर कैसे डालें। पेज नंबर प्रोग्रामेटिकली जोड़ने से आप पूरी फ़ाइल में मैन्युअल एडिट के बिना सुसंगत पेजिंग सुनिश्चित कर सकते हैं। उदाहरण कोड .NET वातावरण में चलाने के लिए तैयार है।

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: यदि दस्तावेज़ में एक से अधिक सेक्शन हैं, तो क्या यह कोड हर सेक्शन के फुटर में पेज नंबर जोड़ देगा?**  
A: नहीं। `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` बिल्डर को केवल *पहले* सेक्शन के प्राइमरी फुटर पर ले जाता है, इसलिए फ़ील्ड केवल वहीं डाले जाते हैं।

**Q: मैं फुटर में पेज‑नंबर पैराग्राफ की अलाइनमेंट कैसे बदल सकता हूँ?**  
A: फ़ील्ड लिखने से पहले `builder.ParagraphFormat.Alignment` को किसी अन्य `ParagraphAlignment` मान (जैसे, `ParagraphAlignment.Right`) पर सेट करें।

**Q: `InsertField(\"PAGE\", null)` में `null` आर्ग्यूमेंट क्या दर्शाता है?**  
A: `InsertField` फ़ील्ड कोड और एक वैकल्पिक फ़ील्ड परिणाम लेता है; `null` पास करने से Aspose.Words को रनटाइम पर Word को परिणाम गणना करने के लिए कहा जाता है।

**Q: क्या मैं वही "Page X of Y" फ़ील्ड फुटर की बजाय हेडर में रख सकता हूँ?**  
A: हाँ—फ़ील्ड डालने से पहले `HeaderFooterType.FooterPrimary` को `HeaderFooterType.HeaderPrimary` (या किसी अन्य हेडर टाइप) से बदलें।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}