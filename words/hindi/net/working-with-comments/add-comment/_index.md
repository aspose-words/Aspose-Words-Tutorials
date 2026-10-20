---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में एक विशिष्ट पैराग्राफ पर Comment डालें।
weight: 210
limit:
description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में चुने हुए पैराग्राफ में लेखक टिप्पणी जोड़ने और उसे DOCX के रूप में सहेजने के लिए चरण‑दर‑चरण मार्गदर्शिका।
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में चुने हुए पैराग्राफ
    में लेखक टिप्पणी जोड़ने और उसे DOCX के रूप में सहेजने के लिए चरण‑दर‑चरण मार्गदर्शिका।
  headline: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में एक विशिष्ट पैराग्राफ
    पर Comment डालें।
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में चुने हुए पैराग्राफ
    में लेखक टिप्पणी जोड़ने और उसे DOCX के रूप में सहेजने के लिए चरण‑दर‑चरण मार्गदर्शिका।
  name: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में एक विशिष्ट पैराग्राफ
    पर Comment डालें।
  steps:
  - name: Word फ़ाइल बनाना शुरू करने के लिए एक नया Document और एक DocumentBuilder
      का उदाहरण बनाएं।
    text: Word फ़ाइल बनाना शुरू करने के लिए एक नया Document और एक DocumentBuilder
      का उदाहरण बनाएं।
  - name: DocumentBuilder.Writeln का उपयोग करके दस्तावेज़ में तीन अलग-अलग टेक्स्ट
      पैराग्राफ जोड़ें।
    text: DocumentBuilder.Writeln का उपयोग करके दस्तावेज़ में तीन अलग-अलग टेक्स्ट
      पैराग्राफ जोड़ें।
  - name: दूसरा पैराग्राफ सुरक्षित रूप से प्राप्त करें; यदि दस्तावेज़ में दो से कम
      पैराग्राफ हैं तो पहले पैराग्राफ को उपयोग करें।
    text: दूसरा पैराग्राफ सुरक्षित रूप से प्राप्त करें; यदि दस्तावेज़ में दो से कम
      पैराग्राफ हैं तो पहले पैराग्राफ को उपयोग करें।
  - name: लेखक विवरण के साथ एक Comment बनाएं, उसका टेक्स्ट सेट करें, और उसे चयनित
      पैराग्राफ से संलग्न करें।
    text: लेखक विवरण के साथ एक Comment बनाएं, उसका टेक्स्ट सेट करें, और उसे चयनित
      पैराग्राफ से संलग्न करें।
  - name: संशोधित दस्तावेज़ को वर्तमान फ़ोल्डर में 'sample.docx' नाम की DOCX फ़ाइल
      के रूप में सहेजें।
    text: संशोधित दस्तावेज़ को वर्तमान फ़ोल्डर में 'sample.docx' नाम की DOCX फ़ाइल
      के रूप में सहेजें।
  type: HowTo
- questions:
  - answer: '`if` ब्लॉक `paraList.Count` 2 से कम होने पर पहले पैराग्राफ (`paraList[0]`)
      को उपयोग करता है, इसलिए टिप्पणी उस एकल पैराग्राफ से जुड़ी होगी, न कि अनुपलब्ध
      दूसरे पैराग्राफ से।'
    question: यदि दस्तावेज़ में केवल एक पैराग्राफ हो तो कोड क्या करता है?
  - answer: वे `Comment` कन्स्ट्रक्टर को दूसरे और तीसरे आर्ग्यूमेंट के रूप में पास
      किए जाते हैं – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – जहाँ
      "Jordan" लेखक का नाम है और "JH" उसके आद्याक्षर हैं।
    question: इस उदाहरण में टिप्पणी लेखक का नाम और आद्याक्षर कैसे सेट किए गए हैं?
  - answer: इस स्निपेट में टिप्पणी `AppendChild` के माध्यम से पूरे `Paragraph` से
      जुड़ी है, लेकिन टेक्स्ट रेंज पर टिप्पणी करने के लिए आपको इच्छित `Run` नोड्स
      के चारों ओर `CommentRangeStart` और `CommentRangeEnd` बनाना होगा और फिर उनके
      बीच `Comment` नोड जोड़ना होगा।
    question: क्या मैं पूरे पैराग्राफ के बजाय किसी विशिष्ट टेक्स्ट भाग पर टिप्पणी
      संलग्न कर सकता हूँ?
  - answer: '`AppendChild` `Comment` नोड को पैराग्राफ की चाइल्ड कलेक्शन में जोड़ता
      है, और Aspose.Words दस्तावेज़ सहेजते समय आवश्यक टिप्पणी प्रारम्भ/समाप्ति मार्कर
      स्वचालित रूप से उत्पन्न करता है।'
    question: क्या मुझे मैन्युअल रूप से टिप्पणी मार्कर डालने की जरूरत है, या `AppendChild`
      यह काम संभालता है?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Word पैराग्राफ में एक टिप्पणी डालें।
