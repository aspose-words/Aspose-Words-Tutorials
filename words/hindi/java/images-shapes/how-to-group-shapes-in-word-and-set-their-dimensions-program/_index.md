---
category: general
date: 2026-11-25
description: जावा का उपयोग करके वर्ड में शैप्स को कैसे समूहित करें और Aspose.Words
  के साथ DOCX फ़ाइल में शैप के आयाम कैसे सेट करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: hi
lastmod: 2026-11-25
og_description: Aspose.Words Java API के साथ Word में शैलियों को समूहित कैसे करें
  और शीघ्रता से आकार सेट करें। पूर्ण चरण‑दर‑चरण समाधान का पालन करें।
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Word में आकृतियों को समूहित कैसे करें और उनके आयाम सेट करें – Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: वर्ड में आकृतियों को समूहित करने और प्रोग्रामेटिक रूप से उनके आयाम सेट करने
  का तरीका
url: /hi/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में शैप्स को ग्रुप करने और प्रोग्रामेटिकली उनके आयाम सेट करने का तरीका

यदि आपको **Word में शैप्स को ग्रुप करने** की आवश्यकता है और उनके सटीक आकार को नियंत्रित करना है, तो यह गाइड आपको एक पूर्ण, चलाने योग्य समाधान दिखाता है। Aspose.Words for Java का उपयोग करके आप एक रेक्टेंगल, एक एलिप्स बना सकते हैं, उन्हें `GroupShape` में जोड़ सकते हैं, और फिर **शैप के आयाम** जैसे चौड़ाई और ऊँचाई को एक ही DOCX फ़ाइल में सेट कर सकते हैं।

आप सीखेंगे:

* शून्य से एक नया Word दस्तावेज़ बनाना।  
* `GroupShape` (वर्ज़न 24.9 में नया API) डालना।  
* रेक्टेंगल और एलिप्स को ग्रुप में जोड़ना।  
* `setWidth` और `setHeight` के साथ **शैप साइज Word** को सटीक रूप से सेट करना।  
* दस्तावेज़ को डिस्क पर सहेजना।

कोई बाहरी टूलिंग आवश्यक नहीं—सिर्फ Java 17+, Maven, और Aspose.Words for Java लाइब्रेरी।

## Prerequisites

* Java Development Kit 17 या नया।  
* Maven (या Gradle) डिपेंडेंसी मैनेजमेंट के लिए।  
* Aspose.Words for Java 24.9 या बाद का ( `GroupShape` API 24.9 में पेश किया गया)।  
* Java सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड अवधारणाओं की बुनियादी समझ।

यदि आपने अभी तक अपने प्रोजेक्ट में Aspose.Words नहीं जोड़ा है, तो नीचे दिया गया Maven डिपेंडेंसी शामिल करें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a new document and a DocumentBuilder

`Document` क्लास पूरे Word फ़ाइल का प्रतिनिधित्व करती है, जबकि `DocumentBuilder` कंटेंट जोड़ने का सुविधाजनक तरीका प्रदान करता है।

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*इस चरण की आवश्यकता क्यों है?*  
एक नया `Document` बनाकर आपको एक साफ़ कैनवास मिलता है। `DocumentBuilder` वह हाई‑लेवल हेल्पर है जो आपको पैराग्राफ, टेबल और इस केस में शैप्स इन्सर्ट करने देता है।

## Step 2: Insert a GroupShape (new API in version 24.9)

`GroupShape` एक कंटेनर की तरह कार्य करता है; आप जो भी शैप जोड़ते हैं वह उसी विज़ुअल ग्रुप का हिस्सा बन जाता है।

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*`GroupShape` का उपयोग क्यों करें?*  
शैप्स को ग्रुप करने से कई ऑब्जेक्ट्स को एक साथ मूव, रोटेट या फॉर्मेट करना आसान हो जाता है। यह API 24.9 में जोड़ी गई थी, इसलिए पुराने वर्ज़न इस लाइन को कंपाइल नहीं करेंगे।

## Step 3: Create a rectangle, set its size, and add it to the group

यहाँ हम **शैप के आयाम सेट करने** का तरीका रेक्टेंगल के लिए दिखाते हैं।

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*चौड़ाई और ऊँचाई को स्पष्ट रूप से सेट करने की जरूरत क्यों है?*  
Word शैप साइज को पॉइंट्स में स्टोर करता है। `setWidth` और `setHeight` कॉल करके आप सटीक विज़ुअल फुटप्रिंट नियंत्रित करते हैं, जो सटीक लेआउट या PDF एक्सपोर्ट के समय आवश्यक होता है।

## Step 4: Create an ellipse, set its size, and add it to the same group

