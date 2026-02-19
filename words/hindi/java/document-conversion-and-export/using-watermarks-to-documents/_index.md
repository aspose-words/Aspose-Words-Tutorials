---
date: 2026-02-19
description: Aspose.Words for Java का उपयोग करके वॉटरमार्क के साथ दस्तावेज़ बनाना
  सीखें और पेशेवर दिखने वाले दस्तावेज़ों के लिए इमेज वॉटरमार्क जोड़ें।
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके वॉटरमार्क के साथ दस्तावेज़ बनाएं
url: /hi/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके वॉटरमार्क के साथ दस्तावेज़ बनाएं

इस ट्यूटोरियल में आप Aspose.Words for Java API का उपयोग करके **वॉटरमार्क के साथ दस्तावेज़ बनाएँगे**। वॉटरमार्क—चाहे टेक्स्ट हों या इमेज—आपको फ़ाइल को गोपनीय, ड्राफ्ट, या स्वीकृत के रूप में लेबल करने में मदद करते हैं, और इन्हें प्रोग्रामेटिक रूप से किसी भी Word दस्तावेज़ पर लागू किया जा सकता है। हम लाइब्रेरी सेटअप, टेक्स्ट और इमेज दोनों वॉटरमार्क जोड़ना, उनकी उपस्थिति को कस्टमाइज़ करना, और जब आवश्यकता न रहे तो उन्हें हटाने की प्रक्रिया को समझेंगे।

## त्वरित उत्तर
- **वॉटरमार्क क्या करता है?** यह प्रत्येक पृष्ठ पर टेक्स्ट या इमेज को ओवरले करके स्थिति या ब्रांडिंग दर्शाता है।  
- **जावा में वॉटरमार्क जोड़ने वाली लाइब्रेरी कौन सी है?** Aspose.Words for Java बिल्ट‑इन वॉटरमार्क समर्थन प्रदान करती है।  
- **क्या मैं इमेज वॉटरमार्क जोड़ सकता हूँ?** हाँ—`Shape` क्लास और `add image watermark java` एप्रोच का उपयोग करें।  
- **क्या वॉटरमार्क अर्द्ध‑पारदर्शी है?** आप टेक्स्ट वॉटरमार्क के लिए `setSemitransparent` के माध्यम से अपारदर्शिता नियंत्रित कर सकते हैं।  
- **क्या मुझे लाइसेंस चाहिए?** परीक्षण के लिए एक फ्री ट्रायल काम करता है; उत्पादन के लिए एक वाणिज्यिक लाइसेंस आवश्यक है।

## वॉटरमार्क क्या है और इसे क्यों उपयोग करें?

वॉटरमार्क एक हल्का ओवरले—टेक्स्टुअल या ग्राफिकल—है जो दस्तावेज़ के प्रत्येक पृष्ठ पर जोड़ा जाता है। यह आमतौर पर **गोपनीयता**, **ड्राफ्ट स्थिति**, या **ब्रांडिंग** दर्शाने के लिए उपयोग किया जाता है, बिना मूल सामग्री को बदले। प्रोग्रामेटिक रूप से वॉटरमार्क जोड़ने से बड़ी संख्या में फ़ाइलों में स्थिरता बनी रहती है और मैनुअल एडिटिंग की तुलना में समय बचता है।

## Aspose.Words for Java सेटअप करना

वॉटरमार्क जोड़ना शुरू करने से पहले, सुनिश्चित करें कि लाइब्रेरी आपके प्रोजेक्ट में तैयार है:

