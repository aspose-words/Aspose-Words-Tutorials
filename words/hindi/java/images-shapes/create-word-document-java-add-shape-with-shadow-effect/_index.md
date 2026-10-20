---
category: general
date: 2026-06-30
description: वर्ड डॉक्यूमेंट जावा उदाहरण बनाएं जो दिखाता है कि वर्ड डॉक्यूमेंट में
  आकार कैसे जोड़ें, आकार का भराव रंग सेट करें, और कुछ ही पंक्तियों में शैडो इफ़ेक्ट
  लागू करें।
draft: false
keywords:
- create word document java
- how to add shadow to shape
- add shape to word document
- set shape fill color
- apply shadow effect shape
language: hi
og_description: वर्ड दस्तावेज़ जावा ट्यूटोरियल बनाएं जो दिखाता है कि वर्ड दस्तावेज़
  में आकार कैसे जोड़ें, आकार का भराव रंग सेट करें, और छाया प्रभाव लागू करें।
og_title: जावा में वर्ड दस्तावेज़ बनाएं – शैडो इफ़ेक्ट के साथ आकार जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  headline: Create Word Document Java – Add Shape with Shadow Effect
  type: TechArticle
- description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  name: Create Word Document Java – Add Shape with Shadow Effect
  steps:
  - name: Creates the shape object.
    text: Creates the shape object.
  - name: Positions it at the current cursor location (top‑left of the page by default).
    text: Positions it at the current cursor location (top‑left of the page by default).
  - name: Adds it to the document’s internal node collection.
    text: Adds it to the document’s internal node collection.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: जावा में वर्ड दस्तावेज़ बनाएं – शैडो प्रभाव के साथ आकार जोड़ें
url: /hi/java/images-shapes/create-word-document-java-add-shape-with-shadow-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ जावा बनाएं – शैडो इफ़ेक्ट के साथ आकार जोड़ें

क्या आपको कभी **create word document java** कोड की जरूरत पड़ी है जो एक आयत बनाता है और उसे हल्का शैडो देता है? आप अकेले नहीं हैं। चाहे आप रिपोर्ट, इनवॉइस, या एक साधारण फ़्लायर बना रहे हों, प्रोग्रामेटिक रूप से **add shape to word document** करने से मैन्युअल समायोजन में घंटों की बचत होती है।  

इस गाइड में हम एक पूर्ण, तैयार‑चलाने‑योग्य उदाहरण के माध्यम से चलेंगे जो न केवल एक नया Word फ़ाइल बनाता है, बल्कि Aspose.Words for Java के साथ **set shape fill color**, **how to add shadow to shape**, और अंत में **apply shadow effect shape** भी करता है। कोई फालतू बात नहीं—सिर्फ वही कदम जो आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं।

> **Pro tip:** यदि आप Aspose.Words में नए हैं, तो सुनिश्चित करें कि आपके क्लासपाथ में नवीनतम JAR मौजूद है। हम जिस API का उपयोग करते हैं वह संस्करण 23.10 और उसके बाद के साथ काम करती है।

## आप क्या बनाएँगे

इस ट्यूटोरियल के अंत में आपके पास एक `.docx` फ़ाइल होगी जिसमें:

* शुरुआत से बनाया गया एक खाली Word दस्तावेज़।
* पहले पृष्ठ पर डाली गई एक पीली आयत (150 × 80 pts)।
* कुछ पॉइंट्स द्वारा ऑफ़सेट किया गया एक नरम ग्रे शैडो, जो आकार को उठी हुई दिखावट देता है।
* ऊपर बताए गए सभी कार्य केवल कुछ Java स्टेटमेंट्स से हासिल किए गए हैं।

कोई बाहरी टेम्पलेट नहीं, कोई जटिल XML नहीं—शुद्ध Java कोड जिसे कोई भी चला सकता है।

---

## Word दस्तावेज़ जावा बनाएं – आकार डालें

सबसे पहले हमें एक नया `Document` ऑब्जेक्ट और एक `DocumentBuilder` चाहिए। बिल्डर को पेन की तरह समझें जो हमें दस्तावेज़ के भीतर ड्रॉ करने देता है।

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to add content.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*यह क्यों महत्वपूर्ण है:* `Document` पूरी फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` हमें `insertShape` जैसी सुविधाजनक विधियाँ देता है। बिल्डर के बिना हमें लो‑लेवल नोड्स को सीधे संभालना पड़ेगा—जो बहुत अधिक काम है।

## Word दस्तावेज़ में आकार जोड़ें – आयत डालना

अब हम वास्तव में **add shape to word document** करेंगे। हमारे मामले में यह एक आयत है, लेकिन आप Aspose द्वारा समर्थित किसी भी `ShapeType` (ellipse, arrow, आदि) को चुन सकते हैं।

```java
        // Step 2: Insert a rectangle shape of size 150x80 points.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

यह एक ही पंक्ति तीन काम करती है:

