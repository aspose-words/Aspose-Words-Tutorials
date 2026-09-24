---
category: general
date: 2026-09-24
description: जावा में एक खाली Word दस्तावेज़ बनाना और Aspose.Words का उपयोग करके आयत
  और रेखाओं जैसी आकृतियों को समूहित करना सीखें। इसमें चरण‑दर‑चरण कोड शामिल है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: hi
lastmod: 2026-09-24
og_description: Java में एक खाली Word दस्तावेज़ बनाएं और Aspose.Words के साथ आकृतियों
  को समूहित करना, आयताकार आकृति जोड़ना, और आकृति का आकार सेट करना सीखें।
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: एक खाली Word दस्तावेज़ बनाएं और Java में आकृतियों को समूहित करें – चरण‑दर‑चरण
  मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: जावा में एक खाली वर्ड दस्तावेज़ कैसे बनाएं और आकृतियों को समूहित करें
url: /hi/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में एक खाली Word दस्तावेज़ कैसे बनाएं और आकृतियों को समूहित करें

यदि आपको **एक खाली Word दस्तावेज़ बनाना** है और फिर कई ड्रॉइंग ऑब्जेक्ट्स को व्यवस्थित करना है, तो यह गाइड आपको ठीक-ठीक बताता है कि कैसे। Aspose.Words for Java का उपयोग करके आप एक समूह आकृति सम्मिलित कर सकते हैं, एक आयत आकृति जोड़ सकते हैं, एक रेखा खींच सकते हैं, और प्रत्येक आकृति का आकार और स्थिति नियंत्रित कर सकते हैं—सभी एक ही चलाने योग्य प्रोग्राम में।

आप प्रत्येक चरण से गुजरेंगे, दस्तावेज़ को प्रारंभ करने से लेकर अंतिम `.docx` को सहेजने तक। अंत तक आप **आकृतियों को समूहित करने**, **आयत आकृति जोड़ने**, और **आकृति का आकार सेट करने** को समझ जाएंगे ताकि आपके Word फ़ाइलें बिल्कुल इच्छित रूप में दिखें।

## आवश्यकताएँ