1. Aspose.Words for Java को [यहाँ](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
2. डाउनलोड किया गया JAR (या Maven/Gradle डिपेंडेंसी) अपने प्रोजेक्ट के क्लासपाथ में जोड़ें।  
3. अपने Java स्रोत फ़ाइल में आवश्यक क्लासेस इम्पोर्ट करें:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

अब लाइब्रेरी सेट हो गई है, चलिए वास्तविक वॉटरमार्क कोड में डुबकी लगाते हैं।

## टेक्स्ट वॉटरमार्क कैसे जोड़ें

टेक्स्ट वॉटरमार्क दस्तावेज़ को “CONFIDENTIAL” या “DRAFT” के रूप में लेबल करने के लिए आदर्श हैं। निम्नलिखित स्निपेट `TextWatermarkOptions` का उपयोग करके **वॉटरमार्क के साथ दस्तावेज़ बनाएं** का एक साफ़ तरीका दिखाता है।

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### टेक्स्ट वॉटरमार्क को कस्टमाइज़ करना
- **फ़ॉन्ट फ़ैमिली और आकार** – `setFontFamily` और `setFontSize` बदलें।  
- **रंग** – कोई भी `java.awt.Color` उपयोग करें।  
- **लेआउट** – `HORIZONTAL`, `DIAGONAL` आदि चुनें।  
- **पारदर्शिता** – हल्का लुक पाने के लिए `setSemitransparent(true)` टॉगल करें।

## इमेज वॉटरमार्क कैसे जोड़ें (add image watermark java)

इमेज वॉटरमार्क लोगो या कस्टम ग्राफिक्स के लिए परफेक्ट हैं। नीचे **add image watermark java** उदाहरण दिया गया है जो प्रत्येक पृष्ठ के केंद्र में PNG डालता है।

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### इमेज वॉटरमार्क के टिप्स
- **रीसाइज़** पृष्ठ में फिट करने के लिए `setWidth` / `setHeight` का उपयोग करें।  
- **पोजिशन** को `RelativeHorizontalPosition` / `RelativeVerticalPosition` का उपयोग करके केंद्रित या किसी भी मार्जिन पर एलाइन किया जा सकता है।  
- **पारदर्शिता** को इमेज लोड करने से पहले उसकी अल्फा चैनल को एडजस्ट करके लागू किया जा सकता है।

## वॉटरमार्क कैसे हटाएँ

जब किसी दस्तावेज़ को अब वॉटरमार्क की आवश्यकता नहीं रहती, तो आप इसे प्रोग्रामेटिक रूप से हटा सकते हैं। नीचे दिया गया कोड सभी शैप्स को इटररेट करता है और उन शैप्स को हटाता है जिनके नाम में “Watermark” शामिल है।

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## सामान्य समस्याएँ और ट्रबलशूटिंग
- **सेव करने के बाद वॉटरमार्क नहीं दिख रहा** – वॉटरमार्क सेट करने के बाद `doc.save()` कॉल करना सुनिश्चित करें।  
- **इमेज नहीं दिख रही** – इमेज पाथ सही है और फ़ाइल समर्थित फ़ॉर्मेट (PNG, JPEG, BMP) में है, यह जांचें।  
- **पारदर्शिता लागू नहीं हुई** – `setSemitransparent(true)` केवल टेक्स्ट वॉटरमार्क पर काम करता है; इमेज के लिए PNG की अल्फा चैनल को एडिट करें।  
- **एकाधिक सेक्शन** – यदि आपके दस्तावेज़ में कई सेक्शन हैं, तो प्रत्येक सेक्शन के बॉडी में वॉटरमार्क जोड़ें या `doc.getWatermark().setText(...)` का उपयोग करें जो ग्लोबली लागू होता है।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: टेक्स्ट वॉटरमार्क का फ़ॉन्ट कैसे बदलूँ?**  
**उत्तर:** `TextWatermarkOptions` में `setFontFamily` प्रॉपर्टी को संशोधित करें, उदाहरण के लिए, `options.setFontFamily("Times New Roman");`।

**प्रश्न: क्या मैं एक ही दस्तावेज़ में कई वॉटरमार्क जोड़ सकता हूँ?**  
**उत्तर:** हाँ। कई `Shape` ऑब्जेक्ट्स (इमेज के लिए) बनाएं या प्रत्येक वॉटरमार्क के लिए अलग विकल्पों के साथ `doc.getWatermark().setText(...)` कॉल करें।

**प्रश्न: क्या वॉटरमार्क को घुमा सकते हैं?**  
**उत्तर:** इमेज वॉटरमार्क के लिए, `Shape` ऑब्जेक्ट पर `watermark.setRotation(angle)` सेट करें। टेक्स्ट वॉटरमार्क के लिए, `setLayout` प्रॉपर्टी का उपयोग करें (जैसे, `WatermarkLayout.DIAGONAL`)।

**प्रश्न: वॉटरमार्क को अर्द्ध‑पारदर्शी कैसे बनाऊँ?**  
**उत्तर:** `TextWatermarkOptions` में `options.setSemitransparent(true)` सेट करें। इमेज के लिए, लोड करने से पहले इमेज की अपारदर्शिता को एडजस्ट करें।

**प्रश्न: क्या मैं दस्तावेज़ के विशिष्ट सेक्शन में वॉटरमार्क जोड़ सकता हूँ?**  
**उत्तर:** हाँ। `doc.getSections()` को इटररेट करें और केवल इच्छित सेक्शन में वॉटरमार्क जोड़ें।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**अंतिम अपडेट:** 2026-02-19  
**परिक्षण किया गया:** Aspose.Words for Java 24.12 (latest)  
**लेखक:** Aspose