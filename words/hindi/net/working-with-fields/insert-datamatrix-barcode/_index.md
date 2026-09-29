---
title: Aspose.Words for .NET का उपयोग करके Word Document में DataMatrix बारकोड डालें।
weight: 210
limit:
description: Aspose.Words for .NET के साथ प्रोग्रामेटिकली एक Word दस्तावेज़ में DataMatrix बारकोड जोड़ें।
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET के साथ प्रोग्रामेटिकली एक Word दस्तावेज़ में
    DataMatrix बारकोड जोड़ें।
  headline: Aspose.Words for .NET का उपयोग करके Word Document में DataMatrix बारकोड
    डालें।
  type: TechArticle
- description: Aspose.Words for .NET के साथ प्रोग्रामेटिकली एक Word दस्तावेज़ में
    DataMatrix बारकोड जोड़ें।
  name: Aspose.Words for .NET का उपयोग करके Word Document में DataMatrix बारकोड डालें।
  steps:
  - name: एक नया खाली Word Document बनाएं और उसे संपादित करने के लिए DocumentBuilder
      बनाएं।
    text: एक नया खाली Word Document बनाएं और उसे संपादित करने के लिए DocumentBuilder
      बनाएं।
  - name: वर्तमान कर्सर स्थिति पर DISPLAYBARCODE फ़ील्ड डालें, जो दस्तावेज़ में एक
      फ़ील्ड प्लेसहोल्डर जोड़ता है।
    text: वर्तमान कर्सर स्थिति पर DISPLAYBARCODE फ़ील्ड डालें, जो दस्तावेज़ में एक
      फ़ील्ड प्लेसहोल्डर जोड़ता है।
  - name: फ़ील्ड का BarcodeType DataMatrix सेट करें और एन्कोड करने के लिए डेटा स्ट्रिंग
      प्रदान करें।
    text: फ़ील्ड का BarcodeType DataMatrix सेट करें और एन्कोड करने के लिए डेटा स्ट्रिंग
      प्रदान करें।
  - name: वैकल्पिक रूप से बारकोड के बैकग्राउंड और फ़ोरग्राउंड रंग निर्धारित करें।
    text: वैकल्पिक रूप से बारकोड के बैकग्राउंड और फ़ोरग्राउंड रंग निर्धारित करें।
  - name: बारकोड छवि को फ़ील्ड के अंदर रेंडर करने के लिए दस्तावेज़ पर UpdateFields
      कॉल करें।
    text: बारकोड छवि को फ़ील्ड के अंदर रेंडर करने के लिए दस्तावेज़ पर UpdateFields
      कॉल करें।
  - name: दस्तावेज़ को .docx फ़ाइल में सहेजें।
    text: दस्तावेज़ को .docx फ़ाइल में सहेजें।
  type: HowTo
- questions:
  - answer: फ़ील्ड डाला जाएगा, लेकिन `document.UpdateFields()` बारकोड को खाली छोड़
      देगा और Aspose.Words एक `FieldException` फेंकेगा जो अमान्य बारकोड प्रकार दर्शाता
      है।
    question: यदि मैं `displayBarcodeField.BarcodeType` को असमर्थित मान असाइन करता
      हूँ तो क्या होता है?
  - answer: '`UpdateFields()` बारकोड छवियों को रेंडर करता है, इसलिए आप कई `FieldDisplayBarcode`
      ऑब्जेक्ट डाल सकते हैं और अंत में एक बार `document.UpdateFields()` कॉल करके सभी
      को रेंडर कर सकते हैं।'
    question: क्या मुझे प्रत्येक बारकोड इन्सर्शन के बाद `document.UpdateFields()`
      कॉल करना चाहिए, या सभी फ़ील्ड जोड़ने के बाद एक बार अपडेट कर सकता हूँ?
  - answer: दोनों प्रॉपर्टीज़ एक हेक्साडेसिमल RGB स्ट्रिंग की अपेक्षा करती हैं जो
      `0x` से शुरू हो (उदाहरण के लिए, लाल के लिए "0xFF0000"); कोई भी अन्य फॉर्मेट
      अनदेखा किया जाएगा और डिफ़ॉल्ट रंग उपयोग किए जाएंगे।
    question: '`BackgroundColor` और `ForegroundColor` के लिए रंग स्ट्रिंग्स किस फॉर्मेट
      में होनी चाहिए?'
  - answer: हां—सिर्फ `displayBarcodeField.BarcodeValue` को नई स्ट्रिंग सेट करें और
      रेंडर की गई छवि को रिफ्रेश करने के लिए `document.UpdateFields()` फिर से कॉल
      करें।
    question: क्या फ़ील्ड डालने के बाद मैं बारकोड पेलोड बदल सकता हूँ?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Aspose.Words के साथ DataMatrix बारकोड डालें।
og_description: .NET कोड की कुछ ही लाइनों में Word फ़ाइल में DataMatrix बारकोड कैसे जोड़ें, सीखें।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में DataMatrix बारकोड को डालने और रेंडर करने का मार्गदर्शन।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word Document में DataMatrix बारकोड डालें।
Aspose.Words for .NET के साथ आप प्रोग्रामेटिकली एक Word दस्तावेज़ में DataMatrix बारकोड जोड़ सकते हैं। यह ट्यूटोरियल दिखाता है कि कैसे नया दस्तावेज़ बनाया जाए, DISPLAYBARCODE फ़ील्ड डाली जाए, उसका प्रकार DataMatrix सेट किया जाए, और Document तथा DocumentBuilder क्लासों का उपयोग करके बारकोड छवि को रेंडर किया जाए। अपने .docx फ़ाइल के भीतर सीधे प्रिंटेबल बारकोड उत्पन्न करने के लिए चरणों का पालन करें।

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: यदि मैं `displayBarcodeField.BarcodeType` को असमर्थित मान असाइन करता हूँ तो क्या होता है?**  
A: फ़ील्ड डाला जाएगा, लेकिन `document.UpdateFields()` बारकोड को खाली छोड़ देगा और Aspose.Words एक `FieldException` फेंकेगा जो अमान्य बारकोड प्रकार दर्शाता है।

**Q: क्या मुझे प्रत्येक बारकोड इन्सर्शन के बाद `document.UpdateFields()` कॉल करना चाहिए, या सभी फ़ील्ड जोड़ने के बाद एक बार अपडेट कर सकता हूँ?**  
A: `UpdateFields()` बारकोड छवियों को रेंडर करता है, इसलिए आप कई `FieldDisplayBarcode` ऑब्जेक्ट डाल सकते हैं और अंत में एक बार `document.UpdateFields()` कॉल करके सभी को रेंडर कर सकते हैं।

**Q: `BackgroundColor` और `ForegroundColor` के लिए रंग स्ट्रिंग्स किस फॉर्मेट में होनी चाहिए?**  
A: दोनों प्रॉपर्टीज़ एक हेक्साडेसिमल RGB स्ट्रिंग की अपेक्षा करती हैं जो `0x` से शुरू हो (उदाहरण के लिए, लाल के लिए "0xFF0000"); कोई भी अन्य फॉर्मेट अनदेखा किया जाएगा और डिफ़ॉल्ट रंग उपयोग किए जाएंगे।

**Q: क्या फ़ील्ड डालने के बाद मैं बारकोड पेलोड बदल सकता हूँ?**  
A: हां—सिर्फ `displayBarcodeField.BarcodeValue` को नई स्ट्रिंग सेट करें और रेंडर की गई छवि को रिफ्रेश करने के लिए `document.UpdateFields()` फिर से कॉल करें।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}