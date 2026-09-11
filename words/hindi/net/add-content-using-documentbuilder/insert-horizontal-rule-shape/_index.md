---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में Horizontal Rule Shape सम्मिलित करें।
weight: 110
limit:
description: DocumentBuilder का उपयोग करके Aspose.Words for .NET के साथ Word दस्तावेज़ में एक क्षैतिज रूल शेप जोड़ना सीखें।
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में Horizontal Rule Shape सम्मिलित करें।
इस ट्यूटोरियल में आप सीखेंगे कि Aspose.Words for .NET के साथ प्रोग्रामेटिकली एक क्षैतिज रूल शेप को Word दस्तावेज़ में कैसे सम्मिलित किया जाए। Document और DocumentBuilder क्लासेज़ का उपयोग करके हम एक नया दस्तावेज़ बनाते हैं, टेक्स्ट का एक पैराग्राफ जोड़ते हैं, और फिर इच्छित स्थान पर एक क्षैतिज रेखा शेप रखते हैं। क्षैतिज रूल एक दृश्य विभाजक प्रदान करता है जो सेक्शन ब्रेक या दृश्य ज़ोर देने के लिए उपयोगी हो सकता है।

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

**Q: `builder.InsertHorizontalRule()` लाइन को दस्तावेज़ में बिल्कुल कहाँ रखता है?**  
A: `InsertHorizontalRule` `DocumentBuilder` के वर्तमान कर्सर पोजीशन पर एक क्षैतिज रूल शेप सम्मिलित करता है; यदि आप इसे अपनी अलग लाइन पर चाहते हैं, तो सम्मिलित करने से पहले `builder.Writeln()` कॉल करें।

**Q: क्या मैं सम्मिलित किए गए क्षैतिज रूल की मोटाई, रंग, या चौड़ाई बदल सकता हूँ?**  
A: `InsertHorizontalRule` एक डिफ़ॉल्ट‑स्टाइल्ड रूल जोड़ता है और फ़ॉर्मेटिंग विकल्प नहीं देता; इन प्रॉपर्टीज़ को कस्टमाइज़ करने के लिए आपको मैन्युअली एक `Shape` सम्मिलित करना होगा (उदाहरण के लिए, `builder.InsertShape(ShapeType.HorizontalLine)`) और फिर उसकी `LineFormat` प्रॉपर्टीज़ सेट करें।

**Q: क्या एक ही दस्तावेज़ में एक से अधिक क्षैतिज रूल जोड़ना संभव है?**  
A: हाँ—जब भी आपको नया रूल चाहिए, बस `builder.InsertHorizontalRule()` कॉल करें; प्रत्येक कॉल बिल्डर की वर्तमान स्थिति पर एक अलग शेप बनाता है।

**Q: क्या सहेजे गए .docx को Microsoft Word में खोलने पर क्षैतिज रूल दिखाई देगा?**  
A: बिल्कुल; रूल .docx फ़ाइल के अंदर एक शेप के रूप में सहेजा जाता है, इसलिए Word इसे उत्पन्न दस्तावेज़ में जैसा दिखता है, वैसा ही प्रदर्शित करता है।

**Q: यदि `doc.Save(...)` कॉल करने से पहले `dataDir` फ़ोल्डर मौजूद नहीं है तो क्या होता है?**  
A: `doc.Save` एक `DirectoryNotFoundException` फेंकेगा; सुनिश्चित करें कि लक्ष्य डायरेक्टरी मौजूद है या सहेजने से पहले प्रोग्रामेटिकली इसे बनाएं।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}