उसी **set shape size word** तकनीक का उपयोग किसी भी शैप टाइप के लिए किया जा सकता है।

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*इसे वही `GroupShape` में क्यों जोड़ें?*  
दोनों शैप्स एक साथ एक इकाई के रूप में मूव करेंगे। यह आइकन, लोगो या जटिल डायग्राम बनाने में उपयोगी है जिन्हें संरेखित रहना आवश्यक है।

## Step 5: Save the document with the grouped shapes

अंत में, DOCX फ़ाइल को डिस्क पर सहेजें।

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

इस प्रोग्राम को चलाने पर **GroupShape.docx** नाम की फ़ाइल बनती है जिसमें एक रेक्टेंगल और एक एलिप्स ग्रुपेड होते हैं। जब आप इसे Microsoft Word में खोलते हैं, तो दोनों शैप्स एक ही ऑब्जेक्ट की तरह व्यवहार करेंगे—आप उन्हें एक साथ ड्रैग, रिसाइज़ या रोटेट कर सकते हैं।

### Expected output

* एक Word दस्तावेज़ (`GroupShape.docx`) जिसमें एक पेज हो।  
* एक `GroupShape` जिसमें 100 × 50 pt रेक्टेंगल और 80 × 80 pt एलिप्स हो।  
* किसी भी शैप को सेलेक्ट करने पर पूरा ग्रुप चयनित हो जाएगा।

## Common questions and edge cases

### How to change the position of the grouped shapes?

`GroupShape` बनाने के बाद, आप उसकी `left` और `top` प्रॉपर्टीज़ सेट कर सकते हैं:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

ये कोऑर्डिनेट्स भी पॉइंट्स में मापे जाते हैं।

### What if I need to add more than two shapes?

`GroupShape` किसी भी अन्य कंटेनर नोड की तरह काम करता है। प्रत्येक अतिरिक्त शैप के लिए `groupShape.appendChild(yourShape)` कॉल करें। API बच्चों की संख्या पर कोई सीमा नहीं लगाता।

### Can I apply style (fill color, line weight) to individual shapes?

हां। प्रत्येक `Shape` ऑब्जेक्ट फॉर्मेटिंग प्रॉपर्टीज़ एक्सपोज़ करता है:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Does the code work with older Aspose.Words versions?

`insertGroupShape` मेथड वर्ज़न 24.9 में पेश किया गया था। यदि आप पुराने वर्ज़न पर हैं, तो आपको नोड ट्री के माध्यम से मैन्युअली `GroupShape` बनाना पड़ेगा, जो अधिक जटिल है। अपग्रेड करना सुझाया गया रास्ता है।

## Pro tips

* **संगतता के लिए पॉइंट्स का उपयोग करें** – Word की आंतरिक इकाई पॉइंट (1/72 इंच) है। पिक्सेल या सेंटीमीटर से कन्वर्ट करने से अनपेक्षित साइज हो सकते हैं।  
* **पोजिशनिंग से पहले ग्रुप करें** – सभी चाइल्ड जोड़ने के बाद `GroupShape` को पोजिशन करें; अन्यथा आपको ऑफ़सेट फिर से गणना करनी पड़ सकती है।  
* **DocumentBuilder को री‑यूज़ करें** – आप एक ही दस्तावेज़ में कई ग्रुप्स इन्सर्ट कर सकते हैं, बस प्रत्येक `insertGroupShape` कॉल से पहले बिल्डर का कर्सर (`builder.moveTo`) मूव करें।

## Conclusion

अब आपके पास **Word में शैप्स को ग्रुप करने** और **शैप के आयाम सेट करने** का एक पूर्ण, एंड‑टू‑एंड उदाहरण है, जो Aspose.Words for Java का उपयोग करता है। ट्यूटोरियल ने दस्तावेज़ बनाना, `GroupShape` इन्सर्ट करना, रेक्टेंगल और एलिप्स जोड़ना, उनके सटीक साइज सेट करना, और परिणाम को सहेजना शामिल किया।

अब आप आगे कर सकते हैं:

* उसी ग्रुप में टेक्स्ट बॉक्स या चित्र जोड़ना।  
* API के माध्यम से Word की स्मार्ट आर्ट फीचर का उपयोग करके ग्रुपेड शैप्स को एनीमेट करना।  
* ग्रुपेड शैप्स को PDF या SVG में एक्सपोर्ट करके वेब पर उपयोग करना।

विभिन्न शैप टाइप, साइज और पोजिशन के साथ प्रयोग करने में संकोच न करें—ग्रुपिंग आपको Word दस्तावेज़ों में जटिल लेआउट पर शक्तिशाली नियंत्रण देती है।

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑बद्ध व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}