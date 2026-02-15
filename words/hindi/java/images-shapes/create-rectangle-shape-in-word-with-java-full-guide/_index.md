---
category: general
date: 2026-02-15
description: जावा का उपयोग करके वर्ड दस्तावेज़ में आयताकार आकार बनाएं। सीखें कि कैसे
  आकार में छाया जोड़ें, वर्ड दस्तावेज़ को सहेजें, और Aspose.Words के साथ आयताकार आकार
  जोड़ें।
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: hi
og_description: जावा के साथ वर्ड फ़ाइल में आयताकार आकार बनाएं। यह गाइड दिखाता है कि
  कैसे आकार में छाया जोड़ें, वर्ड दस्तावेज़ को सहेजें, और चरण‑दर‑चरण आयताकार आकार
  जोड़ें।
og_title: आयताकार आकार बनाएं – जावा Aspose.Words ट्यूटोरियल
tags:
- Aspose.Words
- Java
- Document Automation
title: जावा के साथ वर्ड में आयताकार आकार बनाएं – पूर्ण मार्गदर्शिका
url: /hi/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में Java के साथ आयताकार आकार बनाएं – पूर्ण गाइड

क्या आपको कभी **आयताकार आकार** Word फ़ाइल में बनाना पड़ा लेकिन शुरू करने का तरीका नहीं पता था? आप अकेले नहीं हैं—कई डेवलपर्स को रिपोर्ट या इनवॉइस ऑटोमेट करते समय यही समस्या आती है। अच्छी खबर? Aspose.Words for Java की मदद से आप कुछ ही लाइनों में आयत बनाकर उसे छाया (shadow) दे सकते हैं और Word दस्तावेज़ को सहेज सकते हैं।

इस ट्यूटोरियल में हम सब कुछ कवर करेंगे: खाली दस्तावेज़ को इनिशियलाइज़ करने से लेकर छाया कॉन्फ़िगर करने तक, और अंत में फ़ाइल को सहेजने तक। अंत तक आप जान जाएंगे **shape को shadow कैसे दें**, **shape shadow कैसे जोड़ें**, और **किसी भी Word दस्तावेज़ में आयताकार आकार कैसे जोड़ें**। कोई बाहरी दस्तावेज़ नहीं चाहिए—सिर्फ चलने योग्य कोड।

## Prerequisites

- Java 8 या नया (API Java 11+ के साथ भी काम करता है)।  
- Aspose.Words for Java लाइब्रेरी (संस्करण 23.9 या बाद वाला)।  
- IntelliJ IDEA या Eclipse जैसे IDE—कोई भी चलेगा।  
- Java सिंटैक्स की बेसिक समझ।

> **Pro tip:** यदि आप Maven उपयोग कर रहे हैं, तो `pom.xml` में Aspose.Words डिपेंडेंसी जोड़ें और बाकी IDE संभाल लेगा।

---

## Step 1: Initialize a New Document – How to **create rectangle shape**  

सबसे पहले: आपको एक साफ़ कैनवास चाहिए। Aspose.Words में वह कैनवास एक `Document` ऑब्जेक्ट है।

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

`Document` क्लास पूरे .docx फ़ाइल का प्रतिनिधित्व करती है। इसे आप वह नोटबुक समझ सकते हैं जहाँ आप बाद में **आयताकार आकार** और उसकी छाया **add rectangle shape** करेंगे।

## Step 2: Build the Rectangle – **Add rectangle shape**  

अब हम वास्तव में आयत बनाते हैं। हम इसका आकार, लेआउट और फ़िल रंग सेट करेंगे।

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

`INLINE` रैप क्यों? क्योंकि हम चाहते हैं कि आकार पैराग्राफ की तरह व्यवहार करे—सरल रिपोर्ट के लिए परफ़ेक्ट। यदि बाद में आपको टेक्स्ट को आकार के चारों ओर फ्लो करना है, तो आप इसे `TOPBOTTOM` में बदल सकते हैं।

## Step 3: Apply a Shadow – **How to shadow shape**  

सादा आयत थोड़ा नीरस लग सकता है। छाया जोड़ने से गहराई आती है और दस्तावेज़ अधिक प्रोफ़ेशनल दिखता है। यही वह जगह है जहाँ हम व्यावहारिक रूप से “**how to shadow shape**” का उत्तर देते हैं।

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

हर प्रॉपर्टी का अपना काम है:

