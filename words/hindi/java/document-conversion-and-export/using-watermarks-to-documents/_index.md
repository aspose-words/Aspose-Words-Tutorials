---
date: 2025-12-18
description: Aspose.Words for Java के साथ दस्तावेज़ों में वॉटरमार्क जोड़ना सीखें,
  जिसमें इमेज वॉटरमार्क का उदाहरण, वॉटरमार्क का रंग बदलना, वॉटरमार्क की पारदर्शिता
  सेट करना और वॉटरमार्क हटाना शामिल है।
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके दस्तावेज़ों में वॉटरमार्क कैसे जोड़ें
url: /hi/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का उपयोग करके दस्तावेज़ों में वॉटरमार्क कैसे जोड़ें

## Aspose.Words for Java में दस्तावेज़ों में वॉटरमार्क जोड़ने का परिचय

इस ट्यूटोरियल में आप **वर्ड दस्तावेज़ों में वॉटरमार्क कैसे जोड़ें** सीखेंगे, Aspose.Words for Java के साथ। वॉटरमार्क फ़ाइल को गोपनीय, ड्राफ्ट या स्वीकृत के रूप में लेबल करने का तेज़ तरीका है, और यह टेक्स्ट‑आधारित या इमेज‑आधारित हो सकता है। हम लाइब्रेरी सेटअप, टेक्स्ट और इमेज वॉटरमार्क बनाना, उनकी उपस्थिति को कस्टमाइज़ करना (वॉटरमार्क का रंग बदलना और ट्रांसपेरेंसी सेट करना सहित), और जब वॉटरमार्क की अब आवश्यकता न हो तो उसे हटाने की प्रक्रिया को कवर करेंगे।

## त्वरित उत्तर
- **वॉटरमार्क क्या है?** मुख्य दस्तावेज़ सामग्री के पीछे दिखाई देने वाला अर्ध‑पारदर्शी ओवरले (टेक्स्ट या इमेज)।  
- **क्या मैं कई वॉटरमार्क जोड़ सकता हूँ?** हाँ – कई `Shape` ऑब्जेक्ट बनाकर प्रत्येक को इच्छित सेक्शन में जोड़ें।  
- **वॉटरमार्क का रंग कैसे बदलें?** `TextWatermarkOptions` में `Color` प्रॉपर्टी को समायोजित करें।  
- **क्या इमेज वॉटरमार्क का उदाहरण है?** नीचे “इमेज वॉटरमार्क जोड़ना” सेक्शन देखें।  
- **क्या वॉटरमार्क हटाने के लिए लाइसेंस चाहिए?** प्रोडक्शन उपयोग के लिए एक वैध Aspose.Words लाइसेंस आवश्यक है।

## Aspose.Words for Java सेटअप करना

दस्तावेज़ों में वॉटरमार्क जोड़ना शुरू करने से पहले, हमें Aspose.Words for Java सेटअप करना होगा। शुरू करने के लिए नीचे दिए गए चरणों का पालन करें:

