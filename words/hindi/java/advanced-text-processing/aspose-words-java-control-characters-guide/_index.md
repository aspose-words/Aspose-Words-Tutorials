---
date: '2025-11-12'
description: Aspose.Words for Java का उपयोग करके पेज ब्रेक, टैब, नॉन‑ब्रेकिंग स्पेस
  और मल्टी‑कॉलम लेआउट कैसे डालें, इसे चरण‑बद्ध तरीके से सीखें – आज ही अपने दस्तावेज़
  ऑटोमेशन को बढ़ाएँ।
keywords:
- how to insert control characters
- add page break java
- manage carriage return aspose
- insert non breaking space
- create multi column layout
- Aspose.Words control characters
- Java document formatting
- text layout automation
- document generation Java
- Aspose.Words API
language: hi
title: Aspose.Words for Java के साथ नियंत्रण अक्षर सम्मिलित करें
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ कंट्रोल कैरेक्टर्स डालें

## जावा दस्तावेज़ों में कंट्रोल कैरेक्टर्स क्यों महत्वपूर्ण हैं
जब आप प्रोग्रामेटिक रूप से इनवॉइस, रिपोर्ट या न्यूज़लेटर बनाते हैं, तो सटीक टेक्स्ट लेआउट अनिवार्य होता है। **पेज ब्रेक**, **टैब** और **नॉन‑ब्रेकिंग स्पेस** जैसे कंट्रोल कैरेक्टर्स आपको मैन्युअल एडिटिंग के बिना यह निर्धारित करने देते हैं कि कंटेंट ठीक कहाँ दिखेगा। इस ट्यूटोरियल में आप देखेंगे कि Aspose.Words for Java API के साथ इन कैरेक्टर्स को कैसे मैनेज किया जाए, ताकि आपके दस्तावेज़ पहली बार बनते ही प्रोफ़ेशनल दिखें।

**इस गाइड में आप जो हासिल करेंगे**
1. कैरिज रिटर्न, लाइन फ़ीड और पेज ब्रेक डालना और सत्यापित करना।  
2. स्पेस, टैब और नॉन‑ब्रेकिंग स्पेस जोड़कर टेक्स्ट को अलाइन करना।  
3. कॉलम ब्रेक का उपयोग करके मल्टी‑कॉलम लेआउट बनाना।  
4. बड़े दस्तावेज़ों के लिए बेस्ट‑प्रैक्टिस परफ़ॉर्मेंस टिप्स लागू करना।

## प्री‑रिक्विज़िट्स
शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित उपलब्ध हैं:

| Requirement | Details |
|-------------|---------|
| **Aspose.Words for Java** | संस्करण 25.3 या बाद का (API बैकवर्ड कम्पैटिबल है)। |
| **JDK** | 8 या उससे ऊपर। |
| **IDE** | IntelliJ IDEA, Eclipse, या कोई भी पसंदीदा जावा IDE। |
| **Build Tool** | Maven **या** Gradle डिपेंडेंसी मैनेजमेंट के लिए। |
| **License** | एक टेम्पररी या खरीदा हुआ Aspose.Words लाइसेंस फ़ाइल (`aspose.words.lic`)। |

### Environment Setup Checklist
1. Maven **या** Gradle इंस्टॉल करें।  
2. Aspose.Words डिपेंडेंसी जोड़ें (अगले सेक्शन देखें)।  
3. अपने लाइसेंस फ़ाइल को सुरक्षित स्थान पर रखें और उसका पाथ नोट कर लें।

## अपने प्रोजेक्ट में Aspose.Words जोड़ना

### Maven
अपने `pom.xml` में नीचे दिया गया स्निपेट डालें:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
`build.gradle` में यह लाइन जोड़ें:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### लाइसेंस इनिशियलाइज़ेशन
लाइसेंस प्राप्त करने के बाद, इसे अपने एप्लिकेशन की शुरुआत में इनिशियलाइज़ करें:

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Note:** बिना लाइसेंस के लाइब्रेरी इवैल्यूएशन मोड में चलती है, जो वॉटरमार्क जोड़ती है।

## इम्प्लीमेंटेशन गाइड

हम दो मुख्य फीचर्स कवर करेंगे: **कैरिज‑रिटर्न हैंडलिंग** और **विभिन्न कंट्रोल कैरेक्टर्स डालना**। प्रत्येक फीचर को क्रमांकित स्टेप्स में विभाजित किया गया है, और हर कोड ब्लॉक से पहले एक छोटा व्याख्यात्मक पैराग्राफ होगा।

