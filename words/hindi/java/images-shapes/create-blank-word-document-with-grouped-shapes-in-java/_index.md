---
category: general
date: 2026-08-07
description: Aspose.Words का उपयोग करके जावा में समूहित आकृतियों के साथ एक खाली Word
  दस्तावेज़ बनाएं। सीखें कि आकृति को कैसे समूहित करें, आकार सेट करें, और Word में
  आकृतियों को जोड़ें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: hi
lastmod: 2026-08-07
og_description: जावा में समूहित आकारों के साथ एक खाली Word दस्तावेज़ बनाएं। आकार का
  आकार सेट करने, Word में आकार जोड़ने, और आकार को समूहित करने में निपुण होने के लिए
  इस गाइड का पालन करें।
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: समूहित आकारों के साथ खाली Word दस्तावेज़ बनाएं – Java ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: जावा में समूहित आकृतियों के साथ खाली वर्ड दस्तावेज़ बनाएं
url: /hi/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में समूहित आकारों के साथ खाली Word दस्तावेज़ बनाएं

यदि आपको **create blank Word document** चाहिए जो कई आकारों को एक इकाई के रूप में व्यवस्थित करता है, तो यह ट्यूटोरियल आपको बिल्कुल दिखाएगा कि कैसे। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो **how to group shape** ऑब्जेक्ट्स को प्रदर्शित करता है, उनके आयाम समायोजित करता है, और Aspose.Words for Java का उपयोग करके **add shapes to Word** करता है।

यह गाइड हर चरण को—प्रोजेक्ट सेटअप से लेकर अंतिम .docx फ़ाइल को सेव करने तक—दिखाता है, ताकि आप कोड को सीधे अपने एप्लिकेशन में कॉपी कर सकें। कोई बाहरी संदर्भ आवश्यक नहीं है, और समाधान Aspose.Words 23.9 या बाद के संस्करणों के साथ काम करता है।

## आवश्यकताएँ

* Java 17 (या कोई भी समर्थित JDK)
* निर्भरता प्रबंधन के लिए Maven या Gradle
* Aspose.Words for Java लाइसेंस (या एक अस्थायी मूल्यांकन कुंजी)
* एक नमूना इमेज फ़ाइल (जैसे, `sample.jpg`) जिसे ज्ञात डायरेक्टरी में रखा गया हो

यदि इनमें से कोई भी आइटम गायब है, तो पहले उसे इंस्टॉल करें; ट्यूटोरियल का बाकी हिस्सा मानता है कि पर्यावरण तैयार है।

## चरण 1: अपने प्रोजेक्ट में Aspose.Words जोड़ें

अपने `pom.xml` (Maven) या `build.gradle` (Gradle) में Aspose.Words निर्भरता जोड़ें। यह लाइब्रेरी बाद में उपयोग होने वाले `Document`, `DocumentBuilder`, `GroupShape`, और `Shape` क्लासेज़ प्रदान करती है।

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Why this matters:** लाइब्रेरी के बिना, Word‑processing APIs उपलब्ध नहीं हैं, और आप प्रोग्रामेटिक रूप से **create blank Word document** नहीं बना सकते।

## चरण 2: एक खाली Word दस्तावेज़ बनाएं