1. Aspose.Words for Java को [यहाँ](https://releases.aspose.com/words/java/) से डाउनलोड करें।  
2. Aspose.Words for Java लाइब्रेरी को अपने Java प्रोजेक्ट में जोड़ें।  
3. अपने Java कोड में आवश्यक क्लासेज़ इम्पोर्ट करें।

अब लाइब्रेरी सेटअप हो गई है, चलिए वास्तविक वॉटरमार्क निर्माण की ओर बढ़ते हैं।

## टेक्स्ट वॉटरमार्क जोड़ना

टेक्स्ट वॉटरमार्क आमतौर पर तब उपयोग किया जाता है जब आप अपने दस्तावेज़ों में टेक्स्टुअल जानकारी जोड़ना चाहते हैं। नीचे Aspose.Words for Java का उपयोग करके टेक्स्ट वॉटरमार्क कैसे जोड़ें, दिखाया गया है:

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

**यह क्यों महत्वपूर्ण है:** `setFontFamily`, `setFontSize`, और `setColor` को समायोजित करके आप **वॉटरमार्क का रंग** अपने ब्रांडिंग के अनुसार बदल सकते हैं, और `setSemitransparent(true)` आपको **वॉटरमार्क की ट्रांसपेरेंसी** सेट करने की सुविधा देता है जिससे प्रभाव सूक्ष्म बनता है।

## इमेज वॉटरमार्क जोड़ना

टेक्स्ट वॉटरमार्क के अलावा, आप अपने दस्तावेज़ों में इमेज वॉटरमार्क भी जोड़ सकते हैं। नीचे एक **इमेज वॉटरमार्क उदाहरण** दिया गया है जो PNG लोगो या स्टैम्प को एम्बेड करने का तरीका दर्शाता है:

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

आप इस ब्लॉक को विभिन्न इमेज या पोज़िशन के साथ दोहरा सकते हैं ताकि **एक ही फ़ाइल में कई वॉटरमार्क** जोड़ सकें।

## वॉटरमार्क को कस्टमाइज़ करना

आप वॉटरमार्क की उपस्थिति और स्थिति को समायोजित करके कस्टमाइज़ कर सकते हैं। टेक्स्ट वॉटरमार्क के लिए आप फ़ॉन्ट, आकार, रंग और लेआउट बदल सकते हैं। इमेज वॉटरमार्क के लिए आप आकार, रोटेशन और अलाइनमेंट को पिछले उदाहरणों में दिखाए अनुसार संशोधित कर सकते हैं।

## वॉटरमार्क हटाना

यदि आपको **वॉटरमार्क दस्तावेज़** सामग्री हटानी है, तो नीचे दिया गया कोड सभी शेप्स के माध्यम से इटररेट करता है और उन शेप्स को डिलीट करता है जिन्हें वॉटरमार्क के रूप में पहचाना गया है:

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

## सामान्य उपयोग केस और टिप्स

- **गोपनीय ड्राफ्ट:** “CONFIDENTIAL” जैसे अर्ध‑पारदर्शी टेक्स्ट वॉटरमार्क लागू करें।  
- **ब्रांडिंग:** कंपनी का लोगो शामिल करने वाला इमेज वॉटरमार्क उपयोग करें।  
- **सेक्शन‑विशिष्ट वॉटरमार्क:** `doc.getSections()` के माध्यम से लूप करके केवल चुने हुए सेक्शन में वॉटरमार्क जोड़ें।  
- **परफ़ॉर्मेंस टिप:** कई दस्तावेज़ों में एक ही वॉटरमार्क लागू करते समय वही `TextWatermarkOptions` इंस्टेंस पुनः उपयोग करें।

## अक्सर पूछे जाने वाले प्रश्न

### टेक्स्ट वॉटरमार्क का फ़ॉन्ट कैसे बदलें?

टेक्स्ट वॉटरमार्क का फ़ॉन्ट बदलने के लिए `TextWatermarkOptions` में `setFontFamily` प्रॉपर्टी को संशोधित करें। उदाहरण के लिए:

```java
options.setFontFamily("Times New Roman");
```

### क्या मैं एक ही दस्तावेज़ में कई वॉटरमार्क जोड़ सकता हूँ?

हाँ, आप विभिन्न सेटिंग्स वाले कई `Shape` ऑब्जेक्ट बनाकर उन्हें दस्तावेज़ में जोड़ सकते हैं।

### क्या वॉटरमार्क को घुमाया जा सकता है?

हाँ, `Shape` ऑब्जेक्ट में `setRotation` प्रॉपर्टी सेट करके वॉटरमार्क को घुमा सकते हैं। पॉज़िटिव वैल्यूज़ घड़ी की दिशा में और नेगेटिव वैल्यूज़ घड़ी के विपरीत दिशा में घुमाती हैं।

### वॉटरमार्क को अर्ध‑पारदर्शी कैसे बनाएं?

वॉटरमार्क को अर्ध‑पारदर्शी बनाने के लिए `TextWatermarkOptions` में `setSemitransparent` प्रॉपर्टी को `true` सेट करें।

### क्या मैं दस्तावेज़ के विशिष्ट सेक्शन में वॉटरमार्क जोड़ सकता हूँ?

हाँ, सेक्शन पर इटररेट करके और इच्छित सेक्शन में वॉटरमार्क जोड़कर आप यह कर सकते हैं।

---

**अंतिम अद्यतन:** 2025-12-18  
**परीक्षण किया गया:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}