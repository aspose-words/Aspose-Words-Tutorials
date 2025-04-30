---
"description": "Java के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों को PDF के रूप में सहेजना सीखें। फ़ॉन्ट, गुण और छवि गुणवत्ता को अनुकूलित करें। PDF रूपांतरण के लिए एक व्यापक मार्गदर्शिका।"
"linktitle": "दस्तावेज़ों को PDF के रूप में सहेजना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में दस्तावेज़ों को PDF के रूप में सहेजना"
"url": "/hi/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ों को PDF के रूप में सहेजना


## Java के लिए Aspose.Words में दस्तावेज़ों को PDF के रूप में सहेजने का परिचय

इस चरण-दर-चरण मार्गदर्शिका में, हम Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों को PDF के रूप में सहेजने का तरीका जानेंगे। हम PDF रूपांतरण के विभिन्न पहलुओं को कवर करेंगे और प्रक्रिया को आसान बनाने के लिए कोड उदाहरण प्रदान करेंगे।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

- आपके सिस्टम पर जावा डेवलपमेंट किट (JDK) स्थापित है।
- Aspose.Words for Java लाइब्रेरी। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

## दस्तावेज़ को PDF में परिवर्तित करना

किसी Word दस्तावेज़ को PDF में बदलने के लिए, आप निम्नलिखित कोड स्निपेट का उपयोग कर सकते हैं:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

प्रतिस्थापित करें `"input.docx"` अपने वर्ड दस्तावेज़ के पथ के साथ और `"output.pdf"` वांछित आउटपुट पीडीएफ फ़ाइल पथ के साथ।

## पीडीएफ सेव विकल्पों को नियंत्रित करना

आप इसका उपयोग करके विभिन्न पीडीएफ सेव विकल्पों को नियंत्रित कर सकते हैं `PdfSaveOptions` वर्ग। उदाहरण के लिए, आप पीडीएफ दस्तावेज़ के लिए प्रदर्शन शीर्षक इस प्रकार सेट कर सकते हैं:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## पीडीएफ में फ़ॉन्ट एम्बेड करना

उत्पन्न पीडीएफ में फ़ॉन्ट एम्बेड करने के लिए, निम्नलिखित कोड का उपयोग करें:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## दस्तावेज़ गुण अनुकूलित करना

आप जेनरेट किए गए PDF में दस्तावेज़ गुण अनुकूलित कर सकते हैं। उदाहरण के लिए:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## दस्तावेज़ संरचना निर्यात करना

दस्तावेज़ संरचना को निर्यात करने के लिए, सेट करें `exportDocumentStructure` विकल्प `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## छवि संपीड़न

आप निम्नलिखित कोड का उपयोग करके छवि संपीड़न को नियंत्रित कर सकते हैं:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## अंतिम मुद्रित संपत्ति अद्यतन करना

पीडीएफ में "अंतिम मुद्रित" गुण को अद्यतन करने के लिए, उपयोग करें:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## डीएमएल 3डी प्रभाव रेंडरिंग

DML 3D प्रभावों के उन्नत रेंडरिंग के लिए, रेंडरिंग मोड सेट करें:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## छवियों का अंतर्वेशन

आप छवि गुणवत्ता सुधारने के लिए छवि प्रक्षेप सक्षम कर सकते हैं:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## निष्कर्ष

Aspose.Words for Java, लचीलेपन और अनुकूलन विकल्पों के साथ Word दस्तावेज़ों को PDF प्रारूप में बदलने के लिए व्यापक क्षमताएँ प्रदान करता है। आप PDF आउटपुट के विभिन्न पहलुओं को नियंत्रित कर सकते हैं, जिसमें फ़ॉन्ट, दस्तावेज़ गुण, छवि संपीड़न, और बहुत कुछ शामिल है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Java के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ को PDF में कैसे परिवर्तित करूं?

किसी Word दस्तावेज़ को PDF में बदलने के लिए निम्नलिखित कोड का उपयोग करें:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

प्रतिस्थापित करें `"input.docx"` अपने वर्ड दस्तावेज़ के पथ के साथ और `"output.pdf"` वांछित आउटपुट पीडीएफ फ़ाइल पथ के साथ।

### क्या मैं Java के लिए Aspose.Words द्वारा उत्पन्न पीडीएफ में फ़ॉन्ट एम्बेड कर सकता हूँ?

हां, आप सेटिंग करके पीडीएफ में फ़ॉन्ट एम्बेड कर सकते हैं `setEmbedFullFonts` विकल्प `true` में `PdfSaveOptions`यहाँ एक उदाहरण है:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### मैं उत्पन्न पीडीएफ में दस्तावेज़ गुणों को कैसे अनुकूलित कर सकता हूं?

आप PDF में दस्तावेज़ गुणों को अनुकूलित कर सकते हैं `setCustomPropertiesExport` विकल्प में `PdfSaveOptions`। उदाहरण के लिए:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Java के लिए Aspose.Words में छवि संपीड़न का उद्देश्य क्या है?

इमेज कम्प्रेशन आपको जेनरेट की गई PDF में इमेज की गुणवत्ता और आकार को नियंत्रित करने की अनुमति देता है। आप इमेज कम्प्रेशन मोड को सेट करने के लिए इसका उपयोग कर सकते हैं `setImageCompression` में `PdfSaveOptions`.

### मैं पीडीएफ में "अंतिम मुद्रित" गुण कैसे अपडेट करूं?

आप PDF में "अंतिम मुद्रित" प्रॉपर्टी को सेट करके अपडेट कर सकते हैं `setUpdateLastPrintedProperty` को `true` में `PdfSaveOptions`इससे पीडीएफ मेटाडेटा में अंतिम मुद्रित तिथि प्रतिबिंबित होगी।

### पीडीएफ में कनवर्ट करते समय मैं छवि गुणवत्ता कैसे सुधार सकता हूँ?

छवि गुणवत्ता सुधारने के लिए, सेटिंग करके छवि इंटरपोलेशन सक्षम करें `setInterpolateImages` को `true` में `PdfSaveOptions`इससे पीडीएफ में चिकनी और उच्च गुणवत्ता वाली छवियां प्राप्त होंगी।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}