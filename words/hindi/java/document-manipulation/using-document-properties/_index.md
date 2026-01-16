---
date: 2026-01-16
description: इंच को पॉइंट्स में बदलना, जावा में दस्तावेज़ मेटाडेटा पढ़ना, जावा में
  कस्टम प्रॉपर्टीज़ जोड़ना, और Aspose.Words for Java के साथ जावा में पेज मार्जिन सेट
  करना सीखें।
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: इंच को पॉइंट में बदलें – Aspose.Words for Java में दस्तावेज़ गुणों का उपयोग
  करके
url: /hi/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# इंच को पॉइंट में बदलें – Aspose.Words for Java में डॉक्यूमेंट प्रॉपर्टीज़ का उपयोग करके

इस ट्यूटोरियल में आप **इंच को पॉइंट में बदलने** की प्रक्रिया को सीखेंगे जब आप पेज मार्जिन सेट करेंगे, जावा में डॉक्यूमेंट मेटाडाटा पढ़ेंगे, कस्टम प्रॉपर्टीज़ जोड़ेंगे, और Aspose.Words for Java का उपयोग करके बिल्ट‑इन डॉक्यूमेंट प्रॉपर्टीज़ के साथ काम करेंगे। चाहे आप रिपोर्ट, इनवॉइस या कानूनी दस्तावेज़ बना रहे हों, इन तकनीकों में निपुणता आपको आपके Word फ़ाइलों की उपस्थिति और मेटाडाटा पर सूक्ष्म नियंत्रण देती है।

## त्वरित उत्तर
- **इंच को पॉइंट में कैसे बदलूँ?** Aspose.Words की `ConvertUtil.inchToPoint(value)` का उपयोग करें।  
- **क्या मैं जावा में डॉक्यूमेंट मेटाडाटा पढ़ सकता हूँ?** हाँ – `doc.getBuiltInDocumentProperties()` या `doc.getCustomDocumentProperties()` को कॉल करें।  
- **जावा में कस्टम प्रॉपर्टी कैसे जोड़ूँ?** `doc.getCustomDocumentProperties().add(name, value)` का उपयोग करें।  
- **पेज मार्जिन को पॉइंट में सेट करने का मेथड कौन सा है?** `PageSetup.setTopMargin`, `setBottomMargin` आदि, पॉइंट मान स्वीकार करते हैं।  
- **बुकमार्क लिंकिंग समर्थित है?** हाँ – कस्टम प्रॉपर्टीज़ कलेक्शन पर `addLinkToContent` का उपयोग करें।

## डॉक्यूमेंट प्रॉपर्टीज़ का परिचय

डॉक्यूमेंट प्रॉपर्टीज़ किसी भी Word फ़ाइल का एक महत्वपूर्ण हिस्सा हैं। ये शीर्षक, लेखक, विषय, कीवर्ड्स और आपके डाउनस्ट्रीम प्रोसेसिंग के लिए आवश्यक किसी भी कस्टम मेटाडाटा जैसी जानकारी संग्रहीत करती हैं। Aspose.Words for Java में आप बिल्ट‑इन और कस्टम दोनों डॉक्यूमेंट प्रॉपर्टीज़ को मैनीपुलेट कर सकते हैं, और मार्जिन जैसे लेआउट विवरणों को माप इकाइयों को बदलकर नियंत्रित कर सकते हैं (जैसे **इंच को पॉइंट में बदलें**)।

## “इंच को पॉइंट में बदलें” क्या है?

Word में लेआउट माप इकाइयाँ पॉइंट में व्यक्त की जाती हैं (1 पॉइंट = 1/72 इंच)। इंच को पॉइंट में बदलने से आप मार्जिन, इंडेंट और स्पेसिंग को परिचित इम्पीरियल यूनिट्स में परिभाषित कर सकते हैं, जबकि API आंतरिक रूप से पॉइंट के साथ काम करता है।

## जावा में डॉक्यूमेंट मेटाडाटा का प्रबंधन क्यों?

मेटाडाटा एम्बेड करने से खोज, वर्गीकरण और वर्कफ़्लो ऑटोमेशन आसान हो जाता है। उदाहरण के लिए, आप किसी कॉन्ट्रैक्ट को “Authorized” फ़्लैग से टैग कर सकते हैं या ऑडिट ट्रेल के लिए रिविजन नंबर स्टोर कर सकते हैं। इस जानकारी को प्रोग्रामेटिक रूप से पढ़ना और लिखना बड़े दस्तावेज़ बैचों में निरंतरता सुनिश्चित करता है।

