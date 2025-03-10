---
title: जावा के लिए Aspose.Words में दस्तावेज़ गुणों का उपयोग करना
linktitle: दस्तावेज़ गुणधर्मों का उपयोग करना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Aspose.Words for Java के साथ दस्तावेज़ प्रबंधन को अनुकूलित करें। इस व्यापक ट्यूटोरियल में दस्तावेज़ गुणों के साथ काम करना, कस्टम मेटाडेटा जोड़ना और बहुत कुछ सीखें।
weight: 32
url: /hi/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में दस्तावेज़ गुणों का उपयोग करना


## दस्तावेज़ गुणधर्मों का परिचय

दस्तावेज़ गुण किसी भी दस्तावेज़ का एक महत्वपूर्ण हिस्सा हैं। वे दस्तावेज़ के बारे में अतिरिक्त जानकारी प्रदान करते हैं, जैसे कि उसका शीर्षक, लेखक, विषय, कीवर्ड, और बहुत कुछ। Aspose.Words for Java में, आप बिल्ट-इन और कस्टम दस्तावेज़ गुणों दोनों में हेरफेर कर सकते हैं।

## दस्तावेज़ गुण की गणना

### अंतर्निहित गुण

अंतर्निहित दस्तावेज़ गुणों को पुनः प्राप्त करने और उनके साथ काम करने के लिए, आप निम्नलिखित कोड स्निपेट का उपयोग कर सकते हैं:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

यह कोड दस्तावेज़ का नाम और अंतर्निहित गुण प्रदर्शित करेगा, जिसमें "शीर्षक," "लेखक," और "कीवर्ड" जैसे गुण शामिल हैं।

### कस्टम गुण

कस्टम दस्तावेज़ गुणों के साथ काम करने के लिए, आप निम्नलिखित कोड स्निपेट का उपयोग कर सकते हैं:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

यह कोड स्निपेट प्रदर्शित करता है कि कस्टम दस्तावेज़ गुण कैसे जोड़ें, जिसमें बूलियन मान, स्ट्रिंग, दिनांक, संशोधन संख्या और संख्यात्मक मान शामिल हैं।

## दस्तावेज़ गुण हटाना

विशिष्ट दस्तावेज़ गुण हटाने के लिए, आप निम्नलिखित कोड का उपयोग कर सकते हैं:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

यह कोड दस्तावेज़ से कस्टम प्रॉपर्टी "अधिकृत तिथि" को हटा देता है।

## सामग्री से लिंक कॉन्फ़िगर करना

कुछ मामलों में, आप अपने दस्तावेज़ में लिंक बनाना चाह सकते हैं। यहाँ बताया गया है कि आप ऐसा कैसे कर सकते हैं:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // सामग्री संपत्ति से जुड़े जोड़ें.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

यह कोड स्निपेट दर्शाता है कि अपने दस्तावेज़ में बुकमार्क कैसे बनाएं और उस बुकमार्क से लिंक करने वाला कस्टम दस्तावेज़ गुण कैसे जोड़ें।

## मापन इकाइयों के बीच रूपांतरण

Aspose.Words for Java में, आप मापन इकाइयों को आसानी से परिवर्तित कर सकते हैं। इसे कैसे करें, इसका एक उदाहरण यहां दिया गया है:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // मार्जिन को इंच में सेट करें.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

यह कोड स्निपेट विभिन्न मार्जिन और दूरियों को इंच में बदलकर उन्हें बिंदुओं में परिवर्तित करता है।

## नियंत्रण वर्णों का उपयोग करना

टेक्स्ट से निपटने के दौरान कंट्रोल कैरेक्टर उपयोगी हो सकते हैं। अपने टेक्स्ट में कंट्रोल कैरेक्टर को बदलने का तरीका यहां बताया गया है:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // "\r" नियंत्रण वर्ण को "\r\n" से प्रतिस्थापित करें।
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

इस उदाहरण में, हम कैरिज रिटर्न (`\r`) जिसमें कैरिज रिटर्न के बाद लाइन फीड (`\r\n`).

## निष्कर्ष

दस्तावेज़ गुण Aspose.Words for Java में आपके दस्तावेज़ों को प्रभावी ढंग से प्रबंधित और व्यवस्थित करने में महत्वपूर्ण भूमिका निभाते हैं। चाहे वह अंतर्निहित गुणों, कस्टम गुणों या नियंत्रण वर्णों का उपयोग करके काम करना हो, आपके पास अपने दस्तावेज़ प्रबंधन क्षमताओं को बढ़ाने के लिए आपके निपटान में कई उपकरण हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं अंतर्निहित दस्तावेज़ गुणों तक कैसे पहुँच सकता हूँ?

 Aspose.Words for Java में अंतर्निहित दस्तावेज़ गुणों तक पहुँचने के लिए, आप इसका उपयोग कर सकते हैं`getBuiltInDocumentProperties` विधि पर`Document` ऑब्जेक्ट। यह विधि अंतर्निहित गुणों का एक संग्रह लौटाती है जिसे आप पुनरावृत्त कर सकते हैं।

### क्या मैं किसी दस्तावेज़ में कस्टम दस्तावेज़ गुण जोड़ सकता हूँ?

 हां, आप किसी दस्तावेज़ में कस्टम दस्तावेज़ गुण जोड़ सकते हैं`CustomDocumentProperties` संग्रह। आप स्ट्रिंग, बूलियन, दिनांक और संख्यात्मक मानों सहित विभिन्न डेटा प्रकारों के साथ कस्टम गुण परिभाषित कर सकते हैं।

### मैं किसी विशिष्ट कस्टम दस्तावेज़ गुण को कैसे हटा सकता हूँ?

 किसी विशिष्ट कस्टम दस्तावेज़ गुण को हटाने के लिए, आप इसका उपयोग कर सकते हैं`remove` विधि पर`CustomDocumentProperties`संग्रह में, उस संपत्ति का नाम पास करना जिसे आप हटाना चाहते हैं, पैरामीटर के रूप में।

### किसी दस्तावेज़ की सामग्री को लिंक करने का उद्देश्य क्या है?

दस्तावेज़ के भीतर सामग्री को लिंक करने से आप दस्तावेज़ के विशिष्ट भागों के लिए गतिशील संदर्भ बना सकते हैं। यह इंटरैक्टिव दस्तावेज़ बनाने या अनुभागों के बीच क्रॉस-रेफ़रेंस बनाने के लिए उपयोगी हो सकता है।

### मैं Aspose.Words for Java में विभिन्न माप इकाइयों के बीच कैसे रूपांतरण कर सकता हूं?

 आप Aspose.Words for Java में विभिन्न मापन इकाइयों के बीच रूपांतरण कर सकते हैं`ConvertUtil` यह इंच को पॉइंट में, पॉइंट को सेंटीमीटर में, आदि इकाइयों को परिवर्तित करने के तरीके प्रदान करता है।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
