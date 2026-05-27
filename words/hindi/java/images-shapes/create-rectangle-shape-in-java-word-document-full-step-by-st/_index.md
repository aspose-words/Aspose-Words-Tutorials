---
category: general
date: 2026-05-26
description: जावा वर्ड दस्तावेज़ में आयताकार आकार बनाएं और शैडो इफ़ेक्ट लागू करें।
  सीखें कि कैसे आकार में शैडो जोड़ें, शैडो की दूरी सेट करें, और फ़ाइल को सहेजें।
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: hi
og_description: जावा वर्ड दस्तावेज़ में आयताकार आकार बनाएं, छाया प्रभाव लागू करें,
  आकार की छाया जोड़ें, और Aspose.Words के साथ छाया दूरी सेट करें।
og_title: जावा वर्ड दस्तावेज़ में आयताकार आकार बनाएं – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: जावा वर्ड दस्तावेज़ में आयत आकार बनाएं – पूर्ण चरण-दर-चरण गाइड
url: /hi/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java Word Document में आयताकार आकार बनाएं – पूर्ण चरण‑दर‑चरण मार्गदर्शिका

क्या आपको कभी Java Word दस्तावेज़ में **आयताकार आकार बनाना** पड़ा है लेकिन शुरू करने का तरीका नहीं पता था? आप अकेले नहीं हैं—कई डेवलपर्स को रिपोर्ट या इनवॉइस प्रोग्रामेटिकली जनरेट करते समय यही समस्या आती है। इस ट्यूटोरियल में हम बिल्कुल बताएँगे कि **आयताकार आकार कैसे बनाएं**, एक परिष्कृत शैडो लागू करें, और शैडो की दूरी को फाइन‑ट्यून करें ताकि परिणाम पेशेवर दिखे।

हम Aspose.Words for Java का उपयोग करेंगे, एक मजबूत लाइब्रेरी जो आपको Microsoft Office स्थापित किए बिना Word फ़ाइलों को मैनीपुलेट करने देती है। इस गाइड के अंत तक आप **create word document java** प्रोजेक्ट्स बना पाएँगे जो **add shape shadow**, **apply shadow effect**, और **set shadow distance** को कुछ ही कोड लाइनों से लागू कर सकेंगे।

---

## आप क्या बनाएँगे

- एक नई `.docx` फ़ाइल जिसमें सियान रंग का आयताकार हो।
- एक वास्तविक ड्रॉप शैडो जो धुंधला, कोणीय, और आंशिक रूप से पारदर्शी हो।
- शैडो की दूरी पर पूर्ण नियंत्रण।
- एक तैयार‑चलाने योग्य Java क्लास जिसे आप किसी भी Maven या Gradle प्रोजेक्ट में डाल सकते हैं।
- कोई बाहरी टूल नहीं, कोई मैनुअल UI कदम नहीं—सिर्फ शुद्ध कोड।

---

## पूर्वापेक्षाएँ

- Java 8 या उससे नया (कोड Java 11, Java 17 आदि पर काम करता है)।
- Aspose.Words for Java लाइब्रेरी (Maven Central के माध्यम से उपलब्ध)।
- आपका पसंदीदा IDE या टेक्स्ट एडिटर (IntelliJ IDEA, Eclipse, VS Code…)।
- Java सिंटैक्स की बुनियादी परिचितता।

यदि आपने पहले कभी Maven डिपेंडेंसी नहीं जोड़ी है, तो यहाँ त्वरित स्निपेट है:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

अब, चलिए शुरू करते हैं।

---

## चरण 1: Word दस्तावेज़ में आयताकार आकार बनाएं

सबसे पहले हमें एक खाली दस्तावेज़ और एक `DocumentBuilder` चाहिए। बिल्डर को आप उस पेन की तरह सोचें जो दस्तावेज़ में लिखता है। एक बार यह मिल जाए, हम एक ही मेथड कॉल से **आयताकार आकार बना** सकते हैं।

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **यह क्यों महत्वपूर्ण है:** `insertShape` मेथड न केवल ज्यामिति बनाता है बल्कि आकार को दस्तावेज़ के आंतरिक संग्रह में भी जोड़ता है, जिससे आप तुरंत उसकी स्टाइलिंग शुरू कर सकते हैं।

---

## चरण 2: आकार पर शैडो इफ़ेक्ट लागू करें

अब जबकि आयताकार पेज पर मौजूद है, हम **शैडो इफ़ेक्ट लागू** करेंगे। शैडो गहराई देती है, जिससे आकार पेज से उठी हुई महसूस होती है—एक सूक्ष्म UI सुधार जो रिपोर्ट की पठनीयता बढ़ा सकता है।

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **प्रो टिप:** `5.0` का ब्लर अधिकांश स्क्रीन‑डिस्प्ले दस्तावेज़ों के लिए प्राकृतिक दिखता है। यदि आप प्रिंट कर रहे हैं, तो धुंधला दिखने से बचने के लिए थोड़ा कम मान चुन सकते हैं।

---

## चरण 3: शैडो दूरी सेट करें – प्लेसमेंट का फाइन‑ट्यूनिंग

शैडो केवल ब्लर नहीं होते; उन्हें सही ऑफ़सेट भी चाहिए। यहीं पर हम **शैडो दूरी सेट** करते हैं। `7.0` पॉइंट की दूरी एक मध्यम ऑफ़सेट बनाती है जो दिखने योग्य है लेकिन अधिक नहीं।

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **यदि आपको बड़ा ऑफ़सेट चाहिए?** मान बढ़ाएँ; कसा हुआ लुक पाने के लिए घटाएँ। याद रखें, दूरी एंगल के साथ मिलकर शैडो को सही ढंग से पोजिशन करती है।

