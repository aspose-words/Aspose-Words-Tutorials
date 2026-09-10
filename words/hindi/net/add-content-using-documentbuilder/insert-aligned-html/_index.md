---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में संरेखित HTML सम्मिलित करें
weight: 210
limit:
description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में विशिष्ट संरेखण के साथ HTML कैसे सम्मिलित किया जाए, सीखें।
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में संरेखित HTML सम्मिलित करें
यह ट्यूटोरियल दर्शाता है कि Aspose.Words for .NET के DocumentBuilder का उपयोग करके HTML मार्कअप को Word दस्तावेज़ में एम्बेड कैसे किया जाए और उसकी संरेखण को कैसे नियंत्रित किया जाए। आप देखेंगे कि HTML कैसे सम्मिलित किया जाता है, पैराग्राफ संरेखण (बाएँ, केंद्र, या दाएँ) कैसे सेट किया जाता है, और फिर परिणामी दस्तावेज़ को कैसे सहेजा जाता है। यह उदाहरण उन डेवलपर्स के लिए आदर्श है जिन्हें प्रोग्रामेटिक रूप से Word फ़ाइलें बनाते समय वेब‑स्टाइल फ़ॉर्मेटिंग को बनाए रखना होता है।

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

**Q: क्या InsertHtml का उपयोग नई फ़ाइल के बजाय मौजूदा Word दस्तावेज़ में HTML जोड़ने के लिए किया जा सकता है?**
A: हाँ। मौजूदा फ़ाइल से एक Document बनाएं, DocumentBuilder कर्सर को उस स्थान पर रखें जहाँ आप HTML सम्मिलित करना चाहते हैं (उदाहरण के लिए builder.MoveToDocumentEnd() का उपयोग करके), और फिर अपने मार्कअप के साथ builder.InsertHtml को कॉल करें।

**Q: संरेखण के लिए InsertHtml किन HTML एट्रिब्यूट्स को मानता है?**
A: InsertHtml ब्लॉक‑लेवल तत्वों जैसे <p>, <div> और हेडिंग टैग्स पर \"align\" एट्रिब्यूट को मानता है, और परिणामी Word दस्तावेज़ में संबंधित पैराग्राफ संरेखण लागू करता है।

**Q: यदि HTML स्ट्रिंग में असमर्थित टैग या CSS होते हैं तो क्या होता है?**
A: असमर्थित टैग को नजरअंदाज किया जाता है और उनका अंदरूनी टेक्स्ट साधारण टेक्स्ट के रूप में सम्मिलित किया जाता है; इनलाइन CSS स्टाइल्स जिन्हें Aspose.Words पहचानता नहीं है, उन्हें भी नजरअंदाज किया जाता है, इसलिए केवल समर्थित HTML उपसमुच्चय ही रेंडर होता है।

**Q: क्या दस्तावेज़ को सहेजने से पहले DocumentBuilder को बंद करना आवश्यक है?**
A: कोई स्पष्ट बंद करने की आवश्यकता नहीं है; HTML सम्मिलित करने के बाद आप सीधे इच्छित फ़ाइल नाम और फ़ॉर्मेट के साथ doc.Save को कॉल कर सकते हैं, और Builder के संसाधन स्वतः मुक्त हो जाते हैं।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}