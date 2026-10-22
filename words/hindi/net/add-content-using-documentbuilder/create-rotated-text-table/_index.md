---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में घुमाए हुए टेक्स्ट वाली तालिका बनाएं
weight: 110
limit:
description: Aspose.Words for .NET का उपयोग करके स्थिर कॉलम चौड़ाइयों, घुमाए हुए टेक्स्ट, सटीक पंक्ति ऊँचाइयों और भरे हुए सेल वाली Word तालिका बनाना सीखें।
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Aspose.Words for .NET का उपयोग करके स्थिर कॉलम चौड़ाइयों, घुमाए हुए
    टेक्स्ट, सटीक पंक्ति ऊँचाइयों और भरे हुए सेल वाली Word तालिका बनाना सीखें।
  headline: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में घुमाए हुए टेक्स्ट
    वाली तालिका बनाएं
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके स्थिर कॉलम चौड़ाइयों, घुमाए हुए
    टेक्स्ट, सटीक पंक्ति ऊँचाइयों और भरे हुए सेल वाली Word तालिका बनाना सीखें।
  name: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में घुमाए हुए टेक्स्ट वाली
    तालिका बनाएं
  steps:
  - name: एक नया Document और एक DocumentBuilder बनाएं जिसका उपयोग तालिका बनाने के
      लिए किया जाएगा।
    text: एक नया Document और एक DocumentBuilder बनाएं जिसका उपयोग तालिका बनाने के
      लिए किया जाएगा।
  - name: एक नई तालिका शुरू करें, पहला सेल डालें, और कॉलम चौड़ाइयों को स्थिर करें
      ताकि वे स्वतः समायोजित न हों।
    text: एक नई तालिका शुरू करें, पहला सेल डालें, और कॉलम चौड़ाइयों को स्थिर करें
      ताकि वे स्वतः समायोजित न हों।
  - name: वर्तमान सेल में सामग्री को ऊर्ध्वाधर रूप से केंद्रित करें और पहली पंक्ति
      के पहले सेल का टेक्स्ट लिखें।
    text: वर्तमान सेल में सामग्री को ऊर्ध्वाधर रूप से केंद्रित करें और पहली पंक्ति
      के पहले सेल का टेक्स्ट लिखें।
  - name: पहली पंक्ति का दूसरा सेल डालें और उसका टेक्स्ट लिखें।
    text: पहली पंक्ति का दूसरा सेल डालें और उसका टेक्स्ट लिखें।
  - name: पहली पंक्ति को बंद करें, जिससे उसका लेआउट अंतिम रूप ले लेता है।
    text: पहली पंक्ति को बंद करें, जिससे उसका लेआउट अंतिम रूप ले लेता है।
  - name: दूसरी पंक्ति के पहले सेल को शुरू करें, पंक्ति की ऊँचाई को ठीक 100 पॉइंट
      सेट करें, टेक्स्ट को ऊपर की ओर घुमाएँ, और सेल का टेक्स्ट लिखें।
    text: दूसरी पंक्ति के पहले सेल को शुरू करें, पंक्ति की ऊँचाई को ठीक 100 पॉइंट
      सेट करें, टेक्स्ट को ऊपर की ओर घुमाएँ, और सेल का टेक्स्ट लिखें।
  - name: दूसरी पंक्ति का दूसरा सेल डालें, उसका टेक्स्ट नीचे की ओर घुमाएँ, और सेल
      का टेक्स्ट लिखें।
    text: दूसरी पंक्ति का दूसरा सेल डालें, उसका टेक्स्ट नीचे की ओर घुमाएँ, और सेल
      का टेक्स्ट लिखें।
  - name: दूसरी पंक्ति को बंद करें, जिससे तालिका की दूसरी पंक्ति पूरी हो जाती है।
    text: दूसरी पंक्ति को बंद करें, जिससे तालिका की दूसरी पंक्ति पूरी हो जाती है।
  - name: तालिका निर्माण को समाप्त करें, जिससे तालिका की संरचना सील हो जाती है।
    text: तालिका निर्माण को समाप्त करें, जिससे तालिका की संरचना सील हो जाती है।
  - name: पूरा किया गया दस्तावेज़ .docx फ़ाइल में सहेजें।
    text: पूरा किया गया दस्तावेज़ .docx फ़ाइल में सहेजें।
  type: HowTo