## पूर्वापेक्षाएँ
- Java 17+ (या संगत JDK)  
- आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी जोड़ी गई हो (Maven/Gradle)  
- एक सैंपल `.docx` फ़ाइल (जैसे `Properties.docx`) जिसे आप एक्सेस कर सकें

## चरण‑दर‑चरण गाइड

### बिल्ट‑इन डॉक्यूमेंट प्रॉपर्टीज़ की सूची बनाना
नीचे एक सरल टेस्ट है जो दस्तावेज़ खोलता है और सभी बिल्ट‑इन प्रॉपर्टीज़ जैसे Title, Author, और Keywords को प्रिंट करता है।

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

> **प्रो टिप:** इस स्निपेट का उपयोग करके आप यह सत्यापित कर सकते हैं कि आपका मेटाडाटा पहले के चरणों में सही ढंग से लिखा गया था।

### कस्टम डॉक्यूमेंट प्रॉपर्टीज़ जोड़ना (add custom properties java)
कस्टम प्रॉपर्टीज़ आपको किसी भी डेटा टाइप को स्टोर करने देती हैं—बूलियन, स्ट्रिंग, डेट, नंबर आदि।

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

> **यह क्यों महत्वपूर्ण है:** **Authorized** जैसे फ़्लैग को जोड़ने से आप डॉक्यूमेंट कंटेंट बदले बिना डाउनस्ट्रीम एप्रूवल वर्कफ़्लो को संचालित कर सकते हैं।

### कस्टम प्रॉपर्टी हटाना
यदि कोई प्रॉपर्टी अब आवश्यक नहीं है, तो आप इसे साफ़‑सुथरे ढंग से डिलीट कर सकते हैं।

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### कंटेंट लिंक कॉन्फ़िगर करना (बुकमार्क लिंकिंग)
आप एक बुकमार्क बना सकते हैं और फिर एक कस्टम प्रॉपर्टी जोड़ सकते हैं जो उस बुकमार्क की ओर इशारा करती है, जिससे डायनामिक क्रॉस‑रेफ़रेंसेज़ संभव होते हैं।

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

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### माप इकाइयों के बीच रूपांतरण (set page margins java)
यहीं पर मुख्य कीवर्ड चमकता है। हम मार्जिन को इंच में सेट करते हैं, फिर **इंच को पॉइंट में बदलें** `ConvertUtil` का उपयोग करके करते हैं।

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **नोट:** `ConvertUtil` `pointToInch`, `mmToPoint` आदि मेथड भी प्रदान करता है, जिससे लेआउट को लचीले ढंग से संभाला जा सकता है।

### कंट्रोल कैरेक्टर्स का उपयोग (read document metadata java)
कंट्रोल कैरेक्टर्स आपको टेक्स्ट स्ट्रीम को साफ़ करने में मदद करते हैं। यह उदाहरण कैरिज़‑रिटर्न (`\r`) को Windows लाइन‑ब्रेक सीक्वेंस (`\r\n`) से बदलता है।

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## सामान्य समस्याएँ और समाधान
| समस्या | कारण | समाधान |
|-------|-------|-----|
| रूपांतरण के बाद मार्जिन गलत दिख रहा है | गलत इकाई उपयोग (जैसे इंच के बजाय सेमी) | इंच मानों के लिए `ConvertUtil.inchToPoint` कॉल करना सुनिश्चित करें |
| कस्टम प्रॉपर्टी दिखाई नहीं दे रही | प्रॉपर्टी जोड़ने के बाद डॉक्यूमेंट को सेव नहीं किया गया | प्रॉपर्टीज़ जोड़ने के बाद `doc.save(...)` कॉल करें |
| बुकमार्क लिंक टूट गया | बुकमार्क नाम में टाइपो | `addLinkToContent` में बुकमार्क नाम बिल्कुल वही रखें |

## अक्सर पूछे जाने वाले प्रश्न

### बिल्ट‑इन डॉक्यूमेंट प्रॉपर्टीज़ तक कैसे पहुँचूँ?

Aspose.Words for Java में बिल्ट‑इन डॉक्यूमेंट प्रॉपर्टीज़ तक पहुँचने के लिए आप `Document` ऑब्जेक्ट पर `getBuiltInDocumentProperties` मेथड का उपयोग कर सकते हैं। यह मेथड बिल्ट‑इन प्रॉपर्टीज़ का एक कलेक्शन लौटाता है जिसे आप इटररेट कर सकते हैं।

