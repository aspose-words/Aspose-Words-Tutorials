---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में Horizontal Rule Shape डालें
weight: 110
limit:
description: Aspose.Words for .NET के साथ Word दस्तावेज़ में क्षैतिज रूल शेप डालने के लिए चरण‑दर‑चरण गाइड।
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में Horizontal Rule Shape डालें
जानें कि Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में एक क्षैतिज रूल शेप कैसे डाला जाता है। यह ट्यूटोरियल आपको नया दस्तावेज़ बनाने, एक पंक्ति का टेक्स्ट जोड़ने, DocumentBuilder के साथ एक क्षैतिज रूल शेप रखने, और फ़ाइल को सहेजने की प्रक्रिया से गुजराता है। क्षैतिज रूल आपके कंटेंट के लिए एक सरल दृश्य विभाजक प्रदान करता है।

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: क्या मैं DocumentBuilder.InsertHorizontalRule() से डाले गए क्षैतिज रूल की उपस्थिति (रंग, मोटाई) बदल सकता हूँ?**
A: InsertHorizontalRule डिफ़ॉल्ट फ़ॉर्मेटिंग के साथ एक बिल्ट‑इन क्षैतिज लाइन शेप बनाता है; इसकी उपस्थिति बदलने के लिए आपको डाले गए Shape ऑब्जेक्ट (builder.CurrentParagraph.LastChild) को प्राप्त करना होगा और उसके LineFormat प्रॉपर्टीज़ को समायोजित करना होगा।

**Q: यदि मैं किसी पैराग्राफ के बाद जो पहले से लाइन ब्रेक पर समाप्त होता है, InsertHorizontalRule() कॉल करता हूँ तो क्या होता है?**
A: यह मेथड रूल को एक अलग पैराग्राफ के रूप में डालता है, इसलिए कोई भी पूर्ववर्ती लाइन ब्रेक बस रूल से पहले एक खाली पैराग्राफ बनाता है; रूल फिर भी अपनी स्वयं की पंक्ति में दिखाई देगा।

**Q: क्या DocumentBuilder का उपयोग करके उसी दस्तावेज़ में एक से अधिक क्षैतिज रूल डालना संभव है?**
A: हाँ, builder.InsertHorizontalRule() की प्रत्येक कॉल वर्तमान कर्सर स्थिति पर एक नया क्षैतिज रूल शेप जोड़ती है, जिससे दस्तावेज़ में कई रूल्स हो सकते हैं।

**Q: क्या InsertHorizontalRule() DOCX के अलावा अन्य फ़ॉर्मैट जैसे PDF में दस्तावेज़ सहेजते समय काम करता है?**
A: क्षैतिज रूल दस्तावेज़ मॉडल में एक शेप के रूप में संग्रहीत होता है, इसलिए जब आप PDF, XPS या अन्य समर्थित फ़ॉर्मैट में सहेजते हैं तो रूल आउटपुट में सही ढंग से रेंडर होता है।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}