- questions:
  - answer: कॉलम चौड़ाइयों को स्थिर करने के बाद, अगला सेल डालने से पहले `builder.CellFormat.Width
      = <valueInPoints>;` का उपयोग करके प्रत्येक सेल को चौड़ाई असाइन करें; तालिका
      इन सटीक चौड़ाइयों को बनाए रखेगी।
    question: '`table.AutoFit(AutoFitBehavior.FixedColumnWidths)` कॉल करने के बाद
      मैं विशिष्ट कॉलम चौड़ाइयाँ कैसे सेट कर सकता हूँ?'
  - answer: '`builder.CellFormat.VerticalAlignment` एक सेल‑स्तर की सेटिंग है, इसलिए
      आपको इसे दूसरी पंक्ति के सेल्स के लिए फिर से सेट करना होगा (उदाहरण के लिए, `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) उनके कंटेंट को लिखने से पहले।'
    question: ऊर्ध्वाधर संरेखण केवल पहली पंक्ति को क्यों प्रभावित करता है और दूसरी
      पंक्ति को नहीं?
  - answer: हां—प्रत्येक `builder.EndRow();` कॉल से पहले `builder.RowFormat.Height`
      और `builder.RowFormat.HeightRule = HeightRule.Exactly` सेट करें; अगली पंक्ति
      में अलग ऊँचाई मान हो सकता है।
    question: क्या मैं प्रत्येक पंक्ति को अलग‑अलग सटीक ऊँचाई दे सकता हूँ, और यदि हाँ,
      तो कैसे?
  - answer: अगले सेल में लिखने से पहले `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      असाइन करके अभिविन्यास को रीसेट करें।
    question: '`TextOrientation.Upward` या `Downward` का उपयोग करने के बाद टेक्स्ट
      अभिविन्यास को डिफ़ॉल्ट पर कैसे वापस लाया जाए?'
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Aspose.Words के साथ Word में घुमाए हुए टेक्स्ट वाली तालिका बनाएं
og_description: स्थिर-चौड़ाई वाली तालिका को ऊर्ध्वाधर घुमाए हुए टेक्स्ट और सटीक पंक्ति ऊँचाइयों के साथ बनाने के लिए चरण‑दर‑चरण कोड।
og_image_alt: स्क्रीनशॉट जिसमें एक Word दस्तावेज़ दिखाया गया है, जिसमें तालिका के कॉलम स्थिर चौड़ाइयों वाले हैं, सेल में घुमाया हुआ टेक्स्ट है, और परिभाषित पंक्ति ऊँचाइयाँ हैं, जो Aspose.Words for .NET का उपयोग करके बनाई गई है।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में घुमाए हुए टेक्स्ट वाली तालिका बनाएं
यह ट्यूटोरियल दर्शाता है कि Word दस्तावेज़ कैसे जेनरेट किया जाए और ऐसी तालिका कैसे जोड़ी जाए जिसकी कॉलम स्थिर चौड़ाइयों वाले हों, पंक्तियों की सटीक ऊँचाइयाँ हों, और सेल का टेक्स्ट ऊर्ध्वाधर रूप से घुमाया गया हो। आप ऊर्ध्वाधर संरेखण सेट करना, टेक्स्ट अभिविन्यास लागू करना, प्रत्येक सेल को सामग्री से भरना, और अंत में दस्तावेज़ को सहेजना सीखेंगे—सब कुछ Aspose.Words for .NET के साथ।

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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

**Q: `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` कॉल करने के बाद मैं विशिष्ट कॉलम चौड़ाइयाँ कैसे सेट कर सकता हूँ?**  
A: कॉलम चौड़ाइयों को स्थिर करने के बाद, अगला सेल डालने से पहले `builder.CellFormat.Width = <valueInPoints>;` का उपयोग करके प्रत्येक सेल को चौड़ाई असाइन करें; तालिका इन सटीक चौड़ाइयों को बनाए रखेगी।

**Q: ऊर्ध्वाधर संरेखण केवल पहली पंक्ति को क्यों प्रभावित करता है और दूसरी पंक्ति को नहीं?**  
A: `builder.CellFormat.VerticalAlignment` एक सेल‑स्तर की सेटिंग है, इसलिए आपको इसे दूसरी पंक्ति के सेल्स के लिए फिर से सेट करना होगा (उदाहरण के लिए, `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) उनके कंटेंट को लिखने से पहले।

**Q: क्या मैं प्रत्येक पंक्ति को अलग‑अलग सटीक ऊँचाई दे सकता हूँ, और यदि हाँ, तो कैसे?**  
A: हां—प्रत्येक `builder.EndRow();` कॉल से पहले `builder.RowFormat.Height` और `builder.RowFormat.HeightRule = HeightRule.Exactly` सेट करें; अगली पंक्ति में अलग ऊँचाई मान हो सकता है।

**Q: `TextOrientation.Upward` या `Downward` का उपयोग करने के बाद टेक्स्ट अभिविन्यास को डिफ़ॉल्ट पर कैसे वापस लाया जाए?**  
A: अगले सेल में लिखने से पहले `builder.CellFormat.Orientation = TextOrientation.Horizontal;` असाइन करके अभिविन्यास को रीसेट करें।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}