1. आकार ऑब्जेक्ट बनाती है।
2. इसे वर्तमान कर्सर स्थान (डिफ़ॉल्ट रूप से पृष्ठ के शीर्ष‑बाएँ) पर रखती है।
3. इसे दस्तावेज़ के आंतरिक नोड संग्रह में जोड़ देती है।

यदि आप कभी *how to add shadow to shape* के बारे में सोच रहे थे, तो पढ़ते रहें—क्योंकि अगला चरण वही है।

## आकार का फ़िल रंग सेट करें – दिखावट को अनुकूलित करें

एक साधारण सफ़ेद आयत बहुत आकर्षक नहीं होती, इसलिए चलिए **set shape fill color** को कुछ चमकीला बनाते हैं। हम Java की `java.awt.Color` क्लास का उपयोग करेंगे, जिसे Aspose सीधे स्वीकार करता है।

```java
        // Step 3: Set the shape's fill color to yellow.
        rectangle.setFillColor(java.awt.Color.YELLOW);
```

`YELLOW` को `RED`, `GREEN` या किसी कस्टम RGB वैल्यू (`new Color(123, 45, 67)`) से बदल सकते हैं। फ़िल रंग वह सतह है जिसे आप शैडो लागू होने से पहले देखेंगे।

## आकार में शैडो जोड़ें – शैडो को कॉन्फ़िगर करना

यहीं पर जादू होता है। Aspose.Words एक `ShadowEffect` ऑब्जेक्ट प्रदान करता है जिससे हम शैडो की दिखावट को बारीकी से समायोजित कर सकते हैं।

```java
        // Step 4: Configure a custom shadow effect for the shape.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(java.awt.Color.GRAY);      // Shadow color
        shadow.setBlurRadius(5.0);                 // Softness of the shadow
        shadow.setOffsetX(4.0);                    // Horizontal offset
        shadow.setOffsetY(4.0);                    // Vertical offset
        shadow.setTransparency(0.3);               // Shadow opacity (0 = opaque, 1 = fully transparent)
```

**प्रत्येक प्रॉपर्टी क्यों महत्वपूर्ण है:**

| प्रॉपर्टी | क्या करता है | आम मान |
|----------|--------------|--------|
| `setColor` | शैडो का रंग निर्धारित करता है। अधिकांश मामलों में ग्रे काम करता है, लेकिन आप `Color.BLUE` के साथ बोल्ड भी जा सकते हैं। | कोई भी `java.awt.Color` |
| `setBlurRadius` | किनारों को कितना मुलायम दिखाना है, इसे नियंत्रित करता है। बड़े नंबर अधिक फैला हुआ लुक देते हैं। | 0 – 10 (float) |
| `setOffsetX` / `setOffsetY` | शैडो को दाएँ/बाएँ और ऊपर/नीचे ले जाता है। सकारात्मक मान शैडो को नीचे‑और‑दाएँ धकेलते हैं। | -10 – 10 |
| `setTransparency` | अपारदर्शिता सेट करता है; 0 ठोस, 1 अदृश्य। | 0.0 – 1.0 |

यदि आप **how to add shadow to shape** को लेआउट बिगाड़े बिना लागू करना चाहते हैं, तो मुख्य बात है ऑफ़सेट को मध्यम रखना। बहुत बड़ा ऑफ़सेट शैडो को अगले पृष्ठ पर ले जा सकता है।

## शैडो इफ़ेक्ट आकार लागू करें – दस्तावेज़ सहेजें

अब आकार स्टाइल किया गया है और शैडो कॉन्फ़िगर हो गया है, हमें बस फ़ाइल को सहेजना है।

