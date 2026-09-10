---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में संरेखित HTML डालें
weight: 210
limit:
description: Aspose.Words for .NET का उपयोग करके बाएँ, केंद्र या दाएँ संरेखण के साथ कच्ची HTML को Word दस्तावेज़ में डालना सीखें।
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में संरेखित HTML डालें
यह इंटरैक्टिव ट्यूटोरियल दिखाता है कि कैसे Aspose.Words for .NET का उपयोग करके कच्ची HTML को Word दस्तावेज़ में एम्बेड किया जाए और उसका संरेखण—बाएँ, केंद्र, या दाएँ—नियंत्रित किया जाए। Document और DocumentBuilder का उपयोग करके, आप केवल कुछ लाइनों के कोड में HTML स्ट्रिंग डाल सकते हैं और वांछित पैराग्राफ संरेखण लागू कर सकते हैं। यह उदाहरण तब आदर्श है जब आपको HTML फ़ॉर्मेटिंग को बनाए रखना हो और सामग्री को अपने दस्तावेज़ में सटीक रूप से रखना हो।

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: यदि DocumentBuilder.InsertHtml को पास किया गया HTML स्ट्रिंग उन टैग्स को शामिल करता है जिन्हें Aspose.Words समर्थन नहीं करता, जैसे <script> या <iframe>, तो क्या होता है?**
A: असमर्थित टैग्स को अनदेखा किया जाता है; Aspose.Words केवल उस HTML के उपसमुच्चय को पार्स करता है जिसे वह रेंडर कर सकता है, इसलिए <script>, <iframe> और समान तत्वों को हटा दिया जाता है जबकि बाकी सामग्री डाली जाती है।

**Q: क्या InsertHtml का उपयोग करने पर इनलाइन CSS स्टाइल्स (जैसे <span style=\"color:red;\">) संरक्षित रहेंगी?**
A: हां, InsertHtml कई इनलाइन CSS प्रॉपर्टीज़ जैसे color, font‑size, और background का सम्मान करता है, उन्हें संबंधित Word फ़ॉर्मेटिंग में परिवर्तित करता है।

**Q: क्या InsertHtml स्वचालित रूप से <div> या <h1> जैसे ब्लॉक‑लेवल एलिमेंट्स के लिए नया पैराग्राफ बनाता है?**
A: ब्लॉक‑लेवल एलिमेंट्स को Word पैराग्राफ़ में मैप किया जाता है, इसलिए प्रत्येक <div>, <p>, <h1> आदि दस्तावेज़ में एक अलग पैराग्राफ बन जाता है।

**Q: मैं मौजूदा दस्तावेज़ में शुरुआत के बजाय किसी विशिष्ट स्थान पर HTML कैसे डाल सकता हूँ?**
A: InsertHtml कॉल करने से पहले DocumentBuilder कर्सर को इच्छित नोड पर ले जाएँ (जैसे builder.MoveToDocumentEnd() या builder.MoveToParagraph(index)); HTML वर्तमान कर्सर स्थिति पर डाला जाएगा।

**Q: यदि दस्तावेज़ में पहले से टेक्स्ट मौजूद है, तो InsertHtml कॉल करने से मौजूदा सामग्री ओवरराइट होगी क्या?**
A: नहीं, InsertHtml पार्स किया गया HTML बिल्डर की वर्तमान स्थिति पर डालता है और मौजूदा नोड्स को हटाता नहीं है, जब तक आप स्पष्ट रूप से कर्सर को उन नोड्स में नहीं ले जाते या उन्हें पहले से नहीं हटाते।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}