### क्या मैं दस्तावेज़ में कस्टम डॉक्यूमेंट प्रॉपर्टीज़ जोड़ सकता हूँ?

हाँ, आप `CustomDocumentProperties` कलेक्शन का उपयोग करके दस्तावेज़ में कस्टम प्रॉपर्टीज़ जोड़ सकते हैं। आप स्ट्रिंग, बूलियन, डेट, और न्यूमेरिक वैल्यू सहित विभिन्न डेटा टाइप की कस्टम प्रॉपर्टीज़ परिभाषित कर सकते हैं।

### किसी विशिष्ट कस्टम डॉक्यूमेंट प्रॉपर्टी को कैसे हटाऊँ?

किसी विशिष्ट कस्टम डॉक्यूमेंट प्रॉपर्टी को हटाने के लिए आप `CustomDocumentProperties` कलेक्शन पर `remove` मेथड का उपयोग कर सकते हैं और उस प्रॉपर्टी का नाम पैरामीटर के रूप में पास कर सकते हैं।

### दस्तावेज़ के भीतर कंटेंट लिंकिंग का उद्देश्य क्या है?

दस्तावेज़ के भीतर कंटेंट लिंकिंग आपको दस्तावेज़ के विशिष्ट भागों के लिए डायनामिक रेफ़रेंसेज़ बनाने की अनुमति देती है। यह इंटरैक्टिव दस्तावेज़ या सेक्शन के बीच क्रॉस‑रेफ़रेंसेज़ बनाने में उपयोगी है।

### Aspose.Words for Java में विभिन्न माप इकाइयों के बीच कैसे बदलूँ?

आप `ConvertUtil` क्लास का उपयोग करके विभिन्न माप इकाइयों के बीच रूपांतरण कर सकते हैं। यह इंच को पॉइंट, पॉइंट को सेंटीमीटर आदि में बदलने के मेथड प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: मैं पूरे फ़ाइल को लोड किए बिना जावा में डॉक्यूमेंट मेटाडाटा कैसे पढ़ूँ?**  
उत्तर: `DocumentInfo` का उपयोग करके आप कोर प्रॉपर्टीज़ को पूरी फ़ाइल को लोड किए बिना प्राप्त कर सकते हैं।

**प्रश्न: क्या मैं मौजूदा दस्तावेज़ों के लिए जावा में प्रोग्रामेटिक रूप से पेज मार्जिन सेट कर सकता हूँ?**  
उत्तर: हाँ—दस्तावेज़ खोलें, `PageSetup` मार्जिन को संशोधित करें (यदि आवश्यक हो तो इंच को पॉइंट में बदलें), और सेव करें।

**प्रश्न: क्या कस्टम प्रॉपर्टीज़ को PDF मेटाडाटा में एक्सपोर्ट करना संभव है?**  
उत्तर: PDF में सेव करते समय, Aspose.Words स्वचालित रूप से कस्टम डॉक्यूमेंट प्रॉपर्टीज़ को PDF कस्टम मेटाडाटा में मैप कर देता है।

**प्रश्न: क्या कंट्रोल कैरेक्टर्स PDF रूपांतरण को प्रभावित करते हैं?**  
उत्तर: वे रूपांतरण के दौरान संरक्षित रहते हैं; हालांकि, निरंतरता के लिए आप लाइन एंडिंग को सामान्यीकृत करना चाह सकते हैं।

**प्रश्न: `ConvertUtil` के लिए कौन सा Aspose.Words संस्करण आवश्यक है?**  
उत्तर: `ConvertUtil` Aspose.Words 16.5 से उपलब्ध है; कोई भी हालिया संस्करण इसे सपोर्ट करता है।

## निष्कर्ष

**इंच को पॉइंट में बदलें**, जावा में डॉक्यूमेंट मेटाडाटा पढ़ें, और कस्टम प्रॉपर्टीज़ जोड़ें, इन सभी को महारत हासिल करके आप अपने Word फ़ाइलों के विज़ुअल लेआउट और छिपे डेटा दोनों पर पूर्ण नियंत्रण प्राप्त करते हैं। ये क्षमताएँ आपको ऑटोमेटेड डॉक्यूमेंट पाइपलाइन बनाने, अनुपालन लागू करने, और समृद्ध रूप से फ़ॉर्मेटेड रिपोर्ट्स तैयार करने में सक्षम बनाती हैं—सभी Aspose.Words for Java के साथ।

---

**अंतिम अपडेट:** 2026-01-16  
**टेस्टेड विद:** Aspose.Words for Java 24.11  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}