### Feature 1 – Carriage Return & Page Break Handling
`ControlChar.CR` (कैरिज रिटर्न) और `ControlChar.PAGE_BREAK` जैसे कंट्रोल कैरेक्टर्स दस्तावेज़ के लॉजिकल फ्लो को परिभाषित करते हैं। नीचे दिया गया उदाहरण दिखाता है कि कैसे इन कैरेक्टर्स की सही प्लेसमेंट को वेरिफ़ाई किया जाए।

#### Step‑by‑Step

1. **एक नया Document और DocumentBuilder बनाएं**  
   `Document` ऑब्जेक्ट सभी कंटेंट का कंटेनर है; `DocumentBuilder` फ़्लुएंट API प्रदान करता है जिससे टेक्स्ट जोड़ा जा सके।

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **दो साधारण पैराग्राफ डालें**  
   प्रत्येक `writeln` कॉल स्वचालित रूप से पैराग्राफ ब्रेक जोड़ देता है।

   ```java
   builder.writeln("Hello world!");
   builder.writeln("Hello again!");
   ```

3. **कंट्रोल कैरेक्टर्स के साथ अपेक्षित स्ट्रिंग बनाएं**  
   हम `MessageFormat` का उपयोग करके `ControlChar.CR` और `ControlChar.PAGE_BREAK` को अपेक्षित टेक्स्ट में एम्बेड करते हैं।

   ```java
   String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
           MessageFormat.format("Hello again!{0}", ControlChar.CR) +
           ControlChar.PAGE_BREAK;
   assert doc.getText().equals(expectedTextWithCR) :
           "Text does not match expected value with control characters.";
   ```

4. **डॉक्यूमेंट टेक्स्ट को ट्रिम करें और फिर से वैलिडेट करें**  
   ट्रिमिंग ट्रेलिंग व्हाइटस्पेस हटाता है जबकि इरादतन लाइन ब्रेक को बरकरार रखता है।

   ```java
   String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
   assert doc.getText().trim().equals(expectedTrimmedText) :
           "Trimmed text does not match expected value.";
   ```

> **Result:** असर्शन यह पुष्टि करते हैं कि दस्तावेज़ की आंतरिक टेक्स्ट रिप्रेजेंटेशन में वही कैरिज रिटर्न और पेज ब्रेक मौजूद हैं जो आप अपेक्षित थे।

### Feature 2 – विभिन्न कंट्रोल कैरेक्टर्स डालना
अब हम देखेंगे कि कैसे स्पेस, टैब, लाइन फ़ीड, पैराग्राफ ब्रेक और कॉलम ब्रेक को सीधे दस्तावेज़ में एम्बेड किया जाए।

#### Step‑by‑Step

1. **एक नया DocumentBuilder इनिशियलाइज़ करें**  
   एक क्लीन डॉक्यूमेंट से शुरू करने से उदाहरण अलग‑अलग रहते हैं।

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **स्पेस‑संबंधी कैरेक्टर्स डालें**  

   *स्पेस कैरेक्टर (`ControlChar.SPACE_CHAR`)*  
   ```java
   builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
   ```

   *नॉन‑ब्रेकिंग स्पेस (`ControlChar.NON_BREAKING_SPACE`)*  
   ```java
   builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
   ```

   *टैब कैरेक्टर (`ControlChar.TAB`)*  
   ```java
   builder.write("Before tab." + ControlChar.TAB + "After tab.");
   ```