पहला ठोस कार्य `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है, जो मेमोरी में एक **blank Word document** का प्रतिनिधित्व करता है।

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* डिफ़ॉल्ट सेटिंग्स (A4 पेज, डिफ़ॉल्ट मार्जिन) के साथ एक **blank Word document** बनाता है। साथ में आने वाला `DocumentBuilder` आपको वर्तमान कर्सर स्थिति पर सामग्री डालने की अनुमति देता है।

## चरण 3: एक समूह आकार डालें (how to group shape)

एक *group shape* अन्य आकारों के लिए कंटेनर के रूप में कार्य करता है। इस चरण में आप **how to group shape** ऑब्जेक्ट्स को सीखते हैं ताकि वे साथ में मूव हों।

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

`insertGroupShape` मेथड कंटेनर को बिल्डर के कर्सर स्थान पर रखता है। जब आप कई ड्रॉइंग्स को एक इकाई के रूप में ट्रीट करना चाहते हैं, तब ग्रुपिंग आवश्यक है—यह **group shapes word** कार्यक्षमता का मूल है।

## चरण 4: एक आयत बनाएं और उसका आकार सेट करें

अब समूह में एक आयत जोड़ें। यह **set shape size** को दर्शाता है, जो सटीक लेआउट के लिए आवश्यक है।

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Why set dimensions?* स्पष्ट रूप से `setWidth` और `setHeight` को कॉल करने से यह सुनिश्चित होता है कि आयत ठीक उसी तरह दिखे जैसा आप चाहते हैं, चाहे दस्तावेज़ की डिफ़ॉल्ट आकार शैलियाँ कुछ भी हों।

## चरण 5: एक इमेज डालें और उसे समूह में जोड़ें

एक चित्र जोड़ना **add shapes to word** का एक और सामान्य उपयोग केस दर्शाता है। इमेज उसी समूह का हिस्सा बन जाता है, आयत के साथ मिलकर मूव करता है।

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

यदि इमेज फ़ाइल गायब है, तो Aspose.Words एक एक्सेप्शन फेंकेगा। एक व्यावहारिक टिप यह है कि पहले पाथ को सत्यापित करें:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## चरण 6: समूहित आकारों वाले दस्तावेज़ को सेव करें

अंत में, **blank Word document** (अब एक समूहित आकार से भर गया है) को डिस्क पर सहेजें।

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

जब आप Microsoft Word में `GroupShapeDemo.docx` खोलते हैं, तो आपको एक एकल समूहित ऑब्जेक्ट दिखेगा जिसमें एक आयत और एक इमेज है। समूह के किसी भी भाग को चुनने से पूरा कंटेनर मूव हो जाता है, जिससे पुष्टि होती है कि आकार सही ढंग से **grouped** हुए हैं।

### अपेक्षित आउटपुट

* निर्दिष्ट डायरेक्टरी में `GroupShapeDemo.docx` नाम की फ़ाइल।
* फ़ाइल खोलने पर 300 × 200‑पॉइंट कंटेनर दिखेगा जिसमें:
  * (20, 20) पर स्थित 100 × 50‑पॉइंट आयत।
  * उसी कंटेनर के भीतर (150, 30) पर स्थित इमेज।

## किनारे के मामलों और विविधताएँ

| Situation | How to handle it |
|-----------|-----------------|
| **विभिन्न पेज आकार** | समूह डालने से पहले `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` कॉल करें। |
| **एकाधिक समूह** | नए `GroupShape` इंस्टेंस के साथ चरण 3‑5 दोहराएँ; प्रत्येक समूह को स्वतंत्र रूप से स्थित किया जा सकता है। |
| **आकार घुमाना** | समूह में जोड़ने से पहले आयत या चित्र को घुमाने के लिए `shape.setRotationAngle(45.0);` का उपयोग करें। |
| **गैर‑इमेज आकार** | `Shape` ऑब्जेक्ट्स को `ShapeType.ELLIPSE`, `ShapeType.LINE` आदि प्रकार के साथ बनाएं, और उन्हें आयत की तरह जोड़ें। |
| **बड़ी इमेजेज़** | समूह को उसकी मूल सीमा में रखने के लिए `picture.setWidth(80.0); picture.setHeight(60.0);` के साथ चित्र को स्केल करें। |

## अनुभव से व्यावहारिक टिप्स

* **Pro tip:** यदि आप चाहते हैं कि समूह पेज पर एंकर रहे न कि कर्सर पर, तो समूह के `RelativeHorizontalPosition` और `RelativeVerticalPosition` को क्रमशः `RelativeHorizontalPosition.PAGE` और `RelativeVerticalPosition.PAGE` सेट करें।
* **Watch out for:** ऐसा आकार जोड़ना जो समूह के आयामों से अधिक हो; वह आकार Word में क्लिप हो जाएगा। समूह का आकार `group.setWidth()` और `group.setHeight()` से अनुसार समायोजित करें।
* **Performance note:** यदि आप लूप में कई दस्तावेज़ बनाते हैं, तो एक ही `DocumentBuilder` इंस्टेंस को पुन: उपयोग करें और ऑब्जेक्ट‑क्रिएशन ओवरहेड कम करने के लिए `doc.clone()` कॉल करें।

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for Java का उपयोग करके **create blank Word document** कैसे बनाएं जिसमें आकारों का समूहित संग्रह हो। ट्यूटोरियल ने पूरी कार्यप्रवाह को कवर किया: लाइब्रेरी सेटअप, दस्तावेज़ बनाना, समूह डालना, **set shape size**, **add shapes to word**, और परिणाम को सेव करना।

अब आप अधिक उन्नत सुविधाओं का अन्वेषण कर सकते हैं जैसे चार्ट्स को समूहित करना, व्यक्तिगत आकारों पर स्टाइल लागू करना, या दस्तावेज़ को PDF में निर्यात करना। इन सभी विषयों का आधार इस गाइड में दिखाए गए समान सिद्धांत हैं।

---

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स इस गाइड में प्रदर्शित तकनीकों पर आधारित निकट संबंधित विषयों को कवर करते हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करती हैं।

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}