```java
        // Step 5: Save the document with the shaped shadow.
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`YOUR_DIRECTORY` को अपने मशीन पर मौजूद किसी पूर्ण या सापेक्ष पथ से बदलें। प्रोग्राम चलाने के बाद, `ShadowShape.docx` को Microsoft Word या LibreOffice में खोलें—आपको पृष्ठ पर एक पीली आयत दिखाई देगी, जिसके नीचे ग्रे शैडो लगा होगा।

---

## परिणाम की जाँच – क्या देखना है

फ़ाइल खोलने पर:

* आयत कर्सर की शुरुआती स्थिति (डिफ़ॉल्ट रूप से पृष्ठ के शीर्ष‑बाएँ) पर केंद्रित होनी चाहिए।
* इसका फ़िल रंग चमकीला पीला होना चाहिए।
* एक हल्का ग्रे ब्लर 4 pts दाएँ और नीचे स्थित होना चाहिए, लगभग 30 % पारदर्शिता के साथ।

यदि शैडो बहुत कठोर लग रहा है, तो `BlurRadius` को कम करें या `Transparency` बढ़ाएँ। यदि आकार स्वयं दिखाई नहीं दे रहा, तो `setFillColor` कॉल को दोबारा जांचें—शायद चुना गया रंग पृष्ठ पृष्ठभूमि से मिल रहा है।

---

## सामान्य समस्याएँ एवं किनारे के मामले

| समस्या | कारण | समाधान |
|--------|------|--------|
| **शैडो गायब हो जाता है** | `Transparency` को `1.0` (पूरी तरह पारदर्शी) पर सेट किया गया है। | कम मान उपयोग करें, जैसे `0.3`। |
| **आकार दिखाई नहीं देता** | फ़िल रंग पृष्ठ पृष्ठभूमि (आमतौर पर सफ़ेद) से मेल खाता है। | `setFillColor` से कंट्रास्टिंग रंग चुनें। |
| **शैडो पेज मार्जिन पर कट रहा है** | ऑफ़सेट शैडो को प्रिंटेबल एरिया से बाहर धकेल रहा है। | `OffsetX`/`OffsetY` घटाएँ या `PageSetup` से मार्जिन बढ़ाएँ। |
| **कम्पाइलेशन त्रुटि: `cannot find symbol ShadowEffect`** | पुराना Aspose.Words संस्करण उपयोग किया गया है जिसमें शैडो सपोर्ट नहीं है। | Aspose.Words 23.10+ में अपग्रेड करें (API ने `ShadowEffect` 22.12 में पेश किया)। |

---

## अगले कदम – बुनियादी से आगे बढ़ना

अब आप जानते हैं कैसे **create word document java**, **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, और **apply shadow effect shape** किया जाता है, आप सोच सकते हैं आगे क्या किया जा सकता है। कुछ विचार:

* **डायनामिक रंग** – डेटाबेस से RGB वैल्यू लाकर स्थिति के आधार पर आकार को रंग‑कोड करें।
* **एकाधिक शैडो** – आकार को क्लोन करके प्रत्येक कॉपी पर अलग `ShadowEffect` कॉन्फ़िगरेशन लागू करके दो शैडो स्टैक करें।
* **आकार के भीतर टेक्स्ट** – `Shape.getTextFrame()` का उपयोग करके कैप्शन या लेबल एम्बेड करें।
* **PDF में एक्सपोर्ट** – `document.save("output.pdf", SaveFormat.PDF)` कॉल करके समान विज़ुअल फ़िडेलिटी वाला प्रिंट‑रेडी संस्करण प्राप्त करें।

इन सभी को हमने दिखाए गए मूल पैटर्न पर आधारित किया है: दस्तावेज़ बनाएं, आकार डालें, उसे स्टाइल करें, और सहेजें।

---

## पूर्ण कार्यशील उदाहरण (कॉपी‑पेस्ट तैयार)

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (150 × 80 pts).
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);

        // 3️⃣ Set the shape's fill color to yellow.
        rectangle.setFillColor(Color.YELLOW);

        // 4️⃣ Configure the shadow effect.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(Color.GRAY);        // Shadow color
        shadow.setBlurRadius(5.0);          // Softness
        shadow.setOffsetX(4.0);             // Horizontal offset
        shadow.setOffsetY(4.0);             // Vertical offset
        shadow.setTransparency(0.3);        // 30 % transparent

        // 5️⃣ Save the document.
        document.save("ShadowShape.docx");
    }
}
```

क्लास चलाने पर वर्तमान कार्यशील निर्देशिका में `ShadowShape.docx` बन जाएगा। इसे खोलें, और आप पहले वर्णित ठीक वही परिणाम देखेंगे।

---

## निष्कर्ष

हमने अभी-अभी दिखाया कि कैसे **create word document java** से शुरू करके **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, और अंत में **apply shadow effect shape** किया जाता है—सभी एक संक्षिप्त, समझने में आसान कोड नमूने के साथ।  

यह तरीका जानबूझकर सरल रखा गया है ताकि आप इसे अधिक जटिल परिदृश्यों में अनुकूलित कर सकें—चाहे आपको कई आकार, विभिन्न रंग, या एनीमेटेड‑स्टाइल शैडो चाहिए। API संस्करण संगतता पर नज़र रखें, और शैडो पैरामीटर को अपनी डिज़ाइन भाषा के अनुसार समायोजित करने से न डरें।

क्या आपने कोई ट्विस्ट आज़माया? शायद आपने आयत के पीछे एक चित्र रखा या आकार के अंदर एक टेबल जोड़ी। नीचे टिप्पणी करें; मैं जानना पसंद करता हूँ कि डेवलपर्स इन उदाहरणों को कैसे आगे बढ़ाते हैं। कोडिंग का आनंद लें

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Word दस्तावेज़ जावा बनाएं – शैडो इफ़ेक्ट के साथ आयत आकार जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java के साथ PDF दस्तावेज़ कैसे बनाएं | दस्तावेज़ प्रोसेसिंग API](/words/english/java/)
- [Aspose.Words Java: Word दस्तावेज़ प्रोसेसिंग के लिए व्यापक गाइड](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}