- Java 17 या बाद का (कोड किसी भी हालिया JDK के साथ संकलित होता है)
- Aspose.Words for Java लाइब्रेरी ([Aspose वेबसाइट](https://products.aspose.com/words/java) से डाउनलोड करें)
- एक IDE या बिल्ड टूल (Maven/Gradle) जो क्लासपाथ में Aspose.Words JAR जोड़ सके
- Java सिंटैक्स का बुनियादी ज्ञान

> **Pro tip:** निर्भरता प्रबंधन के लिए Maven का उपयोग करें; अपने `pom.xml` में `com.aspose:aspose-words:23.12` (या नवीनतम संस्करण) जोड़ें।

## चरण 1: एक खाली Word दस्तावेज़ बनाएं

पहला कार्य **एक खाली Word दस्तावेज़ बनाना** है। यह आपको एक साफ़ कैनवास देता है जिस पर आप बाद में आकृतियों को सम्मिलित कर सकते हैं।

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*यह क्यों महत्वपूर्ण है:* A `Document` object represents the entire `.docx` file. Starting with a blank document ensures no hidden formatting interferes with the shapes you will add.

## चरण 2: समूह आकृति सम्मिलित करें – कई ऑब्जेक्ट्स के लिए कंटेनर

एक **समूह आकृति** एक कंटेनर की तरह काम करती है जो आपको कई आकृतियों को एक साथ स्थानांतरित, आकार बदलने या घुमाने की अनुमति देती है। यह Word में **आकृतियों को समूहित करने** का मूल है।

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*व्याख्या:* The `insertGroupShape` method creates a `GroupShape` object and places it at the current cursor location. All subsequent shapes that you `appendChild` to this group will be treated as a single unit.

## चरण 3: आयत आकृति जोड़ें और उसका आकार सेट करें

अब हम समूह में **आयत आकृति जोड़ते** हैं और **आकृति का आकार** सटीक रूप से सेट करते हैं।

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*आपको आकृति का आकार सेट करने की आवश्यकता क्यों है:* चौड़ाई और ऊँचाई निर्धारित करती है कि आयत पृष्ठ पर कैसे दिखाई देती है। `setLeft` और `setTop` मेथड्स आयत को समूह के मूल बिंदु के सापेक्ष स्थित करते हैं, जिससे आपको पिक्सेल‑सटीक लेआउट नियंत्रण मिलता है।

## चरण 4: रेखा आकृति जोड़ें और उसके आयाम कॉन्फ़िगर करें

एक रेखा एक अन्य सामान्य ड्रॉइंग ऑब्जेक्ट है। हम रेखा पर **आयत आकृति**‑जैसी लॉजिक लागू करेंगे, यह दर्शाते हुए कि वही आकार निर्धारण सिद्धांत लागू होते हैं।

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*मुख्य बिंदु:* भले ही रेखा की ऊँचाई नहीं होती, आप फिर भी उसकी लंबाई निर्धारित करने के लिए `setWidth` का उपयोग करते हैं। स्थिति निर्धारण (`setLeft`, `setTop`) अन्य आकृतियों के समान निर्देशांक प्रणाली का पालन करता है।

## चरण 5: समूहित आकृतियों के साथ दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को सहेजकर परिवर्तन को स्थायी बनाएं। यह एक `.docx` फ़ाइल बनाता है जिसे आप Microsoft Word में खोलकर परिणाम की पुष्टि कर सकते हैं।

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**अपेक्षित आउटपुट:** `GroupShapeDemo.docx` खोलने पर एक खाली पृष्ठ दिखता है जिसमें समूहित आयत और रेखा होती है। किसी भी आकृति का चयन करने पर पूरी समूह चयनित हो जाता है, जिससे आप उन्हें साथ में स्थानांतरित कर सकते हैं।

## सामान्य प्रश्न और किनारे‑के‑केस संभालना

| Question | Answer |
|----------|--------|
| *क्या मैं समूह में दो से अधिक आकृतियाँ जोड़ सकता हूँ?* | हाँ। प्रत्येक अतिरिक्त आकृति के लिए `group.appendChild(yourShape)` कॉल करें। |
| *यदि मुझे आकार के लिए अलग इकाई (जैसे सेंटीमीटर) चाहिए तो क्या करें?* | Aspose.Words पॉइंट्स का उपयोग करता है (1 पॉइंट = 1/72 इंच)। `Points = centimeters * 28.3465` का उपयोग करके परिवर्तित करें। |
| *क्या समूह का लेआउट दूसरे कंप्यूटर पर दस्तावेज़ खोलने पर भी बना रहेगा?* | बिल्कुल। सभी आकार और स्थिति डेटा `.docx` फ़ाइल में संग्रहीत होते हैं, जिससे लेआउट पोर्टेबल बन जाता है। |
| *मैं बाद में आकृतियों को कैसे अनग्रुप करूँ?* | `GroupShape` ऑब्जेक्ट प्राप्त करें, फिर `group.getChildNodes(NodeType.SHAPE, true)` पर इटररेट करें और प्रत्येक चाइल्ड को समूह से बाहर ले जाएँ। |
| *यदि मुझे पूरे समूह को घुमाना हो तो क्या करें?* | सहेजने से पहले `group.setRotationAngle(double angleInDegrees)` का उपयोग करें। |

## पूर्ण, चलाने योग्य उदाहरण

नीचे पूरा प्रोग्राम दिया गया है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी आवश्यक इम्पोर्ट्स और टिप्पणियाँ शामिल हैं।

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

प्रोग्राम चलाएँ, Microsoft Word में `GroupShapeDemo.docx` खोलें, और आप समूहित आकृतियों को ठीक उसी तरह देखेंगे जैसा वर्णित है।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for Java का उपयोग करके **एक खाली Word दस्तावेज़ कैसे बनाएं**, **Word में आकृतियों को समूहित करें**, **आयत आकृति जोड़ें**, और **आकृति का आकार सेट करें**। आकृतियों को `GroupShape` के अंदर रखकर आप सामूहिक स्थिति, स्केलिंग और घुमाव पर पूर्ण नियंत्रण प्राप्त करते हैं—डायग्राम, फ्लोचार्ट, या स्वचालित रिपोर्टों में एम्बेडेड कस्टम ग्राफिक्स के लिए बिल्कुल उपयुक्त।

**अगले कदम:**  
- चित्रों या टेक्स्ट बॉक्स जैसी अधिक जटिल वस्तुओं के साथ **आकृतियों को समूहित करने** का अन्वेषण करें।  
- पूरे समूह को घुमाने के लिए `setRotationAngle` के साथ प्रयोग करें।  
- इस तकनीक को मेल‑मर्ज के साथ मिलाकर व्यक्तिगत दस्तावेज़ बनाएं जिनमें ब्रांडेड ग्राफिक्स शामिल हों।

कोड को अपने प्रोजेक्ट्स के लिए अनुकूलित करने में संकोच न करें, और अपने परिणाम कमेंट्स में साझा करें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Java के साथ Word में आयत आकृति बनाएं – पूर्ण गाइड](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Java में Word दस्तावेज़ बनाएं – छाया प्रभाव के साथ आयत आकृति जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [.NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में समूह आकृति बनाएं](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}