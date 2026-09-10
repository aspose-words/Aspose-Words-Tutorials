---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में TC फ़ील्ड डालें
weight: 110
limit:
description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम टेक्स्ट के साथ TC फ़ील्ड कैसे डालें, सीखें।
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में TC फ़ील्ड डालें
यह ट्यूटोरियल दिखाता है कि Aspose.Words for .NET का उपयोग करके नई बनाई गई Word दस्तावेज़ में TC (Table of Contents) फ़ील्ड कैसे डालें। DocumentBuilder का उपयोग करके आप कस्टम एंट्री टेक्स्ट के साथ TC फ़ील्ड जोड़ सकते हैं, जो तालिका सामग्री के लिए एक खोज योग्य इंडेक्स बनाने में उपयोगी है। यह उदाहरण दस्तावेज़ को डिस्क पर सहेजने का भी प्रदर्शन करता है।

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: TC फ़ील्ड कोड में "\f t" स्विच का क्या अर्थ है?**
A: "\f t" स्विच Word को बताता है कि एंट्री को टेबल एंट्री के रूप में माना जाए, जिससे यह \f स्विच के साथ जनरेट किए गए Table of Contents में दिखाई देता है।

**Q: मैं TC फ़ील्ड में दिखाई देने वाले टेक्स्ट को कैसे बदल सकता हूँ?**
A: InsertField कॉल में "Entry Text" को अपनी इच्छित किसी भी स्ट्रिंग से बदलें, उदाहरण के लिए, builder.InsertField(\"TC \\\"Chapter 1\\\" \\f t\");

**Q: क्या मैं एक ही दस्तावेज़ में कई TC फ़ील्ड डाल सकता हूँ?**
A: हां; बस दस्तावेज़ सहेजने से पहले इच्छित स्थानों पर विभिन्न एंट्री टेक्स्ट के साथ builder.InsertField को कॉल करें।

**Q: क्या यह कोड .docx के अलावा अन्य फ़ॉर्मैट्स, जैसे .pdf, के लिए काम करता है?**
A: उदाहरण में दस्तावेज़ .docx के रूप में सहेजा गया है, लेकिन Aspose.Words फ़ाइल एक्सटेंशन को doc.Save में बदलकर और सुनिश्चित करके कि उपयुक्त आउटपुट फ़ॉर्मैट समर्थित है, अन्य फ़ॉर्मैट्स (जैसे .pdf) में भी सहेजा जा सकता है।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}