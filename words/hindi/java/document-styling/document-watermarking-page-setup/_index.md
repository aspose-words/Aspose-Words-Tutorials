---
"description": "Aspose.Words for Java के साथ वॉटरमार्क लगाना और पेज कॉन्फ़िगरेशन सेट करना सीखें। सोर्स कोड के साथ एक व्यापक गाइड।"
"linktitle": "दस्तावेज़ वॉटरमार्किंग और पृष्ठ सेटअप"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "दस्तावेज़ वॉटरमार्किंग और पृष्ठ सेटअप"
"url": "/hi/java/document-styling/document-watermarking-page-setup/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ वॉटरमार्किंग और पृष्ठ सेटअप

## परिचय

दस्तावेज़ हेरफेर के क्षेत्र में, Aspose.Words for Java एक शक्तिशाली उपकरण के रूप में खड़ा है, जो डेवलपर्स को दस्तावेज़ प्रसंस्करण के हर पहलू पर नियंत्रण रखने की अनुमति देता है। इस व्यापक गाइड में, हम Aspose.Words for Java का उपयोग करके दस्तावेज़ वॉटरमार्किंग और पेज सेटअप की पेचीदगियों में गहराई से उतरेंगे। चाहे आप एक अनुभवी डेवलपर हों या जावा दस्तावेज़ प्रसंस्करण की दुनिया में कदम रख रहे हों, यह चरण-दर-चरण गाइड आपको आवश्यक ज्ञान और स्रोत कोड से लैस करेगा।

## दस्तावेज़ वॉटरमार्किंग

### वॉटरमार्क जोड़ना

दस्तावेज़ों में वॉटरमार्क जोड़ना ब्रांडिंग या आपकी सामग्री को सुरक्षित करने के लिए महत्वपूर्ण हो सकता है। Aspose.Words for Java इस कार्य को सरल बनाता है। यहाँ बताया गया है कि कैसे:

```java
// दस्तावेज़ लोड करें
Document doc = new Document("document.docx");

// वॉटरमार्क बनाएं
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// वॉटरमार्क की स्थिति निर्धारित करें
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// वॉटरमार्क डालें
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// दस्तावेज़ सहेजें
doc.save("document_with_watermark.docx");
```

### वॉटरमार्क को अनुकूलित करना

आप फ़ॉन्ट, आकार, रंग और रोटेशन को समायोजित करके वॉटरमार्क को और भी कस्टमाइज़ कर सकते हैं। यह लचीलापन सुनिश्चित करता है कि आपका वॉटरमार्क आपके दस्तावेज़ की शैली से सहजता से मेल खाता है।

## पृष्ठ सेटअप

### पृष्ठ का आकार और अभिविन्यास

पेज सेटअप दस्तावेज़ स्वरूपण में महत्वपूर्ण है। Aspose.Words for Java पेज आकार और अभिविन्यास पर पूर्ण नियंत्रण प्रदान करता है:

```java
// दस्तावेज़ लोड करें
Document doc = new Document("document.docx");

// पृष्ठ का आकार A4 पर सेट करें
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// पृष्ठ ओरिएंटेशन को लैंडस्केप में बदलें
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// संशोधित दस्तावेज़ सहेजें
doc.save("formatted_document.docx");
```

### मार्जिन और पृष्ठ क्रमांकन

पेशेवर दस्तावेज़ों के लिए मार्जिन और पेज नंबरिंग पर सटीक नियंत्रण आवश्यक है। Java के लिए Aspose.Words के साथ इसे प्राप्त करें:

```java
// दस्तावेज़ लोड करें
Document doc = new Document("document.docx");

// मार्जिन सेट करें
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// पृष्ठ क्रमांकन सक्षम करें
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// स्वरूपित दस्तावेज़ सहेजें
doc.save("formatted_document.docx");
```

## पूछे जाने वाले प्रश्न

### मैं किसी दस्तावेज़ से वॉटरमार्क कैसे हटा सकता हूँ?

किसी दस्तावेज़ से वॉटरमार्क हटाने के लिए, आप दस्तावेज़ के आकृतियों को दोहरा सकते हैं और वॉटरमार्क का प्रतिनिधित्व करने वाले आकृतियों को हटा सकते हैं। यहाँ एक स्निपेट है:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### क्या मैं एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?

हां, आप अतिरिक्त आकार ऑब्जेक्ट बनाकर और उन्हें आवश्यकतानुसार स्थान देकर दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकते हैं।

### मैं लैंडस्केप ओरिएंटेशन में पेज का आकार कानूनी रूप में कैसे बदलूं?

लैंडस्केप ओरिएंटेशन में पृष्ठ आकार को वैध बनाने के लिए, पृष्ठ की चौड़ाई और ऊंचाई को निम्नानुसार संशोधित करें:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### वॉटरमार्क के लिए डिफ़ॉल्ट फ़ॉन्ट क्या है?

वॉटरमार्क के लिए डिफ़ॉल्ट फ़ॉन्ट कैलिब्री है जिसका फ़ॉन्ट आकार 36 है।

### मैं किसी विशिष्ट पृष्ठ से प्रारंभ करते हुए पृष्ठ संख्या कैसे जोड़ सकता हूँ?

आप अपने दस्तावेज़ में प्रारंभिक पृष्ठ संख्या इस प्रकार सेट करके इसे प्राप्त कर सकते हैं:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### मैं शीर्षलेख या पादलेख में पाठ को केंद्र में कैसे संरेखित करूं?

आप शीर्षलेख या पादलेख के भीतर पैराग्राफ ऑब्जेक्ट पर setAlignment विधि का उपयोग करके शीर्षलेख या पादलेख में पाठ को केंद्र में संरेखित कर सकते हैं।

## निष्कर्ष

इस विस्तृत गाइड में, हमने Aspose.Words for Java का उपयोग करके दस्तावेज़ वॉटरमार्किंग और पेज सेटअप की कला का पता लगाया है। प्रदान किए गए स्रोत कोड स्निपेट और अंतर्दृष्टि से लैस, अब आपके पास अपने दस्तावेज़ों को कुशलता से हेरफेर करने और प्रारूपित करने के लिए उपकरण हैं। Aspose.Words for Java आपको अपने सटीक विनिर्देशों के अनुरूप पेशेवर, ब्रांडेड दस्तावेज़ बनाने की शक्ति देता है।

दस्तावेज़ हेरफेर में महारत हासिल करना डेवलपर्स के लिए एक मूल्यवान कौशल है, और इस यात्रा में Aspose.Words for Java आपका भरोसेमंद साथी है। आज ही शानदार दस्तावेज़ बनाना शुरू करें!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}