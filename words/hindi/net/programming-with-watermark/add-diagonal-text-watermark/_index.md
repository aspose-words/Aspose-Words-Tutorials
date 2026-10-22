---
title: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम फ़ॉन्ट के साथ डायगोनल टेक्स्ट वॉटरमार्क बनाएं।
weight: 210
limit:
description: Aspose.Words for .NET का उपयोग करके Word .docx में कस्टम फ़ॉन्ट के साथ डायगोनल टेक्स्ट वॉटरमार्क जोड़ने के लिए चरण‑दर‑चरण कोड।
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET का उपयोग करके Word .docx में कस्टम फ़ॉन्ट के
    साथ डायगोनल टेक्स्ट वॉटरमार्क जोड़ने के लिए चरण‑दर‑चरण कोड।
  headline: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम फ़ॉन्ट के
    साथ डायगोनल टेक्स्ट वॉटरमार्क बनाएं।
  type: TechArticle
- description: Aspose.Words for .NET का उपयोग करके Word .docx में कस्टम फ़ॉन्ट के
    साथ डायगोनल टेक्स्ट वॉटरमार्क जोड़ने के लिए चरण‑दर‑चरण कोड।
  name: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम फ़ॉन्ट के साथ
    डायगोनल टेक्स्ट वॉटरमार्क बनाएं।
  steps:
  - name: '`document` नामक एक नया खाली Word दस्तावेज़ इंस्टेंस बनाएं।'
    text: '`document` नामक एक नया खाली Word दस्तावेज़ इंस्टेंस बनाएं।'
  - name: '`watermarkSettings` को Arial 48‑pt ग्रे फ़ॉन्ट, डायगोनल लेआउट, और अपारदर्शी
      रेंडरिंग के साथ कॉन्फ़िगर करें।'
    text: '`watermarkSettings` को Arial 48‑pt ग्रे फ़ॉन्ट, डायगोनल लेआउट, और अपारदर्शी
      रेंडरिंग के साथ कॉन्फ़िगर करें।'
  - name: पहले परिभाषित सेटिंग्स का उपयोग करके टेक्स्ट वॉटरमार्क "Private" को `document`
      पर लागू करें।
    text: पहले परिभाषित सेटिंग्स का उपयोग करके टेक्स्ट वॉटरमार्क "Private" को `document`
      पर लागू करें।
  - name: वॉटरमार्क किया गया दस्तावेज़ जहाँ सहेजा जाएगा, उसका फ़ाइल पाथ निर्धारित
      करें।
    text: वॉटरमार्क किया गया दस्तावेज़ जहाँ सहेजा जाएगा, उसका फ़ाइल पाथ निर्धारित
      करें।
  - name: संशोधित `document` को निर्दिष्ट पाथ पर .docx फ़ाइल के रूप में सहेजें।
    text: संशोधित `document` को निर्दिष्ट पाथ पर .docx फ़ाइल के रूप में सहेजें।
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` निर्धारित करता है कि वॉटरमार्क आंशिक अपारदर्शिता के
      साथ रेंडर किया जाए या नहीं; इसे `false` सेट करने पर वॉटरमार्क पूरी तरह अपारदर्शी
      हो जाता है, जबकि `true` सेट करने पर डिफ़ॉल्ट अर्ध‑पारदर्शी प्रभाव लागू होता
      है।'
    question: '`TextWatermarkOptions` में **IsSemitrasparent** फ़्लैग क्या नियंत्रित
      करता है?'
  - answer: हाँ—`document.Watermark.SetText` को कॉल करने से पहले `Layout` प्रॉपर्टी
      को `WatermarkLayout.Horizontal` (या किसी अन्य enum मान) पर सेट करें।
    question: क्या मैं वॉटरमार्क की अभिविन्यास को डायगोनल के बजाय क्षैतिज में बदल
      सकता हूँ?
  - answer: Word वॉटरमार्क के लिए अपनी डिफ़ॉल्ट फ़ॉन्ट पर वापस आ जाएगा, इसलिए टेक्स्ट
      अभी भी दिखाई देगा लेकिन इच्छित शैली से अलग दिख सकता है।
    question: यदि निर्दिष्ट `FontFamily` (जैसे "Arial") लक्ष्य मशीन पर स्थापित नहीं
      है तो क्या होता है?
  - answer: '`Document document = new Document("Existing.docx");` के साथ मौजूदा फ़ाइल
      लोड करें, फिर `TextWatermarkOptions` को कॉन्फ़िगर करें और दिखाए अनुसार `document.Watermark.SetText`
      को कॉल करें।'
    question: क्या नया फ़ाइल बनाने के बजाय मौजूदा `.docx` फ़ाइल में वॉटरमार्क जोड़ना
      संभव है?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: कस्टम फ़ॉन्ट के साथ डायगोनल टेक्स्ट वॉटरमार्क जोड़ें
og_description: मिनटों में अपने फ़ॉन्ट के साथ झुके हुए टेक्स्ट वॉटरमार्क को Word फ़ाइल में एम्बेड करना सीखें।
og_image_alt: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम फ़ॉन्ट के साथ डायगोनल टेक्स्ट वॉटरमार्क जोड़ने का तरीका दर्शाने वाला गाइड।
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में कस्टम फ़ॉन्ट के साथ डायगोनल टेक्स्ट वॉटरमार्क बनाएं।
यह ट्यूटोरियल आपको एक नया Word दस्तावेज़ बनाने, अपनी चुनी हुई फ़ॉन्ट सेटिंग्स के साथ डायगोनल टेक्स्ट वॉटरमार्क कॉन्फ़िगर करने, इसे Document.Watermark.SetText API के माध्यम से लागू करने, और परिणाम को .docx फ़ाइल के रूप में सहेजने की प्रक्रिया से ले जाता है। अंत तक आपके पास एक पेशेवर वॉटरमार्क किया हुआ दस्तावेज़ होगा जो आपके ब्रांडिंग या स्वामित्व को दर्शाता है। चरण‑दर‑चरण कोड किसी भी .NET प्रोजेक्ट में कॉपी करने के लिए तैयार है।

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: `TextWatermarkOptions` में **IsSemitrasparent** फ़्लैग क्या नियंत्रित करता है?**  
A: `IsSemitrasparent` निर्धारित करता है कि वॉटरमार्क आंशिक अपारदर्शिता के साथ रेंडर किया जाए या नहीं; इसे `false` सेट करने पर वॉटरमार्क पूरी तरह अपारदर्शी हो जाता है, जबकि `true` सेट करने पर डिफ़ॉल्ट अर्ध‑पारदर्शी प्रभाव लागू होता है।

**Q: क्या मैं वॉटरमार्क की अभिविन्यास को डायगोनल के बजाय क्षैतिज में बदल सकता हूँ?**  
A: हाँ—`document.Watermark.SetText` को कॉल करने से पहले `Layout` प्रॉपर्टी को `WatermarkLayout.Horizontal` (या किसी अन्य enum मान) पर सेट करें।

**Q: यदि निर्दिष्ट `FontFamily` (जैसे "Arial") लक्ष्य मशीन पर स्थापित नहीं है तो क्या होता है?**  
A: Word वॉटरमार्क के लिए अपनी डिफ़ॉल्ट फ़ॉन्ट पर वापस आ जाएगा, इसलिए टेक्स्ट अभी भी दिखाई देगा लेकिन इच्छित शैली से अलग दिख सकता है।

**Q: क्या नया फ़ाइल बनाने के बजाय मौजूदा `.docx` फ़ाइल में वॉटरमार्क जोड़ना संभव है?**  
A: `Document document = new Document("Existing.docx");` के साथ मौजूदा फ़ाइल लोड करें, फिर `TextWatermarkOptions` को कॉन्फ़िगर करें और दिखाए अनुसार `document.Watermark.SetText` को कॉल करें।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}