---

## चरण 4: दस्तावेज़ सहेजें – अपना काम सुरक्षित रखें

अंत में, हम दस्तावेज़ को डिस्क पर लिखते हैं। पाथ को उस स्थान पर बदलें जहाँ आप फ़ाइल रखना चाहते हैं।

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

क्लास चलाने से एक `shadow.docx` फ़ाइल बनती है जो Microsoft Word या LibreOffice में खोलने पर 45° पर एंगल्ड और 7 पॉइंट ऑफ़सेट वाली सॉफ्ट ग्रे शैडो के साथ सियान आयताकार दिखाती है।

---

## पूर्ण कार्यशील उदाहरण

नीचे पूरा, कॉपी‑एंड‑पेस्ट‑तैयार कोड दिया गया है। इसमें सभी इम्पोर्ट्स, कमेंट्स, और अंतिम `save` कॉल शामिल है।

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**अपेक्षित आउटपुट:** `shadow.docx` खोलें → आपको पहला पेज के केंद्र में सियान आयताकार दिखेगा, जिसके नीचे‑दाएँ ओर हल्का ग्रे शैडो होगा। शैडो का ब्लर और पारदर्शिता इसे प्राकृतिक प्रकाश जैसा बनाते हैं।

---

## सामान्य प्रश्न और किनारे के मामलों

### “क्या मैं कोई अलग आकार उपयोग कर सकता हूँ?”

बिल्कुल। `ShapeType.RECTANGLE` को `ShapeType.OVAL`, `ShapeType.LINE`, या किसी अन्य समर्थित एन्नुम से बदलें। शैडो कोड का बाकी हिस्सा समान रहता है।

### “यदि मुझे कई शैडो चाहिए तो?”

Aspose.Words प्रत्येक आकार के लिए केवल एक शैडो का समर्थन करता है। कई शैडो का सिमुलेशन करने के लिए, आकार को डुप्लिकेट करें, प्रत्येक कॉपी को ऑफ़सेट करें, और पारदर्शिता को समायोजित करें।

### “क्या LibreOffice में शैडो दिखता है?”

हां—Aspose.Words मानक OOXML लिखता है, जिसे LibreOffice सही ढंग से व्याख्या करता है। रेंडरिंग इंजन के कारण शैडो थोड़ा अलग दिख सकता है, लेकिन प्रभाव बना रहता है।

### “मैं शैडो का रंग अपने ब्रांड के अनुसार कैसे बदलूँ?”

सिर्फ `java.awt.Color.GRAY` को अपनी पसंद के किसी भी `java.awt.Color` से बदलें, जैसे कॉर्पोरेट ब्लू के लिए `new java.awt.Color(0, 120, 215)`।

---

## चित्रात्मक उदाहरण

![Java Word दस्तावेज़ में आयताकार आकार बनाना](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** चित्रण जिसमें Word दस्तावेज़ में सियान आयताकार और ग्रे ड्रॉप शैडो दिखाया गया है।

---

## सारांश और अगले कदम

हमने Aspose.Words for Java का उपयोग करके **आयताकार आकार बनाना**, **शैडो इफ़ेक्ट लागू करना**, **आकार शैडो जोड़ना**, और **शैडो दूरी सेट करना** कवर किया है। कोड स्व-निहित है, किसी भी आधुनिक JDK पर चलता है, और वितरण के लिए तैयार एक परिष्कृत `.docx` फ़ाइल बनाता है।

और आगे बढ़ना चाहते हैं? कोशिश करें:

- आयताकार के अंदर टेक्स्ट जोड़ना `builder.moveTo(rectangleShape.getAbsolutePosition())` के साथ।
- डायग्राम बनाने के लिए आकारों की एक टेबल बनाना।
- दस्तावेज़ को PDF में एक्सपोर्ट करना (`doc.save("output.pdf", SaveFormat.PDF);`)।

इनमें से प्रत्येक उसी मूलभूत सिद्धांतों पर आधारित है जो हमने अभी खोजे हैं, इसलिए आप उदाहरण को विस्तारित करने में सहज महसूस करेंगे।

---

## अंतिम विचार

**create word document java** जैसे आकार बनाना और शैडो लागू करना में महारत हासिल करने से रिपोर्ट, कॉन्ट्रैक्ट या मार्केटिंग कोलैटरल को ऑटोमेट करने में आपको बड़ा लाभ मिलता है। यहाँ दिखाया गया तरीका साफ़, रखरखाव योग्य, और—सबसे महत्वपूर्ण—आपकी किसी भी विज़ुअल स्टाइल के लिए आसानी से समायोजित करने योग्य है।

कोड को चलाएँ, ब्लर, एंगल, और दूरी को समायोजित करें, और देखें कि आपका दस्तावेज़ साधारण से परिष्कृत में बदलता है। यदि आपको कोई समस्या आती है, तो नीचे टिप्पणी छोड़ें; मैं मदद करने के लिए तैयार हूँ।

कोडिंग का आनंद लें!

## संबंधित ट्यूटोरियल

- [Word Document Java बनाएं – शैडो इफ़ेक्ट के साथ आयताकार आकार जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java में DocumentBuilder का उपयोग करके फ़ॉर्म फ़ील्ड बनाना और सामग्री जोड़ना](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word से PDF बनाना बारकोड जेनरेशन के साथ – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}