3. **लाइन और पैराग्राफ ब्रेक जोड़ें**  

   *लाइन फ़ीड उसी पैराग्राफ के भीतर नई लाइन बनाता है।*  
   ```java
   // Verify that we start with a single paragraph
   Assert.assertEquals(1, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());

   builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");

   // After inserting a line feed, a second paragraph should appear
   Assert.assertEquals(2, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *पैराग्राफ ब्रेक (`ControlChar.PARAGRAPH_BREAK`)*  
   ```java
   builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
   Assert.assertEquals(3, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *सेक्शन ब्रेक (`ControlChar.SECTION_BREAK`)*  
   ```java
   builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
   assert doc.getSections().getCount() == 1 :
           "Section count mismatch after section break.";
   ```

4. **कॉलम ब्रेक के साथ मल्टी‑कॉलम लेआउट बनाएं**  

   पहले, एक दूसरा सेक्शन जोड़ें और दो कॉलम सक्षम करें:

   ```java
   doc.appendChild(new Section(doc));
   builder.moveToSection(1);
   builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);
   ```

   फिर कॉलम ब्रेक डालें ताकि कंटेंट कॉलम 1 से कॉलम 2 में चले:

   ```java
   builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
   ```

> **Result:** कोड चलाने के बाद, डॉक्यूमेंट में सही जगह पर स्पेस, टैब, लाइन फ़ीड, पैराग्राफ ब्रेक, सेक्शन ब्रेक और दो‑कॉलम लेआउट मौजूद होगा—सभी Aspose.Words कंट्रोल कैरेक्टर्स द्वारा नियंत्रित।

## वास्तविक‑दुनिया के उपयोग केस
| Scenario | How Control Characters Help |
|----------|-----------------------------|
| **Invoice Generation** | सेट किए गए लाइन आइटम्स की संख्या के बाद पेज ब्रेक फोर्स करके टोटल को नई पेज पर रखें। |
| **Financial Reports** | टैब और नॉन‑ब्रेकिंग स्पेस का उपयोग करके कॉलम को अलाइन करें, जिससे नंबर फ़ॉर्मेटिंग सुसंगत रहे। |
| **Newsletters & Brochures** | साइड‑बाय‑साइड आर्टिकल्स के लिए कॉलम ब्रेक डिप्लॉय करें, मैन्युअल लेआउट की जरूरत नहीं। |
| **CMS‑Driven Docs** | यूज़र‑जनरेटेड कंटेंट के आधार पर डायनामिकली लाइन फ़ीड और पैराग्राफ ब्रेक डालें। |
| **Batch Document Creation** | कंट्रोल कैरेक्टर्स की बल्क इंसर्शन से प्रोसेसिंग ओवरहेड कम करें। |

## बड़े दस्तावेज़ों के लिए परफ़ॉर्मेंस टिप्स
- **Batch Inserts:** संभव हो तो कई `write` कॉल्स को एक स्टेटमेंट में ग्रुप करें।  
- **Repeated Layout Calculations से बचें:** सभी कंट्रोल कैरेक्टर्स को इन्सर्ट करने के बाद ही सेव या एक्सपोर्ट जैसे भारी ऑपरेशन करें।  
- **Java Flight Recorder** से प्रोफ़ाइल करें ताकि टेक्स्ट मैनीपुलेशन में कोई बॉटलनेक आसानी से पकड़ा जा सके।

## निष्कर्ष
अब आपके पास Aspose.Words for Java के साथ कंट्रोल कैरेक्टर्स को मास्टर करने का स्पष्ट, स्टेप‑बाय‑स्टेप मेथड है। स्पेस, टैब, लाइन फ़ीड, पेज ब्रेक और कॉलम ब्रेक को प्रोग्रामेटिकली डालकर आप बिना मैन्युअल ट्यूनिंग के परफ़ेक्टली फॉर्मेटेड इनवॉइस, रिपोर्ट और मल्टी‑कॉलम पब्लिकेशन बना सकते हैं।

**अगले कदम:**  
- कंट्रोल कैरेक्टर्स को फील्ड कोड्स के साथ मिलाकर डायनामिक कंटेंट बनाएं।  
- अपने ऑटोमेशन पाइपलाइन को विस्तारित करने के लिए Aspose.Words की मेल‑मर्ज, डॉक्यूमेंट प्रोटेक्शन और PDF कन्वर्ज़न जैसी फीचर्स एक्सप्लोर करें।

**Call to Action:** इन स्निपेट्स को अपने अगले जावा प्रोजेक्ट में इंटीग्रेट करें और देखें कि आपके जेनरेटेड डॉक्यूमेंट कितने क्लीन और भरोसेमंद बनते हैं!

## FAQ

1. **कंट्रोल कैरेक्टर क्या है?**  
   एक नॉन‑प्रिंटेबल सिंबल (जैसे टैब, लाइन फ़ीड, पेज ब्रेक) जो टेक्स्ट लेआउट को प्रभावित करता है बिना विज़िबल ग्लिफ़ के दिखे।

2. **क्या इन फीचर्स के लिए पेड लाइसेंस ज़रूरी है?**  
   टेम्पररी लाइसेंस इवैल्यूएशन के लिए काम करता है; फुल लाइसेंस इवैल्यूएशन वॉटरमार्क हटाता है और सभी API क्षमताओं को अनलॉक करता है।

3. **क्या मैं `ControlChar.COLUMN_BREAK` को सिंगल‑कॉलम डॉक्यूमेंट में उपयोग कर सकता हूँ?**  
   हाँ, लेकिन ब्रेक तभी असरदार होगा जब आप `PageSetup.getTextColumns().setCount()` के ज़रिए सेक्शन को मल्टी‑कॉलम में कॉन्फ़िगर करें।

4. **सभी उपलब्ध कंट्रोल कैरेक्टर्स की लिस्ट कैसे देखें?**  
   सभी कॉन्स्टैंट्स `com.aspose.words.ControlChar` क्लास में मौजूद हैं; पूरी एन्क्यूमरेशन के लिए आधिकारिक API डॉक्यूमेंटेशन देखें।

{{< /blocks/products/p