og_description: Aspose.Words के साथ एक विशिष्ट पैराग्राफ में लेखक टिप्पणी जोड़ें और फ़ाइल को DOCX के रूप में निर्यात करें।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में पैराग्राफ में टिप्पणी कैसे जोड़ें, यह दर्शाने वाला मार्गदर्शिका।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में एक विशिष्ट पैराग्राफ पर Comment डालें।
Aspose.Words for .NET के साथ आप प्रोग्रामेटिक रूप से Word फ़ाइलों में टिप्पणियाँ जोड़ सकते हैं। यह ट्यूटोरियल नया दस्तावेज़ बनाने, तीन पैराग्राफ डालने, दूसरे पैराग्राफ को खोजने, और लेखक व तिथि जानकारी वाली टिप्पणी संलग्न करने की प्रक्रिया दिखाता है। अंत में, दस्तावेज़ को टिप्पणी को संरक्षित रखते हुए DOCX फ़ाइल के रूप में सहेजा जाता है।

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: यदि दस्तावेज़ में केवल एक पैराग्राफ हो तो कोड क्या करता है?**  
A: `if` ब्लॉक `paraList.Count` 2 से कम होने पर पहले पैराग्राफ (`paraList[0]`) को उपयोग करता है, इसलिए टिप्पणी उस एकल पैराग्राफ से जुड़ी होगी, न कि अनुपलब्ध दूसरे पैराग्राफ से।

**Q: इस उदाहरण में टिप्पणी लेखक का नाम और आद्याक्षर कैसे सेट किए गए हैं?**  
A: वे `Comment` कन्स्ट्रक्टर को दूसरे और तीसरे आर्ग्यूमेंट के रूप में पास किए जाते हैं – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – जहाँ "Jordan" लेखक का नाम है और "JH" उसके आद्याक्षर हैं।

**Q: क्या मैं पूरे पैराग्राफ के बजाय किसी विशिष्ट टेक्स्ट भाग पर टिप्पणी संलग्न कर सकता हूँ?**  
A: इस स्निपेट में टिप्पणी `AppendChild` के माध्यम से पूरे `Paragraph` से जुड़ी है, लेकिन टेक्स्ट रेंज पर टिप्पणी करने के लिए आपको इच्छित `Run` नोड्स के चारों ओर `CommentRangeStart` और `CommentRangeEnd` बनाना होगा और फिर उनके बीच `Comment` नोड जोड़ना होगा।

**Q: क्या मुझे मैन्युअल रूप से टिप्पणी मार्कर डालने की जरूरत है, या `AppendChild` यह काम संभालता है?**  
A: `AppendChild` `Comment` नोड को पैराग्राफ की चाइल्ड कलेक्शन में जोड़ता है, और Aspose.Words दस्तावेज़ सहेजते समय आवश्यक टिप्पणी प्रारम्भ/समाप्ति मार्कर स्वचालित रूप से उत्पन्न करता है।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}