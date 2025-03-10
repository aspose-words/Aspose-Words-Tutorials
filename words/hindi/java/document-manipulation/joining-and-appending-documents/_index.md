---
title: Java के लिए Aspose.Words में दस्तावेज़ों को जोड़ना और जोड़ना
linktitle: दस्तावेज़ जोड़ना और जोड़ना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Aspose.Words for Java का उपयोग करके आसानी से दस्तावेज़ों को जोड़ना और जोड़ना सीखें। फ़ॉर्मेटिंग को सुरक्षित रखें, हेडर फ़ुटर प्रबंधित करें, और बहुत कुछ।
weight: 30
url: /hi/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ों को जोड़ना और जोड़ना


## जावा के लिए Aspose.Words में दस्तावेज़ों को जोड़ने और जोड़ने का परिचय

इस ट्यूटोरियल में, हम Aspose.Words for Java लाइब्रेरी का उपयोग करके दस्तावेज़ों को जोड़ने और जोड़ने का तरीका जानेंगे। आप सीखेंगे कि फ़ॉर्मेटिंग और संरचना को बनाए रखते हुए कई दस्तावेज़ों को कैसे सहजता से मर्ज किया जाए।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके जावा प्रोजेक्ट में Aspose.Words for Java API सेट अप है।

## दस्तावेज़ जोड़ने के विकल्प

### सरल परिशिष्ट

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### आयात प्रारूप विकल्पों के साथ जोड़ें

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### रिक्त दस्तावेज़ में जोड़ें

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### पृष्ठ संख्या रूपांतरण के साथ जोड़ें

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // NUMPAGES फ़ील्ड परिवर्तित करें
dstDoc.updatePageLayout(); // सही क्रमांकन के लिए पृष्ठ लेआउट अपडेट करें
```

## विभिन्न पेज सेटअप को संभालना

विभिन्न पृष्ठ सेटअप के साथ दस्तावेज़ जोड़ते समय:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// सुनिश्चित करें कि पृष्ठ सेटअप सेटिंग गंतव्य दस्तावेज़ से मेल खाती है
```

## विभिन्न शैलियों के साथ दस्तावेज़ों को जोड़ना

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## स्मार्ट स्टाइल व्यवहार

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## डॉक्यूमेंटबिल्डर के साथ दस्तावेज़ सम्मिलित करना

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## स्रोत क्रमांकन रखना

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## टेक्स्ट बॉक्स को संभालना

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## शीर्षलेख और पादलेख प्रबंधित करना

### हेडर और फूटर को लिंक करना

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### हेडर और फ़ुटर को अनलिंक करना

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## निष्कर्ष

Aspose.Words for Java दस्तावेज़ों को जोड़ने और जोड़ने के लिए लचीले और शक्तिशाली उपकरण प्रदान करता है, चाहे आपको फ़ॉर्मेटिंग बनाए रखने, विभिन्न पेज सेटअप को संभालने या हेडर और फ़ुटर प्रबंधित करने की आवश्यकता हो। अपनी विशिष्ट दस्तावेज़ प्रसंस्करण आवश्यकताओं को पूरा करने के लिए इन तकनीकों के साथ प्रयोग करें।

## अक्सर पूछे जाने वाले प्रश्न

### मैं विभिन्न शैलियों वाले दस्तावेज़ों को सहजता से कैसे जोड़ सकता हूँ?

 विभिन्न शैलियों वाले दस्तावेज़ों को जोड़ने के लिए, उपयोग करें`ImportFormatMode.USE_DESTINATION_STYLES` जोड़ते समय.

### क्या मैं दस्तावेज़ जोड़ते समय पृष्ठ क्रमांकन सुरक्षित रख सकता हूँ?

 हां, आप इसका उपयोग करके पृष्ठ क्रमांकन को संरक्षित कर सकते हैं`convertNumPageFieldsToPageRef` विधि और पृष्ठ लेआउट को अद्यतन करना।

### स्मार्ट स्टाइल व्यवहार क्या है?

 स्मार्ट स्टाइल व्यवहार दस्तावेज़ जोड़ते समय सुसंगत शैलियों को बनाए रखने में मदद करता है। इसका उपयोग करें`ImportFormatOptions` बेहतर परिणाम के लिए.

### दस्तावेज़ जोड़ते समय मैं टेक्स्ट बॉक्स को कैसे संभाल सकता हूँ?

तय करना`importFormatOptions.setIgnoreTextBoxes(false)` जोड़ने के दौरान टेक्स्ट बॉक्स शामिल करने के लिए.

### यदि मैं दस्तावेजों के बीच हेडर और फूटर को लिंक/अनलिंक करना चाहूं तो क्या होगा?

 आप हेडर और फ़ुटर को लिंक कर सकते हैं`linkToPrevious(true)` या उन्हें अनलिंक करें`linkToPrevious(false)` जरुरत के अनुसार।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
