---
title: जावा के लिए Aspose.Words में दस्तावेज़ों में वॉटरमार्क का उपयोग करना
linktitle: दस्तावेज़ों में वॉटरमार्क का उपयोग करना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Aspose.Words for Java में दस्तावेज़ों में वॉटरमार्क जोड़ना सीखें। पेशेवर दिखने वाले दस्तावेज़ों के लिए टेक्स्ट और छवि वॉटरमार्क को कस्टमाइज़ करें।
weight: 15
url: /hi/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में दस्तावेज़ों में वॉटरमार्क का उपयोग करना


## जावा के लिए Aspose.Words में दस्तावेज़ों में वॉटरमार्क जोड़ने का परिचय

इस ट्यूटोरियल में, हम Aspose.Words for Java API का उपयोग करके दस्तावेज़ों में वॉटरमार्क जोड़ने का तरीका जानेंगे। वॉटरमार्क दस्तावेज़ों को उनकी स्थिति, गोपनीयता या अन्य प्रासंगिक जानकारी को इंगित करने के लिए टेक्स्ट या ग्राफ़िक्स के साथ लेबल करने का एक उपयोगी तरीका है। हम इस गाइड में टेक्स्ट और इमेज वॉटरमार्क दोनों को कवर करेंगे।

## Java के लिए Aspose.Words सेट अप करना

दस्तावेज़ों में वॉटरमार्क जोड़ना शुरू करने से पहले, हमें Java के लिए Aspose.Words सेट अप करना होगा। आरंभ करने के लिए इन चरणों का पालन करें:

1.  Java के लिए Aspose.Words यहाँ से डाउनलोड करें[यहाँ](https://releases.aspose.com/words/java/).
2. अपने जावा प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी जोड़ें।
3. अपने जावा कोड में आवश्यक क्लासेस आयात करें।

अब जब हमने लाइब्रेरी सेट कर ली है तो चलिए वॉटरमार्क जोड़ने के लिए आगे बढ़ते हैं।

## टेक्स्ट वॉटरमार्क जोड़ना

जब आप अपने दस्तावेज़ों में पाठ्य जानकारी जोड़ना चाहते हैं तो टेक्स्ट वॉटरमार्क एक आम विकल्प है। यहाँ बताया गया है कि आप Java के लिए Aspose.Words का उपयोग करके टेक्स्ट वॉटरमार्क कैसे जोड़ सकते हैं:

```java
// दस्तावेज़ इंस्टेंस बनाएँ
Document doc = new Document("Document.docx");

// टेक्स्टवॉटरमार्कविकल्प परिभाषित करें
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//वॉटरमार्क टेक्स्ट और विकल्प सेट करें
doc.getWatermark().setText("Test", options);

// दस्तावेज़ को वॉटरमार्क के साथ सहेजें
doc.save("DocumentWithWatermark.docx");
```

## छवि वॉटरमार्क जोड़ना

टेक्स्ट वॉटरमार्क के अलावा, आप अपने दस्तावेज़ों में इमेज वॉटरमार्क भी जोड़ सकते हैं। इमेज वॉटरमार्क जोड़ने का तरीका इस प्रकार है:

```java
// दस्तावेज़ इंस्टेंस बनाएँ
Document doc = new Document("Document.docx");

// वॉटरमार्क के लिए छवि लोड करें
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// वॉटरमार्क का आकार और स्थिति निर्धारित करें
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// दस्तावेज़ में वॉटरमार्क जोड़ें
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// दस्तावेज़ को वॉटरमार्क के साथ सहेजें
doc.save("DocumentWithImageWatermark.docx");
```

## वॉटरमार्क को अनुकूलित करना

आप वॉटरमार्क की उपस्थिति और स्थिति को समायोजित करके उन्हें अनुकूलित कर सकते हैं। टेक्स्ट वॉटरमार्क के लिए, आप फ़ॉन्ट, आकार, रंग और लेआउट बदल सकते हैं। छवि वॉटरमार्क के लिए, आप पिछले उदाहरणों में दिखाए गए अनुसार उनके आकार और स्थिति को संशोधित कर सकते हैं।

## वॉटरमार्क हटाना

किसी दस्तावेज़ से वॉटरमार्क हटाने के लिए आप निम्नलिखित कोड का उपयोग कर सकते हैं:

```java
// दस्तावेज़ इंस्टेंस बनाएँ
Document doc = new Document("DocumentWithWatermark.docx");

// वॉटरमार्क हटाएँ
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// दस्तावेज़ को वॉटरमार्क के बिना सहेजें
doc.save("DocumentWithoutWatermark.docx");
```


## निष्कर्ष

इस ट्यूटोरियल में, हमने सीखा है कि Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों में वॉटरमार्क कैसे जोड़ें। चाहे आपको टेक्स्ट या इमेज वॉटरमार्क जोड़ने की आवश्यकता हो, Aspose.Words उन्हें कुशलतापूर्वक अनुकूलित और प्रबंधित करने के लिए उपकरण प्रदान करता है। आप वॉटरमार्क को तब भी हटा सकते हैं जब उनकी आवश्यकता न हो, यह सुनिश्चित करते हुए कि आपके दस्तावेज़ साफ़ और पेशेवर हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं टेक्स्ट वॉटरमार्क का फ़ॉन्ट कैसे बदल सकता हूँ?

 किसी टेक्स्ट वॉटरमार्क का फ़ॉन्ट बदलने के लिए, उसे संशोधित करें`setFontFamily` संपत्ति में`TextWatermarkOptions`। उदाहरण के लिए:

```java
options.setFontFamily("Times New Roman");
```

### क्या मैं एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?

 हां, आप एक से अधिक वॉटरमार्क बनाकर किसी दस्तावेज़ में कई वॉटरमार्क जोड़ सकते हैं`Shape` विभिन्न सेटिंग्स वाले ऑब्जेक्ट्स को खोजना और उन्हें दस्तावेज़ में जोड़ना।

### क्या वॉटरमार्क को घुमाना संभव है?

 हां, आप सेटिंग करके वॉटरमार्क को घुमा सकते हैं`setRotation` संपत्ति में`Shape` सकारात्मक मान वॉटरमार्क को दक्षिणावर्त घुमाते हैं, और नकारात्मक मान इसे वामावर्त घुमाते हैं।

### मैं वॉटरमार्क को अर्ध-पारदर्शी कैसे बना सकता हूँ?

 वॉटरमार्क को अर्ध-पारदर्शी बनाने के लिए, सेट करें`setSemitransparent`संपत्ति को`true` में`TextWatermarkOptions`.

### क्या मैं किसी दस्तावेज़ के विशिष्ट अनुभागों में वॉटरमार्क जोड़ सकता हूँ?

हां, आप किसी दस्तावेज़ के विशिष्ट अनुभागों में वॉटरमार्क जोड़ सकते हैं, अनुभागों के माध्यम से पुनरावृत्ति करके और वांछित अनुभागों में वॉटरमार्क जोड़कर।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