- `setVisible(true)` छाया को सक्रिय करता है।  
- `setColor` एक डार्क ग्रे चुनता है जिससे सूक्ष्म प्रभाव मिलता है।  
- `setBlurRadius` किनारों को कितना सॉफ्ट दिखाना है, इसे नियंत्रित करता है।  
- `setOffsetX/Y` छाया को दाएँ और नीचे ले जाता है, जिससे लाइट सोर्स का एहसास होता है।  
- `setTransparency` इसे थोड़ा पारदर्शी बनाता है, ताकि आकार मुख्य रूप से दिखे।

> **Note:** यदि आपको रंगीन छाया चाहिए, तो बस `setColor` में अलग `java.awt.Color` पास कर दें।

## Step 4: Insert the Shape into the Document  

आयत और उसकी छाया तैयार होने के बाद, हम इसे दस्तावेज़ के पहले सेक्शन में डालते हैं।

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

`body` में अपेंड करने से आकार नई पैराग्राफ की तरह रख दिया जाता है। यदि आप आयत को किसी विशिष्ट स्थान पर चाहते हैं, तो `insertBefore` या `Paragraph` कलेक्शन को मैनिपुलेट कर सकते हैं।

## Step 5: **Save Word document** – Persist Your Work  

अंतिम चरण है फ़ाइल को डिस्क पर लिखना। यही वह क्षण है जब आप वास्तव में **save Word document** करेंगे।

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`YOUR_DIRECTORY` को अपने मशीन पर एक एब्सोल्यूट या रिलेटिव पाथ से बदलें। प्रोग्राम चलाने के बाद, `ShadowShape.docx` को Microsoft Word में खोलें—आपको एक लाइट‑ग्रे आयत साथ में सॉफ्ट डार्क शैडो दिखेगी।

![Aspose.Words का उपयोग करके छाया के साथ आयताकार आकार दिखाने वाला आरेख](https://example.com/rectangle-shadow.png "छाया के साथ आयताकार आकार बनाएं")

---

## Common Questions & Edge Cases  

### What if I need multiple rectangles?  

बस **Step 2** और **Step 3** को लूप में दोहराएँ, प्रत्येक इटरेशन में `setWidth`, `setHeight`, या `setFillColor` को बदलें। प्रत्येक आकार को अलग वेरिएबल नाम दें या उन्हें लिस्ट में स्टोर करें।

### Can I export to PDF instead of DOCX?  

बिल्कुल। आकार जोड़ने के बाद, `document.save("output.pdf")` कॉल करें। Aspose.Words रूपांतरण संभाल लेगा और छाया को बरकरार रखेगा।

### What about older Word versions?  

`document.save("file.doc", SaveFormat.DOC)` ओवरलोड का उपयोग करें। API स्वचालित रूप से फीचर्स को डाउनग्रेड कर देगा, लेकिन कुछ शैडो स्टाइल्स लेगेसी फ़ॉर्मेट में थोड़ा अलग दिख सकते हैं।

### How do I change the shadow direction?  

`setOffsetX` और `setOffsetY` को बदलें। पॉज़िटिव X छाया को दाएँ ले जाता है, नेगेटिव बाएँ। पॉज़िटिव Y नीचे, नेगेटिव ऊपर। इन मानों को एडजस्ट करके किसी भी एंगल से लाइट सोर्स सिम्युलेट करें।

---

## Tips for Working with Shapes  

- **Group shapes**: यदि आपको आयत के बगल में लेबल चाहिए, तो `GroupShape` बनाकर उसमें आयत और `TextBox` दोनों जोड़ें।  
- **Z‑order matters**: `shape.moveToFront()` या `shape.moveToBack()` से तय करें कौन सा आकार ऊपर दिखेगा।  
- **Performance**: सैकड़ों आकार जोड़ना धीमा हो सकता है। उन्हें एक ही सेक्शन में बैच करें, फिर अंत में एक बार `document.updatePageLayout()` कॉल करें।

---

## Recap  

हमने Java का उपयोग करके Word दस्तावेज़ में **आयताकार आकार** बनाने, **shape shadow जोड़ने**, और **Word दस्तावेज़ सहेजने** के तरीके को कवर किया। ऊपर दिए गए स्निपेट्स में पूरा चलने योग्य कोड है, और अब आप प्रत्येक प्रॉपर्टी के “क्यों” को समझते हैं—ताकि आप रंग, ब्लर, और ऑफ़सेट को अपनी डिज़ाइन के अनुसार कस्टमाइज़ कर सकें।

अगली चुनौती के लिए तैयार हैं? आयत को चार्ट के साथ मिलाएँ, या फ़ाइल को PDF में एक्सपोर्ट करके देखें कि शैडो कैसे रेंडर होती है। आप टेबल के अंदर **add rectangle shape** करके फैंसी रिपोर्ट लेआउट भी बना सकते हैं।

Happy coding, and may your documents always look as sharp as your code!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}